---
title: "Install to existing RAID0 array? (Dell XPS M1730)"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by CHR15B on 2009-04-09
Hi there,

I've had a quick search on the forums to see if I can find something else that will help me with my query but I can't find anything that helps.

I'm a complete new user to Ubuntu and so far I'm not doing well... I had it installed on my Desktop system but thats since been replaced by my laptop.

So, information on my laptop which may or may not be useful... it is a Dell XPS M1730 with Core2Extreme CPU and 4GB RAM. It has two nVidia 8800M GTX video cards and two 200GB SATA HDD's. It's current state is a single RAID0 array with a single partition installed with Windows Vista Ultimate 64-Bit.

So last night I downloaded the Live 64-Bit Ubuntu 8.10 ISO and burned it onto a CD, popped it into the XPS and booted the Live CD to the desktop with no problems at all.

After that, I booted back into Vista and resized the partition to about 60% of its original size using the Disk Manager utility and booted the Ubuntu CD again selecting Install.

This progressed fine up until the Disk Paritioner, which shows my two 200GB HDD's.  I wasn't sure if this would happen, or if it would pick up my RAID array and the partition setup - obviouslly not... but it would have been boring if it worked first time, right?

So, as a new user at this point I've come to a dead end and need some support ... I would ideally like to leave the RAID array as it is so that I don't have to scrub my Windows install just yet but if needs must then I would be willing to scrub it.

The only other peice of information I think I may have missed, is that I use the OEM RAID utility, the Intel Matrix Storage Manager... aparently this is not the best but I don't have experience with much else to judge it right now.

Any help would be appreciated,

Thanks...

Chris.

---

### Post by ronparent on 2009-04-09
Your experience highlights a fact that disturbs me. The standard ubuntu distribution does not recognize or work with raid arrays. Fortunately you had the foresight to recognize that something was wrong or you would have proceeded to install to a disk that contained apparently unallocated space. This would have destroyed your raid array and left everything on it unrecoverable! To accomplish what you wanted, you would need to install with an 'alternate cd' which does allow you to install to a raid array. I've heard that the process is involved, which will require some study prior to proceeding. You might avoid this process by installing instead to an external usb drive (hard disk or memory stick). That alternative would allow you to test the experience while you plot out your next step.

---

### Post by CHR15B on 2009-04-09
Thanks for your reply.

I'm in no hurry to install Ubuntu so I might take my time and have a little look around and work out how I'll try and make this work.

So, stepping back a little bit on the message you have mentioned an 'Alternate CD' ... I came across this term before on an article that applied to something slightly different.  Can I ask what the difference is with the Alternate CD? I'm thinking it may have extras like RAID drivers perhaps? I could be way off.

So, the first step from here would be to source and burn an Alternate CD - Where could I get this? Is it on the main Ubuntu website or would it be from an enthusiast website or torrent?

Out of curiosity, what sort of performance should I expect if I installed Ubuntu onto a 4GB 2.0 Flash Disk? The problem I have is that all my data (Music, Images, Etc) are on the local RAID disk which I won't be able to access? (Unless I could 'Play' around once I have the OS installed to the portable drive?)

Thanks again for your clarification.

---

### Post by ronparent on 2009-04-09
I'm sorry I wasn't more specific on the alternate cd, but I know of it only by reputation and never actually used one myself. Yes, it comes with the raid software. I inadvertently by passed the problem by installing on a separate hard drive I had lying around. The performance on a memory stick (mine is 32 Gb but 4 Gb is adequate) is slower than a hard drive but adequate. I also have another install on a 250 Gb WD pasport. Both are setup to boot from the external drive so they can be plugged into and used on any of my computers.

---

### Post by inobe on 2009-04-09
[>>text base alternative installer<<]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")


scroll down for the complete mirror list.

> {*} According to the latest FakeRAID spec, Intrepid users can now install directly to SATA RAID with no additional setup or configuration required. This is is not yet supported in the Ubiquity graphical installer so you must use the Alternate Install CD. The installer will prompt you to activate the RAID partitions, which will make them available to the partitioner and allow you to continue with the installation as normal.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

not everything listed in the documentation applies to one single configuration, the alternative cd setup will discover your raid.

reading more about the boot loader you will discover additional configuration is needed.

> In a non-RAID scenario, one might use grub-install, but we cannot because it cannot see the RAID device mappings and therefore cannot set up correct paths to our boot and root partitions. So we will install and configure grub manually as follows:

back up your data before going forward

---

### Post by kevmitch on 2009-04-09
I totally understand that you want to go for interoperability here, but I just thought that I would confirm that the Intel matrix RAID is not the best. A friend of mine actually did some benchmarking and found it to actually run slower than a single disk (I believe that this was in windows). Finding this he decided to dispense with the BIOS RAID and set up native RAID in Linux. He found it to almost exactly double his bandwidth and he never looked back. 

I'll admit that this is second hand info and I'm mostly just talking out my ***, but you might want to keep it in mind as you're trying out Ubuntu. You should probably check things out for yourself by doing some benchmarks in different configurations. bonnie++ might be a good place to start in terms of benchmarks.

And if anything on your drive is at all important to you now would be a good time to back it up.

---

### Post by inobe on 2009-04-09
```
/dev/md2:
Timing cached reads: 18496 MB in 2.00 seconds = 9259.18 MB/sec
Timing buffered disk reads: 1030 MB in 3.00 seconds = 343.00 MB/sec 
```

hdparm test with software raid0

---

### Post by kevmitch on 2009-04-09
> **inobe said:**
> ```
/dev/md2:
Timing cached reads: 18496 MB in 2.00 seconds = 9259.18 MB/sec
Timing buffered disk reads: 1030 MB in 3.00 seconds = 343.00 MB/sec 
```

hdparm test with software raid0

Wow how many disks? What RAID setup? It looks like you are using md - "multiple device" (rather than dm). I was going to mention that there these two choices of RAID implementation built into the Linux kernel, but I wasn't sure that md was still widely used.

---

### Post by CHR15B on 2009-04-10
I had a bit of a thought last night and done a little bit of revision on installing to the current RAID array and I ended up getting completely lost.

So looking at it today with fresh eyes I've thought it may just be the better idea to do away with the RAID setup and use an individual drive for each OS.

So, a 200GB for Ubuntu and a 200GB for Vista. As mentioned above I doubt I will see much of a performance issue with the system set up like this?

All I'll need to do now and back up my stuff and figure out which of my drives is the master and so on.

Thanks for the replies, the support here seems great and after a quick look at the 'New Posts' it looks like a very busy and active forum.

I'll post up with updates on how I get on, and more than likely be posting a lot over the weekend if the Easter Holiday weather is as poor as expected - I'm sitting in work now (Work in Scotland) so I'll be off Monday.

Who knows, if I start getting into Ubuntu I may try out this RAID thing another time when I feel like a challenge.

Thanks for the response folks,

Chris.

---

### Post by kevmitch on 2009-04-10
> **CHR15B said:**
> 
So, a 200GB for Ubuntu and a 200GB for Vista. As mentioned above I doubt I will see much of a performance issue with the system set up like this?

Well it depends how you look at it. You can't make up for slow i/o throughput with a fast processor. The processor will just end up doing nothing most of the time waiting for the disk. Most of the performance lag you really notice is usually associated with disk access. 

> 
All I'll need to do now and back up my stuff and figure out which of my drives is the master and so on.

Are you referring to the whole "master/slave" dichotomy? That went out with IDE. With SATA, all disks are on equal footing. If you mean which one will the system boot off of, the easiest thing is to have it be the one which Linux is on since it will make sure that it can boot windows whereas windows will not be so gracious. 

The easiest way to achieve this is to install windows first and then install Linux which will set up just such a situation automatically.

---

### Post by darryn.smith on 2009-05-10
I've used this method a number of times on my M1730. 

Just use the regular version of ubuntu (32 or 64, I use 64), And why not 9.04 it's out... and works rather nicely. 

Anyways..  open a terminal and sudo apt-get install dmraid  that will allow the installer to use the fake raid (intel raid). 

follow this for the finer and important details to complete the install..  don't reboot until you've completed all that's required.  

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Enjoy

---

