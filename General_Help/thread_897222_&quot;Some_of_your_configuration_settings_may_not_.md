---
title: "&quot;Some of your configuration settings may not work properly.&quot;"
date: 2008-08-21
forum: General Help
---

### Post by evanct on 2008-08-21
Whenever i open any application, anything at all, i get an alert with this message:

An error occurred while loading or saving configuration information for [application name]. Some of your configuration settings may not work properly.

the output is this line repeated several times:

```

Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0

```

the applications themselves work fine, but i have noticed some configuration errors, for example font settings won't save in bluefish.

---

### Post by Mister.Vash on 2008-08-21
It's usually because of an error in one of your configuration files.  
First try renaming the folder ~/.gconfd to ~/gconfd.backup and restart gnome.

If that doesn't do it, try the ~/.gconf folder and rename it as ~/gonf.backup and restart gnome.

If it's still causing problems, create another user account and log on to that one just to make sure the error doesn't show with the other account.

Post back the results when you have a chance

---

### Post by Benjamin_Lebsanft on 2008-08-22
I get a grey box when booting into gnome which turns out to be a warning message that gnome-settings-daemon could not be started. Each reboot I lose an applet due to some OAFID: bug which asks me to delete or not delete the concerning applet.

This is latest hardy 32bit

The above gconf tricks didn't work. Before the updates this was a fresh install if this helps.

---

