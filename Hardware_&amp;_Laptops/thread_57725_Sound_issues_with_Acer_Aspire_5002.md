---
title: "Sound issues with Acer Aspire 5002"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by luisfpg on 2005-08-17
Hi All!!!
I'm having some issues with sound on my Acer Aspire 5002.
The sound board identifies itself as just as "Silicom Integrated Sistems" on lspci, but the Acer driver download page says it's a Realtek AC'97 sound board.
I've installed Ubuntu 5.04. 
The Enlightment Sound System works ok, but when I try to use OSS, the application hangs and has to be manually killed, and when I try to use ALSA, I always get an exception saying a resource is busy, even if there's no other process using sound...
Can someone help me configuring OSS and ALSA?
I can use XMMS anyway with eSound output plugin, but I want to figure out why ALSA and OSS are not working...
Thanks in advance.

---

### Post by firecat53 on 2005-08-18
Hey...first go through and follow the instructions in the[Ubuntu Beginner's Guide](http://ubuntuforums.org/showthread.php?t=23368) for making sound work. 

If that doesn't work for you, try installing  polypaudio.  It replaces ESD and worked for me in fixing some problems I had with sound following a suspend.

Good luck!! Scott

---

