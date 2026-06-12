---
title: "Formatting dvd-rw doesn't work in nautilus"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by hesoez on 2006-06-08
Hi,

I use nautilus to write my discs.
this is what works:

- writing cd-r: works
- writing cd-rw:works
- blanking cd-rw: works
- writing dvd-r:works
- writing dvd-rw:works
- formatting dvd-rw:doesn't work

I don't have dvd+r and dvd+rw so i couldn't test them.

The problem is that when i insert a dvd-rw that is not empty, try to write to it and tell nautilus to erase the existing data, it will give me "error writing to disc" and the dvd still contains the old data. When not needing to erase the old data(blank dvd-rw or dvd-r) nautilus writes the disc without problems.

I've installed gnomebaker to see if the problem existed there.
After selecting "format dvd-rw" in gnomebaker it seems to erase the disc and completes without an error message but the disc is not blanked at all.

If i run "dvd+rw-format -blank /dev/dvd" in the terminal the disc gets formatted perfectly!
If this works than why aren't nautilus and gnomebaker able to format the disc?

grtz
hesoez

---

### Post by Pulka on 2006-06-22
Same here!

---

### Post by dgrafix on 2006-06-22
me 2

---

### Post by harkonen on 2006-08-01
Yes, I noticed this too in dapper. Thanks for pointing me to dvd+rw-format :)

---

### Post by dgrafix on 2006-08-02
gnomebaker seems to wipe the disk.

---

### Post by wombat20 on 2006-08-04
I cannot get any app I've tried (and I tried most of the obvious ones) to blank or format a DVD-RW.  Is there some commercial-only magic to this or has ANYONE got this working?

I have a recent NEC drive which seems pretty good for everything else.

---

### Post by Ocxic on 2006-08-04
with dvd+rw you don't have to erase the data you simply burn over the current data.

---

### Post by spottraining on 2006-08-30
I have same problem :(

---

### Post by suoko on 2006-09-26
same problem here.

Up to now a solution is to "completely" erase the dvd-RW through nerolinux, but the process takes more than 30 mins...

---

### Post by Ocxic on 2006-09-26
try K3B it's in synaptic

---

### Post by noynac on 2006-09-26
Wouldn't work for me either using Brasero. I rebooted to WinXP and Nero reformatted the DVD-RW just fine.

---

### Post by movil on 2006-09-27
Has anyone managed to change Gnomebaker format code ?
By the way thanks for pointing me to : 
syl@nel:~/mokuto$ dvd+rw-format -blank /dev/dvd
* DVD&#65533;RW/-RAM format utility by <appro@fy.chalme*****.se>, version 4.10.
* 1.5GB DVD-RW media in Sequential mode detected.
* blanking 100.0/
Thanks guys

---

### Post by ChrisC on 2007-02-10
Aha!  Glad I found this thread.  I have exactly the same problem as described at the top.

Pleeeeease, somebody throw us a bone, like a pointer to the launchpad tracking bug, which must be out there somewhere ...

In the meantime, I can't re-use DVD-RW's :(

---

### Post by ChrisC on 2007-02-10
> **hesoez said:**
> If i run "dvd+rw-format -blank /dev/dvd" in the terminal the disc gets formatted perfectly!

If I try this (as sudo, of course), I get:

* DVD-RW/-RAM format utility by <appro@fy.chalmers.se>, version 4.10.
* 4.7GB DVD-RW media in Sequential mode detected.
* blanking .:-[ PERFORM OPC failed with SK=5h/ASC=27h/ACQ=00h]: Input/output error

Any ideas?  Burning to a brand new DVD-RW works, I just can't reuse them ...

---

### Post by ChrisC on 2007-02-10
OK, I'm learning more:

[http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-format.cpp](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-format.cpp) seems to show the source code for the dvd+rw-format tool, and it shows that in version 4.3, it added:
 * 4.3:
 * - -blank to imply -force;
 * - reject -blank in DVD+RW context and -lead-out in DVD-RW;

I don't know what that means, but it implies that I CAN'T blank a DVD+RW.  Mine is a DVD-RW.  OK, whatever, let's try the command without the "-blank":

command-prompt$ sudo dvd+rw-format /dev/dvd
* DVD-RW/-RAM format utility by <appro@fy.chalmers.se>, version 4.10.
* 4.7GB DVD-RW media in Sequential mode detected.
- media is not blank
- you have the option to re-run dvd+rw-format with:
  -force[=full] to enforce new format or mode transition and wipe the data;
  -blank[=full] to change to Sequential mode.

I tried the -blank=full and it gave me the same I/O error as in my previous post.  Fine, I'll try a "-format" ... SAME I/O ERROR.

HELP

[Note sig!  I'll pay!]

---

### Post by Ocxic on 2007-02-10
once a DVD+R/W  is formatted you can just overwrite the current contentstheres no need to format again i dunno if this applies to DVD-R/W

---

### Post by ChrisC on 2007-02-11
Yeah, I'd love to be able to "just overwrite", but it ain't workin.  The burn always terminates with a popup error, and I thought I'd isolated a more narrow/specific case of the error above.

Alas, I don't have the exact popuperror text now. If someone is willing to go back and forth with me on this (see sig!  I pay!) then reply here and I'll go through the test again.

Damn I wish Ubuntu had a paid-support option that was less than $250 ...

---

### Post by ChrisC on 2007-02-23
bump ... still a problem ...

---

### Post by ChrisC on 2007-02-25
OK, I give up, will have to retire the DVD-RWs to the shelf and use DVD-Rs from now on :(

---

### Post by odzx on 2007-03-02
> dvd+rw-format -blank /dev/dvd
thank you for that.
the only other way i am able to format dvd r+w is using k3b (checking force and unchecking fast format) but for some reason k3b does not burn for me. so for burning i use brasero.
seems stupid to use to apps for that.

---

### Post by CaptainMorgan on 2007-07-05
> **odzx said:**
> the only other way i am able to format dvd r+w is using k3b (checking force and unchecking fast format) but for some reason k3b does not burn for me. so for burning i use brasero.
seems stupid to use to apps for that.

Similar issue here, althougth K3b won't format my DVD. 

OP - great find, thanks! Works like a charm. Sometimes it's just best to stick to the command line and not venture out in the abyss.

Oh, also instead of 
> dvd+rw-format -blank /dev/dvd 

the -force switch worked in place of -blank for me.
Cheers.

---

### Post by Ocxic on 2007-07-05
you only need to format a DVD-RW once, the data is just overritten when you burn it later, it's not like a cd-rw
formatting it multiple time acctuall shortens the life span of the media

---

### Post by odin_doma2 on 2007-07-07
i formatted disk w/data with k3b ("Quick Format" is checked).
Now i tried to burn this disk, and i select "Writing Mode" - DAO.
and - Opah!...IT WORKS!!!! NO PROBLEM!!!
so i recommend to select DAO writing mode. And you'll have great chance to write your DVD-RW perfectly.

---

