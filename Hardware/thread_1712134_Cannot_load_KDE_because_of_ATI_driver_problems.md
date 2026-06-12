---
title: "Cannot load KDE because of ATI driver problems"
date: 2011-03-22
forum: Hardware
---

### Post by SpectrumDT on 2011-03-22
Hello. I am a fairly new Ubuntu user running Kubuntu 10.10. My video card is an ATI Radeon HD 5750. I have been having problems with this card. I have switched back and forth a few times between the proprietary ATI driver and the open source driver. Most recently I have installed the proprietary driver (through the "Additional Drivers" application). 

Now, after a reboot, I cannot load KDE. Kubuntu boots into a command line instead. 

I do not get any error messages, so I do not know if KDE is broken. I only know that Kubuntu does not launch KDE on its own, and I don't know how to launch it from the command line. 

Can anyone help me debug this problem? 

Thanks in advance.

---

### Post by mastablasta on 2011-03-22
startx   command should give you some messages on what is going on. this is command to start the desktop interface.
 
if the opensoruce drivers work you could do a purge of additional drivers and try to install them manually. 
 
What KDE are you using? default? then perhaps and upgrade to 4.6 might be in order.

---

### Post by SpectrumDT on 2011-03-22
Thanks for the reply. 

I got KDE working again. It turns out I had a bad xorg.conf file. I deleted /etc/X11/xorg.conf and KDE came back. :)

I am running KDE 4.5.1.

---

