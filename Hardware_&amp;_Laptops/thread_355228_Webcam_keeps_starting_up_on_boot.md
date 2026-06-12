---
title: "Webcam keeps starting up on boot"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by illegalbuds on 2007-02-07
I have a webcam builtin at the top of my laptop's screen that has the ability to rotate 225 degrees  to view behind my screen. The camera uses the gspca driver.

I was in Camorama and I decided to rotate it. Half way through rotation (it makes a snap sound or something.. normal) my computer froze and Camorama went dark, so I decided to reboot.

Now every time I start up Edgy, the webcam light turns on after Gnome loads. I did a "ps ax | grep camorama" NOTHING, so I did "lsof /dev/video" and "camserv" shows up. So now every boot up into Edgy, I have to "sudo killall camserv" to turn off the light..and to use Camorama again or it can't read the device (in use by camserv). Also, there's nothing in Preferences > Session about "camorama" nor "camserv"

Any suggestions?

---

