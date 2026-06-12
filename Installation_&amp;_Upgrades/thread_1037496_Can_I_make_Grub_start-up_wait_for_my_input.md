---
title: "Can I make Grub start-up wait for my input?"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by JEBB on 2009-01-11
I have Ubuntu 8.10 and Windows XP/SP3 on my IBM R40 Thinkpad.  When I start up the computer I get a list of choices for startup.  As it is now, I have to act quickly to move the cursor down the list to select Windows if that is what I want to startup.  Otherwise Ubuntu, which is at the top of the list, stars.  Is there a way to make grub stop at the choice list and wait until I am ready to make a choice?  Thanks.

---

### Post by taurus on 2009-01-11
Yes.  You need to edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and put a # in front of the **timeout 3** to comment it out.  Then in a new line below it, add **prompt**.

Save it and reboot.

---

### Post by metalf8801 on 2009-01-11
another way to do it is to get StartUp-Manager using Add/Remove the using it System>Administration>StartUp-Manager 
 
Then uncheck the box next to Use timeout in bootloader menu you can also just give your self more time by adding more time in the timeout in seconds box 

I hope this helps 
Dan

---

### Post by chex_m8 on 2009-01-11
Another option you have is when the grub menu comes up at boot time hit the down arrow once and the count will stop. now you have all the time in the world to make your decision. I've also discovered you can hit the arrow before the menu comes up and the count will be stopped when the menu is displayed.

---

