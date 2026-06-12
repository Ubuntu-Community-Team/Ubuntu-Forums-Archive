---
title: "MacBook Pro, VMware Fusion 2.0.4, Ubuntu 9.04 Trackpad"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by davidkachel on 2009-05-15
I have buntu 9.04 running on a MacBook Pro inside of VMware Fusion 2.0.4.
The trackpad is glacially slow. I found this on the internet:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux" 
Option "Protocol" "auto-dev"
Option "MinSpeed" "0.60"
Option "MaxSpeed" "1.10"
Option "AccelFactor" " 0.030"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
EndSection

and added it to the xorg.conf file.

It helps, a little bit, but not a great deal. I even upped the min and max speeds a lot and it made little difference.

Is there a fix for this somewhere? Is there a driver I should be installing?

TIA

---

### Post by davidkachel on 2009-05-18
Wow! Nobody out there has Ubuntu running in VMware fusion on a MacBook Pro with slow trackpad problems?

I sure could use some help here. Under these circumstances Ubuntu is not quite useless but it is darn close.

dk

---

### Post by davidkachel on 2009-05-20
Hello??!!

BIg echo in here.

---

### Post by maflynn on 2009-05-20
AFAIK, VMware has not updated its tools to be compatible with Jaunty.  I had played with 9.04 within fusion myself but found it cumbersome because the lack of vmware tools.  

If you're intent on running Ubuntu within vmware, then I suggestion you either downgrade to 8.10 or wait until vmware updates its software.

---

