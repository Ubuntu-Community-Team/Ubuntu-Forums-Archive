---
title: "error 15 file not found when installing ubuntu using wubi"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by cssuss on 2009-09-30
I download the ubuntu 8.04.3 CD image (ubuntu-8.04.3-alternate-i386.iso) and extract wubi.exe from ubuntu-8.04.3-desktop-i386.iso. It all goes well at the beginning, after wubi reboot the computer, I select "Ubuntu" from boot menu, but it occurs and error like this:

find --set-root --ignore-floppies /ubuntu/install/boot/grub//vmlinuz
Error 15: File not found 
Press any key to continue... 

what can I do ?

I have installed Windows XP SP3 on c:, and want to install ubuntu using wubi to d:

---

### Post by shredder12 on 2009-09-30
Error 15 means that somefile is missing.. but the disk partition info is all well..
so i think you should be able to boot into windows..

I don't know how to fix such an error,.. but I think reinstallation would be a good option.. Try it once again.. ( this time check  the image's MD5 checksum).. 

And if you can't boot into windows.. then try restoring grub...

---

### Post by rreese6 on 2009-09-30
Highlight "Ubuntu" from boot menu,
press "e"
Highlight Kernel line
Press "e"
goto "..//vmlinuz"
remove "/"
press "b"

Let us know what happens

---

