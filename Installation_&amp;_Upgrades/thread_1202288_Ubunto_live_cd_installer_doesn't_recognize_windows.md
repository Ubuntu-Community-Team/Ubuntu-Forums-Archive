---
title: "Ubunto live cd installer doesn't recognize windows Me!!"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by Aidenstar on 2009-07-02
Really want to install ubunto. I have a ubunto live cd and the installation process moves smoothly until the partitioning step, where it says that no operating system is detected. I am currently running windows Me...i know ancient right...that is one of the reasons why i want to upgrade to ubunto. So i dont know what to do from this part.. i dont want to delete windows...i would much prefer to dual boot. Does anyone know why it says that i dont have an operating system.

---

### Post by snek on 2009-07-02
Wow, I haven't heard of anyone actually still running Windows ME... 
Your pc is not crashing the whole time? I remember when it was new, it was possibly the worst Windows version I ever used.. BSOD's all the time :P

I am not 100% sure Ubuntu actually recognises Windows in the partitioning step. Maybe someone else can verify this? It might be that it only searches for Linux installations.

Have you made a new partition where you can install Ubuntu? 
I think you can fix the GRUB menu (GRUB is the bootloader, menu found in /boot/grub/menu.lst) to point to your old Windows partition and things should work ok then.

---

### Post by Aidenstar on 2009-07-02
Yes, I know it's almost impossible to find any help with Windows Me...seeing as everyone has already upgraded. It's not the best os that's why I'm anxious to get ubunto...but I'm not ready to fully commit to it. 

I haven't made a new partition yet...to be honest I'm not really sure how...I was hoping there would be enough space on my hardrive that I wouldn't have too, I was planning to use the ubunto installer to just allocate the free space to install ubunto. But I didn't expect for it not to recognize Windows Me...Which I do know it recognizes others such as vista and xp. It wants me to install ubunto using the entire hard drive. Which I dont want to do.

I don't think I fully understand what GRUB is I'm kinda new at this, and I really hope you can help me...

---

### Post by oldos2er on 2009-07-02
What are the hardware specs?

---

### Post by Aidenstar on 2009-07-02
Compaq Presario 5002US 
800 MHz AMD ® Duron &#8482; Processor
200 MHz system bus
40.0 GB 2 UltraDMA Hard Drive
256.0MB Ram

If you need any more specifications please ask, sorry probably gave you too much info. Thanks for any help you can give me. I'm getting desperate...

---

### Post by aidanandrach on 2009-07-02
I'm very new to this as well, so might be barking up completely the wrong tree here - but don't you need to shrink your existing partition first?

I don't think that Ubuntu can be installed on to a FAT32 partition (which I think is what WinME uses from memory), which means that you need to shrink that partition to create some unpartitioned free space, then create your new ext3 or ext4 partition there.  Then you can install Ubuntu on to that new partition...

That's my experience anyway - someone will hopefully correct me if I'm mistaken.

Aidan.

---

### Post by oldos2er on 2009-07-02
I'm surprised you got the LiveCD to work with only 256MB RAM.

 While you're booted from the LiveCD, can you open a terminal (Applications, Accessories, Terminal), and post the output from this command:
```
sudo fdisk -l
```

---

### Post by Aidenstar on 2009-07-02
Yes I did get the Live CD to work albeit very slowly...I'm anxious to get to see ubunto's full potential, at its appropriate speed.

Ok, here is the output:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x0000675f

   Device Boot        Start            End           Blocks             Id          System
/dev/sda1   *                1              4791       36219928+      c        W95 FAT32 (LBA)
/dev/sda2                4792            5170         2865240            f         W95 Ext'd (LBA)
/dev/sda5                 4792            5170         2865208+        c        W95 FAT32 (LBA)

Hope that helps...

---

### Post by Aidenstar on 2009-07-02
Maybe but do you know what I could use to shrink the partition. Would I have to use some type of software, Because I'm not sure WinMe has the capability to do that itself.

---

### Post by aidanandrach on 2009-07-03
> **Aidenstar said:**
> Maybe but do you know what I could use to shrink the partition. Would I have to use some type of software, Because I'm not sure WinMe has the capability to do that itself.

Gparted (on the LiveCD) will do it.

---

### Post by Aidenstar on 2009-07-03
Do I have to download Gparted or is it already on the liveCD...sorry I'm really new at this if you haven't noticed yet. Also, is it easy to use I don't want to go messing with my partitions and fry my computer. Thanks for any help you can give me...

---

### Post by sdlynx on 2009-07-03
If you go to System > Administration > Partition Editor that will start GParted

---

### Post by Aidenstar on 2009-07-03
Thanks I will give it a shot...

---

### Post by Aidenstar on 2009-07-03
Ok, i tried it...but it says unallocated 37.27 GiB. I still don't think it recognizes I have an operating system on it. Do you have any idea what the problem is?

---

### Post by sdlynx on 2009-07-03
Oh very strange.  In that case I'm not sure what you should do (probably just because I don't have enough experience).  Good luck though.

Its not that it does not recognize the operating system, it seems to not even be recognizing the partition that windows is on...

---

### Post by Aidenstar on 2009-07-03
Thanks for your incite... I hope someone else can help fix this problem.

---

### Post by fballem on 2009-07-03
**Before you go any further** please make sure that you have a current backup of all of your data.

I wish I knew enough to help you, but this warning is my only contribution.

---

### Post by Aidenstar on 2009-07-03
Thanks I guess... I've already loaded back to windows everything is still intact.

---

### Post by fballem on 2009-07-03
> **Aidenstar said:**
> Ok, i tried it...but it says unallocated 37.27 GiB. I still don't think it recognizes I have an operating system on it. Do you have any idea what the problem is?

If I'm reading your note correctly, then you may be on your way.

Could you please restart the installer. When it gets to the partition page, you should have three options:

1) Use the Entire Disk (Automatic). **See Out-of-the-Box below**
2) Use Existing Partitions. Please have a look, there should be two partitions, a small one of about 2 - 3 Gigabytes and a larger one of 37.27 Gigabytes. If this is the case, then you will want to install ubuntu on the large partition.
3) Manual Partition. **You don't want this option.**

**Out-of-the-Box**

Thinking outside of the box for a moment, if you do have an external backup of your data, including e-mails, and you have legal copies of Windows ME and your other software, then you may want to try ubuntu as your only operating system, in which case select Use the Entire Disk (Automatic).

Before you do this, it would be helpful to have a list of the sofware that you use and would continue to need. It would also be helpful to let us know if you use either Outlook or Outlook Express for your e-mails, since these would need to be converted and stored on your external backup prior to leaving Windows.

Hope that this helps,

---

### Post by Aidenstar on 2009-07-03
Ok, did what you said, when I got to the partitioning page, it still said no operating system is found on this computer. It only gave me two options:

1: To install ubunto using the entire hard disk.
2: Manual partition

The good news is that I don't use outlook or any other programs besides microsoft word, powerpoint, excel...etc But as I understand it ubunto already has the equivalent of these programs already installed. 

The bad news is that I haven't had the WinMe CD for some time. I'm using the first computer I have ever bought without ever having upgraded the os, and I have moved a few times since getting it. Basically what I'm saying is that I have misplaced the CD since first buying the computer in I think 2001. So if I delete windows it is for good.

But I am willing to do that. Really the only thing I care about in windows are my pictures, which I already have on a usb stick. I'm assuming that those won't be hard to switch over. I can bare to sacrifice everything else I have on there.

Also, I'm concerned about the learning curve of ubunto, I would like to know it its pretty steep. Obviously it doesn't look like dual booting my computer is an option, so I'm preparing myself to completely deleting it in favor of ubunto. 

I would appreciate any incite you can give me, and whether or not you think that would be a mistake.

---

### Post by fballem on 2009-07-03
> **Aidenstar said:**
> Ok, did what you said, when I got to the partitioning page, it still said no operating system is found on this computer. It only gave me two options:

1: To install ubunto using the entire hard disk.
2: Manual partition

The good news is that I don't use outlook or any other programs besides microsoft word, powerpoint, excel...etc But as I understand it ubunto already has the equivalent of these programs already installed. 

The bad news is that I haven't had the WinMe CD for some time. I'm using the first computer I have ever bought without ever having upgraded the os, and I have moved a few times since getting it. Basically what I'm saying is that I have misplaced the CD since first buying the computer in I think 2001. So if I delete windows it is for good.

But I am willing to do that. Really the only thing I care about in windows are my pictures, which I already have on a usb stick. I'm assuming that those won't be hard to switch over. I can bare to sacrifice everything else I have on there.

Also, I'm concerned about the learning curve of ubunto, I would like to know it its pretty steep. Obviously it doesn't look like dual booting my computer is an option, so I'm preparing myself to completely deleting it in favor of ubunto. 

I would appreciate any incite you can give me, and whether or not you think that would be a mistake.

The good news is that the pictures are very easy to transfer to ubuntu. There is a learning curve, but there is also a lot of help. The concern is that if you install ubuntu, you may find that you won't have the resources to run it.

To mitigate this, I would also suggest that you download, and burn a CD containing Xubuntu, which uses the xfce desktop. It is similar to ubuntu, but it uses considerably less system resources.

More information can be found here: [http://xubuntu.com/](http://xubuntu.com/)

The learning curve exists - it took me a couple of months to get comfortable - but there is a lot of help in these forums. Any problems or questions that I had, particularly in the early days, were quickly answered.

I have been using ubuntu only for about a year. I didn't dual-boot. Unlike you, I have a very powerful machine, so I could have dual-booted, but I took the view that 'in for a penny, in for a pound'. It has worked well for me.

Hope this helps,

---

### Post by Aidenstar on 2009-07-03
Yes, however I would much rather run Ubunto. Is how the operating system runs on the Live Cd, an indication of how it will run when installed. Because it does run well, albeit slowly. But I think that has something to do with running it off a CD, plus I'm planning on overwritng windows. Do you still think system resources would be a problem. It will be able to run off of the entire hard disk.

I know I'm being stubburn, but I kind of like the look and feel of Ubunto. Wow...so you chose to delete windows? Any regrets?

---

### Post by fballem on 2009-07-04
> **Aidenstar said:**
> Yes, however I would much rather run Ubunto. Is how the operating system runs on the Live Cd, an indication of how it will run when installed. Because it does run well, albeit slowly. But I think that has something to do with running it off a CD, plus I'm planning on overwritng windows. Do you still think system resources would be a problem. It will be able to run off of the entire hard disk.

I know I'm being stubburn, but I kind of like the look and feel of Ubunto. Wow...so you chose to delete windows? Any regrets?

It took a while to get used to ubuntu. Once I did, however, I found Windows machines to be primitive by comparison. I got really use to having the desktop switcher, for example.

No regrets.

By all means, try ubuntu - full installation. I wanted you to have an alternative in hand in case the ubuntu installation did have a problem. It's not the size of the hard drive that's the issue, it's the amount of RAM (256K) that is installed in your machine.

Since you lost the Windows CD, you needed something that will work in case the full installation of ubuntu fails. As for the look and feel - once you get used to working in Linux, you will find that you can change a lot of things. It doesn't really matter if you are running ubuntu, xubuntu, kubuntu, openSuse, Fedora, ....

By the way, if you look at the avatar for my postings - that's the picture underneath my id on the left of the posting - that's a picture of my desktop. It doesn't look like ubuntu, but it is - I just made a few simple changes to the appearance.

Have fun, and be patient with yourself!

---

### Post by Aidenstar on 2009-07-04
Thanks for the heads up...If Ubunto install fails I'll try xubunto. Thanks for the encouragement I think I'm ready to swear off windows for good. Hopefully I have a good experience with ubunto.

Also I was curious how would my low RAM affect ubunto? would it run slower?

---

### Post by fballem on 2009-07-04
At 256K RAM, you're right at the low-edge for being able to run ubuntu at all. Xubuntu requires a minimum of 192K RAM, so if ubuntu does not run, or runs very slowly, you may want to look at Xubuntu as an alternative.

By the way, please note the correct spelling of ubuntu (not ubunto).

Regards,

---

### Post by Aidenstar on 2009-07-04
Will do... I'm going to go ahead with the full installation.

---

