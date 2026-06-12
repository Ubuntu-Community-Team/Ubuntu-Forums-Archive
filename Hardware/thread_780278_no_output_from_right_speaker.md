---
title: "no output from right speaker"
date: 2008-05-03
forum: Hardware
---

### Post by errenay on 2008-05-03
I have upgraded Kubuntu from 7.10 to 8.04. However, after this I could hear no voice from right speaker of my laptop (Acer 5920G). Changing things with Surround / Master / PCM don't work.
Laptop: Acer 5920 G
ALSA v.1.0.16 (emulation code)
Card config: HDA Intel
Audio devices: ALC 883 Analog (duplex)
Mixers: 0 Realtek ALC888

---

### Post by Zorael on 2008-05-03
Exact same issue and chipset as my system. This should hopefully help you as well.

Open up a text editor with superuser permissions targeting **/etc/modprobe.d/alsa-base**, such as by hitting Alt+F2 to get a run box and entering '**kdesu "kate /etc/modprobe.d/alsa-base"**'. The file should not be empty.

Scroll down to the end and add the following line.
```
options snd-hda-intel model=acer
```

Then restart sound and see if it works.
```
$ sudo /etc/init.d/alsa-utils restart
```


There's another thread here on the first page about the same issue, though with another chipset.

---

### Post by errenay on 2008-05-03
Sorry, but it didn't work... :(
BTW - Thank you for the help!

---

### Post by errenay on 2008-05-04
After some time with some changes in alsa-base right speaker automagically works...:confused:
I do not know how it has happened. I have changed last line in alsa-base to
```
options snd-hda-intel index=0 model=acer
```
```
options snd-hda-intel index=0 model=acer-aspire
```
then restarted. No sound. Change back to model=acer, use alsamixer to unmute all possible outputs (Center, Surround, PCM, etc.). Now it looks like working...?

---

### Post by Zorael on 2008-05-04
Try any of the models at [http://ubuntuforums.org/showthread.php?p=4869649#post4869649](http://ubuntuforums.org/showthread.php?p=4869649#post4869649). Notably the ones under the ALC888 header.

I'm also not sure if you merely need to restart alsa-utils or if you need to restart the snd_hda_intel module. Perhaps doing both would cover it all.
```
$ sudo /etc/init.d/alsa-utils stop
$ sudo modprobe -r snd_hda_intel
$ sudo modprobe snd_hda_intel
$ sudo /etc/init.d/alsa-utils start
```

---

### Post by imsushantjain on 2011-06-26
HI Friends,

I have installed Ubuntu 11.04 on Acer 5742Z and i am facing the similar problem.
Please help.:confused::(

[http://ubuntuforums.org/showthread.php?t=1790902](http://ubuntuforums.org/showthread.php?t=1790902)

---

