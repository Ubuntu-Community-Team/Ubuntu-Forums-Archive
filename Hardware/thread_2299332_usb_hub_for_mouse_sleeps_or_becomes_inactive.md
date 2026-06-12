---
title: "usb hub for mouse sleeps or becomes inactive"
date: 2015-10-17
forum: Hardware
---

### Post by techsupport2 on 2015-10-17
I am new to Ubuntu / LXDE having switched from Fedora.

I searched the forum but did not find this problem.
If this was posted before, please post the link, thank you.

I have a usb hub for the mouse.
It dies after x seconds.


In ubuntu I entered a cron job to keep the mouse alive:



    for i in /sys/bus/usb/devices/*/power/control; do sudo echo on > $i; 
        done
    sleep 30


I tried different intervals of 10, 30, 60 seconds but while the script runs, the usb mouse is reset and inactive for about 20 seconds.

So either way, I have a mouse which will be inactive at intervals.

Any suggestions?  Thanks in advance.

---

### Post by techsupport2 on 2015-10-18
Is there another ubuntu forum which is more active?  I thought this was the main ubuntu forum.
thanks in advance.

---

