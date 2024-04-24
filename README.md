# Net_Practice

![netpractice logo](net_practice/img/np_logo.png)


<br>

NetPractice is a web-based application designed to help users practice and improve their networking skills. Whether you're a beginner learning the basics of networking or an experienced professional looking to refine your skills, NetPractice provides a platform for hands-on learning and experimentation.

#### NOTE:
If you wanna practice more : https://subnetipv4.com/

## Levels

<details>
  <summary>Level 1</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_1.png" alt="level1">  
  <br>
  <br>

**1.** Since _Client A_ and _Client B_ are on the same network, their IP address must represent the same network in accordance with the subnet mask.
<br>
The subnet mask is _255.255.255.0_, which means that the first 3 bytes of the IP address represent the network, and the 4th byte represents the host. Since we are on the same network, only the host can change.
<br>
The solution will be anything in the range of **104.96.23.0 - 104.96.23.255** excluding the following 3:

- **104.96.23.0:** The first number in the range of hosts (0 in this case) represents the network and cannot be used by a host.
- **104.96.23.255:** The last number in the range of hosts (255 in this case) represents the broadcast address.
- **104.96.23.12:** This address is already used by the host _Client B_.

**2.** The same reasoning as _1._, however the subnet mask is _255.255.0.0_ in this case. The first 2 bytes of the IP address will represent the network; and the last 2 bytes, the host address.
<br>
The solution will be anything in the range of **211.191.0.0 - 211.191.255.255**, excluding:

- **211.191.0.0:** Represents the network address.
- **211.191.255.255:** Represents the broadcast address.
- **211.191.89.75:** Already taken by host _Client C_.

</br>

</details>

---

<details>
  <summary>Level 2</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_2.png" alt="level2">
  <br>
  <br>

**1.** Since _Client B_ is on the same private network as _Client A_, they should have the exact same subnet mask.
<br>
The solution can only be **255.255.255.224**.

**2.** To understand the subnet mask of _255.255.255.224_, let's look at it in binary form, along with the IP _192.168.20.222_ of _Client B_:

<center>

```
MASK: 11111111.11111111.11111111.11100000
IP:   11000000.10101000.00010100.11011101
```

</center>
As we can see, the first 27 bits represent the IP address, while only the last 5 bits represent the host address.
<br>
All these 27 bits representing the network must stay the same in the IP addresses of hosts on the same network. To get the answer, we can only change the last 5 bits.
<br>
<br>
The answer is in the range of:

```
BIN:  11000000.10101000.00010100.11000000 - 11000000.10101000.00010100.11011111
or
DEC:  192.168.20.192 - 192.168.20.223
```

Excluding:
<br>

- **11000000.10101000.00010100.11000000:** Represents the network address (notice all 0 in the last 5 bits).
- **11000000.10101000.00010100.11011111:** Represents the broadcast address (notice all 1 in the last 5 bits).
- **11000000.10101000.00010100.11011110:** _Client B_ already has that address.

**3.** Here we are introduced the slash "/" notation for the subnet mask on _Interface D1_. A subnet mask of _/30_ means that the first 30 bits of the IP address represent the network address, and the remaining 2 bits represent the host address:

<center>

```
Mask /30: 11111111.11111111.11111111.11111100
```

</center>

We can see that this binary number corresponds to the decimal _255.255.255.252_, therefore it is identical to the mask found on _Interface C1_.
<br>
<br>
The answers can then be any address, as long as they meet the following conditions:

- The network address (first 30 bits) must be identical for _Client D_ and _Client C_.
- The host bits (last 2 bits) cannot be all 1, nor all 0.
- _Client D_ and _Client C_ do not have identical IP addresses.

</br>

</details>

---
<details>
  <summary>Level 3</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_3.png" alt="level3">
  <br>
  <br>

This exercise introduces the use of the **switch** (_Switch S_ in this example). The switch links multiple hosts of the same network together.
<br>
<br>

**1.** _Client A_, _Client B_, and _Client C_ are all on the same network. Therefore, they must all have the same subnet mask. Since _Client C_ already has the mask _255.255.255.128_, the mask for _Interface B1_ and for _Interface A1_ will also be _255.255.255.128_ (or in slash notation: _/25_).
<br>
<br>
The IP address of _Interface B1_ and _Interface C1_ must be on the same network range as the IP of _Client A_. This range is:

  <center>

```
104.198.241.0 - 104.198.241.128
```

  </center>
  Excluding of course the network address and the broadcast address.

</br>

</details>

---

<details>
  <summary>Level 4</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_4.png" alt="level4">
  <br>
  <br>

This exercise introduces the **router**. The router is used to link multiple networks together. It does so with the use of multiple interfaces (_Interface R1_, _Interface R2_, and _Interface R3_ in this example).
<br>
<br>

**1.** Since none of the masks on _Interface B1_, _Interface A1_, and _Interface R1_ are entered, we are free to choose our own subnet mask. A mask of **/24** is ideal as it leaves us with the entire 4th byte for the host address, and does not require binary calculations to find the range of possible host addresses.
<br>
<br>
The IP address of _Interface B1_ and _Interface R1_ must have the same network address as the IP address of _Interface A1_. With a subnet of _/24_, the possible range is:

  <center>

```
85.17.5.0 - 85.17.5.255
```

  </center>
  Excluding the network address and the broadcast address.
  <br>
  <br>

Note that we did not interact with the router _Interface R2_ and _Interface R3_, since none of our communications had to reach these sides of the router.
</br>

</details>

---
<details>
  <summary>Level 5</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_5.png" alt="level5">
  <br>
  <br>

This level introduces **routes**. A route contains 2 fields, the first one is the **destination** of outbound packets, the second one is the **next hop** of the packets.
<br>

The **destination** _default_ is equivalent to _0.0.0.0/0_, which will send the packets indiscriminately to the first network address it encounters. A destination address of _122.3.5.3/24_ would send the packets to the network _122.3.5.0_.

  <br>
  The **next hop** is the IP address of the next  router (or internet) interface to which the interface of the current machine must send its packets. 
  <br>
  <br>

**1.** _Client A_ only has 1 route through which it can send its packets. There is no use specifying a numbered destination. The destination _default_ will send the packets to the only path available.
<br>
<br>
The next hop address must be the IP address of the next router's interface on the packets' way. The next interface is _Interface R1_, with the IP address of _54.117.30.126_. Note that the next interface is not _Interface A1_, since this is the sender's own interface.

</br>

</details>

---

<details>
  <summary>Level 6</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_6.png" alt="level6">
  <br>
  <br>

This level introduces the **internet**. The internet behaves like a router. However, if an interface is connected directly or indirectly to the internet, it **cannot** have an IP address in the following reserved private IP ranges:

```
192.168.0.0 - 192.168.255.255 (65,536 IP addresses)
172.16.0.0 - 172.31.255.255   (1,048,576 IP addresses)
10.0.0.0 - 10.255.255.255     (16,777,216 IP addresses)
```

**1.** The **next hop** of the internet is already entered, and matches the IP address of the _Interface R2_. Therefore we only need to bother with the destination of the internet.
<br>
<br>
The internet must send its packets to _Client A_. To do so, the internet's destination must match the network address of _Client A_. Let's find the network address of _Client A_:
<br>
_Client A_'s mask is _255.255.255.128_, which is equivalent to _/25_. This means that the first 25 bits of its IP address are its network address. We know then that the first 3 bytes (24 bits) of its IP address make part of its network address:

  <center>

```
40.178.145.?
```

  </center>

We now only need to find out if the 25th bit is a 1 or a 0.
<br>
If we convert the number 227 to binary, we get `11100011`. The first digit, which corresponds to the 25th bit, is a 1. Since only the 25th bit is part of the network address and not the remaining 7 bits, we get `10000000` for the last byte of the network address, which is 128 in decimal.
<br>
<br>
The full network address is:

  <center>

```
40.178.145.128
```

  </center>

With a range of _40.178.145.129 - 40.178.145.254_ for its host addresses.
<br>
<br>
We can now put this address of **40.178.145.128** in the Internet destination. The **/25** following the destination address represents the mask applied to its address.
<br>
<br>
A destination of _40.178.145.227/25_ is equivalent to the destination address _40.178.145.128/25_, since the mask of _/25_ will turn all the bits after the 25th to 0 to get the destination's network address.
</br>

</details>

---

<details>
  <summary>Level 7</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_7.png" alt="level7">
  <br>
  <br>

This level introduces the concept of **overlaps**. The range of IP addresses of a network must not overlap the range of IP addresses of a separate network. Networks are separated by routers.
<br>
<br>

**1.** We have 3 separate networks:
<br>

1. Between _Client A_ and _Router R1_.
2. Between _Router R1_ and _Router R2_.
3. Between _Router R2_ and _Client C_.

For _Interface A1_, we cannot choose our IP address freely since the IP of _Interface R11_ is already entered. Also, if we give it a mask of _/24_, the IP address range will overlap with the range of _Interface R12_, which is already entered. They would both be in the range of _93.198.14.0 - 93.198.14.255_.
<br>
<br>

Since we need addresses for 3 separate networks, it is convenient to split the last bytes of the address into 4 or more address ranges. We do this by using a mask of _/26_ or higher. The mask of _/28_ for example will give us 16 ranges, from which we use the following 3:

```
93.198.14.1 - 93.198.14.14    (Client A to Router R1)
93.198.14.65 - 93.198.14.78   (Router R1 to Router R2)
93.198.14.241 - 93.198.14.254 (Router R2 to Client C)
```

To calculate the possible ranges of a mask:
<br>
https://www.calculator.net/ip-subnet-calculator.html?cclass=any&csubnet=28&cip=93.198.14.2&ctype=ipv4&printit=0&x=97&y=13

</br>

</details>

---

<details>
  <summary>Level 8</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_8.png" alt="level8">
  <br>
  <br>

**1.** The hosts _Client C_ and _Client D_ will send packets to the internet, then the internet will respond by sending packets all the way back to the initial sender. To send these packets, the internet uses the destination _49.175.13.0/26_ to send the packets to the networks in the range of `49.175.13.0 - 49.175.13.63`.
<br>
<br>
All the receiving networks must be in this range, without overlapping each other.
<br>
<br>

**2.** On _Interface R23_ and _Interface R22_ we use the mask _255.255.255.240_ (or _/28_), to conveniently split the range of _/26_ from the destination address, into 4 separate ranges. This separation of 4 is necessary since we have the following 3 networks that must not overlap:
<br>

1. _Router R1_ to _Router R2_.
2. _Router R2_ to _Client C_.
3. _Router R2_ to _Client D_.

Each of these networks can then be attributed one of the following IP ranges with a mask of _/28_:

```
49.175.13.0 - 49.175.13.15
49.175.13.16 - 49.175.13.31
49.175.13.32 - 49.175.13.47
49.175.13.48 - 49.175.13.63
```

Note that the network address (first) and the broadcast address (last) must be excluded from each range.
<br>
<br>

**3.** The destination and next hop for the internet are already entered. We only need to enter the next hop for the _Router R2_, which is the IP on the _Interface R21_.

</br>

</details>

---

<details>
  <summary>Level 9</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_9.png" alt="level9">
  <br>
  <br>

This level is quite straightforward since the internet does not initially send its packets to a specific network. Therefore, the separate networks do not need to share a common address range. I would suggest simply following the 6 goals of the level one by one until the level is completed.
<br>
<br>
Remember not to use the network addresses from the reserved private IP ranges.
<br>
<br>

**1.** **Goal 3** states that we must connect _meson_ with the _internet_. The _internet_ will then have to respond to _meson_, so we enter _meson's_ network address in the _internet's_ destination.
<br>
<br>
**Goal 6** states that we must connect _cation_ with the _internet_, so we enter _cation's_ network address in the _internet's_ destination.
<br>
<br>
It is normal to have an empty field for the 3rd destination of the _internet_, and in _Router R1's_ destination. Not all fields of the routing tables need to be filled.

</br>

</details>

---

<details>
  <summary>Level 10</summary>
  <br>
  <img src="https://github.com/zelabbas/net_practice/blob/main/soultions/imgs/level_10.png" alt="level10">
  <br>
  <br>

At this level, there are 4 different networks:
<br>

1. _Router R1_ to _Switch S1_
2. _Router R1_ to _Router R2_
3. _Router R2_ to _Client H4_
4. _Router R2_ to _Client H3_
   <br>

**1.** The internet must be able to send its packets to all the hosts, so its destination must cover the range of networks of all the hosts.
<br>
<br>

_Interface R11_ and _Interface R13_ already have an IP address entered. This IP address only differs in its last byte. _Interface R11_ has for last byte **1**, and _Interface R13_ has for last byte **254**. To cover this wide range to IP addresses, we take a mask of **/24** for the _internet's_ destination. This destination will cover a range of `70.101.30.0 - 70.101.30.255`.

  <br>
  <br>

**2.** When choosing the IP addresses, we must make sure of 2 things:
<br>

1. The IP address is covered by the _internet_ destination.
2. The IP address range of the various networks does not overlap.
   <br>

With the IP addresses already entered (greyed out), let's examine the ranges covered by the various networks:
<br>

1. _Router R1_ to _Switch S1_ - Covers the range **70.101.30.0 - 70.101.30.127** (mask /25).
2. _Router R2_ to _Client H4_ - Covers the range **70.101.30.128 - 70.101.30.191** (mask /26).
3. _Router R1_ to _Router R2_ - Covers the range **70.101.30.252 - 70.101.30.255** (mask /30).
4. _Router R2_ to _Client H3_ - ??? (mask ???).

The only IP addresses left for the network "Router R2 to Client H3" are **70.101.30.192 - 70.101.30.251**. We can pick any mask that will let us take 2 IP addresses from that range to put in _Interface R22_ and _Interface R31_.
</br>

</details>

