---
title: "sound isnt heard"
date: 2008-09-09
forum: Hardware
---

### Post by pariksakurikar on 2008-09-09
I have a lenovo Y410 laptop....players like amarok show that the song is playin but i am unable to hear anythin..
sound works fine on windows...
please help!!

---

### Post by cariboo on 2008-09-09
Double click on the speaker icon in the top panel and make sure that the master volume and pcm controls are turned up.

Jim

---

### Post by pariksakurikar on 2008-09-09
well its turned on but still no sound!!!!:(

---

### Post by eggdeng on 2008-09-09
Open a terminal & copy and paste the following
```
gksudo gedit /etc/modprobe.d/alsa-base
```
This will open an alsa configuration file. Add the line 
```
options snd-hda-intel index=0 model=fujitsu
```
Save and [COLOR="Red"]REBOOT[/COLOR].
This isn't a complete fix but it should give you basic functionality.

---

### Post by ice2921 on 2008-09-09
You may want to try booting with the ```
irqpoll
``` alot of times sound issues are due to shared irq with laptops.

---

