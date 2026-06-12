---
title: "M1330 Touch Sensitive keys."
date: 2009-04-06
forum: Hardware
---

### Post by leveliv on 2009-04-06
I have an M1330 from Dell with the touch sensitive buttons for 

media and Eject. my only problem is the eject button, I press it when I have a CD inserted and nothing happens, I have to go over right click and say eject, I find this really annoyying how would I go about fixing that. 

Is it as simple as just mapping the key to a certain function?

---

### Post by sdennie on 2009-04-06
Unfortunately, there is no clean way to fix the eject button on that machine.  The button directly talks to the hardware and doesn't generate a button event (you can verify this with the xev program).  Linux locks the CD drive and you can turn this off but, that has the bad side effect of leaving the CD drive mounted (so, you still have to right click and click "Unmount").

---

### Post by leveliv on 2009-04-06
thats okay, I will manage without it haha, Maybe they'll fix it in future releases. If they never ever do I'm sure I will be fine. Thanks for the help.

---

### Post by sdennie on 2009-04-06
If it's possible to fix, I'm fairly certain the fix could only come in the form of a BIOS update.  It's not that linux doesn't understand it as the eject key being pressed, it's that essentially it isn't a keypress.  It's just one piece of hardware (the key) directly talking to another piece of hardware (the drive).

---

### Post by leveliv on 2009-04-06
That's weird, seeing that Dell ships with Ubuntu you think they would want all the features working, but then again ...They wouldnt.

---

