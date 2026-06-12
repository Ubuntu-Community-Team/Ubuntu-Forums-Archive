---
title: "ubuntu 8.04 on ASUS U6SG"
date: 2008-05-29
forum: Hardware
---

### Post by gogo543 on 2008-05-29
Has anyone tried to install Ubuntu on this model yet?
How does it go?
Will the finger-print recognition stuff still work?
How about the SD card reader, wireless and blue tooth?
:lolflag::lolflag:

---

### Post by hotweiss on 2008-05-29
I have an Asus M50 which shares a lot of the same components. Almost everything works out of the box, here's my guide how to get everything working on it:

[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)

---

### Post by gogo543 on 2008-06-02
thanks for the help.
but unfortunately my bluetooth can detect my bluetooth mouse come with the machine but whenever i click on connect it failed.

i try the nvidia driver command you gave and it install some program but as it detects my graphic card as a newer graphic card which don't have a suitable driver for it. how do i uninstall this program as every time i start up the crash warning sign appear which is kinda annoying.

for the web cam
sudo apt-get install build-essential subversion linux-headers-`uname -r`

what should i replace the 'uname -r'?
:confused::confused:

---

### Post by hannulan on 2008-08-30
My works fine. At least for the most common thing. The mouse have worked, but now I have done somehting so it doesn't work anymore. 

But, I have a question. Does the HDMI-port work? I have no possiblity to try it now, but I reall need to know it. Can someone else try?

---

### Post by pall.e on 2008-09-25
sorry to bring up a old forum, here's a great link about what works and what doesn't work on the u6 in general [http://binblog.wordpress.com/2008/06/14/status-of-linux-on-the-asus-u6s/](http://binblog.wordpress.com/2008/06/14/status-of-linux-on-the-asus-u6s/)  It shows how to fix the webcam upside down problem as well.  

I haven't tried the hdmi on mine, and I fixed the bluetooth mouse problem through this link [http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)  and for the mouse_address it was the same as the one on the bottom of the mouse.  

One problem I have yet to solve is standby on the U6, hibernate basically works fine though there is a slight problem with the wireless resuming upon hibernate.  With standby, however, I just get a black screen and a cursor upon resume and I have tried playing with some of the settings but am afraid to do too much because it requires a hard reboot to fix and try and I don't want to hurt my harddrive.  Let me know if anyone has standby working on this.

---

