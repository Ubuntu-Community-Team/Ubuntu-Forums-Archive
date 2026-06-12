---
title: "[SOLVED] Safely remove Windows"
date: 2008-09-08
forum: General Help
---

### Post by Gonz_91 on 2008-09-08
I have decided to run windows virtually inside Ubuntu, but now I want to remove windows from my system. How do I do it?

I have my HD partitioned as following:
-WinRE thingy
-Vista partition
-Ubuntu extended partition
-Data

---

### Post by Sycron on 2008-09-08
Boot Ubuntu LiveCD, run Gparted, System-Administration-Partition editor, and delete the windows partition. Be [COLOR="Red"]sure[/COLOR] to NOT delete your important data's.

---

### Post by Gonz_91 on 2008-09-08
so, simply deleting the partition won't mess up GRUB, right? I'll still be able to boot into ubuntu, just as before, right?

---

### Post by Rocket2DMn on 2008-09-08
Have a look here - [uhelp]community/HowToRemoveWindows[/uhelp]
As for your recovery partition, you CAN remove it, but it's quite alright to leave it there if you are the least bit concerned.

---

### Post by Gonz_91 on 2008-09-08
Recovery partition? WinRE?

Is it not safe to remove it?

---

### Post by Rocket2DMn on 2008-09-08
I assume WinRE is your recovery partition (correct me if I'm wrong).  If you're not using Windows anymore, you should be able to get rid of it since it won't be getting used.
If you were to re-install windows at a later time, I'm not sure what the process is for configuring windows to make use of the recovery partition (whether you have kept the old one of have to create a new one).  There is surely documentation out there for that.

---

### Post by Gonz_91 on 2008-09-08
Since i'm no planning on going back, at least not without formatting the whole drive and trying a new layout, I'll just wipe it and resize my Ubuntu and Data partitions to fit the whole drive.

Any suggestions on how I should partition? Like file system for the data partition, since I'm using linux, I suppose I don't need ntfs anymore...

:D

---

### Post by triphazard on 2008-09-08
> **Gonz_91 said:**
> so, simply deleting the partition won't mess up GRUB, right? I'll still be able to boot into ubuntu, just as before, right?

Just to confirm, as long as you don't mess with any Linux partitions you should be ok.  The Master Boot Record won't be touched and as all Grub's config sits in /boot you'll be absolutely fine.

If you wanted to remove the option to boot into Windows from Grub after removing the Windows partition just edit grub.conf ```
sudo gedit /boot/grub/grub.conf
``` and remove the Windows section.  It should be pretty clear which bits to remove.

---

### Post by Gonz_91 on 2008-09-08
> **triphazard said:**
> Just to confirm, as long as you don't mess with any Linux partitions you should be ok.  The Master Boot Record won't be touched and as all Grub's config sits in /boot you'll be absolutely fine.

If you wanted to remove the option to boot into Windows from Grub after removing the Windows partition just edit grub.conf ```
sudo gedit /boot/grub/grub.conf
``` and remove the Windows section.  It should be pretty clear which bits to remove.

Already knew that, but thanks anyway :)

---

### Post by triphazard on 2008-09-08
> **Gonz_91 said:**
> Already knew that, but thanks anyway :)

haha.  cool cool.  may i also say, that was the quickest reply ever!

---

### Post by Gonz_91 on 2008-09-08
> **triphazard said:**
> haha.  cool cool.  may i also say, that was the quickest reply ever!

And yours was quite fast as well ;)


Now, I have another problem: I deleted those partitions, and then applied. All went well. Then I decided to format my "Data" partition to delete everything in it, at GParted says it doesn't recognize the file system. And I can't mount the partition anymore.

Looks serious

---

### Post by Rocket2DMn on 2008-09-08
I wouldn't try to resize your Ubuntu partitions backwards, that will take ages, and fiddling with partitions alays carries a small risk of failure.  Based on what you told us, I don't see a swap partition, so you should add one if you don't already have one.  The rest of the empty space you can use as more data partition, or to setup a /home partition.  If you choose this option, see the bottom portion of this page for copying over data - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Rocket2DMn on 2008-09-08
Please post the output of
```
sudo fdisk -l
sudo blkid
mount
```
I'm assuming you are in the LiveCD?  If are you in a normal boot, also post the output of
```
cat /etc/fstab
```

---

### Post by Gonz_91 on 2008-09-08
> **Rocket2DMn said:**
> Please post the output of
```
sudo fdisk -l
sudo blkid
mount
```
I'm assuming you are in the LiveCD?  If are you in a normal boot, also post the output of
```
cat /etc/fstab
```

Sorry to take so much time to reply, and thank you very much for your help in all the process ^^,

I solved my problem using a linux distro which I've used sometimes in the paste when my disc needed some fixing. Parted Magic. I highly recommend it.

When I started the live CD's GParted and ran into that problem, I also noticed that, besides not being able to delete that "unknown" partition, I wasn't also able to move my Ubuntu partition (which is an extended partition that includes a 2.9GB swap) to the beginning of the disc.
But when using Parted Magic, it all went well, and my new partition setup is:
-Ubuntu (with swap)
-Data

100 gigs each.




Thank you all very much for your help!
It is communities as this one that make an OS worth the switch :D


(PS: after a reboot, I noticed that, while loading, instead of displaying that "Ubuntu" screen with the progress bar, it displays a lot of letters, describing the loading process. I really do not need to see that, can anyone help)

---

### Post by Gonz_91 on 2008-09-08
/me marks thread as [SOLVED]

---

### Post by Sycron on 2008-09-09
> **Gonz_91 said:**
> /me marks thread as [SOLVED]

Good work!

---

### Post by silverglade00 on 2008-09-09
You should be able to get rid of the scrolling bootup by appending splash=quiet to the end of your kernel line in grub.

---

