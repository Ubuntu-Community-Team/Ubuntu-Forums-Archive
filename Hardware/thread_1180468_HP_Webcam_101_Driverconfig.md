---
title: "HP Webcam 101 Driver/config"
date: 2009-06-06
forum: Hardware
---

### Post by gvast on 2009-06-06
Hi to everyone!

I have laptop Compaq Presario CQ40-300LA. It came originally with Windows Vista Starter. I have just installed Ubuntu 9.04 and I need to know:

[LIST]
[*]How to install and config the built in webcam, also named as "HP Webcam 101"
[*]Which programs can I use for a webcam?
[*]Can I use for chat or record a personal video?
[/LIST]
Thanks in advance for the answer!

Gaston

---

### Post by DomNewToLinux on 2009-08-10
I have the same issue...did you ever find out how to get the webcam to work?

---

### Post by ~dr,j on 2009-08-11
hey guys~
ok so i have an hp pavillion laptop w/a built in webcam as well. when i got the laptop, almost a year ago, i was using intreprid but have since upgraded to jaunty so my suggestions assume your using jaunty (ubuntu 9.04, the newest version) an these programs worked for me at least, so hopefully they will for you!

in synaptic you'll want to install the following programs:
camorama
camstream
wxcam

one you have those, check any of the settings and first try to let it auto detect what 'driver' to use (as in video4linux 1, 2 or auto) mine works set to auto but you may have to change to v4l1 or 2...)

this works for me, i regularly use my webcam on tokbox and in skype w/no real problems (so long as u get it setup and leave the settings alone in the program once its started)

for recording, i don't do that but i've heard that theres some great programs out there....check getdeb.net as i don't remember any of the names off the top of my head....
good luck!
~j

p.s. try installing wxcam first and see if it works, you may not needed the first two i listed

---

### Post by dome412 on 2011-08-13
Hello!
I have Ubuntu 11.04 and "cheese" and "wxcam" said either they can't found a device or driver isn't installed correctly.
My webcam is built-in and works perfectly with ubuntu 9.10, 10.04 and Vista.
So this is my lsusb

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I really don't know what I should do!!

---

