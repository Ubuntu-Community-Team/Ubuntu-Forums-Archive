---
title: "Is This Hard Drive Failure?"
date: 2009-03-29
forum: Hardware
---

### Post by linuxisevolution on 2009-03-29
First Grub gave error 17. Then I reinstalled Grub and found that both my windows ntfs partition and the Ubuntu ext3 was corrupted. I used fsck to fix them and all was fine. But then Linux Mint would not get more than about 1hr uptime and would start with icons dissapearing and then applications would not open, claiming "I/O ERROR". I Installed Ubuntu over Linux Mint and it was all good on that side. Then Windows xp lost the luna theme and reverted to classic, and plug n play broke. So I reinstalled Windows...

But now a few weeks later it's all happening again.
My father called some tech support and he says they said it was "normal". 

So who is right?

---

### Post by linuxisevolution on 2009-03-29
bump..

---

### Post by linuxisevolution on 2009-03-29
why isn't anyone responding? such an easy question....


:confused:

---

### Post by FFfanatic on 2009-03-29
Since you have Windows, DL, install and run HDTune. Then look at both the SMART tab and do an error scan. Post a screen if you can't interpret the results.

---

### Post by linuxisevolution on 2009-03-29
> **FFfanatic said:**
> Since you have Windows, DL, install and run HDTune. Then look at both the SMART tab and do an error scan. Post a screen if you can't interpret the results.

Fsck always fixed it -temporarily.

Will hdtune fix the Linux partiton?

---

### Post by linuxisevolution on 2009-03-29
> **FFfanatic said:**
> Since you have Windows, DL, install and run HDTune. Then look at both the SMART tab and do an error scan. Post a screen if you can't interpret the results.

The smart tab says everything is OK. I did a quick error scan on both drives (both drives in the option list are the same name so I don't know which one I am scanning..)

The quick scan reported 0 bad blocks on both drives. I am doing a thorough scan now. Are you sure this program is accurate? Will it scan the whole drive? (i.e all partitions). :confused:

Thanks!

---

### Post by Hobgoblin on 2009-03-29
Select the memtest option from the Grub menu, let it run a couple of hours.

---

### Post by linuxisevolution on 2009-03-29
> **Hobgoblin said:**
> Select the memtest option from the Grub menu, let it run a couple of hours.

I did that a while ago. It detected 6 errors in the first hour. This is a brand new machine I built. 2 1gb sticks of ram. 2 250gb drives. 

Could bad ram cause the hard drive to read/write incorrectly?

---

### Post by linuxisevolution on 2009-04-01
bump

Windows now locks up on the machine. After a while the mouse refuses to move and the keyboard is unresponsive.

:(


Family thinks its my fault..

---

### Post by linuxisevolution on 2009-04-04
bump

---

### Post by ubuntu27 on 2009-04-04
Does mounting your WIndows partition from Linux give you any error?

In  my desktop computer, when my HD was failing, it game an error that says "NTFS is corrupted...please check.." (I don't remember the exact words) when tryin gto mount my other partitions.

---

### Post by mikepaco on 2009-04-06
I got this exact same problem. When I booted Windows after physically moving my computer, Windows would completely lock up after a minute or so. Chkdsk found nothing, so it's definitely a hardware problem. When I tried running my virtual Ubuntu installed in said Windows, Ubuntu said something about the nfts being corrupt, and I swear I could have heard some odd sounds coming from my harddrive.

---

### Post by Dark_Stang on 2009-04-06
Sounds like your hard drive is failing with bad sectors. Fsck's and Chkdsk's will fix them temporarily, but they tend to spread like cancer. If you want to be sure you can download the diagnostic utility from the hard drive manufacturer's website and run that.

---

### Post by mikepaco on 2009-04-06
Can you recommend any OS-independent backup utilities before my hard drive finally dies?

---

### Post by chriswyatt on 2009-04-06
Ubuntu LiveCD?

---

### Post by mikepaco on 2009-04-06
I was thinking of something a little more lightweight, but that works too.

---

### Post by ubuntu27 on 2009-04-06
> **mikepaco said:**
> Can you recommend any OS-independent backup utilities before my hard drive finally dies?

How about trying


1)[SystemRescueCd]("http://www.sysresccd.org/Main_Page") Linux

> [SystemRescueCd]("http://www.sysresccd.org/Main_Page") is a Linux system on a bootable CD-ROM for repairing your system and your data after a crash. It also aims to provide an easy way to carry out admin tasks on your computer, such as creating and editing the partitions of the hard disk.

2) [URL="http://www.remote-exploit.org/backtrack.html"]
BackTrack Linux[/URL]

> [BackTrack]("URL="http://www.remote-exploit.org/backtrack.html") is an Ubuntu-based distribution with a collection of security and forensics tools. It was created by merging Auditor Security Linux with WHAX (formerly Whoppix).


3)  [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12")

> [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12") (TRK) is a bootable Linux distribution aimed specifically at offline operations for Windows and Linux systems such as rescue, repair, password resets and cloning.

---

### Post by cariboo on 2009-04-06
> **linuxisevolution said:**
> I did that a while ago. It detected 6 errors in the first hour. This is a brand new machine I built. 2 1gb sticks of ram. 2 250gb drives. 

Could bad ram cause the hard drive to read/write incorrectly?

I would suspect the ram if you are getting errors.

I would suggest going to the hard drives manufacturers web site and downloading their diagnostic tools and run them on your hard drives. This will tell you if your drives are failing.

Run Memtest overnight to see how many errors you get anything more than zero, means a problem with the ram. If it is new it shouldn't be to hard to get an RMA for replacement.

Jim

---

### Post by rush_ad on 2009-05-04
> **cariboo907 said:**
> I would suspect the ram if you are getting errors.

I would suggest going to the hard drives manufacturers web site and downloading their diagnostic tools and run them on your hard drives. This will tell you if your drives are failing.

Run Memtest overnight to see how many errors you get anything more than zero, means a problem with the ram. If it is new it shouldn't be to hard to get an RMA for replacement.

Jim

my laptop is behaving in the same exact manner. and i also upgraded my RAM (added a 2gb chip). however i have not yet ran memtest... will do it tonight. i hope it is not the hard drive.

but... windows was running fine... why is linux giving me problems????

---

### Post by freonchill on 2009-05-04
spinrite

[www.grc.com](www.grc.com)

---

