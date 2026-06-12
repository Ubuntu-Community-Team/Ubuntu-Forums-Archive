---
title: "Ati HD4870+Jaunty=No graphic acceleration."
date: 2009-09-05
forum: Hardware
---

### Post by Galban on 2009-09-05
Since day one when upgrading to Jaunty I lost graphic acceleration, so no more Compiz. Like always, at every upgrading of Ubuntu I got hard time setting up again and again the xorg.conf to get it back with the direct rendering up. But this time, we are almost at the release timing of Karmic, and I'm still unable to activate the Desktop Effects on Jaunty. Curiously, in the forums there is almost nobody complaining about Ati's recent GPU's (like HD4870) and getting them full 3D accelerated on Jaunty! Am I doing something wrong?
I'm suspecting now even at my MOBO's chipset.

Please help. Thanks.:confused:

---

### Post by Yellow Pasque on 2009-09-05
This usually gets fglrx/Catalyst up and running: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by Galban on 2009-09-05
> **Temüjin said:**
> This usually gets fglrx/Catalyst up and running: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

And this give me usually a fglrxinfo showing Mesa drivers and after rebooting a blank screen with the message "Input not Supported", which makes me think it could be the resolutions on the xorg.conf but even though after putting some resolutions in the screen section, the blank screen still coming up. I've been trying the ATI's way (custom and automatic), this very "HOWTO" too, and many others things and the result it is the same... "Input Not Supported". My screen (less that 2 years old) is an Acer AL1706 and it is making me doubt if maybe it is itself the problem. I don't know, it looks like libGL libraries are conflicting against each-other again like I found it was the case on 2006 for Dapper with Radeon GPU's. Once and only once I got an error message from fglrxinfo complaining about something avoiding to have DRI to be up and running. And I repeat, it has been like this since and only after upgrading to Jaunty.

Thank you anyway for your time and for your suggestion to watch at this HowTo. Any other ideas will be greatly appreciated.

---

### Post by Galban on 2009-09-14
No acceleration possible with an Acer AL1709 LCD monitor. I got a new one (monitor) and fglrx is working.

---

