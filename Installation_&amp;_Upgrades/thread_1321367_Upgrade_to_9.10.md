---
title: "Upgrade to 9.10"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by gatordude on 2009-11-10
Ok, I attempted to upgrade and during the install I received all sorts of errors that stated that either certain files were already installed or that certain files couldnt install. There were far to many to list and I am hoping that if I get the pc operating again I can find the log file because I was prompted to report a bug before the PC rebooted and then died.

On boot after install I get a failure at Checking file systems:
         fsck: No such file or directory
         fsck died with exit status 1

After it configures the network interface I get:

stat: cannot stat '/usr/bin/screen : No such file or directory
[: 30 -ge: unexpected operator
init: rc-default main process (2185) terminated with status 127.



Please advise

---

### Post by wilee-nilee on 2009-11-10
Did you backup your important stuff? If you did then get the ISO on a CD and do a fresh install. You may be able to get some help here to at least be able to boot into the system, but personally the few times I have had a borked situation I just did a fresh install. Even if you get it working, personally I wouldn't trust it to have the stuff you can't loose being on the computer only.

So if your stuff that you don't want to lose is on a unbootable computer you can use a live CD to access to pull it off then do a fresh install. These are just some options and instruction on many threads on how to do all of these things.

---

### Post by gatordude on 2009-11-10
I keep all of my files external to the PC so I am good there. I dont understand why it borked, and if it did screw up some file while installing why isnt there a catch to keep the install from continuing? I am a little peeved cause I have been upgraging all of my windows PC's to Ubuntu (except for my laptop which is a dual boot XP and Ubuntu box). I would hate to have to go back and do all of the modifications again my hardware requires to this PC because it is a pain in the #$$. (that is the only thing Microcrap has on Linux distos).
As I sit here twirling my XP cd in hand looking and the black sreens of my Ubuntu machine contemplating putting it back on the PC I am holding out some hope that somebody has a bit of information that can help me.

Cheers

---

### Post by wilee-nilee on 2009-11-10
> **gatordude said:**
> I keep all of my files external to the PC so I am good there. I dont understand why it borked, and if it did screw up some file while installing why isnt there a catch to keep the install from continuing? I am a little peeved cause I have been upgraging all of my windows PC's to Ubuntu (except for my laptop which is a dual boot XP and Ubuntu box). I would hate to have to go back and do all of the modifications again my hardware requires to this PC because it is a pain in the #$$. (that is the only thing Microcrap has on Linux distos).
As I sit here twirling my XP cd in hand looking and the black sreens of my Ubuntu machine contemplating putting it back on the PC I am holding out some hope that somebody has a bit of information that can help me.

Cheers

If all that happened is that that ubuntu install got broken on a upgrade and you have XP on the 1st partition use the linux live cd to remove the ubuntu with gparted which is on the live CD then reinstall a fresh version in it's place. It doesn't sound like the XP is damaged if it was running before and the ubuntu upgrade just wont work. Be sure to give all information in the 1st post you didn't mention that you had a dual boot. The new install of ubuntu will load XP into grub, and if it doesn't just run in the installed Ubuntu terminal run sudo update-grub. This command works with Grub 2 which will be installed when you update then install if it isn't in there already. Now I am assuming this a dual boot am I correct, you say dual boot but some think a wubi install is a dual boot.

I did a dual boot of Windows 7 1st and then karmic yesterday and W7 was in grub already.

---

### Post by gatordude on 2009-11-10
It isnt my dual boot pc it is my stand alone ubuntu machine that this happened to.

I just mentioned the other Ubuntu installs I have to kind of point out the fact that even though I am a newbie to the linux world I do "kinda" know enough to get myself into trouble :-\" with Ubuntu.

---

### Post by wilee-nilee on 2009-11-10
> **gatordude said:**
> It isnt my dual boot pc it is my stand alone ubuntu machine that this happened to.

I just mentioned the other Ubuntu installs I have to kind of point out the fact that even though I am a newbie to the linux world I do "kinda" know enough to get myself into trouble :-\" with Ubuntu.

It is not hard to get in trouble with Ubuntu being that you have a lot of control. So if you have a single install of Ubuntu that is broken and have all your data off the computer just insert the live CD delete the partitions with gparted and you have to turn swap off I believe to get it removed then close gparted click on install and watch the magic.

You were smart to have all the important stuff off the computer that is what I do, so I can fresh install, try a new distro or break any of the 5 computers I own.

I would make sure the computer runs okay with the live CD I have an old Inspiron laptop with a known lame graphics card that had some minute problems with karmic., I just put Jaunty back on it. Upgrading to Karmic is not the preferred method a few major changes were made that a fresh install will take care of.

In the future try to be clear and concise adding additional information about computers not involved and spinning a XP disc while at the same time trying to fix a borked upgrade leaves you without any responses I am the only one yet who has tried to help you because I care. ;)

---

### Post by gatordude on 2009-11-10
OK, well lets say that I go ahead and do a fresh install. Before I do that can if I put the live cd in is there a way to see if there is a log file that would show there errors so I can post it? That the information may be helpful  if there is some type of bug that I may have encountered.

Thanks for the help.

---

### Post by wilee-nilee on 2009-11-10
> **gatordude said:**
> OK, well lets say that I go ahead and do a fresh install. Before I do that can if I put the live cd in is there a way to see if there is a log file that would show there errors so I can post it? That the information may be helpful  if there is some type of bug that I may have encountered.

Thanks for the help.

That is beyond my expertise. but make sure the CD runs normally.

---

### Post by coffeecat on 2009-11-10
> **gatordude said:**
> Before I do that can if I put the live cd in is there a way to see if there is a log file that would show there errors so I can post it? That the information may be helpful  if there is some type of bug that I may have encountered.

You could boot up from the live CD, mount the installed root partition and have a look in /var/log. Make sure you are looking in the hard-drive /var/log and not your live session's virtual /var/log.

But I should imagine it would be a forlorn task. There are an awful lot of logs in there - maybe messages or syslog would be the ones to go for - but more importantly I wouldn't be surprised if all those errors were written to a virtual log file held in RAM and lost when you rebooted.

Also, the errors you get on attempted bootup suggest a filesystem corruption and you might not be able to view files in the root partition anyway.

---

### Post by gatordude on 2009-11-11
Thanks for the info.

I tried to look and there were way to many files to find the right one.

So I did a fresh install and opened a whole can of worms.

9.1 tells me after I got it loaded that my HD was failing. Since this is the 3rd drive I have used on this box (1 SATA and 2 IDE) over the last 6 months I am stumped.

I reloaded windows onto it and checked the HD and WIndows doesnt see any errors?? I ran error check twice and it did not see any bad sectors. Now I am not a fan of Microcrap but it would seem that  if there were errors that it would show up when I ran the error checker right?

I know this should be in a different post and I will move it (as soon as i figure out how) but if I had a HD controller problem (SATA vs IDE) I could understand if only one type worked. But they both seem to have issues. (in Ubuntu and not windows) 

If anybody knows of something I could do to either fix the problem I am having or if anybody needs additional info please ask and I will get it.

THis is my system (old but should be a good platform for Ubuntu)

Shuttle SB95
P4 3G 64 bit proc
2G mem
GeForce 8400 GS
Cheers

---

### Post by coffeecat on 2009-11-11
> **gatordude said:**
> 9.1 tells me after I got it loaded that my HD was failing. Since this is the 3rd drive I have used on this box (1 SATA and 2 IDE) over the last 6 months I am stumped.

That could be a false positive from Palimpsest (Disk Utility). Apparently, palimpsest is putting out false alarms and bizarre data from certain makes/models of drives. Have a search of the forums. There are a few threads about this.

---

### Post by gatordude on 2009-11-11
Thanks I will have a look.

---

### Post by wilee-nilee on 2009-11-11
So the only problem with the fresh install is the pesky HD failing applet you can turn off the applet so it leaves you alone. I have a old Dell Inspiron laptop with a old HD and the read out only shows 1 sector as a real problem. I think the program is reading hours of usage and just using general information to say it is failing. It even said a external HD which is fairly new and unplugged all the time as failing. 

This needs to be fixed it is a disconcerting message to the user. It should not be part of the stock setup showing a applet. but only as a usable scan and a good explanation of the limitations.

---

### Post by paxmark1 on 2009-11-12
a lot of people are reporting the "false postitive" of their hard drive about to fail.  Search Palimpsest on the forums or hdd bad sectors

from user Irihapeti
The new disk utility, Palimpsest, is simply reading data from smartctl, which is a utility that reads diagnostic information stored in the drive itself.

Sometimes the figures are out of line with what's really going on and need a correction factor applied, but smartctl and Palimpsest don't know that. Sometimes, I suspect that drives may already be on the way out but haven't done anything terrible yet - or maybe there have been some glitches that have been blamed on software.

If you are at all unsure, do regular backups. Even if you are confident the disk is OK, do regular backups. That way, you are covered.    from user Irihapeti

and also from forums yields

i have the same issue :bad sector
i download Hiren's Boot CD v.10.0 and run HDDRegenerator and this repair problem.
now,message from palimpsest is :'disk is healthy'  from user kkady32

---

### Post by rmjohnson144 on 2009-11-12
I too fell for the upgrade in ubuntu's update program and I received a load of mmessages of files that were being deleted.  It said something about canononical not being supported anymore. I'd assume that it would be redirected to a proper site instead of just deleting vital files and leaving my system crippled.

I have no important info that needs recovering, but I would think the upgrade option would be better tested than this.  

I went into grub and seen I had two different recovery modes and both would boot for me to try and recover.  I guess I'm stuck with my Windows method of fixing my problem

Reformat and reinstall.

I hope there,s a fix soon so others don't have to go through this as well.

-=Mark=-
ps.  I hope I don't run into this HD failing error.  I've had this before and after running the manufacture's disk utilites and writing zeroes to the hard drive seem to fix it.

---

### Post by gatordude on 2009-11-12
OK, I have a question. I have been abusing my HD to see if it is going out by taking huge files and transferring to and from the  hard drive and running as many apps as I can fit on my screens and the only issue i get is processor overload (and memory issues also).

But now my question, how do I delete or turn off the HD Utility?

I'm thinking its as easy as deleting it from the Systems menu and rebooting right?

Does it still remain in the root?

---

