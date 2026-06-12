---
title: "lubuntu 11.04 screen quirks"
date: 2011-09-29
forum: Hardware
---

### Post by sdahlin on 2011-09-29
I decided to give lubuntu 11.04 a try.  However there are a couple of quirks that are making me reconsider and shift to xubuntu.  If I open a terminal window a black area opens up in the upper left corner of the screen which is the size of the terminal window.  I can run a window over the area to restore the background.  What is more irritating is that when I try to resize the terminal window the system behaves grindly slow!  It takes forever to respond to the mouse resizing.  [I have an Nvidia 7600 GT video card].

But what is even more irritating is that I can be running the internet and the system loses its connection to the net.  I have 2 network cards in the box.  Logging out and logging back in will not fix it.

I did not have these problems when I was running ubuntu on this box earlier.

Thanks

---

### Post by LinuxFan999 on 2011-09-29
Did you install the NVidia drivers?

---

### Post by amjjawad on 2011-10-01
> **sdahlin said:**
> I decided to give lubuntu 11.04 a try.  However there are a couple of quirks that are making me reconsider and shift to xubuntu.  If I open a terminal window a black area opens up in the upper left corner of the screen which is the size of the terminal window.  I can run a window over the area to restore the background.  What is more irritating is that when I try to resize the terminal window the system behaves grindly slow!  It takes forever to respond to the mouse resizing.  [I have an Nvidia 7600 GT video card].

But what is even more irritating is that I can be running the internet and the system loses its connection to the net.  I have 2 network cards in the box.  Logging out and logging back in will not fix it.

I did not have these problems when I was running ubuntu on this box earlier.

Thanks

Hi there,


1- What is your hardware specifications?

2- Are you running 32bit or 64bit?

3- Please post the output of:
```
sudo lshw -C display
```

This is my output and yours should be similar except for the driver:

```
*-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: **[COLOR=Red]driver=i915[/COLOR]** latency=0
       resources: irq:16 memory:e2100000-e217ffff ioport:c000(size=8) memory:d0000000-dfffffff memory:e2180000-e21bffff

```

4- What is the output of:
```
sudo lshw -C network

```

Please make sure when you post the output of any command to wrap up the text with "CODE" tags or select the text and click "#"

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

### Post by sdahlin on 2011-10-09
I am running x86_64.  As to the commands:

sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: G73 [GeForce 7600 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:34 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff ioport:dc00(size=128) memory:feae0000-feafffff

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: LNE100TX
       vendor: Lite-On Communications Inc
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth0
       version: 21
       serial: 00:a0:cc:3b:59:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.102 latency=64 multicast=yes
       resources: irq:29 ioport:e800(size=256) memory:febffc00-febffcff memory:feb80000-febbffff

I am not sure if it is the cause or is just a correlation but as to the video driver for my Nvida Card 7600GT I have installed the most current driver recommended.  However, it indicates that the driver is activated but not in use.  I have tried reinstalling and also tried the fallback 173 driver to no effect.  I have tweaked the boot parameters as suggested elsewhere such as adding "nopat" and "noacpi acpi=off" and then running update-grub.  I have also tried grabbing the kernel-headers-pae and kernel-image-pae as suggested.

The behavior of the term window and the the video glitches are really beginning to bother me.

---

### Post by sdahlin on 2011-10-13
bump

---

### Post by amjjawad on 2011-10-15
Hi and sorry for being late!

```
sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: G73 [GeForce 7600 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=**[COLOR=Red]nvidia[/COLOR]** latency=0
       resources: irq:34 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff ioport:dc00(size=128) memory:feae0000-feafffff

```
Quite honestly, I don't have Nvidia and not sure whether the driver that you have is the correct one but as far as I know, Additional Driver will offer you some choices.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

or [www.googlubuntu.com](www.googlubuntu.com) will help you to find more result.


```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: LNE100TX
       vendor: Lite-On Communications Inc
       physical id: 7
       bus info: pci@0000:04:07.0
       logical name: eth0
       version: 21
       serial: 00:a0:cc:3b:59:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.102 latency=64 multicast=yes
       resources: irq:29 ioport:e800(size=256) memory:febffc00-febffcff memory:feb80000-febbffff

```

I see you are connecting to the internet via Wired Connection. 

See this post: [http://ubuntuforums.org/showpost.php?p=10983947&postcount=5](http://ubuntuforums.org/showpost.php?p=10983947&postcount=5)

Try it, it might help.


> The behavior of the term window and the the video glitches are really beginning to bother me.

Have you tried Lubuntu 11.10? at least from LiveCD or LiveUSB?
It has the Kernel 3 and perhaps that will help you to fix the issue but I'm not sure.

---

