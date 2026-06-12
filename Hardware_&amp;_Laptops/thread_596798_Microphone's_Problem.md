---
title: "Microphone's Problem"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by ciclo on 2007-10-29
My laptop is Dell inspiron 1420. 
OS is ubuntu 7.10
alsa is allright
but the build-in microphone doesn't work.
when i insert a extra mic, it works, strage!

---

### Post by macgreagoir on 2007-11-02
I had some similar problems. This may, or may not help: 
[http://mickgregg.blogspot.com/2007/06/ubuntu-704-feisty-on-dell-xps-m1210.html](http://mickgregg.blogspot.com/2007/06/ubuntu-704-feisty-on-dell-xps-m1210.html)

---

### Post by sloggerkhan on 2007-11-02
On my laptop the internal mic channel was muted by default. Try right clicking on the sound icon on the gnome panel and opening volume control and seeing if the channel's muted.

---

### Post by ulmito on 2007-12-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/dell/+bug/153963](https://bugs.launchpad.net/dell/+bug/153963) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This solution works for me

1) added gutsy-proposed to my sources.list
2) ran apt-get update
3) installed linux-backports-modules
4) restarted the laptop to reload the kernel and modules
5) ran alsamixer and set the following settings:
   Section: [All]
     Digital Input Source: Digital
     Input source: Front Mic (probably unnecessary)
   Section: [Capture]
     Capture: max volume, capture ON
     Digital: max volume
6) and, at last, started gnome-sound-recorder with input "Digital" to check if that worked - and it did :)

	
More information at: [https://bugs.launchpad.net/dell/+bug/153963](https://bugs.launchpad.net/dell/+bug/153963)
:popcorn:

---

