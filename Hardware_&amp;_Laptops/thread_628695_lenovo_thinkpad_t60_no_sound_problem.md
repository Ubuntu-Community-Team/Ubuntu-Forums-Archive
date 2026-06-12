---
title: "lenovo thinkpad t60 no sound problem"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by Matt Z on 2007-12-01
Hi. I'm trying to enable sound on my Lenovo Thinkpad T60 laptop.
I've installed alsa 1.15 following this instructions:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

but i don't have /etc/modprobe.d/alsa-base file, 
since i don't have alsa-base installed

I've also red:
[http://ubuntuforums.org/showthread.php?t=246070](http://ubuntuforums.org/showthread.php?t=246070)
and 
[http://ubuntuforums.org/showthread.php?t=607438](http://ubuntuforums.org/showthread.php?t=607438)

but it didn't help me.

my modem device is enabled.

alsaconfig finished with success

```

  Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!

```


my /etc/modprobe.d/sound file:
```
cat /etc/modprobe.d/sound 
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
```

What do I have to do to enable sound in my Lenovo T60 laptop?

---

