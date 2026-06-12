---
title: "1 click backup/restore"
date: 2008-07-24
forum: General Help
---

### Post by Evil_Genius_Todd on 2008-07-24
Main question: I need a 1(or at least very few) click back up and restore system for my Nagios server.

Background: I work as a SysAdmin for a large multinational. Our machine room has something in the neighborhood of 100 servers in it. But only a few run any OSS of any kind(I think it's only one). The situation is a result of a kind of "Must buy a solution to every problem" mentality in management. I've recently taken it upon myself to attempt to integrate some kind of linux based system into our network to show them OSS can actually do useful work. I've chosen a Nagios Server as the pilot project. Because it's not business critical, fairly easy to set up for a linux n00b like me, and it makes fairly cool images and reports that I can wow the boss(s) with. 

The problem: I know when I present this system to the Admin team, the first question out of my boss's mouth with be "Who is going to support this?" The flipside to the "Must pay for solution" culture here is that nearly everything is outsourced to one support partner or another. I know that once I get this system set up it will likely not be modified in any significant way for years to come. The problem is, if two years from now the system crashes and takes all of the configuration files with it. I'm going to have to basically relearn all of the things I've spent the past month figuring out, again. 

The situation: The system I've built this on is a very small desktop unit from IBM(ThinkCentre M52). We just happen to have over 100 of them coming out of service in the next 12 months. So hanging on to a few hardware spares should be no problem. The Ubuntu install(8.04)+MRTG+Nagios is well under 4.7GB. Actually around 3GB, though I'm sure we can get it down much smaller if need be. It would easily fit onto a DVD-RW or memory key.


What I am looking for: I would like to implement some kind of a system configuration backup/restore that is simple enough for some one with no Linux experience whatsoever to use. Both in terms of making a backup and in restoring the system after a hardware failure. 
My ideal dream system would be able to burn a complete DVD copy of the entire system (either via partition, full file list, whatever)with the click of a single button. This DVD would be capable of booting an identically configured PC, partition it's drives, and completely restoring the previous configuration including all of packages, rights, and relationships, and user accounts.

A solution like this would make hardware failures or theft more or less inconsequential to our team. Additionally support, the back ups and restores that comprise a great deal of what our support partners actually do, would be greatly reduced. 

There is probably a better way to do this than what I have described above. I'm all ears for a better/workable/real solution.

---

### Post by hyper_ch on 2008-07-24
you're not looking for a like a "default" state to which you can always revert (burn it on cd) but you are looking for a way to also make "later" a 1-click backup?

---

### Post by Evil_Genius_Todd on 2008-07-25
Yes, exactly. I know the Simple backup system is actually quite simple to use and setup. But I was hoping to find something even simpler than that for later use. The initial configuration need not be simple/easy.

---

### Post by hyper_ch on 2008-07-25
you could make a partition image, put it on a hidden partition, make a initramfs which will just dd it back and adjust the grub menu.lst file.

---

