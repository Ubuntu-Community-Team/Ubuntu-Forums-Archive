---
title: "Dualbooting Linux, and Vista"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Nazty_Nayt on 2009-05-12
Hey guys, I'm trying to dual boot Linux, and Vista.  I'm using the guide  [here](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

I've gotten to step 4, installing Vista.  It does show the unallocated space, and I hit shift+F10, and run diskpart, I select disk 0, and when I choose list partition, it doesn't show partition 3, only my primary Ubuntu partition.  Can anyone help me out here?

---

### Post by lindsay7 on 2009-05-12
I have never used this method to do this but, I am wondering why you just can't use Gparted to format the unallocated space and mark it active and just install Vista to that partition. I am sure there is a reason but it would seem a lot easier to skip all that windows terminal stuff.

Also, in place of using the bcd disk to add the windows mbr you can use the Ubuntu live disk

In the terminal type " sudo fdisk -l"
look for the ntfs partition, this is where windows is. It should be something like sda3.

type sudo apt-get install ms-sys
then type sudo ms-sys -mbr /dev/sda or whatever fdisk tells you and reboot

You will still need to do this

To enter the GRUB configuration mode, type in "sudo grub" and press Enter. Then type in the following commands in sequence:
root (hd0,0)
setup (hd0)
quit
exit

and edit the grub menu.lst as shown.

title Windows Vista
root (hd0,1)
makeactive
chainloader +1

---

### Post by Nazty_Nayt on 2009-05-12
Thanks Lindsay, I'm going to try that here shortly, will post back if have any questions.

---

### Post by Nazty_Nayt on 2009-05-12
Ok, I got to the my-sys part, it couldn't not find the package for it.  I'm looking at the unallocated space in Gparted right now, and I can't figure out how to make it active with Gparted either.

---

### Post by lindsay7 on 2009-05-12
Looks like ms-sys in no longer available, try this instead from the Ubuntu live cd. Type in the terminal "sudo apt-get install lilo" then  "sudo lilo -M  /dev/sda mbr"

I do not think you have to make the partition active. The windows install should do that.

You can also use the vista disk to add the mbr.  Here is the infor.


[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

