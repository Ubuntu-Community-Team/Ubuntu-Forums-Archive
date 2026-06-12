---
title: "RAM not detected"
date: 2018-08-30
forum: Hardware
---

### Post by crypso on 2018-08-30
Hello everyone, I have an issue adding another RAM in my hp notebook 14-am003nk, I had one 4G RAM in one slot and I added a new one in the free slot, but it's not properly detected, I tried to switch the RAMs the problem persists, I tried also to use the new RAM alone and the PC didn't start.

Here are the outputs of some commands:

```

$ uname -a
Linux HP 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

$ sudo dmidecode -t memory | egrep "^\s+Size"
Size: 4096 MB
Size: No Module Installed
   slot: System board or motherboard
   size: 4GiB
 *-bank:0
      description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
      product: HMT451S6BFR8A-PB
      vendor: Hynix/Hyundai
      physical id: 0
      serial: 23138687
      slot: Bottom-Slot 1(left)
      size: 4GiB
      width: 64 bits
      clock: 1600MHz (0.6ns)
 *-bank:1
      description: SODIMM DDR Synchronous 1600 MHz (0.6 ns) [empty]
      product: HMT351S6CFR8C-PB
      vendor: Hynix/Hyundai
      physical id: 1
      serial: 11131631
      slot: Bottom-Slot 2(right)
      clock: 1600MHz (0.6ns)

$ sudo dmidecode -t memory | egrep "^\s+Size"
    Size: 4096 MB
    Size: No Module Installed
```

---

### Post by Autodave on 2018-08-30
Is it seen before it boots into Linux?  Does the BIOS see it?  Sounds like you might have a bad stick....was it new? If new, I would contact vendor for replacement.

---

### Post by crypso on 2018-08-30
When I do a memory check in the BIOS it sees just the 4G of the old ram.
The ram is new, I think I'm gonna contact the vendor for replacement.

---

