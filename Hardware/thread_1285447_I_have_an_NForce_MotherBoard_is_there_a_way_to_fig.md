---
title: "I have an NForce MotherBoard is there a way to figure out which version of NForce it"
date: 2009-10-07
forum: Hardware
---

### Post by grandpa2390 on 2009-10-07
I need to figure out what version of NForce do I have by NVidia. I have no clue which version it is. Is there a program or a terminal command that will give me the details I need to go to NVidia's site and download the driver for my DualBoot Windows partition?

---

### Post by earthpigg on 2009-10-07
hi,

try this command:

```
sudo lshw
```

it is going to return a ***lot*** of information, but one of the first 'paragraphs' will be something like this:

```
  *-core
       description: Motherboard
       _***product: P6T DELUXE V2***_
       _***vendor: ASUSTeK Computer INC.***_
       physical id: 0
       version: Rev 1.xx
       serial: MS1C96B76801753
       slot: To Be Filled By O.E.M.

```

---

