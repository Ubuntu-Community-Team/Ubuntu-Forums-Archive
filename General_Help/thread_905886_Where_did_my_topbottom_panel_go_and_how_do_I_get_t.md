---
title: "Where did my top/bottom panel go and how do I get them back?"
date: 2008-08-30
forum: General Help
---

### Post by thinkren on 2008-08-30
Hi,

At the moment, I'm using a slightly crippled version of Xubuntu (Gutsy) I've unintentionally done something stupid and I don't know how to undo it.  Can't remember what buttons were pressed, but both my top and bottom desktop panel have disappeared.  I now have just a desktop with a few file system icons.  I've figured out how to access menu item with various combination of mouse clicks. However, other things, like everything in the system tray, are not accessible.  I've poked around the system settings but nothing seem to work in bringing the panels back.  In particular, the "panel" icon in "settings manager" seems to be dead and does nothing.  Can anyone suggest some clues on how I can find out what is going on?

thanks for your time.

-ren

---

### Post by Jose Catre-Vandis on 2008-08-30
I think you need ALT+F2 then run xfce-panel, not sure how you make this persistent though

---

### Post by john.nicholls on 2008-08-30
To make the settings persistent, go to the Settings Manager, Sessions and Startup, and tick Automatically Save Session on Logout.

---

### Post by thinkren on 2008-08-31
> **Jose Catre-Vandis said:**
> I think you need ALT+F2 then run xfce-panel, not sure how you make this persistent though
Just tried that, I get:

The command "xfce-panel" failed to run: failed to execute child process "xfce-panel" (No such file or directory)

Any other suggestions?

---

### Post by Jose Catre-Vandis on 2008-08-31
> **thinkren said:**
> Just tried that, I get:

The command "xfce-panel" failed to run: failed to execute child process "xfce-panel" (No such file or directory)

Any other suggestions?

Sorry, was tired last night!

```
xfce4-panel
```

---

### Post by thinkren on 2008-09-06
thanks!

it worked!

---

### Post by kuitems on 2008-09-25
Thanks for the solution.  This happened to me too when I quit the panel instead of logging out.

---

