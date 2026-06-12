---
title: "[SOLVED] Simple grub boot loader question, setting default kernel"
date: 2008-08-24
forum: General Help
---

### Post by iamcims on 2008-08-24
How can I swap the -rt kernel to be below the -generic kernel(on the list), so the generic kernel will load by default.

Thanks

---

### Post by drs305 on 2008-08-24
I recommend installing and using StartUp-Manager to alter menu.lst. It's a gui grub menu editor. Install it with:
```
sudo apt-get install startupmanager
```

Run it with the 'startupmanager' command or System, Administration, StartUp-Manager. You can set the **default OS or kernel**, number of kernels to see in the menu, menu display time, and much more. For more information, read the tutorial at the link in my signature line.

---

### Post by iamcims on 2008-08-24
I installed your program, it seems nice, however two new problems arose out of it. I know you're helping me and im not saying it was your fault or anything.

My splash screen has almost a zoomed tiled appearance.

"Quit" menu no longer shows Restart and Shutdown on the list of options.

any ideas?

---

### Post by drs305 on 2008-08-24
> **iamcims said:**
> I installed your program, it seems nice, however two new problems arose out of it. I know you're helping me and im not saying it was your fault or anything.

My splash screen has almost a zoomed tiled appearance.

"Quit" menu no longer shows Restart and Shutdown on the list of options.

any ideas?

The changes that took effect on your machine were most likely the result of using a different kernel, not the result of the StartUp-Manager program itself. If you change the setting back to the original kernel I would expect the problems to disappear. 

Nevertheless, if you changed any appearance or other settings in StartUp-Manager I would suggest you try returning them to the original settings to see if the problems are resolved. If they are not, I would try changing back to the old kernel to verify that the problem is with the one you switched to. If that is the case - that the problem is with your new kernel, I would start a new post to help you solve that problem if you decide to stay with that kernel.

As far as the Quit/Restart command, you can find posts on this forum about this problem and solutions to it. For now, you can run these commands to shutdown or reboot your system from the command line:
Reboot:
```
sudo shutdown -R now
```
Shutdown:
```
sudo shutdown now
```

By the way, I have no connection with StartUp-Manager other than I use it and wrote a tutorial about it. I will help you as I can but it's time for bed here. I will check back in the morning but perhaps others will also help. Best wishes.

---

### Post by mssever on 2008-08-25
> **drs305 said:**
> For now, you can run these commands to shutdown or reboot your system from the command line:
Shortcuts (these commands do just what they say):
```
sudo reboot
sudo poweroff
```

---

### Post by iamcims on 2008-08-25
ok problem fixed. Now i just have the splash screen problem. It looks/loads great on -rt kernel. -generic still looks zoomed in and tiled.

---

