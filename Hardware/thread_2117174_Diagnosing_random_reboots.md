---
title: "Diagnosing random reboots"
date: 2013-02-17
forum: Hardware
---

### Post by dargaud on 2013-02-17
Hello all,
I have a server/workstation that has been running smoothly for the last 4 years or so. The last night it started doing random reboots: screen goes black and the machine boots just like that. I've had 6 reboots so far, including one while the machine wasn't yet finished booting. Temperatures are fine. Smartctl tells me my drives are fine. I don't see anything strange in the kernel or system logs. How can I diagnose this besides taking the machine apart ?
Thanks

---

### Post by ahallubuntu on 2013-02-17
~

---

### Post by tgalati4 on 2013-02-17
As ahallubuntu said, a complete cleaning and reseating.  Then put a voltmeter on your power supply and verify your voltages during operation.  Leave the meter on and see if you get voltage dropouts.  It could be your power supply is failing.  Do you have an UPS?  It could also be issues with your house power.

---

### Post by dargaud on 2013-02-18
Thanks guys.

My hardware answered my question for me: it croaked during the night an hour after I posted the question. The front lights come up, but no POST, no BIOS screen. So it's a hardware problem, either power supply (but there's light), mobo, memory or some PCI card that's causing major lockup. I will take it apart tonight see if I can figure it out.

PS: in case I need to change mobo, is it OK to go from AMD64 to Intel64 and keep the some OS or do I need to reinstall Ubuntu from scratch (horror!) ?

---

### Post by tgalati4 on 2013-02-18
You should be OK, linux detects hardware on boot, so as long as you are still 64-bit.  Let us know what you find.  Perhaps your server was upside down for too long--being in the extreme south.

---

### Post by ahallubuntu on 2013-02-18
~

---

### Post by dargaud on 2013-02-18
Found the problem: it was a loose wire for the front panel (on/off/reset/...). I only found out after I took everything apart, changed the BIOS battery, etc. Well, still better than shelling a couple hundreds for a new mobo (which I plan to do in a few months anyway to go 'full silent' due to circumstances...).

Thanks.

---

