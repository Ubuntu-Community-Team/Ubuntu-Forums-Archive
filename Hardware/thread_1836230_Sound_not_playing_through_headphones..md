---
title: "Sound not playing through headphones."
date: 2011-08-30
forum: Hardware
---

### Post by sjs7007 on 2011-08-30
I have install Ubuntu 10.04 on a Samsung RV-411 notebook.

While it plays sounds via the internal speaker properly,it just gets muted when I connect my headphones to the notebook.

I have updated my ALSA to the latest available build of 1.0.24

I even tried this:

sudo nano /etc/modprobe.d/alsa-base.conf

then adding : 

options snd-hda-intel model=auto position_fix=0

or

options snd-hda-intel model=auto


But neither of them seemed to solve my problem :(

UPDATE: Hey I noticed that while my alsa-base was updated 1.0.24, alsa-utils is still 1.0.22
Its around 390 MB in size,so it will take some time for me to try and install it.



Any idea what to do? Thanks for your help!

---

### Post by Antarctica32 on 2011-08-30
Check this out:
[http://ubuntuforums.org/showthread.php?t=1784867](http://ubuntuforums.org/showthread.php?t=1784867)

I had a problem a little like yours. ask the guy that helped me

---

### Post by wojox on 2011-08-30
Are the headphones muted?

```
alsamixer
```

---

### Post by sjs7007 on 2011-08-31
@Antarctica32: Thanks! 

@wojox:The headphones part doesn't show up in alsamixer. How do you fix this? Thanks neways!

[IMG]http://dl.dropbox.com/u/19182824/alsamixer.png[/IMG]

UPDATE: Hey I noticed that while my alsa-base was updated 1.0.24, alsa-utils is still 1.0.22
Its around 390 MB in size,so it will take some time for me to try and install it.
Once done I'll post the update here.

---

### Post by sjs7007 on 2011-08-31
Hey all,after updating alsa-utils , now my sound is playing fine both through speakers and headphones properly but alsamixer sets my speaker output to zero on rebooting.

Any idea how to fix this?

---

### Post by lidex on 2011-08-31
Set your levels to where you want them, then run this command:
```
sudo alsactl store 0
```
Next reset pulse configuration:
```
rm -r ~/.pulse ~/.pulse-cookie 
```
Reboot. No help? Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

---

### Post by wojox on 2011-08-31
> **sjs7007 said:**
> Hey all,after updating alsa-utils , now my sound is playing fine both through speakers and headphones properly but alsamixer sets my speaker output to zero on rebooting.

Any idea how to fix this?

After you set it run this and see if it saves it:

```
sudo alsactl -f /var/lib/alsa/asound.state store
```

---

### Post by sjs7007 on 2011-09-01
@lidex: You rock \m/ 

Your first method did the trick.

@wojox: I had tried a similar method earlier but it yielded no results.

---

