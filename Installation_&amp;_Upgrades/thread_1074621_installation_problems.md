---
title: "installation problems"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by ARhere on 2009-02-19
Need some help with a PC I am trying to build for my daughters.

I am trying to install Ubuntu 8.10 from a live CD and it keeps freezing up the PC right at the point where the GUI is loaded.  This happens when I try to install or a live session.  I have already tried disabling all the on-board hardware including the hard drive and same results.  I have also done a full test on the RAM and install media and no errors are found.

After the point where installation freezes, pressing CTRL+ALT+F8 shows me the following...
```
* Starting periodic command scheduler                 [OK]
* Enabling additional executable binary formats binfmt-support [OK]
* Checking battery state...                         [OK]
```

My motherboard is an ECS K8M800-M2 Rev.1.0A and the BIOS version is 1.1c 9/18/2005.  I used this MB before with 8.04 as a file server with no problems so I know it is compatible.  I am going to try a different video card next as that is the only thing left that I can think of.

Any thoughts?

-AR

---

### Post by glotz on 2009-02-19
Perhaps try special kernel parameters like noapic nolapic acpi=off.

---

### Post by ARhere on 2009-02-19
UPDATE:  I swapped out the video card and the PC booted to the 'LIVE' session just fine.

What bugs me is the on board video is the S3 Graphics UniChrome Pro IGP, which worked just fine with 8.04.1 and should be very generic.  I would like opinions/confirmations on this one before I mark this thread closed.

By the way, I tried the no-ACPI option with no effect.  Thank you for the good suggestion.

-AR

---

### Post by taurus on 2009-02-19
What video card do you have?  If you use the add-on video card, make sure you turn off the onboard on from the BIOS.  Then, at the initial menu from the LiveCD, press F4 and try the safe graphic mode to see if the desktop comes up.  Otherwise, you could try the alternate CD.

---

### Post by ARhere on 2009-02-23
> **taurus said:**
> What video card do you have?  If you use the add-on video card, make sure you turn off the onboard on from the BIOS.  Then, at the initial menu from the LiveCD, press F4 and try the safe graphic mode to see if the desktop comes up.
Yep, tried the safe graphics mode and no better results.

[QUOTE=taurus]Otherwise, you could try the alternate CD.[/QUOTE]
REALLY interesting that you say that.  If I remember, when I installed 8.04 previously, I used the alt-install CD.

I threw in a spare Ti4200 card because the kids will play games on it and it is up and running.  I would still like to know what was the problem but ... meh.

Thanks Everyone,

-AR

***EDIT:** Where is the "thread closed" flag???*

---

### Post by glotz on 2009-02-23
The SOLVED functionality is MIA.

---

### Post by azroy on 2009-02-24
what solve is problem stop and 'hang' time running desktop after loading ubuntu???

---

### Post by cariboo on 2009-02-24
@azroy

Start a new thread a and ask a question, your comments don't make sense unless  we know what your problem is.

Jim

---

