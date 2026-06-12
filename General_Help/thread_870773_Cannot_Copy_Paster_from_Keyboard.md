---
title: "Cannot Copy Paster from Keyboard"
date: 2008-07-26
forum: General Help
---

### Post by gavimobile on 2008-07-26
hey folks, 

I just did a fresh install of ubuntu 8.04 i enabled my video hardware driver.. I then installed compiz fusion. and now i cannot copy and paste from the keyboard. Its more than copy paste its all ctrl shortcuts i believe cause alt+tab works. I have a good feeling this cas something to do with ccsm. id live to hear all of your opinions though!

thanks
gavimoble

---

### Post by ryanhaigh on 2008-07-28
Sounds like ccsm has ctrl (by itself) bound to something. Try using the advanced search and look for ctrl (or do they call it control?) go through each of the results and check for ctrl by itself. The other thing that MAY work is to start compiz from the command line, press ctrl and look at the console output, it may give you a hint as to what plugin is associated with the key.

---

### Post by gavimobile on 2008-08-12
> **ryanhaigh said:**
> Sounds like ccsm has ctrl (by itself) bound to something. Try using the advanced search and look for ctrl (or do they call it control?) go through each of the results and check for ctrl by itself. The other thing that MAY work is to start compiz from the command line, press ctrl and look at the console output, it may give you a hint as to what plugin is associated with the key.

rayanhaigh, thanks for your response, and excuse my late response. I opened terminal and ran sudo compiz. Everything seems to work great now. So what are my options? I need to run compiz in the sessions so it can start each time my computer starts?, or is there another cleaner way of doing this?

also this is an error i saw in my terminal which i dont think is related becuase it works when starting compiz in the terminal
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'

Thanks for your response in advance,

gavimobile

---

### Post by Kevbert on 2008-08-12
Hi and welcome to Ubuntu.  Compiz will start automatically, you shouldn't need to do anything.  Dbus is one of the compiz items. Open up compiz configuration manager and make sure Dbus is ticked (it's under Utilities).

---

### Post by gavimobile on 2008-08-19
thanks for your reply, dbus is already ticked, so im back to step 1.

compiz starts automaticly, thats agreed, however when i open up the terminal and type compiz, my crtl shortcut keys works, but when the computer boots up and i try to use my ctrl shrcut keys, they dont work.

compiz works before i type compiz in the terminal and after i type it in the terminal
tia

---

