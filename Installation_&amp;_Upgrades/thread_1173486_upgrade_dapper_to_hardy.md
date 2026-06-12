---
title: "upgrade dapper to hardy?"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by Bunny Boy on 2009-05-29
How can I upgrade from Dapper Drake 6.06 LTS to Hardy Heron 8.04?

I already have the CD for 8.04.  Will that work?

Thanks

---

### Post by hansdown on 2009-05-29
Hi Bunny Boy.

The 8.04 disk will work fine. I prefer a clean install over an upgrade.

---

### Post by Sef on 2009-05-29
Read the link in my signature.

---

### Post by UbuntuNerd on 2009-05-29
I also preferred a clean install over the upgrade, I would back up all your important data and then do a clean install

---

### Post by Bunny Boy on 2009-05-30
> **hansdown said:**
> Hi Bunny Boy.

The 8.04 disk will work fine. I prefer a clean install over an upgrade.

OK, but wouldn't a clean install mean that all of my configuration data would be lost?

I'm not sure how you tell the installer to upgrade, anyway.

---

### Post by hansdown on 2009-05-30
Yes, everything would be a basic install with no added extras.

Don't worry, you can get help here any time.If you would like to do an 

upgrade, here is a how-to.

[http://ubuntu-tutorials.com/2008/04/23/upgrade-ubuntu-606-to-ubuntu-804/](http://ubuntu-tutorials.com/2008/04/23/upgrade-ubuntu-606-to-ubuntu-804/)

The repositories for 6.06 are closed, so you won't be able to update.

Just skip that part.Post back and we'll help you with it.

---

### Post by Bunny Boy on 2009-05-30
> **hansdown said:**
> Yes, everything would be a basic install with no added extras.

Don't worry, you can get help here any time.If you would like to do an 

upgrade, here is a how-to.

[http://ubuntu-tutorials.com/2008/04/23/upgrade-ubuntu-606-to-ubuntu-804/](http://ubuntu-tutorials.com/2008/04/23/upgrade-ubuntu-606-to-ubuntu-804/)

The repositories for 6.06 are closed, so you won't be able to update.

Just skip that part.Post back and we'll help you with it.


I don't understand how that tutorial is useful if the repositories are closed.  When I try to follow the instructions, I get these error messages:

[I]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

======================================================================

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
[/I]

I don't know what you mean by "skip that part."

When I try to boot from the Hardy CD, it tells me it can't detect my video card.  Why can't 8.04 detect a video card that 6.06 can?  When I installed Dapper it went flawlessly (2½ years ago).

So I tell it to go ahead and run the installer with low-res graphics (actually, not even the installer, just the live CD) and I get this on the screen:

[I]* Starting deferred execution scheduler atd             [OK]
* Starting periodic command scheduler crond             [OK]
* Checking battery state . . .                          [OK]
* Running local host scripts (/etc/rc.local)            [OK]
[/I]
. . . and then it hangs.

I'm also unclear on why I would want to go to all the trouble to do a clean install and have to reconfigure all of my software. It took a long time to get everything the way I want it!

---

### Post by hansdown on 2009-05-30
If you post your system specs, someone can give you better information.

You may need to use the alternate install disk.

---

### Post by Bunny Boy on 2009-05-30
> **hansdown said:**
> If you post your system specs, someone can give you better information.

You may need to use the alternate install disk.

OK, it's in my signature.  What's the alternate install disk?

---

### Post by hansdown on 2009-05-30
It's at the same download site.
Choose 8.04, select 32 or 64 bit, click alternate install disk.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Bunny Boy on 2009-05-30
> **hansdown said:**
> It's at the same download site.
Choose 8.04, select 32 or 64 bit, click alternate install disk.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

OK, well that's not really practical, since I'm on a dial-up connection.  (yes, they still exist--I live out in the country).

I'm having a hard time understanding this.  I've got the 8.04 disk, which I used successfully to install Ubuntu on two laptops, but I can't use it to install Ubuntu on the desktop computer that already has 6.06 on it?  

The upgrade manager tells me that I'd have to download 267 MB worth of updates before I can upgrade to Hardy.  Judging from some of the names of the programs on the list, I'm sure these are mostly features that I don't even use!

It seems to me that this is the sort of thing that turns people away from Linux.  I had over two years of running Dapper with absolutely no problems, then suddenly firefox started acting squirrely--myriad annoying problems but most frustratingly, spontaneously closing without warning.  I tried to upgrade ff and that turned into a nightmare, couldn't figure out how to eliminate the possibility of a virus, so I decided to back up my data and upgrade the OS, but so far I don't see a clear path ahead. 

Sorry for the rant.  I just thought it might help if you could see where I'm coming from.  Any assistance appreciated.

---

### Post by lswb on 2009-05-30
I used 6.06 until a month or 2 after 8.04 was released. Sad to say that 6.06 was the more stable release for me, with 8.04, 8.10, and 9.04, I experience occasional freezes, crashes, poorer video playback, and there are some hardware items that stopped working too, though some other hardware is now useable that was not with 6.06.

When 8.04 came out, there was a supported upgrade from 6.06 to 8.04, but I did a side-by-side dual boot install, gradually configuring 8.04 as I wanted it to be. In the forums at the time of 8.04 release, there were a significant number of users reporting problems of varying severity with upgrading as opposed to fresh install. 

Your problems with firefox closing are very likely caused by flash. Make sure you have either version 9 or one of the "final" versions of 10; The flash 10 beta and Release Candidate versions are known to cause firefox to exit unexpectedly. Were you able to install firefox 3 in dapper or are you still using 2.5?

---

### Post by Bunny Boy on 2009-05-30
> **lswb said:**
> 
Your problems with firefox closing are very likely caused by flash. Make sure you have either version 9 or one of the "final" versions of 10; The flash 10 beta and Release Candidate versions are known to cause firefox to exit unexpectedly. Were you able to install firefox 3 in dapper or are you still using 2.5?

I *tried* to install ff3, but I can't get it to work.  When I try to launch it, I get this message:

[I][B]We're sorry, this application requires a version of the GTK+ library that is not installed on your computer.

You have GTK+ 2.8.
This application requires GTK+ 2.10 or newer.

Please upgrade your GTK+ library if you wish to use this application.[/B][/I]

...even though I *did* upgrade gtk+  ...my investigation of this mess led to an intricate tangle of dependencies that I was not able to unravel, because every instruction I followed did not work.  Anyway, long complicated story that I'd really have to bash my head in to relate in detail. If I knew how to regress to ff2.5, maybe I could then fix the problem by upgrading flash?  Only problem is, every time I've tried to upgrade flash on this system, it has not worked. 

BTW, I'm running the galleon browser now, because I could not get ff to work, and Opera starting acting squirrely on me and finally quit too!  Curiously, the galleon browser has the same problem with spontaneously closing.  I guess it uses some of the same libraries as ff?  Maybe I'll try upgrading flash on it.

***addendum:***

I just tried upgrading flash numerous ways that did not work.  When I tried this:

*sudo apt-get install adobe-flashplugin*

I got the following error message:

[I]E: Couldn't find package adobe-flashplugin
[/I]
When I ran *apt-get update*, I got this:

[I]W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems[/I]

hmmm . . . I should run *apt-get update* to fix the problem I get when I run *apt-get update*?  Never mind . . .

---

### Post by lswb on 2009-05-30
I had the same message about gtk+ when I tried to install ff 3.0 in dapper. I considered trying to upgrade to 2.10 but never followed up on it as I started using 8.04 instead of 6.06. (Despite the glitches with 8.04 and the occasional freezes/crashes, it does have improvements over 6.06)

My understanding is that epiphany, galleon, and some other browsers use the gecko rendering engine that firefox uses, and can use many of the same plugins, addons, and extensions such as flash. Not sure whether that necessarily means they would be subject to the same crashes or not!

If installing flash through the repositories isn't working, try downloading the .tar.gz file from the adobe site. Don't unpack the whole tarball, just extract the file named "libflashplayer.so" Find out where the same-named file is located on your system. I don't have a running dapper installation handy, on 8.04 is is at 
/usr/lib/flashplugin-nonfree/libflashplayer.so

Save a copy of the current libflashplayer.so in case you need it, then copy the newer libflashplayer.so file to that location. When you next start firefox it will run the newer version of flash.

---

### Post by Bunny Boy on 2009-05-31
> **lswb said:**
> 
If installing flash through the repositories isn't working, try downloading the .tar.gz file from the adobe site. Don't unpack the whole tarball, just extract the file named "libflashplayer.so" Find out where the same-named file is located on your system. I don't have a running dapper installation handy, on 8.04 is is at 
/usr/lib/flashplugin-nonfree/libflashplayer.so

Save a copy of the current libflashplayer.so in case you need it, then copy the newer libflashplayer.so file to that location. When you next start firefox it will run the newer version of flash.

I tried that and it didn't work.  Websites still think the browser has obsolete flash!

---

