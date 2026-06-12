---
title: "HP LaserJet 1000 issue"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by teleute on 2007-01-05
I have an HP LaserJet 1000, which worked beautifully from the moment I first tried.  Went to the admin interface for printers - it detected it, added fine, and I could print instantly.  Could even share over the network to the windows machines.  All good.

Then I went away for the holidays (leaving it off).  Came back, and now the printer doesn't work, even locally.  Try to print a test page, and it says it's printing, but the lights don't even begin to react on the printer itself.  Go into properties and it says "No %%BoundingBox: comment in header!".  I've tried removing and readding the printer, restarting cupsys, restarting the system, unplugging/replugging the printer, and eventually even upgrading from Dapper to Edgy (which I'd been thinking about doing anyway).  All packages and drivers are the most current versions.  Anyone have any ideas?  Thanks!

---

### Post by damagedspline on 2007-01-05
I have a 1010, which i basically the same... And something similar happend to me once.

I erased all prints from the printer spooler, shutdown the printer, opened it again and resent the prints, and it worked.  Well mostly:
I had a specific pdf file that I imported from a ppt file using openoffice that on each attempt to print caused the printer to have a "memory jam". ](*,)

---

### Post by teleute on 2007-01-05
Sadly, mine won't be so quick - I've already deleted all jobs, removed and readded the printer, unplugged and replugged in the printer, restarted the service, etc...  for hours in many different permutations.  No luck.  :-(

---

### Post by dante2d on 2007-04-15
I had this driver working on Ubuntu 7.4 beta, not sure why it stopped.  

The fix was very  easy.

Step 1) sudo apt-get install build-essential

Step 2) follow the procedure on the drivers main page.  [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

Step 3) when running gnome-cups-manager do NOT choose the default foo2zjs driver, choose the non-recommended one.

should work!  best of luck

---

