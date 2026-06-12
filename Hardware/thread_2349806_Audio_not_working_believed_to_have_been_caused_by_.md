---
title: "Audio not working believed to have been caused by bug &gt;(1574079)"
date: 2017-01-18
forum: Hardware
---

### Post by dorag on 2017-01-18
Hello i'm completely new to Linux and the Ubuntu distro and i'm facing a problem where my sound drivers don't work at all after one of the updates and i believe it has been caused by this bug [https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1574079](https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1574079) 
I'm using a Logitech G930 Wireless version.

The audio and mic did previously work via usb and via 3.5mm jack

Please see my system spec at this link [http://pastebin.com/SEFMvJDq](http://pastebin.com/SEFMvJDq)

**Please can someone help me Thank you **


This is what i posted on Bugs.launchpad.net......

[COLOR=#333333][FONT=monospace]My Usb Audio is still not working i'm new to ubuntu so unsure how to fix it Please can someone help me[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I'm using a Logitech G930 Headset - Wireless Usb Version.
I'm running Ubuntu 16.10 Xenial
I'm Using a Dell Optiplex 755 DT Please see specs AT THIS LINK [http://pastebin.com/SEFMvJDq](http://pastebin.com/SEFMvJDq)
Ubuntu Software Centre Says that everything is up to date[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]System Settings >> Sound >> Output / Imput - No sound devices found not even integrated sound card[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]w.w.w.p.a.s.t.e.b.i.n.c.o.m./.S.E.F.M.v.J.D.q.
REMOVE ALL THE DOTS APART FROM WWW. AND .COM[/FONT][/COLOR]

---

### Post by gdesilva on 2017-01-18
You have 3 audio devices, Intel, nVidia and USB Audio. I would go into the Audio Settings and make sure that your default device is Logitech G930 to start with.

---

### Post by dorag on 2017-01-19
I'd love to but no devices show under the audio settings they have all Disappeared

---

### Post by wildmanne39 on 2017-01-19
*Thread moved to **Hardware**.*

---

### Post by dorag on 2017-01-19
All input devices and output are blank they show no devices to select in the sound box

---

### Post by dorag on 2017-01-19
> **gdesilva said:**
> You have 3 audio devices, Intel, nVidia and USB Audio. I would go into the Audio Settings and make sure that your default device is Logitech G930 to start with.

Do you have any other ideas?:p Thanks for your help up to now

---

### Post by dorag on 2017-01-19
Do you have any ideas Wildmanne39 seems your running the same distro Thanks :P

---

### Post by wildmanne39 on 2017-01-19
> **dorag said:**
> Do you have any ideas Wildmanne39 seems your running the same distro Thanks :P
No I do not, I have not had any issues with my sound and I usually only help with wireless issues when time permits.

Give people time so see your post I am sure someone will have an idea, you can bump your post once every twelve hours to keep it in view.

---

### Post by gdesilva on 2017-01-19
Would be good to see the output of 'alsamixer' and also of 'cat /proc/asound/cards' and 'cat /proc/asound/devices'

---

