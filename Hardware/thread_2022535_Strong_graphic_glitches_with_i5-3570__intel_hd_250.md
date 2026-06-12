---
title: "Strong graphic glitches with i5-3570 / intel hd 2500"
date: 2012-07-11
forum: Hardware
---

### Post by vr164 on 2012-07-11
Dear community

I am using Ubuntu for quite a while now (>5 yrs). Recently I updated my cpu to an intel core i5 3570 with a hd 2500 iGPU. I also got me a new mainboard (Asus P8H77-i).

Right from the start I experienced very rough graphical glitches when starting X (lightdm). So in a first step I tried to switch to Unity 2D (no changes). I updated the bios to the latest version and I changed the kernel to 3.5.0rc6. I also installed mesa-utils.

Still the glitches came back. The weird thing. Altough the glitches show on lightdm, _sometimes_ I can start Unity2D and work on it.

uname -r
3.5.0-030500rc6-generic

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)

I also see a lot of errors like that in syslog:
Jul 11 10:04:35 rongerik kernel: [   53.692124] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung

anyone with an idea?

---

### Post by Ubun2to on 2012-07-11
Why do you have a 3.5 kernel? 12.04 is shipped with 3.2.0-23.36, and I have 3.2.0-26 due to updates (and I just checked for updates).
Anyway, you say your graphics are Intel HD 2500? I think Linux has drivers for all Intel chips already. A common misconception about Intel HD Graphics is that they have their own GPU. Wrong. That is just another way of saying Integrated Graphics. The primary reason they switched names was because they didn't want them to be thought of as Integrated Graphics, as they are infamous for performing well with NT Pinball and nothing else.
You said you switched to a new motherboard. Do you have the proper BIOS installed? Each motherboard has its own BIOS, as no two motherboards have the same ports, speed, fans, layout, and controller. You will most likely have to flash a new BIOS downloaded from the Asus website ( [http://www.asus.com/Motherboards/Intel_Socket_1155/P8H77I/#download](http://www.asus.com/Motherboards/Intel_Socket_1155/P8H77I/#download) ), unless there is a generic one (which is highly unlikely considering how proprietary each one is).
I found a site that tells how to flash a new BIOS:
[http://www.ehow.com/how_7256759_update-bios-ubuntu.html](http://www.ehow.com/how_7256759_update-bios-ubuntu.html)
If flashing a new BIOS doesn't help (or you already flashed a new BIOS), you might just have compatibility issues between the motherboard and the CPU (you said you have Intel graphics-they don't use a separate GPU; they use the CPU). If that is the case, you might have to reinstall the Intel drivers ( [http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Processor+graphics&ProductProduct=2nd+Generation+Intel%C2%AE+Core%E2%84%A2+Processors+with+Intel%C2%AE+HD+Graphics+3000%2f2000](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Processor+graphics&ProductProduct=2nd+Generation+Intel%C2%AE+Core%E2%84%A2+Processors+with+Intel%C2%AE+HD+Graphics+3000%2f2000) ). The Linux drivers are at the bottom of the OS list.
I hope this helps.

---

### Post by megafluffles on 2012-08-02
I am having the exact same problem and have the same CPU, but on an ASUS P8H61-MLE, also running 12.04.

Have you been able to find a fix? I only got my computer tonight, so haven't tried much yet. I think I will check for BIOS upgrades next.... Will report back if I find a fix.

---

### Post by megafluffles on 2012-08-03
Fix this by doing the following:

/etc/default/grub, edit that and find GRUB_CMDLINE_LINUX_DEFAULT, add your nomodeset and update grub:
sudo grub-mkconfig -o /boot/grub/grub.cfg

(Taken from [http://www.overclock.net/t/1283237/ubuntu-installation-issue/50](http://www.overclock.net/t/1283237/ubuntu-installation-issue/50))

---

### Post by vr164 on 2012-11-02
Thank you for your suggestions.

As for myself, I helped myself out by buying a new GFX. Now the system is running smooth.

Yours,
Sven

---

### Post by abferber on 2012-12-07
Got the same Prob here with 12.04 i just updated to  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4-precise/)
works 
the only problem ive Recognized the ufw Firewall wont start automatically.

---

### Post by Dumaxa on 2013-05-28
same trouble. how to fix? (i5-3570 \ p8z77-v)

---

### Post by SonnyE on 2013-06-03
Similar problem. Graphic glitches that make almost everything unreadable except webpages in the Chromium browser window, from booting in legacy BIOS mode to an old Lubuntu 12.04 x86 CD, on a Lenovo H430 desktop (i5-3330 which is an x64, HD Graphics 2500, Intel H61 Express chipset.)


I tried this boot only as a first test of Linux on this new computer that was convenient because I already had the CD.

_______
update: I'm using Ubuntu 13.04 amd64 right now instead and there are no problems with graphics.

(I used LinuxLive USB Creator in Windows 8 to write the iso to USB, because Pen Drive Linux's Universal USB Installer, recommended by [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows), says on its webpage that it requires "[COLOR=#0066ff]**Windows XP/Vista/7 or WINE** to create the USB[/COLOR][COLOR=#000000]" then I booted from l[/COLOR][COLOR=#0066ff][/COLOR]egacy BIOS mode the same as before.)

---

