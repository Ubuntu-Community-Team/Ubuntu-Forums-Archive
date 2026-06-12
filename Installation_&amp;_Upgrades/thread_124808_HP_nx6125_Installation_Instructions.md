---
title: "HP nx6125 Installation Instructions"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by nickpaton on 2006-02-02
(Edited from original post)

For anyone trying to install Ubuntu on an HP nx6125, and have been trying as suggested in numerous posts

[http://www.kastor.org.ar/hpnx6125/](http://www.kastor.org.ar/hpnx6125/)

The new correct hyperlink is:

[http://www.kastorhq.info/hpnx6125/](http://www.kastorhq.info/hpnx6125/)

---

### Post by nickpaton on 2006-02-02
OK, I've got the laptop working, and am posting what was required, having pulled stuff from various posts.  I'm also writing commands out in full, since there is a good possibility that noobs (like myself) will have the same problems as myself.

Having carried out the initial install and reached the Ubuntu login prompt:

login and password using the ones requested earlier in the install.

This takes you to (in my case) nick@ubuntu.

I then had to login as root to configure xserver:

sudo -s 

To get into xserver and configure it, type (taken from a WIKI on these forums but lost the link):

sudo dpkg-reconfigure xserver-xorg

The critical question to get xserver working is selecting the correct video device from a list.  In mine "ati" was already highlighted.

Select instead "vesa".

Leave the ATI card identifier as is.

Assign 131072 kB (128MB) of onboard memory for the video card.

Attempt auto monitor detection.
Leave the 'Generic Monitor' Identifier in next window.
I then selected  a resolution 1024x764
Select 'Medium' monitor characteristics
Select 1024x768 @60Hz
Select 24 for color depth

Finally you will arrive at root prompt again, so restart:

shutdown -r now

and restart, and hopefully take you into Ubuntu (or Kubuntu).

I haven't yest got wireless going but there's a lot of info around.
The reason for having to reinstall was that trying this first time aroung bombed my set up.
If/when I get this going I'll maybe give some nx6125-specific instructions if any different to what's posted.

If anyone with more knowledge than me wants to add or take out of this, please feel free.

---

