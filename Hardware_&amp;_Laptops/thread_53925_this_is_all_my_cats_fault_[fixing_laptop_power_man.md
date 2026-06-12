---
title: "this is all my cats fault [fixing laptop power management]"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by esj on 2005-08-02
Help!  Help me not kill my cat

my inspiron 5000 these usually really happy with ubuntu.  Except, when it comes to the issue of power management.  I've been able to make it hibernate if I select the menu item but any of the buttons or lid closure features don't work and have bizarre effects

but the most recent cry for help comes because of my cat.  The place where I set the laptop is the very path she takes to get to the window so she can watch the birds and the bird feeder[1].  As a result, she tends to walk on the keyboard causing all sorts of mischief when I'm not around.  what I would like to do is close the lid and have the machine keep running[2].  Closing the lid instead creates this strange state where the screensaver login is turned on.  I login and the system is usable for about 10 seconds before it puts me in the password-protected screen saver mode again.

what I get in /var/log/messages is:

Aug  2 18:07:31 localhost kernel:     ACPI-0405: *** Error: Handler for [EmbeddedControl] returned AE_TIME
Aug  2 18:07:31 localhost kernel:     ACPI-1138: *** Error: Method execution failed [\_GPE._L0B] (Node dffeef20), AE_TIME
Aug  2 18:07:31 localhost kernel:     ACPI-0552: *** Error: AE_TIME while evaluating method [_L0B] for GPE[ 0]

if this is already documented, give me a pointer and I will go read.

Thanks in advance for help

---eric


[1] she thinks she can take down Blue Jays and red bellied woodpeckers

[2] this would be useful for other things other than keeping my cat alive.  ;-)

---

