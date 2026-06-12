---
title: "Sound won't work on new install"
date: 2009-11-04
forum: Hardware
---

### Post by abefroman99 on 2009-11-04
I am running a new install Kubuntu 9.10 on a new comp

/etc$ lspci |grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

And have no sound.

And ideas?

TIA

---

### Post by Paul D on 2009-11-04
I am no help for you because I am having the same problem with different sound card.
Google searches show many examples of this kind of problem. The examples only kind of help. Here is one  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[SIZE=2]aplay -l[/SIZE]shows the cards and so-on. I have yet to see an explanation of something straight forward. I mean, 1) system needs to recognize sound hardware, 2) driver for that hardware needed - find driver name at some website. 3) open a file on your system using a text editor and add such command so it will load every time you bootup. 4) Here is where is am lost - Do I need some codec file - If so how do I install that? Why are there multiple sound mixers or controls? There is alsa, jack panel, oss something, and I don't know which to use. Do I need to patch something in Jack> I don't know. If I use audacity do I use which mixer and does it matter? I am trying to use this ubunu.linux deal, but my patience will run out in two weeks. If I can't get this going by then I may have to sadly turn back to XP. I can't spend my life messing with this system.

Once I get the soundcard working (Assuming I do), next is networking issue seeing my other computers on my XP network. Also my CD drive does not seem to acknowledge a music CD when I put it in.

---

