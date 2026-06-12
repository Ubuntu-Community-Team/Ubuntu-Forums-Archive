---
title: "[SOLVED] New motherboard- Do I need to install drivers - other questions"
date: 2009-01-06
forum: Hardware
---

### Post by sofasurfer on 2009-01-06
I just bougt a new motherboard because my old one died. Just bought a MSI K9N6PGM2. I fired up th pc and it seems to work properly although I have not configured the BIOS settings yet. My questions are...

 Since I have not install the included drivers from the cd, what is in the motherboard? 

Is the motherboard sold with all the cd software already installed, and the cd is just in case I need to reload them? 

Or is the MB loaded with only enough to get it started?

The 2 cds included with the MB are "drivers and utilities for WinXP" and "drivers and utilities for Win Vista". Since I am going to run Linux, whats the differance? 

Aren't the motherboard drivers completely independant of the operating system?

---

### Post by Zeroberry on 2009-01-06
Can't guarantee you 100% that everything works perfect but generally you wont need to manually install any drivers. Welcome to Ubuntu.

---

### Post by oilchangeguy on 2009-01-06
> **sofasurfer said:**
> I just bougt a new motherboard because my old one died. Just bought a MSI K9N6PGM2. I fired up th pc and it seems to work properly although I have not configured the BIOS settings yet. My questions are...

 Since I have not install the included drivers from the cd, what is in the motherboard? 

Is the motherboard sold with all the cd software already installed, and the cd is just in case I need to reload them? 

Or is the MB loaded with only enough to get it started?

The 2 cds included with the MB are "drivers and utilities for WinXP" and "drivers and utilities for Win Vista". Since I am going to run Linux, whats the differance? 

Aren't the motherboard drivers completely independant of the operating system?

no these drivers are not installed in the mobo. the cd's include drivers for such things as the chipset, onboard video, audio, and maybe usb. to name a few. and windows may or may not have the needed drivers for these items. whereas ubuntu (linux in general) may. and as you've said (you answered your own question) everything seems to work properly.

---

### Post by sofasurfer on 2009-01-07
Well now, this is just a lesson for me, I'm not saying I need to install the drivers on the cd. But I did try. I inserted the cd and rebooted and my hard drive booted into Ubuntu. So I disconnected the hard drive and rebooted and got a message that I needed to insert a bootable disk. 
Isn't a cd for loading motherboard drivers a bootable disk? I can view the disk if browse to it from within Ubuntu. There is a setup.exe file in it. So can I just click on that to get the installation process started? Or is it required to start it by booting the disk (which I am so far unable to do)?

---

### Post by oilchangeguy on 2009-01-07
> **sofasurfer said:**
> Well now, this is just a lesson for me, I'm not saying I need to install the drivers on the cd. But I did try. I inserted the cd and rebooted and my hard drive booted into Ubuntu. So I disconnected the hard drive and rebooted and got a message that I needed to insert a bootable disk. 
Isn't a cd for loading motherboard drivers a bootable disk? I can view the disk if browse to it from within Ubuntu. There is a setup.exe file in it. So can I just click on that to get the installation process started? Or is it required to start it by booting the disk (which I am so far unable to do)?

.exe files will not run in linux. and the cd is not bootable. why would it need to be? your linux install is fine. as i said in my other post, these mobo drivers are for windows only. and only if windows does not auto install the needed drivers.

---

### Post by sofasurfer on 2009-01-07
I do not understand why we can assume that Ubuntu contains all drivers needed for the motherboard. When buying video cards, tuner cards, network adapters, etc we always need to do research to be sure that Ubuntu (or any version of Linux) supports that particular card. This apparently is not the case with motherboards?

---

### Post by oilchangeguy on 2009-01-07
> **sofasurfer said:**
> I do not understand why we can assume that Ubuntu contains all drivers needed for the motherboard. When buying video cards, tuner cards, network adapters, etc we always need to do research to be sure that Ubuntu (or any version of Linux) supports that particular card. This apparently is not the case with motherboards?

This is getting way too hard. You've already said everything works. The cd's provided with your motherboard are for WINDOWS only. if you feel the need to install mobo drivers for linux, then you'll need to contact the mobo maker, and ask them for a linux driver cd, which most likely does not exist.

my computer is a custom rig, and yes, when i installed windows xp pro (legal copy) i had to install drivers from the mobo maker, so that everything worked properly. this computer now runs kubuntu 8.10. and there are no mobo drivers to install. now if it had some new cutting edge sound, or video card, then there may be a driver issue. and only then.

---

### Post by sofasurfer on 2009-01-07
I'm simply asking questions in order to understand things. I'm not saying I need to install anything.

---

### Post by oilchangeguy on 2009-01-07
> **sofasurfer said:**
> I'm simply asking questions in order to understand things. I'm not saying I need to install anything.

post #4 sure sounds like you're wanting to install it. but anyway, please use the thread tools and mark this thread as solved.

---

### Post by cariboo on 2009-01-07
I've got an earlier version of the same motherboard, all the proper open source drivers are included with the Linux kerenl. Have a look in /lib/modules/<kernel_version>, that is where all the modules (drivers) are located. The only time you need the driver disks are when you install either XP or Vista, otherwise if you don't intend on installing windows you can put them away somewhere, where you won't loose them, just in case. :)

Jim

---

