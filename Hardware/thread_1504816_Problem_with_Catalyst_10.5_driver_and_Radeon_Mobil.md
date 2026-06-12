---
title: "Problem with Catalyst 10.5 driver and Radeon Mobility 4550"
date: 2010-06-08
forum: Hardware
---

### Post by benjamimgois on 2010-06-08
Recently i got a new Laptop HP dv4-2080br. It's a core i5 with Radeon Mobility HD 4550. I'm having problems with the oficial ATI Drivers, after installing fglrx with Jockey or the version downloaded from ATI/AMD site the screen just goes black after the reboot. I already tried Catalyst 10.3 , 10.4 and 10.5 but all of then give me the same result, black screen. The strange thing is that Mobility 4550 is listed as supported by this driver. I'm using Lucid 64bit.

I check the X.org log and it seens that it has an invalid ATI BIOS. Please anyone has any idea of what is happening ?

/var/log/Xorg.1.log

[PHP](II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
	Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.11
(II) ATI Proprietary Linux Driver Version Identifier:8.72.11
(II) ATI Proprietary Linux Driver Release Identifier: 8.723.1                              
(II) ATI Proprietary Linux Driver Build Date: Apr  8 2010 21:40:58
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9555) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x1a855e0
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 11, (OK)
ukiOpenByBusid: ukiOpenMinor returns 11
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4500 Series " (Chipset = 0x9555)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x1409)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xe8400000
(--) fglrx(0): I/O port at 0x00006000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Bad V_BIOS checksum
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitAdatper failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "fglrxdrm"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(II) UnloadModule: "fglrxdrm"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found[/PHP]

---

### Post by dpezely on 2010-06-23
Just above the first "(EE)" error message in your log is "[COLOR=#000000][COLOR=#0000bb]Bad V_BIOS checksum[/COLOR][/COLOR]" which may be the real problem.  

Consider using a generic driver to least make X11  functional, albeit with reduced resolution, color depth and without  acceleration.  That is, rather than potentially use the wrong ATI driver, consider the  default "vesa" or "vga" driver.  At least, this should confirm whether the issue is a bad Video BIOS versus insufficient proprietary driver for  your machine's particular mix of chips.

Should that confirm a corrupt Video BIOS: HP is usually good about providing BIOS updates, from what I recall.  Try updating firmware, and contact HP directly if unable to find an installer that specifically mentions "video BIOS" or similar wording.  (I don't currently own/use HP gear so can't be more precise here.)


Also, yet another update from ATI is available: 10.6

This URL seems to forward to the right page: [http://www.ati.com/drivers/linux/](http://www.ati.com/drivers/linux/)

---

### Post by benjamimgois on 2010-06-23
> **dpezely said:**
> Just above the first "(EE)" error message in your log is "[COLOR=#000000][COLOR=#0000bb]Bad V_BIOS checksum[/COLOR][/COLOR]" which may be the real problem.  

Consider using a generic driver to least make X11  functional, albeit with reduced resolution, color depth and without  acceleration.  That is, rather than potentially use the wrong ATI driver, consider the  default "vesa" or "vga" driver.  At least, this should confirm whether the issue is a bad Video BIOS versus insufficient proprietary driver for  your machine's particular mix of chips.

Should that confirm a corrupt Video BIOS: HP is usually good about providing BIOS updates, from what I recall.  Try updating firmware, and contact HP directly if unable to find an installer that specifically mentions "video BIOS" or similar wording.  (I don't currently own/use HP gear so can't be more precise here.)


Also, yet another update from ATI is available: 10.6

This URL seems to forward to the right page: [http://www.ati.com/drivers/linux/](http://www.ati.com/drivers/linux/)

Thanks for the answer, but it seens to be a bug that's affecting many other people with core i3,i5 and Radeon Graphics. A bug is already open in launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/430919](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/430919)

---

### Post by hsantanna on 2010-09-14
Here is [my post at Phorolix]("http://www.phoronix.com/forums/showthread.php?p=145549#post145549") about my bad experience with HP DV-4 2080BR (ATI Radeon Mobility HD 4550) on Ubuntu:

> 
I have a very similar problem: can't get fglrx to work because I always get into a blank screen. I'm unsuccessful trying to install fglrx since Catalyst 10.3 (now 10.8 ), on my new HP Pavilion DV-4 2080BR.

The problem in my case, and maybe yours, is that the Intel Core CPU (i3/i5/i7) have integrated graphics, and since I bought a notebook model that also have discrete ATI GPU, in a way that I have 2 GPUs at same computer, with the infamous 'switchable' option.

The bad thing is that Linux kernel is just starting to support switchable graphics, and worst, Xorg totally don't support it.

Be best (fast) solution would be to disable the switchable thing at BIOS, enabling only the ATI GPU. But to my bad luck, that's not an option to me, because there is no HP notebook with BIOS option about switchable graphics.

So fglrx detects something that it don't understand, and, so, I get the black screen thing.

I e-mailed HP asking them for a new BIOS version to disable Intel integrated GPU, so I would get only the ATI GPU detected by my favorite OS.
HP replied saying something that seems to be wrote by a bad-programed-robot, with all nonsense phrases, just copying and pasting my own words from the initial message.
So I replied their response asking for someone that understand what BIOS is. Some days later, a guy e-mailed me, he said that HP will not release a new version of BIOS, and if HP does, it will not contain the switch-off integrated graphics feature. dot.

The good thing is that I still can have hardware accelerated graphics from the i5's GPU. Intel have much better linux driver support than ATI. My KDE works beauty with all those transparency and animations.
Sad that I paid/waist $500 more on this notebook model just because of the ATI GPU and I can't use it. 

I will have better luck on the next buying, keeping away from HP and ATI. Maybe a [Dell]("http://www.dell.com/ubuntu") with [Ubuntu]("http://www.ubuntu.com/dell").


---

### Post by nando4 on 2010-09-18
> **hsantanna said:**
> Here is [my post at Phorolix]("http://www.phoronix.com/forums/showthread.php?p=145549#post145549") about my bad experience with HP DV-4 2080BR (ATI Radeon Mobility HD 4550) on Ubuntu:

If you want to try a different solution, download the latest bios, run PhoenixTool on the bios, then run the following on one of the extracted files:
```
ndisam -a -b 16 4FA68826-0CA1-4D05-A4F0-EE9C1EA42F06_2_695.ROM > out.dis
```In out.dis you'll see references to the systemboard ID. The systemboard ID is stored somewhere but even the DMI tools don't give access to it. So the workaround is to modify the BIOS code to apply the code for the non-switchable graphics option:

```
000006F6 B80A14 mov ax,0x140a    :: 0x140a = HP DV4 (HD4550)
0000071A B81414 mov ax,0x1414    :: 0x1414 = Compaq CQ41 (HD4350)
000007F9 B80914 mov ax,0x1409    :: 0x1409 = HP DV4 (HD4550 + Intel HD)
```So in your case you could swap the B80A14 and B80914 OPCODES, recreate the bios using PhoenixTool and flash and hopefully that would give you ATI-only graphics.

The DSDT table also has references to 1409 which creates the ACPI switchable graphics options which would might also require setting to 140a. As always take appropriate precautions if attempting such a mod as could otherwise brick your system.

---

### Post by Carl.Spackler on 2010-09-18
Another hybrid/switchable graphics laptop. It seems these are becoming more popular. Not sure if this applies but you may want to look at this blog entry:
 
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
 
I have a dv7-4060us that has the ATI/ATI combination. Yours appears to have the ATI/Intel combo. Either way the link above may be able to help. 
 
BTW, this is built into the current Maverick kernel.

---

### Post by hsantanna on 2010-09-26
> **nando4 said:**
> If you want to try a different solution, download the latest bios, run PhoenixTool on the bios, then run the following on one of the extracted files:
```
ndisam -a -b 16 4FA68826-0CA1-4D05-A4F0-EE9C1EA42F06_2_695.ROM > out.dis
```In out.dis you'll see references to the systemboard ID. The systemboard ID is stored somewhere but even the DMI tools don't give access to it. So the workaround is to modify the BIOS code to apply the code for the non-switchable graphics option:

```
000006F6 B80A14 mov ax,0x140a    :: 0x140a = HP DV4 (HD4550)
0000071A B81414 mov ax,0x1414    :: 0x1414 = Compaq CQ41 (HD4350)
000007F9 B80914 mov ax,0x1409    :: 0x1409 = HP DV4 (HD4550 + Intel HD)
```So in your case you could swap the B80A14 and B80914 OPCODES, recreate the bios using PhoenixTool and flash and hopefully that would give you ATI-only graphics.

The DSDT table also has references to 1409 which creates the ACPI switchable graphics options which would might also require setting to 140a. As always take appropriate precautions if attempting such a mod as could otherwise brick your system.

nice to know that, i probably will try anytime. it is the first realizable solution that i sow around.

thank you for sharing! :KS

---

### Post by benjamimgois on 2010-09-26
> **hsantanna said:**
> nice to know that, i probably will try anytime. it is the first realizable solution that i sow around.

thank you for sharing! :KS

Yeah, really impressive ! Please if you give it a try post the results here. Maybe we can redistribute a new BIOS to fix the problem.

---

