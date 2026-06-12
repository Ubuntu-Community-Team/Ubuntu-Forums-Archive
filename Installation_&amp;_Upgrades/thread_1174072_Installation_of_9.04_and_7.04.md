---
title: "Installation of 9.04 and 7.04"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by huzefa_from_kuwait on 2009-05-30
Hi guys, Please help, I got stuck.

I installed 9.04 Desktop on a fresh Hard disk.

I installed in on ext4 partition.

Afterwards I installed 7.04 on another partition.

After installation of 7.04 the grub is going to the 7.04 partition for the menu.lst file (as expected)

I entered the entry for 9.04 in the menu.lst of 7.04 but unfortunately it won't boot (it says file / directory not found) because most probably it cant read the ext4 partition.

Now I can't boot in 9.04 so I booted from System Restore CD and changed the boot partition to be the one of 9.04, but still it won't go there.

When I do fdisk -l it does show me that 9.04 is the boot partition.

Now what do I do? 

Please help as I cant get into my 9.04 system !

---

### Post by coffeecat on 2009-05-30
I've no experience of ext4 but I believe your problem is that the version of grub that came with 7.04 wasn't patched to be able to deal with ext4 partitions. The solution is to reinstall the 9.04 grub back to the mbr to use the 9.04 menu.lst, and then edit the 9.04 menu.lst so that you can boot 7.04 from it. You'll be able to reconfigure the 9.04 grub from the 9.04 live CD but first we need some information. You've already done a fdisk -l, but post the output of:

```
sudo fdisk -l
```... and then I or someone can give you the grub commands to use from the 9.04 live CD. By the way...

> **huzefa_from_kuwait said:**
> When I do fdisk -l it does show me that 9.04 is the boot partition.

I presume you mean that the 9.04 partition has the boot flag set. Don't worry about that. The boot flag is irrelevant to Linux - Linux doesn't use or need the boot flag. The boot flag is for Windows only.

Er... Excuse the curiosity, by why do you want to run 7.04? :?

---

### Post by huzefa_from_kuwait on 2009-05-30
Thanks for the reply, here you go with the output.

fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc02fc02

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         373     2996091   82  Linux swap / Solaris
/dev/sda2             374        5474    40973782+   5  Extended
/dev/sda3            5475        6127     5245222+  83  Linux
/dev/sda5   *         374        2863    20000893+  83  Linux
/dev/sda6            2864        5474    20972826   83  Linux
```


Ubuntu 9.04 menu.lst

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		6a79d3d4-5adf-4e42-bf57-583500db377d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6a79d3d4-5adf-4e42-bf57-583500db377d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		6a79d3d4-5adf-4e42-bf57-583500db377d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6a79d3d4-5adf-4e42-bf57-583500db377d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

Ubuntu 7.04 menu.lst

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ed55d1d9-85be-4bd9-86bb-d8e019b9dbd5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ed55d1d9-85be-4bd9-86bb-d8e019b9dbd5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic


root@ubuntu:/u7/boot# sudo vol_id -u /dev/sda6
bad4c6ec-5a31-4a66-861b-b7548408f8be
root@ubuntu:/u7/boot# sudo vol_id -u /dev/sda5
6a79d3d4-5adf-4e42-bf57-583500db377d
root@ubuntu:/u7/boot# sudo vol_id -u /dev/sda3
ed55d1d9-85be-4bd9-86bb-d8e019b9dbd5

---

### Post by coffeecat on 2009-05-30
OK. Your 9.04 root partition is on sda5, which is (hd0,4) in grub-speak.

Boot up from the 9.04 live CD and open a terminal, and:

```
sudo grub
```The prompt will change to the grub one. Now...

```
root (hd0,4)
setup (hd0)
quit
```Obviously with a <return> between each line. Hopefully, you'll get a 'success' message after the setup command. Now reboot and you should be seeing the 9.04 grub menu. Boot into 9.04, and all you have to do is to add the 7.04 stanzas to the 9.04 menu.lst. I'll leave that to you as you clearly know your way around menu.lst.

Good luck!

**Edit:** the above is the way I like to reinstall grub - I'm doing it all the time with my multibooting machines. :) But there is a slightly quicker way, which I forgot about until this moment. Apologies for that. You can use [SuperGrubDisk](http://www.supergrubdisk.org/). It will find all the Linux installations in a multiboot, let you boot into any of them **and** reinstall grub for whichever one you want. **However**, the SGD menu is not at all intuitive and it's difficult to make out what's going on - at least until after it's happened. Nevertheless, I do recommend you download that for your emergency toolkit. It's also a quick and easy way of reinstalling the Windows mbr - if you ever need to. Much quicker than using the Windows install disc.

---

### Post by huzefa_from_kuwait on 2009-05-30
Yep, that did it.
Thank you , thank you , thank you very much :-)

Now i will install solaris 10 on another partition, and once it is screwed again, i will repeat the same procedure :)


btw I use 7.04 because I cant get packet injection working on any other kernel except 2.6.20.* :)


Thanks again.

---

