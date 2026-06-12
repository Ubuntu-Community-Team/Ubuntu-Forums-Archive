---
title: "No Software Centre after Karmic upgrade"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by JorisGoudriaan on 2009-11-04
I upgraded from 9.04 to 9.10 rather painlessly, but noticed in Karmic that I don't have either the old 'Add/Remove Programs' (logical), nor the newly advertised 'Software Centre'. And it isn't either in the 'Edit Menu' options unticked. 

I am running Ubuntu Tweak, could there be a possible conflict? Or any ideas on how I can surface it/install it/etc?

---

### Post by tommcd on 2009-11-04
> **JorisGoudriaan said:**
> I upgraded from 9.04 to 9.10 rather painlessly, but noticed in Karmic that I don't have either the old 'Add/Remove Programs' (logical), nor the newly advertised 'Software Centre'. And it isn't either in the 'Edit Menu' options unticked. 
Open a terminal and run:
```
aptitude search software-center
```
to see if the Ubuntu Software Center is on your system. An "i" before the package name means it is installed. A "p" before the package name means it is purged (i.e., not installed). If you see a "B" before the package, that means it is broken or has broken dependencies that you will need to investigate.
If the software-center is not installed you can install it:
```
sudo apt-get install software-center
```
If it is on your system, see if you can run it from the terminal by typing **software-center** in the terminal.
> **JorisGoudriaan said:**
> 
I am running Ubuntu Tweak, could there be a possible conflict? 
It has always been my belief that all these 3rd party repos and 3rd party, unofficial packages that people add to their systems are a big reason that so many people end up with problems after doing a dist-upgrade. They then often blame this on Ubuntu, when really the cause is something else on their system.
This is just my opinion though. It would be interesting to do a poll of people who had upgrade failures and see what unofficial packages and repos they may be using.
I am not familiar with Ubuntu Tweak. I had to google it to find out what it was.

---

### Post by sjosul on 2009-11-04
right-click on "Applications" on the top left panel, and choose "edit menus". Put a tick next to "Ubuntu software center", which should show on the right panel.

---

### Post by JorisGoudriaan on 2009-11-12
Thanks tommcd, indeed it was installed but had to manually (i.e. add a new menu item as using the command 'software-center') add it to the menu!

---

