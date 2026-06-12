---
title: "Starting over and need some tips"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by troegs on 2009-03-06
i installed ubuntu about 3 months ago. had a few hitches but got everything up and fairly easily. Now after a couple months of piling on all the compiz/emerald/awn/cairo/nameYourShinyAppHere eye candy (thank god I got that out of my system) as well as tinkering with just about every app i could in order to see just what I could do with linux, my system isn't running as well as when it was nice and clean. I would like to just do a clean wipe. I've gotten important files i need pics/papers etc off of my machine and am now looking to wipe this linux partition (dual booting vista) clean and start over. 

Now to why I'm starting this thread. When I initially installed ubuntu H had troubles with the partitions. my installed failed several times during the partition process so my kept getting partition after partition til it was sliced into bits. I ended up finally getting all those partitions removed and used a cd that was burned at the slowest settings possible, (never thought that could actually affect things). My question is this, with the existing boot/main partition, will I get similar issues of this current partition getting sliced into a smaller size and again?

If there is an easier way of doing what I'm trying to do let me know. I just want to go back to where I was at after my initial install, (driver/app/settings/config)wise.

Any help would be greatly appreciated,

T

---

### Post by s.dalas on 2009-03-06
I don't really know if i can help you, but i can tell you what i did when my system started to slow down after i was experiment with Wine and crossover and other apps.
1.I just restarted my system with the Ubuntu cd inside and made a new installation. 
2.When partition started i formated my ext3 file system (my Ubuntu partition) and swap.
3.I also have a dual boot ( Ms XP) in ntfs file system. So my partition manager was like this :
dev/sda1 ntfs /windows
dev/sda2 ext3 /
dev/sda3 swap

These ( /windows  and  /  ) are the mountpoints for each partition. 

I simple formated my linux partitions (ext3 and swap) and did a new installation.
I don't know if this is what you you need but its for sure a solution in this problem. 

Hope i helped you ( with the "clean up" and the partition manager).

PS: if you do something like this DONT format your Vista partition!

---

### Post by rdotex on 2009-03-06
Excuse me for interrupting, but I am also wanting to 'start from scratch'.  I've built a new box and have a 250GB hdd and want to dual boot Ubuntu 8.04 and Win XP Pro.  I've already tried two times, first having Ubuntu installed first and then XP, but I had not done the partiioning very well and needed more room in the XP partition.  So, I used the XP CD to reformat the drive, installed XP, then Ubuntu.  Now, I can't get the grub corrected and just want to start over and do it right.

What should I do first, second, etc.?

Any suggestions will be appreciated.

---

### Post by wpshooter on 2009-03-06
> **rdotex said:**
> Excuse me for interrupting, but I am also wanting to 'start from scratch'.  I've built a new box and have a 250GB hdd and want to dual boot Ubuntu 8.04 and Win XP Pro.  I've already tried two times, first having Ubuntu installed first and then XP, but I had not done the partiioning very well and needed more room in the XP partition.  So, I used the XP CD to reformat the drive, installed XP, then Ubuntu.  Now, I can't get the grub corrected and just want to start over and do it right.

What should I do first, second, etc.?

Any suggestions will be appreciated.

Get [www.killdisk.com](www.killdisk.com) and WIPE the drive completely clean.  Then install XP first and in the process leave some unformatted space for your Ubuntu partitions.  Then after XP is properly installed, come back and then install Ubuntu in the unformatted drive space with partitions / = root (make it bootable), /home and /swap.  You may need to make your /home partition and /swap partitions logical partitions instead of primary but make sure that you make the / root partition a primary partition.

But if it were me, I would just get rid of the XP piece of junk and install Ubuntu only.

Good luck.

---

### Post by rdotex on 2009-03-06
Thanks for your suggestions.  I really appreciate it.

---

### Post by theozzlives on 2009-03-06
> **s.dalas said:**
> I don't really know if i can help you, but i can tell you what i did when my system started to slow down after i was experiment with Wine and crossover and other apps.
1.I just restarted my system with the Ubuntu cd inside and made a new installation. 
2.When partition started i formated my ext3 file system (my Ubuntu partition) and swap.
3.I also have a dual boot ( Ms XP) in ntfs file system. So my partition manager was like this :
dev/sda1 ntfs /windows
dev/sda2 ext3 /
dev/sda3 swap

These ( /windows  and  /  ) are the mountpoints for each partition. 

I simple formated my linux partitions (ext3 and swap) and did a new installation.
I don't know if this is what you you need but its for sure a solution in this problem. 

Hope i helped you ( with the "clean up" and the partition manager).

PS: if you do something like this DONT format your Vista partition!

How about:
sda1 NTFS
sda2 ext3 / (10-20 GB)
sda3 ext3 /home (what's left)
sda5 swap (amt of RAM you have)

Believe me if you re-install or upgrade it's easier to have a seperate /home.

---

### Post by troegs on 2009-03-06
> But if it were me, I would just get rid of the XP piece of junk and install Ubuntu only.
I'm with you there but to be quite honest there are still a couple programs i need one of the main ones being dreamweaver. If anyone can suggest a honest to goodness linux variant that is comparable in every way, (expecting crickets at about this point) please let me know as that is the main thing holding me back, that and the m-soft office. Yes i know open office is a decent productivity suite, however in my opinion it is not a full office replacement. Can I type a paper? ya. simple spreadsheet? ya. Do it like i can in office? no. That may just be me though.

Anyhow, at the moment a full disk kill isn't really an option as I don't have a full vista cd, just a recovery. As a cs student I get free xp business but I'll have to wait and see. Another reason for holding on to the windows is a few things in my pc still don't transfer.

So all that being said, is there any way I can just wipe the swap and main disk? like from a live cd using gpart.. or perhaps my backtrack bootable usb. I just want to make sure i don't start turning my HD into sashimi again. As a fairly computer literate, however linux semi noob, changing the properties of all the dorked up partitions via the shell you get from the live cd was not a fun intro to linux and perhaps the memories of that are what's making me so gunshy to go through it all again. Granted I've come a whole long way from where i was 3 months ago. (writing my first python gui app yay! lol)

Thanks for all the input, and anymore that keeps getting added.

---

### Post by s.dalas on 2009-03-06
> **theozzlives said:**
> How about:
sda1 NTFS
sda2 ext3 / (10-20 GB)
sda3 ext3 /home (what's left)
sda5 swap (amt of RAM you have)

Believe me if you re-install or upgrade it's easier to have a seperate /home.

Thats good too. Actually its better but its a little more complicated for newbies. 

> 
So all that being said, is there any way I can just wipe the swap and main disk?

I think you got the answer. just format the ubuntu partitions and make something like above.

---

