---
title: "Sound stopped working (Intel card)"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by mula on 2007-01-11
Hi,

I have a Thinkpad R50e with an integrated Intel sound card. For quite a long time everything has been working without any problems until one day I just didn't have sound anymore. This happened after my system had crashed while reading a scratched CD. Since then, the only sound that Ubuntu Edgy can make is the beep and that annoying thing when you plug-in the battery.
I don't remember to have made any relevant updates either.

While playing multimedia files, I receive no errors. It appears that everything is working flawlessly, it's just that I can't hear it. Furthermore, I've checked and I know that it's not a problem of permissions and the hardware itself works fine. I tried to play with the *alsamixer*: mute, unmute and so on but still nothing...

Do you have any ideas of what else might be wrong with it? :-k 
Just give me a word if you need any further information.

*lspci *output for my soundcard:
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
```

Solution: problem solved by installing gnome-alsamixer and unchecking *Headphone Jack Sense*. For some reason apparently, this can't be done in alsamixer.

---

### Post by DirtDawg on 2007-05-06
After days of [fruitless trial and error]("http://ubuntuforums.org/showthread.php?t=431813"), your post has saved the day. :KS

---

