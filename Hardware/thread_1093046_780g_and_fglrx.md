---
title: "780g and fglrx"
date: 2009-03-11
forum: Hardware
---

### Post by dalhamir on 2009-03-11
Hello, I have a M3A78 Motherboard and I am having video driver issues in trying to get Boxee working. I'm posting in their forum as well, but I figured someone here might have some more info on fglrx.

so, my mobo has a built-in Raedon HD3200:
```
boxee@boxee-box:~$ lspci | grep 'HD 3200'
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
```

notice it's on 1:5.0

fglrx is needed to make boxee run smoothly. I can boot into X when I install fglrx, but I get nasty black lines that pop in and out and boxee won't load completely. Obviously unusable. So I checked out my /var/log/xorg.0.log and here are what look to be the most relevant parts:

```
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.543.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 10 2008 21:37:39
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1

...

(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x82f1)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI

...

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.54.3
	ABI class: X.Org Server Extension, version 1.1
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported

...

drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
...
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72

```

I've attached the whole thing too if I'm leaving out any pertinent details. (well, it'll only allow 19kb for text files, so i'm putting the log inside a tar, which allows 970kb... silly)

It looks like the ATI drivers don't even recognize their own card... odd and annoying certainly.

Has anyone had any ideas on how to get fglrx working more smoothly with this mobo, I'd love to hear them. This machine is supposed to be dedicated to boxee (hence the name) so I don't mind trying something a bit risky with my xorg.conf. I can always just wipe it again.

---

### Post by choco140 on 2009-03-12
Same issue on Ubuntu 8.10, on same motherboard. Fglrx not usable, horizontal lines all over the screen, a bit like vertical refresh issues.

Have been looking arround too. No solution (except using open source ati driver).

---

### Post by arunthopil on 2009-03-19
> **dalhamir said:**
> Hello, I have a M3A78 Motherboard and I am having video driver issues in trying to get Boxee working. I'm posting in their forum as well, but I figured someone here might have some more info on fglrx.

so, my mobo has a built-in Raedon HD3200:
```
boxee@boxee-box:~$ lspci | grep 'HD 3200'
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
```

notice it's on 1:5.0

fglrx is needed to make boxee run smoothly. I can boot into X when I install fglrx, but I get nasty black lines that pop in and out and boxee won't load completely. Obviously unusable. So I checked out my /var/log/xorg.0.log and here are what look to be the most relevant parts:

```
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.543.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 10 2008 21:37:39
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1

...

(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x82f1)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI

...

(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.54.3
	ABI class: X.Org Server Extension, version 1.1
(II) fglrx(0): Using adapter: 1:5.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported

...

drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
...
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72

```

I've attached the whole thing too if I'm leaving out any pertinent details. (well, it'll only allow 19kb for text files, so i'm putting the log inside a tar, which allows 970kb... silly)

It looks like the ATI drivers don't even recognize their own card... odd and annoying certainly.

Has anyone had any ideas on how to get fglrx working more smoothly with this mobo, I'd love to hear them. This machine is supposed to be dedicated to boxee (hence the name) so I don't mind trying something a bit risky with my xorg.conf. I can always just wipe it again.



hi dalhmir.......

   I think i cud help U............. i was also fightin with ths Radeon driver issue ........am new to linux but smeway i fixed it......... you visit my blog that i just cntaing the fix of ths ATI radeon driver error


[http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)


i am sure U dnt hav to mess up with xorgconf............  try ths...its easy:D

---

### Post by dalhamir on 2009-03-19
Well, I was going to respond that I had fixed it, but thanks arunthopil, looks like there are two solutions.

For me, I knew that the Neuros LINK ([http://www.neurostechnology.com/neuros-link](http://www.neurostechnology.com/neuros-link)) was working with fglrx and a M3A78-EM board, so I actually just removed ubuntu's restricted driver repo and added the LINKs 3rd party repo.

you can find directions here: [http://wiki.neurostechnology.com/index.php/LINK_repositories](http://wiki.neurostechnology.com/index.php/LINK_repositories)

for me, that automatically prompted to install a set fglrx drivers through the package manager updates, but this might be because of all the screwing around on my system, so you might want to run

```
sudo apt-get install xorg-drivers-fglrx
```

if the prompt doesn't show up. then I needed to run ```
aticonfig --initial
``` to get my xorg.conf to use fglrx, and then everything was working as it should be.

And boxee is happy too!

---

