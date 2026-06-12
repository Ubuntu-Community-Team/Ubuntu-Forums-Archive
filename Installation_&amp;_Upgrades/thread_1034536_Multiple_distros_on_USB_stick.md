---
title: "Multiple distros on USB stick"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by aeronotix on 2009-01-08
I have an 8GB Flash drive which I'd like to contain the following; Ubuntu Live, BackTrack 3 and Damn Small Linux. With the rest of the space taken up by programs and other media. 

Does anybody know a way I can accomplish this?

---

### Post by thomas228 on 2009-01-08
> **aeronotix said:**
> I have an 8GB Flash drive which I'd like to contain the following; Ubuntu Live, BackTrack 3 and Damn Small Linux. With the rest of the space taken up by programs and other media. 

Does anybody know a way I can accomplish this?

Hi

I've installed ubuntu 8.04 and a 2GB Swap on an 8GB flash drive.

By the time I updated to the present version (-22) the drive only had 3 GB remaining.  Are you sure an 8GB is large enough to do what you want.  Even using the same swap for all three OS it appears to be a pretty tight fit.  16 GB thumbs have really come down in price

For a viable thumb installation I used an 8GB thumb using 2 GB as swap and 6GB for 8.04.
The threads I used were [http://ubuntuforums.org/showthread.php?t=1017566&page=2](http://ubuntuforums.org/showthread.php?t=1017566&page=2) post #14 and [http://ubuntuforums.org/showthread.php?t=1021772](http://ubuntuforums.org/showthread.php?t=1021772)

If you need more info on how I installed 8.04 let me know.

Good luck 

Tom

---

### Post by thomas228 on 2009-01-09
> **aeronotix said:**
> I have an 8GB Flash drive which I'd like to contain the following; Ubuntu Live, BackTrack 3 and Damn Small Linux. With the rest of the space taken up by programs and other media. 

Does anybody know a way I can accomplish this?

Hi again

Reread your post and came to the conclusion that my first response is not what you are trying to do.

Here's what I think might work though.

Use gparted from your ubuntu live cd to partition your flash drive into 4 parts and format each partition according to its use.  Ext2 or ext3 for ubuntu/linux partitions and fat 32 for your everything else partition 

Install Ubuntu Live in the first partition, BackTrack 3 and Damn Small Linux in the next 2 partitions.

Use ubuntu 8.10 usb option or unebootin as appropriate 

Install grub on the first partition so you can edit ubuntu's /boot/grub/menu.lst as needed for your bios bootup of your usb stick.  Ubuntu will be hd0,0  BackTrack 3 will be hd0,1 and  Damn Small Linux will be hd0,2

I hope that gives you enough to accomplish what you want.

Good luck

Tom

---

### Post by aeronotix on 2009-01-09
This is exactly what I thought I'd have to do. I thought for some reason I would be wrong in doing so. 

Thanks for the reply. 

So here's what I'm going to do, install grub on primary partition along with Ubuntu (Ubuntu will install Grub for me I beleive?) then the other two OS's in the others, then edit menu.list to accomodate them all. This is correct?

---

### Post by thomas228 on 2009-01-09
> **aeronotix said:**
> This is exactly what I thought I'd have to do. I thought for some reason I would be wrong in doing so. 

Thanks for the reply. 

So here's what I'm going to do, install grub on primary partition along with Ubuntu (Ubuntu will install Grub for me I beleive?) then the other two OS's in the others, then edit menu.list to accomodate them all. This is correct?


Hi again,

That's the way I'd try. Make sure you set up your partitions first

Good luck
Tom

---

### Post by thomas228 on 2009-01-09
> **aeronotix said:**
> This is exactly what I thought I'd have to do. I thought for some reason I would be wrong in doing so. 

Thanks for the reply. 

So here's what I'm going to do, install grub on primary partition along with Ubuntu (Ubuntu will install Grub for me I beleive?) then the other two OS's in the others, then edit menu.list to accomodate them all. This is correct?


Hi again,

That's the way I'd try. Make sure you set up your partitions for everything first.There are lots of good help out there if you need it.

Good luck

Tom

---

### Post by aeronotix on 2009-01-10
Oke doke, here's where I am at.

I booted into the GParted Live CD and partitioned the USB stick into four partitions.

At the moment I don't have access to a Linux machine so it might be different on that system, but this Vista machine is only seeing the first partition and UNetBootIn also is doing the same thing, whcih is worrying since I wanted to use UNetBootIn to install two out of the three OS's.

Is there something that I missed in GParted because I saw an option to place a drive label but the only way I could do that was if I had the partition as an extended drive and it gave me no option as to what filesystem I could use for them extended partitions (Which I need them to be ext2/ext3 don't I?)

Thanks.

Aaron.

---

### Post by Saghaulor on 2009-05-04
I believe Windows does not natively support reading ext2 and ext3 partitions. You'll have to find a third party software to support that. That may be why you're not seeing the partitions in the first place.

Regarding a swap, I don't recommend using your flash drive for swap. Flash drives have a limited life cycle of writes, so using it for a swap is guaranteed to reduce the lifespan.

One thing that is unclear to me, I believe that you need some sort of app that tells the computer that the flash drive is a bootable device. Then you need it to load Grub, so that you can select which os you would like to use. I'm not sure how all of that goes down. It seems like Unetbootin does a Grub like function, but I don't think that it does.

Any clarifications would be most appreciated.

---

