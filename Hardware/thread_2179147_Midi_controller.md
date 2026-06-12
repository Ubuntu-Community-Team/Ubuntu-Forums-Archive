---
title: "Midi controller"
date: 2013-10-06
forum: Hardware
---

### Post by lenzojake on 2013-10-06
So to start off I found this older midi controllor, it's a Hercules Dj control mp3 e2. Yeah I know it's sort of a mouth full.
  My problem stems that Once I got the hdjmod installed it would cause a kernal panic killing my linux box. Like clicking hard drive of death. :confused: Anyway so I went to the site for Mixxx a virtual djing program that should be able to interface with my controller. The problem is that it's not showing up in the Mixxx program under controllolers, the method that they had in case this happened was like so:

[COLOR=#0000ff] If the device is still not visible as a separate entry under  “Controllers” you need to modify the device permissions using udev  rules. First create the rule file: 
[/COLOR]
[COLOR=#0000ff]sudo nano /etc/udev/rules.d/hercules-usb.rule[/COLOR][COLOR=#0000ff] Add following lines to this file: [/COLOR]
[COLOR=#0000ff]SUBSYSTEM=="usb_device", SYSFS{idVendor}=="06f8", MODE="0666"
SUBSYSTEM=="usb", ATTRS{idVendor}=="06f8", MODE="0666"[/COLOR][COLOR=#0000ff] Save the contents and restart udev: [/COLOR]

[COLOR=#0000ff]sudo /etc/init.d/udev restart // [/COLOR][COLOR=#000000]Okay here is where I get confused. What the heck is this supposed to do? I get a very interesting message.[/COLOR][COLOR=#0000ff] Pull out the controller and plug it in again. Run mixxx and select  “Preferences” &#8594; “Controllers” and you should be able to select and  enable the controller. 


[/COLOR]

Not only does it not seem to work I get this from my terminal when I copypasta the above into it. If anyone could help me here it would be very greatly apriciated.

[COLOR=#800080] :~$ sudo /etc/init.d/udev restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop udev ; start udev. The restart(8) utility is also available.
udev stop/waiting
udev start/running, process 3428




[/COLOR]

---

### Post by lenzojake on 2013-10-06
firgued it out I just needed to run the application mixxx under sudo. fixed all problems.

---

### Post by mörgæs on 2013-10-07
Good, then please mark the thread 'solved'.

---

### Post by lenzojake on 2013-10-08
Sorry it took me forever my hdd crashed and I had to replace it but gave me new excuse to buy a ssd. ):P

---

