---
title: "karmic audio problem Intel 82801G (ICH7 Family)"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by bingung99 on 2009-11-01
Hi

With alot of help from the online community, i FINALLY managed to get 9.10 upgrade from 9.04...:D

However....problem is now I don't have sound...sigh...I tried some threads regarding the Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)...but still doesn't work....on one occasion...it muted my speaker...

...anyone ever managed to get the sound working with this model??

:(:(

---

### Post by rothfarb on 2009-11-01
I have the same problem.
In addition when I print it does not crash but does not print as well.

---

### Post by rothfarb on 2009-11-02
Problem solved. /etc/boot/menu.lst has not been updated in upgrade.
Mended it and now it recognizes audio card.
Way mended:
1.
2. Added the entry:
[COLOR="Blue"]title Ubuntu 9.10, kernel 2.6.31-14-generic
uuid 364530f3-021b-4e58-828f-24230cc1f1d3
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=364530f3-021b-4e58-828f-24230cc1f1d3 ro quiet splash 
initrd /boot/initrd.img-2.6.31-14-generic
quiet[/COLOR]
as first in entries list.
Where the the uuid I got using: [COLOR="blue"]ls -l /dev/disk/by-uuid[/COLOR]

---

### Post by ravy on 2009-11-02
> **rothfarb said:**
> Problem solved. /etc/boot/menu.lst has not been updated in upgrade.
Mended it and now it recognizes audio card.
Way mended:
1.
2. Added the entry:
[COLOR="Blue"]title Ubuntu 9.10, kernel 2.6.31-14-generic
uuid 364530f3-021b-4e58-828f-24230cc1f1d3
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=364530f3-021b-4e58-828f-24230cc1f1d3 ro quiet splash 
initrd /boot/initrd.img-2.6.31-14-generic
quiet[/COLOR]
as first in entries list.
Where the the uuid I got using: [COLOR="blue"]ls -l /dev/disk/by-uuid[/COLOR]


are you saying that you had to rebuild your kernel?

I'm having the same problem with my audio device not being recognized ... is this a kernel issue?

---

### Post by csete on 2009-11-03
I can validate that this was the problem I had with my audio.  Fixing up my grub menu.lst file to point to the newer kernel solved my audio issues.  

Now I need to figure out my video issues.

---

### Post by bingung99 on 2009-11-04
Ok...somehow I managed to get the audio working via virtualbox.....How do I copy and paste the current settings for me to do a fresh install on karmic later on the same computer??...without the virtualbox...

---

### Post by JCollierDavis on 2009-11-07
I've been horribly frustrated with my own lack of sound.  I've spent a total of about 10 hours trying everything to get it working with no luck.  I've added nearly every combination of options to my alsa-base.conf file with no success.

I'd like to try the fix mentioned above but don't have a /etc/boot/ directory or a menu.lst file.

I do have a /boot menu with files: vmlinuz-2.6.31-14-generic et.al and a /grub sub-directory.

Should I simply create a menu.lst file in that /boot menu? Is there perhaps another work around?

I've been using Xubuntu for about 4 months and have never had sound; I like it so much better than XP except the audio.

---

### Post by bingung99 on 2009-11-09
> **JCollierDavis said:**
> I've been horribly frustrated with my own lack of sound.  I've spent a total of about 10 hours trying everything to get it working with no luck.  I've added nearly every combination of options to my alsa-base.conf file with no success.



On another machine...9.10 works...even the sound...but I installed it inside Windows...using a 4GB RAM....I don't really see the difference in performance....just have to wait till the team fix the problem...I followed almost every post....the internal sound doesn't work with the version... :(:(

---

### Post by sarsbretta on 2009-11-10
I'm getting this error:

Nov  9 19:42:05 desktop pulseaudio[2839]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov  9 19:42:05 desktop pulseaudio[2839]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov  9 19:42:05 desktop pulseaudio[2839]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

I would report the issue but I don't know where to report it or how too.

---

### Post by mich_123 on 2009-11-11
I fixed it with the following steps:

[LIST]
[*]gksudo gedit /etc/modprobe.d/alsa-base
[*]add one line to the end of the file:
[FONT=courier new]options snd-hda-intel model=6stack-dig[/FONT]
[*]save and reboot
[*]rightclick on the volume icon and select **Sound Preferences**
[*]in the hardware tab, select a profile with "Surround" in it.
[/LIST]
[http://michael-peeters.blogspot.com/2009/11/sound-in-ubuntu-910.html](http://michael-peeters.blogspot.com/2009/11/sound-in-ubuntu-910.html)

---

### Post by szaemon on 2009-11-19
> **mich_123 said:**
> I fixed it with the following steps:

[LIST]
[*]gksudo gedit /etc/modprobe.d/alsa-base
[*]add one line to the end of the file:
[FONT=courier new]options snd-hda-intel model=6stack-dig[/FONT]
[*]save and reboot
[*]rightclick on the volume icon and select **Sound Preferences**
[*]in the hardware tab, select a profile with "Surround" in it.
[/LIST]
[http://michael-peeters.blogspot.com/2009/11/sound-in-ubuntu-910.html](http://michael-peeters.blogspot.com/2009/11/sound-in-ubuntu-910.html)

Hey Mich, this is exactly the chip and I guess the bug that I have. I tried your fix, but unfortunately I don"t have any options in the Hardware Tab with surround in them. I have analogue stereo input, analogue stereo output, and analogue stereo duplex.

Can you offer any suggestions? Or am I misunderstanding something?
Please let me know.

Thanks.

---

### Post by doballve on 2009-11-19
mich's suggestion does not work for me, I still get sound hardware reset to dummy and muted.. but then, this helps:

# sudo alsa force-reload

then just re-select sound hardware and increase the volume..

BTW, this was in some other thread, I just can't find it now.

---

### Post by xpo38 on 2010-04-01
> **doballve said:**
> mich's suggestion does not work for me, I still get sound hardware reset to dummy and muted.. but then, this helps:

# sudo alsa force-reload

then just re-select sound hardware and increase the volume..

BTW, this was in some other thread, I just can't find it now.


First time Ubuntu user here and had the same sound issue with my Intel 82801G and no sound after installing 9.10. Mich's suggestion did not work for me either and  I had no sound device options show up under Sound Pref's > Hardware.  As soon as that failed to get the results I wanted I used doballve's command and immediately had the Hardware tab populated with one device, a Internal Audio, 1 Output/1 Input, Analog Surround 7.1 Output+analog Stereo Input device.  I selected a profile with the same description and now have sound.  For what it's worth here's part of the output from the command and thanks to Mich and Doballve for the suggestions.


[I]Unloading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-si3054 snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.[/I]

---

### Post by JCollierDavis on 2010-04-01
> **rothfarb said:**
> Problem solved. /etc/boot/menu.lst has not been updated in upgrade.
Mended it and now it recognizes audio card.
Way mended:
1.
2. Added the entry:
[COLOR="Blue"]title Ubuntu 9.10, kernel 2.6.31-14-generic
uuid 364530f3-021b-4e58-828f-24230cc1f1d3
kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=364530f3-021b-4e58-828f-24230cc1f1d3 ro quiet splash 
initrd /boot/initrd.img-2.6.31-14-generic
quiet[/COLOR]
as first in entries list.
Where the the uuid I got using: [COLOR="blue"]ls -l /dev/disk/by-uuid[/COLOR]

I have GRUB2 which doesn't include the menu.lst file.  Any ideas about how to try this solution on grub.cfg?

I've really done everything several times and have run out of things to try, this is a solution I haven't seen before.

---

