---
title: "Wine problem"
date: 2008-10-26
forum: General Help
---

### Post by Spider44 on 2008-10-26
I was trying to make a game run but it kept saying that it couldn't load directX, so i intalled directX on wine.Since that moment everything else was working just fine after that nothing was working.I was trying to lounch apps and they kept crashing with no error messeges coming up, they just wonn't run.I tried to uninstall and reinstall wine but still nothing.Any ideas???

Thanks for your time

---

### Post by markharding557 on 2008-10-26
wine has its own directx so you shouldn't be installing the ms version.
you can have a look on wines database to see if your game can run
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by CatKiller on 2008-10-26
When you uninstall a package, your configuration files aren't generally deleted. These are normally stored as hidden files in your Home directory.

In the case of Wine, all of the files (including your pretend C: drive as well as Wine's own files) are stored in the directory ~/.wine. If you delete or rename this directory, the next time you run Wine you will have a pristine install to work from.

While specific files from Windows can help with getting some programs to work in Wine, installing the full DirectX in Wine just breaks Wine's own DirectX system, as you've found.

---

### Post by Spider44 on 2008-10-27
I did find that...but the problem is that i have uninstalled it and deleted the .wine folder and the reinstalled wine and i still have the same problem... :(

---

### Post by Spider44 on 2008-10-27
oh btw, dunno if it helps,but when i uninstall it the folders at Applications/Wine still remains there even if I delete the .wine folder

---

### Post by CatKiller on 2008-10-27
> **Spider44 said:**
> I did find that...but the problem is that i have uninstalled it and deleted the .wine folder and the reinstalled wine and i still have the same problem... :(

You don't need to uninstall Wine. Just removing the ~/.wine folder will put your Wine install back to how it was originally. You haven't been re-installing DirectX, have you?

The menu launchers are a way to integrate your Windows applications more seamlessly into your normal usage. They are stored in ~/.local/share/applications, I believe.

---

### Post by ajmartinez on 2008-11-18
Here is the problem I have with Wine:

I installed Wine and try to run winecfg and here is what I get


There is no titles on the tabs
No titles on the buttons
not a single word in the winecfg window.

All the applications I try are the same. No titles, no text, nothing

I delete the ~/.wine folder
Re-run wine and it did created the ~/.wine folder but the wine-gecko was not there. I re-installed the wine-gecko but nothing.

change the font type, nothing
removed wine and re-install it, nothing

Please Help!

OS: Ubuntu 8.10 Ibex
Wine: 1.8

---

### Post by ajmartinez on 2008-11-19
Thanks guys.

I found the problem.

It was in the WINE.INF on the [Desktop]
The "HKCU_software\wine\X11 Drivers" was missing and also was missing on the User.reg on the [Desktop]

---

### Post by Lightstar on 2008-12-02
> **ajmartinez said:**
> Thanks guys.

I found the problem.

It was in the WINE.INF on the [Desktop]
The "HKCU_software\wine\X11 Drivers" was missing and also was missing on the User.reg on the [Desktop]

Can you explain how you fixed it?
I have a similar problem, though my files are elsewhere.

My wine.inf is in /usr/share/wine/wine.inf
My user.reg is in /home/myname/.wine/user.reg

is "HKCU_software\wine\X11 Drivers" a line I need to add somewhere?

---

