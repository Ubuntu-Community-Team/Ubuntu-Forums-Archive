---
title: "Software install problem"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by yildiz.a on 2009-03-20
Hi,

I have problems with installing and upgrading software. I use Ubuntu 7.10.

But I can't install anything. I can't even listen mp3 files. What should I 

do? What is the matter? If anyone can help me, I appreciated.

---

### Post by taurus on 2009-03-20
Try running these two commands from a terminal, one at a time to install media codecs.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by buixuanduong1983 on 2009-03-20
What software you want to install? How you do it? What error message you get?
Because mp3 is a property format so if you only install a fresh Ubuntu without any other codec then you cannot play mp3. Try to play the audio file in Examples folder to see if your sound card are working.
Btw, now we already had Ubuntu 8.10, try it.
Try to suply more information then many nice people here will help you.
Good luck!

---

### Post by yildiz.a on 2009-03-20
I done with playing mp3's but this time I couldn't run avi files. Because when I want to install an applet or whatever it is via synaptic package manager, an error message is given to screen about dependicies. I don't understand.

---

### Post by taurus on 2009-03-20
What are the outputs of these two commands from a terminal.  Make sure you close down synaptic first though.

```
sudo apt-get update
sudo apt-get upgrade
```

---

