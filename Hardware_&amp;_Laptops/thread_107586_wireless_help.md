---
title: "wireless help"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by wwbdd on 2005-12-23
I just installed ubuntu on my new compaq v2000 series laptop (actually the v2404us).  So far I am very pleased with the way everything is setup.  After a quick change X works and it automatically configured sound and the mouse and even the touchpad scrolling thing that I cant even get windows to do!  The only thing left is to get wireless to work.  I clicked on the networking button thing under system administration and it doesn't even see the wireless card so I have no clue what to do since that didn't work.  Any help would be greatly appreciated.

---

### Post by Michael Steinberg on 2005-12-23
Best to start with the Wiki: [https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

You may have to resort to ndiswrapper loading the Windows drivers for your card. I've had good luck with thr GUI tool, ndisgtk, after finding & downloading the driver I found by following the Wiki's instructions.

Michael Steinberg

---

### Post by wwbdd on 2005-12-24
So I followed the instructions on that page and got the wireless to work... temporarily.  I dont know what i have done to it, but it doesn't want to connect anymore.  I tried removing and reinstalling the drivers i tried rebooting i tried connecting to a different network... nothing.  There is a button that turns the wireless on and off and when it is on it turns blue but it is off (I may be a newbie, but i did have the sense to press it, nothing happens).  Occasionally when i reinstall something or restart something it will flicker on momentarily.  I dont know what to do.  Any suggestions???

---

### Post by emperor on 2005-12-24
If the v2404 is similar to the v2405, it has a Broadcom chipset for which there is no native linux driver. The solution in this case is to use the windows drivers via ndiswrapper.

[http://www.dimensionalstorm.net/v2405us/](http://www.dimensionalstorm.net/v2405us/)

---

### Post by wwbdd on 2005-12-24
Sorry i should have mentioned, that is what i did.  I had it up and running with the ndiswrapper thing and now it doesn't work.  I cant for the life of me figure out why.

---

### Post by servant74 on 2005-12-24
I to am having problems with getting ndiswrapper to work.  It seems that the kernel must be re-compiled to use it.  Or am I reading things wrong?

If I want to purchases a PCMCIA card that does not require wrappers, what kind of card should I get?

My laptop is an old Dell Latitude C600 with Ubuntu 5.10 on it.

---

### Post by dys4ic on 2005-12-24
[QUOTE=servant74]I to am having problems with getting ndiswrapper to work.  It seems that the kernel must be re-compiled to use it.  Or am I reading things wrong?

If I want to purchases a PCMCIA card that does not require wrappers, what kind of card should I get?

My laptop is an old Dell Latitude C600 with Ubuntu 5.10 on it.[/QUOTE]

Hi, for a list of supported wireless network cards look here: [http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/")

And about ndiswrapper, I tried to install ut myself using these instructions: [https://wiki.ubuntu.com/forum/hardware/ndiswrapper]("https://wiki.ubuntu.com/forum/hardware/ndiswrapper")
and it worked without re-compiling kernel or anything. However I gave up this idea after finding out that ndiswrapper didn't support Monitor mode for the device (DWL-G132 usb) I had.

---

