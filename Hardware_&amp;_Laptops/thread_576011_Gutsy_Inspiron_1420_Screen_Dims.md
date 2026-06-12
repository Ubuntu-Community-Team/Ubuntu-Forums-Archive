---
title: "Gutsy Inspiron 1420 Screen Dims"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by kroenecker on 2007-10-14
The screen on my laptop dims after only a couple of minutes without use and then it fails to return to the normal brightness level once I start using it again.  I can increase the brightness using the proper hotkeys on the keyboard.

Should I be concerned about this?

---

### Post by KCPokes on 2007-10-17
You are not alone on this.  This just started happening after I upgraded tonight.  What is odd is that it only happens AFTER I unplug my USB mouse and use the touchpad.  I can bring the screen back using the hot keys, as well, but it is annoying that it goes black within seconds of doing nothing on the machine.  

BTW, mine is not a Dell.  I assume this is a general issue related to laptops rather then just Dells, as mine is a Gateway.  I do have an Intel chipset (graphics), which may be the common factor.  

Anyone else experiencing this?  I did have to reconfigure xorg after the upgrade thus it may be related to something within that.

---

### Post by KCPokes on 2007-10-18
I found that if I set my power management settings to not dim my screen after an idle period, I don't have this issue.  Why it dims immediately after I unplug it from AC, I have no idea.  Seems to be a bug in the power management piece.

---

### Post by griffithsdj on 2007-10-22
I had this problem on an HP 6120, figured out that if I added acpi=off to the boot script, it stopped doing it. Seems that Gutsy tries to handle laptops that don't support acpi without disabling it and fails.

---

### Post by angora on 2007-10-25
I figured out what's up with this.  In the Battery Power tab in Power Management, there's a slider labeled "Dim display brightness by".  When you're on battery power, it tries to dim the display by the set amount *even if you're not idle*.  Set it to 0% and you're all good.

---

### Post by skootamota on 2008-04-23
I'm using a Sony Vaio TXN15P laptop, and my screen fades even on AC power.  I'll be working away and out of nowhere it'll fade to a blank screen, then I have to tap the keyboard and it comes back.  It's super annoying.  I'd say it happens about 20 times a day.

---

