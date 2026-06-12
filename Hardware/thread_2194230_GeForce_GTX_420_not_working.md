---
title: "GeForce GTX 420 not working"
date: 2013-12-17
forum: Hardware
---

### Post by michaeljj2 on 2013-12-17
[COLOR=#333333][FONT=UbuntuRegular]With the default open source driver it's slow as hell. So I tried the latest one and installed according to the steps from [http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml)
it was working fast, but i had to restart few times until i get something different from black screen upon booting and also recovering from suspend was also going to the black screen.
So I purged it and installed the nvidia-current from the app centre, again it has problems booting and the graphics are moved to the left couple inches.
So what should I install to have my nvidia work properly? :(


it's GeForce GTX 460 v.2


[/FONT][/COLOR]

---

### Post by efflandt on 2013-12-18
If you did not include **nomodeset** boot parameter during install, see if editing this line in /etc/default/grub (use **gksu gedit** or **sudo nano**) as shown helps (it cannot hurt):```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
``` I have been using **nvidia-experimental-310** in 12.04 for GTX 550 Ti since January when steam (still beta then) recommended using experimental drivers and in 13.10 on a new laptop with GTX 765M. Although, the laptop has combo Intel/Nvidia graphics, so I had to learn how to specifically use Nvidia instead of Intel integrated graphics.

---

### Post by michaeljj2 on 2013-12-18
no i haven't inlcluded it
what does this do and do i just add that line on the bottom of that file?

---

### Post by michaeljj2 on 2013-12-18
i added it and it didn't help, still can't start :(

---

