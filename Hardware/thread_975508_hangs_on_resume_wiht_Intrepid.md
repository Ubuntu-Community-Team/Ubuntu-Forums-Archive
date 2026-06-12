---
title: "hangs on resume wiht Intrepid"
date: 2008-11-08
forum: Hardware
---

### Post by dlstyley on 2008-11-08
With Hardy, I was able to suspend and resume successfully (although it took upwards of 20 seconds to fully resume).  

Now on Intrepid, my laptop appears to be resuming, but it either ends up with a blank screen, or the screen comes back but the laptop is hung.  Pressing any keys have no effect, except for a couple of keys that result in beeps.  Closing the lid, etc doesn't do anything either.  I have to hard-reboot.

Below is an entry from the log that occurs right after the system resumes.  After that, a bunch of debugging info is dumped and then no other entries to the log until I hard boot.  Any suggestions?


[FONT="Fixedsys"]Jul  2 12:27:30 thorbuntu kernel: [ 3333.640290] Restarting tasks ... <6>[fglrx] ASIC hang happens.
[/FONT]

---

### Post by microsome on 2008-11-09
I have a pretty similar issue. After resume it shows some kind of "thaw error". Afterwards the keyboard does not work anymore, so the only solution is to restart the laptop (dell inspiron 600m).

---

