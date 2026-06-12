---
title: "USB sound card works with some apps but not others."
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by sgarman on 2007-10-27
Hi folks,

I've done some digging and gone through some of the other sound troubleshooting guides but I'm coming up with nothing. It appears that my Creative USB SB Live! external sound card is working properly, but some applications aren't aware of it. 

Sound is working fine for gstreamer-based applications, such as Totem and Rhythmbox. It is not working for mplayer, vlc, or the Flash plugin for Firefox. 

I do have an on-board sound card on my motherboard but it is disabled in my BIOS and is not showing up in any of my kernel logs.

After I did a fresh install of Gutsy, I did not get any sound until I went to my sound preferences and selected "USB Audio" in the drop down lists. Again, this fix only seemed to work for gstreamer-based applications. 

aplay -l correctly shows my USB SB Live! but alsamixer reports "no such device". 

Could someone give me a nudge in the right direction?

Thanks,

Scott

---

### Post by whateva on 2007-10-28
hi there,
same with me.
also would like to know how to check wihich sound system does it use OSS/ALSA or other maybe itll will help to properly configure appz.
im using ac3 passthru over spdif and when movie is in stereo my speakers every 10 or 15 sec make some scrachy noise. how can i fix it? when im listening mp3 everything is ok.
thank you lads

---

### Post by sgarman on 2007-11-01
Update: I found the solution described in [this thread]("http://ubuntuforums.org/showthread.php?t=570220") worked to enable sound in all my apps. 

To restate it, you want to edit /etc/modprobe.d/alsa-base and change the index value for the snd-usb-audio module from -2 to 0. After a reboot I was all set.

Scott

---

### Post by mchaggis211 on 2007-11-04
i tried that work around and i still have no luck getting sound on youtube etc.

---

