---
title: "Sound in HP Pavillion tx2500z CTO not working"
date: 2009-08-31
forum: Hardware
---

### Post by Klopenator on 2009-08-31
I'm running Ubuntu 9.04 but cannot get the sound to work on my HP Pavillion tx2500z CTO notebook.  I've tried some of the methods on this site but none of them seem to work with my compy.  Suggestions?

---

### Post by Favux on 2009-08-31
Hi Klopenator,

The following line seems to work for TX2500 users:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
Add it to the bottom of the file "alsa-base.conf" at "/etc/modprobe.d/".  Don't worry that it says Toshiba.

To edit it enter in a terminal:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Save, close, and reboot.

Also check to see if the mixer is muted.  If so make sure the sliders are up.

Hope this helps.

---

### Post by Klopenator on 2009-09-01
Wow, that actually worked!  I've tried this before, but I had had configuration lines in options.conf in the same directory which configured the device wrong.  Thanks for your help!  (Now I may actually consider removing Windows 7!)

---

### Post by Favux on 2009-09-01
Hi Klopenator,

Good deal.  You're welcome.

Nothing wrong with dual booting.

---

### Post by jc4gavejc on 2009-09-02
I have a tx2513cl and this line works fine for audio output, but I cannot seem to get the front mic working without tons of crackling and static.

Any suggestions?

---

### Post by Favux on 2009-09-02
Hi jc4gavejc,

Have you tried switching between mic and front mic in Volume Control (Alsa mixer)->options(tab)->input source?

---

### Post by jc4gavejc on 2009-09-03
Yeah, did try that a few times; I plugged in an ext. mic and it worked perfectly. Front mic works great in Windows and openSUSE 11.1...

Maybe I will try to sort this out with just using an external mic though it would be very nice to have the front mic working

Also webcam images appear stretched here when I'm using most apps such as Skype and Pidgin... Pidgin won't even initiate a video chat I'm assuming because of this hardware malfunction..

Webcam image is fine in gstreamer-properties

---

### Post by Favux on 2009-09-03
Hi jc4gavejc,

Well you can look at this and the following page on the TX2500 thread where they talk about dealing with those issues:  [http://ubuntuforums.org/showthread.php?t=845911&highlight=mic&page=52](http://ubuntuforums.org/showthread.php?t=845911&highlight=mic&page=52)  I think they are using Intrepid and you have Jaunty?

---

### Post by jc4gavejc on 2009-09-03
yep I'm on Jaunty could try Intrepid for the time being if necessary, i was actually thinking more about hardy, being a long term release supported longer than Jaunty will be...

---

