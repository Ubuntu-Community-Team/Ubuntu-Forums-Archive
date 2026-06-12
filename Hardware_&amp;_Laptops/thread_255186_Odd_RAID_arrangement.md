---
title: "Odd RAID arrangement"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by jonkun227 on 2006-09-11
I'm fairly certain the answer to this is something along the lines of "no", but I'd be happy if I was wrong.

Is it possible to have a mirror (RAID 1) consisting of not only mismatched drives, but even a concated set (115 gig and 150 gig) on one channel and a 250 gig single drive on the other? I'm basically looking for a 250 gig server with mirror for security, without spending more money.

If that's not possible, I believe I can do a RAID 1 with my 150 and 160 gig mismatched drives, with an apparent size of 150. Is that correct? Obviously a 250 would be better, but I'll take what I can get.

(I'm using a SI PCI 0680 IDE RAID controller. If this doesn't work I'll use the onboard SIL 3112 SATA RAID controller on my Asus A7N8X-Deluxe. But I'd like to save a couple hundred bucks if I can. 

Thansk!


- Jon

---

### Post by HAARP on 2006-09-11
You can still sue the leftover space for swap/tmp or something.
What are those cards? The Sil3112 is a Fake-RAID card and thus won't work without special drivers.

---

### Post by ruedu on 2006-09-11
The short answer is: yes, but it's not an ideal setup, you *usually* cannot boot a linux system on anything other than a straight mirrored setup.

For the long answer I'd need to know more.  I'm not sure that the advanced parition tool can handle what I can suggest.  I know that you can do it all on the command line, no problem.  But then it'd be too late if you're plan is to install Ubuntu on this.  

What I'd suggest, is to parition the 150GB drive into three parts and partition the 250GB drive into two parts.  the 150GB drive should be partitioned into a 20GB part, a 115GB part (to match the 115GB drive) and the remainder you can just not partition.  Then, paritition the 250GB drive into two parts, a 20GB part for a remainder of 230GB.  Create a mirror set of the two 20GB parititions and install Ubuntu onto that.  

I'll stop here, but if that is your plan, then go ahead with it and then report back and I'll tell you how to finish up the remaining raid set, in the end, my idea will result in a wasted 15GB, but you'll be able to otherwise get alot more space than if you just mirrored for 150GB.

---

### Post by jonkun227 on 2006-09-11
Okay, that's much better news than I'd hoped. I know it's a fake RAID, but it will suit my needs just fine. I did a lot of searching before I got started and it appeared that both of these cards were supported a couple versions back.

I'm not booting from this. Sorry I didn't explain it better. I'm booting from an old 12 gig that I have sitting around. Then these drives are all on the SI PCI 0680 IDE RAID controller. Again, I'm not going to be doing a RAID 5 or anything. Just looking for a large mirror with a weird arrangement of drives.

I'm still in the process of cleaning the existing data off the old drives. (One lost its partition table under Winblows and I'm recovering the data with my Mac. SUCH a long process, and it typically generates 2x as much data as it's actually recovering because it searches twice.) Anyway, once the drives are clean and good to go I'll partition as you've described and come back for more instructions.

Thanks!


- Jon

---

### Post by ruedu on 2006-09-11
Actually, if you're NOT booting from these disks it gets much easier, and you get a lot more space.

I would stripe the 115 and 150 together, this will result in a 265GB set.  Then, create a mirrored set using the striped set + the 250GB drive.  You'll have a realized 250GB that way.  Striping the 115 and the 150 will give you a bit of a performance boost there, which will be handy since the 250 is a bit newer and a bit faster.  Let me know if you need detailed info on how to setup this type of software RAID.

---

### Post by jonkun227 on 2006-09-11
Cool. Yes, I do need help there. Right now though I'm trying to figure out why the 150 won't mount with permissions for me to read it without being root. My /etc/fstab tells it to mount with user permissions, but whenever I try to access it I get a "you don't have permissions" error.

My brother (he's probably used every distribution known to man) is helping me there. But he's never done a RAID configuration, which is why I'm here today.

Thanks again!

---

### Post by ruedu on 2006-09-11
Make sure you're putting the user option in the right spot.  It should go in the same column after the filesystem type column, so, defaults,user or more specifically

```
/dev/md2          /home                   xfs defaults,user    0 0
```

---

### Post by ruedu on 2006-09-11
Your RAID will get setup as follows.

I'm a command line junkie and I'm not aware of a GUI tool that can do this so this is probably your only option.

Open a command line (terminal) and become root by issuing sudo su - 

You have a lot of work to do and it's far easier to be root for awhile than putting in sudo all the time.

Figure out what the kernel is using to refer to your drives as by issuing dmesg | grep ^hd or dmesg | grep ^sd if you're using SATA drives.  You're looking for entries that look like the following:

```
hde: WDC WD800BB-00DKA0, ATA DISK drive
hdf: WDC WD800JB-00FMA0, ATA DISK drive
hdg: WDC WD800JB-00FMA0, ATA DISK drive
hdh: WDC WD800JB-00FMA0, ATA DISK drive
``` 
On my system, I have a RAID10 set of 4 80GB drives.  You'll want to avoid RAID5 if you can unless you are using a dedicated RAID hardware raid card with built in cache or a rather powerful CPU.  

Anyway, you can see that my kernel refers to my drives as hde-hdh.  I'm going to assume that your 115 is called hde, your 150 is hdf and your 250 is hdg.  I'm also assuming you do NOT have any othe RAID sets.  Replace those items accordingly!  

First, create the striped set out of the hde and hdf by issuing the following

```
mdadm --create --raid-devices=2 --level=0 /dev/md0 /dev/hde /dev/hdf
``` 
Press enter, if you get a warning that the devices are used in an array already or some other warning where you are asked if you want to continue anyway, say yes.

Next create the mirror set by issuing the following

```
mdadm --create --raid-devices=2 --level=1 /dev/md1 /dev/md0 /dev/hdg
``` 
Again, if you get any warnings, say yes to force the creation of the raid set.

You're mirror set will now start to sync.  You can monitor the sync progress by issuing:

```
cat /proc/mdstat
``` 
You'll get out put the looks similar to:

```
md2 : active raid0 md0[0] md1[1]
      156301184 blocks 64k chunks

md1 : active raid1 hdh[0] hdf[1]
      78150656 blocks [2/2] [UU]

md0 : active raid1 hdg[0] hde[1]
      78150656 blocks [2/2] [UU]

unused devices: <none>

```  

However, you'll see a series of ==>.... indicating the resync progress of your mirror set.

---

### Post by jonkun227 on 2006-09-20
Well, I ended up breaking down and buying two new 320 gig Seagate SATA drives. I was in the process of recovering data that had been corrupted on my 160 gig drive to my 115 gig drive when I bumped the power cable. Seriously, your average piece of paper could have impacted it this much with the help of gravity alone. Turns out the power strip has a short. So I threw it away. And in the process the data on the 115 was corrupted.

I told my wife how sick of these problems I am and we made room in the budget for some new drives. And when (if) I ever finish restoring those drives I'll use them in another array for ripping all of my DVDs. 

Anyway, your tutorial was helpful because it helped me understand what to do with my SATA drives to accomplish the same thing, albeit with fewer steps. So, thanks!


- Jon

---

