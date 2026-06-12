---
title: "headphone jack and mic not working"
date: 2008-09-10
forum: Hardware
---

### Post by kriml0n on 2008-09-10
Hello I am running ubuntu 8.04 on a Sony Vaio vgn-fz430e laptop. I am getting sound through my speakers but i am not able to get sound through the headphone jack and microphone are not working. I have searched and tried other driver installations but none have worked yet. Any suggestions would be much appreciated.

---

### Post by Sam Lars on 2008-10-15
Are you using Hardy or Intrepid?  You could give Intrepid a try, at least from the LiveCD, to see if that works.
Also, check out this guide.
[http://ubuntuforums.org/showthread.php?t=385739&highlight=microphone+jack](http://ubuntuforums.org/showthread.php?t=385739&highlight=microphone+jack)

---

### Post by markbuntu on 2008-10-15
Here are a bunch of links to help for that. Your most likely solution would be the vaio or auto option. How to do that is in the links.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)


[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by Mr Goode on 2009-03-07
Hello, this worked great with my vaio fz19vn.
I found this solution in the forums.

update your repository list then run in a terminal:

sudo apt-get install linux-backports-modules-generic

sudo gedit /etc/modprobe.d/alsa-base

be carefull now. you are editing a file which only root has access to.
just add at the end of this file in a new line

options snd-hda-intel model=vaio

now reboot and cross your fingers

---

### Post by Mr Goode on 2009-03-07
I forgot one thing:
Do this first, got to 
System  -  administration  -  software sources
and click the "Unsupported updates (intrepid-backports)" box

---

### Post by Klarinet on 2009-03-24
@Mr Goode
thanks for this!
I can finally listen music with my headphone!

---

