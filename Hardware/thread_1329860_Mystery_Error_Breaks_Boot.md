---
title: "Mystery Error Breaks Boot"
date: 2009-11-17
forum: Hardware
---

### Post by theWrkncacnter on 2009-11-17
If my laptop (ubuntu) is left on long enough, the screen turns off and the power button flashes (does this mean kernel panic?) It won't revive, and I have to hold the power button down to turn it off. But the strange thing is when I turn it back on, it doesn't load bios. I finally figured out you have to take the battery out and hold the power button for 20s. Then it works. What is happening here?

---

### Post by Bucky Ball on 2009-11-17
Does the caps lock light flash too, if you have one? Flashing lights in this case doesn't mean disco, but indeed, usually kernel panic. 

You should be able to find and perform a fix if it is a hibernation problem. I presume you are running on battery so it is going to auto-standby/hibernate at some stage. That is probably what is happening and it is a known issue. You might want to try that line of enquiry. 

Open up the power-management gui and have a look in there and maybe set it to something other than hibernate if that is what it is. Try Standby or Sleep or whatever. When you are plugged in and leave it, does the same thing happen?

---

