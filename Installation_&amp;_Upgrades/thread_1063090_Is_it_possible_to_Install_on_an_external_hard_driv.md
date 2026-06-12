---
title: "Is it possible to Install on an external hard drive?"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by Rickmasta on 2009-02-07
I search, but sorry, I found nothing.:(

So, I have my computer, Windows vista, and I just can't install over it, BUT I do have an external hard drive going to waist, it's a 500g.. And I wonder if I can **install** on this hard drive, and make all changes and such, save on this hard drive (Downloads, changes, anything that has to do with ubuntu).  :p. So yeah, does anyone have any suggestions, links, guides? I don't want to just hit like "Try ubuntu" every time I boot it, I actually want to install it, but not install it on this computer, just on that hard drive, so anytime I load that hard drive, it boots ubuntu.

Also, is it possible that I can install it without removing everything that's currently on the external hard drive? Like, without formatting it?

Thanks in advanced, sorry if there's a thread already on this. :KS

[COLOR="Red"]Edit:[/COLOR] I forgot to mention, I'm a totally newbie at ubuntu, this is my first real attempt at installing ubuntu, or any Linux (before I would just do that "Try ubuntu without changes to your computer").

[COLOR="Red"]
Edit #2:[/COLOR] I read over my thread, and it wasn't so clear. So just clearing it up,

**_What I want?_** To be able to keep my current OS on my computer untouched, and *install *(actually install, not the "Test before installing") ubuntu to my hard drive, so that when I'm starting my computer I can just boot it from my External hard drive, and have it just go to my ubuntu. I want all changes, settings, files I made, Files I downloaded, on ubuntu, to be saved on this hard drive.

Also, this is a USB hard drive, It is a Maxtor **Model:** [*Maxtor  Personal Storage 3200*]("http://www.google.com/products/catalog?hl=en&client=firefox-a&rls=org.mozilla:en-US:official&hs=jJ4&q=maxtor+personal+storage+3200&um=1&ie=UTF-8&cid=13769689059161193348#ps-tech-specs"). 500GB. 

Any more info, just ask.

---

### Post by Tim Sharitt on 2009-02-07
I don't see any reason you shouldn't be able to install to an external drive. 
If you want to install grub to the mbr of the external drive and leave the internal alone, you will need to change the install location for grub to that drive (I believe you do this on the last part of the pre-install setup before commiting the changes). The default is probably (hd0) which is the internal drive, you can change it to (hd1) to get it installed to the external drive (assuming you have one internal and one external hard drive).

---

### Post by avtolle on 2009-02-07
[https://help.ubuntu.com/community/Installation/#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation/#Installing%20on%20external%20or%20RAID%20hard%20disks) may be of assistance to you.

---

### Post by Rickmasta on 2009-02-08
Lol, I need this stuff, Dumbified.
(Also edited info to original thread)

[COLOR="Red"]Edit:[/COLOR]I believe I found what I wanted; [http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/) Now, just to be sure, if I use that, will it save anything I do on ubuntu to this hard drive, and does it work for the latest version of Ubuntu?

---

### Post by PurposeOfReason on 2009-02-08
Yes. As long as GRUB is installed on the external HDD, you should not have any problems. However, external HDDs are typically slower and not designed to have to support an OS.

---

