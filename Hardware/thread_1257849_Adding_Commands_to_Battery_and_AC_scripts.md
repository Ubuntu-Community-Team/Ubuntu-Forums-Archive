---
title: "Adding Commands to Battery and AC scripts"
date: 2009-09-04
forum: Hardware
---

### Post by SteveONCSU on 2009-09-04
I really enjoy seeing what Powertop does for me.  I'd like to add the few suggestions to whatever scripts are run when the laptop switches to battery or AC.  I know there are two areas for this:  /etc/acpi/ac.d and /etc/acpi/battery.d

I'm not the best at this area of linux.  Any suggestions??  I'm not sure if I should create a new script or just add my custom commands to an existing script that is executed.

---

### Post by tgalati4 on 2009-09-04
Back up your existing scripts then simply add to them.  Be sure to add comment lines with your name or initials and the day and why you are making the change.

I also copy any scripts/config files that I modify to a directory called ~/home/Projects/scripts so when I do a home directory backup, I have my goodies there as well.

This is helpful for when you dist-upgrade and you need to retweak to get the new distro working the way you want.

---

