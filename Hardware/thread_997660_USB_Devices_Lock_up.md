---
title: "USB Devices Lock up"
date: 2008-11-30
forum: Hardware
---

### Post by mel_phil@flashmail.com on 2008-11-30
Hi,

I have done a customised basic or "Lite" install of ubuntu. Have got it up & running however I am having problems with USB. I plug in any (Have tried 3 different USB type devices)USB device, I then go to the main menu & choose places & I can see the USB device there but when I try to access it the PC will lock up & the only way out is to hit ctrl-alt-delete & do a restart of the PC. I have noticed that I do not get the icon on the desktop when I plug the device in either.

I used Ubuntu Server 8.04 to install a command line only system. Once the system was installed I ran the following from the command prompt

* sudo apt-get remove linux-image-****-server
* sudo apt-get install linux-image-****-generic
* sudo apt-get install xorg
* sudo apt-get install gdm
* sudo apt-get install gnome-core
* sudo apt-get install usplash usplash-theme-ubuntu
* sudo apt-get install ubuntu-gdm-themes
* sudo apt-get install synaptic
* sudo apt-get install startupmanager

I was then able to boot into Ubuntu GUI & installed the following from Synaptic

fast-user-switch-applet
samba
gnome screensaver

In troubleshooting this problem I looked through Synaptic & installed the following

usbmount

I don't know if I have any parts or dependencies missing.  Also I have done both a standard Ubuntu & Kubuntu 8.04 installation & the USB is fine so it is something I have missing or not configured correctly in this custom config. Any help is greatly appreciated to get this working. Any other advice on components I may need in my install is also appreciated

Cheers

PS

---

### Post by cariboo on 2008-11-30
What is th output of dmeag when you plug a usb device in? In a terminal type:

```
dmesg | tail -n 10
```

This will print out the last 10 lines of demsg, which may indicate what the problem is.

Jim

---

### Post by mel_phil@flashmail.com on 2008-11-30
Hi,

Thanks anyway. What I wanted was a clean install of Ubuntu with all the backend & essential stuff such as printing, Wireless & Bluetooth etc but without all the bloat & programs. I have found more things that just don't work (Missing dependencies & files etc)since writing this post. I think it may be quicker to do a standard install & just Add/Remove the programs manually as running an I.T business, a family with 3 Kids & playing in bands does not leave enough time to work all these probs out. Anyway many thanks for the rapid reply & advice I did learn something

Cheers

PS

---

