---
title: "Uninstalled, I think, but.."
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by Gmr Leon on 2009-09-27
After looking over several of the solutions here to removing Ubuntu, most of which pertaining to a partitioning of the internal hard drive, I finally found one that had to deal with it on an external hard drive. The instructions more or less were: 

Boot up computer from Live CD, use the Partition Editor to clear off the HD with Ubuntu on it, and reboot. Well, apparently, from what I read from the other solutions, I made the wrong move and somehow GRUB still starts up as well. Except..I get Error 17, which I subsequently searched for solutions for and found only MBR fix solutions.

This wouldn't be a problem, as I also read about that, but it tends to require booting into XP, which, as of now, I cannot do. (As a matter of fact, I'm only able to post on this computer via running Ubuntu from the Live CD.) 

So..In short, I was dual-booting Ubuntu, with it being on my external hard drive, and XP on my internal hard drive. I completely formatted the Ubuntu partitions I had set up on the external hard drive (foolishly) thinking it would be as simple as that. Now, I'm getting error 17, can't boot into XP, and I've been slamming my head against a virtual wall for the past hour or two. Help? Please? 

(As a note, I have no qualms with Ubuntu whatsoever, I just realized that a large sum of music was previously on its hard drive, alongside my games, and it would just be far more convenient to format it and use it for those purposes once more.) 

Also, as a quick heads-up, I've already taken a look at this: 
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

I've also read that NTFS external hard drives can be the issue, but, as soon as Error 17 came up, I disconnected it, rebooted, and found myself facing Error 21 (haven't looked into this yet). If that helps. If there's any more information I can provide, or if I need to clarify anything, I will gladly do so. I know I might be quite unclear, as I'm sitting here fuming in frustration at this.

---

### Post by earthpigg on 2009-09-27
what is wrong with the MBR fix solutions you found?

---

### Post by Gmr Leon on 2009-09-28
Well, the main issue is simply that I can't boot into Windows to run the possible solutions. Not to mention the solutions I found don't seem to work in Ubuntu when running it from the Live CD.

---

### Post by oldos2er on 2009-09-28
I believe Super Grub Disk can restore Windows' MBR. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by jward3010 on 2009-09-28
Have you an XP disc?

A standard XP disk, booted into the recovery console can recover the windows MBR. I think the command is "fixmbr" - running it will cause no harm if no good. Disconnect all other drives before running it though so that it's forced to look at your XP partition and you don't accidentally write a windows MBR to a useless drive.

---

### Post by Gmr Leon on 2009-09-28
I don't have a Windows installation disc, unfortunately, unless a reinstallation disc counts. (I started to put it in, and let it run, but I was wary of it formatting my internal hard drive.)

Edit: I tried installing Super Grub Disk on my flash drive and couldn't get it to boot from that..I suppose the next best thing is to set it up on a disc?

---

### Post by raymondh on 2009-09-28
Just in case ...  in my signature is hiren's CD which has MBR tools to give you access to a command prompt so you can fixMbr your install.

Good luck.

---

### Post by Gmr Leon on 2009-09-28
Alright..I reinstalled Ubuntu on my external hard drive, and now I can boot into either Ubuntu or Windows XP..So, I'm thinking now I just need to find the bread crumb trail I followed last time to fix it up and remove Ubuntu properly. However, if anyone could point me in the right direction, I'm going to keep glancing back at this, and I do thank you all for responding kindly. Some areas of the Net aren't nearly as welcoming. 

Also, I really wish I could get everything I wanted to run on Ubuntu to run, as any operating system that can install in almost less than an hour is my virtual lover. :(

Edit: Well, this is lovely. I tried to boot up XP, and apparently my Hal.dll file has become screwed up somehow..Looking into this now.

---

### Post by oldos2er on 2009-09-28
In my opinion, the first step you should take in restoring Windows is to restore its MBR, then deal with any Linux partitions from within Win*.

---

### Post by Gmr Leon on 2009-09-28
I was thinking along the same lines, except that, well, it seemed like it'd be easier to restore the MBR from within XP. :( Edit: Well, obviously not initially, and really, I'm still a tad more concerned with working out this issue with the hal.dll and then the MBR, then removing Ubuntu (again).

---

### Post by presence1960 on 2009-09-28
> **raymondhenson said:**
> Just in case ...  in my signature is hiren's CD which has MBR tools to give you access to a command prompt so you can fixMbr your install.

Good luck.

That hiren's Cd is a must have. there is a lot of good software on it. I downloaded and burned my copy last night. This will undoubtedly be a major tool in my arsenal.

The OP can use testdisk to fix MBR so windows can boot.

---

### Post by Gmr Leon on 2009-09-28
I think I'm missing something here. I followed the link to Hiren's BootCD 10.0, but I'm not seeing any options to download it.

---

### Post by presence1960 on 2009-09-28
> **Gmr Leon said:**
> I think I'm missing something here. I followed the link to Hiren's BootCD 10.0, but I'm not seeing any options to download it.

[http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)

---

### Post by Gmr Leon on 2009-09-28
Ah, thanks Presence. I'll have to try it out tomorrow evening, unfortunately, but at least it might be something.

---

### Post by presence1960 on 2009-09-28
> **Gmr Leon said:**
> Ah, thanks Presence. I'll have to try it out tomorrow evening, unfortunately, but at least it might be something.

If you decide to use testdisk to fix the MBR post back if you need help.

---

### Post by Gmr Leon on 2009-09-29
Alright, I loaded up Hiren's BootCD, but I don't have any idea how to properly use testdisk, so, if anyone (Presence, if you're around) could help me out with that, it would be much appreciated. And, just so you know, I did at least take a glance at it before inquiring.

---

### Post by presence1960 on 2009-09-29
start testdisk.
Choose "No log" option
select disk with windows on it
select Intel/PC partition
select advanced
Highlight windows partition & at bottom select "boot"
choose "rebuild BS"

This should rebuild your boot sector as long as the message says your back up is intact. You should also see the message that your MBR and backup are different.

---

### Post by Gmr Leon on 2009-09-29
Not sure how this would affect it, but it says that the Extrapolated Boot Sector and Current Boot Sector are identical, nothing about being different. On the screen prior to that, it says Boot Sector and Backup Boot Sector are identical. However, it does at least say the backup boot sector is ok..So that's good. 

I'm guessing the Boot Sector would be the MBR, and if it was messed up, it would appear different from the backup, then?

---

### Post by Gmr Leon on 2009-09-30
In regards to my last post, I think that may be due to my reinstalling of Ubuntu. Despite that, even if I did remove it again, boot it up, and fix the MBR, then I'd be stuck against the issue with the hal.dll, so I'm in quite the bind.

---

### Post by Gmr Leon on 2009-10-02
Finally managed to sort things out a bit here, since I had time to play around with it. I'll probably fool around with it even more so before I get a response, but, the tools on Hiren's BootCD can be used to format a hard drive and set it up to be usable under Windows XP without any trouble, correct? 

(Thought it would be best to keep using this thread, instead of continually making new ones.) 

I'm actually considering lessening the amount of space Ubuntu can use on my external hard drive, so that I can dual-boot, while still having space for excess storage on it. Which is the whole reason I was going to format it in the first place.

---

