---
title: "Toshiba screen resolution and lost wireless connect"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by RKelly5327 on 2006-09-05
Gang, I did run the Xubuntu and it ran fine. Ran the Live desktop version. Get this- My wireless adapter ran great and I got right on the net. I thought "This is fantastic. I'll go ahead and install it." But guess what, after I installed it I could no longer get an internet connection. I have no idea how to get it going, especially since it ran fine with the Live Desktop CD! PLUS, the screen resolution is terrible! It has one lesser setting, 320x240, so I don't know what it's running at and don't know how to tell. I do know in Windows 2000 and XP it will run at 800x600 and looks halfway decent. I forget what the color sets at in 2K and XP, but it's not too bad. In this XUbuntu the thing looks pathetic. When I saw Xubuntu closing the installer getting ready to reboot, and the ton of stuff it was removing and deleting, it's no wonder the wireless card won't work! If you read this and know what I can do to improve it with drivers from Ubuntuland, or whatever, let me know. And don't forget the wireless adapter. It's a GFE!?!?!
Thanks,
Ron K

---

### Post by renesisspeed on 2006-09-05
I Also just installed xubuntu on an old toshiba laptop and was having the same problems.

I was able to solve the wireless problem with this guide [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns)

as for the resolution, I found another post saying you could edit the "xorg.conf" file to add another resolution. Maybe it will work for you, but when I try to save it I get an error "Cant open file to write"

---

### Post by RKelly5327 on 2006-09-05
What model is your Toshiba? Mine is a 2100CDS I believe. It's in the other room. I could go look but I have a broken foot. :???:  Where in the world is that xorg.conf file you mention? You say you couldn't open it? How do you find it in the first place? I wonder if you have to have some sort of permission to access the file. 
I sure hope I can do something about the resolution. It really looks sick.
Thanks for replying.
Ron K.

---

### Post by renesisspeed on 2006-09-05
Mine is a Tecra 8000

The xorg.conf file is located @ filesystem/etc/x11/xorg.conf

What you do is scroll down to where it says: 
Section "Screen"

And add another subsection like this for example:

SubSection
    Depth      24
    Modes      "1024x768"
EndSubSection

... Just for example.

I can open it no problem, I just cant save it

PS I'm a noob :-)

---

### Post by RKelly5327 on 2006-09-05
I is a newbie too. My resolution won't go that high, but I sure would like to at least get the 800x600.
rk

---

### Post by renesisspeed on 2006-09-05
I would like to see mine at 800x600, but i need to be able to save the file first or, find some other way](*,)

---

### Post by el.motar on 2006-09-06
hi guys,
to be able to edit the xorg.conf file you need admin privileges.
This should do it.
sudo gedit /etc/X11/xorg.conf
atb

---

### Post by renesisspeed on 2006-09-07
That did the trick thanks el.motar:-)
Except for the fact that in xubuntu it seems I have to use Mousepad, so: sudo mousepad /etc/X11/xorg.conf

However, after I did this and rebooted, xserver failed to start.
Since I'm a noob I have no idea what this does but running this command seemed to do the trick "sudo dpkg-reconfigure xserver-xorg"

and then starting xserver "startx"... (I think)

And now I am happily at 800x600 resolution :-)

P.S. unless I missed it and it already is, this should be like a faq or something as I have noticed people with what seems to be the same problem in other posts ;-)

---

