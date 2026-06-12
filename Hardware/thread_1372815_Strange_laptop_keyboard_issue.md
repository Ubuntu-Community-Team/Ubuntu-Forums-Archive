---
title: "Strange laptop keyboard issue"
date: 2010-01-05
forum: Hardware
---

### Post by aminal on 2010-01-05
Hey guys,

Just had a strange issue happen with my laptop / keyboard.  I've had Ubuntu Server running fine for awhile now.  Just a few minutes ago I was messing with getting a pcmcia card to work.  I ejected and inserted it a few times, and all of a sudden the keyboard stopped working.  Thinking the system had simply locked up for whatever reason, I rebooted.  

The keyboard works in BIOS.  I can enter setup and all that, but as soon as Grub comes up, the keyboard is unresponsive.  I loaded up a live cd and the keyboard works fine there as well.

I even added a USB keyboard which also works in BIOS but not when GRUB starts up.

Any reason why the keyboard wouldn't work once the installed system starts up?

Thanks!

**edit** 

I should add - after the keyboard stopped working I did a hard shutdown and when the system started up, fsck started. I got a couple warnings mentioning something about the CPU being (soft?) locked for x amount of seconds.  After a minute or so of this, I restarted again.  This is when GRUB started and they Keyboard continuted to not work. 

thanks again.

---

