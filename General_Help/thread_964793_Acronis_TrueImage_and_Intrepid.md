---
title: "Acronis TrueImage and Intrepid"
date: 2008-10-31
forum: General Help
---

### Post by shane19174 on 2008-10-31
After doing a fresh install of Intrepid on an older laptop, I found out that Acronis TrueImage (which I have been using for several years to make backup images of drives and partitions) is no longer able to image partitions made with Intrepid. [Here]("http://ubuntuforums.org/showthread.php?t=899190") is a thread with the details. The options that I know of are the following:

1) I can reinstall Intrepid, having partitioned and formatted with a Gparted liveCD or something other than the Intrepid disk.

2) I can leave things as they are and continue using Acronis TrueImage, only that I'll have to use the slower sector-by-sector method.

3) I can switch to Partimage (or SystemRescueCD or Clonezilla).

I really don't like the first alternative: I spent some time setting up the installation and don't want to have to do it again. Moreover, I'd have to remember to partition/format with a separate tool before each future installation (as detailed in the link above, the incompatibility with Acronis is due to a change in the ext3 format, and I don't expect that Jaunty and later versions will revert to the pre-Intrepid formatting).

The second alernative is no good either: the sector method is really slow, and it's even slower when you're backing up to an external drive from an old laptop that still uses USB ver. 1.

The third option seems the most promising, but I've still got a few reservations. Most centrally, I want a solution with a GUI that is simple and self-explanatory. I realize that partimage has a basic GUI, as does Clonezilla, and I realize that many would prefer no GUI at all. But I need something that non-geeks with no prior experience will be able to boot up to restore an image. (I installed Ubuntu on an old computer for my wife's classroom at an elementary school, and she sometimes needs to do a restore. She's not stupid, but she has to do this quickly and amidst lots of distractions, so there can be no room for error here.) Acronis was perfect for this, but partimage & co. look too complicated and, in a word, "primitive" (I know, that's just looks, but we have to admit that they're important to most users--see Mac OSX, but also Ubuntu with Compiz, etc).

So my question: Can anybody recommend an alternative solution that will backup and restore complete partitions and/or disks, which can be booted from a live CD, and that has a graphically pleasing GUI in the style of, say, Gparted?

Or couldn't a better GUI for partimage be created and integrated into an Ubuntu liveCD? This would be the optimal solution for me...

Thanks for any suggestions.

---

### Post by louieb on 2008-10-31
The [Clonezilla ]("http://www.clonezilla.org/")front end to partimage  is pretty simple. Give it a try. Just a simple ncursors screen but it works.

---

### Post by shane19174 on 2008-10-31
Thanks for the response, louieb.

I'm doing a backup of the laptop right now. The speed is quite good. But the interface itself still leaves a lot to be desired. I have no real problem with it myself, but I can't imagine someone with a Windows-only background liking it. Acronis's GUI in fact looked a little TOO much like Windows for my taste, but it's basic functionality was great: point and click on a list of partitions and disks, add comments, decide on the exact location of the backup, etc. There's still too much room for error with Clonezilla, not to mention aesthetics. Can't we get a GNOME frontend for Partimage the same way we get one with Gparted?

Or are there other alternatives already out there?

Thanks

---

### Post by kaibob on 2008-10-31
> **shane19174 said:**
> After doing a fresh install of Intrepid on an older laptop, I found out that Acronis TrueImage (which I have been using for several years to make backup images of drives and partitions) is no longer able to image partitions made with Intrepid....
Thanks for the information. I'm a long time True Image user and hope to continue using it. If I understand correctly, I'll be OK as long as I use a gparted CD to both create and format the partitions that will be used during a fresh Intrepid install. I normally do that anyway, so hopefully True Image will continue to work.

BTW, I'm going to monitor the Acronis True Image forum to see if this issue is mentioned:

[http://www.wilderssecurity.com/forumdisplay.php?f=65](http://www.wilderssecurity.com/forumdisplay.php?f=65)

There are many people who use True Image Home to image Linux partitions, so I'll be interested to see if this issue is discussed.

Thanks again.

---

### Post by shane19174 on 2008-11-04
Clonezilla failed to restore GRUB on my laptop. It was no big deal, really, as I could restore it from an Ubuntu live CD. Still, not really an option that I can recommend to friends with little or no experience. So again: any other options out there?

And kaibob, have you seen anything on the Acronis site?

Thanks.

---

### Post by kaibob on 2008-11-04
I checked the True Image forum and found no mention of this issue. I also checked the manuals for True Image 11 and 2009 but found nothing. I have started a thread on this issue in the True Image forum at:

[http://www.wilderssecurity.com/showthread.php?p=1343077#post1343077](http://www.wilderssecurity.com/showthread.php?p=1343077#post1343077)

I did a google search on "256 inodes acronis" (no quotes), and found many postings on this precise issue and not only in relation to Ubuntu. It appears that there is no fix for this right now other than to stick with a 128-byte inodes Ext3 system. 

As an aside, the mod's in the True Image forum are very, very slow in responding to new threads, so it may be a while before a response is posted.

---

### Post by NoVista on 2008-11-04
Interesting read. I have used Acronis TI for years.
One thing I have noticed about Acronis though, even before this problem. If you try to do a backup, from a pre-made image file, on ext 3, and you use the backup cd to run the program at bootup, it will always lock up and freeze, after it runs a bit, ruining the partition of course in the process. Running the main program from a hard disk, however, always worked well.

If you have never truly "ripped" a cd or dvd, and used sector by sector, you can bet your booties it's going to take forever. :)

Thanks for the Heads Up.

---

### Post by ove overgaard on 2008-11-04
Hej
May I propose Terabyte's Image for linux. I have used it for some years. It is simple, cheap and it just works.

Kindly Ove

---

### Post by Orographic on 2008-11-07
> **NoVista said:**
> Interesting read. I have used Acronis TI for years.
One thing I have noticed about Acronis though, even before this problem. If you try to do a backup, from a pre-made image file, on ext 3, and you use the backup cd to run the program at bootup, it will always lock up and freeze, after it runs a bit, ruining the partition of course in the process. Running the main program from a hard disk, however, always worked well.

If you have never truly "ripped" a cd or dvd, and used sector by sector, you can bet your booties it's going to take forever. :)

Thanks for the Heads Up.

I haven't found this at all. My Acronis boot CD runs perfectly and never freezes when restoring Hardy Heron. I've done it maybe a dozen times with no problem. Good to get the heads up on this issue though as I did a drive check via Seatools today after getting that Acronis error with Intrepid. I figured it might be a conflict with Intrepid and Acronis.

Will do some more reading.

---

### Post by scouser73 on 2008-11-08
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by Orographic on 2008-11-09
That second link didn't work for me but this one seems to:

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

I'll look into it all a bit more soon. Thanks for your input.

---

### Post by Orographic on 2008-11-09
One question: Why would you need to install the first program you listed if the second one makes an iso image of your system anyway?

---

### Post by shane19174 on 2008-11-26
In case anyone is still following this topic, I have been in contact with Acronis concerning this issue. Up to now, I haven't gotten any really straight answers. They first asked me to download the demo version of True Image 2009, but unfortunately the rescue disk it made didn't allow making backups, so this was no help. Then they sent me a link to an .iso, and it no longer reports (erroneously) that ext3 partitions with 256-byte inodes are damaged, as True Image 11 did. But the backup process is incredibly slow nonetheless, making me think that the new version simply covers up its lack of compatibility with the new standard and silently does a sector-for-sector backup without informing the user. Not much of a solution to the problem. And that's what I told Acronis. I didn't really expect to hear anything back after that, but I just got the following email:

> Wir möchten Ihnen mitteilen, dass dieses Problem vor kurzem festgesetzt wurde.
Unser Entwicklungsteam arbeitet mit dem Hochdruck an der Lösung dieses Problems.

Sobald die Unterstützung von 256-byte Inode implementiert wird, schicken wir Ihnen eine Nachricht.


In English:

"We would like to inform you that this problem was recently identified. Our development team is working hard on a solution to this problem.

As soon as support for 256-byte inodes is implemented, we will notify you."

OK, it might be an empty promise, but who knows? I keep telling Acronis that lots of Linux users are turning their backs on them because of this, and maybe if enough people tell them the same they'll do something about it. In the hopes that that might be true, I encourage everyone affected by this to write to Acronis and tell them. Even if there are other (free) solutions, I don't want to write off the money I spent on this program yet. And I still think that True Image is the most user-friendly solution out there.

Anyway, in case Acronis really does write back to me and tell me that 256-byte inode support has been implemented, I'll be sure to post back here.

---

### Post by NoVista on 2008-11-26
> But the backup process is incredibly slow nonetheless, making me think that the new version simply covers up its lack of compatibility with the new standard and silently does a sector-for-sector backup without informing the user.

To confirm that, check the size of the image file made. If you selected to compress the image before making it, it of course can not do this when doing it sector by sector.
So, to be proper, that option should not even be made available either, in that particular instance, but it is.

---

### Post by kaibob on 2008-12-31
I just noticed the following on the True Image forum: 

> Please be aware support for 256 I-nodes was implemented in the latest builds of Acronis True Image Home 2009. The similar update is planned for Acronis Disk Director 10.0.

[http://www.wilderssecurity.com/showthread.php?t=227327](http://www.wilderssecurity.com/showthread.php?t=227327)

---

