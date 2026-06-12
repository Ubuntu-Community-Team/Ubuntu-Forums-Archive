---
title: "Touchpad stopped working after updating to 11.10"
date: 2011-10-13
forum: Hardware
---

### Post by WorthyNoob on 2011-10-13
So I have a dell inspiron 1764 and after I updated to 11.10, my touchpad suddenly stopped working.  there's a little toggle button for turning on and off the touchpad which when I used to press in 11.04, it used to show up a little box on the top right with a touchpad.  But now after updating an empty box shows up.  Had updating to 11.10 removed the drivers for my touchpad?  If so how do I reinstall the drivers?

Thanks!

---

### Post by strikeir13 on 2011-10-13
I also have this problem. HP Pavilion dv4000. worked fine in 11.04...

---

### Post by ShapeShifta on 2011-10-13
Same here, HP Pavilion dv5000.

---

### Post by hernanjx on 2011-10-13
Hi, I'm having the same problem after upgrading to 11.10 Thinkpad T61. Worked perfect with 11.04

I checked all the logs and dont see any problem, they says that the Touchpad was found.

Seems like the problem existed at release time, [https://bugs.launchpad.net/ubuntu/oneiric/+source/xserver-xorg-input-synaptics/+bug/868400]("https://bugs.launchpad.net/ubuntu/oneiric/+source/xserver-xorg-input-synaptics/+bug/868400")

---

### Post by diasf on 2011-10-14
That happened to me as well... but   i switched to unity 2d and rebooted, and now it's working (Dell inspiron 6400/ E1505)

---

### Post by Dhezballah on 2011-10-14
Same thing happened to me on a Toshiba L300.

Edit: Restarting has fixed it.

---

### Post by kilpikonna on 2011-10-14
Same here, but it occurs after I try to deactivate screensaver. It works again only after restart. I have LG -laptop.

---

### Post by vsr1312 on 2011-10-14
I was facing the same problem in my Laptop,and i installed Synaptiks and it worked for me.
See full article [http://www.myapitips.com/2011/10/14/touchpad-stopped-working-after-installing-ubuntu-11-10/]("http://www.myapitips.com/2011/10/14/touchpad-stopped-working-after-installing-ubuntu-11-10/")
Hope it works for you also

---

### Post by ShapeShifta on 2011-10-14
> **vsr1312 said:**
> I was facing the same problem in my Laptop,and i installed Synaptiks and it worked for me.
See full article [http://www.myapitips.com/2011/10/14/touchpad-stopped-working-after-installing-ubuntu-11-10/]("http://www.myapitips.com/2011/10/14/touchpad-stopped-working-after-installing-ubuntu-11-10/")
Hope it works for you also

Yea, that's what I did as well. I was installing that when I made my previous post and when i got on the laptop now I noticed it's working again. I use a usb wireless with my laptop, but it's still necessary to have the touchpad working just in case.

---

### Post by ajay.pratham on 2011-10-15
Please try the following - Go to' system settings'>'mouse and touchpad'>'Touchpad'
Unselect 'Disable touchpad while typing'.
Restart your computer.

---

### Post by ajay.pratham on 2011-10-15
Please try the following - Go to' system settings'>'mouse and touchpad'>'Touchpad'
Unselect 'Disable touchpad while typing'.
Restart your computer.

---

### Post by John_T on 2011-10-26
> **ajay.pratham said:**
> Please try the following - Go to' system settings'>'mouse and touchpad'>'Touchpad'
Unselect 'Disable touchpad while typing'.
Restart your computer.
Just a note to say that the above solution did NOT work for me.  A comment in a bug report turned up a solution however. 

Essentially, you need to use dconf Editor to toggle the "touchpad-enabled" setting on. It's at "/org/gnome/settings-daemon/peripherals/touchpad/". Trivially easy and worked without a reboot/logout.

[Link to my more complete writeup]("http://askubuntu.com/questions/66907/touchpad-not-working-on-msi-u130-after-login-in/72610#72610").

[[IMG]http://img853.imageshack.us/img853/9193/touchpadenabledsetting.png[/IMG]](http://imageshack.us/photo/my-images/853/touchpadenabledsetting.png/)

64 bit Ubuntu 11.10, upgraded from a clean install of 10.10

---

### Post by Jamble on 2011-11-17
Install dconf
Start dconf-editor
go to this path "/org/gnome/settings-daemon/peripherals/touchpad/"
enable touch pad

---

