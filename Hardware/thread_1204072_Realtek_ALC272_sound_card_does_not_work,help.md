---
title: "Realtek ALC272 sound card does not work,help"
date: 2009-07-04
forum: Hardware
---

### Post by yorkzhang on 2009-07-04
I am very new to ubuntu and I just purchased a netbook -  Toshiba NB200. Then I installed ubuntu netbook remix version 9.04 after windows xp installed. Everything is working well except the sound card. There seems no visual error in the system but no sound can be heard.

Then I try to compile and install the drivers(include drivers,libs and utils)from realtek web site([http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)) and offical  alsa web site([http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)). More options were displayed in the volume control panel but still no sound. 
(I have already disable the mute and push volume to highest in alsamixer and control panel of ubuntu).

However, I can hear the sound from built mic if I plug the earphone in the netbook. 

Anyone can solve this problem?

---

### Post by Ultim8Fury on 2009-07-04
You're not alone. I also have the NB200 and no sound. There is an open bug report on launchpad for the issue. It appears that it's being looked at so I guess it's just a matter of waiting. Seems you've tried everything I've tried, so I have no further suggestions. My temporary work around is to use a USB headset which has its own sound card in it but the sooner the problem is fixed the better. It sort of explains why Toshiba don't offer this very nice netbook with linux where they did with the NB100.

---

### Post by yorkzhang on 2009-07-05
Just solved this problem partly.(You can hear sound from a plug-in earphone or speaker but not the build-in speaker) 
The post in SUSE forums really helps me a a lot.
[http://forums.opensuse.org/hardware/laptop/406598-yet-another-sound-problem.html](http://forums.opensuse.org/hardware/laptop/406598-yet-another-sound-problem.html)

The brief instruction for ALC272 is as below:
$sudo gedit /etc/modprobe.d/alsa-base.conf

then add(or edit) this:

options snd-hda-intel model=asus-mode4

Close gedit,then run this in the terminal

alsamixer

adjust volume and reset your computer.

If still no sound, try to upgrade the alsa. you can follow the way of this post

[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script](http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script)

Good Luck

---

### Post by Ultim8Fury on 2009-07-05
Nice find. It's a step further on than I was. Next up ... wifi.

Thanks.

---

### Post by crlbeijing on 2009-07-05
I had the same experience as Yorkzhang so really appreciate finding a partial solution.  For me everything (including wireless) works great and I really like the netbook re-mix.

If anyone finds a solution to the sound from built-in speaker and microphone I would be grateful.

Thanks

---

### Post by yorkzhang on 2009-07-05
> **Ultim8Fury said:**
> Nice find. It's a step further on than I was. Next up ... wifi.

Thanks.

The wifi is much easier.What you should do is just as below.

$sudo apt-get install linux-backports-modules-jaunty

---

### Post by Ultim8Fury on 2009-07-06
Yeah I did that,, now the card is detected during boot and appears in the output of ifconfig however it doesn't seem to actually work. Maybe I'm being dense but it can't detect any wifi networks at all and I'm only 6ft from my router.

Think I may have found out what the problem is. According to [http://ubuntuforums.org/showthread.php?t=1193429&page=3&highlight=AR928]("http://ubuntuforums.org/showthread.php?t=1193429&page=3&highlight=AR9285")

if wifi was turned off in windows then it won't work in linux. 

[http://tjmcgrew.com/](http://tjmcgrew.com/)

useful link from some guy with an NB205

---

### Post by chalkie1975 on 2009-07-06
I'm also an NB200 owner - i've played around with all the installed packages so much that I don't have a new build feel to the kernel i'm running. I can get wireless working fine, but the sound problem was and still is annoying me.

I found the linux-backports-modules-jaunty actually 'stopped' my wifi from working, so i unstalled it. I did a manual compile of the compat-wireless.2.6.30 drivers and all works ok. I even narrowed the makefile down to the ath9k driver so i didn't have to compile useless modules.):P

---

### Post by arjantje on 2009-07-11
I just bought a NB200 also, have sound on the headphones and no speaker.

I hope somebody will figure this out soon, it quite useless like this to me.
I was surprised that the sound would be the big issue.

I was playing with the mixer and noticed to following (using the 'options snd-hda-intel model=asus-mode4"):

- microphone is listed as a playback device
- headphone & pcm both control the volume for the headphones like the one is piped into the other.
- master does nothing

It seems like the sound chip is working fine, but that the channels are not mapped properly through the mixer. I am wondering how the alsa mixer is mapped, and if that can be done manually.

Can anybody shine some light on this?

---

### Post by dimeotane on 2009-07-17
I ran 8.10 using a usb stick today on my Toshiba NB200 and totally expecting the audio to not work and IT DID!  (But no wireless =(

I tried using ndiswrapper and it seemed to install the drivers on the windows partition (/programfiles/atheros/driver/netathw.inf)
ndiswrapper -l showed
"netathw: driver installed 
      device (168C:002B) present"

but I couldn't get it any futher than that
iwconfig showed no wireless extensions.
Has anyone managed to get the NB200 wireless working on 8.10 using ndiswrapper?




So apparently the audio is a problem on the newer 9.04 read more here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040")

The AR9285 wireless requires kernel 2.6.29.
I've read the latest daily build of the netbook remix is supporting it, so I'm downloading that now.


anyone got the bluetooth  working now?   (Oh and will the Gshock detector work in ubuntu or is it a windoze only feature?)

---

### Post by Ultim8Fury on 2009-07-17
I don;t think bluetooth is working but I've never setup bluetooth in Linux so it might be and I just don't realise it. 

I'm fairly sure the g-shock thing is Windows only since it seems to rely on a toshiba driver to make it work. 

I replaced the harddisk with an SSD a couple of days ago so I've sidestepped that issue ( and extended the battery life a little bit). 

I also found getting the latest stable xorg helped with video performance. I was getting tearing on most video before but since the upgrade it's completely gone. 

This stuff probably deserves a dedicated Dynabook UX/NB200/NB205 setup thread. 

I found an fdi script which improved the mouse response as well. 

Just got in from work and going to get some sleep but when I get up I'll kick off a proper setup thread unless someone beats me to it.

---

### Post by divan0 on 2009-07-17
Just in case - Alsa 1.0.18rc3(default in Jaunty) and 1.0.20 works perfectly out-of-the box with ALC272 on Acer AspireOne 751h.

---

### Post by a2cno on 2009-08-03
Hi Divan0,

Could you please check what model is used in your /etc/modprobe.d/alsa-base file and post it here? It should be like 'options snd-hda-intel model=YOUR_MODEL'. Thx

---

### Post by dimeotane on 2009-08-24
I'm happy to share that I finally have both the speakers and headphones working on my Toshiba NB200 (NB205) netbook.  YAY!!  (I'm using Karmic 2.6.31) 

There is a new patched kernel that's available to be tested for Karmic and Jaunty that you can download and install as a deb.


Check the bottom of this page for the debs to test that were released on August 22
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040)

:guitar: I'm listening to music through the speaker right now, and although it's small, it is nice to have!


Some things I also did was add


options snd-hda-intel model=toshiba
(also using model=ALC272 seems to work)


to /etc/modprobe.d/alsa-base.conf

and then restart ALSA with
$ sudo alsa force-reload
$ sudo /etc/init.d/alsa-utils restart



Also on this Karmic version of Ubuntu Netbook remix I installed gnome-media and ran gnome-volume-control-applet



I don't think the mic is working yet. 
I also ran alsamixer to set all the sliders to max and changed the capture input source to front mic to try to get the mic working.


I can see mic levels when I use  (but no playback)
options snd-hda-intel model=auto
changed input to microphone 2 

also ran alsamixer to set all the sliders to max and changed the capture input source to front mic to try to get the mic working, and it appears to sense the internal microphone sound levels.

---

### Post by tenfishsticks on 2009-12-24
I have an eMachines E627 running Jaunty.  I've been running for about two weeks, and yesterday the Ubuntu gods decided to punish me with no sound.  I don't know what I did to displease them - I didn't change anything to my configuration that I can remember.  I have been using Rubyripper for the last several days, but no changes to my setup.  

I used alsamixer to get some sound out of the headphones, but there is now significant white noise at low volumes!  No sound through the internal speakers.

After installing the deb package and restarting ALSA, it works like a charm... excellent work!  Thanks!

---

