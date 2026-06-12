---
title: "hp dv6t select edition - hardware bugs"
date: 2010-07-19
forum: Hardware
---

### Post by blackicepro on 2010-07-19
I've just purchased a HP dv6t select edition ([http://www.shopping.hp.com/series/category/notebooks/dv6tse_series/3/computer_store](http://www.shopping.hp.com/series/category/notebooks/dv6tse_series/3/computer_store))

I'm currently using ubuntu 10.04 and i'm having issue with the trackpad, since the buttons are apart of the trackpad, it's pretty much impossible to drag and drop because when ubuntu detects 2 fingers on the trackpad, the mouse jumps around the screen.

Also, since the intel core i5 processor has GPU capability and there's a dedicated ATI graphics card on this computer, I don't know which GPU it's using. I tried to install the ATI restricted drivers, but after rebooting I get a black screen so I used the nomodeset option in grub's boot parameters and the display works again, but when I try to install the ATI drivers again, it crashes ([https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573748](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573748)). This laptop has been running extremely hot, so I want to either disable the ATI graphics card and use the intel GPU or be able to limit the power usage on my ATI graphics card. I can't even tell if it's using the Intel GPU or the ATI one.

Here's lspci:
> 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



Anyone else having these same problems or have a fix to these issues?
Thanks.

---

### Post by elricscripts on 2010-07-19
> **blackicepro said:**
> ...impossible to drag and drop...

I couldn't find any related issues or open bugs.  Here's a forum thread on disabling the touchpad.  And other Ubuntu users utilizing it.
[http://ubuntuforums.org/showthread.php?t=1457349](http://ubuntuforums.org/showthread.php?t=1457349)
[http://ubuntuforums.org/showthread.php?t=1119071](http://ubuntuforums.org/showthread.php?t=1119071)


And Ubuntu help
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)




Hope you find a solution.

---

### Post by blackicepro on 2010-07-19
> **elricscripts said:**
> I couldn't find any related issues or open bugs.  Here's a forum thread on disabling the touchpad.  And other Ubuntu users utilizing it.
[http://ubuntuforums.org/showthread.php?t=1457349](http://ubuntuforums.org/showthread.php?t=1457349)
[http://ubuntuforums.org/showthread.php?t=1119071](http://ubuntuforums.org/showthread.php?t=1119071)


And Ubuntu help
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)




Hope you find a solution.

Thanks for the help. I think I'll stick to windows for a bit until bug fixes are released. If anyone have work arounds for these issues, please post.

---

### Post by zero7404 on 2010-07-19
i'd be interested in finding out more as well, i just got an Envy 17, similar hardware config, although the trackpad is a single smooth surface, it has 2 traditional clicks (left click, right click).

---

### Post by blackicepro on 2010-07-20
I've found a post that solved the mouse jumping, right click, drag and drop issue.
[http://ubuntuforums.org/showthread.php?t=1388164](http://ubuntuforums.org/showthread.php?t=1388164)

Edit: nevermind, this doesn't seem to work very well.... 
[http://ubuntuforums.org/showpost.php?p=8816327&postcount=6](http://ubuntuforums.org/showpost.php?p=8816327&postcount=6) will fix the issues but you can't scroll or change mouse sensitivity, [http://ubuntuforums.org/showpost.php?p=9158330&postcount=30](http://ubuntuforums.org/showpost.php?p=9158330&postcount=30) didn't do anything for me, and [http://ubuntuforums.org/showpost.php?p=9250735&postcount=43](http://ubuntuforums.org/showpost.php?p=9250735&postcount=43) wasn't too good either. I couldn't use the 2 finger scroll option or right click. There's a very useful man page [http://manpages.ubuntu.com/manpages/lucid/man1/synclient.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/synclient.1.html), if there's a custom setting that works for you, please post.

---

### Post by blackicepro on 2010-07-20
I also managed to figure out which graphics card it's using by installing sysinfo.

---

### Post by elricscripts on 2010-07-22
> **blackicepro said:**
> I also managed to figure out which graphics card it's using by installing sysinfo.

Sounds like you're getting closer, congrats!  I finally found the site that helped me to setup my HPtx2000, however i couldn't find the dv6t.  Hopefully it will be added in the near future:

[https://wiki.ubuntu.com/Testing/Laptop](https://wiki.ubuntu.com/Testing/Laptop)
[https://wiki.ubuntu.com/LaptopTestingTeam/Old/HewlettPackard](https://wiki.ubuntu.com/LaptopTestingTeam/Old/HewlettPackard)

---

### Post by blackicepro on 2010-07-22
> **elricscripts said:**
> Sounds like you're getting closer, congrats!  I finally found the site that helped me to setup my HPtx2000, however i couldn't find the dv6t.  Hopefully it will be added in the near future:

[https://wiki.ubuntu.com/Testing/Laptop](https://wiki.ubuntu.com/Testing/Laptop)
[https://wiki.ubuntu.com/LaptopTestingTeam/Old/HewlettPackard](https://wiki.ubuntu.com/LaptopTestingTeam/Old/HewlettPackard)

Thanks for the links, I'll check regularly. Since this laptop model just came out in May 2010, it'll take a while for updates to come around.

---

### Post by zero7404 on 2010-07-22
is there no option to turn the trackpad off completely when an external mouse is in use ?

---

### Post by blackicepro on 2010-07-23
> **zero7404 said:**
> is there no option to turn the trackpad off completely when an external mouse is in use ?

I've been using an external mouse, however mobility is important to me and it's annoying to carry an extra mouse and pull it out each time when I want to use my laptop.

---

### Post by blackicepro on 2010-08-18
[http://ubuntuforums.org/showpost.php?p=9734605&postcount=19](http://ubuntuforums.org/showpost.php?p=9734605&postcount=19)

Trackpad is now usable, see this post.

I'm still having problems with dual GPUs and heating issues.

---

### Post by Chris1274 on 2010-08-19
I've been having the exact same graphics issues on my dv6t SE. The ATI proprietary driver crashes the system, so I've been using the default driver, but trying to toggle between X and tty causes it to lock up.

---

### Post by Chris1274 on 2010-08-20
Apparently there's a thing called "vga switcheroo" that allows you to switch between the integrated and dedicated gpu's. Have a look at this guy's blog, where he mentions it:

[http://www.andreas-demmer.de/en/2010/07/18/testbericht-linux-auf-dem-hp-envy-14/](http://www.andreas-demmer.de/en/2010/07/18/testbericht-linux-auf-dem-hp-envy-14/)

Unfortunately it seems to be available only for the 64-bit kernel :(

---

### Post by Chris1274 on 2010-08-24
> **blackicepro said:**
> [http://ubuntuforums.org/showpost.php?p=9734605&postcount=19](http://ubuntuforums.org/showpost.php?p=9734605&postcount=19)

Trackpad is now usable, see this post.

I'm still having problems with dual GPUs and heating issues.

I *think* I've stumbled upon a way to disable your ATI video card. Since adding:

```
radeon.modeset=0
```

to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, the syslog no longer shows some items mentioning "radeon" at startup. My bootup time has also sped up quite significantly.

---

### Post by Chris1274 on 2010-08-24
Yes indeed, I believe that fix does work.

```
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
    Subsystem: Hewlett-Packard Company Device 144a
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at a0000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at c4400000 (64-bit, non-prefetchable) [disabled] [size=128K]
    I/O ports at 4000 [disabled] [size=256]
    Expansion ROM at c4440000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon
```

---

### Post by mathgeek618 on 2010-08-29
Hi,

First of all, thanks for the tips/links here! I think this is where I first discovered vga_switcheroo in Googling.

I've got the dv6tse, running 64-bit Lucid.

Graphics: Initially, running a 2.6.32 kernel, I couldn't figure out exactly what was going on with the graphics cards, other than that the fglrx driver currently can't handle hybrid graphics and that power consumption was really bad. I really wanted to try the vga_switcheroo thing though, so I started playing with kernels from the Ubuntu Kernel PPA ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)). 2.6.34-lucid didn't have vga_switcheroo enabled, so I installed 2.6.35-maverick and got vga_switcheroo working nicely. I've been able to disable the discrete - I did try it, but the driver doesn't work so Compiz didn't start up - and power it off, and I think I'm seeing better battery life, although that is possibly mostly psychological. [Currently, from 100%, I'm at 30% and have gotten 1:45 out of the standard 6-cell battery with full brightness; I have yet to measure with both cards powered on.]

Touchpad: On a clean install, I could do edge scroll, the double-tap drag thing (is there a technical term for that?), left-click taps, left-click hard click, and right-click hard click. I could not do two-finger scrolling at all, although if my two fingers were close enough to each other the pointer didn't jump. I could also do hard-click left+drag, with two fingers on the trackpad, without jumping, provided the clicking finger was close enough to the edge. With the 2.6.35-maverick, I can do edge scroll, still no two-finger, left-click hard and soft, and only soft right-click in the right-click corner, which sometimes causes a scroll and then a right-click. The scrolling also seems to be faster than it was before. On all kernels, I've noticed that the disable-while-typing feature isn't always spot-on, as my sentences occasionally jump up a line or two to where the pointer is.

I'm thinking I'll stay with the 2.6.35, as I'll probably mostly be using an external mouse and battery life is more important to me than the trackpad, which works when needed, albeit sometimes annoyingly. I'll update in a few days when I have more battery numbers.

Has anyone has any luck with the trackpad, though? ... I would love to be able to use the multitouch, even if it's only the emulated version for scrolling.

---

### Post by ak9tyOne on 2010-08-30
I recently purchased this laptop as well and it should arrive soon (sig below is optimistic). Anyways is the touchpad MT-enabled? In otherwords does this fix work? [http://ubuntuforums.org/showthread.php?t=1334696]("http://ubuntuforums.org/showthread.php?t=1334696")

---

### Post by mathgeek618 on 2010-08-30
> **ak9tyOne said:**
> In otherwords does this fix work? [http://ubuntuforums.org/showthread.php?t=1334696]("http://ubuntuforums.org/showthread.php?t=1334696")

Not for me. I did run across this posting asking for help testing the Maverick MT library, but I'm not actually running Maverick (yet?) so I don't know if it works.

[http://ubuntutesting.wordpress.com/2010/08/30/testing-your-multitouch-device/](http://ubuntutesting.wordpress.com/2010/08/30/testing-your-multitouch-device/)

---

### Post by mathgeek618 on 2010-08-30
> **mathgeek618 said:**
> Currently, from 100%, I'm at 30% and have gotten 1:45 out of the standard 6-cell battery with full brightness; I have yet to measure with both cards powered on.

I've finished my informal benchmarks. Using the standard 6-cell battery, with screen at full brightness, I get about:
[INDENT]only integrated: 2.5
both cards: 2[/INDENT]
hours of battery life.

---

### Post by ak9tyOne on 2010-09-02
i just got my laptop today. i was surprised to find that the trackpad worked out of the box with two finger scrolling using the clickable buttons. I did not think this was the case. Anyways, now i just need two finger scrolling and ill be happy.

---

### Post by mathgeek618 on 2010-09-03
I also just noticed that the mute button light now works correctly. I'm not sure exactly what caused this, but I would guess it's the 2.6.35 kernel.

---

### Post by xpartmgr on 2010-09-07
I just got my DV6T last week. I have used Ubuntu on my old laptop but not as a primary OS. I enjoy messing with it but this new laptop does not play well with it. I also had the problem of allowing Ubuntu to install the ATI driver and getting the black screen. I installed Ubuntu inside windows instead of having a dual boot setup. I was confused when I installed it because the drive already shows a bunch of partitions. I didn't want to mess up anything that already existed.

Anyway, I would like to know how to get that ATI driver to work? I have no idea what to do. I hear people talking about changing GRUB and such but do i even have that because of the type of install I did? If I do can someone please tell me how to get into it and make the changes. I am a rookie so please be specific. 

I am also having the touchpad issue. I am about to return this laptop because i really dislike that touchpad...even in windows I hate it. 

Thanks for any help you can offer.

---

### Post by blackicepro on 2010-09-26
> **Chris1274 said:**
> I *think* I've stumbled upon a way to disable your ATI video card. Since adding:

```
radeon.modeset=0
```

to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, the syslog no longer shows some items mentioning "radeon" at startup. My bootup time has also sped up quite significantly.

This works for me, but it's still quite hot (maybe that's because I just changed the grub boot parameters).

---

### Post by Chris1274 on 2010-09-26
It's been awhile since I dealt with these issues since I sent my dv6t back to HP, but as I recall, upgrading to the 2.6.34 kernel solved the graphics issues. I was able to go back and forth between X and the virtual consoles with no problems. 2.6.35, on the other hand, messed things up again. Honestly, I have no real idea what that radeon.modeset=0 actually does; I'm not sure if it actually disables the ATI card or just changes something in the boot paramters, but it got rid of some error messages in the syslog, so that was a plus.

That whole experience taught me to avoid ATI video cards and just stick with integrated graphics, which is all I need anyway.

---

### Post by blackicepro on 2010-11-16
After updating to 10.10, the touchpad stopped working. I can't right click and the mouse jumps if i put more than one finger on it.

:(

---

