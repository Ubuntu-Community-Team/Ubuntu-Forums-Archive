---
title: "Installation bug?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by qwerta001 on 2009-10-31
Hi guys,
I had heard of disk recognition problems in the RC build of Ubuntu 9.10, but I had expected this to be either a faulty hardware problem, or a minor bug that would be fixed in the RTM build.
Unfortunately, it seems not to be the case - as I have found out myself.

My computer is....

Motherboard
         Asus P5K Premium

Processor
         Intel Core2Quad Q6600 2.4Ghz no overclock

Memory    
     4GB

OS    
     Windows Vista x64 SP2
             Ubuntu 8.04 Studio
    
Disks
         WD1500ADFD 150GB disk
         WD740GD 74GB disk

Partitions
         Disk 0
                 C: 111.58GB NTFS Vista bootable
                 26.94GB Ubuntu 8.04 Studio bootable
    
    Disk 1
                 E: 69.24GB NTFS

Video
         Nvidia 8800GT 512MB


I booted off of the DVD, and selected language, location and keyboard layout, then the installer started.

Installer

-------------------------------------------------------------------------

          [][][][][][][][][][][][][][][][][][][][][][][][]
                          [] /dev/sdb1 69.2GB

This computer has no operating systems on it

Where do you want to put Ubuntu 9.10?

         @ Install these side by side, choosing between them each startup

         O Erase and use entire disk
                 SCSI4 (0,0,0)(sda) - 150GB ATA WDC WD1500ADFD-0
      This will delete Windows Vista (loader), Ubuntu 8.04.1 (8.04) and install Ubuntu 9.10
    
     O Specify partitions manually (advanced)

           [][][][][][][][][][][][][][][]||[][][][][][][][]
                 [] /dev/sdb1 39.2GB       [] Ubuntu 9.10 30.0GB

--------------------------------------------------------------------------

As you can see, Ubuntu fails to correctly recognise the disks and partitions - it even fails to recognise it's own sibling (Ubuntu 8.04) - although it _does_ see them in the 'Use entire disk' option, it doesn't when you want to dual-install it (I was going to install it on the old Ubuntu 8.04 partition).

This is very disappointing for such a high profile OS release, and I am definitely not going any further with this, sadly.
Is there a fix for this (Remembering that this is supposed to be a general-purpose OS, and not a "Unix Guru" OS)?

---

### Post by qwerta001 on 2009-10-31
Just to add - after cancelling the install, the Ubuntu desktop appeared. I clicked (top right) the Ubuntu power menu, and selected Restart. The disk was ejected, the screen went blank, and then - nothing! No shutdown or reboot. Ctrl-Alt-Del did nothing, and I had to hold the power button down for 5 seconds to stop the PC.

As an aside, I tried going through installing my Windows 7 RC-1 disk, to see if it could find all my partitions - it did, without any dramas, so the problem is definitely with Ubuntu 9.10.
Plus, my Ubuntu 8.04 Studio install was done long after I had installed Vista. It correctly identified my disks and partitions, so Ubuntu 9.10 seems to have gone backwards! :o
Very poor, in my opinion :(

---

### Post by Ginsu543 on 2009-10-31
I ran into the exact same problem as you did (I did a clean install off the 9.10 Live CD), except that in my case Ubiquity recognized my two WD 74 GB Raptors as a RAID array when I don't even have RAID turned on in BIOS. On the other hand, it recognized my two WD 1 TB Caviar Blacks just fine. When I physically unplugged one of the Raptors, this time both failed to show up. When I unplugged all of them except for one of the Raptors, Ubiquity reported that I had no hdds whatsoever!

I've been looking all over the net (including this site) for a fix, but there doesn't really seem to be an easy one (although you might try the alternate installer CD). For me, my 9.04 installation is set up exactly the way I want and working perfectly (except for few minor glitches from the well-documented problems with ATI drivers), so I will most likely forego 9.10 altogether and wait for 10.4.

---

### Post by qwerta001 on 2009-10-31
> **Ginsu543 said:**
> I ran into the exact same problem as you did (I did a clean install off the 9.10 Live CD), except that in my case Ubiquity recognized my two WD 74 GB Raptors as a RAID array when I don't even have RAID turned on in BIOS. On the other hand, it recognized my two WD 1 TB Caviar Blacks just fine. When I physically unplugged one of the Raptors, this time both failed to show up. When I unplugged all of them except for one of the Raptors, Ubiquity reported that I had no hdds whatsoever!

I've been looking all over the net (including this site) for a fix, but there doesn't really seem to be an easy one (although you might try the alternate installer CD). For me, my 9.04 installation is set up exactly the way I want and working perfectly (except for few minor glitches from the well-documented problems with ATI drivers), so I will most likely forego 9.10 altogether and wait for 10.4.

Hi, I too had no problems with 8.04. I will take some convincing before going Ubuntu again. I was really looking forward to this, so I am pretty disappointed.
Perhaps I will actually pay cash, and get Windows 7! ;)

---

### Post by Ginsu543 on 2009-10-31
If you haven't given 9.04 Jaunty a try, I would heartily recommend it. I've been using Ubuntu since 8.04 and 9.04 is by far the best release. Ironically, unlike 9.10, 9.04 installed and worked from the get-go and addressed all (well, most, again the ATI thing) the issues I had with previous versions. I'd hate for you to give up on Ubuntu just because of 9.10 when 9.04 is such a good OS.

---

### Post by bingung99 on 2009-10-31
> **Ginsu543 said:**
> If you haven't given 9.04 Jaunty a try, I would heartily recommend it. I've been using Ubuntu since 8.04 and 9.04 is by far the best release. Ironically, unlike 9.10, 9.04 installed and worked from the get-go and addressed all (well, most, again the ATI thing) the issues I had with previous versions. I'd hate for you to give up on Ubuntu just because of 9.10 when 9.04 is such a good OS.

As a newbie to Ubuntu, I was very excited about the new 9.10 release...9.04 had some problems but I managed to fix the errors...I followed the normal upgrade process via the Update Manager...everything was going fine....installed the new packages, did the clean up and stuff like that....however....the problem started when the computer restarted....I could only see the new Ubuntu white logo....and then my PC began to restart by itself again and again....My GOD!!!What is happening???...I lost the whole 9.04 and could not even see the login screen for 9.10!!!...Arghhh!!!!
:(:(:(

And YES....this did make me seriously consider of giving up Ubuntu for another distro....even Window$ didn't disappoint me like this...please guys..help me..how can I solve this disaster??....
:(:(

---

### Post by qwerta001 on 2009-10-31
> **bingung99 said:**
> As a newbie to Ubuntu, I was very excited about the new 9.10 release...9.04 had some problems but I managed to fix the errors...I followed the normal upgrade process via the Update Manager...everything was going fine....installed the new packages, did the clean up and stuff like that....however....the problem started when the computer restarted....I could only see the new Ubuntu white logo....and then my PC began to restart by itself again and again....My GOD!!!What is happening???...I lost the whole 9.04 and could not even see the login screen for 9.10!!!...Arghhh!!!!
:(:(:(

And YES....this did make me seriously consider of giving up Ubuntu for another distro....even Window$ didn't disappoint me like this...please guys..help me..how can I solve this disaster??....
:(:(

As I mentioned in another thread - I really think Canonical should temporarily pull 9.10, fix these issues, then re-release it.
What does bother me, is that many of the issues I've seen here were flagged-up during the beta and RC builds, but these seem to have been ignored. I really would not have minded if Canonical had said "Sorry guys, we have to postpone the launch for a week, to get everything running perfectly"
I'll give them another week, then I'll probably have to get Windows 7 - I want to move on from Vista, and the 7 RC looked fine, and performed well, on my test PC - we'll see...

---

### Post by Ginsu543 on 2009-10-31
If you went the upgrade route, the only way to get 9.04 back, I believe, is to do a clean reinstall (there is no way to downgrade from 9.10 back to 9.04). I'm frustrated with this situation as well, but it is not enough to give up on Ubuntu altogether. I'll just stay with 9.04 until they release a working 9.10 or I'll just wait for 10.04. It's not like 9.04 is not getting the job done for me. Is there a reason why you need to get 9.10, or is it just a desire to have the latest and greatest?

---

