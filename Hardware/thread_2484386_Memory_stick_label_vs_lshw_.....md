---
title: "Memory stick label vs lshw ...."
date: 2023-02-24
forum: Hardware
---

### Post by michael351 on 2023-02-24
I was preparing to upgrade my motherboard memory and before opening up the computer case I did a 
lshw -C memory to see what I had. I am looking to upgrade the Samsung to 8GB.

But when I removed the memory, I noticed the label on the Kingston read: HX318C10FK2/16 NOT what lshw reported. These are two very different 8GB versions. One is dual channel, the other single and slower speed.

I have never seen this before.

Which is likely to be correct or how to tell?

>  *Bank:0
          description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          product: M378B5173QH0-CK0
          vendor: Samsung
          physical id: 0
          serial: 0190960CE023
          slot: DIMM3
          size: 4GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
     *-bank:1
          description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          product: KHX1866C10D3/8G
          vendor: Kingston
          physical id: 1
          serial: 0B408B02806D
          slot: DIMM1
          size: 8GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:2
          description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          product: M378B5173QH0-CK0
          vendor: Samsung
          physical id: 2
          serial: 0260960CE023
          slot: DIMM4
          size: 4GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
     *-bank:3
          description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          product: KHX1866C10D3/8G
          vendor: Kingston
          physical id: 3
          serial: 0B407502806D
          slot: DIMM2
          size: 8GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)


---

### Post by Autodave on 2023-02-24
As a rule, if you have mismatched sticks, the slowest one will rule.  A lot of times, you won't even get 2 different sticks to work at all.

---

### Post by michael351 on 2023-02-24
I should have been more clear. I have a memory stick with a label on it which doesn't match what lshw says is installed. I wanted to know if it is possible for lshw to be incorrect or is it more likely that the label is wrong. The memory as it is - is installed in pairs so it does work, but the 8GB modules are not showing up in lshw as what I thought they were. I was hoping to match them so all 4 bank slots were identical.

---

