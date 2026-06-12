---
title: "Replacing Nvid card with Ati Card"
date: 2010-02-03
forum: Hardware
---

### Post by Highest on 2010-02-03
I initially installed ubuntu on Gateway system. It did all the work for me as far as drivers are concerned. But now i want to remove the stock nvidia(one vga out) card with a ATI (vga, dvi, s-vid out) card. I tried removing the nvidia card, while the machine was off and pop in my ati vid card and boot up but the screen is all lines. Any advice for entry level user to get this card working? Its hard cause i think i want the new card in so i can install it but obviosly i cant run terminal if my monitor is full of lines.

---

### Post by ratcheer on 2010-02-05
I have never done this in Ubuntu, but the normal way to do this would be to uninstall your current video driver, power down the system, swap video cards, and reboot. Upon reboot, the system should try to find and install the driver for the new card.

Tim

---

### Post by ratcheer on 2010-02-05
PS - In the above instructions, you may want to reboot the machine once without swapping cards, just to make sure it comes up with the generic VGA driver after you uninstall the existing driver.

Tim

---

### Post by pizza-is-good on 2010-02-05
Maybe you've tried this already, but consider testing all the video outs(VGA & DVI), and see if there is any difference.

---

### Post by markbuntu on 2010-02-05
This thread here has explicit instructions for successfully changing from nvidia to ati with a minimum of trouble. It has been tested and works. If you have not messed around too much you should be able to put the nvidia card back in and then follow the directions.

[http://ubuntuforums.org/showthread.php?t=1373813](http://ubuntuforums.org/showthread.php?t=1373813)

---

