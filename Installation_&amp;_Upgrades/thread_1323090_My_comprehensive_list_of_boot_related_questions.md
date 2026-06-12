---
title: "My comprehensive list of boot related questions"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by ed-koala on 2009-11-11
These are questions I need answers to, hopefully very specific step by step answers. I've made several posts that wander around, so hopefully I can get all my answers in one nice package here.

1. Are there any known bugs with installing 9.10 on a RAID array? Is there any workaround? What are the links to the bugs?

1a. What is /dev/mapper? Is this an acceptable partition to install to?

2. With Ubuntu 9.04 installed on a machine, why does the 9.10 installer report that there are no operating systems installed on the PC? Is this related to the RAID setup?

3. What is Busybody? If you are dropped to a busybody prompt (<initramfs>) has Ubuntu loaded?

4. If all your PC will boot to is the Busybody prompt, if I use the live CD what files, and what parts of those files, should I be checking/editing to make the PC find the operating system and boot to it?

5. If installing 9.10 fresh from CD, can you name a partitioning scheme that can be set up manually that will work? List mount points, grub install place, ext format, partition type (logical/primary) that is needed.

6. Grub error 2. What should I check to find the problem?

7. Will installing the 32 bit version of 9.10 onto an AMD64 machine create problems? (never has with 9.04)

8. In Bios, where will a raid setup appear? I've been through every entry in my Bios and do not see RAID mentioned anywhere, not even as an option.

9. Does 8. mean I will have to physically change my hard drives in the machine to change the RAID setup?

Hopefully if I can get enough of these answered, I'll solve various different issues getting 9.10 to boot up.

---

### Post by cariboo on 2009-11-11
> 1. Are there any known bugs with installing 9.10 on a RAID array? Is there any workaround? What are the links to the bugs?

Read the known issues [here]("http://www.ubuntu.com/getubuntu/releasenotes/910")

> 1a. What is /dev/mapper? Is this an acceptable partition to install to?

That is your raid array, in my case it was /dev/mapper/nvidiaxxxxx

> 2. With Ubuntu 9.04 installed on a machine, why does the 9.10 installer report that there are no operating systems installed on the PC? Is this related to the RAID setup?

If you are using the Live CD that is more than likely the problem.

> 3. What is Busybody? If you are dropped to a busybody prompt (<initramfs>) has Ubuntu loaded?

It's **busybox**, it means that some part of the os load procedure has failed

> 4. If all your PC will boot to is the Busybody prompt, if I use the live CD what files, and what parts of those files, should I be checking/editing to make the PC find the operating system and boot to it?


See above, you have an error loading Linux, you have to solve the problem first before doing anything else. IF you are getting a busybox prompt when loading the Live CD try some of theoptions available by pressing F6 at the Live CD menu screen.

> 5. If installing 9.10 fresh from CD, can you name a partitioning scheme that can be set up manually that will work? List mount points, grub install place, ext format, partition type (logical/primary) that is needed.


Refer to this [thread]("http:///ubuntuforums.org/showthread.php?t=408461") when installing on a raid array. Normally I just create / swap and /home partitions, you will probably have to put grub on both disk if you setup either raid 0 or raid 1. Disk format should be ext4 for speed. Always use primary partition first, you can use up to 4 of them.

> 7. Will installing the 32 bit version of 9.10 onto an AMD64 machine create problems? (never has with 9.04)

I always recommend installing 64-bit on a 64-bit capable computer.

> 8. In Bios, where will a raid setup appear? I've been through every entry in my Bios and do not see RAID mentioned anywhere, not even as an option.

The bios setup is different for every manufacturer, It may be an idea to check your user manaul. You should see a raid setup option during boot if it is enabled. Even if you don't have a raid option in the bios, you can setup software raid.

> 9. Does 8. mean I will have to physically change my hard drives in the machine to change the RAID setup?

I'm not sure what you mean here.

THe one thing I question here, is have a good look at why you want a raid array, if it is for speed raid 0 is all you need, if it is for redundancy, raid arrays can fail, so don't rely on it to keep your data safe, have a good backup plan.

---

### Post by ed-koala on 2009-11-11
Thank you for that great list of replies.  I need to clarify a point or two tho ...

[INDENT]1. Are there any known bugs with installing 9.10 on a RAID array? Is there any workaround? What are the links to the bugs?
Read the known issues here[/INDENT]

Question 1 -- the link is informative, but all I see is this issue: 

Automatic boot from a degraded RAID array not configured upon installation 

The installer option to support "boot from a degraded array" does not properly configure the installed system. To correct this after installation, run dpkg-reconfigure mdadm after installation and select the option again.

The solution isn't clear. How am I going to run anything if the system doesn't boot?  From the live CD?  And what is "the option" it is telling me to select?

[INDENT]2. With Ubuntu 9.04 installed on a machine, why does the 9.10 installer report that there are no operating systems installed on the PC? Is this related to the RAID setup?
If you are using the Live CD that is more than likely the problem.
[/INDENT]

Question 2 - I'm trying to install 9.10 from the live CD, but 9.04 is already installed on my hard drive. When the partitioner starts during the install process, shouldn't it "see" 9.04 already on the hard drive and ask to put them side by side?  It doesn't currently know 9.04 is there at all.  Why?

[INDENT]3. What is Busybody? If you are dropped to a busybody prompt (<initramfs>) has Ubuntu loaded?
It's busybox, it means that some part of the os load procedure has failed[/INDENT]

Question 3 - Is there a way for me to tell exactly what failed during the boot process?  How?  Also, Live CD boots fine to 9.10, just it won't do so from the HD.

[INDENT]9. Does 8. mean I will have to physically change my hard drives in the machine to change the RAID setup?
I'm not sure what you mean here.[/INDENT]

Question 9 - I am asking if my hardware is hard wired into a raid array somehow that will need to be physically disconnected.

---

### Post by ed-koala on 2009-11-11
I think I found the root of my problems, now the question is how to go about fixing it.  The main issue seems to be 9.10 not "seeing" any OS, not the already installed 9.04, or 9.10 once the install is done.

I do feel this is an issue with partitioning (too bad 9.10 can't do it right on its own).

Here are my options:

Detected RAID array, do you want to activate the RAID?  Should I?

Assuming I say yes, as I'd like to, I'm thinking I should add a small space for a /boot partition, non RAID.  That seems to be advised when dealing with RAID.  Is this a good idea? How?

Would appreciate a step by step walk through of what to do when installing from the Alt CD and dealing with RAID.  After I activate RAID, I see these options:

Guided partitioning
Configure software RAID
Configure the logical volume manager
Configure encrypted volumes

Serial ATA RAID nvidia_XXXXXXXX () 1.0 TB linux device mapper (

Which do I select? And then what?

---

