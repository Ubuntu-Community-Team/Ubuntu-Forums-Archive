---
title: "Can't see boot partition. Installation failed ;("
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by xmod on 2009-07-11
I'm trying to install Ubuntu netbook remix on my Lenovo S10 with Windows XP (so I'll use Linux as my 2nd OS).
So make 20 GB of free space.
I follow next instructions:
[http://jager.no/news/ubuntu-netbook-remix-with-encrypted-root](http://jager.no/news/ubuntu-netbook-remix-with-encrypted-root)

[SIZE=3][COLOR=Red]**but I write sda6 instead of sda1 and sda7 instead of sda2**[/COLOR][/SIZE].


[B][IMG]http://www.sait.kiev.ua/linux/Screenshot-1.png[/IMG]
[/B]



**Intro**

 The UNR (Ubuntu Netbook Remix) install image does not contain the needed options to create the encrypted root file system from the installer. But doing it manually is easy and also gives you more freedom over the encryption options you want use. If you follow this step by step guide you should end up with a very secure netbook.
 **Step 0. Boot UNR. Create Partitions**

 Boot the UNR live-image. Open a terminal from Accessories menu.
 Create two partitions on the disk you want to use:
 Where /dev/sda is your disk
 $ sudo cfdisk /dev/sda In cfdisk:
 
[LIST]
[*]Create a boot partition (500mb) and mark it as bootable and type 83 (Linux)
[*]Create a second partition with the rest of the space and set it's type to 8e (Linux LVM)
[/LIST]
  
 [B]Step 1. Create Crypto device
[/B]

  
 Create crypto device and open it.
 **Step 1.1. Prerequisites**

 $ sudo -i
# apt-get install lvm2 cryptsetup **Step 1.2. Format crypto device**

 This command creates a crypto-device on the second partition of sda.  I use aes-xts-plain here as it's currently the safest cipher mode. (default in ubuntu is: aes-cbc-essiv:sha256). There are many options available here. For example you may want to use twofish or serpent encryption algorithm instead of aes. If you decide to not to use aes remember to load the right modules in step 5.
 # cryptsetup luksFormat -s 256 -c aes-xts-plain /dev/sda2 **Step 1.3. Open Crypto device**

 Open the new crypto-device as sda2_crypt.
 # cryptsetup luksOpen /dev/sda2 sda2_crypt **Step 2. Create LVM Groups**

 Use LVM commands to split it into root and swap.
 # pvcreate /dev/mapper/sda2_crypt
# vgcreate vg /dev/mapper/sda2_crypt
# lvcreate -L 512M -n swap vg
# lvcreate -l 100%FREE -n root vg Now you have a encrypted place for / and swap.
 [B]Step 3. Create file systems
[/B]

  Now we need to create file systems on the encrypted LVM back end, I use ext4 here for / since it's new and exiting. /boot still should be ext2 though.
 # mkfs.ext4 /dev/mapper/vg-root
# mkfs.ext2 /dev/sda1
# mkswap /dev/mapper/vg-swap  
 **Step 4. Install Ubuntu Netbook Remix**

 Exit the terminal and start the installer. It's in the Favorites menu. Just install as you normally would but select manual partitioning. In the partitioning screen select /dev/mapper/vg-root. Left click -> edit and select / as mount point. [COLOR=Red]Do the same for /boot.

[COLOR=Blue][IMG]http://www.sait.kiev.ua/linux/Screenshot.png[/IMG]

[SIZE=4]So as you can see I have no partition to select /boot as mount point! What's I'm doing wrong? 

Thanks for any help![/SIZE][/COLOR]


[/COLOR]

---

