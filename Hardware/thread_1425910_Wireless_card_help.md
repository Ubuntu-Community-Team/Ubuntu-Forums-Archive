---
title: "Wireless card help"
date: 2010-03-09
forum: Hardware
---

### Post by Rogue5 on 2010-03-09
I have another laptop which I have installed Ubuntu 9.10 on.  It is a HP Pavilion dv4000.  I cannot get on the internet.  I ran a couple of commands I read about to see if it even reconized the card, and to my surprise it did reconize the card, it just says deactivated.  So how do I activate?

Also, I plugged in an external wireless card into the laptop and ubuntu didn't reconize that one either.  I am a complete noob at Ubuntu, though since I have discovered it I love it.  You will notice this is my first post.  Please walk me through this (begs)?
(p.s.)
I notice there are so many names for different releases of ubuntu.  I installed Ubuntu 9.10, but does that one have a nickname like Kubuntu? Or Xubuntu? Or ChuckNorrisBuntu?

---

### Post by p110011 on 2010-03-09
Welcome, Ubuntu 9.10 is called Karmic Koala.
You can get your card info running this
```
lspci -v | less
```If it's the same broadcom bcm4306 (rev3) as mine it will be ez

---

### Post by Rogue5 on 2010-03-10
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g [COLOR=Red]Wireless[/COLOR] LAN Controller  [COLOR=Black](rev 02)

My output from [/COLOR]
lspci | grep Wireless

---

### Post by dmzamora on 2010-03-10
I too have the same issue. 
I installed Ubuntu via wubi, it installed 9.10.
I was able to use the wireless when I used my Live CD prior to installation.

---

### Post by p110011 on 2010-03-10
You can first try installing B43-fwcutter from the Synaptic package manager. system>administration>synaptic package manager in the quick search start typing fwcutter
and when you see B43-fwcutter click and apply.

And after that go to system>administration>hardware drivers  and see if the broadcom driver is activated. If that doesn't work go back do the same, but instead click the B43-cutter and select uninstall.

The other way is using ndiswrapper installation is the same was as fwcutter and after installed it will be listed under administration as windows wireless drivers. As the name implies it uses your windows driver, so you will need that to direct it to install the correct .inf file

---

### Post by hotrock3 on 2010-03-13
I can't seem to get Ubuntu 9.10 to even install on my HP Pavilion dv4000. I can get as far as choosing to install but then it just sits there. Any ideas as to how to fix that?

Thanks

---

### Post by p110011 on 2010-03-13
All I can say is make sure the cdrom drive is set to boot in your bios.
And maybe start a new thread.

---

