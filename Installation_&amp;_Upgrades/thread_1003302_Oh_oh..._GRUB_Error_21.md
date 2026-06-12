---
title: "Oh oh... GRUB Error 21"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by RX8volution on 2008-12-06
Hi - before someone says it - yes I checked these forums and I don't know that any of the previous posts directly apply to me, and this situation is delicate since this is a PC that I *cannot* screw up (oops).

Here's the situation... I bought a USB external disk for my laptop, and booted from CD-Rom (Ubuntu latest), and installed it to that external disk.  When it told me to reboot, I let it, and tried to boot off of that external disk (USB) but I got an Error 18 when GRUB first started loading.  I panicked, **** down, pulled the USB drive and rebooted again, now I get ERROR 21.

HELP!  I need the Windows partition on my INTERNAL disk to work, (come back!), but I'd like to get my Ubuntu external USB disk working as well... help?

---

### Post by Diabolis on 2008-12-06
There is nothing special in your situation.
[http://www.google.com/search?hl=en&q=ubuntu+forums%3A+grub+error+21&btnG=Search](http://www.google.com/search?hl=en&q=ubuntu+forums%3A+grub+error+21&btnG=Search)
[http://www.google.com/search?hl=en&q=ubuntu+forums%3A+grub+error+18&btnG=Search](http://www.google.com/search?hl=en&q=ubuntu+forums%3A+grub+error+18&btnG=Search)

---

### Post by RX8volution on 2008-12-06
Hi again...
  I tried this...[http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/)

And after booting into the "Live Ubuntu OS" (without modifying anything) I dropped into su, and fdisk -l yielded /dev/sda1 "boot" with the *... so I did grub-install /dev/sda1 and got "Could not find device for /boot: Not found or not a block device"

W T F?

I don't know if this helps troubleshoot but my WindowsXP partition (my laptop HD) is where there is now a directory called boot with tons of files in it... (Ubuntu I presume).  At this point I just want to restore my WindowsXP partition....

---

### Post by psusi on 2008-12-06
Boot the windows install cd and load the recovery console, then run the FIXMBR command.

When you installed Ubuntu, it installed grub to the first hard disk, which is usually the disk the computer boots from.  That's not what you wanted though, but grub had no idea that was the case.  The fixmbr command will have windows put its boot code back in the MBR instead of grub's.

---

### Post by RX8volution on 2008-12-06
Yes, that would be the best course of action EXCEPT... "Setup did not find any hard disk drives installed in your computer"... which is weird because when I boot from the LiveCD in Ubuntu 8.10, my C: drive is right there, and I can browse it.  W T F?!

---

### Post by psusi on 2008-12-06
You probably are trying to use XP and it needs a newer driver on a floppy to see your hard disk.

---

### Post by RX8volution on 2008-12-06
Yes - you are correct.

The problem is, this laptop doesn't even HAVE a "floppy"...nor would I know where to even look for a floppy disk!  Any other ideas?

---

### Post by RX8volution on 2008-12-06
Has anyone tried this method?  I'm kinda screwed here...

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by RX8volution on 2008-12-06
ALRIGHTY!  I solved it!

  I know this isn't a Windows forum but in case anyone runs into this kind of thing again... since WinXP CD wouldn't find my drive I had to "integrate in" the drivers into the boot CD.  This program called nLite let me do it - AMAZING

[http://www.nliteos.com/index.html](http://www.nliteos.com/index.html)

---

