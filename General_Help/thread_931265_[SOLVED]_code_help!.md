---
title: "[SOLVED] code help?!"
date: 2008-09-27
forum: General Help
---

### Post by L4S7 on 2008-09-27
Please help i have no idea how to enter this code? i know i go into Terminal but i type it in and not getting any good results.



> Try adding two lines to /etc/modprobe.d/alsa-base

```

options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-inte
```l

It works for me.

just some help on what he means by adding two lines? 

Please help


got this from this thread

[http://ubuntuforums.org/showthread.php?p=4780395#post4780395](http://ubuntuforums.org/showthread.php?p=4780395#post4780395)

---

### Post by iaculallad on 2008-09-27
In your terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base
```

then add the lines of text below on the last part of the file:

> options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel


Save and Close the file.

---

### Post by L4S7 on 2008-09-27
Thanks so much, sorry so new to this code thing.

---

