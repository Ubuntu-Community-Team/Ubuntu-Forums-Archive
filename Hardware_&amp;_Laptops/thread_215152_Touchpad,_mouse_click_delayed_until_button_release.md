---
title: "Touchpad, mouse click delayed until button release (drag and drop not working)"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by isak on 2006-07-13
Just wanted to post this note here to help others who might have this problem.

The problem was that when the "mouse" buttons below the touchpad was clicked, the button press wasn't recognized until the button was released. This made it impossible to use drag'n'drop, move windows and icons etc.

xev confirmed this: 
[LIST=1]
[*]Click and hold button => nothing happens
[*]Release the button => ButtonPress and ButtonReleased gets printed
[/LIST]

The behaviour was random, i.e. sometimes it worked, most often, it didn't.

**The problem:** Buggy xorg-input-synaptics drivers
**The solution:** Get the drivers from debian testing: [http://packages.debian.org/testing/x11/xserver-xorg-input-synaptics](http://packages.debian.org/testing/x11/xserver-xorg-input-synaptics)

Install with "dpkg -i packagefile.deb"

Hopefully, this post saves someone a couple of hours of googling :) 

Regards,
Isak

PS. My system is:
HP Pavilion dv5000
AMD64 (turion)
Ubuntu Dapper

---

### Post by herrminer on 2006-07-18
This worked perfectly for my machine.  I have the same system configuration as you (dv5000, AMD64, Dapper).  The touchpad had been driving me crazy!  Now it works great.

Thanks for posting this.

---

### Post by herrminer on 2006-07-18
Since you have the same system I do...

Have you been able to get the wireless to work?  If so, how exactly?

---

### Post by blueidealist on 2006-09-05
I have a different machine, but the same Synaptic touchpad.
I had tremendous difficulties with my touchpad which was way too sensitive on tapping, kept dragging & dropping or selection everything it came accross.

Anyway, tried to reinstall your drivers and now it is just PERFECT!

Worked like magic,

Tnanks,

David

---

