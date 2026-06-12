---
title: "I don't need a monitor for my space balloon"
date: 2008-11-28
forum: Hardware
---

### Post by dcs02d on 2008-11-28
I've installed the latest xubuntu on a Jetway J8F9

[http://www.jetway.com.tw/jw/ipcboard_view.asp?productid=431&proname=J8F9-P](http://www.jetway.com.tw/jw/ipcboard_view.asp?productid=431&proname=J8F9-P)

I'm using a 4 gig CF card for a hard disk.  This is going to be used for a telemetry system on a high altitude balloon thats taking pictures.  

I've got everything working....  GPSD, the RS232 connections to the Camera, audio out is great for position reporting over the radio.

There is just one catch.

When I boot up, just after GRUB loads the computer will hang if no monitor is plugged in.  I'm not loading gdm and I made the boot display quiet (or something like that to the boot line) so I don't get the xubuntu graphic when it boots.  Just the text of everything loading.

Yet, for some reason it wants to have a monitor plugged in.

Suggestions?  

On a side note there is nothing in /var/log/boot and I am running the boot log daemon.

Thanks!

Donny in Tallahassee

---

### Post by dcs02d on 2008-11-28
I goes to Starting Up... and hangs there.

If I plug a monitor in after that it still just hangs until I reboot.  The keyboard is alive as a ctrl alt delete will reboot.

Anyone?????

I must be doing something stupid.

---

