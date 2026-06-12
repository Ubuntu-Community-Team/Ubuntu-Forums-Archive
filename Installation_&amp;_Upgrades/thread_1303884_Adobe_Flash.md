---
title: "Adobe Flash"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by jats605 on 2009-10-28
Which version of flash should I download for youtube vids?

BTW: I got the dual boot working.

---

### Post by 1roxtar on 2009-10-28
I use the newest version (Adobe Flash Player 10).  With Ubuntu RC, I no longer get any choppy video on my Acer Aspire One netbook or older Gateway 7324GZ laptop.

:guitar:

---

### Post by jats605 on 2009-10-28
Well yeah, but for Linux it has 4 differnt ones. 
YUM
.tar.gz.
.rpm
.deb (this says for Ubuntu 8.04+ so it would be this one right?)

---

### Post by trubble on 2009-10-28
Yes, use the .deb version.

---

### Post by 1roxtar on 2009-10-28
> **jats605 said:**
> Well yeah, but for Linux it has 4 differnt ones. 
YUM
.tar.gz.
.rpm
.deb (this says for Ubuntu 8.04+ so it would be this one right?)

Yes, you need to download the .deb package.  If you are using Ubuntu 9.10 Beta/RC you can find it in the Ubuntu Software Center.  Simply type "Adobe Flash" in the search box and install.

---

### Post by jats605 on 2009-10-29
Ok, i downloaded it but youtube still wont work. Any help?

---

### Post by 1roxtar on 2009-10-29
Go to System/Administration/Synaptic Package Manager....type in the search box "swfdec-mozilla" if it is installed, uninstall it.  Sometimes, it can conflict with Adobe Flash, but removing it should help.  Are you running 9.04 Jaunty or 9.10 Karmic?

---

### Post by jats605 on 2009-10-29
Jaunty atm, but plan to upgrade asap.

---

### Post by jats605 on 2009-10-29
THANK YOU! It works now!

---

### Post by jats605 on 2009-10-29
Gah now the cound isnt working. I dont know why, but the video plays, but the sound doesn't. The weird part is, it was working a while ago...

---

### Post by edanto on 2010-01-24
I have the same problem as you - sound isn't working in my Flash, but it's working fine in everything else (music player for example).  I'm just starting to use Ubuntu (9.10) and I'm a little unsure of things like terminals!

I'm going through the sound troubleshooting steps one by one, but can you please say if you fixed your sound in flash, and how?

thanks

---

### Post by edanto on 2010-01-30
Updating Flash player fixed the sound problem.

(although video play is quite sluggish - I'll try a different flash player)

---

### Post by grouchyolddude on 2010-03-22
My audio quit several updates back in 9.04. I've been searching trying every "fix"  I can find for a few weeks. 
>  apt-get purge pulseaudio
fixed the flash plugin sound in firefox, but now I have no audio in the movie player.
Reinstalled pulseaudio and now the sound and video in flash plugin(firefox) is choppy and distorted and the movie player, kaffiene  no longer has audio ..
Sound preferences are set to oss in system.all volumes on the alsa mixer are up in the red.  

I'm frustrated....:???:

---

### Post by edanto on 2010-03-22
I must admit, I'm a complete novice with Ubuntu, but if it's any help to you, someone on this thread suggested a Firwfox greasemonkey extension that was able to smooth out the flash playing for me.
[http://ubuntuforums.org/showthread.php?t=1390335&page=3](http://ubuntuforums.org/showthread.php?t=1390335&page=3)

Unfortunately, I still have some audio problems (my mic won't work, which means no voip), but at least that workaround fixes Flash in Firefox.

If anyone can advise me on the audio problems, I'd be grateful -
[http://ubuntuforums.org/showthread.php?t=1392915&page=2](http://ubuntuforums.org/showthread.php?t=1392915&page=2)

---

### Post by grouchyolddude on 2010-03-22
results of sudo lshw -C sound

>   *-multimedia            
       description: Multimedia audio controller
       product: MCP2S AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0


---

### Post by grouchyolddude on 2010-03-22
ran sudo apt-get update and rebooted.. It appears I'm right back at square one.. no flash audio, but movie player, ect are back to working normal

---

### Post by grouchyolddude on 2010-03-22
> 
sudo apt-get remove pulseaudio
then
> 
sudo apt-get install esound
reboot ..
fixed the issue entirely for me..

EDIT: I did have to go into systems-preferences-sound and put everything on alsa from the drop menu

---

