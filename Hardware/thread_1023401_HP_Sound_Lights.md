---
title: "HP Sound Lights"
date: 2008-12-27
forum: Hardware
---

### Post by Rohan Kapoor on 2008-12-27
Hello Ubuntu Community,

Over the past year I have migrated several computers within my home to Ubuntu. Throughout that time-frame I have been greatly helped by many people and now I am much more knowledgeable about Linux than before.

However there still is one problem that is bugging me that I haven't been able to solve. This problem is on an HP Compaq Presario V2000 Laptop Computer running Ubuntu 8.10. The problem is that the "mute light" doesn't work. This light is located below the mute button. On a Windows install the light is off when the volume is not muted. Once muted the light glows orange. In Ubuntu this does not work. I have tried many different versions from 6.06 onward and this hasn't worked in any of them. Does anyone have any ideas?

Thanks!

---

### Post by j.m.wilson@earthlink.net on 2009-02-18
I have a Presario v5206 and had the same problem.  Use the commands below in terminal.

sudo gedit /etc/modprobe.d/options


At the bottom of the page add "options snd-atiixp ac97_quirk=7"

that did it for me.

---

### Post by Rohan Kapoor on 2009-02-19
> **j.m.wilson@earthlink.net said:**
> I have a Presario v5206 and had the same problem.  Use the commands below in terminal.

sudo gedit /etc/modprobe.d/options


At the bottom of the page add "options snd-atiixp ac97_quirk=7"

that did it for me.

Thanks. This worked for me!

---

### Post by Rohan Kapoor on 2009-10-07
> **j.m.wilson@earthlink.net said:**
> I have a Presario v5206 and had the same problem.  Use the commands below in terminal.

sudo gedit /etc/modprobe.d/options


At the bottom of the page add "options snd-atiixp ac97_quirk=7"

that did it for me.
Hi! This works as well in 9.04! My question now is how to get the light to continue functioning after a suspend/resume. Currently I have to reboot to get it working, :(

Any ideas?

---

