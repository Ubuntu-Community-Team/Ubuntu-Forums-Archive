---
title: "Is this laptop hosed?"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by skrimpy on 2007-07-13
This is for a friend.  He thinks his system is completely hosed; I told him I'd post here before he starts looking up repair centers.

He's been running a dual boot on a Gateway notebook, Ubuntu 7.04 dual booting with Windows XP.  

The onboard sound card has been messed up - he's been using a PCMCIA soundcard - he thinks whatever corrupted the onboard card/speakers is what has hosed the system.

The computer has been running fine, except the sound card.  Yesterday he had a Windows update which required a system restart.  When he tried to reboot the computer it wouldn't start back up.

He's seeing the BIOS menu go by and then gets a blinking cursor.  The Grub menu never loads.  He cannot boot from the Ubuntu liveCD.  He cannot get a prompt.  He's tried reseating the hard drive and the RAM.

Anything else to try?  Any suggestions?

---

### Post by w4ett on 2007-07-13
will it boot from the live CD?  if so, try  to rebuild grub....sounds like it's been corrupted...try setting thge bios to boot only from the cd, and remove the HDD from the boot order

---

### Post by w116tjb on 2007-07-13
Have you tried using other LiveCDs, such as Knoppix? You'll be able to fix grub that way too.

Does the laptop have a floppy drive? If so, try using a XP bootdisk.

---

### Post by skrimpy on 2007-07-13
Tried completely taking the HDD out of the boot list, that didn't help.  Only tried the Ubuntu CD thus far, but the CD drive isn't spinning up when the computer is turned on.  I also thought it sounded like a corrupt GRUB at first, but can't figure out why it won't boot from a CD if that's the case.

---

### Post by w4ett on 2007-07-13
> **skrimpy said:**
> Tried completely taking the HDD out of the boot list, that didn't help.  Only tried the Ubuntu CD thus far, but the CD drive isn't spinning up when the computer is turned on.  I also thought it sounded like a corrupt GRUB at first, but can't figure out why it won't boot from a CD if that's the case.

W...E....L...L.....at this point it sounds like a hardware problem.....one possible other fix might be to D/L Damn Small Linux to a USB drive......set the bios to boot from the thumbdrive (USB), and see if you can mount the HDD from there....then rebuild grub  OR...connect an external CD drive and try to set the boot priority to this drive and boot a live cd.....(try the super GParted Live CD, it will fix ALMOST any storage device problem)

---

