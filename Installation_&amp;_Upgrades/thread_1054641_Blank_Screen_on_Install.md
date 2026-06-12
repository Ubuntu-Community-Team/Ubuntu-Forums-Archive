---
title: "Blank Screen on Install"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by emoutal on 2009-01-29
I am trying to install ubuntu 8.10 on my Acer Aspire 6530 laptop (AMD RM-70, ATI Radeon 3470, 3gb ram, windows vista). However, when I try to install, I get the progress bar, then all I get is a blank screen with a cursor blinking in the top left corner. I can type anything, but nothing seems to do anything. However, ubuntu is still somewhat running because when I hit the power button on the laptop, it goes through the shutdown procedure.

I have also tried to run ubuntu from the cd (which was ordered from the website and has been checked for errors) and I get the progress bar, followed by "Loading, please wait...". Then some information about the version, a little disclaimer (no warranty, etc.) and then a command prompt with "ubuntu@ubuntu:~$". I can get some response from things typed there, but i have no idea what I'm doing.

Any ideas on how to fix this? I really want to get away from windows and try linux.

---

### Post by emoutal on 2009-02-01
Any ideas?

---

### Post by emoutal on 2009-02-02
OK, so i was able to install ubuntu using the alternate install cd. However, I still get stuck at the command prompt. Is there a way to get into the desktop from there? Do i have to somehow install the drivers for the video card?

---

### Post by brentoboy on 2009-02-02
sudo apt-get update

sudo apt-get install ubuntu-desktop

---

### Post by emoutal on 2009-02-02
I just tried that and it's still the same. It says I already have the latest version of desktop (or something like that).

I downloaded these drivers from ATI [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I have it on a cd, but i don't know how to install from the command prompt. Or even if that would work.

---

### Post by emoutal on 2009-02-03
any ideas?

---

### Post by rosserver on 2009-02-03
Yes, your blank screen is common, I got the same thing on an old workstation.
I have found that when I hit "escape" it starts working again...

(I guess there is some question that it not visible to us)

...it ends up at the "live" desktop.  Click on the "install" icon and proceed as normal.

IMO forget the drivers.

---

### Post by Powerman2442 on 2009-02-03
Same thing happens to me in Xubuntu. Think I am going to try to get a hold of an older version, maybe 8.04? How did you get yours to work then, or does it still not work?

---

### Post by emoutal on 2009-02-07
I still can't get it to work. It appears to be installed completely, but I just can't get into the desktop. It stays at the command prompt.

I can log into my account, but I don't know what to do after that. Could be the drivers, but i'm not sure.

---

### Post by retrovoice on 2009-02-11
I'm experiencing a similar problem with an ASUS Pundit-R system, which has integrated ATi Radeon 9100 IGP graphics.

When you arrive at the blank screen, hit Ctrl-Alt-F1 which will bring up a console (i.e. command prompt).  Then reconfigure the video to "Vesa" using

>sudo dpkg-reconfigure xserver-xorg

You'll get asked several questions regarding Xserver options.  When it asks you to select a driver, select "Vesa," and not the ati driver.  There's something in the current Ati driver that's not working for my system.  Also set the Xserver resolution to the highest resolution your adapter/display will support.

When finished, hit Ctrl-Alt-F7 to try and get back to your X-display.  You might also need to hit Ctrl-Alt-Backspace, which (should) restart your X-server with the new Vesa driver.

I'm not positive about these steps, but this combination of tools might get you to a viewable display.

The frustrating thing about this is that the Vesa driver has no accelerated graphics support.  I've tried installing the ATi proprietary driver after this approach, but I get a blank screen with it too.  The Vesa driver will give you a decent high-res desktop, but anything that needs hardware graphics acceleration is either going to run slow or not work at all.

---

### Post by emoutal on 2009-02-11
I just tried that and still no luck. I can start going through the questions and it asks me to configure the keyboard. After a few of those questions (i just choose the default options), it stops and goes back to the command prompt with the message "xserver-xorg postinst waning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20090211124152"

Any ideas now?

---

