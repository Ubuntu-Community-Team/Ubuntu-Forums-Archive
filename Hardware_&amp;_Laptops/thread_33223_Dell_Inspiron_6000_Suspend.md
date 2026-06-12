---
title: "Dell Inspiron 6000 Suspend"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by dasunst3r on 2005-05-10
I have a Dell Inspiron 6000 laptop.  The problem right now is that my laptop can suspend, but it can't resume.  Any ideas?

---

### Post by mfyahya on 2005-11-18
bump
same hardware, same problem  here.. please help.

---

### Post by Confuse on 2005-12-21
I'm on your side fellas. It seems that it goes into suspend but it doesn't come back from it or at least the screen doesn't. Anyone have any ideas?

---

### Post by Confuse on 2005-12-23
Any news on this? I have the integrated video and it goes to suspend fine but it just doesn't come back.

---

### Post by dans on 2007-02-12
Suspend works ok for me on Edgy 6.10 since install.

I always suspend, then close the lid, then re-open the lid to bring the machine out of suspend.  I think I remember having trouble trying to wake the machine by the power button without closing the lid.

I had some problems running VMWare after suspend, but that is the only program to give me any issues.

---

### Post by boulderjams on 2007-02-20
Well, I have the same problem. Dell Inspiron 6000.

Suspend & Hibernate from console work just fine.

Suspend from X works fine.

When I right click gnome-power-manager and click hibernate, my system take the normal 20 seconds or so and shuts down. When I press the power button, I see usplash then a few glitchy screen. After about 45 seconds I can move the mouse with just a black screen. Then I see the hourglass then a normal mouse. This will continue until I restart my system. In which everything is back to normal. I have installed the 'hibernate' package with synaptics and that works just fine from the command line.

I was able to previously use both suspend/hibernate with a fresh install. I do have NetworkManager-gnome installed, which I am getting the feeling that might be holding it up.

Dell Inspiron 6000
915m Video Card
ipw2200 Wireless Card
acpi 0.09-1
acpid 1.0.4-5ubuntu4
acpi-support 0.90
gnome-power-manager 2.16.1-0ubuntu3

Any ideas?

I have a launchpad report, linuxquestions & ubuntuforums question out there. No replies?

[https://bugs.launchpad.net/ubuntu/+bug/77582](https://bugs.launchpad.net/ubuntu/+bug/77582)

---

### Post by boulderjams on 2007-02-20
Finally fixed! After an upgrade from Edgy to Fiesty Herd 4, I still had the same problem. After playing around with /etc/defaults/acpi-support I added 'nm-applet' to the stop-restart services section and it works just fine. Suspend is quick as quick can be and hibernate takes about a minute.

---

### Post by dimbulb1024 on 2007-03-24
I have had the same problem and what worked for me was to unplug my usb mouse prior to suspending and plug it in after resuming.
I haven't had any problems since doing this.

---

