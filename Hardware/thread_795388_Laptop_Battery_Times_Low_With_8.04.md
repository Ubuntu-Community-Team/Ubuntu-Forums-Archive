---
title: "Laptop Battery Times Low With 8.04"
date: 2008-05-15
forum: Hardware
---

### Post by nexus_2006 on 2008-05-15
Hello again.  Since I installed Hardy Heron my discharge times have gone from nearly four hours to only 2.5.  Any ideas about why or how to fix it?  It is very annoying.  I was previously running Dapper Drake.  -Matt

---

### Post by hermes0710 on 2008-05-16
What model is your laptop?

---

### Post by nexus_2006 on 2008-05-16
It is a Dell Latitude D820, only about 2 years old now.  Core 2 Duo 2.00 ghz, 2gb ram.  I have noticed that the wifi light is now on all the time, I can't seem to turn the wireless off with the switch.  Could that be decreasing battery life that drastically?

OTOH, I just had my first successful linux experience with hibernate, nice job guys!

---

### Post by hermes0710 on 2008-05-16
You should install powertop and run it through a terminal. It's a useful application that shows which processes "consumes" more power in order. Try it to figure out

---

### Post by nexus_2006 on 2008-05-16
Here is my output from powertop.  Is it normal to have 60% of the usage be kernel interrupts?  It also appears that Amarok uses quite a bit of power/CPU time just sitting there, not playing any media.  How good a suggestion is it to disable 'hal' as well?

---

### Post by hermes0710 on 2008-05-16
I really don't know. You can try the suggestions by powertop (you must run it with root privileges: sudo powertop) and see if the battery lasts longer. ps>You can see that the wireless driver is not in the list

---

### Post by nexus_2006 on 2008-05-16
True, but I was under the impression that by its being on and scanning, it uses noticable power.  I need to figure out how to get the card to go off and on, as I don't use it very often.

---

### Post by hermes0710 on 2008-05-16
You can right-click on the "network" icon in the system tray and untick "enable wireless" to stop searching

---

### Post by nexus_2006 on 2008-05-16
That did it, thx.  Now to see if between the two, battery times come back.

---

