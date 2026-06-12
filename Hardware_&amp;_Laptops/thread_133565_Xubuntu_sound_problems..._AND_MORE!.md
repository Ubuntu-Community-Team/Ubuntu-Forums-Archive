---
title: "Xubuntu sound problems... AND MORE!"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by Wonka_Vision on 2006-02-20
Hi there. I'm not too sure if this is where I should be posting Xubuntu related stuff, but I figured I'd try anyway. 

I am running Breezy Badger Xubuntu (Ubuntu with Xfce4.2 frontend) on a Thinkpad A31 laptop with 128mb memory. I have previously used Breezy Badger Ubuntu (gnome) on it and had no problems. All hardware was detected and configured properly. However with Xubuntu I am having some problems with sound. 
When I enter or exit the system, it makes a system "Beep", but that's about the extent of the audio I am able to enjoy at the moment. 
I have ALSA installed and I turned ALSA-mixer up, but to nuttin. lsmod returns that all of the required audio drivers are bring run. I am guessing that there is something blocking the sound, but I don't know where to begin looking...
Alsamixer says the card is Intel 82801CA-ICH3 

Any help would be fantastic!

Oh and another small problem... I have a USB key with FAT32 and it's mounted under /dev/sda and linked to /media/usb0. When I open that directory, none of the files are shown.

Thank you all in advance!

Mat

---

### Post by Wonka_Vision on 2006-02-20
Okay well I actually just figured it all out. 

I had to edit the /etc/esdsound/esd.conf file and replace 5 with 2.

For the USB key, I mounted manually with mount /dev/sdb1 /media/usb1
I had to mkdir /media/usb1

Xubuntu is light alright.. in that it has nearly no config apps!

---

