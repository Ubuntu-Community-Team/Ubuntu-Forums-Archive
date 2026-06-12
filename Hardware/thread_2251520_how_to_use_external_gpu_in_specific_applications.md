---
title: "how to use external gpu in specific applications"
date: 2014-11-04
forum: Hardware
---

### Post by canavaroski90 on 2014-11-04
hi all,

my current laptop has hybrid gpu system. one of them is intel's hd3000, integrated in CPU, and the another one is amd 7690m xt. trying to enable hybrid graphics architecture by using vga_switcheroo and fglrx drivers but no luck. when i install fglrx drivers, black screen welcomes me on next reboot. 

how can i use amd in order to get more power in some specific applications? it doesnt have to be in use all the time, just need amd for redering and games.


```
lsb_release -a;
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


uname -a;
3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



```

thanks.

---

### Post by QIII on 2014-11-04
Hello!

Vga_switcheroo does not work with the proprietary ATI driver.  You should not have it installed and should use tbe default Radeon driver with vga_switcheroo.

However, Ubuntu now supports ATI hybrid graphics natively without the need for vga_switcherooin muxless systems.  [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

You will likely have to uninstall both the driver and vga_switcheroo and start again. I'm on the train or I'd walk you through the process from recovery mode.

What was happening before you installed the ATI driver?

---

### Post by canavaroski90 on 2014-11-05
hello,

thanks for your response.

i've tried apt-get install fglrx.... but no chance. i got black screen on reboot. i've got to remove fglrx drivers.

and also tried to install driver package via downloading ati catalyst 14.04 from amd's website, again, black screen. 

lastly, i've tried below window to select amd's fglrx driver, and again and again and again... black screen.

This is current status of additional drivers windows;
[IMG]http://i.imgur.com/WaaVdzb.png[/IMG]

i am not sure how to use amd's graphics card in applications which requires high gpu power. does ubuntu automatically selects and uses amd i.e. when i open a game? if it is, how can i be sure about that? i mean how can i check whether the application is using amd or integrated intels low power gpu?

this is lspci output (cutted for only gpus);

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT] (rev ff)
```


this is detailed information for VGA devices;
```
sudo lspci -v -s 01:00.0
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6730M/6770M/7690M XT] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: radeon


sudo lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 185e
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

```


and this is the only section that is related to VGA in lshw output, no information about AMD;
```
 sudo lshw -class display
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:53 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:6000(size=64)

```

and this is vga_switcheroo output;

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0

```


thank you for your help.

***Edit:***
do not know if it is causing my situation, however, a bug has been reported about *_**unknown header**_*. (when i try to get detailed information about amd with lspci it returns unknown header line )
[https://bugs.launchpad.net/ubuntu/+source/fglrx-pxpress/+bug/1315928](https://bugs.launchpad.net/ubuntu/+source/fglrx-pxpress/+bug/1315928)

---

### Post by QIII on 2014-11-05
OK.  Let's take a breather here and step back.  I think you have a bunch of stuff piled on, so let's see if we can't get you back to the default situation.  This is all from memory, so if you get any messages you don't understand or errors, stop!  Someone will be along shortly to point out what an absent-minded old fool I am if something is wrong.

Cut and paste the commands rather than trying to type them, please.

If you are not able to get into the Desktop at all, as you boot up, the instant you see the BIOS splash, hold down the shift key (to be honest, I'm not at my Linux machine so I can't remember if it is the left or right shift key).

That should get you to the GRUB menu if it would not otherwise show.

Now, you need to go to "Recovery" and select the option that says "Root with networking" or something like that.

You will drop to a command prompt.  You're system is mounted in read only, so you have to remount read/write so you can make changes.

```
mount -o remount,rw /
```


*** NOW REMEMBER:  You are in super-duper "I know what I'm doing" mode (you're root) so be very careful.  ***

If you can get to the desktop DON'T do the above.  Just use the terminal for the following.  Remember that from the terminal you will have to preface each of these commands with "sudo".

You need to uninstall the driver you installed from the AMD/ATI website.

```
amdconfig --uninstall
```

You may need to do the following depending on the state of your machine

```
/usr/share/ati/amd-uninstall.sh --force
```


Let me know if you get any errors or messages here.



Then, to be sure, you need to uninstall the driver from the repo since I think you have it both ways right now.

```
apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

Again, let me know if you get any errors or messages here.


Then add some stuff back if fglrx removed it

```
apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri
```
```
dpkg-reconfigure xserver-xorg
```
```
update-initramfs -u
```

Again, let me know if you get any errors or messages here.


And remove (in this case we are going to rename it in case you want to get at it later) any conf if it was created when you installed fglrx

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Again, let me know if you get any errors or messages here.

Finally, uninstall vga_switcheroo

```
apt-get remove vgaswitcheroo
```

This should get you cleaned up and back to a basic default installation with regard to the video driver.

Reboot and tell me what happens.

---

### Post by canavaroski90 on 2014-11-06
thank you for your detailed support.

actually i've been trying to install fglrx proprietary drivers for 1 week, so having a black screen after fglrx installation, removing it, on next reboot be able to get desktop is became a default routine for me. when i get black screen i open terminal with CTRL + ALT + F1, removing fglrx with following command, and reboot the machine. it automatically installs open-soruce radeon drivers on next reboot, so i always be able to get desktop after removing fglrx drivers. moreover, i'm writing these on Xubuntu 14.04.

```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates[/FONT][/COLOR]
```

after that /usr/share/ati folder appears to be not removed and when i check inside there is nothing. (*actually just license.txt*) 

on the other as i mentioned above hand it recovers open-source radeon drivers and drops me directly to the desktop without an effort. so i do not need to run this;
```
apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri
```

even so, i've done it as you wish :))

and lastly, there is nothing installed as vga_swithcerooo, so;

```
 sudo apt-get remove vgaswitcheroo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vgaswitcheroo

```
then i wondered if there is a package as vgaswitcheroo or not and tried;
```
 sudo apt-get install vgaswitcheroo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vgaswitcheroo

```

now i'm using radeon drivers and be able to get desktop. just wonder can xubuntu switch between gpu units as it needs more gpu power? and can i check it? with the help of a software like GPU-Z ?

---

### Post by QIII on 2014-11-06
OK.  Let's move on then.

[This]("https://help.ubuntu.com/community/HybridGraphics") should give you the information you need for using vga_switcheroo.  But remember that using the open source Radeon driver means that not all of the GPU's capabilities are exposed.  Its performance may be limited.

If you want to go any further with the idea of using the proprietary driver (and it seems you experience is not good to this point...), you need to research your machine and find out if it is muxed or mux-less.  If it is multiplexed you won't be able to switch back and forth between the adapters using CCC -- even if you can install fglrx and get your machine to run.

I imagine you can start that research by googling ```
your OEM Model Linux mux
``` to see if there is some info out there indicating if it is muxed or not.  I don't have a list, unforutunately, or I'd let you know if it is muxed or not.  :)

Depending on the outcome of that research, we can either move forward or just live with vga_switcheroo.

---

