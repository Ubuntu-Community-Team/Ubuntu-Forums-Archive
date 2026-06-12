---
title: "Can't see/mount External Hard drive"
date: 2008-09-24
forum: Hardware
---

### Post by Cjmkee on 2008-09-24
I am new to linux and I can't get my Western Digital external hard drive to mount on Ubuntu Hardy. I have been searching forums and websites all day trying different things. Most of the post I found are about External Hard drives or USBs being seen but not auto mounting. My problem is it seems like it's not even recognizing that there is a hard drive plugged into the USB port. I have tried mounting it using terminal (ie making a directory then mounting it) but that doesn't work. I don't really have any experience with command line work so I don't feel very confident that I am doing it correctly. 

Can anyone help?

---

### Post by Sef on 2008-09-24
Applications > Accessories > Terminal 

type in ```
lsusb
```

It will show if it is detected or not.  If not, then change the usb port that it is in and retype lsusb.

---

### Post by Cjmkee on 2008-09-25
I tried the hard drive in both USB ports and it doesnt recognize it in either when I do the command lsusb

What should I try next?

---

### Post by StitchJAcket on 2008-10-12
I'm having the same issue... I run fdisk -l no luck not shown. I am  trying to use a western digital 140GB passport external HDD

---

### Post by Deuce2 on 2010-12-18
Sorry to bring up an old thread, but I wasnt sure if I should create a new one. i am not too computer savvy and definitely not Ubuntu savvy. 

My dilemma, I installed Ubuntu 10.10 onto an external hdd i have (western digital 372gb) and am running it through oracle virtualbox. It works fine everything except for recognizing the the rest of the files on the external hdd. Now, is that because i am running it off of a partitioned part of the external hdd?? or am i just a novice who is in over his head.

I have searched here and google and came across some steps to manually mount a drive but in all honesty I am only like 60% sure of what I am doing.  ([https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)) < Is the web page I came across which has been very useful for that among other things that have to do with Ubuntu.

When I key in 'sudo fdisk -l'  this is what I get :

Disk /dev/sda: 22.0 GB, 21987590144 bytes
255 heads, 63 sectors/track, 2673 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000191fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2557    20532224   83  Linux
/dev/sda2            2557        2674      936961    5  Extended
/dev/sda5            2557        2674      936960   82  Linux swap / Solaris

Im guessing sda1 is where Linux is actuall stored (booting from) on my (partitioned part) external hdd, and sda5 is for stored memory (like windows page filing)???
So is sda2 just a partition? and if so how do i get it to show the rest of my external hdd?

I also tried plugging in a thumb drive to see if maybe it was because Ubuntu was actually running from my hdd which was causing the problem, but it does not recognize my thumb drive either.

Lastly (so sorry for this lengthy post... ),

When I key in 'lsusb' into the terminal i get this: 

Bus 002 Device 003: ID 80ee:0021  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

^all greek to me...? Bus 002 is my drive where Ubuntu is running right? So is this > Bus 002 Device 003: ID 80ee:0021 < Just a partition or the rest of my external hdd?

I am very sorry if I have confused anyone but please excuse my ignorance I am trying my best to learn something that is very new to me. Thanks for your time

-Deuce

---

### Post by Deuce2 on 2010-12-19
Any help is really appreciated.

---

### Post by Tamrac on 2010-12-21
Have the same problem.... using Ubuntu Disk Utility. It shows my WD external to be present. But if I choose to mount it, this error appears.


Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed


Any advice?

---

### Post by xcxc on 2011-01-23
Hi everybody,

I've just got the same problem and then found the solution that worked for me.

I have a dual boot system Windows 7 + Ubuntu 10.10, and I have a Western Digital 2Tb external drive ("Elements"), which I was using under Windows 7 and got quite a few files stored on this drive already.

But then, when I once tried to mount it under Ubuntu it failed with the same error as reported above. 

So what I did was I resized the partition (the only one on the drive at that time) under Windows 7 (from 2000 -> 1500 Gb) and also created a new partition 500Gb at the end of the drive - just to see what will come out

- so it worked - I could see both partitions under Ubuntu since then

It looks that one has to somehow 'touch' it with Windows utility and then it's OK


Hope this will help those who

---

### Post by Joherrer on 2011-03-11
I´ve been suffering a similar problem, with a 1 Terabyte external hard drive. 
When I connect it to an USB port, the activity ligth blinks and blinks and blinks... 
... and I never see the hard drive.
BTW, the unit works fine on Windows system (XP at office, Seven in my personal notebook).
I´m using maverick on my desktop.

---

### Post by parminides on 2011-03-17
I'm having similar problems (see below). The likely cause seems to be that the hard drive isn't getting enough power from the computer. See [http://www.compatdb.org/forums/topic/32707-usb-device-not-recognized-external-hard-drive/](http://www.compatdb.org/forums/topic/32707-usb-device-not-recognized-external-hard-drive/) (and start reading from post #4).

Some users have found that changing cables, especially to shorter cables, which affects voltage, fixes the problem. If you're not using the original cable that came with the hard drive, try switching back to that cable.

Western Digital, et al., offer optional power booster cables ([http://www.amazon.com/gp/product/B002GWMLE8/ref=pd_lpo_k2_dp_sr_2?pf_rd_p=486539851&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=B000RY2PLQ&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=0HV9VHZSW9BAK89406F0](http://www.amazon.com/gp/product/B002GWMLE8/ref=pd_lpo_k2_dp_sr_2?pf_rd_p=486539851&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=B000RY2PLQ&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=0HV9VHZSW9BAK89406F0) and [http://store.westerndigital.com/store/wdus/en_US/DisplayAccesoryProductDetailsPage/productID.106596600/categoryID.13095900](http://store.westerndigital.com/store/wdus/en_US/DisplayAccesoryProductDetailsPage/productID.106596600/categoryID.13095900)).

More details about my situation:

I've have a Western Digital (WD) 250GB Passport external hard drive for almost 3 years. The Ubuntu Disk Utility says the model is 2500 BEV. It was long ago reformatted with gparted to make fat32 and ext2 partitions. I've used it with a few computers in Ubuntu and Windows and never had any trouble until now.

I recently installed Ubuntu 10.10 on an old hand-me-down laptop (Dell Latitude D600). When I plugged in the drive, at first it automounted. But then it spontaneously unmounted while I tried to copy files. This happened several times. The drive would spontaneously mount, I'd try to copy files, then it would disappear again. Later it would pop back up.

Now it doesn't mount at all. The drive now makes these periodic clicking noises (every 1-5 seconds) as it unsuccessfully tries to mount, and the drive's light brightens in synch with clicks. I didn't notice those before.

The drive still works fine on my other computers. Also, a flash drive, similarly formatted with gparted to fat32 and ext2 partition works fine on the hand-me-down Dell laptop.

The lsusb command doesn't find the hard drive on the Dell. The problem persists with the hard drive plugged into either of the computer's two usb ports. Ubuntu Disk Utility doesn't detect the drive on the Dell. However, running Disk Utility on another Ubuntu 10.10 computer shows that "SMART Status: Disk is healthy."

---

### Post by vanadium on 2011-03-17
> **Deuce2 said:**
> Sorry to bring up an old thread, but I wasnt sure if I should create a new one. i am not too computer savvy and definitely not Ubuntu savvy. 

What about the button "New thread"?
> 
My dilemma, I installed Ubuntu 10.10 onto an external hdd i have (western digital 372gb) and am running it through oracle virtualbox.

1) This statement does not fit the "not too computer savvy" from above.
2) If running from virtual box, it cannot be installed on a dedicated partition. It runs on a virtual drive, and the output of your sudo fdisk -l is that of a virtual drive within virtualbox.

To access the contents of your regular drives through an operating system installed in virtual box, you need to mount the real drive as a network drive. I am not computer savvy enough to know the details (i.e., it is too long ago when I tried this with a Windows in Virtual box under Linux.) You can find that in Virtualbox documentation. I am not sure whether you need to install Virtual box guest additions for that.

---

### Post by mgmyers on 2011-03-18
I ran lsusb and got this.

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0461:4d0f Primax Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 064e:a118 Suyin Corp. 

It's still not mounting though.  I formatted the disk as ext3 with Gparted.  It was mounted before the format, but I was unable to remount after.

Anybody have a clue what this could be?

---

### Post by mgmyers on 2011-03-19
I have only linux to worry about here on a Dell mini.

---

### Post by mgmyers on 2011-09-18
OK, I'm back.  For a while, the WD drive mysteriously worked.  It has now stopped being recognized even in lsusb. I have tried plugging it in to various ports to no avail.  The lights come on, it spins up, it was recognized by windows on another computer (though since I formatted to ext3, windows was unable to read it).  

Is there a manual way to get it recognized???  I've got a lot of info on here and need access! =P

---

