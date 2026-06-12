---
title: "all these partitioner issues"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by Uppinator on 2005-12-09
Hallo. I've been having issues with the partitioner during install. I've noticed other people have had these problems, but I haven't found any answers yet. Before anything else, I want to say that I have successfully installed regular Ubuntu on a freshly formatted, entirely empty hard drive. I am using an E Machines eOne with a 433 Celeron and 64 mb of ram with a 6GB hard drive. Ubuntu was understandably a little slow, but it worked. I am aiming for a dual boot system with win98SE on the first partition, and Ubuntu on the second. Now, I have had two different problems in two different situations. I have tried regular and server installs, simple and expert, and the outcome is always the same.

1.) After having formatted the drive with a single partition, I install win98. As soon as installation is complete and I gain control of the computer, I reboot with the Ubuntu CD in the drive. Everything looks fine until the partitioner comes up. Ideally, from what I understand, the partitioner should shrink the current single partition to make room for Ubuntu. Instead, I get a message box that looks like this:
                                [!!] Partition Disks
                                   ???        ???
                            <go back>    <continue>
I press enter on either one of those, and the white text bar briefly flashes, "E: Unimplimented Function" Several times, and the screen resets to the message box. From there I have to reset the system.

2.) Installing with two partitions already on the disk. I split the disk into a 2GB partition for win98, and a 4GB partition for Ubuntu. I use fips for this. I have Installing windows first and then partitioning, and partitioning, formatting both drives, and then installing windows. No go. I'll boot into the installer. Everything will be fine until I get to the partitioner. At first, it looks like it is working fine. After getting to 100%, however, the screen flashes to a blank blue screen with the white bar at the bottom, then flashes to a black screen with a cursor in the lower left, flashes to a white screen with a cursor in the upper left, and then restarts the partitioner which then freezes at 52%. I have to reset the system.

I don't know the partitioner wants to be so difficult when I know the CD works fine on an empty hard drive. I'm sorry the post was so long, but I know other people are having troubles with these things, too. I just hope that giving all this information might be able to help work out some of these problems. If there is anything I haven't been clear about, or any more information I need to give, just let me know. Thanks for your time.

---

### Post by Herman on 2005-12-09
>  [!!] Partition Disks??? ???<go back> <continue>I press enter on either one of those
Hi, uppinator, to me it looks like you were on the right track up to that point, then what you are supposed to do is select the Windows partition using the blue rectangle, and press your 'Enter' key.
I went through all these problems myself over a year ago when I first installed 'Warty' version of Ubuntu, which is now out-dated. I didn't know anyone else around who could help, so I found the easiest way to do it all by trial and error, and by reading threads in these forums. Now I have my own website to show other people some examples of how I do it. It isn't an official Ubuntu website, just by another home user trying to be helpful, but it should still help you get the job done. (Check my 'signature link', at the bottom of the typing here.)
I hope that helps you It is well worth persevering with, Ubuntu is great once you have it installed ! Good luck with it, :D (Herman).

---

### Post by Uppinator on 2005-12-09
Yep, I've checked your site out before. Handy stuff; it's just that I can follow the steps on your page, but at the partitioner bit it messes up. Well, actually, there is one difference! My wacko computer has an irregular ethernet card. When the installer tries to to configure the network with DHCP(sp?), it always fails. I once upon a time installed Debian on this thing, but could never get the ethernet card up and working. I don't see how this would cause a problem with partitioning, but what do I know? Unfortunately, there is a good chance that even if I could get this thing installed, the inability to get the stupid ethernet card up and running might keep me from using Ubuntu in any meaningful way. Yeah, mine's a really sad story, huh? In the worst-case senario, I'm hoping a new computer is in the not-to-distant future (for my schoolin', you see). So, if nothing else, I will certainly be making sure to get hardware that is fully compatible with Linux, and I will be starting with Ubuntu. Is there any way you could get your stuff on an Ubuntu wiki? Seems like a good idea.

---

### Post by jerrykenny on 2005-12-09
Hi Upp

Try this

Boot up using your ubuntu disk

goto "custom disk partitioning"

delete all the partitions, then create . . .

1   2Gb Primary Partition, type windows whatever
2  4 Gb (remainder) Extended partition
3  200mb Logical Drive within 2 (linux swap)
4  3.8 Gb (remainder again) Logical Drive (Linux native or ext3)

Finalise, then "write changes to disk", then . . . . . 

Exit the ubuntu installer, and reboot with your windows disk.

Install Windows on the 2 Gb, and then

reboot with ubuntu, and install onto your prepared logical drives.

---

### Post by Iesos on 2005-12-25
I got the same problem as explained above, but I cant do anything of all explained above. I cant do any partitioning with the ubuntu install, all just hangs on the 
??? ??? 
sign. I came over something (cant remember how or where, but probably by ranomly pressing buttons on the keyboard) like: Cant find harddrive. But windows installation detects a harddrive.
help plz.

---

### Post by 504harry on 2005-12-25
You guys seem to have this (almost fixed) - but reading the Original Post, I was amazed that WIn98SE would work with only 64Mb RAM although the 6G HDD is fine.
I'm not sure I want to "dual boot" as I distrust software and if it's not there (so to speak) it can't be corrupted.....so I have splashed out on a new HDD for Ubuntu's use alone.
However, I have an old PC 75MHz Intel - 64MB Ram and a defective HDD - so I wondered if ubuntu 510 will operate on so little..... before I throw it away - I buy Linux Mag and there there are many small distros but not often do they suggest what minimum hardware will suit, nor what the  resulting computer is good for.....
I like the unofficial Website, I'm waiting for a non-windows (dual)boot.......
Maybe you'd consider dual-booting from Ubuntu and a "guest" Linux distro - so one can try them out whilst still having a decent (ie  a Working install) to prove my hardware is still connected. Just a thought. Harry

---

### Post by aysiu on 2005-12-25
First of all, can you explain why you need Windows 98? As far as I know, most programs that will run in Windows 98 will also run in Ubuntu using Wine--the same cannot be said for Windows 2000 or Windows XP, though.

That said, if you still want to do the dual boot... while Ubuntu's partitioning tool is excellent, I've found the easiest-to-use and most reliable partitioning tool is Mandriva's DiskDrake. What I would do is...

1. Install Windows 98 on the entire hard drive.
2. Download and burn the ISO for the first Mandriva installer disk
3. Defragment Windows 98 completely.
4. Boot up the Mandriva disk and go through the resizing and repartitioning part.
5. Force a reboot with Ubuntu's installer disk in.
6. Select "manually edit partition table" and select the new partitions as the ones you want to install to.

---

