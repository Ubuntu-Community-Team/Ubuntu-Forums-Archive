---
title: "[SOLVED] What do I do when Sysytem hangs"
date: 2008-11-27
forum: General Help
---

### Post by raunchyrex on 2008-11-27
In windows we press crtl+alt+del to bring up the task manager that can aid in restarting or closing the non-responding application. What should I do to achieve this on Ubuntu? Is there any task manager in Ubuntu? And, what is the short-cut key for shutdown(like alt+F4 in windows?):confused:

---

### Post by mike555 on 2008-11-27
ctl + alt + del    will log you out, or you could go to ; system, preferences, keyboard shortcuts , and set up your own ........
   if you can move the mouse when you get a lockup, you might want to add to panel the "force quit " icon ....

---

### Post by damis648 on 2008-11-27
If a program is not responding, the system will recognize that and ask you if you would like to force quit it. If the Caps/Num/Scroll lights are blinking, there is nothing you can do. You must hold down the power button to shut it off. On the other hand, if they are not, and the whole system is bogging up, press Ctrl+Alt+Backspace to force restart X. If that doesn't work, press Alt+SysRq+[RSEIUB], in that order. (IE Alt+SysRq+R, then Alt+SysRq+S, etc, leaving a 1-2 second pause between each). An easy way to remember that is "Raising skinny elephants is utterly boring". This will input directly into the kernel to restart the system, so there is no risk of hardware/filesystem damage, as the power button could do. (BTW, the SysRq key is the same as the Prnt Scrn key)

---

### Post by Cheesehead on 2008-11-27
If only one app is frozen, then open System Monitor to kill that process.

If everything is frozen, including your clock, mouse, and keyboard, then either the xserver or kernel has crashed. You can reset the xserver with CTRL+ALT+BACKSPACE, but you will immediately lose all unsaved work! Of course a kernel crash requires a full reboot.

Sometimes, you get something between. Your machine gets sluggish, or only partially responsive, but doesn't fully freeze up. Try CTRL+ALT+F1 to get into a text terminal, and run the command 'top' to see what is eating your CPU cycles. You can use the command 'sudo kill PID#' to kill the offending process. Then CTRL+ALT+F7 to return to the window environment.

You can always put a launcher to System Monitor on your desktop panel. Or, some CPU cycle monitors (like XFCE's CPU Graph) have one built-in.

---

### Post by brigadoon on 2008-11-27
Press <ctrl><alt>F1 to the terminal log in prompt.

log in with user name and password.

type in top.

observe the offending operation at the top of the list and note it's PID number.

Press <ctrl>Z

Type kill -9 PID# (I always like the -9 option, take no prisoners!)

Press <ctrl><alt>F7

Should return to the GUI with the application killed and your system running OK.

Good luck.

---

### Post by raunchyrex on 2008-11-27
thanks guys .. ctrl+alt+backspace helped

---

### Post by merekat on 2008-12-08
When using RSEIUB or RSEIUO to shut down or restart, how do I prevent the PrintScreen/SysRq button from executing print screen (instead of the desired SysRq function)? I have been having random freezes, so I was just trying to test out RSEIUB while not frozen, but I can't prevent print screen from coming up as soon and I hit Alt+SysRq.

> **damis648 said:**
> If a program is not responding, the system will recognize that and ask you if you would like to force quit it. If the Caps/Num/Scroll lights are blinking, there is nothing you can do. You must hold down the power button to shut it off. On the other hand, if they are not, and the whole system is bogging up, press Ctrl+Alt+Backspace to force restart X. If that doesn't work, press Alt+SysRq+[RSEIUB], in that order. (IE Alt+SysRq+R, then Alt+SysRq+S, etc, leaving a 1-2 second pause between each). An easy way to remember that is "Raising skinny elephants is utterly boring". This will input directly into the kernel to restart the system, so there is no risk of hardware/filesystem damage, as the power button could do. (BTW, the SysRq key is the same as the Prnt Scrn key)

---

