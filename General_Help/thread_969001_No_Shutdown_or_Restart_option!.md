---
title: "No Shutdown or Restart option!?"
date: 2008-11-03
forum: General Help
---

### Post by ricster on 2008-11-03
Upgrade went very smoothly from 8.04 to 8.10 last night but after rebooting and checking my email was still there (hurrah!) I clicked the red power button at the top right of the screen to shut down like i normally do (as does the wife) to only be given the option to "Log out" and "Switch User".

I never use "Switch User" so would like to get rid of that and have my shutdown and restart options back. I have no issues with editing a config file to do that, just point me at it if there is one!

I'm aware that there's a "Shutdown" option in the System menu but i'd prefer to just keep the 2/3 options i actually use tied to that big red onscreen button!

---

### Post by cmnorton on 2008-11-05
I am not quite sure what you want to do, or if this is Ubuntu, Kubuntu, Xubuntu, or something else. It seems like you will need to go into startup under Admin and play around with the look of your menus.

---

### Post by mc4100 on 2008-11-05
> **ricster said:**
> Upgrade went very smoothly from 8.04 to 8.10 last night but after rebooting and checking my email was still there (hurrah!) I clicked the red power button at the top right of the screen to shut down like i normally do (as does the wife) to only be given the option to "Log out" and "Switch User".

I never use "Switch User" so would like to get rid of that and have my shutdown and restart options back. I have no issues with editing a config file to do that, just point me at it if there is one!

I'm aware that there's a "Shutdown" option in the System menu but i'd prefer to just keep the 2/3 options i actually use tied to that big red onscreen button!

Shutdown/logout was reworked to more resemble upstream, and now the preferred way is to replace the old shutdown button with the User Switch applet (Through right clicking the panel, "Add to Panel" -> User Switcher -> Add). Alternatively, you can create your own custom shutdown button, making it run the command:
```
gnome-session-save --shutdown-dialog
```

---

### Post by mac-duff on 2008-11-09
Hi,
is it possible to edit the current button with that command?

 gnome-session-save --shutdown-dialog

I have an EEE PC with not the standard taskbar. Can u tell me the file where I can change it?

Thx

---

### Post by Ryadt on 2008-11-09
> **ricster said:**
> Upgrade went very smoothly from 8.04 to 8.10 last night but after rebooting and checking my email was still there (hurrah!) I clicked the red power button at the top right of the screen to shut down like i normally do (as does the wife) to only be given the option to "Log out" and "Switch User".

I never use "Switch User" so would like to get rid of that and have my shutdown and restart options back. I have no issues with editing a config file to do that, just point me at it if there is one!

I'm aware that there's a "Shutdown" option in the System menu but i'd prefer to just keep the 2/3 options i actually use tied to that big red onscreen button!
Go in System > Administration > Login Window. Under the 'local' tab check the box 'Show Actions Menu'. That should do it.

---

### Post by mac-duff on 2008-11-09
and what is if this box is clicked but its still not working?

---

