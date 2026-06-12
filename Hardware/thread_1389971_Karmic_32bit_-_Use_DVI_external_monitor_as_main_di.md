---
title: "Karmic 32bit - Use DVI external monitor as main display"
date: 2010-01-25
forum: Hardware
---

### Post by pechar on 2010-01-25
Hi all,

I'm trying to setup my external HD screen as my main desktop. It is connected using a DVI output on my laptop (ATI HD2400 XT gfx card). I practically don't need to extend my desktop. I just want to use my external screen as the main display whenever it is connected. i.e. having all the task bars and panels on the external screen.

Also the resolution though 1920 X 1080 seems to be given a black padding of an inch around the edge. The external screen is a Philip 22" wide-screen if it is of any help. ATI restricted drivers are also installed.

I've found forums guiding to modify the xorg.conf file but I hear there is none on Karmic. I would consider myself as a beginner to intermediate Linux user so please take that into consideration.

Thanks a lot

---

### Post by pechar on 2010-01-27
Hi everyone,

I've solved my problem. Steps taken:

[LIST=1]
[*]Install restricted drivers (by default found in System > Administration > Hardware Drivers)
[*]In terminal run: sudo amdcccle to run ATI Catalyst
[LIST]
[*]Under Display Manager select external monitor > Adjustments tab & move slider in Scaling Options to expand desktop to get rid of black borders. Apply.
[/LIST]
[*]To move the panels to the external screen hold Alt and drag them over to the screen. (Thank you Josh @ superuser [here]("http://superuser.com/questions/76196/ubuntu-ati-second-display-as-main-display/101352#101352") for this one)
[/LIST]

This is the simplest way I managed to get the setup I wanted.

I'm open to any other suggestions

---

### Post by mdwy62 on 2010-03-29
I am using Karmic 32bit. I had an unwanted "dual head" effect when I plugged in an external monitor. 

I went to Gnome Panel>System>Preferences>Display

There I selected the graphic of the laptop display and selected the "off" button, and selected the graphic for the external display and selected "on". I changed the resolution slightly and everything is fine.  

I used to use (under Jaunty) the sudo xrandr command, but this doesn't seem to work anymore.

---

