---
title: "Logitech G5"
date: 2009-06-07
forum: Hardware
---

### Post by benhamill on 2009-06-07
In both Hardy and Intrepid, I could edit xorg.conf to mess with the way my mouse (A Logitech G5) behaved. Specifically, I want to switch the behavior of button 2 (center-click) and button 8 (under my thumb). Before 9.04, I'd do that by tellit the buttons were [1 8 3 4 5 6 7 2].

Does anyone know where I'd do this in Jaunty now that mouse stuff is not in xorg.conf? Thanks in advance.


Ben

---

### Post by days_of_ruin on 2009-06-10
I'm looking for help on this too.

---

### Post by benhamill on 2009-06-11
Thanks for reminding me this thread is still open. So... here's what I found:

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

I should note: I guess this article might be slightly out of date. I reconfigured successfully with 8 buttons with the xinput method, which is higher than the stated maximum listed here.

Also, you'll have to run this every time you log in, so you can just paste the command you end up assembling into your run-on-startup list in System > Preferences > Startup Applications.

I hope that helps other people.


Ben

---

