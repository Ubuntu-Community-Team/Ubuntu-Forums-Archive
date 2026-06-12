---
title: "No display output on ACER Veriton N281G"
date: 2020-02-07
forum: Hardware
---

### Post by lundo on 2020-02-07
I reformatted the Windows disk in this old Acer and installed Bionic Beaver. On the monitor connected to the single VGA output, I see the grub menu and ubuntu boot progress dots. Then, when boot is complete, the display shows an empty desktop with the beaver background. I can slide the cursor off-screen to the left, so it appears as though ubuntu considers this display "display 2", and the icons and menu are being "output" to some virtual non-existent display. I can't access any controls. Right-click on this empty desktop allows me to launch Terminal, but of course it's shown on the "main" invisible screen. So there's little I can do. Could there be anything I can alter in the internal hardware, a jumper or something, which would solidify this VGA port as THE one and only display to use? Has anyone seen anything like this before?

---

### Post by CelticWarrior on 2020-02-08
It has HDMI and VGA.
 
Do you have something conneceted to the HDMI port?
UEFI or Legacy install?
Also check the UEFI (&#8220;BIOS&#8221;) settings. Either it has some sort of virtual display enabled or the VGA output needs to be set as primary.

---

### Post by lundo on 2020-02-08
The Acer N281G has only the single VGA port, no HDMI. As I mentioned, the boot output and progress are displayed on the VGA-connected monitor, so it seems to be the primary display with respect to the boot/BIOS code. Once it boots and I am auto-logged in, I'm seeing display #2 and all output goes to some sort of virtual display.

---

### Post by CatKiller on 2020-02-09
> **lundo said:**
> The Acer N281G has only the single VGA port, no HDMI.

Many images of that device, such as [this one](https://www.acer.com/ac/en/ID/content/support-product/3235[/url), show an HDMI port between the VGA port and the network port. It's not clear from other pictures whether that port is covered or blanked on some models.

xrandr will show you the outputs that are being detected by your Ubuntu install. You should be able to use something like ```
xrandr --output VGA --primary
``` to make the VGA one primary, which should help you configure it all, whether there's really another output or the computer just thinks there is.

---

### Post by lundo on 2020-02-09
Thanks for that command! I wound up taking the solution I've often criticized others for doing too quickly, the old "wipe the disk and re-install". Basically, when I booted from an installation medium, the desktop appeared fine. So I knew it was a software, not a hardware issue. Reinstalling Bionic Beaver from scratch eliminated the problem, so something in the old install was apparently botched.

---

