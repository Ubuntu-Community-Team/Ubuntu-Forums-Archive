---
title: "Boot, HD-USB e Kernel panic"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by newubu on 2005-08-10
Hi everyone....
I love ubuntu and I want to install and boot it from an external USB hard disk 30Gb!!

I try to find on this forum and I find a good how to [HERE](http://www.ubuntuforums.org/showthread.php?t=5151)

but I have some problems....in particular with the menu.lst!
I don't know how I have to edit it!

----------------------------------------------------------
I try to edit the line:

*kernel vmlinuz-2.6.10-5-386 root=/dev/sda ro quiet splah*

with

**kernel (hd0,1)/boot/vmlinuz-2.6.10-5-386 ro  root=/dev/sda**


And I do an:

/sbin/grub-install --root-directory=/boot hd0,1 (or sda I don't remember)

But when I restart the system it say something like this:

kernel (hd0,1)/boot/vmlinuz-2.6.10-5-386 ro  root=/dev/sda
file not found error line:15
--------------------------------------------------------------

if I try to startup the ubuntu recovey mode,  it say this:

unable to open /dev/init
kernel panic: attemp to kill init!!
---------------------------------------------------------------
My partition are:

#1 /boot "flag as bootable"
#2 /
#3 swap area
#4 /home

Someone can help me please?

PS
Can I edit, for example menu.lst without reinstall the whole system??

---

