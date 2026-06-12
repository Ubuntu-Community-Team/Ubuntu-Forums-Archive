---
title: "amaroK says dcopserver not running on launch"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by daibak on 2005-12-22
I only have GNOME installed with kernel 2.6.12-10-386 and to add MP3 playback ability to amaroK 1.3 I followed instructions in Breezy Badger 5.10 [RestrictedFormats wiki page]("https://wiki.ubuntu.com/RestrictedFormats"), where it says under Playing Non-Free Media
[HTML]If you live in a country where it is legal to play MP3s and other non-free media formats without a license,  enable the universe and multiverse repositories, and install the support packages by typing in a terminal:[/HTML]
```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
```

and ended up with this DCOP communications error window (amaroK) once terminal install completed and I had launched amaroK:

```

There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/david/.DCOPserver_ubuntu_0

Please check that the "dcopserver" program is running!   OK button
```

I'm clueless what to do here - how do I find out if dcopserver is running?
Do I need to install KDE as well as GNOME? Any tips greatly appreciated.
Meanwhile XMMS 1.2.10 playing MP3s just fine.

TIA to all.

---

### Post by daibak on 2005-12-22
amaroK 1.3.1 (using KDE 3.4.3) now playing a Radio Streamed Mozart sonata. First time I've heard exquisite streamed audio on this HP Pavilion in three years.

Here's what I found on another thread in the Ubuntu Forums (thanks to [adrianhensler]("http://ubuntuforums.org/showthread.php?t=97768&highlight=dcopserver")) is what you type in a Breezy Badger terminal window:

```
myusername@ubuntu:~$ sudo chown -R myusername:myusername /home/myusername/.*
Password:
```

as, according to adrianhensler above, root had ended up owning a bunch of ./kde files; so the user was not getting correct access. amaroK 1.3.1 launched first go.

Oh, if all Linux troubles were so simple to solve for this Windows graybeard and Ubuntu fan!

---

### Post by Ibbelz on 2006-01-02
Ah, nice one. Thank you very much for that solution! It did the trick for me. Klibido also gave errors, but this also fixed that problem. :)

---

### Post by charlieg on 2006-01-05
Great tip, fixed my issues trying to run amaroK in Gnome.  It is so nice to use, I wish Rhythmbox / Banshee would catch up.

---

### Post by eXume on 2006-11-16
This is one of the reasons im loving open software.
If you have a problem its already been written about and fixed in publicly open forums.

Awesome!!!!

---

### Post by szxuzhou on 2007-02-28
Thank you very much! I have searched how to fix this problem since last weekend.

---

### Post by dark_diablo_01 on 2007-03-02
what if we get an error trying to sudo, for me it says unable to lookup Diablo OS via gethostbyname()

---

### Post by bingnet on 2007-05-16
I have encountered this error verbatim while trying to launch KDE Guarddog (firewall). CHOWN my home directory did not resolve this. Gaurddog still runs with ancient gnome-like window decoration.

---

### Post by d3X7eR` on 2008-06-07
Thank you so much i've been looking for a solution for hours!!:guitar:

---

