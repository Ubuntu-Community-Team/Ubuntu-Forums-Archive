---
title: "Problem (with pcmcia?) booting Ubuntu 6.10 from live cd on Laptop"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by MrKlaus on 2007-04-08
Hello!

I'm trying to install Ubuntu 6.10 form the live cd on a Peacock Freeliner XP Laptop.

I maybe should add that I'm quite new to linux.

After booting from cd when the splash screen appears I select "start/install" the installer starts. After a while it freezes however.

So after restarting I used F6 and deleted "quiet" and "splash" from the command line options.

The last output I get is:

```
cs: IO port probe 0x100-0x3af:
```

After that nothing happens.

I tried a knoppix live cd on that laptop and this only boots with additional commandline option nopcmcia. Otherwise it freezes at pcmcia detection.

But by adding a "hw-detect/start_pcmcia=false" to the ubutu command line I didn't get it to work.

I allready unplugged the pcmcia wlan card (and all usb devices aswell) but it just wont work.

Oh and i have a LAN cable to my router attached...

What should i do/try to get it work?

Thanks for any help.

Klaus

---

### Post by r00tintheb0x on 2007-04-08
1. Press F6 when the liveCD boot menu comes up to alter the boot options.
2. Add the following at the end (before the '--'):
pci=noacpi ide=nodma ide=reverse
3. Boot

---

### Post by MrKlaus on 2007-04-08
wow! 3 minutes reply time!

I tried what you suggested. It freezes at the same message. (Splash displayes "loading event manager" or somthing similar at the time i think).

I also tried adding "hw-detect/start_pcmcia=false" to your list. Doesn't work.

:-(

Klaus

P.S. does the "--" denote the end of the boot command line?

---

### Post by MrKlaus on 2007-04-10
Any ideas anyone?

---

