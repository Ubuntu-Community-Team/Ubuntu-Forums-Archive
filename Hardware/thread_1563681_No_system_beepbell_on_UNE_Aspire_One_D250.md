---
title: "No system beep/bell on UNE Aspire One D250"
date: 2010-08-29
forum: Hardware
---

### Post by narnie on 2010-08-29
Hello,

I'm trying to enable my system beep on my Aspire One D250 running UNE (10.04).

I have enabled audible bell in gconf-editor at /apps/metacity/general/audible_bell

I have the bell enable in gnome-terminal

I have bell enabled in ccsm (compiz settings manager).

I have system sounds enabled on gnome-volume-control

I have:```
sudo modprobe pcspkr
```

I have the "visual beep" working, but the audio does not.

Any ideas?

Thanks,
Narnie

---

### Post by narnie on 2010-08-29
Well, I'm not sure if I have a system speaker on this netbook. I'm guessing that I probably don't.

As a work-around, I found a link ([http://superuser.com/questions/22767/enable-system-beep-in-ubuntu]("http://superuser.com/questions/22767/enable-system-beep-in-ubuntu"))

Essentially, install vorbis-tools to get a beep sound and command line tool ogg123:

```
sudo aptitude install vorbis-tools

```

Then do:

```
mkdir ~/.xkb
nano ~/.xkb/xkbevd.cf
```

putting this in the file:

> soundDirectory="/usr/share/sounds/"
soundCmd="ogg123 -q"

Bell() "ubuntu/stereo/bell.ogg"


Then run:

```
xkbevd -bg
```


(btw, the -bg is for "background" which starts it as a daemon)

Then start it up at every boot by configuring gnome-session-properties or put it in your .profile by running :

```
echo <<EOF >> ~/.profile
if [ -n "$DISPLAY" ]; then
  xkbevd -bg
fi
EOF

```

Hope this helps someone,
Narnie

---

### Post by FlameLicker on 2010-09-08
... yes, thanks. I had the same problem with a HP 530 Notebook PC. Probably your post spared me a lot of time. Cheers!

---

### Post by narnie on 2010-09-08
> **FlameLicker said:**
> ... yes, thanks. I had the same problem with a HP 530 Notebook PC. Probably your post spared me a lot of time. Cheers!

Glad to hear it. I like getting help, but I really enjoy giving it much more! I always try to post solutions when I find them if I beat someone else to it.

Thanks for the encouragement.

Narnie

---

### Post by honeybear on 2010-11-27
> **narnie said:**
> Well, I'm not sure if I have a system speaker on this netbook. I'm guessing that I probably don't.

As a work-around, I found a link ([http://superuser.com/questions/22767/enable-system-beep-in-ubuntu]("http://superuser.com/questions/22767/enable-system-beep-in-ubuntu"))

Essentially, install vorbis-tools to get a beep sound and command line tool ogg123:

```
sudo aptitude install vorbis-tools

```

Then do:

```
mkdir ~/.xkb
nano ~/.xkb/xkbevd.cf
```

putting this in the file:



Then run:

```
xkbevd -bg
```


(btw, the -bg is for "background" which starts it as a daemon)

Then start it up at every boot by configuring gnome-session-properties or put it in your .profile by running :

```
echo <<EOF >> ~/.profile
if [ -n "$DISPLAY" ]; then
  xkbevd -bg
fi
EOF

```

Hope this helps someone,
Narnie
#


but you could use : 

xbelld 

  Using xbelld

If you don't have a PC speaker (or simply want to customise it beyond your hardware limitations), then you can try using xbelld. This can emulate the PC speaker beep via your sound card (using ALSA) , and let you adjust the volume, frequency and duration. (It can also natively play WAVE files, or run an external command if you so desire).

Unfortunately xbelld is not yet in portage (2008-04-13). But I have submitted an ebuild here. Now once you've emerged xbelld (preferably with the alsa USE flag), put

xbelld -bt50 -F400 -v127 -d100

in ~/.xinitrc. You can control the duration, frequency and volume using the -d, -F and -v options. Alternately you can play WAVE files, or execute external programs using the following forms:

xbelld -bcf beep.wav
xbelld -be aplay -q beep.wav

See

man xbelld

for a complete list of options.

---

