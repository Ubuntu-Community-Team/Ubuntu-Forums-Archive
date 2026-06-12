---
title: "Screen dimmer buttons not working"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by smeat on 2006-08-23
I have an HP Compaq nc6000 laptop.  I am not able to use my screen dimmer/brighten buttons.  Also when I unplug the laptop the screen should drop in brightness, but does not.

I previously had Mandriva 2006 on this laptop and the buttons worked perfectly.  Does anyone have an idea of what might be causing this?

Thank you.

---

### Post by Eddie Hung on 2006-08-23
I have a Compaq N410c and my laptop brightness settings (i.e. Fn + Up arrow / Down arrow) do not work either.

However, they do work under windows with the Compaq software.

I did not know that they worked in another Linux distro though, I assumed that because it was proprietary hardware, no-one had reverse-engineered it to get it working.

I have found that setting the "Compaq Power Saving" setting under the Compaq software under Windows saves the brightness setting when on battery permanently, so that it always dims the screen. (i.e. On my laptop, after setting this, the screen dims when I'm on battery when I'm booting up, when in grub, when in Ubuntu - everywhere!)

Hope that helps,

Eddie

---

### Post by smeat on 2006-08-23
Wierd, now I am really curious what Mandriva is doing different.  Maybe something got messed up in xorg at some point and the version that is in Mandriva 2006 works correctly.  I will have to try out their live cd distro and see what they are doing or what versions they are running that works.

I will have to go into windows and set the brightness on battery than, right now it is all the way up when I am on battery and it really drains it quick.


Do developers from ubuntu frequent these forums?  Should I report this is a bug on ubuntu?

---

### Post by jjhart on 2006-10-25
I am having the same problem with the same computer.  I recently installed Ubunutu Dapper on a HP/Compaq NC6000 notebook.  I can adjust the brightness in windows using the hotkeys.  I can even adjust the brightness when it is booting, that is before either windows or ubuntu boots, suggesting that it is hard-wired and doesn't require any software or drivers to make it work.  But alas, once ubuntu is up and running, I cannot control the brightness using the hotkeys anymore.  Unfortunately, I have not tested whether I can adjust the brightness during boot and if it will stay that way once it makes it all the way in to ubuntu.
As a help to those that are helping us, the NC6000 uses an ATI video card rather than an nvidia.  If you have an nvidia card, you can go into the power management in ubuntu and adjust the brightness there, but that option is not available to us with ATI cards.  I would like to be able to use the hotkeys while in Ubuntu to adjust the screen on the fly, not just have it be at one setting for plugged in and another for battery power.  I have noticed other posts that mention the same problem with a toshiba laptop but they say it works fine with dapper but then breaks with Edgy and it seems that it is a problem with HAL? what ever that is.  Anyway, a fix would be nice.  The screen eats up the battery and it is just way to bright for me anyway.  THanks

---

### Post by chele on 2006-11-25
This used to work on the hp nw8000, but it not longer does once I upgraded to 6.10, Edgy.

---

