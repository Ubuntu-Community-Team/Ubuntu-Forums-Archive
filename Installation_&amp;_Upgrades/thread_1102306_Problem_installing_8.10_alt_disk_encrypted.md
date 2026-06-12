---
title: "Problem installing 8.10 alt disk encrypted"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by kaledev on 2009-03-21
I have an interesting problem that I can't seem to solve. I am installing Ubuntu 8.10 on a seperate harddrive. I have Vista on my main drive. Well I wanted to install an encrypted OS so I used the alt CD. Well I also use truecrypt to encrypt my Windows partion, and you can't have a third-party boot loader such as Grub if you plan on encrypting your windows partition. Well it seems I also cannot install Grub on my Ubuntu partition. Trying to install it to hd2,0 (where ubuntu is) recieves an error. It will only let me install to the swap partition which is hd2,4 and I heard that doing this will cause Ubuntu not to boot (which is does because I tried it) So what options do I have and where in the world can I install grub that isn't on the MBR, and will still allow me to dual boot, and leave my windows disk alone?

Right now hd0,1 contains Vista, and hd2,0 contains Ubuntu.

Thanks! :(

---

### Post by tommcd on 2009-03-21
The solution for this is to create a small /boot partition of around 200mb and install grub (as well as your kernels and related files) there. The boot partition will be unencrypted and be file system type ext3. The boot partition should be a bootable partition (i.e., the boot flag will be on). See this:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)
You will need to set the Ubuntu hard drive to boot before the Vista drive in your computer's BIOS. Otherwise Vista's boot loader will load Windows and you won't be able to boot Ubuntu. Grub will give you the option to boot Ubuntu or Vista.

---

### Post by kaledev on 2009-03-21
Thanks for the help.

I ended up solving the problem by having a separate /boot partition as you mentioned.

I ended up doing it from a fresh install which isn't very strait-forward if you want to install an encrypted Ubuntu OS. I thought I would say how I did it just in case anyone else runs into the same problems I did.

First I followed this guide:
[http://howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

However, the bug mentioned about not being able to set up an encrypted swap partition on the manual install doesn't seem to be a problem with 8.10.

Just set up swap like the /, or /home partition, and I decided not to use a Passphrase with swap and instead used the Random option.

Thanks!

---

