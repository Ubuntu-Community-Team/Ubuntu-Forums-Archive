---
title: "[SOLVED] Drive letters for optical and floppy drives"
date: 2008-08-01
forum: General Help
---

### Post by bilijoe on 2008-08-01
Did I dream this, or did I see a screen somewhere in my system that showed drive letters for all my drives?  And, if I did see it, then the two optical drives each had two icons, each with a different letter.  The first drive was D:, and also M:, and the second was E: and also N:.  It appeared that I could not access the drives via the D: and E: icons, though the properties clearly showed which drives they related to.  I got the access I would expect by using M: and N:.  'Sup with this?:confused:

---

### Post by schauerlich on 2008-08-01
> **bilijoe said:**
> Did I dream this, or did I see a screen somewhere in my system that showed drive letters for all my drives?  And, if I did see it, then the two optical drives each had two icons, each with a different letter.  The first drive was D:, and also M:, and the second was E: and also N:.  It appeared that I could not access the drives via the D: and E: icons, though the properties clearly showed which drives they related to.  I got the access I would expect by using M: and N:.  'Sup with this?:confused:

SCSI or SATA drives are named /dev/sda (or sdb, or sdc, etc) and IDE drives are named /dev/hda (hdb, hdc, etc). An easy way to see what hard drives you have hooked up is to run

```

ls /dev | grep sd

```
If you use SATA/SCSI, or
```

ls /dev | grep hd

```

If you use IDE. If you use both, run both commands. You'll get something similar to this:

```

eric@ubuntu:~$ ls /dev | grep sd
ptysd
sda
sda1
sda2
sda3
sda4
sdb
sdb1
sdb2
sdb3
sdb4
ttysd

```

As you can see, I have two SATA hard disks hooked up named sda and sdb. Each partition is named individually, too. So sdb3 would be the third partition on the second hard disk.

---

### Post by coffeecat on 2008-08-01
Optical drives used to be referred to by the older kernel drivers as hdb/hdc and so on (iirc) - I have no idea what scsi optical drives were referred to then. With the changeover to the newer libata drivers in the last year or so, the optical drive on each of my systems has become sr0. I guess a second one would be sr1. At the moment I cannot think where you could have seen a X: type designation.

> **bilijoe said:**
> Did I dream this

You must have been dreaming about Windows, but that was no dream; that was a nightmare. :lol:

---

### Post by der_joachim on 2008-08-01
Actually, my Xandros install on my EEEPC assigns drive letters to external media. I do not recommend dreaming about Xandros though. :(

---

### Post by Jouke74 on 2008-08-01
I think that this is done to not scare windows users away too much. Since Xandros is linux, it will also assign /hda /hdb etc behind the scenes. How it is subsequently shown on your "desktop" is just a matter of naming. Funny enough linux is also basically using drive letters, just not for every partition but for every complete disk: sdA sdB sdC etc..

---

### Post by bilijoe on 2008-08-02
This is all very interesting, but none of these posts tells me how to log into a directory on an optical, or my second hard drive, from the command line of a terminal window.  I want to do the equivalent of "cd e:/home".  I have tried various combinations of "cd sda1/", "cd sda1:/", etc., and nothing gets me what I need.  This cannot be difficult, I'm just missing something.  Any help would be appreciated.

---

### Post by ModelM on 2008-08-02
You don't want to cd to the device, but instead to where the filesystem is mounted.

If your optical drive is /dev/scd0 (for our example), & it has been mounted automatically you'd type into a terminal:

mount

and you'd see a line similar to:

/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=lolly)

...meaning the filesystem has been mounted at:

/media/cdrom0

...so you'd type:

cd /media/cdrom0 to "go there".

If you then type:

ls

you'll see what's at the root directory of this optical disk.

In other words, it matters not what/where the device is. What matters is where the filesystem is mounted.

And keep in mind that's "filesystem" - not "device". You can have multiple partitions and filesystems on a hard drive, for example, and have only one mounted - or have them all mounted in wildly different areas of the directory tree.

---

### Post by northern lights on 2008-08-02
> **coffeecat said:**
> 
you must have been dreaming about windows, but that was no dream; that was a nightmare. :lol:+1

---

### Post by bilijoe on 2008-08-03
OK, I think ModeM got me straightened out.  I don't know how I've forgotten so much, but as soon as I read his post. something just clicked, and much of what I once knew about the UNIX file system came back to me.  Ah hA! There ***are no drive letters!***  What did I think this was?  DOS?  But this is Linux so... "We don't need no stinking drive letters."  Things are slowly coming back to me.

And, yes that was a nightmare--dreaming about Windows... Wait a minute, that wasn't a dream!  I actually used, and programmed for Windows from the very beginning [of Windows].  But, though the target OS was Windows, I never did any of my primary professional programming on a Windows system.  

First, it was Mini-Computers, and UNIX.  The PCs were slaved to the Unix boxes in such a way that we could code, and compile on the UNIX box, and then run the program, and monitor *everything* that went on inside the PC, all from the UNIX box.  The PC could have been in a different room.  And, if the program, or (more likely, given the kinds of things we did) Windows **did** crash, you just took over control from the UNIX box, and freed up the jammed Windows system.  And, no matter where the bug or whatever stopped the computer was, you could back trace through every line of code, right back to and through the boilerplate the compiler puts in, to initialize things.  It's amazing how easy finding bugs is, when you can walk backwards from what may actually be hundreds of lines of code away from where the thing finally hung.  

So I knew about UNIX.  Then came some work we did for the folks of Berkeley Softworks, on an OS called GeoWorks.  It was coincident with Windows version 1.  Remember that awful piece of crap?  Anyway GeoWorks was _*much*_* _more_* like XP with regard to look and feel, and, it was not a software carousel, it was a true preemptive multitasking OS, that left Windows in the dust on every benchmark, looked and felt 21st century... And it would run just fine, thank you, with it's full featured Word Processor (comperable to MS WORD 2000, in 1990), and spreadsheet (=Excel 5), graphics program, etc.,etc., etc.  And it'd do it all on an original IBM [brand] PC, Model 2 (I think.  The one with the 8086 in it --and a 20 Mb HDD?  Or was it ten?), with only 64k of memory.  

Most of you probably don't remember those days--when it was worth working 2 or 3 days, and converting all or parts of a module to Assembler Language, in order to make it a few bytes smaller, so it would fit in memory!  

Anyway, so I knew GeoWorks, which made Windows 1 look like a toy, but through "creative marketing", MS managed to squash GeoDos too (though, for years, it did run all the Palm Pilot type of devices; a fully functional, GUI interfaced OS, that only needed 16k of memory to run--worked pretty well for those guys).  

And then there was OS 2.  What an OS that was.  I also did Windows programming under OS 2 as well--much easier than doing it under Windows.  And again, better OS, 10 years ahead of Windows, just... goes missing.  Hmmm.  

So I knew about all these great Oss, **_*Real*_* _OSs!_***  OSs that didn't *ever* crash.  What on earth was I thinking?  To come [back, sort of] to Windows, after all those years working with REAL OSs.  He_ _, Windows wasn't even an OS until NT.  It was a fancy, poorly written (and documented, even worse--some say not at all), DOS program that was primarily a software carousel.  That's right, Until NT, all versions of Windows ran *UNDER DOS!*  Essentially, Windows was a GUI "shell" through which to invisibly run a command line system, which was  DOS. 

So let's see, hasn't Linux been in existence, as a fully functional, high level, multitasking OS for 16 years?  When did NT come out?  So, then, Windows is the Johny come lately--the baby in the bunch.  Whoda thunk?  

Anyway, I'm glad to say that my Windows days are completely behind me.  I still yearn a bit for OS 2, and GeoWorks.  They were both HOT, and if competition in the market place had been fair, either one of them would have burried Windows so deep that, today, no more people would know of Windows, than today, actually know GeoDos.
But today, I am happy to say ***[COLOR=Purple][SIZE=4]Ubuntu-Linux RULES![/SIZE][/COLOR]***[COLOR=Purple][SIZE=4][COLOR=Black][SIZE=1]  :guitar::guitar::guitar:

If Global Warming doesn't get us first, Linux (I predict Ubuntu-Linux) will be the OS of choice, for a majority of hsers--at home--in the office--running the Internet (oh, wait--it's laready doing that), and the Pentagon (wait, that too, I think), And all in a very few years.  So you might as well convert now--get through the [trivial] learning curve while you're still young enough for it to be easy.  Neck and Neck, Comin' Down the Back Stretch!!!  And we all know who I'm betting *my* paycheck on.
[/SIZE][/COLOR][/SIZE][/COLOR]

---

