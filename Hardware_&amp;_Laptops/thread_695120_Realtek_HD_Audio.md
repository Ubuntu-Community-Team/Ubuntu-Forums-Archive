---
title: "Realtek HD Audio"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by msjones on 2008-02-12
Hi,

Can anybody help me?

I have installed 7.10 got my x1650 pro wokring with compiz (sweet desktop!!!) but I cant get my sounds to work?

I am using a realtek HD audio sound card, was working yesterday but after this evening reinstall I cant get it working. I downloaded compiled and installed the HD driver from the realtek website.... nothing?

Thanks

---

### Post by Yellow Pasque on 2008-02-12
What codec are you using? Run:
> cat /proc/asound/card0/codec#* | grep Codec
Maybe try this:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
Or this:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by msjones on 2008-02-12
ok when I run **cat /proc/asound/card0/codec#* | grep Codec** it tell me there is no such file or dir, when I run aplay -l i get [B]aplay: device_list:207: no soundcards found...
[/B]

I followed the second thread and ran the first shell script. This downloaded and installed alsa and asked me to reboot. After reboot i went to run the second scripd and i got a list of cannot find files or dir's....

Anything else?!

---

### Post by msjones on 2008-02-13
Solved!

Just added **options snd-hda-intel model=3stack** into the **/etc/modprobe.d/alsa-base**file

Got sound, got compiz...... running COD4!

---

