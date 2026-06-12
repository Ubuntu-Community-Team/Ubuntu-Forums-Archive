---
title: "fwcutter failed during upgrade to 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by CJScully on 2009-04-24
I started downloading the upgrade from 8.10 to 9.04 on my Sony Vaio PCG-FRV26 laptop this afternoon but had to leave before it finished. When I returned I had an error message on my screen that the fwcutter failed to upgrade but the rest of the upgrade process would continue.  The upgrade finished and as suspected my wireless card is now dead.

When I open up Hardware Drivers I see Broadcomm B43 wireless driver listed.

Under the description it says "fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files"

Under the description it says "This driver is not activated."

When I click on the Activate button nothing changes.

I figured I need to manually upgrade fwcutter so I fired up Adept and tried to browse for fwcutter figuring I would either need to uninstall the old version then re-install the new version or it would tell me that there was an upgrade available for it.  Well, I got neither of those results.  What I got was "No matches found"

Pretty well stumped as to where to go from here.

---

### Post by CJScully on 2009-04-24
UPDATE: After I posted I went away and did something else for a while and then it occured to me that I could probably find fwcutter with Aptitude even though Adept could not seem to locate it.  That turned out to be the case and it turned out that the actual name was b43-fwcutter.  I manually removed it and then reinstalled it.  Rebooted the machine and the device is now working properly.

---

