---
title: "Can't play DVDs which worked in Windows"
date: 2008-10-20
forum: Hardware
---

### Post by Jepperen on 2008-10-20
Hey

My girlfriend have a DVD boxset with Sex And the City. My laptop had no problem playing them, when i had Windows XP installed. Now i installed Ubuntu and it can't read the DVDs, or play them at least. Because i can browse to DVD drive and see the AUDIO and VIDEO folders on the DVD, but it cant play. There is no problems with playing ohter DVD movies.

I tried many different software videoplayers for Ubuntu, but none works.

An additional information, is that my Xbox 360 cant play the DVDs either. Hmm...

Anyone who can come up the a solution for this?

---

### Post by Afkpuz on 2008-10-20
Even in windows, you must install somethings before you can watch DVDs.  The same is true for ubuntu. Assuming you're using hardy heron...


 First, you need to install libdvdcss2- Know that this is illegal in the U.S. because of copy write laws.  Thanks movie companies!  Here is the 32 bit version.
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)


Then, you'll need a better dvd player because totem is really flaky.  So, I recommend vlc.  Put this into the command line

```
sudo apt-get install vlc
```

Then reboot and try watching in vlc.  xine is also a decent player, but tends to lock up more often than vlc

---

### Post by teaker1s on 2008-10-20
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

if drive is new then you will need regionset for some dvd's

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by Jepperen on 2008-10-21
Thank you both for your answers. Afkpuz solution worked for me! :D

It isnt a new drive, but i will keep your post in mind when i install Ubuntu on my ohter computer, teaker1s :).

---

### Post by teaker1s on 2008-10-21
your welcome:popcorn:

---

