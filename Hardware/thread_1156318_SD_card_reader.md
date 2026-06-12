---
title: "SD card reader"
date: 2009-05-11
forum: Hardware
---

### Post by eidoslinux on 2009-05-11
i can not get my sd card reader to work with in Ubuntu 9.04 it sees the reader in the system, but when i put in my sd cards nothing happens.. when i boot into the other os's they can see it fine, but i dont care for that drive if you know what i mean.

can anyone help?

---

### Post by natacho on 2009-05-16
I have the same problem
Ubuntu 9.04 runing in a HP TX2500
With ubuntu 8.10 the SD card reader was working....

---

### Post by jlh68 on 2009-05-17
What computer are you using?  For the Acer Aspire ONE here is the How-To to fix:

> OPTION 1:  
Open the Terminal via Accessories>Terminal and then type (or copy-n-paste) the line "sudo gedit /boot/grub/menu.lst".  It will likely prompt you for a password.  After which, the menu.lst file will open -- if you drop all the way to the end of the file, you should see the boot options available (the first line should start with something like "title          Ubuntu 9.04, kernel 2.6.28-11-generic"). 

You will want to append that code right after the kernel line, which
ends with "ro quiet splash" so that it becomes "ro quiet splash
pciehp.pciehp_force=1".  Then save and reboot your Acer.


OPTION 2: 
Same as OPTION 1, but instead of going through the Terminal, you can just press ALT+F2 to bring up the Run window and type in "gksu gedit /boot/grub/menu.lst" to open the file automatically.  Or just put in "gksu gedit" if you want to open the Text Editor with Root access only and then navigate to /boot/grub/menu.lst yourself using File>Open.

I hope this helps.  More info on the AspireOne - Community Ubuntu forum

---

### Post by natacho on 2009-05-17
I tried that solution but it does not work.
I'm using a HP TX2500. The SD card reader was working well with ubuntu 8.10 
Thanks for the help

---

### Post by eidoslinux on 2009-05-23
ya did not work for me ether. and like you natacho it worked fine in 8.10 and the beta too.

---

### Post by plaurits on 2009-06-14
Is there a solution to this problem?

As everybody else said it worked fine in 8.10 but doesn't work in 9.04 :(

---

### Post by eidoslinux on 2009-06-14
the only thing i have found to do with mine is insert a flashdrive or something in the usb slot on my card reader and then the card. Then i can use it normally, but it is a pain to do that everytime. But that tells me that there is a bug in the kernal, with it working like that. hopefully will be fixed in the next kernal release, just have to wait and see!

---

### Post by plaurits on 2009-06-15
Ah, thanks for the tip that actually works (on my TX2500), at least I can use my SD cards now :D But yes, lets hope this bug will be fixed.

---

