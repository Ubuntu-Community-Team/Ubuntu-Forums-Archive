---
title: "RS6000 Install"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by OldManRiver on 2009-04-23
All,

I got 3 ea. RS6000 7046 B50 Rack mount servers today; price was right.

All were dedicated appliace boxes so none of the boxes had video cards and even install of U-Server require video, until totally config'd and you can remote in.

Anyway, put in some video cards and can not get any video output.

Wonder if anyone has tackled one of these before and can help?

Thanks!

OMR

---

### Post by OldManRiver on 2009-04-24
All,

After some research found the acceptable VICs for the B50-RS6000 are:
[LIST=1]
[*]IBM POWER GXT130P Graphics Accelerator
[*]HIS ATi Radeon 9250 128MB PCI Video Card
[*]Jaton GeForce MX4000, (128 MB) PCI Video Card
[*]Evga e-GeForce FX 5200 128 MB DDR PCI Graphics Card
[/LIST]

I also found out the boxes I purchased were POS dedicated appliances running Kash-N-Karry POS, so have no idea if the existing SW has the video drivers stripped out, which could also explain why no video.

I found a post at:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=346206](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=346206)

which indicates a serial connect to video may be needed.  If that is the case I need instructions on this, though I know the principle, have not done that is over 20 years, so forgot already.

One of the units has a bad CD, which is SCSI, but so far that is the only component I found to be bad.

Sure can use some help on this.

Thanks!

OMR

---

### Post by OldManRiver on 2009-04-24
All,

Does anyone know anything about this box or is there a better place/forum to post at?

Help!!!

OMR

---

### Post by OldManRiver on 2009-04-25
All,

OK, Guy on IRC at #ubuntu says I need null modem cable to connect via TTY on com1/com2.  Do not have here @ house, but have @ shop, so getting today to see if I can see the box that way.

I understand (my laptop is WinXP) I use TelNet to see the box.

Am I right?

OMR

---

### Post by OldManRiver on 2009-04-25
All,

Trying install of 8.04 on RS6000-B50 2U Rack Mount server.  

This box is hard to find online as there are sooo many models of the RS6000-B50.  The 2U Rack Mount unit is a 7046-B50, but that model also had tower units as well.  The hardware is different for the tower units as they hold more cards and drives.  The 2U Rack Mount unit only holds 2 SCSI drives (mine are 18GB).  It also only hold 2 PCI cards, where the tower holds 8-10.  CD-ROM is SCSI, has one floppy, on board NIC, MAU port, COM1, COM2, some sort of S-Video connector and audio codec jacks.  Looking for rear end photo to show.

Thanks!

OMR

---

### Post by wopeer on 2009-05-05
Hi ,i am not sure if this would be usefull for you: 
i got ubuntu-server 6.06 LTS running on my rs6000 43p-150.
As i know this is the same hardware as the b50 .
ubuntu-server boots from the cd. The installer starts automatically, but you have to use the expert or advanced - installation to be able to select the right kernel ; use the powerpc kernel then installer should work fine. 

I did not get the X window running since my S3 Trio is not well supported . But the radeon should work fine. 
On the other hand you won't need X on a server  ;-)

Hope this helps a little.

Regards 
... Wolfgang

---

### Post by OldManRiver on 2009-05-16
> **wopeer said:**
> Hi ,i am not sure if this would be usefull for you: 
i got ubuntu-server 6.06 LTS running on my rs6000 43p-150.
As i know this is the same hardware as the b50 .
ubuntu-server boots from the cd. The installer starts automatically, but you have to use the expert or advanced - installation to be able to select the right kernel ; use the powerpc kernel then installer should work fine. 

I did not get the X window running since my S3 Trio is not well supported . But the radeon should work fine. 
On the other hand you won't need X on a server  ;-)

Hope this helps a little.

Regards 
... Wolfgang

W,

To the first box I added a Jaton TVGA9685 VIC and added the 512MB of RAM from the 3rd box (one with broken CD), but get video only on COM1, with null modem cable on TTY screen (PUTTY on laptop), calling this my primary box.  I need to know what instruction to run from the command line there to get the Ubuntu CD to kick as it does not appear to do so natively or it would install the video drivers and I would get video from the VIC.

The second box I added a Diamond Stealth 3D 2000 VIC but it only has the 512MB of RAM it came with.  Again COM1 shows the command line, but nothing from VIC when trying to boot from CD.

If you know what command is needed and/or how to get box to install the video drivers, then I can get past my install issues and work from video screen like normal install.

Anyway that is current status on this.

Thanks!

OMR

---

### Post by OldManRiver on 2009-05-16
W,

I get this screen output:
```
     memory      keyboard     network      scsi      speaker
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000                                 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000       STARTING SOFTWARE         RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000         PLEASE WAIT...          RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000                                 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000
RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000 RS/6000


BOOTP: Waiting 60 seconds for Spanning Tree

BOOTP: do-BOOTP-req failed: 0
BOOTP: do-BOOTP-req failed: 1
BOOTP: do-BOOTP-req failed: 2
BOOTP: do-BOOTP-req failed: 3
BOOTP: do-BOOTP-req failed: 4
BOOTP ERROR: BOOTP request failed, ABORT
        !20A80004 !

```

If I insert the software recovery disk, I get past this, but the system never recognizes my Unbuntu CD.  I think it is because the CD in the machine is old one no greater than 4X and Ubuntu CD is written at 8X.  Guess I need to re-burn the CD on slower unit.

What do you think?

OMR

---

### Post by OldManRiver on 2009-05-16
Help Please

---

### Post by OldManRiver on 2009-05-22
All,

Found several resources searching, but this link:

[https://help.ubuntu.com/8.04/installation-guide/powerpc/hardware-supported.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/hardware-supported.html)

Definitely says Ubuntu supports the RS6000 B50, but shows it under "CHRP subarchitecture", which is something to do with the boot files needed for the B50 bios to recognize the CD as bootable.

Does anyone know where the CHRP install distro resides?

Thanks!

OMR

---

### Post by OldManRiver on 2009-05-25
All,

From the docs I gleaned from the net Canonical is responsible for these non-standard distros.  I have, as Ubuntu Partner a resource there, so I sent email to my resource for assistance on this.

Will post what I learn and where I get, once I get a working solution.  Right now, from the HOWTOs, etc designing the follow scripts and interfaces:
[LIST=1]
[*]Web Interface:   (PHP) to call make-distro.sh,
[*]make-distro.sh   to call all the following scripts,
[*]rip-distro.sh:   to rip files from alternative distro.iso,
[*]preseed.sh:      to add need preseeds to distro file dir/list,
[*]custom.sh:       to add CHRP or other custom file to dir/list,
[*]build-distro.sh  to rebuild the distro with new files.
[/LIST]

I am currently designing this by passing parms, but alternative is to create version with distro.cfg config file, so parms are not passed but read from the file.

Anyway this is where I am at in this process.  If anyone has some files along this order that would speed up the process, please contribute.

Cheers!

OMR

---

### Post by OldManRiver on 2009-05-28
All,

Well got a tip to use ISOMASTER, from the guys @ IRC and it appears it will do all the custom building I need to make the CHRP install CD.

Will post when I finish.

OMR

---

### Post by OldManRiver on 2009-06-07
All,

For some reason, unknown to me, isomaster and mkisofs will not install on my U_DT.  I had to copy the alternate CD to my Win machine, use MAGICISO, unpack the distro, then copy the files back to my Ubuntu machine.

Since I already had an AIX CD (with Kash-N-Karry), I also unpacked that distro, so I could run the comparison and see what is needed to make the CHRP distro.

Still working on it, should have it soon.

OMR

---

### Post by OldManRiver on 2009-06-08
All,

The book found at:

[http://books.google.com/books?id=HZ37FT3unW8C&pg=PA15&lpg=PA15&dq=ubuntu+CHRP+install&source=bl&ots=A1fVx37Z_c&sig=x9LE5mfblyZd2ckbGiqoqhsnOGM&hl=en&ei=mcUrSvaXBJWvtgeqjKy5Bg&sa=X&oi=book_result&ct=result&resnum=2#PPA15,M1](http://books.google.com/books?id=HZ37FT3unW8C&pg=PA15&lpg=PA15&dq=ubuntu+CHRP+install&source=bl&ots=A1fVx37Z_c&sig=x9LE5mfblyZd2ckbGiqoqhsnOGM&hl=en&ei=mcUrSvaXBJWvtgeqjKy5Bg&sa=X&oi=book_result&ct=result&resnum=2#PPA15,M1)

gives link to hfs.map as:

[http://people.ubuntulinux.com/~cjwatson/hfs.map](http://people.ubuntulinux.com/~cjwatson/hfs.map)

but link has changed, since printing to:

[http://people.ubuntulinux.org/~cjwatson/hfs.map](http://people.ubuntulinux.org/~cjwatson/hfs.map)

So now have this file needed for this install.

Some help from you gurus would be nice.

Thanks!

OMR

---

### Post by OldManRiver on 2009-06-08
All,

Since not much progress here posted problem at:

[http://www.powerdeveloper.org/forums/viewtopic.php?p=12452#12452](http://www.powerdeveloper.org/forums/viewtopic.php?p=12452#12452)

Response link was:

[http://penguinppc.org/ppc64/power-bootable-iso/](http://penguinppc.org/ppc64/power-bootable-iso/)

Got most of the files built already, per this HOWTO, but since I can not get mkisofs to install, stuck.

Can I get some help on the mkisofs install?

OMR

---

### Post by OldManRiver on 2009-06-09
All

Help Please!

OMR

---

### Post by topcat5 on 2009-06-09
Having worked with RS/6000s for many years I think you are in for a lot of trouble in trying to get this to work.  Even if you manage to get a system to boot it's going to be my guess that you probably won't have drivers for some of the hardware in the server depending upon how it was configured.  If you get the video to work in graphics mode it will be a miracle.   

Your best bet is to get a copy of AIX 5.1 and install that on this machine.  It will boot up with no trouble at all from a disk and once installed will run without problem.  You will also be able to bring it up in graphics mode assuming you have a supported monitor attached.  There should be a linux "xtras" disk with the distribution that should make the system seem more like linux but depending upon what you plan for this machine it should not be necessary.  AIX is an extremely competent Unix.

---

### Post by OldManRiver on 2009-06-10
> **topcat5 said:**
> Having worked with RS/6000s for many years I think you are in for a lot of trouble in trying to get this to work.  Even if you manage to get a system to boot it's going to be my guess that you probably won't have drivers for some of the hardware in the server depending upon how it was configured.  If you get the video to work in graphics mode it will be a miracle.   

Your best bet is to get a copy of AIX 5.1 and install that on this machine.  It will boot up with no trouble at all from a disk and once installed will run without problem.  You will also be able to bring it up in graphics mode assuming you have a supported monitor attached.  There should be a linux "xtras" disk with the distribution that should make the system seem more like linux but depending upon what you plan for this machine it should not be necessary.  AIX is an extremely competent Unix.

TC,

As IBM partner there should be a place to download the AIX 5.1, but I do not know the link.  Can you help?

As far as the custom install is concerned I read all the docs on my B50 and it supports any VIC that will config with VESA drivers, which is what I installed into the machines, at least VESA on Ubuntu drives these.  If there are hardware specific issues about the VICs vs VESA, they are not in the docs, so if you have insight would like it.

One more question, do you know why my AIX screen, on my COM1 TTY, goes blank and does not let me see the command line after full load?  I think it has to do with the Kash-N-Karry, which I think is setting up all login session on NFS for the remote POS terminals, but I can not find anything on this to say so.

Thanks!

OMR

---

### Post by barbaGNU on 2009-06-10
hi, but have you tried other distro that might suppurt your machine?

I can think... CRUX PPC, GentooPPC, YDL or Debian PPC.

bye,

---

### Post by OldManRiver on 2009-06-12
B,

I did try the Debian version, since close to Ubuntu as U is Debian based, but ran into same set of problems, of having to build in my own CHRP and YABOOT, so no advantage.

OMR

---

### Post by barbaGNU on 2009-06-13
debian ppc has a good mailing list, you can ask for support if you really need this one.
btw, the previous submitted howto (from penguinppc.rg) is damned good and does solve your problem.

crux ppc and gentoo ppc are released under gpl then (if you don't want to install these distros on your rs6k) find their sources... study them... go ahead and apply.

but a question.. why do you want ubuntu on this old a low end machine ? i think: too much work for a quite bad result.

---

### Post by OldManRiver on 2009-06-15
All,

Cleared this over the week-end with help from the guys at:

irc.freenode#ubuntu

Turns out my status file at:

/var/lib/dpkg/status

was corrupted.  When I got it cleaned up the:

apt-get upgrade and the app installs ran, so have both ISOMATER and genisofs (replaces mkisofs on U) out there now.

Thanks!

**Note:**
My BP contact at Canonical opened a ticket with IBM on this distro, so starting to get some feedback from them and should help getting this build done.

Thanks again!

OMR

---

### Post by barbaGNU on 2009-06-15
nice, good luck!!

btw, did you already give a try with some other distros to benchmark performance of your chrp beast?

---

### Post by topcat5 on 2009-06-15
> **OldManRiver said:**
> TC,

......

One more question, do you know why my AIX screen, on my COM1 TTY, goes blank and does not let me see the command line after full load? .....

OMR

My memory is a bit shaky on this but here is what I remember.  If there is a graphics card in the machine and AIX has been configured to use it (default if installed with it) then when AIX takes over control from the service processor, the console defaults to the graphics display. It will not try to use the TTY which is why it essentially goes blank.

---

### Post by OldManRiver on 2009-06-16
> **topcat5 said:**
> My memory is a bit shaky on this but here is what I remember.  If there is a graphics card in the machine and AIX has been configured to use it (default if installed with it) then when AIX takes over control from the service processor, the console defaults to the graphics display. It will not try to use the TTY which is why it essentially goes blank.

TC,

No I added the VIC to try to get installer to load VESA driver so could get rid of the TTY cable.

I could do more, on my B50 box, but the TTY is set to go blank after install, so need the IBM folks monitoring this to chime is as to why and how to fix this.

Right now have the directories created per the HOWTO at:

[http://penguinppc.org/ppc64/power-bootable-iso/](http://penguinppc.org/ppc64/power-bootable-iso/)

ISOMASTER is showing iso size of 1.4GB so have following q's:
[LIST=1]
[*]What is deletable from Ubuntu to bring size right?
[*]I have latest Yaboot 1.3.14.  Is this correct or is older version needed?
[*]Per HOWTO, assume the Ubuntu files go into the /ppc/chrp/vmlinux directory.  Is this right?
[*]I built the yaboot.conf and bootinfo.txt files, per the HOWTO. What is needed for the ramdisk.image.gz file?
[*]Where does the hfs.map file go?
[*]The HOWTO at:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
says build the preseed files.  I assume their information is not right.  What is needed in my preseed files?
[/LIST]

Ready to run the build when I have the right stuff.

Thanks!

OMR

---

### Post by barbaGNU on 2009-06-16
lol, just now i realize your first and big problem is you are unable to understand and master your ubuntu...

just a trivial question... but do you already have a working bootkernel for ibm chrp machine?

---

### Post by OldManRiver on 2009-06-16
> **barbaGNU said:**
> just a trivial question... but do you already have a working bootkernel for ibm chrp machine?

B,

Well, for your LOL, I have several U-boxes and have never had the "status" file go corrupt on me before.  I knew I could not install anything, so when I did not get a response here nor on the thread I opened here just for the install problem, it was time for serious geek power from the IRC crowd.

Anyway now past that so to answer your trivial Q, well I have bootable AIX 4.3.1 with Kash-N-Karry, but it is what keep me locked out on the COM1 TTY, so no; do not really have a bootable version for the CHRP, that is what I'm working on here.

Per my last post you can see I have some of the files already built, and will start posting them.  Just really need the gurus to let me know what I still need to complete this.

I can get around, code in bash, etc and do most things on my U boxes, but by no means think I've arrived at guru status yet, but working on it.  LOL!

Thanks!

OMR

---

### Post by barbaGNU on 2009-06-17
well, now that your U is fixed you did 50%.
You can give a try booting your machine with another distro (e.g. crux ppc 2.5 32bit should have a chrp bootkernel) then go ahead and apply the other 50%.

i'm a n00b too, and my past question was trivial but not the related answer...

---

### Post by barbaGNU on 2009-06-17
> **OldManRiver said:**
> 
**Note:**
My BP contact at Canonical opened a ticket with IBM on this distro, so starting to get some feedback from them and should help getting this build done.


mmh, i don't think ibm people 'll help for an obsolete machine.

---

### Post by OldManRiver on 2009-06-17
B,

Well IBM will help because the distro will work on all IBM P-Series machines.  When I finish P-Series will purchase an X-Series and make distro for that as well.

The main things, that IBM geeks need to contribute is **HOWTO** install with existing AIX so the **existing AIX is not bothered or overwritten** and with **"Dual Boot"** so both AIX and Ubuntu come up and user can switch between OSs with the CTL+ALT+Fx combo or in X-Win.

Right now if I build the distro with existing files the option for install/format entire disk will still be present.  Do not want that option available to the installer, unless no existing install of AIX exists.  Will have to write a bash or C script to include with install to search for existing AIX install.

Then defining TTY sessions, some to AIX and some to Ubuntu will be challenging. Furthermore most AIX boxes I've dealt with were servers no never had an X-Win interface (IBM guys chime in if you do have X-Win) so configing the X-Win, in Ubuntu desktop with 4 or more sessions, where at least 2 go to AIX, will be a fun chore.  Furthermore X-Win should have 2nd Terminal Session defined that goes to AIX command line not Ubuntu command line.

Yes I intend to add DT version to existing AIX servers as admin from the X-Win interface is/will be easier, especially for newer/younger up-and-coming admins who grew up only with GUI interfaces.

Networking will need special attention as both OSs need to share the existing definitions.  Scenarios for 1.) AIX installed first then Ubuntu, 2.) Ubuntu installed first then AIX, and 3.) Both co-installed from DVD distro with both, need to be defined and exist.

I may be over complicating this, but also using this thread to communicate to all, so they can get my concept.  Realized I did not give the full intent of my project until now.

Thanks!

OMR

---

### Post by barbaGNU on 2009-07-08
well, what's happened? Did you received direct support from IBM ??

---

### Post by OldManRiver on 2009-08-11
B,

One IBM guru says they already have this so I asked for URL, but he doesn't have or know it.  DUH!

OMR

---

### Post by OldManRiver on 2009-08-22
All,

Someone says there are CHRP copies of Debian, so searching to see what I find and learn.

OMR

---

### Post by henriquemeira on 2009-10-17
I got it!!!

I have an old IBM Server RS/6000 F50 7025.

I found this boot CD:

[http://ftp.uni-augsburg.de/pub/tuxppc/debian-bootcds/ppc64/Debian-boot-64.iso](http://ftp.uni-augsburg.de/pub/tuxppc/debian-bootcds/ppc64/Debian-boot-64.iso)

It's work.

---

### Post by henriquemeira on 2009-10-17
Ok, finally I got it works fine!!! :D

I build a little tutorial. Read here: [http://ubuntuforums.org/showthread.php?p=8121431](http://ubuntuforums.org/showthread.php?p=8121431)

see you.

henrique.

---

### Post by barbaGNU on 2009-10-19
thanks for update!

---

### Post by OldManRiver on 2011-05-22
henriquemeira,

I have the additional problem that the B50's I'm working with did not have a video card but using Null Modem Terminal cable on COM 1.

Therefore since I added the VIC and boot, my CD can not be interactive, but must find and load the video card first before any prompts are issued.

Any suggestions on that?

OMR

---

### Post by OldManRiver on 2011-06-04
All,

I finally found the resource I think my IBM person was referring to at:

[http://www14.software.ibm.com/webapp/set2/sas/f/lopdiags/home.html](http://www14.software.ibm.com/webapp/set2/sas/f/lopdiags/home.html)

and

[http://www14.software.ibm.com/webapp/set2/sas/f/lopdiags/installtools/home.html](http://www14.software.ibm.com/webapp/set2/sas/f/lopdiags/installtools/home.html)

Working on finishing out this now, to see if I get build for i386/i586 as well as 64.

Inspecting all the elements now.

Thanks!

OMR

---

### Post by barbaGNU on 2011-07-04
still interested.
Please, provide updates if available.

thanks,

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #27 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

