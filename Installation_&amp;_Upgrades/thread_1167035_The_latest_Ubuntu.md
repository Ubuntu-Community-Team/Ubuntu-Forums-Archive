---
title: "The latest Ubuntu"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Gins on 2009-05-22
I am running Ubuntu Desktop version. It is 8.04 and works fine.

	Ubuntu 8.04, kernel 2.6.24-16-generic
Please advice me.

If there is a version to upgrade, please tell me the easiest way to install it.

Thanks for any help.

---

### Post by aninona on 2009-05-22
> **Gins said:**
> I am running Ubuntu Desktop version. It is 8.04 and works fine.

	Ubuntu 8.04, kernel 2.6.24-16-generic
Please advice me.

If there is a version to upgrade, please tell me the easiest way to install it.

Thanks for any help.

**You _should_ search the forums and/or google before posting.**
[http://ubuntuforums.org/showthread.php?t=1135537]("http://ubuntuforums.org/showthread.php?t=1135537")
[http://www.google.co.il/search?&q=upgrade+ubuntu+8.04+to+9.04]("http://www.google.co.il/search?&q=upgrade+ubuntu+8.04+to+9.04")

):P

---

### Post by jerrrys on 2009-05-22
im an LTS'er so im bias, but if lts works, leave it alone...

---

### Post by growled on 2009-05-22
> **jerrrys said:**
> im an LTS'er so im bias, but if lts works, leave it alone...

I agree. Don't upgrade just to upgrade. However, if you need/want the latest software, then upgrade.

---

### Post by jerrrys on 2009-05-22
> **growled said:**
> I agree. Don't upgrade just to upgrade. However, if you need/want the latest software, then upgrade.

good point...

---

### Post by Gins on 2009-05-22
Thanks everybody for the valuable comments.

The reason I posted the question is to get some information from the people who upgraded to a latest version.

Sometimes people say the latest version is more stable than the old version.

[I]I'll give you a good example.

I have upgraded My Mandriva Linux to the latest Mandriva 2009 Spring version. I did this almost 2 weeks ago.
It is more stable than the previous version. The previous version hanged very often and it drove me crazy. Probably they fixed a few bugs in the latest version.[/I]

**Again, I posted the question to learn from our friends who have upgraded or installed a latest version.**

---

### Post by Wiebelhaus on 2009-05-22
Network upgrade is by far the easiest.

Start System>Administration>Update Manager  

Click the Check button to check for new updates.

If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete. A message will appear informing you of the new release.

[IMG]https://help.ubuntu.com/community/JauntyUpgrades?action=AttachFile&do=get&target=um2.jpg[/IMG]

Click Upgrade and just follow the instructions

[IMG]https://help.ubuntu.com/community/JauntyUpgrades?action=AttachFile&do=get&target=um3.jpg[/IMG]

It's going to take awhile so sit back and relax! Cheers.

---

### Post by Gins on 2009-05-22
Thanks Wiebelhaus for the reply.

Have you done this upgrade?
[B]
If so, are you pleased with the latest version?[/B]

---

### Post by snowpine on 2009-05-22
> **Gins said:**
> 

[I]I'll give you a good example.

I have upgraded My Mandriva Linux to the latest Mandriva 2009 Spring version. I did this almost 2 weeks ago.
It is more stable than the previous version. The previous version hanged very often and it drove me crazy. Probably they fixed a few bugs in the latest version.[/I]


Mandriva is not Ubuntu.
Ubuntu 8.04 is the Long Term Support release and will be supported through April 2011. This support includes bug fixes and security patches.
Other Ubuntu releases are only supported 18 months.
I have no idea whether or not Mandriva follows this release cycle, but it is probably not a good comparison.

---

### Post by Gins on 2009-05-22
Yes, Snowpine it is correct to say Ubuntu is not Mandriva.

I used Mandriva in the past. So I like it. I run it too from time to time.

.....................................................................................................................................

Wiebelhaus

I took the risk of upgrading just now.
I just followed your instructions.
I mean the following:

Start System>Administration>Update Manager 

It worked fine. It was very quick.
[B]How do I find out whether I have the latest version of Ubuntu?
[/B]

[COLOR="Red"]None of the following commands don't give me a clue to as to the version number.[/COLOR]
......................................................................................................................
ni@ni-desktop:~$ uname --version

uname (GNU coreutils) 6.10

Copyright (C) 2008 Free Software Foundation, Inc.

License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software: you are free to change and redistribute it.

There is NO WARRANTY, to the extent permitted by law.



Written by David MacKenzie.

ni@ni-desktop:~$ 


.....................................................................................................................

ni@ni-desktop:~$ uname -o

GNU/Linux

ni@ni-desktop:~$ 



........................................................................................................................

ni@ni-desktop:~$ uname -m

i686

ni@ni-desktop:~$ 



.........................................................................................................................

ni@n-desktop:~$ uname -a

Linux ni-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

ni@ni-desktop:~$

---

### Post by trench.me on 2009-05-22
cat /etc/lsb-release

Or

Start x and in the Main Menu go System > About Ubuntu.

:)

On the upgrade to Jaunty discussion, I've had polar opposite experiences on two different machines. One upgrade went smoother than any OS upgrade I've *ever* experienced. We're talking since '93, yo. But. On the other machine, the upgrade was complete fail. I've lost all my tty sessions and x refuses to resurrect itself. I spent 8 hours doing CPR on her last night to no avail.

---

### Post by trench.me on 2009-05-22
lsb_release -a 

... also works, if you don't want to use cat.

And here's a thread listing several other ways to version check Ubuntu: [http://ubuntuforums.org/showthread.php?t=263340](http://ubuntuforums.org/showthread.php?t=263340)

---

### Post by hal8000 on 2009-05-22
In my experience many distros break during upgrading; the ONLY exception is Debian (on which ubuntu is based).  Sometimes its nothing more than updating a few files, at other times it can lead to a total system failure and having to reboot.

For this reason I always create a couple of spare partitions and install a new Ubuntu to the new partitions; this way I can test the new version without breaking anything.
Hope that helps

---

### Post by Gins on 2009-05-22
[COLOR="Red"]It is strange!
Didn't it upgrade[/COLOR]?

.........................................

ni@ni-desktop:/etc$ cat lsb-release 

DISTRIB_ID=Ubuntu

DISTRIB_RELEASE=8.04

DISTRIB_CODENAME=hardy

DISTRIB_DESCRIPTION="Ubuntu 8.04.2"

ni@ni-desktop:/etc$ 

........................................

Help version is 2.22.1

---

### Post by Gins on 2009-05-22
[COLOR="Red"]
It is strange. I think it didn't upgrade at all. Just upgraded a few files or rather programs.
What do you all think?[/COLOR]
.............................................................................
ni@ni-desktop:/etc$ cat issue
Ubuntu 8.04.2 \n \l

ni@ni-desktop:/etc$

---

### Post by trench.me on 2009-05-22
It might seem redundant but try following this guide:

[http://www.ubuntugeek.com/how-to-upgrade-ubuntu-810-intrepid-to-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-upgrade-ubuntu-810-intrepid-to-ubuntu-904-jaunty.html)

And something I forgot to add in my earlier comment: the upgrade to Jaunty is definitely worth it. I love everything about it. The only reason I had problems with the second upgrade is because of an old Voodoo card. The old voodoo cards always make for a much more difficult install/upgrade in my experience.

---

