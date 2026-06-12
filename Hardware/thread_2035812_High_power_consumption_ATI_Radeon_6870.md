---
title: "High power consumption ATI Radeon 6870"
date: 2012-07-31
forum: Hardware
---

### Post by Eosis on 2012-07-31
I have a dual boot machine, running both windows 7 and ubuntu.

I have noticed that the machine draws much more power when simply resting idle on the desktop in ubuntu when compared to windows.

The only component which could increase the draw by this much (over 100W) is my 6870, but is anyone able to explain to me why so much power is running thorough the card in ubuntu vs. windows?  Should I be worried by this in the long term, with regards to hardware lifespan?

I am running Ubuntu 11.10, and using the proprietary drivers for the card.

---

### Post by Kreaninw on 2012-07-31
Never let your computer with AMD/ATI GPU became idle on Linux/Ubuntu, that's 100% working. Just disable this feature for now.

Here's why >>> [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860)

---

### Post by Eosis on 2012-08-02
Ah, I have been unclear.  Used the word idle to represent the fact that there was no graphics - heavy applications running (where one would expect an increase in power consumption).  The power consumed is higher simply using text editors, etc, when compared to Windows.

Thankyou for the answer, though.

---

