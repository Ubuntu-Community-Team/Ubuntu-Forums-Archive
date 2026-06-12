---
title: "Thinkpad recurrent shutdowns"
date: 2009-06-21
forum: Hardware
---

### Post by jean calvin on 2009-06-21
Afternoon all,

My thinkpad was running 9.04 quite happily until very recently.  It now is shutting down with no warning.  A quick trawl suggested temperature:

CPU at 40°C
MiniPCI at 78°C
HD at 27°C
GPU at 50°C

Would appreciate help with this as I am at the limit of my competence.  Forcing the processor to run at 600 MHz instead of 1.7 GHz seems to make no difference.

Ta muchly.

---

### Post by quixote on 2009-06-22
Hmm.  Those temp readings don't look high enough to explain sudden shutdown.  You're right that that kind of behavior is symptomatic of overheating, but maybe not in your case.  Just the fact that slowing down the CPU doesn't make a difference argues against that.

Have you run memtest?  It's generally the third option on boot.  Maybe there's a failing chip in there somewhere.  (Just a wild guess.  I really have no idea!)

---

### Post by jean calvin on 2009-06-27
Not a memory issue.  Memtest passed.  Still tripping out and I rather suspect it is when the miniPCI temperature reaches 79C.  Any idea how I can either cool this down or set a higher trip temp?

---

### Post by mhgsys on 2009-06-27
Maybe you could set another "trip temp" in the bios, but I recommend better cooling instead. 
You could buy a cooling path, or you could just aim a regular fan onto it.

---

### Post by quixote on 2009-06-27
I vote for the cooling pads with fans in them and even extra usb sockets thrown in for good measure.  I have one for each laptop I own.  Only problem with them is the fans can start to make whirring noises, which gets annoying.

---

