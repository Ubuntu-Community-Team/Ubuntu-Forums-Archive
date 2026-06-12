---
title: "want to install 9.10 - manual partition?"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by SatieB on 2009-11-07
Hi,
I've got a dual boot machine with Vista and 9.04.
I want to upgrade to 9.10 using the possibility to create a second / and leave my 9.04 swap and /home untouched.

Partition setup is;
/dev/sda1      ntfs
/dev/sda3      extended
  /dev/sda5    linux-swap
  /dev/sda6    /
  /dev/sda7    /home
/dev/sda2     ntfs  (recovery setup)

I already shrank Vista making room for a second / (still unallocated though).

When I played around with the 9.10 installer, I noticed that you can create a second / partition but cannot attach the swap and /home partition to it. 

My question is: does the installer picks this up or do I miss something? 
Txs for your help!

---

### Post by sc30317 on 2009-11-07
Yes, the installer should pick it up; it will boot either kernel within grub from a partition I believe;  Give it a shot!

---

### Post by SatieB on 2009-11-07
Hi Rc30317, 
Txs for the advise. I looked somewhat furhter and found this [http://superuser.com/questions/12182/how-to-get-a-reinstall-of-ubuntu-to-recognize-home-partition](http://superuser.com/questions/12182/how-to-get-a-reinstall-of-ubuntu-to-recognize-home-partition)

Will this also do the trick? Simply editing fstab with the right /home partition?

---

### Post by SatieB on 2009-11-09
After playing with the installer some more I find out that you could actually add a mountpoint to the /home partition. However, you must not forget to select what kind of filesystem you will use on the mountpoint. ;)
I did this and in the 9.10 I can still use my old 9.04 /home.

---

