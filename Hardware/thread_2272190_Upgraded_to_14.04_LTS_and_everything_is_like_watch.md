---
title: "Upgraded to 14.04 LTS and everything is like watching a 'slug' crossing a road"
date: 2015-04-04
forum: Hardware
---

### Post by sdgreen on 2015-04-04
Running a Sabertooth 990 FX R2 motherboard with an AMD FX 9590 processor running at 4.8 GHz, along with 16GB 1866mHz ram, a Nivida GTX 570 video card, a Asus wireless pcie card AC1900, Logitech keyboard/mouse MK710/M705, and Ubuntu runs like crap. So slow! Video runs like molassis, Keyboard has about a four second delay, mouse  is erratic, wireless is erratic, even a direct connect to a 120 Ghz internet connection is terrible.

This was a 'clean' install. All updates applied. 

Either Ubuntu 14.04 has become 'bloatware' or the routines to discover hardware are flawed. 

Took me 15 min to create this note. The system is totally unuseable in its current state.

How to fix?

---

### Post by tgalati4 on 2015-04-04
Put some temperature monitors on your panel.  It's possible that a CPU overheat condition is causing throttling.  Open a terminal and run *top* to see if a runaway process is locking up your system.

---

### Post by weatherman2 on 2015-04-04
I'd guess it's the graphics driver.  Look for one from Nvidia.

Try this, though: in Ubuntu Software Center, install Gnome Flashback.  Logout, then before logging back in again, choose "Gnome Flashback (Metacity)" from the "Ubuntu" menu.  This will give you a retro look back to the old Gnome of versions past and should be extremely fast as well (not saying you need to stick with that, just doing this to help debug your problem).  Anyway, if that is super fast, then almost for sure your original problem is the graphics driver.

---

### Post by sdgreen on 2015-04-04
Temperatures normal. No indication of a runaway process.

---

### Post by sdgreen on 2015-04-04
Will try as suggested. Am suprised though with hardware that this should be an issue. Graphics driver could be a problem, not certain which one other than such recommended to use?

---

### Post by weatherman2 on 2015-04-04
Your original description sounds exactly like what Ubuntu behaves like when installed on an older computer: sluggish to the point of being useless.  Graphics fade reallllly slowly.  But installing Gnome Flashback and logging in to it makes it fly.  That's why I suggested you try that, too.  In my case, I didn't want to use the Unity interface anyway, so that was really the solution to my problem - probably not to yours.

If Ubuntu doesn't find a good default graphics card driver, it may use an incredibly slow old-style driver instead.

If it really is the driver, try searching the desktop for "Additional Drivers" and see if an Nvidia driver is suggested - if so, activate/use it.  You may also find one on Nvidia's website.

---

### Post by sdgreen on 2015-04-04
Did that and no joy. will try Gnome Flash Back. This computer is new, like maybe 2 years, with hardware that makes Windows 8.1 fly at incredible speeds. Unbuntu should do so as well; but it does not.

---

