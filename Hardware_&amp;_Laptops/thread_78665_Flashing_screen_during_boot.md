---
title: "Flashing screen during boot"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by GoodPanos on 2005-10-18
From day 1 when Ubuntu boots up the screen flashes.  I can get a glimpse of the logo and the progress bar as it boots.  Soon as Gnome loads up everything is ok.  The same thing happens when I shut down or reboot.

If I plug in an external monitor I can see the boot up process okay.  As a matter of fact that's how I was able to intall Ubuntu.

Any ideas on how to correct this?

Dell Inspiron 6000 w/ ATI Radeon X300

---

### Post by GoodPanos on 2005-10-19
I looked around and noticed that a few people had to type *linux vga=771* before booting into the LiveCD.

How do I do the same if I have installed Unbuntu?
Where would I put this command so it only works at boot time?

Any advice is appreciated.

---

### Post by civilwarlord on 2005-10-19
I had something else typed here, but then I found the way it "should" be done

go into a terminal
sudo nano /boot/grub/menu.lst
look for the # kopt= line and add vga=771 to the end
Press Ctrl-X
Press Y
Press Enter
sudo update-grub (this will append the vga=771 to the kernel lines)
reboot


Hope this helps.

---

### Post by GoodPanos on 2005-10-19
**...A concrete solution!!**

Thank you so very much civilwarlord.

That worked great!

---

### Post by civilwarlord on 2005-10-19
I'm glad that I was able to help.:D

---

### Post by GoodPanos on 2005-10-19
Once again thanks for that solution.

One side effect though, has come up since this change and that is when I put the notebook in Stand By (Fn+Esc) the screen never comes up after I press the power button.  I can see that the power returns but the screen remains blank.

Any advice?

Thanks

---

### Post by civilwarlord on 2005-10-19
I'm not sure about that, but I'll look around.  If you really like having stand by, then you should undo what I posted, just take out the vga=771 and run update-grub.

---

