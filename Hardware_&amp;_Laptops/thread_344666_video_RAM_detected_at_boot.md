---
title: "video RAM detected at boot"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by amorgen on 2007-01-23
Hello,
I tried with the french forum but nobody can say what is the problem: [http://forum.ubuntu-fr.org/viewtopic.php?id=88850](http://forum.ubuntu-fr.org/viewtopic.php?id=88850)

My problem is that I can't enable hardware acceleration with my radeon mobility 9700:
```
...
        *-pci:1
             description: PCI bridge
             product: nForce3 AGP Bridge
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@00:0b.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: RV350 [Mobility Radeon 9600 M10]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e0000000-e7ffffff ioport:c000-c0ff iomemory:ff4f0000-ff4fffff irq:11
...
```

**But I have 64 mb of video RAM and not 128 !!**

```
root@laptop:/home/amorgen# cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=  16MB: write-back, count=1
reg01: base=0x01000000 (  16MB), size=  16MB: write-back, count=1
reg02: base=0x02000000 (  32MB), size=  32MB: write-back, count=1
reg03: base=0x04000000 (  64MB), size=  64MB: write-back, count=1
reg04: base=0x08000000 ( 128MB), size= 128MB: write-back, count=1
reg05: base=0x10000000 ( 256MB), size= 256MB: write-back, count=1
reg06: base=0x20000000 ( 512MB), size= 512MB: write-back, count=1
reg07: base=0xf0000000 (3840MB), size= 128MB: write-combining, count=1
```

I tried this to correct /proc/mtrr:
```
echo "disable=7" >| /proc/mtrr
echo "base=0xd8000000 size=0x4000000 type=write-combining" >| /proc/mtrr
```

But the problem is the same...

I also declared the file by a script:
```

for i in 1 2 3 4 5 0 6 7; do echo "disable=$i" >| /proc/mtrr; done
echo "base=0x00000000 size=0x01000000 type=write-back" >| /proc/mtrr # 0
echo "base=0x01000000 size=0x01000000 type=write-back" >| /proc/mtrr # 16
echo "base=0x02000000 size=0x02000000 type=write-back" >| /proc/mtrr # 32
echo "base=0x04000000 size=0x04000000 type=write-back" >| /proc/mtrr # 64
echo "base=0x08000000 size=0x08000000 type=write-back" >| /proc/mtrr # 128
echo "base=0x10000000 size=0x10000000 type=write-back" >| /proc/mtrr # 256
echo "base=0x20000000 size=0x20000000 type=write-back" >| /proc/mtrr # 512
echo "base=0xf0000000 size=0x04000000 type=write-combining" >| /proc/mtrr # 64

```

I am running Edgy Eft Kubuntu with "Linux laptop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux" kernel on a Asus A2K laptop (amd64 3000+ with 512+256mb ram) with the last BIOS available (0207 [http://support.asus.com/download/download.aspx?SLanguage=fr-fr&model=A2K&type=map&mapindex=1](http://support.asus.com/download/download.aspx?SLanguage=fr-fr&model=A2K&type=map&mapindex=1))

I tried with Feisty Fawn Herd2 livecd with a newer kernel, same problem:
```
Linux ubuntu 2.6.20-5-generic #2 SMP Sat Jan 6 14:50:47 UTC 2007 i686 GNU/Linux
ubuntu@ubuntu:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(WW) RADEON(0): Failed to set up write-combining range (0xe0000000,0x4000000)
(WW) RADEON(0): Enabling DRM support
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe3ffe000 is: 0xe3ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf07ff000
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
ubuntu@ubuntu:~$ glxinfo | grep irect
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
ubuntu@ubuntu:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
986 frames in 5.0 seconds = 196.981 FPS
1250 frames in 5.0 seconds = 249.785 FPS
1251 frames in 5.0 seconds = 249.984 FPS
ubuntu@ubuntu:~$
```

What could you advice me ?

---

### Post by amorgen on 2007-01-25
up please !

---

### Post by grim4593 on 2007-01-26
I have a similar "problem". I have a Radeon Mobility 9600/9700 with 64mb ram (windows says I have 64). In Ubuntu using the same tools as you it says I have 128. However elsewhere it says it only has 64. As far as I know this does not affect the computer at all. I was able to install the fglrx driver fine:

grim@LTUZ0529:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

