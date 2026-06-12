---
title: "ati driver"
date: 2008-07-04
forum: Hardware
---

### Post by sonaural on 2008-07-04
i installed the ati driver suggested by my ubuntu system and the graphics got worse.

when i restarted after the install a window popped up before the system had fully loaded that said no driver was detected and directed me to reconfigure the system.  i tried both doing and indicating the model of graphics accelerator, etc and reinstalling the whole os.  neither worked

i tried uninstalling the driver to no avail

---

### Post by brunolabs on 2008-07-04
Try the drivers available on the ATI official website.

[http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html")

---

### Post by Ashejoe on 2008-07-04
OK, I pretty much have the same problem:

I downloaded the appropriate drivers for my ATI 9600 All-In-Wonder card, but Ubuntu 8.04 won't let me install it !

Instead, it begins to initiate the install, then STOPS saying that I'm not a "Super User". 

I attempt to go into the Konsole and type in

sudo ati-driver-installer-8-6-x86.x86_64.run

and it still refuses to install it, again, claiming I'm not a Super User.

Now what ?

---

### Post by ProbablyX on 2008-07-04
I had this issue with some installer. I had to mark it as executable first
chmod +x ati-driver-installer-8-6-x86.x86_64.run

then run it from GUI by clicking on it.

Else you can try entering su mode by doing:
sudo su
this will open a ROOT terminal now run
ati-driver-installer-8-6-x86.x86_64.run

then type
exit

to leave root mode once done

---

### Post by Ashejoe on 2008-07-04
Hey thanks.... that did the trick !  (sort of...)

The "ATI Drivers" now work, but not the TV tuner portion of the card ?  (Unless I need to some how initiate that portion of the hardware ??

Thank again.):P):

---

### Post by larry61 on 2008-07-05
I installed driver and best graphic I could get is 800 x 600 with my 9500 pro. Got driver fglrx from ati site directed to from this forum.

---

