---
title: "HP Laserjet 1020"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by saracen on 2006-08-20
i'm having issues with my HP LaserJet 1020.  I followed the instructions from people on the forums and downloaded the foo2zjs driver from [http://foo2zjs.rkkda.com](http://foo2zjs.rkkda.com), make, make install, all that stuff.  The printer is detected and it appears to get installed but then when I try to print something, the little printer icon appears briefly in the notification area and then it just disappears.  The printer doesn't print, whir or anything.  

I'm really stumped on this....

---

### Post by meng on 2006-08-20
Does it not work through System > Admin > Printing > New Printer?

---

### Post by saracen on 2006-08-20
It adds the printer and I choose the foo2zjs driver.  It says "Ready", but then when I try to print something, nothing happens.  The little printer icon appears briefly and then just disappears.  No printout, nothing.

---

### Post by meng on 2006-08-20
What sort of connection do you have to the printer, and what do select in CUPS?

---

### Post by saracen on 2006-08-20
> **meng said:**
> What sort of connection do you have to the printer
USB connection

> **meng said:**
> and what do select in CUPS?
What do u mean?  I just use the Gnome Add Printer Dialog through System->Administration.  I select the HP LaserJet 1020 printer and the foo2zjs driver.

---

### Post by meng on 2006-08-20
Let me rephrase:
When you added the printer through Sys>Admin, did you "use a detected printer" or "specify a port"? In other words, where did you tell the computer to look for your printer?
What I'm driving at is that this may not be a problem with your printer or the driver, but simply where the test page is being sent to.

---

### Post by saracen on 2006-08-21
I chose "use a detected printer".

---

### Post by dwith on 2006-08-28
[I]saracen  	i'm having issues with my HP LaserJet 1020. I followed the instructions from people on the forums and downloaded the foo2zjs driver from [http://foo2zjs.rkkda.com](http://foo2zjs.rkkda.com), make, make install, all that stuff. The printer is detected and it appears to get installed but then when I try to print something, the little printer icon appears briefly in the notification area and then it just disappears. The printer doesn't print, whir or anything.

I'm really stumped on this....[/I]

I have installed the HP 1020 several times on my desktop due to operating system re-installations. Saracen, go to Synaptic Packet Manager and remove the foo2zjs package. This is the faulty default driver. Once it is removed, and cups is restarted, you should be able to print normally.

---

### Post by xster on 2006-09-17
How do I remove the driver individually? when I click it in the package manager, it wants me to remove ubuntu-desktop as well

---

