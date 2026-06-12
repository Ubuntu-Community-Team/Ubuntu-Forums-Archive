---
title: "USB broken? CH joystick and pedals not working anymore"
date: 2014-06-11
forum: Hardware
---

### Post by MikeCyber on 2014-06-11
Hi
my CH sticks and pedals worked fine but suddenly stopped. Then they worked again for some days and now they're death again.
What to do? Is USB or udev broken in 14.04? At least udev smacks insanely buggy. :frown:

---

### Post by Kirboosy on 2014-06-11
I can see that this isn't the first time you have posted about this. I found this link on another website that discusses how to fix their controller on Ubuntu 13.10. Hopefully the information on it will clear up your issue and you can get back to enjoying your sim.
[URL="http://forums.x-plane.org/index.php?showtopic=71300"]
Upgraded to Ubuntu 13.10 and now CH Pedals not working in X-Plane 10.22[/URL]

Hope that helps!
~Caboose

---

### Post by MikeCyber on 2014-06-11
I did that and I didn't want to post in that forum again. That even helped for some weeks. Unbelievable that usb is not working in 14.04! :cry: Udev devs go home.

---

### Post by Kirboosy on 2014-06-11
Perhaps the permissions have become skewed again. Have you checked the permissions on them since the issue started happening?

It seems that these controllers have had issues for a while now. [LP Bug #500834]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500834")

I've also seen a few people report success using the program [QJoyPad]("http://qjoypad.sourceforge.net/"). That might be another item to look into.

Hope that helps!
~Caboose

---

### Post by MikeCyber on 2014-06-12
I confirm Udev is broken. Worked this morning but after lunch not anymore.- I never had any problems at all on 12.04. They worked out of the box always.

---

### Post by Kirboosy on 2014-06-12
It appears that your CH Joysticks/Pedal arent compatible  with Ubuntu  14.04 at the moment, perhaps you can stay with 12.04 until the issue is  fixed.

~Caboose

---

### Post by Pablo_San_Martn on 2014-10-04
For my PS2 joystick, this problem has been solved in the latest update for **udev** in trusty, so just run the **Software Updater** or open a **Terminal** and enter

  sudo apt-get update 
sudo apt-get upgrade

---

