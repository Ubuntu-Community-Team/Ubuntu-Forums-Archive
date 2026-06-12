---
title: "Installing to a flash drive, any good guide for this?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by gohanssjn on 2009-04-23
Searched around a bit and couldn't seem to find a guide for this.  I have an 8GB flash drive and would like to put Ubuntu on it for my laptop.

Can it be done in that amount of space?

---

### Post by JMacGill on 2009-04-23
I just did this a few days ago. 8GB SD Micro card and Ubuntu 8.10 amd64 on a Sony Vaio.  Working fine for me.  The free space stays at about 2.4-2.8 GB.  Make sure you get a good reader and test a few out on your system. I have one reader that my computer can't boot from but three other readers that can boot.

Make sure your computer can boot from flash drives.  Set your computer to boot from CD to do the install.  Durring the install, make sure your installing to the flash drive and not your internal harddrive. Also before the actual install starts, make sure to use the advanced setting on the last page to install the boot manager on the flash drive, if you don't want it to mess with the internal drive. You can then use the Bios to chose which drive to boot from.

---

### Post by PhrankDaChickenGeek on 2009-04-23
Have you seen this:
[http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)

---

### Post by gohanssjn on 2009-04-23
I will check it out.

Unfortunately, 9.04 won't even start the LiveCD on my computer right now, so I can't test out the new version to see if I want it.

Also, juse because this is my work (personal work) laptop, if I choose install from the boot menu, it gives me an option down the line where to install, correct?  So it doesn't overwrite my harddruve off the bat...

Just a little paranoid for the drive...

---

### Post by sgosnell on 2009-04-23
It should boot the live CD, provided it was burned correctly, and the proper options are set in the BIOS.

Yes, you get the option of which drive to install to, and how to partition it.  Just don't install to sda1, which is your internal hard disk.  The USB drive should show up as sdb1, if there are no other drives.  You should be able to tell by the size of the drive, if nothing else.  You also probably want to click on the Advanced button, on the last screen before the actual install, and put the grub bootrecord on the USB drive, not on the HDD.

---

### Post by gohanssjn on 2009-04-24
Yeah, no go.

Boots fine on my Desktop, but not the laptop (Dell Latitude XT Tablet).

Gah.

---

### Post by sgosnell on 2009-04-26
What happens when you try to boot the laptop from the USB disk?  Does it even try, or does it just boot from the HD?  If so, you need to change the BIOS settings to boot from the USB before the HD.

---

### Post by gohanssjn on 2009-04-27
No no...I mean the LiveCD itself will not boot, so I can never get to the part to install Ubuntu to USB.  it tries to start, and then crashed to a command line.  That's it.

---

