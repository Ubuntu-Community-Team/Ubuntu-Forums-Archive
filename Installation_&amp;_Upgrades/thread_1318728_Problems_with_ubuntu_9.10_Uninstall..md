---
title: "Problems with ubuntu 9.10? Uninstall.?"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Edgar09 on 2009-11-07
Hi everyone.. A couple of days i finally convinced my pal "Windows User" to try & install the New Karmic Koala Ubuntu 9.10. I burned the ISO in a CD & he took it home. Today he installed it & he said worked perfectly. But when he reboot it he couldnt get back to windows nor linux.!! He says that in the screen appears an error 'Grub rescue' or something like that... & that the swap doesnt appear.! This really makes me feel bad cause i finally convinced him..

But now he wants to uninstall but i dont know how.?
Please help me Linux experts.!

---

### Post by jheaton5 on 2009-11-07
We need more information than that.  Can you get him and his computer (laptop?) over so we can get better information?

---

### Post by ssican on 2009-11-07
Possibly this will help:

On item 10, of the PAGE -Grub 2 Basics-

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

There is this Information:

10- How to Boot to the Recovery Mode w/o a Menu Option

   1. If you have Grub 2 set to boot without displaying the menu at all, hold the SHIFT key down until the menu displays. (In Grub it was the ESC key.)
   2. Press any key once the menu is displayed to 'freeze' it. Then arrow to the kernel you want to boot.
   3. Press E
   4. Scroll to the end of the "linux /boot/vmlinuz...." line. If displayed, remove "quiet" and/or "splash". Add the word "single" to the end of the line.
   5. Press CTRL-X to boot to the Recovery menu.

---

