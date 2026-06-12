---
title: "HP Laserjet P1102w not recognized after update."
date: 2016-10-22
forum: Hardware
---

### Post by Ferule_Bezel on 2016-10-22
tl;dr
Hp Laserjet not detected after unknown update.
It's not a hardware issue.
Which package should I revert to an older version.


The full version.

I have a HP Laserjet p1102w at home and we have the same at work.

The computer at work died, when I got then new one and installed Ubuntu 16.04 I chose to apply updates during the installation.  Everything seemed to work fine, until I went to install the printer.

I went throught he usual multiple attempts plugging and unplugging.

I finally took it home to see if it would work on my machine at home.  It didn't.  I deleted it and tried to reinstal and it wasn't detected.  I then reconnect my printer and tried to reinstal it and it wasn't detected.

After some back and forth with some helpfull people on redit it was determined that it is definately not a hardware problem.  I only wish someone suggested booting a live DVD and trying it earlier because that how I determined it wasn't hardware.  It works fine when I do so.

So I'm pretty sure that an update broke it.  When I search for hplip and cups in synaptic only the packages 

    cups-browsed
    cups-filters
    cups-filters-core-drivers.
    libcubsfilters-dev
    libcupsfilters1
    libfontembed-dev
    libfontembed1

don't have the "Force version" option greyed out, and none of the description in those packages seem to be relevant to my problem.

I repeat due to experience in other forums.  It's not a hardware issue.

So which package(s) should I revert to get it working again?

---

