---
title: "Ubuntu freezes if mouse doesn't move"
date: 2009-06-25
forum: Hardware
---

### Post by sirbobbinhood on 2009-06-25
Hi I have a laptop that I just recently installed Ubuntu on and there is a major obnoxious problem. If I don't move my mouse every 5 or 10 seconds the whole laptop will freeze. When you move the mouse after it has frozen it starts to work again but my wireless card stops working. Everything looks like it should be fine but I can't communicate with anything. This is a major problem especially when I am downloading updates because I have to sit at my computer for an hour and a half moving my mouse non-stop. I have an intel 4965 wireless card and an elantech touchpad on my laptop if you need anymore info I can get it for you.

---

### Post by AnWe on 2009-07-08
I have a similar problem on my Clevo M720R laptop, although it might not be the exact same problem. I'm not sure it is directly related to the wlan, my problem seems to also occur using the wired interface. I can see no errors in the syslog or dmesg that relates to this.

The processor seems to sleep while the error occurs, I've noticed the clock on my machine slacking behind after some time in use. I just noticed even the animated smilies to the right when posting stopped for a while... Even runnning downloads through e.g. aptitude freezes.

I can "wake" the system by using some kind of input (keyb. mouse), guessing there might be som IRQ-problem or maybe related to powersaving, but as I have no error messages I'm stabbing in the dark. It's also very hard to search for bug reports, I don't know where to start...

I tried some different kernels from Karmic, but it's still there. The latest 2.6.31-2 kernel broke graphics in X-windows, so I temporarily gave up on that.

Anyone else with this kind of problem?

I'm gonna try to reproduce the bug using only the console, ruling out X and network activity, have to find a suitable app first though... I'll also try a memtest over      night to see if I maybe have a bad module.

My hardware is:
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:07.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
0c:07.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
0c:07.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
0c:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)



/Andreas

---

### Post by AnWe on 2009-07-19
I think my problem comes down to dodgy cooling. I have a Clevo m72r laptop, and the chipset heatsink (if you can call it that, it's a thin sheet of copper) wasn't seated correctly. I reseated it and now things seem to be snappier. I have yet to test extensively though.

If you have the nerve (it's probably not that difficult if you have basic mechanics skills, depends on the computer construction), I'd recommend you open your computer and check the heatsink(s). Have some thermal paste handy if you need to reseat a heatsink, they may be done with thermal pads that may break if you remove them.

PS. I'm considering drilling some andair holes in the cpu/chipset cover, there are no intake vents att all on my computer!? The case designer must have failed basic physics... 

/Andreas

---

### Post by sirbobbinhood on 2009-09-27
I don't think that is the problem I've never had a heating problem and I've pushed the laptop pretty hard. I know I fixed it once but I can't remember how. I think it was a video problem where the video card would freeze and then it would throw off the wireless card as well.

---

### Post by AnWe on 2009-10-05
I *think* i might have solved my problem. It was not the cooling as i thought, might have been a kernel upgrade that made it less obvious, but later the problem returned.

I then found an error message in the logs that looked suspicous, see [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798)

I tried "clocksource=acpi_pm" in kopts in /boot/grub/menu.lst (see bug for details) and that seems to have worked so far (knock on wood). YMMV, so do a "cat /sys/devices/system/clocksource/clocksource0/available_clocksource to see what your options are. I only had hpet and acpi_pm to choose from.

I have only done a quick reboot, so I can't be sure it's gone for good this time, but i have yet to see a freeze. Normally I'd see a freeze during boot. 

Next thing is to try wifi, it was next to unusable before with disconnects all the time, hope things have changed...


/Andreas

---

### Post by AnWe on 2009-10-11
Nope, that didn't solve things either...
I think it's slightly better using "hpet=disable" or "clocksource=acpi_pm", but the pauses/freezes are still there. I'm using an RT-enabled kernel from Ubuntu Studio (2.6.31-6-rt) which may affect things, but not sure, I'm gonna compare with a standard kernel and see.

I'm tempted to file a bug report, but I've no idea what package to file against... next to impossible to know what causes this.

/Andreas

---

