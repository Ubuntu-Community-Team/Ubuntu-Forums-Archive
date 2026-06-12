---
title: "Wacom pad ud-0608-r problem"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by wog on 2008-03-04
I have an ancient Wacom ArtZ II, with an rs232 serial port (not USB).

I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=619967"), but they seem to be for a usb tablet.

wacdump seems to find my pad with the following line: ```
wacdump -c serial -f art2 /dev/ttyS1
```

I don't really know how to proceed from here.

Can anybody help me?

---

### Post by oldsoundguy on 2008-03-04
You might be hard pressed to get that legacy piece of hardware installed, but a visit to the Wacom support site may get an answer as to what is now supported and what is in the works.

This thread installed my tablet (Intos 3) and for all intents and purposes DOES work and works well in Gimp. (although it is USB)

[http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

A tremendous amount of time and effort has gone into that post! (along with the co-operation of Wacom and their hosting of the driver repository!)

You could always try using a serial to usb adapter .. not that much in cost and it may salvage an otherwise still useful and valid tool.

---

### Post by wog on 2008-03-04
> **oldsoundguy said:**
> You might be hard pressed to get that legacy piece of hardware installed, but a visit to the Wacom support site may get an answer as to what is now supported and what is in the works.

This thread installed my tablet (Intos 3) and for all intents and purposes DOES work and works well in Gimp. (although it is USB)

[http://ubuntuforums.org/showpost.php?p=4253232&postcount=133](http://ubuntuforums.org/showpost.php?p=4253232&postcount=133)

A tremendous amount of time and effort has gone into that post! (along with the co-operation of Wacom and their hosting of the driver repository!)

You could always try using a serial to usb adapter .. not that much in cost and it may salvage an otherwise still useful and valid tool.

The rs232-to-USB port adapter won't work. I've tried it. The light on the adapter lights up when I apply pen to tablet, but Ubuntu continues to ignore input from it. All hardware signals thus far prove the tablet is functioning properly. 

That set of instructions is Black Magic to me, so I wouldn't even know how to adapt them for looking at a known and identified rs232 port such as the one I have. I suppose I could change the /dev/input/wacom line to /dev/ttyS1 to see what would happen, if anything. I'll report back with any findings.

---

### Post by wog on 2008-03-04
And here's the solution!

Follow [the Black Magic instructions]("http://ubuntuforums.org/showpost.php?p=4253232&postcount=133"), but for every line which reads "USB", make sure the setting is to "off".

Also, replace "/dev/input/wacom" with whatever location wacdump gets the input readings from.

It starts out in the mode where the tablet dimensions correspond to the screen dimensions. I'm too happy Ubuntu is finally paying attention to the tablet to mess with it much at this point. Maybe later. :)

---

### Post by oldsoundguy on 2008-03-04
that set of instructions is what installs your pad into Ubuntu.  there is no "quick installer" for the equipment yet.  Using terminal, you cut and paste those commands into there and execute the commands and edit xorg when required.  Just as you would if you are installing some other thing from a repository only it is in spades!

Here the Ubuntu Guide"
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

If you can install items from this, you can install from the laundry list.

---

### Post by oldsoundguy on 2008-03-04
glad to see you found your answer.

It is not the easiest piece of hardware to install and they still lack support for the airbrush.  But it does work and quite well once tweaked.  The Intuos has special shortcut keys on it that I have not mapped yet, but having the pad do it's basic thing is enough for right now.

---

