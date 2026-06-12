---
title: "External 56k modem issues with 6.10"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by darclaird on 2007-05-10
Hi,

I'm having some issues with (K)Ubuntu 6.10 and running an external dialup modem.

I am currently between houses and have been forced to resort to dialup for a little while, I had an old Lucent Winmodem kicking about, but even Windows XP wouldn't play nicely with that so I went out and bought a D-Link DFM-562E external modem. which (kinda nedless to say) I have no issues with under WinXp, but on the same machine Ubuntu wont recognise it at all, I have tried directing to to /dev/ttys0, /dev/ttys1 and no response from the gnome networking panel (which worked fine on my lappy with an inbuilt winmodem under 6.06) and wvdial baulks at it every time I try

The machine specs:
AMD Sempron 2800+
ASUS AN78X motherborad (nforce2 chipset)
512MB of generic ram

The modem is a D-Link DFM562E it is attached to an onboard serial port, which is acitvated within bios and can be seen from Device manger in GNOME and registers and COM! in Windows

I am contemplating an upgrade to 7.04 but dont want to hazzard it without knowing the modem will work (thought I may wait until I have broadban reconnected)

Thanks muchlyu in advance

dl

---

### Post by maniac_X on 2007-05-12
> **darclaird said:**
> 
I am contemplating an upgrade to 7.04 but dont want to hazzard it without knowing the modem will work (thought I may wait until I have broadban reconnected)


Some of the issues people have been facing are noted in this thread that refers also to a bug report: [http://ubuntuforums.org/showthread.php?t=391956](http://ubuntuforums.org/showthread.php?t=391956)

Try Dapper (6.06). Edgy/Fiesty are having issues with regard to dial-up. As for modem, I have both the Actiontec 56k v92 external EX560LKA serial modem and Actiontec 56k v92 external EX560LKU serial/usb modem(only using the serial portion) both of which worked flawlessly in Dapper. Not working in Fiesty yet. If I find a solution, i'll post.

**EDIT** Have since installed Gnome-ppp and have no issues getting online.

---

### Post by guysmiley25 on 2007-06-12
Did you get your modem working?

I thinking about getting the [D-Link DFM-562E]("http://www.ascent.co.nz/productspecification.aspx?ItemID=334085"). But I do not know if it will work!

[Here]("http://ubuntuforums.org/showthread.php?t=467818&page=2") is my thread.

Thanks.

---

### Post by mike555 on 2007-06-12
I have had good luck using the Zoom external serial modem ......    [http://www.zoom.com/products/dial_up_external_serial.html](http://www.zoom.com/products/dial_up_external_serial.html)    ... here in Fl. USA  one can get it at Staples for about $50.

---

### Post by guysmiley25 on 2007-06-12
Do not think I can get it here in NZ however I will look around.

By good luck what do you mean? Did you have to install a driver, or did it just work? Are you using Dapper/Edgy/Feisty etc?

I'm confident using wvdial/gnome-ppp, I just know I need a working /dev/modem for it to work.

If I can plug it in, and the /dev/modem appears. Then that is what I would consider good luck. I would not mind installing a driver of some sort, as long as it is not too hard.

Thanks.

---

### Post by guysmiley25 on 2007-06-12
How about that [D-Link DFM-562E]("http://www.ascent.co.nz/productspecification.aspx?ItemID=334085")?

---

### Post by darclaird on 2007-06-12
Yes, running wvdialconf got it going no worries
has been quite serviceable though now I have restored my braodband so its sits here unused

Cheers

Justin

---

### Post by guysmiley25 on 2007-06-12
Did you have to install any drivers or did it just work out of the box?

Thanks

---

### Post by darclaird on 2007-06-12
I should run a quick howto

1) Buy modem
2) connect modem to pc
3) install gnome-ppp
4) in a terminal type "wvdialconf" let it do its thing
5) run gnome-ppp fioll in appropriate details
6)  hit connect

I had some routing issues to do with my lan that I wotn go into.... but they were easily worked around

Justin

---

