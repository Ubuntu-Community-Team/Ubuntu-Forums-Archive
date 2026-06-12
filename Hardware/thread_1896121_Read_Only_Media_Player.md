---
title: "Read Only Media Player"
date: 2011-12-16
forum: Hardware
---

### Post by snurfle on 2011-12-16
Ubuntu 11.10
Kernel 3.0.0.14
More details to follow

This problem has existed for several years and on multiple computers; I have been writing it off as "I'm doing something wrong" or "My hardware is bad", but I've finally come to the conclusion it is an Ubuntu problem.

The short version is this:
While copying files to my media player, the process will stop at some point, and inform me that I am now trying to copy files to a "Read-Only File System".
This happens out of the blue, for no obvious reason.
The only fix that I have found that will work is to format the player on a Windows machine and start over.
Unfortunately, this bricked one of my players as I was not able to back up the firmware which was apparently loaded into memory and not hardwired.

This happens on the following players:
Sansa E250 with the sansa firmware, and also with rockbox
Sansa Fuze also with sansa and with rockbox  (Both sansa players with multiple cables)
Pryus MP4 player (rockchip, 2gb player)
Polaroid PMP282 media player

This also happens with just the SD memory chips:
PNY and sasa, 2, 4, 8, and 16 gig chips,
and it happens when they are plugged into the media player (as a new storage drive) or in a card reader (with several different sd-microsd adapters).
It has happened in the following card readers:
Neodio Technologies Corp. 7-in-1 Card Reader (external)
another external card reader (no longer have it; assumed it was a card reader problem so replaced it)
and Alcor Micro internal multi card reader.

I have used multiple USB cables for the readers and the players.

This has happened on both of my desktops and also on my laptop.

This has happened since my first media player in 2007, and has continued to be a problem randomly over the years.

Most recently, I found a thread that suggested file copying to thumb drives and media players should be done from the command line rather than from Nautilus. (something about Nautilus making the transfer speed go wonky because of trying to read the files and make thumbnails?)
So, on my newest desktop machine, with a 2-week old card reader and a 2-month old installation of Ubuntu 11.10, I have begun doing it from the terminal.
It certainly made the copying speed much faster, but yesterday while copying a few songs to the card reader, I got the same old "read only file system" error.

According to my windows machine at work, there is no problem copying files on and off of the card; it is only ubuntu that has the problem.

I reformatted the card and have started over again.

This is an incredible waste of time, and is making me question my decision to go with strictly Linux-based OS at home.  If reading and writing to a memory stick or media player is so difficult, the what other issues are still to come?

Please note:  this is NOT fixed by any chmod or chown commands... it is NOT a question of root access, this is a "read only" issue, identical to sliding the little tab over on a floppy disk.  Once the error happens, the player or memory stick is essentially useless on any ubuntu machine (other than being able to read the files; but not delete or move or add new files).

I have not, in 4 years, been willing to plug my camera or memory card into any ubuntu machine; I dont really want to have to replace a $1500 camera because my OS decides to trash it.

Sorry for venting, but this really is a problem in my mind... multiple pieces of hardware, multiple versions of the kernel as well as multiple releases of the OS...  

I am fed up at the wasted time, and I don't know what to try next.

---

### Post by snurfle on 2011-12-18
well, THIS is new...
After spending all yesterday trying to see if it will do it again, I now have 3 'read-only' sd cards, one read-only media player, and new, none of my sd card readers work... but they both work is I run the ubuntu live cd.
I did not change any files or settings, I have simply been copying music files onto memory cards.

Any hints?
Should I just make this a bug report?

---

### Post by snurfle on 2011-12-18
Is there some way to just disable or remove the card reader?  Some setting or config file somewhere so I can see if ubuntu will re-install it?  It worked fine when I first installed it, and the live cd can find it and use it with no trouble, so is there at least some way to make the current installation re-initialize it?

---

### Post by snurfle on 2011-12-20
Bump


at least somebody give me a hint where to start on this?

---

### Post by snurfle on 2012-01-11
*Bump*

But only because I tried to copy a podcast to my player this morning, and after a full 5 minutes of inactivity, Ubuntu tells me that the destination does not exist.

Nothing showed up in Nautilus (that is, no player after the file copy failed), and it also did not show up in palimsest.

I unplugged it and plugged it back in, and it is now read only.  The whole player.

I brought it to work and plugged it into a windows machine, and have tried running chkdsk, only to be repeatedly told "An unspecified error occurred."

The podcast cannot be deleted using windows; explorer will let me delete it, but then if I exit that folder and re-open it, the file is still there.

Deleting it from windows terminal does not work either... it says it deletes it, but then doing "dir" shows it is still there.

What is the deal with Ubuntu and media players?  This is a brand new (month old) sansa player that has worked fine until I tried...   sorry, ranting now.  
Just frustrated beyond words at this point.  Please please please somebody tell me what to do to make ubuntu stop screwing up my stuff?!?!

---

### Post by snurfle on 2012-01-11
One more bump to share one more piece of information...

When copying the podcast this morning, I was copying it to the media player.
The media player had a fairly new (~3 wks old?) SD card plugged into it.
I just discovered that not only is the media player essentially useless until I can reformat it, but the SD card is also behaving exactly the smae... read-only on Ubuntu, and unable to fix on windows with chkdsk ("An unspecified error occurred.")

I was not copying the file onto the SD card when the player got trashed, but only onto the player itself.

Why would ubuntu take out both the player AND the sd card at the same time?

Is this something requiring a bug report, or is this just a continuing issue that is unique to me, or is there some kind of workaround... something, anything?

---

### Post by snurfle on 2012-01-13
Problem solved.

I took the new SD card back to Best Buy, and they replaced it for free.
I bought a new media player and windows 7 home premium.
The installation borked my ubuntu installation, so I will have to reinstall it some time.
But, I spent all evening copying files to my new media player, and didn't have a bit of trouble.

Not a real solution to the ubuntu problem, but at the same time, the math just makes it a pretty obvious solution in hindsight... it's cheaper to give my money to microsoft than to keep screwing up and replacing media players.

---

### Post by gordintoronto on 2012-01-13
Here's why you never got a response: no one else has this problem. 

It makes it difficult to believe that you have had it with multiple computers, multiple cables, multiple devices, when I've done these things with multiple computers, multiple devices and multiple devices, and never had anything go wrong.

---

### Post by snurfle on 2012-05-02
Just on a lark, I tried 12.04... I was smart enough to use one of my older players.
And it futzed it up after copying only one file.

>"Here's why you never got a response: no one else has this problem. "
That seems to be inaccurate:
[http://ubuntuforums.org/showthread.php?t=1359835](http://ubuntuforums.org/showthread.php?t=1359835)
[http://ubuntuforums.org/showthread.php?t=1085858](http://ubuntuforums.org/showthread.php?t=1085858)
[http://askubuntu.com/questions/47538/how-to-make-read-only-file-system-writable](http://askubuntu.com/questions/47538/how-to-make-read-only-file-system-writable)
[http://ubuntuforums.org/showthread.php?t=1820549](http://ubuntuforums.org/showthread.php?t=1820549)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/124553](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/124553)
[http://ubuntuforums.org/showthread.php?t=1855130](http://ubuntuforums.org/showthread.php?t=1855130)

---

### Post by rpdayton on 2012-09-14
I saw this marked as solved and thought i would find how to fix it but buying windows it not really the answer.  you should not mark it as solved if there is not a solution.
 
i have the same problem.
 
[http://ubuntuforums.org/showthread.php?t=2057276](http://ubuntuforums.org/showthread.php?t=2057276)

---

