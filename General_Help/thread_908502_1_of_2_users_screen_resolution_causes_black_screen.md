---
title: "1 of 2 users screen resolution causes black screen"
date: 2008-09-02
forum: General Help
---

### Post by j.e.ludovico on 2008-09-02
Hello,

I was testing a program in different screen resolutions and unfortunately set it to such value that my LCD can't display it. My other user account display and xorg.conf default are fine but i need to know what file should I edit to restore default resolution for my other user account too.

---

### Post by j.e.ludovico on 2008-09-02
> **j.e.ludovico said:**
> Hello,

I was testing a program in different screen resolutions and unfortunately set it to such value that my LCD can't display it. My other user account display and xorg.conf default are fine but i need to know what file should I edit to restore default resolution for my other user account too.


1 did the following:

1. CTRL+ALT+F1 for virtual console
2. login   to log in and log in 
3. gconftool-2 --set /apps/metacity/global_keybindings/run_command_terminal -t string "<Control><Alt>x"    to set keyboard short cut for lauching terminal
4. logout
5. CTRL+ALT+F7    to go back to killed black screen 
6. CTRL+ALT+x    to lauch terminal
7. xrandr -s 0    to set default screen size

Yeah, good luck with that.

---

