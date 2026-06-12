---
title: "Dell e1505, resolution issues"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by tht00 on 2006-08-27
Alright - I recently installed Ubuntu on my new Dell e1505 laptop, and nearly everything worked 'out of the box'.  Screen resolution was detected right, wireless driver worked, sound worked, etc (quite the opposite from XP... that's another issue ;)).

Anyways, I installed the nvidia driver from Synaptic, and all was well, though, I think using the nvidia driver broke my virtual consoles (ctrl+alt f1-f6).  This has become slightly troublesome, as I've had some applications hang X, and without being able to get to a terminal to kill the process, I have to restart Gnome.  Besides this, the shutdown process is now blank too.  At times, it has taken a long time to shutdown, and I can't see why.  So, it seems that whenever the resolution is kicked down to the 'system' level, it just goes blank (but only after the nvidia driver has been loaded).

Thoughts?  Attached is my xorg.conf.  I don't see anything obviously wrong with it, but I don't have a whole lot of experience in troubleshooting it.

---

### Post by tht00 on 2006-08-28
hmm... *bump*

---

### Post by tht00 on 2006-08-28
*bump*

Is it just me, or are more-than-the-usual of more 'specific' or 'complex' issues getting no responses? :-k

---

### Post by tht00 on 2006-08-29
*bump*

Alright... this is getting old.  I need this problem fixed, but I'm really not sure where to start.  Can someone at least nudge me in the right direction (or at least starting point)?

---

### Post by r0ydster on 2006-08-30
I have the same laptop as you do - Dell E1505, with the Nvidia GeForce 7300. 

I have had no problems with the resolution once I installed the nvivia driver...

I've attached my xorg.conf.

Hope this helps.

Mike

---

### Post by tht00 on 2006-08-30
> **r0ydster said:**
> I have the same laptop as you do - Dell E1505, with the Nvidia GeForce 7300. 

I have had no problems with the resolution once I installed the nvivia driver...

I've attached my xorg.conf.

Hope this helps.

Mike

Thank you. :) 

I'll dig in and see if I can find anything useful.

---

### Post by magnom on 2006-08-30
Hey all,

Am new here and I had some questions,
I just perchased a new e1505 and I have some problem with the resolution, on IE7 the pictures quality are very very poor and on firefox the web content are very small. I tried every trouple shooting possible but no result. I really apreciate your help.
Thanks

---

### Post by tht00 on 2006-08-31
Hmm... I found nothing in the xorg.conf.  It may be my nvidia driver (I got it out of synaptic rather than the latest), or I guess it could be my kernel... I haven't tried the 386 kernel  again to see if that resolves anything.

I'm having wireless issues that are also not getting resolved, so I may try playing with reinstalling Linux (possibly another distro, or attempt the now-unstable Edgy).  Don't worry, if I do leave Ubuntu (at least on my lappy), I'll be back for the release of Edgy. :D 

> **magnom said:**
> Hey all,

Am new here and I had some questions,
I just perchased a new e1505 and I have some problem with the resolution, on IE7 the pictures quality are very very poor and on firefox the web content are very small. I tried every trouple shooting possible but no result. I really apreciate your help.
Thanks

IE7?  You're running Windows then?  I've really not used XP on this system.  The first thing I did was I 1) reinstalled Windows to get rid of the pre-installed crap-ware, and 2) Installed Ubuntu.  I've booted Windows maybe 10 times in the past week or so that I've had this laptop.

At least with Firefox, you can adjust text size, if that helps any.  Not sure where to start with the rest of it

---

### Post by r0ydster on 2006-09-03
> **tht00 said:**
> Hmm... I found nothing in the xorg.conf.  It may be my nvidia driver (I got it out of synaptic rather than the latest), or I guess it could be my kernel... I haven't tried the 386 kernel  again to see if that resolves anything.

I use the command line method, and did the following:

sudo apt-get install nvidia-glx 
sudo apt-get install nvidia-xconfig nvidia-settings

I also used this post as well for my both my desktop machine and laptop: [http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

> I'm having wireless issues that are also not getting resolved, so I may try playing with reinstalling Linux (possibly another distro, or attempt the now-unstable Edgy).  Don't worry, if I do leave Ubuntu (at least on my lappy), I'll be back for the release of Edgy. :D 
I have the Intel 3945 Wireless adapter, and I was expecting problems as well, but Ubuntu recognized it out of the box.

What wireless card do you have?

> The first thing I did was I 1) reinstalled Windows to get rid of the pre-installed crap-ware, and 2) Installed Ubuntu.

First thing I did as well - De-crapified the laptop, reformatted and reinstalled clean.  My windows partition run a lot faster (the few times I boot into it).

Hope this helps,

Mike

---

### Post by LinuxSmith on 2006-09-05
Edit /boot/grub/menu.lst
Go through it and remove the word "splash".
Restart and you will be good, but without usplash; no big loss.

---

