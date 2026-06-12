---
title: "1 file with 2 multiply-claimed block(s)"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by binary00mind on 2008-01-31
I am on on my 4th or 5th day.on Ubuntu 7.10 with all updates..After restartarting.the machine normal way.On the reboot,after witnessing matrix of numbers for minute..I was presented with black screen. At the very bottom command line = root@127:~# ..with note that it is a read only ! command..( I guess to view the file or files involved). Also a note; the 2 multiply-claimed block(s), are shared with 1 file(s)
P.S...I would love to make an extensive search, here at Ubuntu Home Forums but my resources are very limited. (I am on broken pda, no chat or e-mail) If this subject and/or conflict was brought up previoously and belongs to a different thread, sorry about it..I just need some direction..to save the day, before I use Partition Magic

---

### Post by binary00mind on 2008-02-01
> **binary00mind said:**
> . Also a note; the 2 multiply-claimed block(s), are shared with 1 file(s)After I reviewed my initial post, I see that I failed to include much more needed information. First I belong to a group of people who have problems because of the wireless card. I am kinda mad at myself that during a moment I was presented with the opportunity and a chance to install the "bmc43xx " firmware (I am recalling the name from memory) I didn't do it.There were 2 of restricted items..And just by trying to be extra careful and going by old Windows habits, I wanted to install them 1 by 1.and that was a mistake that I didn't go for both of them at once. After going for the first one from the top of the list (related to ATI card ) I never had the opportunity to get to the other one. Because I was in read only mode (restricted)..I did an easy 100 restarts with no problems..I have no other OS installed. on my computer Besides Ubuntu. I have 5 (all empty) partitions. I am booting from Lilo .I am connected to the same router "via air and land".After getting stuck on #4 .the autmatic file system check (fsck) of the root filesystem failed...the root is mounted in read-only mode. All lines with bash: ..are negative or not found..At this very moment,I still have my machine on. I didn't shutted down..After checking a while ago. A New line showed up. [ hub 1-0:1.0: port 4 disabled by hub (EMI?), re-enabling..] and then bqck to the line( root127:~#) I will wait a little while, maybe someone come with 
some hints..All my Linux research & documentation I have gathered over the past 10 months is on portable 320GB portable H.D that I never got permission to accessing it..thus not giving me a chance for quick references. Now it's Academic anyway..Should I Install Ubuntu side by Side on the first partition. Claim the MBR and then leave this 1 here, for future diagnostics..Anyone ? Also I am not mad or anything..Sometimes the best way to learn, is 
the hard way...BTW I'm not native english speaker, so please be clear

---

### Post by binary00mind on 2008-02-01
> **binary00mind said:**
> Should I Install Ubuntu side by Side on the first partition. Claim the MBR and then leave this 1 here, for future diagnostics..Anyone ?I was waiting for any kind of guidance....but it seems there are no willing members to do so.....I will include more info down below but first..Because of no replies to this thread. I took the following action(s) I went to BIOS I reorder booting list.."Floppy diskettes" and CD-ROM went ahead of Ide and SATA...I was thinking of booting from CD Ubuntu disc, then maybe installing new or re-install the present one..And to my suprise all my changes (in BIOS) were dis-regarded.or bypassed and erased, It went right to Lilo...Then when I went to BIOS again, all my settings were reordered to Manufacturing settings, plus all my passwords: Supervisor,User and for SATA, were cleared to null (clear) I don't know what to think about all this and what next step to take now..I don't have any access to all my floppy disc(collected over the years) With programs that could help me. HERE IS THE LATEST I've gathered:
(check forced
Duplicate or bad black in use
in node 2490175: 5031730
in node 2490176: 5031731 5031732
fsck 1.40.2
forced check
duplicate or bad block in use...)
I need some direction..I don't want to give up on Ubuntu..(despite un-friendly and RollerCoaster experience) I am not using the following to gain extra treatment..But I am disabled mostly bound to bed ..Plus I have PC related, injuries accumulated from years of abusing my body sitting at front of the computer, like Limited use of my fingers especially to my right hand(Please All of You, take your T.O. or brakes It is very serious matter) I am not in rush. I am not going anywhere..I just feel isolated...Thanks to All of You..Who were or are reading this..

---

### Post by binary00mind on 2008-02-29
Well, seems that no one answered so far. It does not matter I went over/through  many installations since then. I have changed my tactics. If all is not at least 90% OK, I Start over.
But back to this one here. I Did´t forget about this experience and I am guessing now that the problem originated from my own action, using the same name for ESSID host, and one of my keyring names (and worst, the passwords). I wonder if anyone could verify this. If yes, then it is solved, if not I will keep digesting this.( I hate to know, Not to know)...ANYONE ?

---

