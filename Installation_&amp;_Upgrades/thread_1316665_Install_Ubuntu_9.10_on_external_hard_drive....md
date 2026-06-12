---
title: "Install Ubuntu 9.10 on external hard drive..."
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by ppp0 on 2009-11-06
Hello guys!
I wonder how i can install ubuntu on an external harddrive?
I have Win7 on my sony vaio laptop and WD passport.
So... I've tried to install it on wd:
Created free unused space 20GB on ext. drive then i\ve inserted live cd and installed it on ext. drive. But when i've restarted laptop it showed like (oh i dont remember) "ubuntu rescue>" (grub2 has gone but why it's installed on laptop? maybe...) and that's all. And it killed Win7 boot (which was fixed later)
I googled and found some ways to install it on laptop but no result. So can anyone explain how to do it with Win7 ?
Oh thanx :)

---

### Post by Mighty_Joe on 2009-11-06
> **ppp0 said:**
> And it killed Win7 boot (which was fixed later)


That sounds like you installed GRUB to the laptop drive and not the external drive.  On the last step of the install, there is a button marked "Advanced".  That gives you the choice of where to put GRUB.

---

### Post by ppp0 on 2009-11-06
> **Mighty_Joe said:**
> That sounds like you installed GRUB to the laptop drive and not the external drive.  On the last step of the install, there is a button marked "Advanced".  That gives you the choice of where to put GRUB.

Yes yes ! LAter i'vew found "advanced" button on step 7 and now it all ok thanks!

---

### Post by lesodk on 2010-02-12
Thank you for the quick answer. When i install Ubuntu 9.10 from the live CD i install it to dev/sdb. The same goes for the grub, from the advanced menu.

When i boot from the USB it start grub, but when i select the ubuntu entry it says "error: no such device  : aca365...... ".

Can you give me any idea of what to do?

Thanks!

---

### Post by ppp0 on 2010-02-15
you just need to reconfigure grub

---

### Post by sync00 on 2010-02-15
I have an external drive that I want to install Ubuntu on. I want to have 1 ntfs partition and 2 ext3 partitions. I want to set up the partitions using Acronis software in Windows because I am familiar with that software.

When I create the Ubuntu partition, do I have to do anything to make it bootable?

---

### Post by darkod on 2010-02-16
> **sync00 said:**
> I have an external drive that I want to install Ubuntu on. I want to have 1 ntfs partition and 2 ext3 partitions. I want to set up the partitions using Acronis software in Windows because I am familiar with that software.

When I create the Ubuntu partition, do I have to do anything to make it bootable?

No, but linux does not use by default existing partitions even if they are ext3/ext4. You will still need to go into manual partitioning during the install and set their mount points and filesystem. So you might as well use the ubuntu installer partitioner. Besides, if you are planning of using linux don't avoid starting to learn its partitioners.

---

### Post by sync00 on 2010-02-16
> **darkod said:**
> No, but linux does not use by default existing partitions even if they are ext3/ext4. You will still need to go into manual partitioning during the install and set their mount points and filesystem. So you might as well use the ubuntu installer partitioner. Besides, if you are planning of using linux don't avoid starting to learn its partitioners.
I did discover that during the install.

Does Grub need to be in the first partition? I choose to put it in the second partition, which is where I installed Ubuntu. When I try to boot from the drive the BIOS says that Bootmgr is missing.

---

### Post by darkod on 2010-02-16
> **sync00 said:**
> I did discover that during the install.

Does Grub need to be in the first partition? I choose to put it in the second partition, which is where I installed Ubuntu. When I try to boot from the drive the BIOS says that Bootmgr is missing.

NO. Grub2 needs to be in the MBR (Master Boot Record) of the ext hdd. But I guess you discovered that too now. :)

You can't boot from it like this. But you don't have to reinstall ubuntu completely, you can just add gub2 to the MBR now.

Boot the live desktop and in terminal check the ubuntu root partition with:
sudo fdisk -l

For example, /dev/sdb5 will be the Linux partition, and /dev/sdb the ext hdd as device. In that case you would reinstall with:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

If you are confused by the fdisk results post them here and I'll adjust those commands if necessary.

After that you should be able to boot OK.

---

### Post by rimshot4 on 2010-02-16
When I first upgraded to Linux I put Ubuntu on an external HD. It worked well, but in my experience moving Ubuntu from a USB HD to my internal HD made it much faster. 

Either way it was lightening compared to Windows.

---

### Post by darkod on 2010-02-16
> **rimshot4 said:**
> When I first upgraded to Linux I put Ubuntu on an external HD. It worked well, but in my experience moving Ubuntu from a USB HD to my internal HD made it much faster. 

Either way it was lightening compared to Windows.

I'm not some great expert but it makes perfect sense. :) USB hdd transfer rates are not even near to int hdd transfer rates. And it will stay that way for a while it seems.

What I'm intrigued right now, is how much performance you gain from SSD and is it worth the huge price tag. :)

---

### Post by sync00 on 2010-02-16
> **darkod said:**
> NO. Grub2 needs to be in the MBR (Master Boot Record) of the ext hdd. But I guess you discovered that too now. :)

You can't boot from it like this. But you don't have to reinstall ubuntu completely, you can just add gub2 to the MBR now.

Boot the live desktop and in terminal check the ubuntu root partition with:
sudo fdisk -l

For example, /dev/sdb5 will be the Linux partition, and /dev/sdb the ext hdd as device. In that case you would reinstall with:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

If you are confused by the fdisk results post them here and I'll adjust those commands if necessary.

After that you should be able to boot OK.
The live disk is amazing. I'm using it to post this.

Here are the fdisk results.

```
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc27c4f8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       34639   278237735+   7  HPFS/NTFS
/dev/sdc2           34640       60801   210146265    5  Extended
/dev/sdc5           34640       38287    29302528+  83  Linux
/dev/sdc6           38557       60801   178682931   83  Linux
/dev/sdc7           38288       38556     2160711   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by darkod on 2010-02-16
Both sdc5 and sdc6 are linux partition and they can both be root. The other is probably /home. Since you obviously created the setup manually, do you know which partition is root?

If it's /dev/sdc5 use that in the first command, if not use /dev/sdc6. The second command stays the same.

sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc

That should sort it out. Reboot without the cd, try booting from the usb disk.

---

### Post by sync00 on 2010-02-16
> **darkod said:**
> Both sdc5 and sdc6 are linux partition and they can both be root. The other is probably /home. Since you obviously created the setup manually, do you know which partition is root?

If it's /dev/sdc5 use that in the first command, if not use /dev/sdc6. The second command stays the same.

sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc

That should sort it out. Reboot without the cd, try booting from the usb disk.
I installed Ubuntu to sdc5. Does that make it root? sdc5 is where I had the installer put grub.

---

### Post by darkod on 2010-02-16
> **sync00 said:**
> I installed Ubuntu to sdc5. Does that make it root? sdc5 is where I had the installer put grub.

It doesn't matter where you put grub (by the way it should have been to /dev/sdc). When you were using the manual install you assigned mount points like /, /home, swap to the partitions. / is root partition, the main one where the system resides, like C: in windows. That's what you're after.

PS. In the worst case, if you don't remember it, there is a script you can run which will show it, but if you did it manually you should know. :)

---

### Post by sync00 on 2010-02-16
> **darkod said:**
> It doesn't matter where you put grub (by the way it should have been to /dev/sdc). When you were using the manual install you assigned mount points like /, /home, swap to the partitions. / is root partition, the main one where the system resides, like C: in windows. That's what you're after.

PS. In the worst case, if you don't remember it, there is a script you can run which will show it, but if you did it manually you should know. :)
Thanks. :)

sdc5 is the root and it is now booting.

When I look at the other ext3 partition in File Browser it says that the permissions can't be determined.

---

### Post by darkod on 2010-02-16
> **sync00 said:**
> Thanks. :)

sdc5 is the root and it is now booting.

When I look at the other ext3 partition in File Browser it says that the permissions can't be determined.

sdc6 is huge, maybe 5x the sdc5. Too bad if you can't use it depending what you did during setup. If feeling like it, do the install all over. That's how you practice. :)

Otherwise it seems that space will remain wasted until your next install.

---

### Post by sync00 on 2010-02-16
Putting data on sdc6 is actually the main reason I installed Ubuntu.

I did not do anything with sdc6 during the install. Did I need to specify a mount for it? If so, is that something I can do now.

I did not have a problem using that partition from Ubuntu within VirtualBox. But that was before I did this install.

---

### Post by darkod on 2010-02-16
> **sync00 said:**
> Putting data on sdc6 is actually the main reason I installed Ubuntu.

I did not do anything with sdc6 during the install. Did I need to specify a mount for it? If so, is that something I can do now.

I did not have a problem using that partition from Ubuntu within VirtualBox. But that was before I did this install.

Yes, you need to mount it first in order to work with it. If you used it from VB it might have some permissions clash, I don't know.
It should be in Places, like 80GB Filesystem. Click on it and it should mount it. Check if you can see the data on it.
If that is fine, you can consider making a permanent mount point for it that will be automatic every boot.

---

### Post by sync00 on 2010-02-16
> **darkod said:**
> Yes, you need to mount it first in order to work with it. If you used it from VB it might have some permissions clash, I don't know.
It should be in Places, like 80GB Filesystem. Click on it and it should mount it. Check if you can see the data on it.
If that is fine, you can consider making a permanent mount point for it that will be automatic every boot.
It showed up automatically on the desktop, which I think means it is mounted.

The partition is empty. I can't create a folder in it and when I copy to it permission is denied.

[edit] I found that I can work with the partition using 
sudo nautilus

---

### Post by Sgt_P on 2010-02-16
> **darkod said:**
> NO. Grub2 needs to be in the MBR (Master Boot Record) of the ext hdd. But I guess you discovered that too now. :)
 
You can't boot from it like this. But you don't have to reinstall ubuntu completely, you can just add gub2 to the MBR now.
 
Boot the live desktop and in terminal check the ubuntu root partition with:
sudo fdisk -l
 
For example, /dev/sdb5 will be the Linux partition, and /dev/sdb the ext hdd as device. In that case you would reinstall with:
 
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
 
If you are confused by the fdisk results post them here and I'll adjust those commands if necessary.
 
After that you should be able to boot OK.
Ok, this has been really helpful but I have one difference from the original poster's issue that is causing me problems - any advice is greatly appreciated!
 
My setup: Macbook Pro, Snow Leopard, with external firewire drive. Used 9.10 alt disc to install LVM, fully enctrypted partition. Install went fine, was asked where to put GRUB at the end and I chose (hd,1) since the external is my only other harddrive. 
 
My problem is that I cannot boot the system. I tried holding alt during boot but doesn't show up, and I tried installing rEFIt and it sees it, but gives an 'operating system missing' error. It doesn't look like it even gets to stage 1 of GRUB.
 
When I boot to live CD and open gparted it shows an unformatted 97kb partition with a bios_grub flag, a 188mb ext2 partition, and the 250gb luks encrypted partition. If I try to mount the drive in order to run fdisk it says the drive is encrypted and asks for a password - but the password box won't allow me to type the full password I created when encrypting! The password is 35 characters, but the password text field stops at around 20. Sigh.
 
I know I'm missing something, can anyone help?

---

### Post by darkod on 2010-02-16
> **Sgt_P said:**
> Ok, this has been really helpful but I have one difference from the original poster's issue that is causing me problems - any advice is greatly appreciated!
 
My setup: Macbook Pro, Snow Leopard, with external firewire drive. Used 9.10 alt disc to install LVM, fully enctrypted partition. Install went fine, was asked where to put GRUB at the end and I chose (hd,1) since the external is my only other harddrive. 
 
My problem is that I cannot boot the system. I tried holding alt during boot but doesn't show up, and I tried installing rEFIt and it sees it, but gives an 'operating system missing' error. It doesn't look like it even gets to stage 1 of GRUB.
 
When I boot to live CD and open gparted it shows an unformatted 97kb partition with a bios_grub flag, a 188mb ext2 partition, and the 250gb luks encrypted partition. If I try to mount the drive in order to run fdisk it says the drive is encrypted and asks for a password - but the password box won't allow me to type the full password I created when encrypting! The password is 35 characters, but the password text field stops at around 20. Sigh.
 
I know I'm missing something, can anyone help?

Unfortunately I know absolutely nothing about the Mac boot process. :(
But I have few pointers, and with your Mac knowledge, we might figure it out.

1. LVM needs separate /boot partition even if we are talking about a PC. With Mac I guess you need it even more. So, delete all the partitions on the ext hdd, and start first by creating 200MB or 300MB primary partition, ext4 or what ever you want, mount point /boot. Then create another primary from the rest of the hdd and use it as physical device for the LVM, if that's what you want.

2. I know it's double work, but why not try to first install without any encryption just to make sure that's not getting in the way. Once you have the process flow figured out, retry with encryption.

3. If you can boot straight from the ext hdd avoiding any Mac booting process, I guess that's what you need to do. As I said, I know nothing about Macs.

Got any ideas?

---

### Post by sync00 on 2010-02-16
> **rimshot4 said:**
> When I first upgraded to Linux I put Ubuntu on an external HD. It worked well, but in my experience moving Ubuntu from a USB HD to my internal HD made it much faster. 

Either way it was lightening compared to Windows.
I just installed Ubuntu on my internal drive. It takes 52 seconds to boot which is about the same as a new Win 7 install.

In Win 7 I copied a 3.4GB file from an ntfs partition on external drive A to an ntfs partition on external drive B. It took 172 seconds.

In Ubuntu I copied the same file on external drive A to an ext3 partition on external drive B. It took 212 seconds.

---

### Post by levanapr on 2010-04-14
Sorry for being a pain, I have a rather simple question. I myself want to perform a Ubuntu install on a external HDD, to use with my Laptop -  HP Pavilion dv7-2220eq with a Windows 7 currently running. I searched all over the web for a thorough guide, found quite a lot of them, all for different versions, using different external HDDs. However I did not quite find one which would fit what I need, or come specifically close to it. Maybe by bad, just wanted to ask whether someone could point me to a step by step guide, or a general manual. 
Thanks a lot!

---

### Post by Mighty_Joe on 2010-04-15
I posted links to the steps I used [in this topic]("http://ubuntuforums.org/showthread.php?t=1193680&highlight=partition+table"), but there really isn't much to it:
-boot from Live CD
-at the partition step, select your external drive.  If you have enough RAM, don't create a swap partition as it will be slow via USB.
-at the last step you will be given a summary of your options. Click the "advanced" button and select your external drive as the destination for GRUB.

---

### Post by GazuliGod on 2010-05-09
> **levanapr said:**
> Sorry for being a pain, I have a rather simple question. I myself want to perform a Ubuntu install on a external HDD, to use with my Laptop -  HP Pavilion dv7-2220eq with a Windows 7 currently running. I searched all over the web for a thorough guide, found quite a lot of them, all for different versions, using different external HDDs. However I did not quite find one which would fit what I need, or come specifically close to it. Maybe by bad, just wanted to ask whether someone could point me to a step by step guide, or a general manual. 
Thanks a lot!

Ya im having a simmilar issue. i have a Hp pavillion dv6-1334us with windows 7 home prem. i Installed ubuntu 9.4 desktop on my 30gb external and i also choose /dev/sdb1 (external hard drive) as the destination for grub. when i pressed f9 to go to boot device order the harddrive wasnt there. i went into partition manager on windows and it found the hard drive. so its not broken its just that the computer isn't letting me choose it to boot from. Advice anyone?

---

### Post by GazuliGod on 2010-05-22
I've also tried this with 10.04 and i am having the same issue. Would it work if i don't install the grub bootloader?

---

