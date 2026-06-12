---
title: "no sound in gnome"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by simoncullen on 2005-08-23
I've just installed Ubuntu and everything's going okay.  There are a few issues that I'd like to iron out (suspending to ram/harddisk), but the most important is getting my sound card to work.  I've read through many of the topics on this forum, but I can't get it going.  It appears to me as if Ubuntu has correctly detected the hardware...

this is the relevant output from lspci:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

I think the card is called a "Soundmax Integrated Audio".  

Any help will be much appreciated!

Cheers,
Simon

---

### Post by simoncullen on 2005-08-23
Just a bit more info:

When I run 'Multimedia systems selector', I can see the Default sink is ALSA, and I press 'test' and the bar moves from side-to-side.  I've been in ALSA mixer, tried almost everything!  I really want to use my computer to call home (Australia) as I'm studying in the US for the next year!  So help will really be appreciated.

Thanks,
Simon

---

### Post by s_p_a_r_k_y on 2005-08-23
in my sound woes the most important thing to do is kill any sound daemon so you can use the sound card directly.

```
pkill -9 esd
``` should take care of that pest. Then try something fun like
```

cat /dev/urandom > /dev/dsp

```
It should create a quite soothing sound (make sure you do this with the volume turned all the way up in a public library)
or 
```

sudo cat /dev/input/mice > /dev/dsp

```
will make a nice beep when you move your mouse enough
also if you have a wave file
```
cat wavfile.wav > /dev/dsp 
``` will play the wav.
Let us know if these tricks work for you to atleast get some sound out of your computer. Then the next step is to see if playing a song in xmms

---

### Post by simoncullen on 2005-08-24
Hi, and thanks for your reply.  None of this makes my computer so much as beep!  What to do?

---

### Post by simoncullen on 2005-08-24
One other thing which you might be able to help me with...

I am trying to install azureus as per the guide.  But it gives me this error:

> The following packages have unmet dependencies:
  azureus: Depends: sun-j2sdk1.5 but it is not installable or
                    java2-runtime but it is not installable

I've installed java from the sun website and I think it's working...  Any ideas?

Thanks again!
Simon

---

### Post by s_p_a_r_k_y on 2005-08-24
simoncullen, a problem with installing software from the vendors websites is that its not in the .deb package format usually. Thus when you try to use apt to install software which needs java, apt can't "find" java bc it wasn't installed through apt.

I would remove the java install from sun and go through apt. I think its called blackdown-java. Google for it and you'll find it : ) THen installing azerus shouldn't be a problem...Also do you just want a bittorrent client? There are many other ones out there:

apt-cache search bittorrent
bittorrent - Scatter-gather network file transfer
bittorrent-gui - Scatter-gather network file transfer (GUI files)
mldonkey-server - Door to the 'donkey' network
qtorrent - BitTorrent client for QT 3.x
kdenetwork-kfile-plugins - torrent plugin for kfile
gnome-btdownload - Gnome interface for 'executing' BitTorrent files.
azureus - BitTorrent client
bittornado - bittorrent client with enhanced curses interface
bittornado-gui - bittorrent client with enhanced GUI interface

---

### Post by ola on 2005-08-24
I have the same problem with my soundcard.. 

```
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
``` 

It seems to be almost the same card as you have.. 

Is there any luck here? I can't get it working...

---

### Post by ola on 2005-08-24
I found a solution posted here: [http://ubuntuforums.org/archive/index.php/t-32063.html](http://ubuntuforums.org/archive/index.php/t-32063.html) 

Hope it works for you as well!

.o

---

### Post by ola on 2005-08-24
I found this post: [http://ubuntuforums.org/archive/index.php/t-32063.html](http://ubuntuforums.org/archive/index.php/t-32063.html) and it worked for me. Hopefully does it work for you as well.

.o

---

### Post by simoncullen on 2005-08-24
Ahoy again,

None of this has worked... In the media systems selector when I test the pipeline the bar goes from side-to-side, but I still don't hear anything!  I can't use Ubuntu (as much as I love it) if I can't get this working?  I've even tried installing ALSA from their website...

Cheers,
Simon

---

### Post by simoncullen on 2005-08-26
...still not more ideas??  i tied it with mandrake and had the same problem,

---

### Post by Project 318 on 2005-08-26
I have the same card (Gateway laptop) and it annoyed the crap out of me when whatever I did didn't work.
Open up kmix or an equivalent  and set Switches as Stereo Mic, not External Amplifier, and enable Master Mono in the Output tab (and IEC95B playback if it isn't enabled).
It should work then, if not just play with the mixer until you get sound because it WILL work.

---

### Post by simoncullen on 2005-08-26
Thanks for your replies...  None of this has worked, though I'm sure it can.  Should I try something other than ALSA perhaps?

Cheers,
Simon

---

### Post by simoncullen on 2005-08-26
Thank you!  You have no idea how good Ella's sounding right now (even through my laptop's crappy speakers).  SImon

---

### Post by vkkim on 2005-08-28
[QUOTE=simoncullen]Thank you!  You have no idea how good Ella's sounding right now (even through my laptop's crappy speakers).  SImon[/QUOTE]

Could you please explain how you got it to work? I have the exact same problem with the same soundcard, or so I think ([http://ubuntuforums.org/showthread.php?t=47048](http://ubuntuforums.org/showthread.php?t=47048)) but I have yet to get it working.

---

