---
title: "Sound keeps looping on IBM Thinkpad 770?"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by Richard Rowlands on 2005-09-15
Hi,

I am using an IBM Thinkpad 770 running Ubuntu 5.04 and have a problem where the bongo sound keeps repeating over and over.  I have read other threads on this topic which suggest disabling the sound, however I have also read that people have managed to get sound working on Thinkpad 770 laptops.  To get the sound to work at all I added the following to the /etc/modules file :-

snd-cs4232

I also created a file /etc/modprobe.d/sound with the following options in it :-

options snd-cs4232 port=0x530 cport=0x530 isapnp=0 dma=1 dma2=0 irq=5

I can run alsamixer and set the volume for PCM  and hear the volume of the bongos increase or decrease.  I suspect ALSA is therefore configured properly.

Following on from this, I have set gstreamer-properties to use ALSA instead of ESD.  I have also set the "Multimedia Systems Selector" to use ALSA.

Neither of these options improved matters.  Further to this I disabled ESD and noticed no change (probably due to me having chosen ALSA previously).

Eventually, I disabled the logon sound by changing SoundOnLogin=false in /etc/gdm/gdm.conf.  When running the recording level monitor from Applications->Sound & Video, I'm told "Please run 'esd' at a command prompt".  However, when I ran esd at the command prompt, esd would not return and would sit there repeating a pulsating bleeping sound.

It seems that anything that accessing the sound system will get stuck repeating that sound until the process is killed.

This is driving me mad, I've spent all evening every evening for a week trying to sort this.  Can anyone shed any light?

Regards, Richard.

---

### Post by Richard Rowlands on 2005-09-16
Further to what I wrote yesterday, I've noticed that after I have logged in and done a "killall aplay" to silence the bongos - sounds work correctly in Flash animations in FireFox.  The volume control also appears next to the clock in the Gnome start bar and this functions properly.  This is weird.   :-|   I think I'm more frustrated with my sound half working than when it wasn't working at all!  Help anyone?

Cheers, Richard.

---

### Post by lightenup on 2006-04-15
I have/had a similar problem with 5.10 but not in 5.04. In 5.10 using some information I found here:

[http://www.axxite.com/brn/en/index.html](http://www.axxite.com/brn/en/index.html)

So I tried:
Sudo modprobe snd-cs4232

The module would never load. However, using the OSS drivers worked:

Sudo modprobe cs4232

So I added cs4232 to the last line in /etc/modules

cs4232

…and the following in a new file /etc/modprobe.d/sound:

alias char-major-14 cs4232
post-install cs4232 modprobe "-k" opl3 
options cs4232 io=0x534 irq=5 dma=1 dma2=0 mpuio=0x330 mpuirq=9
options opl3 io=0x388

Upon a reboot the mixer would see the card and the volumes level would work. However, sound would play but it would just loop over and over. Thus if I fired up XMMS (from the terminal: sudo apt-get xmms) and played a mp3 file it would just sit and studder over and over like a broken record. At this point If I entered the mixer application and hit the mute button rapidly I could hear a song play. Crazy eh? Moving on…

I really wanted Ubuntu on this old laptop so I decided to try the older version 5.04. 

In 5.04 if I followed the same procedure as above everything works. The mixer functions properly and XMMS playes my mp3’s! Now I just have to get my wifi card up! 

Also, on this system the screen does not function correctly at 24bit color. You need to edit /etc/X11/xorg.conf and search for the number 24 and replace it with 16 as talked about here: [http://www.ubuntuforums.org/archive/index.php/t-11657.html](http://www.ubuntuforums.org/archive/index.php/t-11657.html) . After a reboot you will have a nice full screen display ;)

One other thing does any one know how to enable the fan? I never hear it turn on any more.

---

