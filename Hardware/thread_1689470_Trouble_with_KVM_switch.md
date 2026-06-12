---
title: "Trouble with KVM switch"
date: 2011-02-16
forum: Hardware
---

### Post by willystylee on 2011-02-16
hello again all, i bought a KVM switch and i'm trying to use it to have it connected to my main PC (win7) and my new machine i just installed ubuntu on. I hooked it up properly, and tried using it. It worked when switching from the win7 machine to the ubuntu one, but after the (1st and only) successful switch, ubuntu just didn't seem to recognize my mouse or keyboard. Can anyone help?


[http://www.newegg.com/Product/Product.aspx?Item=N82E16817107417](http://www.newegg.com/Product/Product.aspx?Item=N82E16817107417)

Win7 x64
Ubuntu 10.10

---

### Post by tgalati4 on 2011-02-16
What resolutions are you using?  Most KVM's are limited to 1600 by 1200.  If you are using higher resolution (on your new computer perhaps) then you will run into problems.

I have a 4-way and a 2-way IOGear KVM and they have been quite reliable, but for VGA, they are limited to 1600x1200.  If you go higher than that, they tend to lose sync and lock up.

---

### Post by willystylee on 2011-02-16
> **tgalati4 said:**
> What resolutions are you using?  Most KVM's are limited to 1600 by 1200.  If you are using higher resolution (on your new computer perhaps) then you will run into problems.

I have a 4-way and a 2-way IOGear KVM and they have been quite reliable, but for VGA, they are limited to 1600x1200.  If you go higher than that, they tend to lose sync and lock up.

Preeetty sure resolution is not the issue, on the ubuntu machine its standard res, i never changed it. 

Basically when i tried it the easiest was to explain what happened was it only worked with Win7. When i switched over to ubuntu by doing a [scroll-lock] [scroll-lock], my keyboard and mouse were not recognized. However, the lights on the keyboard and mouse did work when on ubuntu, but they didn't function, and since keyboard wouldn't function, i couldn't do a [scroll-lock] [scroll-lock] to switch back to the win7 machine. So i was basically locked in, and i had to unplug the keyboard/mouse usb's and d-sub to plug the monitor d-sub back into win7 computer to type up this thread and google the issue. Seems some people have had this issue before but i couldn't find a fix... :(

I am 80% sure it has to do with drivers... *but there isn't any for KVM switches, at least not this one* also i never was unable to find ubuntu drivers/firmware for my mouse and keyboard (Logitech G15 and Razer Deathadder 3500). I don't know how to fix this, perhaps someone super-savvy could write/code a script or work-around or something? I really need to get this thing working, my back is getting sore from bending over and plugging in / unplugging usb/monitor/usb/monitor/usb/usb over and over again lol... and i really would be sad if the constant plugging unplugging of the usb's or the d-sub port would over time damage the ports... i don't want that...

There has to be some way to get this working..

---

### Post by willystylee on 2011-02-17
bump

---

### Post by tgalati4 on 2011-02-17
You do realize that for a KVM to work properly, you need to boot each machine in order.

1.  Boot the first machine and make sure the display is painted during boot and the keyboard lights up (hit Caps Lock a few times.)  You must wait for machine #1 to boot completely.  The graphics card will sometimes negotiate with the monitor for refresh rates, etc and you must not interfere with this communication.

2.  Only after machine 1 is completely booted, then boot machine #2.  Hit scroll-lock to wake up the KVM and make sure the display is painted.  Check the keyboard by hitting Caps Lock.  Wait for machine #2 to completely boot.  Once this happens, then you should be able to scroll-lock between the displays and the mouse and keyboard should work normally.

If this is not the case, then perhaps your KVM is defective, or (more likely) you have a bad connection.  All it takes is one mouse or one keyboard connection to go bad and it will lock up the KVM.  Try swapping some mice and keyboards to see if the behavior changes.

I'm not familiar with your mouse/keyboard hardware, but most mouse buttons can be activated by adding a few magic lines to /etc/X11/xorg.conf.  Your keyboard's extra keys can be mapped using one of several methods.  It will take some time to figure it out.

[http://ubuntuforums.org/showthread.php?t=921870&highlight=keyboard+multimedia](http://ubuntuforums.org/showthread.php?t=921870&highlight=keyboard+multimedia)

---

