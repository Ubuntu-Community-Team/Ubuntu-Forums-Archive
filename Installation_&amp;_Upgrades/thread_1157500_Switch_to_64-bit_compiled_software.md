---
title: "Switch to 64-bit compiled software?"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by grenadier32 on 2009-05-12
Hi all--

So I made a dumb mistake when I installed Ubuntu on my new laptop: I didn't realize that it had a x86-64-bit processor, and I installed the 32-bit Ubuntu onto it. Is it possible to upgrade the system in place by changing my apt sources and upgrading? Or would this be really dangerous? I don't see why it would be, all my configuration would still work, presumably.

Thanks in advance!

---

### Post by Partyboi2 on 2009-05-13
You would need to reinstall Ubuntu using the 64bit version.

---

### Post by saivin on 2009-05-13
Yes, the above suggestion makes sense...

Unless we are gurus and know what we are doing, its better to reinstall with 64-bit version.

You are not alone buddy, me too scratching my head.  Installed 32-bit on laptop which has most modern hardware.  If we don't start using the technology on a wide scale, how will it gain support from ISVs?  Will not repeat this mistake from now on... :)

---

### Post by zvacet on 2009-05-13
@ **grenadier32**

You can run 32 bit Ubuntu on 64 bit procesor.It is not a problem.You will want to install 64 bit version if you have >4 GB of ram.That would be good reason.If that is not a case just keep your 32 bit version and enjoy Ubuntu.

---

### Post by skymera on 2009-05-13
If you need 64bit, then reinstall.

If 32bit is fine, then you may as well leave it.
I only run 64bit due to 4GB RAM

---

### Post by grenadier32 on 2009-05-13
> **zvacet said:**
> @ **grenadier32**

You can run 32 bit Ubuntu on 64 bit procesor.It is not a problem.You will want to install 64 bit version if you have >4 GB of ram.That would be good reason.If that is not a case just keep your 32 bit version and enjoy Ubuntu.

Sadly, that is the case, and I am thus limited to around 3.4 GB of it. I guess I have no choice but to back up and reinstall at some point (or maybe just move my home directory to another partition to simplify the process). May as well wait for Karmic if I'm going to be doing that, I guess.

Are there any disadvantages to 64-bit? Problems it can introduce?

---

### Post by oldos2er on 2009-05-13
I suggest you read the stickies on the x86_64 forum.

---

### Post by Artemis3 on 2009-05-13
Backup and reinstall. 64 bits is worth it.

---

### Post by jowilkin on 2009-05-13
In most cases, I don't think 64-bits is worth it.  You will still run into problems with several applications not fully supporting 64 bit systems. One example I ran into just recently is the media player XBMC.  Some features just don't work on the 64 bit version (web interface for example) and often it just crashes for no reason.  I posted about my problems on the XBMC forum and they told me I would be much happier running the 32-bit version, and I am.

On top of that, there is no real speed difference.

The only reason to run 64 bits is if you have >4gb ram.

Since you have 4 gigs, you are losing a bit, but I doubt you are actually ever using the full 3.4 gigs that you are able to address right now.  Actually installing the PAE enabled kernel may let you use the full 4 gigs, I know on servers with >4gb of ram, it allows you to address the full amount of memory (but any single program cannot use more than 4gb).

---

### Post by Artemis3 on 2009-05-13
There IS a performance gain using 64 bits over 32 bits, google the benchmarks out there. 

XBMC seems to use mplayer, so you need the medibuntu repositories and install the package w64codecs for those few proprietary formats that don't work.

All machines i install Ubuntu, i try the amd64 cd first, and only if the message about cpu not supporting 64 bits comes, then i use 32 bits.

There is just no reason not to use 64 bits if you have a recent processor. Been using it for 2 years on many machines.

---

### Post by jowilkin on 2009-05-13
> **Artemis3 said:**
> There IS a performance gain using 64 bits over 32 bits, google the benchmarks out there. 

XBMC seems to use mplayer, so you need the medibuntu repositories and install the package w64codecs for those few proprietary formats that don't work.

All machines i install Ubuntu, i try the amd64 cd first, and only if the message about cpu not supporting 64 bits comes, then i use 32 bits.

There is just no reason not to use 64 bits if you have a recent processor. Been using it for 2 years on many machines.

There is no *noticable* performance gain in most applications though.

For XBMC this is an exchange I had with one of the developers after having a wide variety of problems with the 64-bit version, Me: [quote=Me]
Ah ok thanks. I guess between this and boxee not working on 64-bit, I might just wipe the OS and go back to 32-bit.[/quote]
Developer:
[quote=XBMC-Dev]You will probably be quite happy you did.[/quote]
See [http://xbmc.org/forum/showthread.php?t=49940](http://xbmc.org/forum/showthread.php?t=49940).

It is not a matter of me simply not being able to figure out codecs, I'm quite computer/Linux literate.  Here is another bug that seems to only effect 64-bit installs of XBMC - [http://xbmc.org/forum/showthread.php?t=49641](http://xbmc.org/forum/showthread.php?t=49641)

The 64-bit support situation is much better than a couple years ago (i.e. when there was no 64-bit flash player), but it is still not perfect.  The average user is still better served going 32-bit in many cases unless they are heavily using an app that has clear performance benefits from 64-bit (yes I know there are some).

---

