---
title: "Most stupid error ever."
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by Havoc on 2006-11-06
Well, to make a long story short, I rebooted 30 minutes ago, and found that my sound card was not recognised by gstreamer, or something to that effect. So I opened up a console to see what's wrong, and learned so right off the bat, as I would say. Well, now, the system beep comes through my speakers. And unless my music constitutes of carefully placed beeps, I won't be able to listen to it. 

I really can't care hard enough to fix it, but I think this experience was worthwhile enough to post over here. Shoulda posted somewhere in the Cafe, now that I think of it.

Have a nice Ubuntu day! :cool:

---

### Post by po0f on 2006-11-06
Havoc,

```
$ sudo modprobe -r pcspkr
```

And then, as root, edit /etc/modprobe.d/blacklist and append a line similar to the following:
```
$ gksu gedit /etc/modprobe.d/blacklist
# add the line "blacklist pcspkr" to the bottom, save and exit
```

---

### Post by Havoc on 2006-11-06
I don't know if removing the pcspkr module will do anything, but thanks. I'm downloading something now, and can't reboot as of yet, so I'll just append some more data, even if the problem is already fixed.

First of all, udev has not even created a /dev/dsp device node... Furthermore, ALSA gives me problems about not beeing able to find the card. I bet a reboot will fix this whole thing.

Still, it's pretty ridiculous. I mean, system beeps? I get enough of those whilst playing 80s DOS games.

Anyways, thanks for the help once again,poOf. ;)

---

### Post by Havoc on 2006-11-06
Well, the pcspkr was not the culprit, as expected. The real reason for this whole mess was because I overclocked my CPU a little bit more.

I'm not kidding :neutral: I overclocked my P4 2.4MHZ CPU from 2.8 to 3.0 mhz to see if it would run nicely (It did), and the problem came up. I clocked it down again, and the problem is fixed.

These machines never fail to amuse me.

---

