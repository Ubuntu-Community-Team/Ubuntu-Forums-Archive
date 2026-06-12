---
title: "[Ubuntu GNOME] Multiple monitors don't work anymore"
date: 2015-09-21
forum: Hardware
---

### Post by maritn2 on 2015-09-21
I recently installed Linux to try to replace Windows. Initially, I was able to connect my TV (via HDMI) with my Laptop (GTX 660M), but since last week, it just doesn't work anymore. I don't know if a kernel update (or any other update) caused this or if it is due to the driver I installed recently (first nVidia offical 346, then 352, now 352 optimus). The problem is, even when I switch back to the default driver, I can't get it to work.

As long as the TV is not connected and switched on, my laptop display works. As soon as I switch the TV on, it stays black while my laptop display goes black (but you can hear a click 1/s; it seems like the screen switches from off to on (black) ). It is not a hardware issue, as everythings works perfectly on Windows 8. Without beeing able to connect a second screen, I will not be able to switch to Linux... but before giving up on Linux I really want to give it a try, so please help my fix this. :)

---

### Post by Vladlenin5000 on 2015-09-22
Hi and welcome.

Like you, I suspect it has to do with drivers. How exactly did you install the proprietary nvidia drivers?

---

### Post by maritn2 on 2015-09-22
Thanks for answering :)

I used the "Additional Drivers" tool that was included and switched from the default driver (X.org-X-driver) to the latest nVidia driver that was available (346 or something like this). Then after I tried to connect my TV several days later, it did not work anymore (there had been some updates in the mean time), so I used the following PPA

$ sudo add-apt-repository ppa:xorg-edgers/ppa -y
$ sudo apt-get update

and selected version 352 from the "Additional Drivers" tool. It didn't work either, so I installed the latest Optimus driver, but it still did not change anything.

---

### Post by Vladlenin5000 on 2015-09-22
So now you have a mess, to put it mildly. 

You probably should remove all of the "nvidia" you currently have, reboot and try again to install some recent version. 346 and newer should be fine. Then check its behavior and settings either at System Settings and/or Nvidia X Server Settings (installed along the nvidia driver).

```
sudo apt-get purge nvidia*
```

---

### Post by maritn2 on 2015-09-23
Well, it still does not work with the nvidia drivers... and I don't  know, which setting to change in die Nvidia X Server Settings. Do you  have any clue?

---

### Post by maritn2 on 2015-09-23
Ok, I accidentaly got my TV to work in a special case: if it is switched on during boot, both displays work mostly. Still quite buggy, because the stream I was watching tonight was barely enjoyable due to heavy vsync problems, but that might have been f**king flash cancer. I will test it tomorrow with the X.org driver to maybe see if it works better with this one.

But one thing I noticed is that my TV is not recognized as a second screen by the Nvidia X Server Settings, but instead both displays are recognized as one. I guess that's the reason (or one of them) why it is not working properly. The Linux settings recognize two displays and their correct resolution, but thinks my TV is 32'' instead of 42''.
I'm starting to understand why Linux is so rarely used on desktops... :( but I don't want to give up now, not after all the effort I already put into selecting a distro / DE and getting Linux to work properly.

---

### Post by maritn2 on 2015-09-28
Ok, it looks like I'm not the only one having this issue:

[https://devtalk.nvidia.com/default/topic/860345/ubuntu-15-04-external-monitor-connection-causes-black-screen-on-laptop-with-gtx-870m-/?offset=2#4678312](https://devtalk.nvidia.com/default/topic/860345/ubuntu-15-04-external-monitor-connection-causes-black-screen-on-laptop-with-gtx-870m-/?offset=2#4678312)

For now, I'll go back to the Xorg driver and see how this works out.

---

