---
title: "Can wine be used to install windows drivers for a mouse?"
date: 2008-11-09
forum: Hardware
---

### Post by Rubicon421 on 2008-11-09
I can't use my extra mouse buttons and was thinking of trying to install the program (not just the driver) that allows you to assign the functions of the extra buttons for the mouse and keyboard. Would it work and is it safe to use wine with something that will affect my drivers in Ubuntu?

---

### Post by starcannon on 2008-11-09
I don't think the wine approach would be practical if or even possible; however, you can map all the buttons on your mouse, and this guide should help you in that endeavor.

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

Good Luck and Have Fun

---

### Post by Rocket2DMn on 2008-11-09
Wine is used to run Windows applications in Ubuntu, not for drivers or firmware.  For this, you need a wrapper (perhaps the best known is ndiswrapper, which is used for wireless cards).  As starcannon pointed out, this is not a practical approach if it's even possible.  Most hardware works out of the box in Ubuntu, and a few devices like wireless cards and video cards can have proprietary firmware, but I haven't heard of any for peripheral devices like mice and keyboards.  You can configure extra mouse buttons as shortcuts or other functionality (See the wiki help page in post 2).

---

