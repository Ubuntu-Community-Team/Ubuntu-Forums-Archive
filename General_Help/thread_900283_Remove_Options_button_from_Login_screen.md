---
title: "Remove Options button from Login screen"
date: 2008-08-25
forum: General Help
---

### Post by slvjerome on 2008-08-25
I've installed Hardy Heron to use in a Kiosk application.

Is it possible to remove the Options button at the Login screen?  

Is it possible to control which menu items appear in the Options list?  For example, how would I only show "Shutdown" and hide the others?

Thanks!
Jerome

---

### Post by Oldsoldier2003 on 2008-08-25
A good place to start would be Kiosk mode. Kiosk mode is a KDE feature, so you'll need to install Kubuntu if you go this route.

---

### Post by Stemp on 2008-08-25
Hi Jerome,

Yes it's possible but by modifying the gdm theme.

---

### Post by kpkeerthi on 2008-08-25
Look for an xml file in /usr/share/gdm/themes/<your-theme>. Open it with your favorite text edit and it should be easy from there.

---

### Post by slvjerome on 2008-08-25
> **kpkeerthi said:**
> Look for an xml file in /usr/share/gdm/themes/<your-theme>. Open it with your favorite text edit and it should be easy from there.

OK.  That allowed me to get rid of the "Options" menu.  It didn't seem to allow me to just allow the "Shutdown" item in the menu.

However I now have the problem with F10.  Users can still get all of the menu items using F10 and I've found no way to disable that or to only allow shutdown.

Any ideas?

---

### Post by slvjerome on 2008-08-27
I can get rid of most of the F10 Actions by setting SystemMenu=false in /etc/gdm/gdm.conf-custom.  But it still shows "Select Language..." and "Select Session...".  How can I get rid of those?  Or better yet disable F10 altogether?

I've searched for hours and can't find a solution.

---

### Post by d2globalinc on 2009-02-05
I solved my problem.. 

To remove options from the F10 menu - you need to set the variables in the /etc/gdm/gdm.conf file for the specific options to blank..

So for example - If you want to remove both the suspend and hibernation buttons from the F10 menu - 

sudo nano -w /etc/gdm/gdm.conf

- Find: "SuspendCommand=/usr/sbin/pm-suspend" and comment it out and add "SuspendCommand=" below it

- Find: "HibernateCommand=/usr/sbin/pm-hibernate" and comment it out and add "HibernateCommand=" below it

so that section of the config will look like this:

```

# Reboot, Halt and suspend commands, you can add different commands separated
# by a semicolon.  GDM will use the first one it can find.
RebootCommand=/sbin/shutdown -r now "Rebooted via gdm."
HaltCommand=/sbin/shutdown -h now "Shut Down via gdm."
#SuspendCommand=/usr/sbin/pm-suspend
SuspendCommand=
#HibernateCommand=/usr/sbin/pm-hibernate
HibernateCommand=

```

You could do the same with the Reboot and Halt (shutdown) commands.

Amazing this was not really well known out there on google..

And if you want to remove items from the list of "Sessions" you need to check this entry in the gdm.conf

```

SessionDesktopDir=/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/:/var/lib/menu-xdg/xsessions/:/etc/dm/Sessions/

```

That shows you what directories GDM looks for to make the list of sessions.

---

### Post by dave66 on 2009-07-22
> **d2globalinc said:**
> 
And if you want to remove items from the list of "Sessions" you need to check this entry in the gdm.conf

```

SessionDesktopDir=/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/:/var/lib/menu-xdg/xsessions/:/etc/dm/Sessions/

```

That shows you what directories GDM looks for to make the list of sessions.

Thanks everyone for the pointers in this thread!

I was wondering if anyone found a method to either disable F10 or to remove the "Select Session", "Select Language" and "Remote Login" when F10 is pressed?

---

