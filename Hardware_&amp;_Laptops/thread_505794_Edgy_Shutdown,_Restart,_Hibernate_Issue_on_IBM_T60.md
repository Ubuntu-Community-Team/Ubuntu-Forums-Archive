---
title: "Edgy Shutdown, Restart, Hibernate Issue on IBM T60"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by catfishk on 2007-07-20
hey all!

 i have Ubuntu Edgy installed on my Thinkpad T60.  i am running the xorg-driver-fglrx driver ( version 8.28.8 ) for my ATI X1300 card

 when i try to shut down, restart, or halt, i get a flashing cursor in the top left of the screen.  i can switch between virtual terminals however i cannot type.  i have to hard power off EVERY time.  also, when i hibernate the machine will flash the moon icon for a while then pop back to life.  suspend to ram works fine from the Gnome menu, however

 i think this is an ACPI or video issue.  if anyone has an idea what logs to check or what might be happening i would love the help.  if another T60 user could post or send me their acpi-support, /etc/hibernate/* files for review that would be excellent, as well!

 also, i used to use use uswsusp in Feisty and it was great.  now i get:

[HTML]suspend: Could not stat the resume device file[/HTML]

 thanks in advance!

---

### Post by catfishk on 2007-08-12
ok, i fixed it!

 well, no i didn't really, because i ditched uswsusp as it wasn't working at all, i only got the error above trying.  instead i installed the suspend2 patched kernels from [here]("http://3v1n0.tuxfamily.org/dists/edgy/suspend2/") and configured hibernate and suspend2

 i also had too little of a swap partition to have this method work last time at only 500 megabytes.  i upped it to 900 MBs (i have 2 GBs of RAM so swap is kept to a minimum)

 it is much slower and uglier than uswsusp so far :cry:.  i have gotten uswsusp to work on this machine in Debian Sid (no XGL support) and in Ubuntu Feisty (breaks XGL and network-manager-gnome).  maybe through some tweaking i can get suspend2 to work faster?

 a note for you thinkpad users, the 'moon' LED light works with this method!

---

