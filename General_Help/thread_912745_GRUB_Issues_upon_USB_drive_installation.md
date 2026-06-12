---
title: "GRUB Issues upon USB drive installation"
date: 2008-09-07
forum: General Help
---

### Post by md6 on 2008-09-07
I tried installing Ubuntu 8.04 to an 8GB USB flash drive by following the instructions linked to below. Basically, when it asked where to install, I selected the USB drive and continued with the installation. The installation finished successfully.

When I restarted my PC, I hit F12 to go to the BIOS boot menu and selected to boot from USB. It took me to a black screen with a single white line that was blinking. I waited for a few minutes and restarted the computer. This time, I let it start up on it's own without entering the BIOS boot menu. This time, the normal GRUB bootloader came up and there were a LOT of options.

Instead of the normal ubuntu, ubuntu (recovery mode) and vista/longhorn there were 3 or 4 more down below the vista option(normally the bottom one).

In a thread I read somewhere, it had mentioned the GRUB bootloader not being installed correctly when you install to a USB drive. I am not entirely sure, but I think rather than the GRUB being installed to the USB drive, it was installed on the C:\ drive along with the normal GRUB menu.  Anybody have any ideas on how to fix this? I'm a fairly new ubuntu user so I don't know too much (I'm able to copy/paste things to a terminal) but I will appreciate any help anybody can offer.

CLIFNOTES VERSION: I installed Ubuntu 8.04 to an 8GB USB flash drive and cannot boot from it. When I boot into 8.04 on my PC (the same PC that I used to install it on the USB drive) there are several NEW options in the GRUB menu. I'm not sure what to do now...

Installation instructions: [http://blogs.zdnet.com/hardware/?p=1873](http://blogs.zdnet.com/hardware/?p=1873)

---

### Post by md6 on 2008-09-07
After re-reading the installation instructions, it appears I missed step #4. I didn't print out the instructions to read as I was installing because I thought I knew what I was doing.

I'm not sure how to fix this.

---

### Post by md6 on 2008-09-07
BUMP Anyone know of a way to fix the GRUB? I cannot boot from the flashdrive and when I try and boot into my normal Ubuntu thats installed on the HD it won't let me.

Basically, I'm stuck with WinVista for the time being...

---

### Post by caljohnsmith on 2008-09-08
> **md6 said:**
> 
In a thread I read somewhere, it had mentioned the GRUB bootloader not being installed correctly when you install to a USB drive. I am not entirely sure, but [COLOR="Blue"]I think rather than the GRUB being installed to the USB drive, it was installed on the C:\ drive[/COLOR] along with the normal GRUB menu.  Anybody have any ideas on how to fix this? 
Based on your computer's symptoms, I think you hit the nail on the head; it sounds like Grub was installed to the master boot record (MBR) of your internal HDD (C drive) instead of the USB, which is what will happen by default during the install since your internal HDD is the boot drive. That's also explains why it is necessary to have your USB drive connected to be able to boot, and why you can't boot directly from the USB drive.

Anyway, the fix is usually really easy. First post the output of:
```
sudo fdisk -lu
```
And we can go from there.

---

