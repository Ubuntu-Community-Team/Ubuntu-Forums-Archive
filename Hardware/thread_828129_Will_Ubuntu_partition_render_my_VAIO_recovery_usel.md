---
title: "Will Ubuntu partition render my VAIO recovery useless?"
date: 2008-06-13
forum: Hardware
---

### Post by Klaw198 on 2008-06-13
Hi I'm new to Ubuntu and I was wondering if any other VAIO users are able to install Ubuntu on a partition and still use their VAIO recovery.  I've read a few threads on HP recovery, but there doesn't seem to be an organized thread about Vaio recovery and Ubuntu partition playing well together.  Basicly I'm worried that changing my C: partition (where Vista is) will prevent the Recovery from working because of various checks and stuff.  For the longer story please read on.  Thanks for your help!

I recently installed Wubi on my Vaio SZ650 and decided to put Ubuntu in it's own partition.  However in the process my Vista partition was corrupted.  I tried boot up my restore partition by hitting one of the f keys and it booted up the recovery OK, however when I chose the option to restore my C: drive to factory settings the program told me that my C: drive did not have enough space.  I think at this point it had 100+gb, so I know it had enough for Vista and whatever stuff Sony wanted to put on it.  I suspect it needed to be the max amount(160gb) minus the amount the recovery took, slimming the chances people who didn't purchase the computer could install Vista.  I managed to fix this error by using GParted and making my C: drive the maximum possible amount.  Of course, this error was followed by another error, saying that it couldn't find the target C: drive, which is funny because another Sony utility labeled the partition as C:.  I suspect that Sony may have put some sort of key somewhere on the C: partition which allows the installation to start.  I sent my computer back to Sony to let them reinstall everything to the way it was before.  I still want to give Ubuntu a try, but I need the recovery partition to be able to restore Vista the C: partition when needed or even restore the hard drive to factor settings.

---

### Post by jimv on 2008-06-13
I think the issue is probably because of Grub being installed on the MBR.  You need to run FixMBR, which can be found on the Ultimate Boot CD at [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by -Outcast- on 2008-06-18
I wanted to Dual boot with Vaio and ran into probs with that bloody recovery crap. Here's a rundown. 

Right I tried G parted on D and it reformatted it.

VISTA did not boot. An error about kernal missing popped up. So I am guessing Sony in all their wisdom put something on D: that was booting the system on C:

The whole purpose on this was to aid in installing a dual boot with ubuntu and vista.

Taking this into account I installed ubuntu 8 onto D: using a manual partition and letting it decide where to put the boot loader.

It did not see or allow any windows user settings to be imported so I assumed it did not see it at all.

Then on restart I saw Vista loader and it worked. Now got dual boot working with no more Sony inspired D:

Rather than save 20 cents on a CD to some with an already expensive laptop they went for this common recovery drive which is a complete pain in **** to me. I have a back up, even online storage with all. My laptop came with 80GB HD and yet i only had 65 GB in reality after Vista consumed so much and then the 5GB recovery partition. If Sony had just stated 75GB HD Availible or the like it would not have pissed me off so much. But they didn't. So I kicked it out. And reclaimed what I paid for.

I hope this helps other Sony users. My advice to those not wanting to Dual boot and just get rid of D: is to either wipe D: out with file manager settings, and then use Vista to resize it. Reclaim the unallocated space and leave D: as a small 50MB boot partition.

Either that or delete D: with gparted as above, and then use Vista recovery disk to reinstal the MBR boot loader on C:

Case closed

---

