---
title: "No sound - Dell E520 - SigmaTel STAC9227"
date: 2008-11-10
forum: Hardware
---

### Post by dunk010 on 2008-11-10
Since upgrading to ibex I have had no sound.  I'm fully updated.  I have tried to force the intel sound module to the dell-3stack option by adding "options snd-hda-intel model=dell-3stack" at end of /etc/modprobe.d/alsa-base, but to no avail.  Sound appears to play from mplayer (and others), but no sound is heard.

My config info:
[http://www.alsa-project.org/db/?f=a8df09f371653008921ed9b45c17f9047a1234df](http://www.alsa-project.org/db/?f=a8df09f371653008921ed9b45c17f9047a1234df)

I'm a bit stuck now, any ideas?

---

### Post by dunk010 on 2008-11-16
Found my problem - by installing gnome-alsamixer I found that the command line version was showing me the wrong card, so I ran:

alsamixer -c 0

I think that in the mean time that the patches fixed the underlying problem as I've removed the forced 3stack change I made earlier.

---

### Post by pacofvf on 2008-11-16
almost the same problem, I changed my motherboard, the audio also was Sigmatel stac9227, and the same thing hapenned.... I just ran: $ alsamixer -c 0
 , and problem solved

---

### Post by thba on 2009-08-22
I have exactly this setup. No sound except when using alsamixer and selecting analog loopback. I can here my mic but no sound from anything else.

The sound starting working once I installed gnome-alsamixer

---

### Post by helpdeskdan on 2009-10-09
Finally!  More E520 users! 

I had to install oss4 to get it to work.  However, not everything works with oss4 and I can't get recording to work.  I didn't try alsamixer -c 0.  If I can successfully get oss4 removed and alsa reinstalled, I will try it.

---

### Post by helpdeskdan on 2009-10-09
Finally got it working in Jaunty.  The correct line should be:
options snd-hda-intel model=dell-3stack

BUT... that doesn't work.  This works:
options snd-hda-intel model=ref

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363721)

Hope that helps somebody out!

---

### Post by feedmecereal on 2009-11-08
Hi folks! I've had a disaster of a time getting sound to work for forever until I read helpdeskdan's post. However, I still can't get sound **in** to work. I really want to use the Skype credits that I bought a while back when it was working.

I get a strange message when I try to use Sound Recorder: "Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System-Preferences menu." I don't even think that option still exists under the System-Preferences menu in 9.10.

Any ideas?

---

### Post by helpdeskdan on 2009-11-15
If it's of any consolation, neither can I.  Oh, and don't even think of upgrading to 9.10 because it's worse.  It has a sound fade bug that #1.  They have no intention of fixing and #2. The workaround (model=3stack) doesn't work.  

I'm thinking of going back to oss again!!

---

### Post by feedmecereal on 2009-11-16
The wierd thing is that I know I got sound in to work before my old hard drive crashed but I can't seem to find the thread that I used to fix it. I used to use Skype all the time. It just seems that information on Ubuntuforums is just so spread around all over the place that it's hard to find info again.

---

### Post by helpdeskdan on 2009-11-16
K, here's what I did in 9.10

1: upgrade alsa:
[http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

(I used the repo one of the guys talked about in the thread rather than compiling) 

Then, in /etc/modprobe.d/alsa-base.conf:

comment out the line that begins: "options snd-hda-intel power_save=10"

add:
options snd-hda-intel model=ref

sudo alsa force-reload
& you should see:
dan@dan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

hope that helps!

---

### Post by feedmecereal on 2009-11-16
> **helpdeskdan said:**
> (I used the repo one of the guys talked about in the thread rather than compiling) 


I fear this may sound really dumb, but what repo are you referring to?

---

### Post by feedmecereal on 2009-12-01
Well, my hard drive crashed and I had a hell of a time getting my sound to work again. The strange thing is that helpdeskdan's first fix didn't work this time. I had to use your last post. And I figured out what you meant by that one line about the repo. But I can't get sount to work with Flash now!

Damnit, this is getting frustrating. I'm thinking about giving up and just buying a System76 computer.

---

### Post by smellyman on 2009-12-01
> **helpdeskdan said:**
> K, here's what I did in 9.10

1: upgrade alsa:
[http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

(I used the repo one of the guys talked about in the thread rather than compiling) 

Then, in /etc/modprobe.d/alsa-base.conf:

comment out the line that begins: "options snd-hda-intel power_save=10"

add:
options snd-hda-intel model=ref

sudo alsa force-reload
& you should see:
dan@dan-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

hope that helps!

Thank You!!  Was beating my head against the wall and this finally worked.  I had to add the line to alsa-base.conf too.

---

### Post by puffead on 2010-02-09
Thank You! i Have been struggling with this for a week and this fix took about 5 min you may have rescued my sanity

---

