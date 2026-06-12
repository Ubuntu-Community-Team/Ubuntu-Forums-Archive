---
title: "How to output the display to a LCD mon"
date: 2008-08-27
forum: Hardware
---

### Post by pumber on 2008-08-27
and turn off the notebook mon at the same time ?

My notebook is Fujutsu T4020, and in WinXP, when I press [Fun]+F10, the display will be exported to the LCD mon with the notebook mon turned off. However, this doesn't work in Ubuntu.

What setting can I adjust to make it work ?
Thank you !

---

### Post by silvanus2005 on 2008-08-27
Go to System-Preferences-Screen resolution and choose there Clone display.

---

### Post by dsm iv tr on 2008-08-27
silvanus2005 offers good advice.

Be aware that if your card is an ATI Radeon Xpress 200, it won't work yet with this method and you'll have to use the proprietary drivers (fglrx). I found this out a couple days ago when I was trying to dual-head my laptop.

---

### Post by pumber on 2008-08-28
> **dsm iv tr said:**
> silvanus2005 offers good advice.

Be aware that if your card is an ATI Radeon Xpress 200, it won't work yet with this method and you'll have to use the proprietary drivers (fglrx). I found this out a couple days ago when I was trying to dual-head my laptop.

It works half, as what I want is to  export the display to an external LCD mon but [COLOR="Red"]at the same time[/COLOR], the notebooks's mon is turned off.


Now, both are turned on and off at the same time.

What can I do ? Thanks !

---

### Post by silvanus2005 on 2008-08-28
In System-Preferences-Power Management you can choose Black Screen when the lid is close. Try this, and tell me if your external monitor goes black also. If it does not, I think yu can work on your laptop using an external keyboard and having your lid closed.

---

