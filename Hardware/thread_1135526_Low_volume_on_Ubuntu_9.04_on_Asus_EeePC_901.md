---
title: "Low volume on Ubuntu 9.04 on Asus EeePC 901"
date: 2009-04-24
forum: Hardware
---

### Post by andy80 on 2009-04-24
I've installed Ubuntu 9.04 (Jaunty) on my Asus EeePC 901 and all is working fine except audio.

Volume is really low compared to Ubuntu 8.10 I had installed before.

I've tried to increase the volume using Gnome Volume Applet, gnome-alsamixer, alsamixer (from console) but nothing to do: even if volume is at maximum value, it's still very very low :(

Is there any way to fix this problem? Do you need more information to help me? Thanks for your support!

p.s: my /home/ folder is the same I used in Ubuntu 8.10.... maybe a wrong setting I'm using?! I try to create a new user...

---

### Post by kanikilu on 2009-04-24
Are you sure your master *and* PCM volumes are turned up in alsamixer?

---

### Post by andy80 on 2009-04-24
> **kanikilu said:**
> Are you sure your master *and* PCM volumes are turned up in alsamixer?

Yes, they're all UP. I'm starting to think it's a problem related to this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/325215](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/325215)

submitted 2 months ago and still not assigned..... I think I'll switch back to Ubuntu 8.10 on my EeePC!

---

### Post by crav on 2009-04-24
In that bug report, the poster mentions using pulse audio to crank the gain up to 400%. Does this at the very least make things louder?

I understand that turning up gain reduces sound quality, but I'm using this on me Eee, so sound quality isn't much of a concern.

How can I get to that pulseaudio interface?

---

### Post by jiffyjeff on 2009-04-26
You can install PulseAudio Manager by installing and running 'paman':

sudo apt-get install paman

paman

Then, click no the Devices tab, and select your ALSA device.  Click Properties.  You can increase the volume here.  However, note that you may experience audio clipping at higher settings.  It may be beneficial to have something playing while you are making the changes.

In any case, this is a hack to work around a bug in 9.04.

---

### Post by geoflyer on 2009-04-28
i'm having the same low volume problem with my eeepc1000. I haven't tried the workaround yet but when i rebooted into windowsxp  i realized the volume was set at about the 50% level. Could this have an effect on the Ubuntu install volume level?

---

### Post by zapher67 on 2009-04-30
I found this fix which I applied to to my Ubuntu 9.04 on me EeePC 901 which worked much better than the Pulse solution. Volume is now acceptable.

Here is the original post
[http://andreeleidenfrost.blogspot.com/2008/11/eeepc-901-with-ubuntu-intrepid-ibex.html](http://andreeleidenfrost.blogspot.com/2008/11/eeepc-901-with-ubuntu-intrepid-ibex.html)

Here is the fix

Also, the sound volume was very low. Appending the following to /etc/modprobe.d/alsa-base fixed this: **options snd-hda-intel model=auto**

zapher67.

---

### Post by Niuginibenz on 2009-06-22
I found this in another post and it fixed my low  volume on 901 with Jaunty. Open the volume control. You will see PCM and LineOut. Set them BOTH to MAX and it should solve your problem.

---

### Post by sosafan1 on 2009-07-28
> **zapher67 said:**
> Appending the following to /etc/modprobe.d/alsa-base fixed this: **options snd-hda-intel model=auto**

zapher67.

This worked for me as well.
Also, I'll add, for newbies like myself, that you'll need to open the file with sudo or it won't let you save.

sudo gedit /etc/modprobe.d/alsa-base.conf

Then add **options snd-hda-intel model=auto** to the bottom and save.

The first time I tried this with gedit it wouldn't save for me so I actually used:

sudo nano /etc/modprobe.d/alsa-base.conf

This is my first post to the Ubuntu forum and just wanted to say thanks for all the help you've all given to ME.

---

### Post by giyad on 2009-11-18
I was having the same problem but I was able to solve it by going into the volume control and raising the control of "Front".  It was really annoying but I finally got that fixed :)

---

