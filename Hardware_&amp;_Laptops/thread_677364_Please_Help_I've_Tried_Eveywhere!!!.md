---
title: "Please Help I've Tried Eveywhere!!!"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by Death Note Rocker on 2008-01-24
I have a Hp nc6120 laptop That I want to install Linux ubuntu 7.10. I just don't know the drivers I need can someone tell me what drivers I need? Screen shots of device manager:
[IMG]http://i263.photobucket.com/albums/ii144/DeathNoteRocker/Computer%20Things/Drivers1.jpg[/IMG]
[IMG]http://i263.photobucket.com/albums/ii144/DeathNoteRocker/Computer%20Things/Drivers2.jpg[/IMG]
[IMG]http://i263.photobucket.com/albums/ii144/DeathNoteRocker/Computer%20Things/Drivers3.jpg[/IMG]

---

### Post by Whiffle on 2008-01-24
Well, windows doesn't seem to know what drivers you need either.  IF you have trouble with anything I can see on that list it could be the broadcom wireless.  Other than that, can't tell much.  Try running a LiveCD, it will give you some idea of what works and what doesn't.

---

### Post by Rhubarb on 2008-01-24
The only problem that I think you'll have with ubuntu running is your Broadcom b g wireless network card.

The best way to find out if your hardware is supported, is to burn the ubuntu 7.10 desktop cd, then boot off it.  (This does not install it to your hard drive until you tell it to install).
When it's running you'll have the Ubuntu desktop, test things out like sound, wireless networking, play some videos.  If something doesn't work, do a search here on the ubuntu forums to find out if / how it can be fixed.

---

### Post by Sami_Sdata on 2008-01-24
Why don't you try booting to a livecd of Ubuntu?  Hopefully it will detect the correct drivers and load them for you.  Worst case you will find what hardware might give you problems and search for some solutions before you install.

---

### Post by Death Note Rocker on 2008-01-24
I just need to be 100% SURE the wireless will work if it doesn't have a driver for the broadcom wireless i need a back up plan for it so what driver do i need if that doesn't work??

---

### Post by Dngrsone on 2008-01-24
Have you tried to install yet?  Ubuntu should install the drivers automatically.

Have the machine connected to your internet, if possible, when doing the install.

---

### Post by Death Note Rocker on 2008-01-24
I will install tomorrow but i can't have it conneted to the wireless because i have dail up w'no router

---

### Post by Yellow Pasque on 2008-01-24
Sound might not work out of the box. Analog Devices' codecs aren't well-supported in the version of ALSA that comes with Gutsy. You will probably have to compile a later version of ALSA or at least tweak some config files. 

Should you need to build ALSA, the process has been scripted here ([http://ubuntuforums.org/showpost.php?p=3603812&postcount=13](http://ubuntuforums.org/showpost.php?p=3603812&postcount=13)). You may want to alter the script to download the very latest ALSA (1.0.16rc1)

EDIT: Just saw you have dial-up. Do you ever have access to a broadband or wireless connection?

---

