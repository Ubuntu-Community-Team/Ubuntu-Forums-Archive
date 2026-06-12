---
title: "Screen doesn't wake up"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by argentum2f on 2007-10-14
My screen doesn't come back on from standby when try to use the computer after leaving it for a while. The monitor itself shows there is no input. If I switch to a virtual terminal (CTRL-ALT-F6) then switch back (CTRL-ALT-F7), it magically comes back on. But just shaking the mouse, and hitting random buttons on the keyboard doesn't bring it back like it should.

---

### Post by Linicks on 2007-10-14
I have to either:

Close the lid.  Then reopen it, or hit the 'power button' once.  This is the way it works.

You can configure wake up options:

System->Preferences->Power Management | general -> buttons.

I must admit, this caught me out at first when nothing I seemed to do woke the laptop up, but once you see it, all works 100%.

Nick

---

### Post by bmomjian on 2007-10-19
I can confirm the above behavior.  I am using a Thinkpad T43 running Ubuntu 7.10.  I have configured Power Management to "Do nothing" when I close the lid.  If I leave the laptop lid shut for a 15 seconds and the open it, about 50% of the time the screen is off/black and pressing keys does not change that.  (The laptop is still running because I can still hear music playing.)

If I close the lid and open it again, the screen is now lit but still black.  If I close the lid and open it a third time the screen restores normally.  I can also confirm that the Control-Alt 6 and 7 does restore the screen on first lid open, but that is hardly user-friendly.

---

### Post by bmomjian on 2007-10-20
Seems changing to the Compiz window manager fixedit, or an Ubuntu update fixed it.

---

### Post by bmomjian on 2007-10-21
Seems  I posted to soon. The problem has returned. I have reported it as a bug.

---

