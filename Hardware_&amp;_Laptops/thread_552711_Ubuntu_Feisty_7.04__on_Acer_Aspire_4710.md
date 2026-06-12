---
title: "Ubuntu Feisty 7.04  on Acer Aspire 4710"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by Agent_Bain on 2007-09-16
Hello! 

Between Windows Vista frustrations and Office XP demanding that I buy a second copy if I want to run it on my laptop as well as my desktop I've made the long overdue jump to Ubuntu Linux. I was amazed by the installer, running it of a LiveCD is a really good idea. Nearly everything worked straight off the install! Sadly I have a few problems and. It would be great If you guys could help me get this working easily and quickly.

I'm sure your going to need more information than I've provided here, if you could please tell me the magic command line incantations I need to invoke to get the information. I'm browsing around learning things at the moment but I think it will be a while before I'm up to par. I've spent some time looking round the forums for answers, but I've messed things up enough that I've had to completely reinstall Ubuntu twice now ... you know what they say about a little knowledge being a dangerous thing :)

**Broken things in order of Priority:**

Sound Card:
The headphone and microphone lines in the front of the computer don't work. I followed this guide to get them working 
[http://ubuntuforums.org/showthread.p...ht=aspire+4710](http://ubuntuforums.org/showthread.p...ht=aspire+4710)

Web cam:
For webcam use Ekiga; in video device chose V4L2 as video device. It works fine.

**Possibly working/broken things: ** (I don't have any hardware to test them yet)

Bluetooth
USB Card Reader

I'm very happy to keep updating this post so other users can use it as a guide for installing ubuntu on this laptop.

Thanks everyone!

Mike

---

### Post by Agent_Bain on 2007-09-16
Reserved for updates.

---

### Post by crandude on 2007-09-17
I am having the same problems too... mine is acer 4710 too...runnin edgy.

---

### Post by bitra on 2007-12-13
I'm using Acer 4710 too with Gutsy Gibbon in it.
The problems are similar:
[LIST=1]
[*]External speaker doesn't work. Instead, sounds came out from laptop speaker.
[*]Built-in webcam doesn't work too.
[*]But I think the laptop special hotkeys is working (like the internet and wireless button)
[/LIST]

I'm still browsing, trying to find the way how to fix them... :(

---

### Post by suselover on 2007-12-14
For that speaker problem(i.e after inserting headphone into the front jack the sound still comes from external speaker)... I had the same problem on my acer aspire 4710 laptop with SLED 10 SP1 installed. But I updated the alsa to the latest version from opensuse buid service.. and the all the front mi and headphone port they worked... And for the webcam I installed the uvc driver for the acer crystal eye webcam from suse repos.. and it worked.. Though U are running ubuntu I thought of sharing my experiences so that U may get some clue to the problem

---

### Post by bitra on 2007-12-16
> **suselover said:**
> For that speaker problem(i.e after inserting headphone into the front jack the sound still comes from external speaker)... I had the same problem on my acer aspire 4710 laptop with SLED 10 SP1 installed. But I updated the alsa to the latest version from opensuse buid service.. and the all the front mi and headphone port they worked... And for the webcam I installed the uvc driver for the acer crystal eye webcam from suse repos.. and it worked.. Though U are running ubuntu I thought of sharing my experiences so that U may get some clue to the problem

I'm going to try it out. Thanks.:)

---

### Post by abhi.datt on 2007-12-17
I built the latest uvc on gutsy using this
 [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)
however I'm still not able to use the Crystal Eye webcam present on acer 4710. Any thoughts

---

### Post by ddrake on 2007-12-24
Hi 

 I recently installed kubuntu7.10 on a new 4710N and after installing uvcvideo
drivers (compiled after checking it out from the subversion respository)) I tried
using kopete (instant messenger). In its 'devices' part of the configure settings tab,
I was able to see the webcam work!

Ofcourse, I had installed the necessary packages to install camorama, xawtv etc as well
as per the help.ubuntu.com's webpage on webcams.

Wonderful!

Bigger question - camorama says that cannot get the connection to /dev/video0 right....

any ideas from anyone?

DD

---

### Post by bitra on 2008-01-05
I've updated alsa to version 1.0.15 using [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") as a guide. But the external speaker doesn't work either. :-(

---

### Post by vigyani on 2008-01-20
Hi
I am using Ubuntu 7.10 on Aspire 4710.

Sound, speaker, headphone jack sense, mic work fine. For details look at:
[http://ubuntuforums.org/showthread.php?t=558069&highlight=aspire+4710]("http://ubuntuforums.org/showthread.php?t=558069&highlight=aspire+4710")

For webcam I use Ekiga; in video device chose V4L2 as video device. It works fine.

best wishes
Vig

---

### Post by obria on 2008-01-24
Hi there im still new with linux... 

I have 4710 and i just download Ubuntu 
I want to put dual OS in my 4710, Xp and Linux.
Anyone knows beside sound,webcam,cardreader,bluetooth   i  need to be sure that Modem,LAN, USB is working well ...???

Because ineed that device working to  get connet to the Internet.


TQ.


Sorry for my English...

---

### Post by vigyani on 2008-02-07
for me on this Laptop, except modem everything works fine under 7.10.

regards
vig

---

### Post by rimade on 2008-03-02
well try this; it works for me ,-)

install linux-backports-modules-generic
adde options line to /etc/modprobe.d/alsa-base: options snd-hda-intel model=acer


good luck.

---

