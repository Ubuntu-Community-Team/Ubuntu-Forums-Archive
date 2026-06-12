---
title: "Problem with Installing"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by samuel.stidham314 on 2009-07-15
I know that this is probably pathetic for a CIT major to break down and ask for help with this problem, seeing I should probably already know how to fix this problem.  However, I'm having an extremely difficult problem trying to figure out how to get an installation of Ubuntu on my hard drive.
 
Okay,  I have tried several versions of Ubuntu and Kubuntu (along with certain other versions of linux) and what I have discovered is in most versions I have tried my hard drive and it's partitions are hidden .... and in Ubuntu 7.10 live session ... I opened up "My Computer" and right clicked the Hard Drive .... the permissions are set to read only.  I have tried to change these settings in the live setting but it says that I cant do that for some reason.
 
All help is much appreciated.
 
I am an Ubuntu beginner ... I mean I barley know how to set up the partitions and install the operating system successfully.  I have run successfull installations of Ubuntu before, but not on this hard drive or with this computer.
 
Thanks

---

### Post by grizzyfizzy on 2009-07-15
I installed Ubuntu 9.04 on the whole disk. I used a Boot Nuke program to get rid of everything then just installed the operating system with the cd from a cold boot. It seems to be working fine for me.

---

### Post by samuel.stidham314 on 2009-07-15
I think I need to restate the question:
 
How do I change the permissions on the Hard Drive, make it "un hidden" so to speak, to ensure that I can set up the proper partitions for installing Ubuntu. I have tried everything that I know to try. Here is a list of things I have done to fix this problem:
 
1. Various different versions of linux, including various versions of Ubuntu/Kubuntu, using the partition manager in each of those versions of linux.
2. I have used FDisk
3. I have set the Hard Drive up as a slave and tried to change the permissions in a couple of different versions of Windows
 
The Hard Drive seems to be in a locked position, not allowing any partitioning software (this includes partition magic) access to the Hard Drive to make partitions for an Ubuntu installation.  As I have stated previously, Linux says that all permissions on the Hard Drive are set to **read only.**
 
How do I reverse this problem?

---

### Post by grizzyfizzy on 2009-07-15
I do not know much about ubuntu but I do have a few more questions for you. Do you have anything on the computer that you still want to use. If you dont then  I think that the Boot Nuke program will show the hidden partitions when you try to install ubuntu. If you run the ubuntu cd it will ask you what type of install do you want. A full system install or do you want to run it on certain partitions. If it your partitions dont show up on the install I do not know how to help you. Sorry if what i said isnt any help.

---

### Post by samuel.stidham314 on 2009-07-15
I have tried to run full system installations, but the problem with that is .... **read only** partitions make it impossible for Ubuntu to make the necessary changes to the Hard Drive for the operating system to be installed.  How do I **change the permissions** on the hard drive so that the Ubuntu installation cd can do it's job?

---

### Post by ramnarayan on 2009-07-15
> **samuel.stidham314 said:**
> I have tried to run full system installations, but the problem with that is .... **read only** partitions make it impossible for Ubuntu to make the necessary changes to the Hard Drive for the operating system to be installed.  How do I **change the permissions** on the hard drive so that the Ubuntu installation cd can do it's job?

did you try the partition manager in the Ubuntu Live CD
after starting up the live cd
 go to System -> Administration -> Partition Editor

This will show you your main hard disk some thing like /dev/sda etc

and if you check the top right - there is a drop down box that will have (if you have more than one HD) an option to select any other HD.

See what this says

also in your live boot open up a terminal and try
-$sudo df -h

this should also give you a list of your various partitions and what format they are on etc etc

---

### Post by samuel.stidham314 on 2009-07-15
It doesn't matter what format my partitions have ... The point is is that they are **read only**, which means that they are locked to all the partition managers/editors that I have used (as you would be able to conclude if you have thoroughly read all of my posts).  So what I want to know is .... is there a way to reset one's hard drive or directly change the permissions so that these partitions can be changed?
 
The Hard Drive had a version of windows XP with Service Pack 3 on it.  I'm not sure if SP3 causes hard drives to become **read only** (ie literally change the Hard Drives permissions). 
 
I want to bring to your attention .... A floppy disk has a mechanism that changes the disk from read/write to read only.  When that little mechanism is flipped upwards and you can see through that small hole ... nothing you can do (except changing the mechanism back to the previous position) will enable you to write to that disk.
 
My hard drive is going through the same principal.  Something has happened to make it read only.  I want to reverse the read only condition that the hard drive is in .... so that I can (or some other program) change the partitions and contents of the Hard Drive so that it will run Ubuntu.
 
It's a very simple equation.  Seeing which hard drives are on my system, or what partitions are on my hard drive is something that I don't need to see.  I already know whats on the hard drive .... a single partition that has the NTFS format used for windows xp .... it is the only hard drive in this computer.
 
So, this takes me back to my original problem.  How do I change the hard drives **permissions** from read only to read and write so I can install ubuntu.
 
Thank you

---

