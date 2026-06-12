---
title: "linux image fails compile USB Harddrive 8.10, works on 8.04"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by luckstrikes on 2008-12-15
Hey,

Earlier, I successfully installed 8.04 onto my External 320GB Harddrive along with GRUB on the same drive(Had to make minor changes to menu.lst to make it boot).

Today i decided to erase it and install 8.10 on the drive. I installed grub onto the harddisk itself(deleted the earlier boot and root partitions and made new ones). Now the installation successfully completed and i restarted. Grub loaded.
However,

There was only memtest in the boot menu apart from my Windows on the other harddisk.(Even the rescue option was missing)

I inspected the problem further and it seems that the vmlinuz-2.6.27-7(no vmlinuz file is present) file is missing in the boot drive(suspecting it failed to compile and hence update-grub couldn't update menu.lst accordingly).

The initrd and vmcore files are present.

I tried reinstalling the kernel by doing chroot from another system and using the apt-get install command. However it says file installed and no updation required.

I'd really appreciate it if someone understood the problem.

My system has an ATI X1300 Graphics card(if it helps to know) and is a Dell Inspiron 6400 with all the usual stuff. 

Also note that 8.04 worked perfectly fine.


Thank You,

luckstrikes

---

### Post by luckstrikes on 2008-12-16
ummm...i'm new to ubuntu forums and ubuntu, hope someone can understand this problem...

actually if someone can tell me how to recompile the kernel and get the vmlinuz-2.6.27-7 into the boot drive, my problem would be solved!!!

---

