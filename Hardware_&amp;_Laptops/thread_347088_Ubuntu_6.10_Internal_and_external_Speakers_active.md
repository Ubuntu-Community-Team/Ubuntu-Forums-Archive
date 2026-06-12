---
title: "Ubuntu 6.10: Internal and external Speakers active"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by klofisch on 2007-01-26
Hello,

when i plug my external Speakers to my Notebook (LG T1) the internal dont turn off.

What can i do to solve this problem??


thanks
Peter

---

### Post by eggdeng on 2007-01-26
Assuming your soundcard is an Intel HDA model, you probably need to configure alsa with a specific option for it to route sound properly on your laptop. 
You can do this by opening the appropriate configuration file with root privileges in your text editor, if you are using gedit -
```
sudo gedit /etc/modprobe.d/alsa-base
```
and adding the line
```
options snd-hda-intel model=lg
```

---

### Post by klofisch on 2007-01-27
Great. This also solved my problem with the jotkey for volume control.


Thanks.

---

### Post by andradx on 2008-03-03
Bit of a bump here...but I'd mostly appreciate if you could help me out.

I have a LG laptop E500 with an Intel HDA ALC883
I'm using Ubuntu 7.10

I've added the line to the alsa-base specifying lg

options snd-hda-intel model=lg

And still speakers don't turn off when i plug in headphones

---

