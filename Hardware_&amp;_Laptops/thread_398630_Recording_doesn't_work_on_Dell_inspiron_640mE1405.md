---
title: "Recording doesn't work on Dell inspiron 640m/E1405"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by nadav2605 on 2007-04-01
Hello, i have a dell inspiron E1405/640m (which is exactly like the 6400/E1505 but with a smaller screen).
It has a sigmatel audio chip and i think it's called stac92xx by the device manager. anyway, audio playback works just fine but recording from a microphone doesn't work at all.
I'm using Edgy. what sould i do?

Thanks!

---

### Post by jjalocha on 2007-04-08
I have the same card on a [Latitude 131L notebook]("http://ubuntuforums.org/showthread.php?t=367898"). In my case, sound works right out of the box. Microphone input didn't work always, specially when using skype. Try the following (weird) workaround (case sensitive) that solved it for me:

```

$ amixer set "Input Source" Line
$ amixer set "Input Source" Mic

```

If switching those in that order fixes the problem, you can make the change permanent in your /etc/rc.local file. Just put the following before exit 0:

```

/usr/bin/amixer set "Input Source" Line
/usr/bin/amixer set "Input Source" Mic

```

---

### Post by Pcniatic on 2007-04-09
I had the same problem in the same notebook(Dell 640m). I solved this problem installing the last version of the alsa driver following [this howto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").
Hope it works for you too. :-D

---

### Post by emmajane on 2007-05-29
When I try the code that is pasted above (at the command line) I get the following error:
amixer: Invalid command!

---

