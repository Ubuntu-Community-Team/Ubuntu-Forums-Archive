---
title: "Problem At Install;debootstrap Error"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by BadCluster on 2005-01-07
i have a celeron pc at 1.8GHZ with 384MB RAM and 4.3GB hard disk

i put the cd i made from the iso file i downloaded([http://source.rfc822.org/pub/mirror/releases.ubuntu.com/4.10/warty-release-install-i386.iso](http://source.rfc822.org/pub/mirror/releases.ubuntu.com/4.10/warty-release-install-i386.iso))

everything went well until i got the following message...

[B]"Installs the base system      
[COLOR=DarkRed]Debootstrap Error [/COLOR]
 Couldnt retrieve gettext-base.This may be due to a network problem or a bad cd, depending on your installation method  If you are installing from cd-r or cd-rw , burning the cd at a lower speed may help"[/B] 


well i burned another cd and then burned a cd-rw but i still get the same message...
can u help me???

---

### Post by tiiim on 2005-01-07
[QUOTE=BadCluster]i have a celeron pc at 1.8GHZ with 384MB RAM and 4.3GB hard disk

i put the cd i made from the iso file i downloaded([http://source.rfc822.org/pub/mirror/releases.ubuntu.com/4.10/warty-release-install-i386.iso](http://source.rfc822.org/pub/mirror/releases.ubuntu.com/4.10/warty-release-install-i386.iso))

everything went well until i got the following message...

[B]"Installs the base system      
[COLOR=DarkRed]Debootstrap Error [/COLOR]
 Couldnt retrieve gettext-base.This may be due to a network problem or a bad cd, depending on your installation method  If you are installing from cd-r or cd-rw , burning the cd at a lower speed may help"[/B] 


well i burned another cd and then burned a cd-rw but i still get the same message...
can u help me???[/QUOTE]
 did you do check sum?

also try and burn it slower and see if that works...

---

### Post by BadCluster on 2005-01-07
i ll try once more but in case it doesnt work also can u gimme a link to download a new iso file???
i think may i didnt download the correct one...

---

### Post by tiiim on 2005-01-07
[QUOTE=BadCluster]i ll try once more but in case it doesnt work also can u gimme a link to download a new iso file???
i think may i didnt download the correct one...[/QUOTE]
 try

[http://releases.ubuntu.com/warty/warty-release-install-i386.iso](http://releases.ubuntu.com/warty/warty-release-install-i386.iso)

that directly from Ubuntu so see if that works.

---

### Post by BadCluster on 2005-01-07
well i burned the cd for the 5th time but still i get the same message///
now i am downloading from the link u gave me...
hope it works!

---

### Post by tiiim on 2005-01-08
[QUOTE=BadCluster]well i burned the cd for the 5th time but still i get the same message///
now i am downloading from the link u gave me...
hope it works![/QUOTE]
 let us know...

it could be a (small) chance that maybe the cds your using were too slow for your burning speed? that issue almost gone today but it could be...

but how did your new install go?

---

### Post by Rambo on 2005-01-19
Same problem with debootstrap here. my cd's are OK, but the file could of course be damaged. Did it work with a new download for you?

---

### Post by TryMe on 2005-01-30
I have an AMD 750, 128 mb RAM test system.

Got error
"Base System Installation Error
The Debootstrap program exited with error (return value 1)"

Md5 sum checks out on .iso
burned  .iso twice - different speeds
ran the disk integrity utility on disk . 
./pool/main/p/pciutils_2.1.11-11_i386.deb 
faild check

Why?
I burn .iso's all the time to try out different distros. Never seen this or anything else like it before. Is there something new about this .iso or is this just dumb luck?

---

### Post by dikki on 2005-01-30
I had a problem, like, but not especially this problem too. I downloaded the .iso again, and burned the -RW with slower speed, and it worked fine.
My Fedora Core 3 disks didn't worked when I tried to use them a while ago, so I checked the surfaces of the -RW's and I found that they are scratchy. So, I only can say check your installation media, and try again..

---

### Post by TryMe on 2005-01-30
I burned the .iso again same failure. So I tried it on another system and it installed perfectly. Maybe the AMD has a bad CD-ROM drive. I am going to take a look at the logs and see what I can see.

---

### Post by rudedoc on 2005-01-30
I too am having this probelm.... I've burned the cd 3 times (32x, 16x, and 8x) on 48x rated media.  I used a different source for the iso as well (using the above link).  I really don't know why this is fouling up....

Comp is: Pentium MMX 200 mHz 96megs Ram.  (I've installed debian woody, and mepis on it before.)

So does anyone know what this error message is referring to and how to fix it?
I would appreciate any help.  Thank you.
 :confused:

---

### Post by veritas366 on 2005-02-11
this is looking bad.  First off, when several people have the exact same missing file (I too have the same debootstrap error) this makes the odds of a bad disk write quite small, I would think.

Secondly, I burned my disk at 1X.  I couldn't go any slower without spinning the cd writer by hand!  

Has there been an small update to the install disk in the last week or so?

---

### Post by rolo on 2005-02-12
[QUOTE=][/QUOTE]
 I have the same problem on a Presario 1525us, 2.4Gz,256 Ram, HD 40 GB. First, I try burning the iso at 8X, then, at 4X and I received the same messagge mentioned in this thread.

---

### Post by dogs on 2005-02-12
I have the same problem.  Downloaded the iso image yesterday and have tried two CDs with same result. 

I have previously installed Red Hat on this drive without a problem.

After posting this message I tried once last time and the installation completed.  I didn't do anything different and have no idea why it finally worked.

---

### Post by Felipejane on 2005-02-12
[QUOTE=dogs]I have the same problem.  Downloaded the iso image yesterday and have tried two CDs with same result. 

I have previously installed Red Hat on this drive without a problem.

After posting this message I tried once last time and the installation completed.  I didn't do anything different and have no idea why it finally worked.[/QUOTE]
 One more person with the same problems, only my install dies when it can't find BSDUTILS. I've tried installing from the same CD twice; the last post makes me think if I just keep trying eventually I'll get there. That doesn't make much sense to me, but I'll try.

I also saw the message about recording at a slower speed, but I'm having trouble changing the recording speed in Roxio.

An hour later: I burned a new copy, and while I couldn't choose a slower burning speed than 40X, I noted during the process that it ran at several different speeds, all well below 40X. The result, however, was the same: debootstrap error because the install failed to load BSDUTILS. 

Still scratching my head...

Another hour later: the MD5SUMS for the whole ISO file that I downloaded match the checksum that is listed on the UBUNTU download page. Not only that, when I look at the checksums file that's on the CD, I find that BSDUTILS is listed there. So the file IS in the image. Right?

Four or five attempts from two apparently identical CDs, and I still only have a newly clean second hard drive. I hadn't expected to be thankful for Windows, but right now I am. 

Still hoping to succeed with Ubuntu...

---

### Post by Jelte on 2005-02-14
I have the same problem, but for me it fails on 'telnet'.  I dont think its to do with the actual CD's, but more the target.

I have used this very same install CD before, and it worked fine. Then I installed Ubuntu on the first partition of my only HD. Now, however, I'm installing it on the second partition, since I've put WinXP on the first to dual boot.

Looking at the output on console 3, i have the following:
  No matching physical volumes found
  No volume groups found
  Reading all physical volumes.  This may take a while...
cp: Write Error: Input/output error
cp: Write Error: Input/output error
cp: Write Error: Input/output error
cp: Write Error: Input/output error
cp: Write Error: Input/output error

So it looks like more a problem with the target than with the source (ie CD)

---

### Post by Jelte on 2005-02-14
Maybe getting closer....

I tried installing ubuntu again, but this time just using the second partition. Before I was trying to install ubuntu on the second partition with the /home on a logical partition.

Trying to install everything on hda2 got me a few packages further. Now it falls over on 'vim'.

---

### Post by Jelte on 2005-02-14
Solved it!!!  \\:D/ 


I found the problem, it was to do with the partition, not the cd.

When selecting the partition(s) to use in the partition table, make sure that 'Usage method' is set to 'format the partition'.

Mine was already formatted, but it seems ubuntu installer wants to format it for itself. Anyway, once that was done the install worked fine.

Hope it solves the other problems mentioned here.

Ubuntu might want to change the text in the error dialog, that currently suggest the CD is at fault... another suggestion to add is to use the format option in the partition section of the install...

---

### Post by Felipejane on 2005-02-14
So, Jelte, are you happy with Ubuntu, now that you've successfully installed it? I.e., should I keep struggling with it? Is it worth the effort? How does it compare with other distros you've looked at?

---

