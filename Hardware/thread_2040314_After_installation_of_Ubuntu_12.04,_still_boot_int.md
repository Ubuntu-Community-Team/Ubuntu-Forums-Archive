---
title: "After installation of Ubuntu 12.04, still boot into Windows on Lenovo Y580"
date: 2012-08-10
forum: Hardware
---

### Post by alfchung on 2012-08-10
I guess Lenovo Y580 has caused a lot of problem with all kinds of Linux installation b/c they install Windows in a strange way.

I tried both Ubuntu and Fedora. Fedora doesn't let me install and reported lack of GPT partition. 

Ubuntu installed, but it still boot into Window. You know what, I almost want to get rid of the Windows!!! However, I have to admit that their Window is optimized and very fast. So I want to keep it.

I have the same problem as mentioned there
[http://ubuntuforums.org/showthread.php?p=12163110#post12163110](http://ubuntuforums.org/showthread.php?p=12163110#post12163110)

The original question was focused on partitioning and then mentioned bootloader. They are smart enough to solve the bootloader problem. However, I am not. I don't even know what MBR, GPT, UEFI,... were before running into this problem. 

It is marked "Solved" and I don't know if people still look at it. 

In short, Lenovo comes with 4 primary partitions and I get rid of one and resized one. Therefore, I have 3 primary for Windows and empty space (220 GB)

Then in Ubutun live USB, I partitioned the empty space into 210G Ext4 and mounted as / (sda4 logical) and 2G as Linux swap. 

For where to install grub, I tried both sda( I guess the whole disk), and sda4 ( the 210 Ext4 as mentioned before)

The installation went through. However, it boots to Windows 7 every time!!!

I tried on BIOS, both enable and disable UEFI. No luck. 

I read a little bit about MBR, GPT, UEFI and got some concept. However, I have no idea how to make my Linux partition GPT and bootable. 

I don't even know what kind of partition the pre-installed Windows is. 

Would you mind telling me how exact should I set up dual boot on Y580. Maybe we can create a Wiki page for Lenovo Ideapad Y580. 

Here is one for Arch Linux
[https://wiki.archlinux.org/index.php...o_IdeaPad_Y580](https://wiki.archlinux.org/index.php...o_IdeaPad_Y580)

I think it is way too complicated to follow. 

And this is the post for Fedora
[http://forums.fedoraforum.org/showthread.php?t=282998](http://forums.fedoraforum.org/showthread.php?t=282998)


I still don't know the answer. 

Thanks a lot!

---

