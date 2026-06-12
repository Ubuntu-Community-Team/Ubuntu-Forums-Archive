---
title: "No Sound on my Laptop (Jaunty)"
date: 2009-04-27
forum: Hardware
---

### Post by Rainfire on 2009-04-27
Last night I just installed Ubuntu 9.04. I must say, as a first time Linux user it has so far made me happy. I've had a couple of small issues but nothing I haven't been able to work out. I'm definitely going to stay a Linux User now. 

However, I do have one issue that worries me, considering I love my music. I am not getting any sound from my laptop/speakers (I have external speakers as well as the ones on my book). The only sound I've been getting is this increasingly loud thumping noise on the Externals. I know very little so far about Linux but any help would be appreciated! 

Thanks. 

(Note: If this has already been discussed/fixed, please direct me to the right place because I can't find anything on it.)

---

### Post by Kidney on 2009-04-27
No sound on my Acer 6920G.
It's like people say that linux is better than windows.For basic users like me - I don't think so.When Linux is installed on Desktop PC or Laptop you need to do bunch of things to make it work as well.And ot Jaunty there are still things to be fixed - like sound issue on Acer laptops.Ubuntu needs to be like this - fresh installed - just have to install some drivers and to be ready to use - than I'll say that It's better than windows.

---

### Post by brunogirin on 2009-04-27
Have a look at [the community article about troubleshooting sound issues]("https://help.ubuntu.com/community/SoundTroubleshooting"). If you have a problem with any of the steps in there, ask in this thread.

---

### Post by dream_coder on 2009-05-08
already solved if you search the forums it would avoid dupilcate posts all the time.

[http://ubuntuforums.org/showthread.php?t=1013750&highlight=6920g+sound](http://ubuntuforums.org/showthread.php?t=1013750&highlight=6920g+sound)

Hint:  instead of modprobe.d/alsa-base with jaunty it is now modprobe.d/alsa-base.conf - Just remeber this when you follow the guide and you will go far my friend.


Also alot of people had success using this on top of that the guide tells you to do- [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) just install the .deb and reboot after you have followed the guide.

I just updated to Latest snapshot alsa-driver also and volume quality if far superior :)

---

### Post by raymondh on 2009-05-08
> **dream_coder said:**
> 

Hint:   with jaunty it is now modprobe.d/alsa-base.conf - 

so true, so true :)

---

