---
title: "HP Photosmart 7760 issues"
date: 2011-06-21
forum: Hardware
---

### Post by EriktheAwful on 2011-06-21
I built a new computer running Ubuntu a few months back and am really enjoying the experience more than Windows. However, I have never been able to get the printer working right. I installed the hplip package and according to linuxprinting.org it should run perfectly.

I am running natty on an AMD Zacate/ASUS motherboard and the printer is an HP Photosmart 7760.

I can only get it to print if I have the printer unplugged, turn on the computer, plug the printer in, and then turn the printer on. After one document prints I'm done and have to reboot to print any more. If I leave the computer on a while and the printer goes to sleep, it will not wake up when I print. As much as I hate memory resident programs, I installed the hplip gui to try and sort it out. I get prettier error messages, but can't print a test page.

On a related note, does anyone know how to get a Panasonic Panafax DX-1000 network laser printer working? It's ancient and all the information on it seems to have dropped off the internet.

---

### Post by dFlyer on 2011-06-21
When you say you install the hplip package was that hplip-gui. I have the 8250 photosmart and it work perfectly with linux. I've been using it for the past 7 years without a problem. I was having problems with the printer until I started using the hplip-gui.

---

### Post by EriktheAwful on 2011-06-21
I believe it found the printer upon initial installation and installed hplip. Today I read about hplip and checked the package manager to find it already installed, so I installed the hplip gui to see if it had any more information. I get a nice HP icon now whenever I fire the computer up, but it doesn't help any. I'd really rather get rid of the gui and not have to know when my ink cartridge is less than 90% full.

---

### Post by EriktheAwful on 2011-06-24
No ideas?

---

### Post by dFlyer on 2011-06-24
Do you connect it visa usb, serial or lpt. I believe it is usb but could be wrong. My problem with the hp8250 before installing the hplip-gui was print 4x6 inch prints. I was never able to get a borderless print. Installing the hplip-gui solved that problem. My computer is setup as usb and works great. What ppd are you using? If it's the cups ppd you might want to change it to the hp ppd for your printer to see if that helps. Sorry I can't be of much more help.

---

### Post by EriktheAwful on 2011-06-26
I connect with USB. I have no idea what ppd or cups are, and I'm not at home with my computer, so I just now googled ppd and found this thread:
[http://ubuntuforums.org/showthread.php?t=182332](http://ubuntuforums.org/showthread.php?t=182332)
 
I'm thinking this is my problem, so when I get home I'll look into it. Thanks!

---

### Post by EriktheAwful on 2011-06-26
[http://hplipopensource.com/hplip-web/models/photosmart/photosmart_7700_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_7700_series.html)
 
This is leading me to believe that cups/ppd issues are not my problem. I will go through the cups setup steps anyways to make sure.
 
I did some more research on the Panasonic and discovered that it's NOT a laser printer. It's purely a fax machine that has the ability to fax over the internet with additional software. Crap, no wonder I got it for near free. It works well as a copier, but I need a laser printer.

---

### Post by EriktheAwful on 2011-06-26
I don't think it's a cups or ppd problem. The computer sees the printer just fine, and hplip thinks it's communicating just fine with the printer - it even tells me the ink is low (although it's full). It looks like the printer just isn't doing what it's told.
> If it's the cups ppd you might want to change it to the hp ppd for your printer to see if that helps.How do I check to see which ppd is being used?

Edit: I went to "Make and Model" in the printer properties and found two drivers, hpcups and hpijs. I switched it from hpcups to hpijs, but it didn't make a difference.

---

### Post by EriktheAwful on 2011-06-29
I still can't print from Ubuntu. I found more info on the Panasonic DX-1000 and got it printing from a windows computer, but I need a ppd file for it. The HP7760 is still a brick for me. Ugh. Does anyone know of a ppd for a "normal" Panasonic printer that would work? How simple are ppd files? Is it something a bumbling fool like myself could write?

Edit: The Panasonic is plugged directly into the wireless router. My wife's Windows 7 laptop can't find it yet.

---

