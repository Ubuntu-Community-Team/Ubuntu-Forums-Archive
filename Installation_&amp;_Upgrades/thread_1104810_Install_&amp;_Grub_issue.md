---
title: "Install &amp; Grub issue"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by Trido on 2009-03-24
I am trying to install Ubuntu 8.10 server and whenever I boot from the CD and try to select any option, I get a box with Grub Loader in the title bar, then text saying Install (If I selected install, but it does this for every option with different text) and then an ok button. When I hit enter again on that, it just returns me to the menu and does nothing. What the ... ? :)

---

### Post by overdrank on 2009-03-24
> **Trido said:**
> I am trying to install Ubuntu 8.10 server and whenever I boot from the CD and try to select any option, I get a box with Grub Loader in the title bar, then text saying Install (If I selected install, but it does this for every option with different text) and then an ok button. When I hit enter again on that, it just returns me to the menu and does nothing. What the ... ? :)

Hi and welcome, have you checked the cd for errors?

---

### Post by jakslev on 2009-03-24
Do you not get to the screen where you can edit the boot entries? What do you have written as the start-up partition for the menu item called install? 

Mine came up weirdly first (I have a dual-boot with Vista), but I changed the text there to simply say (hd0,1) and that did the trick..

---

