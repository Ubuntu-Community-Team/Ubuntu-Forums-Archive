---
title: "Install Via USB and Remote Access"
date: 2008-11-26
forum: General Help
---

### Post by GavFre on 2008-11-26
Hello everyone:)

This is my situation, hope someone can guide me in the right direction.

I have a computer upstairs that works fine (but is very load) and I also have a Compaq Ipaq, which has no CDRom drive.

What I want to do is install Kubuntu onto my 700GB USB HD and boot the Compaq from that. All I want this computer to do is sit next to the router and download files from the internet using Utorrent out of peak times (11pm till 8am) and then for me to transfer these files across my LAN to my main computer

But I want to be able to control this computer (compaq) from my computer upstairs as the compaq will not have a monitor attached to it.

I have started downloading this tonight..

[http://www.pendrivelinux.com/2008/11/04/usb-kubuntu-810-persistent-install-using-windows/#more-641](http://www.pendrivelinux.com/2008/11/04/usb-kubuntu-810-persistent-install-using-windows/#more-641)

But if someone would be kind enough to tell me weather I am doing the right thing or indeed have a better suggestion I would be very grateful

Thanks

Gav

---

### Post by jimv on 2008-11-26
That sounds fine.  What you do is when you're installing Ubuntu, select the USB drive to install to.  Then, on the last step of the installation, click the Advanced button and make sure that you set GRUB (the boot loader) to be installed onto the USB drive, not your computer's internal HD.

Then, once you've go it installed, you'll need to boot up Compaq, and enable Remote Desktop (System > Preferences > Remote Desktop), and also enable automatic login (System > Administration > Login Window > Security).  Then when you turn the machine on, it will automatically log you in and enable Remote Desktop so you can remote in.

---

### Post by GavFre on 2008-11-26
Great thanks for the reply:-D. One last thing which you mention and I cant find anything on, when I turn the machine on downstairs how would/do I connect to it? via my web browser? or some other way

---

### Post by jimv on 2008-11-26
Are you using Kubuntu or Ubuntu (i see the Kubuntu tag, but I want to make sure).

---

### Post by GavFre on 2008-11-26
Kubuntu, I am basically following the install guide from here>

[http://www.pendrivelinux.com/2008/11/04/usb-kubuntu-810-persistent-install-using-windows/#more-641](http://www.pendrivelinux.com/2008/11/04/usb-kubuntu-810-persistent-install-using-windows/#more-641)

---

### Post by GavFre on 2008-11-27
Ive looked at using VNC but this will not allow me to transfer files over my network from one computer to another.

Is there another method?

Thanks

---

