---
title: "Car computer + Power management, powering off when mains unplugged"
date: 2014-10-19
forum: Hardware
---

### Post by mr.z on 2014-10-19
Hi all,

I'm looking at using my venerable old x61 ibm laptop as an in car computer. I'm thinking if i can have the system suspend when the mains is removed (I.e. the inverter power is removed and the laptop isn't geting "mains" supply) and ideally powers back up when power is plugged back in.

Is there a simple way to acheive this? a script or settings i've not thought of?

Also, any general tips for using ubuntu as a car computer? (Thinking XBMC) or other distributions that are better suited? 

Thanks!

---

### Post by mr.z on 2014-10-21
Bump.. and while i'm here, are there, are touchscreen (such as lilliput) generally well supported in ubuntu?

---

### Post by grahammechanical on 2014-10-21
How can a computer operating system run the suspend script when the machine does not have any power? A lot would depend on the APM options of the BIOS. Investigate those possibilities first.

You might also want to investigate the possibility of running the laptop from the vehicle's battery supply without using a DC to AC converter. Have a look at this site and see what others have achieved. Look up power supplies. With the right kit it is possible to connect the motherboard to the vehicle's power supply and dispense with the AC to DC transformer (PSU) in the machine.

[http://www.mini-itx.com/](http://www.mini-itx.com/)

[http://www.mini-itx.com/store/?c=10#int](http://www.mini-itx.com/store/?c=10#int)

DC (vehicle battery) to AC (computer PSU) and then to DC (motherboard) is inefficient and produces unwanted heat coming from the DC to AC converter and then from the computer PSU as it converts AC back to DC.

Regards.

---

### Post by tgalati4 on 2014-10-21
How can you drive and operate a computer at the same time?  Linux is good at multitasking.  Humans, less so.  Check your local jurisdiction for operating electronic devices.  I had a friend get pulled over for checking his blood sugar with a meter while driving.  The cop was not amused when he found out it was not a cell phone.

You can set Power Management settings in Control Panel to "hibernate" when On Battery after a couple of minutes.  Make sure your swap file or partition is slightly bigger than your RAM.  Hibernate should work fine on a Thinkpad.

As far as desktop environment, what sorts of things do you envision this car computer doing?

"Right Turn"

nothing happens.

"Sudo Right Turn"

Whoa!

---

