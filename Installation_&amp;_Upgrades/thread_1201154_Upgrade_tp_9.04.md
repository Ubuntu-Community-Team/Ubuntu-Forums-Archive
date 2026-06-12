---
title: "Upgrade tp 9.04"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by CHFFriday on 2009-06-30
I have five PC with 8.04 or 8.10 installed. All have ATI video cards of  one short another.

Question: As there seams to be much trouble with 9.04 and ATI cards,should I forget about upgrading?

---

### Post by ibutho on 2009-06-30
You could test the computers with the Ubuntu live disc. If the live disc runs well, there are good chances that the version on the live disc will run well on the hardware that you tested.

---

### Post by starcraft.man on 2009-06-30
Just a note, but if your upgrading that many machines, you'd be best served by downloading the 9.04 install disk, and using the disk to upgrade (insert it into a booted up machine to run upgrade). You could even burn multiple copies to update several at once, without using bandwidth (most ISPs have caps now). The alternative is setting up a local mirror, but it's not really needed until you scale well beyond 5 IMO.

As to ATI and 9.04, my lone ATI linux box is running the ATI driver just fine. It's a 3650, a bit weak a card, but works alright. I do want to note, I manually upgraded to the latest 9.6 release, I don't know which is being used by the repos. Anyway, no trouble, 3d works fine, except that the card is a bit underpowered for all the nice compiz effects I want.

Also of worth noting, you can't upgrade directly by skipping a generation (i.e. 8.04 > 9.04) you have to actually go one at a time to 8.10 then 9.04. For these or older systems, just reinstall and overwrite the root directory, if you've a separate home partition you'll be fine. If not, well, you'll want to back up and do a clean install or do a double upgrade (seems wasteful IMO).

That's my 2 cents, take what you will and good luck.

---

### Post by linuxmagick on 2009-06-30
I would definately only try this on one of the machines to start with.  That way, if you run into any issues, you can work past them on that machine without having the rest of the systems out of commission.  

You may want to check and see if AMD is still providing their fglrx driver for your model graphics adapters.  They recently retired a lot of graphics cards.  I have an ATI Mobility 9600 and can no longer use the fglrx driver with Jaunty.  However, all is not lost because the open source drivers are working just fine to provide me with 3D support.  Good luck!

---

