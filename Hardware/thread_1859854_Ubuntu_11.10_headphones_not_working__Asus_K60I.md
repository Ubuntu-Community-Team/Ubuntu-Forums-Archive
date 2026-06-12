---
title: "Ubuntu 11.10 headphones not working / Asus K60I"
date: 2011-10-14
forum: Hardware
---

### Post by marcshawn on 2011-10-14
im using Ubuntu 11.10 also tried with Ubuntu 10.10 liveCD. 

Running on a ASUS K60I laptop. 
The thing is that im having sound issues. 
Internal speakes work fine. 

But i cant get any sound on just my headphones.  
If i keep them fully plugged in, the internal speakers and headphones mute. When I un-mute i get sound on my headphones and on the internal speakers. 

No clue where to start here.. 
If its of any help, this laptop has one input jack (mic) and one output jack (headphones), and an internal mic. 

Here is my sound card:

Sound Chip Vendor: Intel Corporation
Sound Chip     : 82801IB/IR/IH (ICH9 FAMILY) HD Audio Controller
AC'97/HDA Codec Name: VIA VT1708S

Just ring if there's any other info i can provide to you guys in order to know whats going on. 

Thanks

---

### Post by bcooperb on 2011-10-14
Here is what worked for me on my Dell Studio 17 Laptop. Might be along the same problems you are having. Please post back the solution if you get this working.

[http://ubuntuforums.org/showthread.php?t=1469949](http://ubuntuforums.org/showthread.php?t=1469949)

---

### Post by mattybe on 2011-10-15
I can't promise this will work, but you might try running ```
alsamixer
``` from command line and playing with the automute option

---

### Post by Rosscopico on 2011-10-16
Thanks!
AlsaMixer worked for after upgrading to 11.10. Turned out my speaker volume had been muted.

---

