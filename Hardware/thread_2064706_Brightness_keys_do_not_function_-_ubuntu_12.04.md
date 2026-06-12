---
title: "Brightness keys do not function - ubuntu 12.04"
date: 2012-09-30
forum: Hardware
---

### Post by deathbycopypaste on 2012-09-30
Hello and welcome to my third issue posting.  I am running ubuntu 12.04 on a compaq cq62 laptop and the brightness keys do not work using fn+f2 and f3.  After finding nothing on the internet relating to this specific situation (I did find one on these forums for ubuntu 8.something) , i decided to try the instructions at (also pasted below) [http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)

```
Open terminal ( Ctrl+Alt+T ) and type: [INDENT]sudo gedit /etc/default/grub
[/INDENT] You will find this line in the new opened window:
 [INDENT] GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" [/INDENT] Change it to:
 [INDENT] GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" [/INDENT] Save and close the window and type this in the terminal:
 [INDENT]sudo update-grub
[/INDENT]This will update your grub and while rebooting your PC, it will set  an extra parameter on the grub menu during boot. This problem might have  occur on due to the upgrade on kernel.

```
Unfortunately these instructions did not work.  Now, when pressing Fn+f3 it opens a blank file called "x-nautilus-desktop".  This is not what I wanted....  I reverted the changes back to original "quiet splash" and ran sudo update-grub, but the blank file still opens after reboot.  

Any ideas?  Either on how to get the brightness keys to work or how to make it stop opening the file?

---

### Post by deathbycopypaste on 2012-12-04
I have decided to reformat the computer to not only resolve this issue, but other very minor quirks (so minor that I don't recall them at this time). 

Would an older version allow these brightness buttons to work and if so, which one? 
Or should I upgrade to 12.10?

---

### Post by deathbycopypaste on 2012-12-25
Reinstalled ubuntu.  The text editor still comes up with brightness buttons.  Must have been "normal" operation ... oh well.

---

