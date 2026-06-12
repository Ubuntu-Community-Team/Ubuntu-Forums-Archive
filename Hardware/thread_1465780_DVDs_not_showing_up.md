---
title: "DVDs not showing up"
date: 2010-04-29
forum: Hardware
---

### Post by keljaden on 2010-04-29
DVD's and CD's do not show up when I put them in...

If I reboot and they are in the drive, it works, but once I boot in, if I put a movie in, it won't show up.  Help, I really need this to work.

---

### Post by 2hot6ft2 on 2010-04-29
You need codecs to play dvd's
Open konsole
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```then for the codec for decrypting dvd's```
sudo apt-get install libdvdcss2
```
That's it. Put your dvd in and enjoy.

---

### Post by keljaden on 2010-04-29
I already have the medibuntu stuff installed... Like nothing I put in my optical drive mounts. (like i don't have the option to mount it)

The KDE device thing doesn't pop up saying "anything.  Like if I put a blank CD-R in there it doesn't show up either.

---

