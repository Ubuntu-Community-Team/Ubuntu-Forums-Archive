---
title: "Problem with Internet (Compaq 6720s)"
date: 2010-05-14
forum: Hardware
---

### Post by kokoszken on 2010-05-14
welcome everyone, my first post on this forum :)

I have laptop HP Compaq 6720s.
I recently decided to try ubuntu for the first time (it is also my first Linux system).
After installing ubuntu 10.04, everything seemed fine at first.
Then I realised I couldn't connect to internet via my Wired connection.

I check google and it turned out that someone has already answered my question with this:

> 1) Ethernet card not working 
it appears to be an ubuntu bug (i had no problems with the wired with fedora 8 for example) but there are two ways to quickly solve this trouble:

Simple Way : Boot with the pci=noacpi parameter:

howto : open a terminal window and input the command

Code:
sudo gedit /boot/grub/menu.lst
However you may change "gedit" with "kwrite" if you are using kubuntu, with "mousepad" if you are using xubuntu, or "nano" if you wanna edit the file using the terminal (or you have no graphic interface - for exaple if you installed a server edition);

Once the text file has shown up, locate this section:

Code:
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a089c41b-e47e-444e-b389-e5a23ed610ee ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
Add the "pci=noacpi" option to the kernel string, so it has to result like this:


Code:
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a089c41b-e47e-444e-b389-e5a23ed610ee ro quiet splash pci=noacpi
Now reboot, ethernet should work !!!

The problem is, this is about Ubuntu 7.10.
On my version when I put this code into terminal, I only get blank window menu.lst

Someone on IRC advised me to use gksudo instead of studo, but it did not change a thing.

What should I do?

---

### Post by chunkster29 on 2010-05-14
ubuntu dos'nt use menu.lst anymore try /boot/grub/grub.cfg instead

---

