---
title: "Noob to Linux, need help with a few things"
date: 2008-08-10
forum: General Help
---

### Post by noobLinuxuser on 2008-08-10
hello, I've never really installed Linux until recently when i figured out the hole boot loader thing (after totaling my system twice) but now Windows and Linux are running nicely.

the problem is that i want my computer to boot into Windows by default. (family reasons) and i have found how to change the GRUB boot loader for that it can do this for me. however Ubuntu wont let me make the necessary changes to the GRUB files.
i am wondering, what exactly can i do in order to gain "root axes" for that i can swap the file that has been changed.

I'm new to Linux, and I'm not ready to jump in to the command line in order to do this, so pleas, tell me how to do it with as little Command line as possible, or non at all.

---

### Post by lisati on 2008-08-10
I'm not sure if you can avoid the command line completely with this one.

Have a look here: [http://ubuntuforums.org/showthread.php?t=885439](http://ubuntuforums.org/showthread.php?t=885439)

(edit) p.s. from the command line, you can type something like ```
gksudo gedit /boot/grub/menu.lst
``` then make your changes.

---

### Post by noobLinuxuser on 2008-08-10
thank you, (never found the linked post when serching) im making the changes and should have it right this time (wrong number last time)

---

