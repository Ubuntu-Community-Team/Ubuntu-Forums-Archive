---
title: "grub doesn't find menu.lst even though it is there"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by vertago1 on 2009-07-22
[Solved] Alright, so I edited my menu.lst file and when I rebooted I ended up at the grub menu.

I then used a live cd to move the old menu.lst and run update-grub to generate a new one. When I rebooted I still ended up at the grub menu.

I tried:
find /boot/grub/menu.lst
and it says file not found, but when I try:
find /boot/grub/stage1
it shows (hd0,0)

I know the menu.lst file is there but grub doesn't see this. Plz help.

---

### Post by vertago1 on 2009-07-25
after messing around I was able to get the system in a workable state:

1) I booted from a live cd, installed the text editor I wanted to use

2) I mounted my ext3 partition

3) I cded to the location I mounted it to, in my case:
cd /media/disk

4) I moved the old menu.lst file to menu.bak
sudo mv boot/grub/menu.lst boot/grub/menu.bak

5) I mounted proc and dev to the disk:
sudo mount -t proc /proc proc/
sudo mount -o bind /dev dev/

6) I logged into root on the disk:
sudo chroot .

7) I generated a new menu.lst file using update-grub (answer y for yes to the prompt to generate the new menu.lst file):
update-grub

8. I exited out of root:
exit

9) I made the modifications I wanted to the menu.lst file, before I used vim but this time I used kwrite (if kwrite is not installed gedit or kate should work) note that it needs root privileges to edit the menu.lst file:
sudo kwrite

10) I don't think this step made any difference but I am going to note it none-the-less...I logged back into root on the disk and ran update-grub again to verify that it found the menu.lst file and could read the configuration parameters at the top of the file.

11) This time when I rebooted it didn't dump me into the grub menu.

---

### Post by leye0 on 2010-01-28
Hi!

So this is solved. But what was the solution?

Thank you!
Leon

---

