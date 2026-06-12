---
title: "nec cd/dvd + burner not working with feisty fawn"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by ravanwin on 2007-05-27
Hello, 

I apologize if my ignorance is too vast for any help BUT here is what's happening to the best of my understanding:

I had ubuntu 6.10 Edgy Eft and upgraded a day ago to Feitsty Fawn, I think. 

Today, I tried to burn some cds and dvds and neither worked. The burner was recognized and windows did pop up asking me what i wanted to do (i.e. burn data cd) but when I tried to write to disk a window appeared asking me to insert a blank disk with at least 345 bytes free. It said "the following disk formates are supported:" but offered no options. Suffice to say, I tried a variety of cds and dvds and none worked. 

My hardware is a NEC r/rw burner but Feisty Fawn seems to recognize it as dvd rw nd 3540A whereas  it was previously recognized as a NEC drive. I am not sure of any more details of the nec drive other than I know it was bought about 2 years ago and is an external drive. 

If you have any advice or assistance, that would be great. Hope I wrote this approprately. 
All the best,
Ryan

---

### Post by Gremlinzzz on 2007-05-27
I always use K3b seems to work best .sudo aptitude install k3b libk3b2-mp3

---

### Post by chombee on 2007-05-28
**Gremlinzzz**, thanks for helping out but ravanwin here is a total newbie. He isn't going to know that ```
sudo aptitude install k3b libk3b2-mp3
``` is a command to be typed in the terminal, much less what it does.

**Ravanwin**: Gremlinzzz is telling you to try using a different application to burn your CDs, one that is not installed on Ubuntu by default, so you first have to install it. The application is called k3b, and to install it you open a terminal by going to Applications->Accessories->Terminal then in the terminal type the above command then press return.

OR you could do exactly the same thing graphically by going to System->Administration->Synaptic Package Manager. Search for k3b, tick it, then search for libk3b2-mp3, tick it, then press Apply. To 'tick' a package in Synaptic you have to right-click on it then choose Mark for Installation.

libk3b2-mp3 sounds like an additional package you need to get the CD burning application k3b to work with mp3 files. Otherwise you could just install k3b more easily using Applications->Add/Remove.

**Ravanwin**: What application are you currently using to try to burn CD and DVDS? Are you trying to burn data CDs or music CDs?

**Everyone**: Ravanwin's real problem seems to be that his CD/DVD burner was working fine in Edgy, but on upgrading to Feisty it got renamed from a NEC R/W to a DVD RW ND 3540A and how he can't burn. This is beyond me, does anyone have any suggestions?

**Ravanwin**: Apart from that, how has the upgrade been for you?

Also, can you post some screenshots of the error you are getting? The Print Screen key on your keyboard should take a screenshot, otherwise you can go to Applications->Accessories->Take Screenshot. You can then upload the image to [http://imageshack.us/](http://imageshack.us/) and link to it on this thread.

---

### Post by maxxum on 2007-05-28
HI Guys,
Sorry to jump in, but I thought its better not to make yet another new thread for a similar problem. I followed your instructions in this thread and installed k3b. It recognizes my NEC DVD RW drie but when I tried to burn data to it (I chose 1X speed), it gave me an error. 

Unable to read disc input out information: Input/Output error.
Fatal error at startup: Input/output error.

The log is:
```

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
_NEC DVD_RW ND-3500AG 2.16 (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [TAO; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 2094757

Used versions
-----------------------
growisofs: 5.21

growisofs
-----------------------
:-( unable to READ DISC INFORMATION: Input/output error

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hda=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2094757 -dvd-compat -speed=1 

mkisofs
-----------------------
2094757
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.02% done, estimate finish Mon May 28 11:12:39 2007
  0.05% done, estimate finish Mon May 28 11:12:39 2007
  0.07% done, estimate finish Mon May 28 11:12:39 2007
  0.10% done, estimate finish Mon May 28 11:12:39 2007

mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-atul/k3bTOXIda.tmp -rational-rock -hide-list /tmp/kde-blah/k3bSmCDFa.tmp -joliet -hide-joliet-list /tmp/kde-blah/k3bjkwBYa.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-blah/k3bOJLzib.tmp 

```

---

### Post by ravanwin on 2007-05-28
Hi there. 

Grimlinzzz, et al. thanks for the responses. 

Chombee is correct; I'm a complete newbie to Ubuntu, I am using Ubuntu 7.04 Feisty Fawn and the GNOME desktop and I have little understanding about what I am actually doing. I need real basic language to help solve these glitches.

I am attaching screen shots so you all can see what I'm getting. I'm not sure what program I am using to burn DATA cds... it seems to be the basic one: "cd/dvd creator". I've not tried to burn audio cds yet but, at the moment, i am most concerned, that my drive is being recognized improperly and, to that end, I am reluctant to add new burning software but maybe that is a newbie parinoia.

here are the screen shots. any advice, translated for a dummy, would be most helpfull. 

thanks to everyone for helping with this.

All the best,
R

---

### Post by chombee on 2007-05-29
**maxxum**: do you get the same problem as ravanwin that your drive is detected as the wrong type? Do you get the same error as ravanwin when you try to burn a data disc using the built-in CD burner?

Anyone got any pointers for ravanwin? What information he could provide that might be a clue? Or what might fix it? Uninstall then reinstall hal maybe? (don´t try this yet ravanwin).

---

### Post by maxxum on 2007-05-29
chombee: No, dapper does not even mount anything on my dvd burner, even blank discs. I cannot use edgy or fiesty on this system, fiesty also has a problem with this PATA dvd-rw drive. In Nautilus, when I click on CD-ROM 1 in the left shortcuts, it says it was unable to mount. Similarly, k3b, while it shows the name of the burner as NEC (which means it recognizes it is there) but it cannot mount a blank DVD to write on it (i guess?). The same dvd drive is recognized and worked well while running the live CD and it was in fact used to install the OS.

---

### Post by ravanwin on 2007-05-30
very interesting development here folks:::

despite the fact that ubuntu is incorrectly recognizing my cd/dvd burner, it seems to actually be workiing for some reason? 

perhaps there was something in a recent update that I downloaded today? 

Anyway, I've only tested a cd at this moment but will attempt a dvd in a few moments. I will report back if anything is still buggy but, at the moment, it's "all good."

rv

---

### Post by merlinus on 2007-05-30
The kernel upgrade means that my Plextor burner is now recognized and mounts when I install a CD-R, but it will not read already-burned cds.

-merlin

---

### Post by ravanwin on 2007-06-15
this has quit working for some reason. same problems. 

i can read and extract cds but not burn data onto dvd / cd.

some help, in very simple terms, if poss.?
thanks,
r

---

### Post by ravanwin on 2007-06-16
here are screen shots as requested. any thing else i can do to help slove this annoying problem?
r

---

### Post by Unterseeboot_234 on 2007-06-21
I run Dapper. I have Fiesty but I can build software in Dapper. I was trying to burn to an external USB DVD burner. That does work with the default installed CD/DVD burner that comes with Ubuntu. However, I couldn't get the internal CD/DVD reader to read a DVD and burn that DVD to the external burner. All I could do with the external was put in a blank DVD, ubuntu sees that and asks me if I want to back up some data.

I downloaded GnomeBaker (Automatix2 has a 64-bit vers, "ready to go"). GnomeBaker uses the libs from CD/DVD burner. If the CD/DVD works, then GnomeBaker shouldn't have a problem.  The other thing is GnomeBaker has a message output console. Very useful. The message showed me GnomeBaker did not have permissions for the internal Hard Drive. I've run into this before trying to hook up a DV video camera.

Whenever we build software, it makes a big difference in Linux whether we are making the software as root or as user. Sometimes we have to be in root just to build. The build works but the build wasn't smart enough to change permissions for some of the files inside Linux. The short answer was: I can sudo GnomeBaker from a Terminal -- which makes me a root user -- and the software recognizes all of my devices.

It will take more study, but when I get the time I will research what text file inside of Linux I need to change dev names and/or permissions for the dev file. As I understand it, the defaults text file that GnomeBaker references needs to have permissions allocating group and user (me) as part of that group.

---

### Post by sorenotes on 2007-07-01
Hi everyone,

Sorry but I'm no help to you either ravanwin, but I've been having the same prioblem with my ND 3540A. I can rip music from cd's I can play dvd's but I can't burn either. it's getting me down big time!!!!

I try to burn a film to a dvd cd and it seems to be working okay until the very last minuet when it says an error has occured and it was unsucessful. I have tried burning it through windows media and it just ejects the cd and asks for a cd to be placed in to the drive, which I do and it takes a few seconds and does the same again.

Any help please I'm desperate and by the way I'm not very computer literate so easy speak for me too please!!

Regards

mick

---

