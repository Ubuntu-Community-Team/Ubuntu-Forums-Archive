---
title: "Joystick problem..."
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by Rasputin_III on 2006-05-31
I have a Logitech Rumblepad 2
([http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2225,CONTENTID=8674](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2225,CONTENTID=8674))
and seem to be having some problems getting it to work in any application
other than the joystick calibrator.

First off, I doubt this is a dapper specific issue, and is likely going to be a simple
fix, but I've been pulling my hair out the last three days, and am at my wits end.

The calibrator recognized all buttons, and both joystick movement; but any game
I've tried to play (and even the js_demo) program will only acknowledge the buttons.
I get no response when moving either stick.
I've also tried switching "modes", and used the + directional, but it didn't work either.

Any ideas?

Oh yeah, this is a USB controller.

Ras

---

### Post by Rasputin_III on 2006-05-31
Ok, this has turned out to be a bug of some sort.  Possibly with the calibration
program?

Deleting the .joystick file and rebooting (removing & reinserting the module
probably would have done it as well) fixed the problem.

Once the system came back up, I ran gl-117 WITHOUT calibrating the controller,
and it worked fine.

I then exited, calibrated the joystick, and restarted the game--and it stopped
working, exhibiting the aforementioned symptoms.
The joystick continues to malfunction until a reboot/reinsertion.

Hmm...

Ras

---

### Post by coco_ on 2006-11-07
I have the same issue with a logitech wingman extreme digital 3d joystick.
i found (i dont remember where) that this problem is because how ubuntu threats the joystick:

jscalibrator can understand the "input" interface, but common games and old apps cannot understand the "input" interface because they use the old classic interface.
i supose that ubuntu depelopers can make the joystick run in the vanilla mode so as js_demo, vegastrike, flightgear, etc etc etc programs can understand the old interface. but plase correct me.

yesterday i found that if you unplug and replug the usb conector the js_demo detects axis!:confused:

---

