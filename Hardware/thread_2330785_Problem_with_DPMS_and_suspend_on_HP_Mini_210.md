---
title: "Problem with DPMS and suspend on HP Mini 210"
date: 2016-07-14
forum: Hardware
---

### Post by T.lancer on 2016-07-14
I have a HP mini 210 (Atom based, 2GB RAM) that I'm traying to set up with Lubuntu 16.04. Most things work fine (Wifi, touchpad etc) but a few things that is still causing problems is the power managment and the backlight of the LCD.

it seems I can't get the screen to acutally turn off, such as via "xset dpms force off". it just blanks the LCD but the backlight is still on. However, running the same command from the Lubuntu live session works exactly as it should and turns the LCD off. I've googled around and haven't found any solution to the problem.

I also had a problem with the backlight not dimming, but I fixed that by adding the following command to the grub command line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

I already tested to see if that was somehow the reason dpms was not working. But dpms doesn't work with or without that command. I haven't tested it on the live session since it works straight out of the box.

The other problem I have it that suspend doesn't work either.  if I tell the device to suspend, the screen goes blank, if I move the mouse I'm right back and the unlock prompt.  Trying to shut down gives me the error, that a shutdown/suspend process is already running.

Any ideas? from what I have read, ubuntu/lubuntu should work perfectly on this machine. Yet it seems it doesn't.

---

### Post by T.lancer on 2016-07-16
I have solved the problems by installing Linux Mint 17.4 with XFCE.  ACPI features all work without any modifications needed.

---

