---
title: "Lenovo T400 ssd corruption"
date: 2009-06-25
forum: Hardware
---

### Post by jgeorger on 2009-06-25
I got a Lenovo T400 a few weeks ago with a 128 GB SSD, 8 GB ram, 2.4 GHz Core2, Vista Business pre-installed.

First thing I did was install Ubuntu 9.04 in a dual boot config. 

Initially did it with ext3.

After a few days, upon boot I drop to a maintenance shell with the instruction to run fsck on the root device.  I do so.  Sometimes the machine even goes funky while linux is booted, and upon reboot I get hit with the drive corruption.

I reinstall Ubuntu using ext4 and get the same results.

But before you tell me "bad hardware", Vista does not suffer from this at all!!!  And I've run it quite a bit now to be sure.

So next I imaged the drive and then blew away the entire drive to install 9.04 by itself.  That did not help.

So now I'm back to Vista and unsure of what to do next.  Any ideas???

---

### Post by eth00 on 2009-06-26
I actually am experiencing a similar thing with a Lenovo x200s and a OCZ Vertex SSD. After running ubuntu for only a few hours it went read only and required a FSCK. I just started to mess around and will try to update this thread if I find a good solution. 

The same machine also kept hard rebooting whenever an SSD is the main drive and the cpu frequency scaling was enabled in the bios. It did this in XP, Vista, Windows 7, and ubuntu.

---

### Post by beefcurry on 2009-07-05
I don't know if this is a same issue or an different one, everytime I have an improper shutdown in my Acer Aspire One the SSD managed to corrupt itself. I have yet to find the problem (using ext2 ubuntu 9.04). Will report back once I have.

---

### Post by ajartz on 2009-10-21
[COLOR=black][FONT=Verdana]It sounds like I am having the same problem, but with Linux Mint 7 x64 (which is built on Ubuntu 9.04) and a new 250 Gb hard drive. I bought two new 250 Gb Seagate disk drives and tried to upgrade my work Lenovo T400 to Linux Mint. I bought two drives, one for work and one for home. I figured I could always swap the old disk drive back in when I have to turn the work laptop back in.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]On the first drive I Ghosted Windows XP to make the system dual bootable. The Linux file system kept eating itself, and I tried ext2, ext3, ext4 and XFS. Windows XP NTFS partitions did not have any issues. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I then turned Windows XP into a virtual image and tried using the other disk drive. I loaded Linux Mint on the entire second drive and had the same issue. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]My coworker has two Lenovo systems, and R61 and a T400. The T400 had the same issue of the file system melting down. As I have also checked the disk drive's firmware (at latest rev.) and ran every physical test I could find on each disk drive (no errors), I have come to the conclusion the issue is with the T400. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]In "Googling" for a solution to this, there are posts out there about the hdaps driver. The hdaps driver lets the operating system talk to the hardware's accelerometer that moves the disk drive’s head to a safe location when the system is moved. After I make sure I am at the latest, greatest BIOS version, I am going to try the mods for this I found after looking at Jan de [/FONT][/COLOR][COLOR=black][FONT=Calibri]Graaff ‘s blog:[/FONT][/COLOR]
[COLOR=black][FONT=Calibri] [/FONT][/COLOR]
[COLOR=black][FONT=Calibri][http://meandmyubuntu.blogspot.com/2009/05/getting-hdasp-to-work-on-jaunty.html](http://meandmyubuntu.blogspot.com/2009/05/getting-hdasp-to-work-on-jaunty.html)[/FONT][/COLOR]
[COLOR=black][FONT=Calibri][/FONT][/COLOR] 
[FONT=Calibri][SIZE=3]I think I am grabbing at straws with this, but I will let everyone know what I find.[/SIZE][/FONT]

---

### Post by ajartz on 2009-10-21
Well, my BIOS was out of date by a few years. I have just upgraded things to 3.09/3.10. I will try loading Linux Mint 7 x64 (Ubuntu 9.04 x64) the next chance I get (probably Friday). If this does not work then I will follow the steps in Jan's blog.

---

### Post by ajartz on 2009-10-23
[SIZE=2][COLOR=black][FONT=Verdana]Well, I feel dumb for not seeing this web site sooner :mad::[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]So, I upgraded the BIOS, loaded Linux Mint, and then let the system run over night without any errors or issues. When I got to the office, I ran every update that could possibly be gotten at, including the kernal. While this was happening, I did a few more Google searches and found the above article. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]ThinkWiki.org is dedicated to all things ThinkPad and Linux. The article on the link above describes a parameter to add to boot up in the Grub to enable the mute button, then goes on to a script that fixes and tweaks all sorts of little issues with the T400 and Ubuntu 9.04. The one labeled “harddrivebug” was hard to ignore, even though I think it just fixes the hard disk head parking issue. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]In any event, I cut and pasted the script and ran it. Further testing is required, but at this time either the BIOS upgrade or running the script has seemed to fix things. The file system has not eaten itself, yet. With this issue it would need a good FSCK after all the updates were installed, the system was rebooted, and then new software was started to be installed. This has not been the case so far. I will leave the system on for an extended period this weekend to see what happens. If I don't post anything else, assume all is well and this helps.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR][/SIZE]

---

### Post by ajartz on 2009-10-26
Well, I let things run for an extended time this weekend, but I needed to reload things when I could not get VMware Workstation to install. At one point I needed to run FSCK, but I think it was from trying to get VMware to load/unload. I have since gotten things loaded and will continue testing.

---

### Post by ajartz on 2009-10-29
Well, file corruption took place again. After a bunch of new searches, I found this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691)

After reading the 175+ posts on this bug post, I figured the problem on the T400 is the SATA disk controller being set Compatibility mode instead of AHCI. When I set thing to AHCI, it seemed stable, but I also followed the steps on this link (sort of):

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122)

Since I thought the issue was AHCI, I loaded Linux Mint 7 x64, did all the upgrades, then followed the steps on the bug post to install a 2.6.29 kernal. As before, if there are more issues i will post more (though I would think everyone on this post has either solved their problem by now). .

---

### Post by whalebus on 2009-11-06
I initially had an OCZ vertex SSD but I found that it would hang sometimes during boot and often while using software that cached history data like Firefox.  This occured on both 9.04 and with XP.

I recently replaced the OCZ with an Intel X-25G1 (~220$ for 80GB) and haven't had any issues.  I am completely off MS software for now.  I also found the Thinkwiki article about installing 9.04 on the T400 and only used the scrolling fix.  I did not apply any other recommended fixes or scripts.

In case it crosses your mind, I also tried 9.10 but then my system was extremely slow and unresponsive even after numerous attempts to work out the bugs.  I was very happy with 9.04, so I went back to that and do not plan to upgrade anytime soon.

---

