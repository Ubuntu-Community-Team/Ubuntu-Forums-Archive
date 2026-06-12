---
title: "Feisty - Gnome Vanishes"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by xerman on 2008-01-31
Hello there:

I decided to post this thread in this forum because I do not know where to put it.

Finally, seems the Grub Error I told you about in this thread:

        [http://ubuntuforums.org/showthread.php?t=673434](http://ubuntuforums.org/showthread.php?t=673434)

got fixed. I reinstalled Feisty and now, after subsequent trials, restarts, reboots, more restarts and more reboots, seems the Grub Error dissappeared. So, for now, I can power on the computer and get to GDM and Gnome.

What I found lately is that after a while of working into the Gnome Desktop, things start to go wrong. I know I live in a part of the world where it is said "Witches,them there are", so sometimes we could assign guilt to them.

I would appreciate any help, as always.

What is happening now is that after logging into Gnome I can work with apps for a while. Sometimes until I decide to shutdown. But sometimes the following issues happen:

(Status Quo applies the one stated in the thread referenced above. But now, Feisty is in every computer: Compiz is installed and running)
1 - Randomly application windows start to grey out. 
and when this happens system starts to do somethings weird, as shuting down daemons or apps. Gaim is one app that when others start to grey out, dissappears from the status bar.
2 - When the "grey out" thingy starts to happen there is no possibility to get the system back to normal.
Apps start to grey out, some of them recover from grey out some not. Menus from the menubar start to loose their icons.
3 - No app is able to be launched from the menubar, or from anywhere.
4 - Changing to another TTY, and trying to login from console is not possible. After typing the username there is no way to type password. Username Login repeats after a while. So I find myself typing my user name for ever and ever.
5 - Once this gets worse, there is no way to type in any app. No way to launch any app. No icons on the desktop. And even menubars dissappear. The only way to shutdown is physically turn off the computer in the On/Off switch.
6 - If panels do not dissappear, shutting down shows the standard "Shutdown, Reboot, Logout, Suspend..." Dialog, but with no icons at all, just the buttons with names. Selecting "Shutdown" produces an exit from Gnome and a black screen with red text that says "The system is going down" but in spanish and with lots of typos, missplacing characters, mostly acuted vowels and entilde. The computer never shutsdown unless i turn it off physically.

This is random because I had to start the computer 4 times to get to this point in writing this message, and do not know if I will finish writing and will be able to send it.

I must say, as I said in the other thread referenced above, that the 1GB ram Dimm does not show 1GB, but 995MB... which is no good. Does not mind on which bank it is placed.

I could not check the System info now because of the "no menu launching stuff", so i cannot even launch a terminal.

Could it be due to a Memory Hardware failure? If the dimm is wrong, could it cause this issues?
Could it be due to a Hard Disk Failure?

Thanks and hope I could post this, because if not, I will need to reboot and try again, as I cannot copypaste right now.

---

### Post by xerman on 2008-02-03
Hello there again:

Some news:
I've managed to download 8.04 alpha4 and burned to a CD. Took me quite a while due to these Vanishes and Locks.

I reboot the machine with the 8.04 livecd to check the filesystem with > fsck.ext3 and > badblocksas I've read these two could tell me if the filesystem is messed up.

Results of both, forcing fsck.ext3 to do the check, were that filesystem is OK and no badblocks. Though I checked all sda partitions, sda1, sda2 and sda3 (all of them ext3) I could not check the swap "filesystem".

Though, while on Live CD i experienced no Vanishes, no locks. Just a keyboard mapping issue that "kept" -alt- key pressed.

I'm not a linux geek, I'm just trying to get to be a poweruser. But I presume that these narrows the diagnose to RAM or SWAP. Being it swap will mean the sda4 partition (swap) will have an issue which would conclude in HD failure.

Ram is still 995,2 MB instead of 1024 (this info provided by Sysinfo). After setting in the BIOS to handle dinamically the VRAM assign, and max VRAM to 128MB so the most RAM used for VRAM will be 128 instead of the 256 Fixed initially.

Checking swap with > cat /proc/swaps produces de following:
```
Filename                                Type            Size    Used    Priority
/dev/sda4                               partition       2931852 0       -1
```

wich shows that no swap is being used. Right now I can type with no issues at the moment.



I will keep adding more info as it comes out.

See you

---

### Post by Yellow Pasque on 2008-02-03
> I could not check the swap "filesystem".
The swap space isn't a permanent filesystem, so you don't need to check it.

To test the RAM, boot into memtest86 (should be on the GRUB menu, if not enable in the /boot/grub/menu.lst file).

This does not sound like a hardware issue to me, but it never hurts to check.

---

### Post by xerman on 2008-02-03
> **Temüjin said:**
> The swap space isn't a permanent filesystem, so you don't need to check it.

I see this point Temujin, but what I intended to do is check the swap space on the HD to see wether there is some sort of issue with the disk. But as mostly is unused, I am not sure about that.

> To test the RAM, boot into memtest86 (should be on the GRUB menu, if not enable in the /boot/grub/menu.lst file).
I will try that one. One thing is for sure. Being a 1GB dimm, should show 1024MB instead of 995,2MB in ubuntu, or 1008 in the BIOS. I cannot discard this one because the issue is happening almost all the time. This time the computer has been UP for 2:10 hours, which is good, but, next time could go wrong after 5 minutes, after half an hour, ....

> This does not sound like a hardware issue to me, but it never hurts to check.
Well, I have to think about hardware as right now is Feisty fresh install. 
I thought could be RAM related as VRAM is shared and could be that bios is assignin parts of RAM that do not work properly. Actually I do not discard anything, but I have not much info on how to check system integrity.

"dmesg" output has been different from before doing de 8.04 fsck and after. And the first time launched not just worked properly, but also extremely fast. Now speed has gone back to normal. (By fast I mean startup process and login into gnome, not overall application running).

Thanks for the info anyway.
I will be checking the ram as you said.

---

### Post by xerman on 2008-02-05
> **Temüjin said:**
> 
To test the RAM, boot into memtest86 (should be on the GRUB menu, if not enable in the /boot/grub/menu.lst file).

I did a memtest86 as you said and seems that memory is ok. At least the 1007 MB that memtest sees.

Since I changed the VRAM asignment from Fixed 256MB to DVMT (or whatever name). From Fixed to Dynamic and set Fixed Maximum to 128MB I have not experienced locks yet. This does not mean that I will not experience more issues, just that by now I have not experienced any weird issue.

The most wicked thing about this is that I own another machine, almost exactly the same. Same barebone, Kingston Ram, 2 HD, 1 DVDRW, same Core2Duo, and in that one I have not experienced any issue of this kind.

Actually, now I can shutdown the machine from Gnome, reboot, and menus in the panel show icons and arrows all the time. Something did not happen before. Moreover, before the VRAM reassignment computer reached a point in where I could not launch any app from the panel or the menus, producing an Input/Output error. So the only apps running where the ones launched before the lock.

After the lock, if top panel is still showed, turn off the computer produces de multishutdown option window (Reboot, Logout, Shutdown, Suspend... with no icons, but just text). Rebooting produces a lock, black screen with red text that ells "The systin is goeng donw, pleaz wait". Typos are not exactly like these because is Spanish System. Computer will never reboot nor shutdown unless a hard switch reboot. After this reboot the Grub Error "Read Error" appears again... sigh...

Rigth now I'm on the 8.04a4 LiveCD. With liveCD's i have no issues at all. System monitor in 8.04a4 LiveCD shows Ram is 994'8MB instead of 995'2 seen by Feisty, or 1007 seen by Bios. I have no "greyout window" issue with LiC (LiveCD), which are the begining of a total lock. As soon as a window grays out, for sure the system will lock.

Something that also happens with 804a4LiC is that all partitions are always shown. (This used not to happen with Gutsy Desktop CD  (GDeC) nor Feisty (FDeC).) Swap is set properly (seems so), though there is none used. So I cannot check wether issue was swap related or not. Temüjin suggests is software related, which I am starting to think about seriously. But does not fit with the Office Computer Way, as this is almost the same and has almost the same apps installed.

FACTS:
1- The fsck resulted in hard drives working fine.
2- The memtest86 resulted in "available" ram being fine.
3- 804a4LiC works properly.
4- Kingston Ram 1GB DIMM lost 17MB to score 1007MB top.
5- It all started when updating to Gutsy from Feisty.
6- Feisty Clean Install with HD formatting did not solve the issue.
7- Installed Feisty UpToDate.
8- Both HD are Seagate SATA 120 and 250 GB.
9- Intel Core2Duo E6400.
10- Intel G965 Chipset and Graphics.
11- Random Locks Still take place (20080205)
12- Random Locks start when app window greys out.
13- Lock produces Top panel menu icons dissappear.
14- Lock produces Launch apps from menus or top panel to cause errors (random):
   14.1- An error occurred while trying to execute son process "name of app" (permission denied).
   14.2- An error occurred while trying to execute son process "name of app" (input/output error).
15- Lock produces "Input/Output" error when trying to save work from any app.
16- Lock produces icons dissappear from logout/shutdown screen
17- Shutdown/restart from the shutdown screen produces freeze. Black screen with red Terminal text "System is going down" with misspelling, and no restart/shutdown possible but hard shutdown through switch.
18- Start after switch shutdown produces Grub Read Error.
19- Grub Read Error after switch shutdown keeps appearing until computer feels like. Usually the computer "rests" some time and after that time start is possible and work is also possible until next lock/freeze.
20- Partition table is:
    /dev/sda1 -> 1 GB -> /boot (ext3)
    /dev/sda2 -> 50'5 GB -> / (ext3)
    /dev/sda3 -> 65'5 GB -> /home (ext3)
    /dev/sda4 -> 2'8 GB -> swap

    /dev/sdb1 -> 122'9 GB -> /media/one (ext3)
    /dev/sdb2 -> 127'2 GB -> /media/two (ext3)

More on this, as soon as comes out more info.

Regards
Xermán

---

### Post by xerman on 2008-02-08
Hello there:

New issues:
1- When a lock in gnome takes place, the only way to get out is by hard switch off.
2- Turning on again produces Grub Stage 1.5 Read Error.
3- Rebooting reproduces the Read Error
4- Unpluggin from mains, repluggin eliminates Read Error

weird!

I am completely lost.
Xermán

---

### Post by xerman on 2008-02-09
Hello there again:

I write back because the "window grey out" is also happening to another computer, this one is an AMD 64 with Nvidia 6600 and gigabyte mobo.

So, population is:

1- intel core2duo, g965, asus mobo, intel chipset, 2xHD sata, DVDRW pata, 1007MB ram, video ram shared (dynamic, max 128MB)
2- amd 64, nvidia 6600, gigabyte mobo, nvidia chipset, 2xHD sata, DVDRW pata, DVD pata, 512MB ram, 256MB video ram
3- intel core2duo, g965, asus mobo, intel chipset, 2xHD sata, DVDRW sata, 2GB ram, video ram shared (fixed to 256)

Issues are happening to 2 out of 3.
All computers are wearing Feisty uptodate 32 bit.

The entrance of experiment 2 in population can confirm a software issue, as related by Temüjin, regarding the Dimm hardware issue with experiment 1.
Experiment 3 has not showed yet this kind of issue.

Applications are mostly the same, though not exactly the same.
All are running compiz.

Thanks for any info provided to solve this
Regards

---

### Post by xerman on 2008-02-09
Hello again:

Today i could not start the computer.

Some /dev/sda2 error took place while on the boot process so there was no way to start. 

After a reboot there was a problem with the hard drive so I let the computer "rest for a while" as I've been doing lately when this happened before.

After that, a Grub Stage 1.5 Read Error took place. And as for now, there is no way to get out of this problem again.

Right now I'm using 8.04 LiCD which seems to work fine, but I cannot see /dev/sda at all. None of the partitions of first SATA drive are shown. Second SATA HD is there and can be accessed with no issues. I've been searching the forums and the net and found nothing about this, that could help.

Thanks all.
Regards
Xermán

---

### Post by xerman on 2008-03-19
Finally...

One of the DIMM was broke. The other day the computer started with just 2 GB ram instead of 3 GB ram. After removing the DIMM things seemed to start do go half ok.

Today I'm running Hardy, and Memory is shown properly in System Monitor. The issues I am having now are mostly regarded to Hardy alpha stage.

Soon I will move to Hardy 64 beta. Then I am pretty sure new things, new issues will take place. I will keep you all informed of these.

Regards.
Xerman &#38634;

---

