---
title: "Memory bank layout recommendation ...."
date: 2023-02-21
forum: Hardware
---

### Post by michael351 on 2023-02-21
I have a Dell Optiplex 7020 SFF computer with 4 memory banks. It came with the following layout shown below.
Is this the ideal way to position the memory or should bank 0-1 and 2-3 be the same?


    *-bank:0
          description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          product: M378B5173QH0-CK0
          vendor: Samsung
          physical id: 0
          serial: 0260960CE023
          slot: DIMM3
          size: 4GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
     *-bank:1
          description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          product: KHX1866C10D3/8G
          vendor: Kingston
          physical id: 1
          serial: 0B407502806D
          slot: DIMM1
          size: 8GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)
     *-bank:2
          description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          product: M378B5173QH0-CK0
          vendor: Samsung
          physical id: 2
          serial: 0190960CE023
          slot: DIMM4
          size: 4GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
     *-bank:3
          description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
          product: KHX1866C10D3/8G
          vendor: Kingston
          physical id: 3
          serial: 0B408B02806D
          slot: DIMM2
          size: 8GiB
          width: 64 bits
          clock: 1333MHz (0.8ns)

---

### Post by TheFu on 2023-02-21
You need to follow what the motherboard documentation says to do.  Generally, 0 and 2 need to be paired and 1 and 3 need to be paired to get double data rate transfers.

BTW, whenever posting text or terminal output, please, please, please use forum code tags to help readability.

---

