---
title: "BIOS (UEFI) Won't Show/Can't Access"
date: 2017-03-24
forum: Hardware
---

### Post by ThePowerpuffGirls on 2017-03-24
Lately, when I start my main desktop, the monitor stays blank until the login screen shows. If I press the delete key to enter the BIOS (UEFI), nothing happens the monitor stays blank and the light stays orange.

Here are the specs:
Motherboard: ASUS Z97-K
Processor: Intel Core i3-4130 @3.40GHz (x4)
RAM: 8GB DDR3 @1600MHz
Drive: Samsung EVO 850 250GB M.2
Monitor: ASUS VP278H-P (HDMI)

---

### Post by oldfred on 2017-03-24
Did you leave Fast Boot on. That is a UEFI setting.
My Asus z97-ar had multiple fast boot settings.
Cold boot, warm boot (reboot), and then time delay settings on fast boot.
I set mine to full reboot on cold boot and 3 sec delay on warm boot, so I have 3 sec to press a key to get into UEFI. I also have 3 sec on grub menu so I slow boot by 6 sec. With SSD that 6 sec almost doubles my boot time, but I always want to be able to directly get into system or grub menu.

UEFI Fast Boot means that you have made no system changes to either hardware nor system software, so the normal scan of system by UEFI/BIOS is not required and UEFI can immediately turn boot process over to operating system. All parameters are already correctly on drive for operating system to use.

If full cold boot, all power off (unplugged), hold power switch for ten sec or so to drain all power in system and then boot and immediately press f2 to get into UEFI.
If cold boot does not work, you may have to jumper pins on motherboard, see manual.
That will reset UEFI/BIOS to defaults, just a a new update to UEFI does.
I had to write down, copy screens as I change many settings.

[https://ubuntuforums.org/showthread.php?t=2298896&p=13373570#post13373570](https://ubuntuforums.org/showthread.php?t=2298896&p=13373570#post13373570)
But in this thread I had more screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by ThePowerpuffGirls on 2017-03-24
Hi,

I tried resetting the it. I took out the CMOS battery, and it still didn't work, but here's the weird thing.
Something told me to try another monitor. I got another flat screen, connected via VGA (as it only takes VGA/DVI and my DVI cable that I have left is broken), the BIOS shows up on it, it won't on this.
I wonder does the screen size have anything to do with it as this monitor is 27"

However my folks have a 46" TV and the BIOS shows on that, but different motherboard though.
I'm sure it used to show. I had this monitor for at least a month.

UPDATE: I tried connected this monitor (the 27") via VGA and the BIOS (UEFI) works, but it won't shows when connected to HDMI.

---

### Post by oldfred on 2017-03-24
Changing monitor is a hardware change.

And then it may be what video card/chip you have and how it is configured.

Is it just UEFI display or grub menu display?

---

### Post by ThePowerpuffGirls on 2017-03-24
I fixed it. I've updated the BIOS (UEFI) and now it is working.
Thank you for your help. :)

---

