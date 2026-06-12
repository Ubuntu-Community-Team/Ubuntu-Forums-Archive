---
title: "Ubuntu 6.10+ on Sony VAIO TX"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by golem3 on 2007-03-13
I am interested in getting a new Sony VAIO TX ultraportable notebook, but want to know how Ubuntu runs on it. 

I have done quite a bit of research on this matter before bothering you all with another thread to read. There isn't much info out there on the linux pages...or on that one site that collects a lot of Linux experiences on notebooks.

There is one thread
[http://ubuntuforums.org/showthread.php?t=87619]("http://ubuntuforums.org/showthread.php?t=87619")

But it doesn't answer questions for 1) its a guide for Breezy 2) I want info on the new TX line 3) media keys. I want to know if Edgy or Feisty will allow media keys to work out, even if it needs some work.

thanks, 
gautam

---

### Post by Big_Croc7 on 2007-03-14
I can't say anything about the TX I'm afraid, but I have a vaio BX, which I've tried to install both dapper and edgy (ubuntu and kubuntu) on, and I've given up as nothing seems to work.  It's currently running windows XP still, so I don't know how comparable this is to Ubuntu (if you can install it), but I have to say that the whole thing is generally unreliable.  Sony have packed it full of features but don't seem to have tested it properly.  I'd advise against buying a vaio :(

List of issues:
- the fingerprint scanner is a useless gimmick that dosen't work well, and its use often crashes the system
- the bios password has a '3 strikes' policy, after which it needs an 'unlock code' which sony charge for (but this can be bypassed - I did :-S)
- random crashes on booting/resuming
- battery is already starting to lose its charge capacity, this is after ~6 months of light use

Sorry - that's probably not what you wanted to hear!!!

---

### Post by golem3 on 2007-03-15
Yikes, well thanks for the help. :popcorn:

---

### Post by chartman on 2007-03-18
Hi. I bought a VAIO TX5XN last week. No serious issues so far. I installed beryl and it works flawlessly. bluetooth mouse, microphone (for Skype), wireless card.. all OK!

A few minor issues (minor for me at least):
- When installing, I accidentially wiped the VISTA installation.. maybe I didn't use the partition resizer correctly. (Be more careful than me an create a VISTA recovery CD first.
-  The brightness adjustment of the monitor is not "stored"... so each time the system comes up it is in 100% brightness.
- The volume level controls don't work
- Haven't tried the fingerprint device

---

### Post by null84 on 2007-03-22
i bought txn15. i am going to follow the link below and try Mandriva.

[http://www.markadavis.org/vgntxn15.html](http://www.markadavis.org/vgntxn15.html)

---

### Post by Laterix on 2007-04-24
I have TX3 and I wrote [something]("http://www.taimila.com/vaio.php") about it and linux.

In feisty everything works except memory card readrs and volume buttons.

---

### Post by GrumpyBob on 2007-05-09
> **chartman said:**
> Hi. I bought a VAIO TX5XN last week. No serious issues so far. I installed beryl and it works flawlessly. bluetooth mouse, microphone (for Skype), wireless card.. all OK!

A few minor issues (minor for me at least):
- When installing, I accidentially wiped the VISTA installation.. maybe I didn't use the partition resizer correctly. (Be more careful than me an create a VISTA recovery CD first.
-  The brightness adjustment of the monitor is not "stored"... so each time the system comes up it is in 100% brightness.
- The volume level controls don't work
- Haven't tried the fingerprint device

I took delivery of a Vaio TX5XN yesterday.
Vista took about 30 minutes to set itself up.  I then tried to make the Apoplication and System recovery DVDs - the first one was a coaster, and I was told to reboot.  The second attempt worked, but I got told to reboot.  The final DVD also worked, and I was to follow up with yet another reboot!  That was basically my exposure to Vista (which seemed notable by the frequency of messages getting popped up onscreen!).  

Ubuntu 7.04 installation went flawlessly, I have kept the Vista as adual boot option - there seem to be no problems after it ran a check disk.

Of the features of the TX5N, 

I have not got the SD card reader to work, so any hints would be welcome.  This would be good to get working.

Power mangement seems good, though the automatic screen dimming on battery doesn't work - is there a work-around?

I have not investigated the fingerprint reader.

The front volume control buttons don't work, but mute does.  I'm happy using Gnome software tools for that.  

I haven't investigated multimedia yet

Both Compiz and Beryl worked straight after installation.

Wireless and wired networking worked as soon as I tried to set them up, no problems.  Vpnc from the repositories refused to connect me, so I installed an older version, which worked fine (this is also the case with my IBM R52 laptop).  I haven't tried bluetooth yet.

Robert

Edit:  I notice that there is a fat book with the EULA for InstantON video playback software.  What's notable is that all the specified components are GPL or lesser GPL or library GPL, except linpng and lijpeg.  Yet the EULA bangs on about not copying, reverse engineering, installing on more than 1 PC, etc.  On a quick skim there's no mention of any other licence, or what component limits one's GPL rights.  Nor do I see the source code available.  What gives?

Edit 2:  I found the sources at the Intervideo website

Edit 3:  I now have the SD card reader working, by following [this How-To]("http://ubuntuforums.org/showthread.php?t=420721&highlight=Sony+SD+card+reader").

---

### Post by eugencc on 2007-06-23
Hello all,

I need your HELP.

I bought a Vaio VGN-Tx5XN notebook, I forgot to make the recovery disks and now I cannot have posibility to boot the system... I tried to repartition the HDD and I don't know... The result is that I don't have possibility to reboot the notebook.

What are the possibilities to recover the Vista OS without the recovery disks?

Many thanks in advance.

Eugene

---

### Post by Big_Croc7 on 2007-06-25
Could you give a bit more detail about what you've done? (and what you'd like to do)

Can you boot from the liveCD and run the following command
```
sudo fdisk -l
```
and paste the output here?

---

### Post by eugencc on 2007-06-25
I forgot to create the Recovery Disks for my TX5XN notebook. After that Vista OS crashed in the middle of repartition procees with Paragon Repartition. When I restarted the system I receive a error message an the notebook requested a Recovery Disks. 

Because I don't have the Recovery Disks I installed now the Vista from other Vista DVD. 

I added the drivers and utilities, but I not have the Recovery Utility on my computer. I found the hidden partition but I don't know what is the possibility to start Recovery process to rebuilt the initial Sony status on my notebook.

I tried to use F10when I booting the system, as other Vaio systems, but without succes.

What is the way? If I will bought the Sony Recovery Disks will works OK?

Please help me with correct way.

---

