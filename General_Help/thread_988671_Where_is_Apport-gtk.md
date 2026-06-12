---
title: "Where is Apport-gtk?"
date: 2008-11-20
forum: General Help
---

### Post by DonQuichote on 2008-11-20
On "How to submit a bug" ( [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) ), the application "Apport" is mentioned. I even have it installed and it is nowhere to be found. apport-gtk is not in the path, there is no launcher to it and it even displays no user interface when fired directly ( /usr/share/apport/apport-gtk ). There is also no man page for apport-gtk. Should I report a bug on the bug reporter?

---

### Post by prshah on 2008-11-20
> **DonQuichote said:**
> there is no launcher to it and it even displays no user interface when fired directly ( /usr/share/apport/apport-gtk ). 

Should I report a bug on the bug reporter?

It's been done.

To get apport working: 
[indent]first, right-click the menu and choose "Edit Menu"
Then, choose "System Tools", and place a check mark next to "Report a problem...". 
Then, click Properties. 
Edit the last part of "Command" and remove the "-c %f" part of it. 
Click "Close" twice. 

You should now have an entry for "Report a problem..." in your System Tools menu.[/indent]

If apport still doesn't launch, make sure the daemon is running from System-Administration-Services-Automated Crash Reports Support.

---

### Post by DonQuichote on 2008-11-22
> **prshah said:**
> It's been done.

To get apport working: 
[indent]first, right-click the menu and choose "Edit Menu"
Then, choose "System Tools", and place a check mark next to "Report a problem...".[/indent] 

I assume you use the Gnome environment. Editing the menu is not an option for XFCE users, alas. We can add extra menus, but not edit the "installed" one. There is no option "System tools", and if I edit the properties of the "system menu" entry (which contains the entire installed menu), I can only choose between simple and multilevel view.

> **prshah said:**
> [indent]Then, click Properties.
Edit the last part of "Command" and remove the "-c %f" part of it. 
Click "Close" twice. 

You should now have an entry for "Report a problem..." in your System Tools menu.[/indent]

If apport still doesn't launch, make sure the daemon is running from System-Administration-Services-Automated Crash Reports Support.

The automated crash report service is active.

---

