---
title: "Nvidia Drivers won't install"
date: 2009-09-28
forum: Hardware
---

### Post by g03t3098 on 2009-09-28
I'm trying to install drivers for my nvidia 8800gt. I went to system -> administration hardware drivers and tried to install the 180 version and all i get is a blank error message.

I have attached a screenshot of my issue.

Any ideas would be useful.

If you want me to post log files or anything like that please leave idiot proof instructions. I'm fairly new to ubuntu.

Many Thanks for any trouble

---

### Post by Sin@Sin-Sacrifice on 2009-09-28
Did you try through synaptic or even better the command terminal so you can see the output? I've personally never had this problem but I'm sure it's probably just the hardware drivers program... can't remember what it's called (on my G1 right now... can't look) but if you search nvidia in synaptic it's in there and you can try reinstalling. I could be wrong but it's a start eh? I would say solve the nvidia problem via the command line and see if it works/gives you an output to clue you in on the nature of the error.

---

### Post by g03t3098 on 2009-09-29
Solution:

As far as i can tell it was some sort of conflict with X server (or whatever the gui system is called - had X in its name somewhere). I just downloaded the latest drivers off nvidia site and bypassed X by logging in as console only.

Then ran: sudo sh driverName*

*whatever the driver was called

seemed to solve the problem. Got shiny new special effects now.

I think the problem may have stemmed from me installing KDE (kubuntu-desktop) alongside gnome (it broke some other stuff to like the user switcher - which is mildy irritating). I'm waiting for Karmic Koala then i'm going to switch to 64bit bog standard ubuntu so i can use all my ram

---

### Post by Ace- on 2009-09-29
Have you tried Envy?

Should be available in synaptics.

=)

---

### Post by g03t3098 on 2009-09-29
the drivers i got off nvidia site seem to be happy enough. Will keep Envy in mind in case i have issues later on. Thanks for the suggestion :)

As an aside i fixed the issue with components of gnome not working when i installed kubuntu. I switched the default display back to gdm and it seems happy - just in case someone stumbles across the same issue - otherwise completely irrelevent to topic

---

