---
title: "HP Laserjet P1102 problem"
date: 2010-09-27
forum: Hardware
---

### Post by xzibit12 on 2010-09-27
hi,

I'm having problem with my printer connection. I installed the printer in widows 7 ultimate pc and shared it to everyone.

I tried to connect to the printer with my ubuntu lucid with samba... And i got this error on ubuntu pc... /usr/lib/cups/filter/hpcups failed

I also update the ubuntu pc with the latest hplip

What could be the problem.

---

### Post by starnixsa on 2010-10-08
Hi,

Try opening up a terminal (Applications > Accessories > Terminal or Ctrl+Alt+t) and type hp-setup followed by enter. Follow the on screen instructions and allow the downloading of the plug-in. 

If that doesn't work, try deleting the printers and try the method on [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html).

I had no problem with printing after I attempted the second method (printer was not listed in the drivers list and a driver was automatically selected as Photosmart 1100 for me).

I hope that helps.

---

### Post by sbergman on 2011-07-26
I've experienced similar problem(s) with the HP laserjet P1102:

- When I plugged the USB printer in, Ubuntu would immediately detect a printer, but I could not print. 
- When I ran hp-setup it would not detect any devices.
- When I tried installing an updated hplip-3.11.7.run it would get stuck when trying to detect a network and fail at that point. See this bug [http://bugs.launchpad.net/hplip/+bug/724625]("http://bugs.launchpad.net/hplip/+bug/724625"). I am connected from South Africa so I assume google.com would direct to google.co.za and cause the connection test to fail.

Anyhow,

I managed to solve the problems by making use of the foo2zjs driver. Here's the install instructions: [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/")

---

### Post by wildcoast on 2011-08-23
What is the reason for HP's proprietary plugin?

Why (the hell) isn't it automatically installed from the CD?

OSS? (Open Source Sabotage)

---

### Post by bstjon on 2011-10-05
i had this same problem and, like starnixsa, used steps [here]("http://hplipopensource.com/hplip-web/install/install/index.html").  after that, installation and connection worked fine.  I think it's this particular model -- i've installed other hp printers with these [basic steps]("https://help.ubuntu.com/community/HpAllInOne") and never had any trouble.

---

### Post by teloris on 2011-11-22
hi all,
i have same problem too
this is my network schema :

ubuntu (192.168.1.14) ==> xp (192.168.1.19)

HP Laserjer P1102 attached at xp (192.168.1.19) and i want to print through LAN (as my win7 can do).

i have tried some tricks mentioned above, and still nope :sad: (their method will work if printer attached locally through USB / LPT).

any suggestion will very appreciated

ps : i have upgrade my ubuntu to 11.04 and still no driver for this printer model :(

---

### Post by Fisher on 2012-01-11
A thing that I just cannot understand:
Why the hplip package that supports the printer does not comes with the install CD?
Maybe it's the OSS theory (Open Source Sabotage)!!!

---

