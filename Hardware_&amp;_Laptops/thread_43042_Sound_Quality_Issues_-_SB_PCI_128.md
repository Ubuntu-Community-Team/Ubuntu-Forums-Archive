---
title: "Sound Quality Issues - SB PCI 128"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by tristure on 2005-06-20
Hi,

some of you may have followed my (failed) attempts to get good sound quality in Linux.

My last chance is with my old Sound Blaster PCi 128.

Unfortunately I get horrible sound quality with it : I hear cracks and static whenever I play music. Turning the volume down doesn't help... It's just not as loud, but it's always there !!

Now I noticed something : booting with Knoppix 3.7 I saw that the sound quality within Knoppix was really good. I mean I heard no static or cracks.

I use Kubuntu.
In hoary KMIX displays my card as "Ensoniq audio PCI"
In Knoppix Kmix displays it as "SigmaTel STAC 9721/23". And I get much more controls in the Knoppix mixer that way.
So it seems that the Sigma Tel driver is more suited to my card.

So : do you know what is going on? Any idea how I could get this driver to work with my card in Kubuntu?

Thanks a lot!

---

### Post by tristure on 2005-06-20
[QUOTE=tristure]Hi,

some of you may have followed my (failed) attempts to get good sound quality in Linux.

My last chance is with my old Sound Blaster PCi 128.

Unfortunately I get horrible sound quality with it : I hear cracks and static whenever I play music. Turning the volume down doesn't help... It's just not as loud, but it's always there !!

Now I noticed something : booting with Knoppix 3.7 I saw that the sound quality within Knoppix was really good. I mean I heard no static or cracks.

I use Kubuntu.
In hoary KMIX displays my card as "Ensoniq audio PCI"
In Knoppix Kmix displays it as "SigmaTel STAC 9721/23". And I get much more controls in the Knoppix mixer that way.
So it seems that the Sigma Tel driver is more suited to my card.

So : do you know what is going on? Any idea how I could get this driver to work with my card in Kubuntu?

Thanks a lot![/QUOTE]
 OK, I checked out a few things, and some results surprise me.
Here's what I get in Knoppix :

knoppix@ttyp1[knoppix]$ cat /proc/asound/cards
--- no soundcards ---


knoppix@ttyp1[knoppix]$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Oct 19 2004 for kernel 2.6.9 (SMP).


knoppix@ttyp1[knoppix]$ cat /proc/asound/oss/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.6 emulation code)
Kernel: Linux Knoppix 2.6.9 #2 SMP Tue Oct 19 23:51:10 CEST 2004 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers: NOT ENABLED IN CONFIG

Mixers: NOT ENABLED IN CONFIG


So it doesn't seem to recognize anything... and yet the sound works flawlessly?

What the hell?

Any ideas on this would be GREATLY appreciated. Thanks a lot for your help!!

---

### Post by tristure on 2005-06-20
Just another post to add that my card is correctly recognized in Hoary, and sndstat shows some result too...
And yet it doesn't work correctly compared to Knoppix...

This is really puzzling me.

---

### Post by tristure on 2005-06-21
This is getting really strange.

If i boot Knoppix with the alsa=ens1371 option, it loads the same modules as Hoary does, so it has the same drivers for the same card!

And yet it sounds perfect in Knoppix, crappy in Hoary and other distros. (for the same volume settings).

I'm getting really mad with sound and Linux. It COULD sound good, but doesn't whatever I do. And it's been like that for two years.

Well, if any of you has a suggestion...

Thanks a lot!

---

### Post by Curlydave on 2005-06-21
I have the exact same problem. It's weird, and I don't know what's causing it. You can try lowering the PCM volume and raising the master. Tell me if that reduces it. It certainly won't fix it however, and will leave you with a very weak signal. It reduced the static content for me though.

Does anyone know what's causing this problem, because I would really like to know. It happens with my onboard audio and my TB Catalina.

I havn't compared it to knoppix, but in Windows the sound is fine.

---

### Post by tristure on 2005-06-22
Well I figured it out.

In this case, the problem was caused by using ESD and Alsa to play multiple sounds (following a Howto on this forum).

I switched back to the default situation and the sound became perfect.

So if you used the same trick, you could try to cancel the changes.

Mind you, using another sound card (cs46xx) even the default situation gives horrible sound. In this case I think the driver is to blame...

Now the problem is I need to be able to play multiple sounds without breaking anything.

---

### Post by afonic on 2005-06-22
Hi,

can you post the steps you followed to cancel the changes?

I have a similar problem and want to see if that will fix it.

---

### Post by tristure on 2005-06-22
Did you read this guide and make the changes listed?

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=hoary+multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=hoary+multiple+sounds)

If you didn't, then you don't need to do anything.

If you did, well, take the guide backwards and do the opposite of what's told : change esd.conf, delete asound.conf and install libesd0 instead of libesd-alsa0.

Good luck!

---

### Post by afonic on 2005-06-22
[QUOTE=tristure]Did you read this guide and make the changes listed?

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=hoary+multiple+sounds](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=hoary+multiple+sounds)

If you didn't, then you don't need to do anything.

If you did, well, take the guide backwards and do the opposite of what's told : change esd.conf, delete asound.conf and install libesd0 instead of libesd-alsa0.

Good luck![/QUOTE]
 Yeah, I just needed to be sure what you did to get back. I followed the same steps, and yes, the system sounds play all fine.

However my mp3s still have small problems which you can clearly hear in a "silent" moment on the track. Do mp3s pay nice and clear (as in "Crystal clear") to you?

---

### Post by tristure on 2005-06-23
[QUOTE=afonic]Yeah, I just needed to be sure what you did to get back. I followed the same steps, and yes, the system sounds play all fine.

However my mp3s still have small problems which you can clearly hear in a "silent" moment on the track. Do mp3s pay nice and clear (as in "Crystal clear") to you?[/QUOTE]
 I listened to many songs last night, with earphones, and the sound was pretty much crystal clear to me.

Could you give one or two examples of songs where you hear problems so I could check it out precisely?

---

### Post by afonic on 2005-06-23
[QUOTE=tristure]I listened to many songs last night, with earphones, and the sound was pretty much crystal clear to me.

Could you give one or two examples of songs where you hear problems so I could check it out precisely?[/QUOTE]
 Well I finally fixed it by selecting Also and not ESD in "Multimedia Systems Selector" in the System menu.

I think that when I had the setting in ESD it used OSS which must have used another MP3 decoder.

Thanks for the suggestion about reverting the changes in that post, before that even my system sounds where problematic, and I thought it was a driver issue!

---

