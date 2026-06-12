---
title: "Synaptics refuses to co-operate"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by themagicmanfromtrent on 2008-12-22
Hi, I seem to be having a problem with Synaptics Package Manager, which in turn means I am unable to install anything on ubuntu.

Every time I attempt to open it, it asks me for my password, and when I enter my password, nothing happens. It just sits there. I tried exectuting the following code but to no avail:

```
sudo aptitude update
```

I hope someone can help me find out what my problem is.

Danny

---

### Post by SlidingHorn on 2008-12-22
run synaptec from a terminal and post your error results

---

### Post by themagicmanfromtrent on 2008-12-22
```
dannyl@DAN:~$ synaptic
Traceback (most recent call last):
  File "/usr/sbin/update-apt-xapian-index", line 511, in <module>
    lockfd = os.open(XAPIANDBLOCK, os.O_RDWR | os.O_CREAT)
OSError: [Errno 13] Permission denied: '/var/lib/apt-xapian-index/update-lock'

```

I typed synaptic and it worked!:) That's wierd...:confused: The menu button still refuses to work, why would that be?

---

### Post by gerkin on 2008-12-22
you can only run one instance of apt-get/synaptic and I have found that sometimes it locks up and only a reboot will clear it

cheers ..........dave

---

### Post by themagicmanfromtrent on 2008-12-23
Okay, I've rebooted, and although synaptics works when i run it from terminal, I can't install anything through add/remove programs, which is highly frustrating. I get the same error for everything, and it looks similar to my installation of the below codecs:

[IMG]http://img383.imageshack.us/img383/7826/gstreamerie7.png[/IMG]

Any ideas what the problem might be?

---

### Post by jrusso2 on 2008-12-23
> **themagicmanfromtrent said:**
> Okay, I've rebooted, and although synaptics works when i run it from terminal, I can't install anything through add/remove programs, which is highly frustrating. I get the same error for everything, and it looks similar to my installation of the below codecs:

[IMG]http://img383.imageshack.us/img383/7826/gstreamerie7.png[/IMG]

Any ideas what the problem might be?

Try running that in terminal and post the error message.

---

### Post by someoneelse on 2008-12-23
When you run Synaptic from the command line, make sure that you use sudo:

```
someone@yourcomputer>:~$ sudo synaptic
```

That will ensure that you have the permissions to install/upgrade the computer.

---

### Post by themagicmanfromtrent on 2009-01-20
Highly frustrating:

```
dannyl@DAN:~$ sudo apt-get install gstreamer0.10-tools gstreamer0.10-x gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-alsa gstreamer0.10-schroedinger gstreamer0.10-pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-tools is already the newest version.
gstreamer0.10-x is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-schroedinger is already the newest version.
gstreamer0.10-pulseaudio is already the newest version.
The following extra packages will be installed:
  freepats liba52-0.7.4 libavcodec51 libavformat52 libavutil49 libcdaudio1
  libdc1394-22 libdvdnav4 libdvdread3 libfaad0 libfftw3-3 libfreebob0
  libgmyth0 libgsm1 libid3tag0 libiptcdata0 libjack0 libmad0 libmms0
  libmpcdec3 libmpeg2-4 libmysqlclient15off libneon27-gnutls libofa0
  libopenspc0 libpostproc51 libsidplay1 libsoundtouch1c2 libwildmidi0
  mysql-common
Suggested packages:
  libdvdcss2 debhelper fakeroot libfftw3-dev jackd sidplay-base xsidplay
The following NEW packages will be installed:
  freepats gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-ugly liba52-0.7.4 libavcodec51 libavformat52
  libavutil49 libcdaudio1 libdc1394-22 libdvdnav4 libdvdread3 libfaad0
  libfftw3-3 libfreebob0 libgmyth0 libgsm1 libid3tag0 libiptcdata0 libjack0
  libmad0 libmms0 libmpcdec3 libmpeg2-4 libmysqlclient15off libneon27-gnutls
  libofa0 libopenspc0 libpostproc51 libsidplay1 libsoundtouch1c2 libwildmidi0
  mysql-common
0 upgraded, 33 newly installed, 0 to remove and 73 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
dannyl@DAN:~$ 

```

---

### Post by themagicmanfromtrent on 2009-01-20
AHA!, I simply unlocked the directory, and back online :D

Thanks!

---

