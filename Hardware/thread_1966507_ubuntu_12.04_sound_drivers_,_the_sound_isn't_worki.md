---
title: "ubuntu 12.04 sound drivers , the sound isn't working"
date: 2012-04-27
forum: Hardware
---

### Post by tawfekov on 2012-04-27
I had already installed ubuntu 12.04 , everything works fine except the sound , input and output aren't  really working 
`**lshw -html**` shows the sound card details in **red** 

this one is related some how to vga card shows in red 

```
id:	
multimedia
description:	Audio device
product:	High Definition Audio Controller
vendor:	NVIDIA Corporation
physical id:	
0.1
bus info:	
pci@0000:01:00.1
version:	a1
width:	32 bits
clock:	33MHz
capabilities:	pm msi pciexpress bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	cbc7c000-cbc7ffff

```

and this one is the msi sound hardware also shown up in red 

```
id:	
multimedia
description:	Audio device
product:	N10/ICH 7 Family High Definition Audio Controller
vendor:	Intel Corporation
physical id:	
1b
bus info:	
pci@0000:00:1b.0
version:	01
width:	64 bits
clock:	33MHz
capabilities:	pm msi pciexpress bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	cbefc000-cbefffff

```

when i boot up on old ubuntu dist `10.04` the sound and the microphone works well

---

