---
title: "TX2000 problems"
date: 2009-05-24
forum: Hardware
---

### Post by SuperGiraffe on 2009-05-24
Hi everybody,

I'm having problems with my TX2104ca laptop that messed up the display and don't allow me to connect to usb devices. I don't know how they started but initially I was using the Nvidia 180.51 display driver and could connect my printer, scanner, and Sony ericsson phone (to download photos) to my laptop. One day those things just stopped working. 

I've uninstalled the Nvidia drivers a couple times and reinstalled them again so i can access Nvidia X Server settings in the System menu again although it says I'm running driver version 180.11 when I only had 180.51 and 180.22 on my computer to install. Strange but probably okay and i can go through the procedure to get functional wacom by editing the xorg.conf file.

I can connect to my USB thumbdrive and Creative Zen Micro mp3 player and drag and drop files to them. However, i still can't can't connect to my printer, scanner, and cellphone.
I'm running Ubuntu 8.10 with Gnome 2.24.1. I've attached the output from the sudo lsusb and sudo lspci commands if that helps. Please tell me if there is any other information that is needed. Thanks,

---

### Post by SuperGiraffe on 2009-06-02
Hi again,

So i still don't know what's wrong with my laptop but i did realize that the Cypress USB 2.0 TetraHub listed in the lsusb hasn't been connected to the laptop for a couple weeks.
So i've used the lsusb -v -s 002:002 command as root to try and get more information on the device.
Now I have an idea of what's wrong, it's as if the USB device list isn't updating. Why is that? Can I force a USB reset somehow? Did i change a grub menu option or a bluetooth driver? Please help.

---

### Post by Favux on 2009-06-02
Hi SuperGiraffe,

No idea what's going on but I saw Cypress.  When Microsoft rolled out the Cypress update I was one of the ones caught by it breaking USB.  After frantically Googling I realized I just had to roll back the driver.  Since a window driver shouldn't do anything I then thought maybe your bios isn't the latest.  Have you looked at that?  That could make a difference with Ubuntu.

Anyway basically wanted to say you're not being ignored.

---

### Post by SuperGiraffe on 2009-06-05
Partial solution! I googled ubuntuforums.org usb restart and found a thread [http://ubuntuforums.org/showthread.php?t=306289](http://ubuntuforums.org/showthread.php?t=306289) with the usb restart command!
$ sudo /etc/init.d/udev restart
So now my printer connects and my phone connects directly to the laptop. I'll try the hub now and then i'll restart my computer to see if i can still works.
Thanks Favux, I appreciate the post.

---

### Post by SuperGiraffe on 2009-06-15
Turns out that the Cypress Tetrahub USB 2.0 is part of the laptop, even though there are only 3 USB ports.
[edit]
After a few minutes of detecting the new phone or launching wammu mobile phone manager, the X window manager restarts and flashes back to a terminal window with the following messages and continuously restarts.

```
module ssb is in use by b44
using Timidity ALSA midi emulation

```
For the TX2000 there is a config file edit that is required for wireless LAN to work and I think this is related to that somehow but I can't be sure, maybe these are the config line immediately before the problem. Can someone recommend error logs in /var/log/ that would help determine the problem? Thanks.

---

### Post by brainsqueezer on 2009-08-23
Anybody had problems with latest nvidia drivers (185.18.31)?

[http://www.nvnews.net/vbulletin/showthread.php?t=137772](http://www.nvnews.net/vbulletin/showthread.php?t=137772)

---

