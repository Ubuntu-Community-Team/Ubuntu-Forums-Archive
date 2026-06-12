---
title: "Any one able to help me? Update manager just trashed my system!"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by matheuu on 2007-08-31
Update Manager just down loaded a few items and now gstreamer, any media player will not work and I seem to have lost alsamixer and got no sound. All just happened....

---

### Post by Lord Illidan on 2007-08-31
You didn't by any chance noticed what it downloaded?

---

### Post by matheuu on 2007-08-31
NAh . just hit the icon ...actually .... I thinks it was headers?
maybe?
damn I knoe I shulda looked at it....

---

### Post by holiday on 2007-08-31
There's a problem with sound that Ubuntu is working on. It's pretty much screwed up right now, but I'm sticking with them. If I was smarter I'd help out, but I know I'd just take up airtime.

In the meantime....   oh dear .....  there are some good diagnostic guides (if you're into it, they're very good) 

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)
and
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It's a bit of work, and doesn't fit with a party night, but after a few bewildered hours I managed to get my sound working again. This was after the upgrade to Feisty. 

You're a bit of a ride,  Linux. I wonder if we'll ever sort you all out. 

Maybe I hope not.

---

### Post by nowshining on 2007-09-01
did you happen to try updating the feisty kernel to the gutsy kernel earlier??

---

### Post by MrDexterity on 2007-09-01
I've lost my sound too after todays update.

sudo modprobe snd-hda-intel WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by nowshining on 2007-09-01
what did you guys update : Regular FEISTY UPDATES or  DID ANY OF YOU TRY UPDATING THE KERNEL AS SPECIFIED IN A HOW TO THREAD? and DID YOU forget to remove the Gutsy update repository ?? I haven't myself but I KNOW WHAT I AM DONG when I update things that in the Gutsy repositories and if you forget to remove it well then AUTO updates will manage it and trash you up..

My tip: Don't do automatic updates do them manually each time so that way this doesn't happen to you and you KNOW what is downloading.. geest!

---

### Post by MrDexterity on 2007-09-01
I updated using regular updates, no custom kernel upgrade and I'm most certainly  not using the gutsy repository

---

### Post by Lord Illidan on 2007-09-01
If you upgraded your kernel, chances are that alsa has to be reinstalled..

---

### Post by E_K on 2007-09-03
same thing happened to me, i just re installed :P and wont do updates :P

---

### Post by MrDexterity on 2007-09-03
I just reinstalled the latest alsa driver from source and got it running again.

---

### Post by E_K on 2007-09-04
yeh now i feel dumb, should of thought of that, i also got to resize my swap partition, and get rid of some junk i had on there while i was at it though :P

---

### Post by Mize on 2007-09-04
Okay, this AM's update (new kernel headers) busted sound on my HP nc8430 laptop too :(
"Reinstalling" ALSA base in synaptic didn't help. Any ideas? No devices detected it tells me. Is there any way to simply roll back updates in reverse chronological order?

---

### Post by Mize on 2007-09-04
I tried a complete purge of all alsa-relateds and reinstall and no-go. My old kernel (2.6.20-15-generic) works fine so it must be the header updates from this AM that killed my sound. No time to reinstall from source at the moment...later.

---

### Post by Mize on 2007-09-04
I fixed it with help from this thread:

[http://ubuntuforums.org/showthread.php?t=540296](http://ubuntuforums.org/showthread.php?t=540296)

Not sure why my manual source install didn't work :( oh well, it's working now:

wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
tar xvf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure --with-oss=yes --with-cards=hda-intel
sudo make
sudo make install
sudo modprobe snd-hda-intel
/etc/init.d/alsasound restart

---

### Post by skier on 2007-09-04
I have a Thinkpad X61 and the recent updates caused me to lose sound and the two USB ports on the right (one on left worked fine).  

I Recompiled the alsa drivers and rebooted and it was fixed...

---

