---
title: "Kubuntu 14.04 How do I add HP 648c printer when it's not detected/seen?"
date: 2014-04-19
forum: Hardware
---

### Post by zapjb on 2014-04-19
Specs: asus a7n8x vm 400 with integrated Nvidia nforce2 graphics, 2500 Athlon Barton, 2x 512MB pc3200 DDR RAM with HP 648c parallel port.

Problem is I don't know how to add my HP 648c printer in Kubuntu 14.04. It is not detected (it is turned on). I searched & searched, tried various "fixes". It's weird cause at least a half dozen other distros worked ootb or had easy walk throughs including other 14.04 buntus. Anybody know how and give or link me to instructions. 

The reason I installed Kubuntu is I tried at least 12 distros including 14.04 ubuntu & 14.04 flavors lubuntu, xubuntu, and gnome. Also tried a few older ubuntu and their offspring. And Puppy and many of the Distrowatch suggested distros for older computers. The only distro that had full functionality after a live session and install is Kubuntu. Minor video twitching but nothing compared to the other distros.

Thanks.

---

### Post by carl4926 on 2014-04-19
Did you try cups web interface
[http://localhost:631/](http://localhost:631/)

---

### Post by zapjb on 2014-04-19
Yes I tried that on Kubuntu & the walk through just said some sort of HP sockets or something. The weird part is in other distros [http://localhost:631/](http://localhost:631/) listed my specific printer & the walk through was easy-peasy.

But not in Kubuntu.

---

### Post by carl4926 on 2014-04-19
Couple of things I's try.
Ubuntu live dvd - go to settings : printer - see if it picks it up

Have you installed hplip

---

### Post by zapjb on 2014-04-19
hplip is installed. but i cant locate it to open it. 

now i'll try Ubuntu live dvd - go to settings : printer - see if it picks it up

---

### Post by SeijiSensei on 2014-04-19
> HP 648c printer serial port
I presume by "serial port" you mean a USB connection?  Does the device appear if you run "lsusb"?  I have a Photosmart that has this corresponding entry:
```
Bus 001 Device 004: ID 03f0:c202 Hewlett-Packard PhotoSmart 8200 series
```

Also try disconnecting the cable from the printer, then open a terminal and run 
```
sudo tail -f /var/log/syslog
```
Now plug the cable back in.  Do you see log entries that it has been detected by the OS?

---

### Post by zapjb on 2014-04-19
Fixed I think. Too tired to see if fix survives a reboot but it should. Later I'll post about my nvidia card. lol.

Thank you carl4926. This is what worked. From Wilders Security.

"You need to also install hplip-gui. Then you should find it under System in the start menu, titled 'Printer Toolbox.' "

---

### Post by carl4926 on 2014-04-19
> **zapjb said:**
> Fixed I think. Too tired to see if fix survives a reboot but it should. Later I'll post about my nvidia card. lol.

Thank you carl4926. This is what worked. From Wilders Security.

"You need to also install hplip-gui. Then you should find it under System in the start menu, titled 'Printer Toolbox.' "
Well done!

---

### Post by zapjb on 2014-04-19
lol. Thank you. It does survive a reboot. There's a HP icon logo in the taskbar now though. Bit scared if I removed it, it'd fubar the printing.

I just saw my Join Date: May 2007. Funny been using different distros. Came back here for help & forgot my pw. Site said wasn't registered. So I did & shazam my original join date.

And I don't think I'll forget "sudo apt-get install _____" for a while either. :)

---

