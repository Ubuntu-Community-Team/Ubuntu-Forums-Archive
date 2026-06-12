---
title: "Software Raid on 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by ignisuti on 2009-11-06
Hello, I've tinkered with Ubuntu in the past, but am relatively still a newbie. 

I found this terrific write-up for installing a Raid 1 system in Ubuntu that I want to follow: [http://tuxtraining.com/2008/11/04/setting-up-software-raid-in-ubuntu-server]("http://tuxtraining.com/2008/11/04/setting-up-software-raid-in-ubuntu-server")

The problem appears to be that it was written or an older version of Ubuntu and the menus appear to have changed. I'm installing Ubuntu 9.10 from a CD and choose to Manually configure my drives on the partition manager screen. However, my options are different than in the write-up and I don't see any options for Raid. Please help.

---

### Post by Lvcoyote on 2009-11-06
If your setting the motherboards BIOS to raid, expect 9.10 to break that array every time you boot to it.... something is broken there.

---

### Post by ignisuti on 2009-11-06
I didn't setup anything in BIOS. I just want to do a software Raid 1.

Can I trick it by trying Ubuntu without any changes, edit the partitions there, and then install Ubuntu 9.10 on the that?

---

### Post by Cr0n_J0b on 2009-11-06
I'm not sure about this...but you might try this.

Boot to the liveCD,
THIS METHOD WILL DELETE DATA ON THE DRIVES!!!!

ALERT!!! READ ABOVE NOTE!!!!

assumes disks are same size and drives are sda, sdb
format your disks for raid

example:  fdisk /dev/sda
choose "n"
choose "P"
choose "1"
choose defaults for size and you will use the entire capacity
now choose "t"
type "fd"
and finally select "w"

do this for the second drive

in the end you should type fdisk -l and see 2 partitions:  sda1 and sdb1...for example

this will partition your drives for RAID.

load mdadm:  apt-get install mdadm

create your RAID volume

mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1 /dev/sdb1

you now have a raid device.

Now select the install ubuntu...and hopefully, you will see your volume in the partition manager...this is the part that I'm unclear on.  I'm having a ton of issues installing ubuntu 9.10 as it is...and I've never tried this method, but it's what I would do in the same situation.

---

### Post by ignisuti on 2009-11-06
Cron_Job, you're great!! That worked!  :KS

I had to add on just a touch because I setup a 10GB ROOT Raid 1 and also a 25GB HOME Raid 1.

It all seemed to work and is installing right now. Cheers!

---

### Post by ignisuti on 2009-11-06
Darn! It loaded 9.10 100%, but now it won't boot to it.

The Ubuntu icon shows briefly, then a black screen appears. It just sits there doing nothing until I hit a key on the keyboard and see a bunch of stuff about initramfs, busybox, and much more... 

Please help.

---

### Post by P.KO on 2009-11-06
Hi,

I also tried to install using the live CD to no avail.

Managed to install on raid 1 using the alternate.

Anyhow to me the support for raid seems to be a little flaky.

Grub couldn't be installed to /dev/md0 as the installer suggested and I had to manually change it to (hd0).

---

### Post by ignisuti on 2009-11-06
> **P.KO said:**
> Hi,

I also tried to install using the live CD to no avail.

Managed to install on raid 1 using the alternate.

Anyhow to me the support for raid seems to be a little flaky.

Grub couldn't be installed to /dev/md0 as the installer suggested and I had to manually change it to (hd0).

Would that be part of my problem? Would changing GRUB to hd0 fix my booting problem? If so, how can I do that?

---

### Post by Cr0n_J0b on 2009-11-06
Sorry, I forgot to mention the thing about GRUB.  I've always had problems understanding exactly what needs to be done to make GRUB work correctly...especially when you have multiple drives and RAID.

I would try to setup GRUB on the md device it if lets you...otherwise choose the first drive in the system.

---

### Post by falconindy on 2009-11-06
The "legacy" solution has always been to use a small (50-100mb) partition that uses a simple filesystem like ext2 for /boot if you're using LVM or MDADM. From there, you can hook the initramfs of the system on the array.

The other option is to use Grub2, which will recognize the array without the need for a separate boot partition.

The Arch Linux [wiki](http://wiki.archlinux.org/index.php/Installing_with_Software_RAID_or_LVM) on MDADM and LVM might be of use to you.

---

### Post by ignisuti on 2009-11-06
There are lots of posts out there saying that there is an issue with raid because 9.10 uses GRUB2. 

I know absolutely NOTHING about GRUB other than it's some sort of system that handles booting. So, most of those posts are a little over my head.

I'll do a bit of research to see if I can figure out how to load md0. Should I be focusing on loading into GRUB or GRUB2?

---

### Post by ignisuti on 2009-11-06
> **falconindy said:**
> The "legacy" solution has always been to use a small (50-100mb) partition that uses a simple filesystem like ext2 for /boot if you're using LVM or MDADM. From there, you can hook the initramfs of the system on the array.

The other option is to use Grub2, which will recognize the array without the need for a separate boot partition.

The Arch Linux [wiki](http://wiki.archlinux.org/index.php/Installing_with_Software_RAID_or_LVM) on MDADM and LVM might be of use to you.

I didn't see this post before my last post. Isn't GRUB2 already loaded on there because I used 9.10?

---

### Post by falconindy on 2009-11-06
> **ignisuti said:**
> I didn't see this post before my last post. Isn't GRUB2 already loaded on there because I used 9.10?
Is your GRUB config in menu.lst or grub.cfg?

Re-reading your initial post, it sounds like you need to use the alternative install CD.

---

### Post by ignisuti on 2009-11-06
> **falconindy said:**
> Is your GRUB config in menu.lst or grub.cfg?

Re-reading your initial post, it sounds like you need to use the alternative install CD.

Where do I look for menu.lst or grub.cfg?

My understand now is that the Alternative install CD would have saved me some trouble, but would have ended up with the same result I have now, right?

---

### Post by falconindy on 2009-11-06
> **ignisuti said:**
> Where do I look for menu.lst or grub.cfg?

My understand now is that the Alternative install CD would have saved me some trouble, but would have ended up with the same result I have now, right?
menu.lst or grub.cfg would be under /boot/grub.

The alternate install CD allows you to create logical volume groups and MDADM arrays at install time rather than having to boot off a liveCD and partition manually beforehand.

If you still have problems booting directly from the array, then you'll need to make a separate /boot partition that uses a simple file system. I'm a little surprised Karmic shipped with a **beta** bootloader that replaced an otherwise functional bootloader. Even "better", Grub 1.97 was released on the 25th of October and it still hasn't made it into Karmic yet.

---

### Post by ignisuti on 2009-11-06
I installed Karmic 9.10 that I downloaded just a couple days ago. I checked it it says I have Grub 1.97 installed... So, it must have recently slipped in there. Although it did say Grub 1.97 Beta 4.

I ran home over lunch and took a look at my /boot/grub folder. There was a file in there, but it wasn't either of the two you mentioned. I made sure to show hidden files and still didn't see it. 

I then opened the Utility Disk Manager and noticed that my raids (md0 & md2) were no longer setup. All the drives appeared to be setup ready for raid, just md0 & md2 were no longer present...?

The Alternate Boot CD is downloading now. I'll start over and give it a try later tonight. If that still fails, I'll try the separate boot partition trick.

---

