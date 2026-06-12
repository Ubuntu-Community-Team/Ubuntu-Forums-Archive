---
title: "blank screen on install"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by fatman on 2006-01-10
I just made a server install of ubuntu (probably gonna do Xubuntu) which was kinda hairy.  (had to format a couple of times before /home would mount).

When I pull the install CD, my graphics card (Nvidida Geforce 6200) lets me know its ok, then I get the motherboard splash screen, and then nothing but a cursor.  Doesn't get to grub.  

Any suggestions on where I should start looking for trouble would be appreciated.

(I do have a pair of SATA drives - any potential problems there?)

---

### Post by winlux on 2006-01-10
I would try to find some tools to do a factory certification of the hard drive. It could be that one of the drives are failing which seems probable seeing you had to format so many times to get /home mounted. Other than that you could try rewriting the whole disk with 0s (low level format) and reinstalling from there. If you still have the problem you would need to configure your bootloader configureation file to detect everything properly, but this might be a slight prob if you can't even get to the loader instead of past it. Although if it happens when you put in the boot cd, you may want to press one of the F1-10 keys to see options you can use at boot time, try dropping some usb detection maybe or change screen resolutions and load additional functions. Play around with those and maybe try a memtest too

---

### Post by fatman on 2006-01-10
You hit the nail on the head - bad hard drive - RMA'd to Maxtor.

Thanks.

---

### Post by winlux on 2006-01-14
no prob

---

