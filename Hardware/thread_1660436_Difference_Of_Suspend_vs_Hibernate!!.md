---
title: "Difference Of Suspend vs Hibernate!!"
date: 2011-01-05
forum: Hardware
---

### Post by freesparks on 2011-01-05
Hello seems kind of a silly question, but I purchased a Lenovo Thinkpad Edge and was wondering what the made difference is between suspend and hibernate.  They seem to both do the same thing in that I select them and I cant seem to figure out the keyboard or function i.e. Fn combination on the keyboard to wake the laptop back up.  Are the suspend and Hibernate functions specific to the laptop manufacturer or is this something that is control in a preference tab somewhere?  Any further insight on this would be greatly appreciated.  I'm only wondering because this laptop is going to be glued on me and I am thinkinh about this in terms of battery conservation..

Best Regards,

freeparks

---

### Post by IcarusR on 2011-01-05
Suspend writes the info to RAM (memory) & still uses power (drive cpu & moniter are powered off, RAM is still powered)
Hibernate writes info to hard drive then powers laptop off.
Suspend should be resumed on pressing any key or moving mouse.
Hibernate is resumed by pressing the power button.

So in terms of optimising battery life hibernate is better, but can take as much time as powering off, suspend is quicker but still uses power.

---

### Post by rCXer on 2011-01-05
I have also thinkpad edge.  To wake up from suspend I just open the lid or press the power button.  To wake up from hibernation I have to press the power button.

**Warning!** Hibernate writes the contents of RAM to the [swap partition]("http://help.ubuntu.com/community/SwapFaq") if you have one.  For hibernation your swap size would have to be bigger than your RAM size.  If you don't have a swap partition or if it isn't big enough [hibernation will fail]("http://brainstorm.ubuntu.com/idea/18019/").

---

### Post by freesparks on 2011-01-11
Very Strange indeed,

However, I'm sure there's an explanation.  Guys, thanks so much for the reply.  I did exactly as you specified rCXer to no avail.  When I close the lid the laptop beeps but does not turn back on.  I'm guessing its a setting of some sort.  I have 4 GB of RAM on my machine.  I made my swap 8GB.  This is my output when I type free in the Terminal:

> myname@mycomputer:~$ free
             total       used       free     shared    buffers     cached
Mem:       2835900     746748    2089152          0      64752     218860
-/+ buffers/cache:     463136    2372764
Swap:      7812092          0    7812092Best Regards,

freesparks

P.S.  Thanks much for the links!!

---

