---
title: "Very weird sound problem, Toshiba"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by rtn_ylw on 2007-06-27
Hi!
I bought Toshiba Satellite A135-S4527 yesterday, installed kubuntu, but the sound is not working. I followed [this thread]("http://ubuntuforums.org/showthread.php?p=2886365"), but that didn't solve my problem. This is my aplay -l output:
```
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Both, my sound card and modem is listed. I added the *options snd-hda-intel probe_mask=8 model=3stack* at the bottom of /etc/modules.d/alsa-base and restarted my laptop, but then when I ran  aplay -l after, nothing comes up and kmix has red x over it. I thought maybe just unload the module for modem, but I'm not sure which module does it use.. any suggestions please? thank you!!

---

### Post by BobLand on 2007-06-27
Have you looked at and run the procedure [[COLOR="Red"]Comprehensive Sound Solution[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound")...?  That will give you the basics of how to get the system set up with drivers etc.

Look at /etc/modules.  You must see your driver there.  If not, add it and comment out the others.
run 
```
sudo apt-get update && sudo aptitude dist-upgrade
reboot
```
  
[[COLOR="Red"]Click here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=457373") to see posts that I documented that helped me get my sound to work.  There are many things that kill sound in Ubuntu.  When that happens, I go back to this thread.  The most common problem is an overwritten /etc/modules file.

Hope this helps
bobland

---

