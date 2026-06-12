---
title: "Add Windows 2000 to GRUB"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Max Barney on 2009-01-28
Hello, I am trying to dual boot Ubuntu 8.04 with Windows 2000.


Here is my hardware configuration:

Internal IDE Hard Drive 6.9GB With Ubuntu on it

Internal IDE Hard Drive 4.0GB With Windows on it


Both are bootable by changing the boot order in the BIOS, so what should I add to the GRUB file so that I can select which OS to boot from the GRUB menu?

---

### Post by shark1997 on 2009-01-28
Edit your /boot/grub/menu.lst file, assuming you know which partition W2K is on.
Format:
title        Windows 2000
root         ([harddisk],[partition number])
chainloader +1
boot

---

### Post by shark1997 on 2009-01-28
Did you install W2k after Ubuntu?

---

### Post by Max Barney on 2009-01-28
I installed Ubuntu first, then unplugged the Hard Drive it is on, then plugged in the new hard drive then installed W2K on it. So they are both on separate Hard Drives.

---

### Post by logos34 on 2009-01-28
then you'll need a windows entry like this:
> 
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows 95/98/Me
root        (hd1,0)
savedefault
makeactive
[B]map        (hd0) (hd1)
map        (hd1) (hd0)[/B]
chainloader    +1

---

### Post by Max Barney on 2009-01-28
Thank you logos34!!! It worked!

---

