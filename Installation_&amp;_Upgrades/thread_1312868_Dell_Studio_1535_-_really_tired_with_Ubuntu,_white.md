---
title: "Dell Studio 1535 - really tired with Ubuntu, white screen at boot again?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by netlaptop on 2009-11-03
Updated:Solved!

I have been looking for this nearly 4 months!

See this post first:

[http://ubuntuforums.org/showpost.php?p=8362484&postcount=9](http://ubuntuforums.org/showpost.php?p=8362484&postcount=9)

This way also works for me:

1- Live CD F6, add nomodeset... like[ #9 post]("http://ubuntuforums.org/showpost.php?p=8362484&postcount=9")

In Ubuntu, active driver in System/Administrator/Hardware Drivers (to prevent Broadcom STA wireless driver problem for my dell studio)

then Install Ubuntu to HDD.

2- When Ubuntu is installed, restart as it asks. At boot menu, let press "e" to edit grub at boot and add _nomodeset_
like:
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=a6850822-f08e-4f11-8cd3-4ce83a864b8a ro nomodeset  quiet splash nomodeset

3- In Ubuntu just edit:

sudo chmod u+w /boot/grub/grub.cfg
sudo gedit /boot/grub/grub.cfg



(It helps us pass "mount" or find UID-XXX-XXX-XXX step)

then do as #9 post

 > you need to change the following menu entry by adding "nomodeset" - see the line starting with "linux"

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3 ro nomodeset quiet splash nomodeset
initrd /boot/initrd.img-2.6.31-14-generic
}
now reboot. we are almost there !!!

after rebooting the system, we again open the terminal and edit the grub default

$ gksudo gedit /etc/default/grub

here there a two changes which added the "nomodeset":

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
    GRUB_CMDLINE_LINUX="nomodeset"

after saving the changes execute

$ sudo update-grub


Thanks much!


------------------------

History problem


My laptop:

Dell Studio 1535 64 bits

**Intel graphics media accelerator x3100**
........

I could not install Ubuntu 8.10 due to the "white screen error - white background with lots of colorful lines" when I try to install Ubuntu from CD.

It was strange, after waiting for 6 month, I could install Ubuntu 9.04 (64 bits)from the CD, not getting "white screen with lots of colorful lines". 

I was so happy and Ubuntu 9.04 worked well with my dual boot laptop. I can even enable "extras visual effects" in appearance preferences.

**This morning, I carefully updated all new available updates for Ubuntu 9.04 before upgrading it to Ubuntu 9.10 from Update Manager.**

And now it gets that white screen - with many colorful lines - again at boot...

I have tried advices I met on the Net, but no luck! And I even tried installing a fresh Ubuntu 9.10 for the computer but I could not because of that unexpected white screen...

Any ideas to fix this issue?
 
PS: My Intel Graphics Media Accelerator (GMA) X3100 is an integrated (onboard). ==> So I can not remove GMA, and buy a new graphic chip which fully supports Ubuntu?

---

### Post by nmrcy on 2009-11-10
> [IMG]http://img211.imageshack.us/img211/8996/dsc00741om.jpg[/IMG]
> [IMG]http://img109.imageshack.us/img109/6460/dsc00742.jpg[/IMG]

like this? i have same problem in 9.04 this problem was fixed but stg happened again with this sick graphics card

---

### Post by netlaptop on 2009-11-13
@nmrcy: YES, exactly!!

I just have this problem with Ubuntu 8.10 and 9.10. Ubuntu 9.04 works fine with me.

Now I am still using Ubuntu 9.04. And I am waiting for Ubuntu 10.4...:D

---

### Post by hasagar on 2009-11-19
I had the same problem. I dont have the CD right now. But I will try to be clear.

1. When you are using the live CD, you have to give 'nomodeset' as an option. I dont remember exactly, but pressing F6 will show you a command. Add 'nomodeset' as an option in the command.  This solved my problem.

2. Remember to add nomodeset in your menu.lst file. Search for the kernel in the file and add nomodeset. I hope you are familiar with this file. It is in /boot/grub

If you upgraded to 9.10, changing(add nomodeset) the menu.lst file will solve your problem. But you need to change the file somehow.

I know I am not very specific. But this helped me to use karmic

---

### Post by netlaptop on 2010-02-04
Sorry for replying so late. I was so busy... 

I have collected some workaround on the Net , and I will try them next week (my Tet holidy).


[https://docs.google.com/Doc?docid=0AchsrUb3C_h0ZGhxbXJtNl81NjVoenE4cjl4&hl=en_GB](https://docs.google.com/Doc?docid=0AchsrUb3C_h0ZGhxbXJtNl81NjVoenE4cjl4&hl=en_GB)

You can also permission to edit this document as well. Pls add more details if you had the same problem and fixed it...

Thank you very much!

---

### Post by netlaptop on 2010-02-09
So happy with Ubuntu on my Laptop again...! :D

---

