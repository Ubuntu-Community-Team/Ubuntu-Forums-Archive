---
title: "How do I get MythTV  (or Ubuntu) to detect my DVB-T TV card?"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by gusjones on 2005-09-09
Left over from my windows days I have a digital TV card in my PC.

Recently after browsing the net I became aware that there are Linux drivers out there for it. I installed Myth TV and TVtime from Synaptic, but neither automatically pick up my **AverTV 761 DVB-T** television card.

I am a newbie when it comes to things like MythTV but following the instructions I managed to run the mythtv backend, but I simply could not get the backend interface to pick up that my card even exists.

When I run TVtime it complaines about there being no input signal, which I suspect is down to not detecting the card as I have pretty good freeview terestrial reception.

Any helpful comments, solutions or pointing in the right direction would be gratefully appreciated.

 :???:

---

### Post by tonym on 2005-09-28
This may help.  Or may not!  See my post at the end.

[http://www.ubuntuforums.org/showthread.php?t=64164](http://www.ubuntuforums.org/showthread.php?t=64164)

---

### Post by gusjones on 2005-09-29
This doesn't sound too desperately hard!
So I will give it a try and let you know how things go.

---

### Post by Joshua on 2005-10-04
[QUOTE=gusjones]This doesn't sound too desperately hard!
So I will give it a try and let you know how things go.[/QUOTE]
I was curious as to whether you got it to work.  I found this helpful:

[http://www.abarbaccia.com](http://www.abarbaccia.com)

Also, two things that took me forever to figure out (with a pcHDTV 3000 card):
- Using Breezy gives you the benefits of a 2.6.12 kernel.  ie. the DVB drivers are built in.
- You need to select DVB as your card type during configuration.
- I needed to copy firmware files for my card to /usr/lib/hotplug/firmware.

---

### Post by Jose Catre-Vandis on 2006-05-22
[QUOTE=gusjones]Left over from my windows days I have a digital TV card in my PC.

Recently after browsing the net I became aware that there are Linux drivers out there for it. I installed Myth TV and TVtime from Synaptic, but neither automatically pick up my **AverTV 761 DVB-T** television card.

I am a newbie when it comes to things like MythTV but following the instructions I managed to run the mythtv backend, but I simply could not get the backend interface to pick up that my card even exists.

When I run TVtime it complaines about there being no input signal, which I suspect is down to not detecting the card as I have pretty good freeview terestrial reception.

Any helpful comments, solutions or pointing in the right direction would be gratefully appreciated.

 :???:[/QUOTE]


If you are still struggling, tvtime only works with analog tuners not dvb-t. Install Kaffiene and everything to do with libxine (you may need to expand your repositories. You could also install the w32codecs. Look at the ubuntu wiki - restricted formats for advice

---

