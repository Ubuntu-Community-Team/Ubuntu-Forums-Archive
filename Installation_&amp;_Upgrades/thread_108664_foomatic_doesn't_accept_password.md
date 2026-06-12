---
title: "foomatic doesn't accept password"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by Dr. E on 2005-12-26
I installed the foomatic-gui in order to install my printer drivers and tried to run it. I prompted me for the root password which I gave. It gave me this error message:

Failed to run /usr/bin/foomatic-gui:
Wrong password

I checked my caps lock, ran another application that required the root password, and nothing indicates that there are problems with my password.

I uninstalled and reinstalled foomatic-gui with the same results.

Any ideas?

---

### Post by MotorCityMadMan on 2006-03-07
I'm having the same issue. Here is my happens: Opening Foomatic Printer Configuration tool / unlock keyring window:enter password for default keyring to unlock the application 'gksu' (/usr/bin/gksu) wants access to the default keyring, but it is lock. 

I never assigned a Password for foomatic and the keyring. So i try my log-in password and a new windows comes up: To run the program "/usr/bin/foomatic-gui" you need to enter the root password.

So i do and a new window opens: error: failed to run /usr/bin/foomatic: wrong password.

If someone has time to help i will be grateful

---

### Post by NZ-Wanderer on 2006-03-26
I did find a way around this, open a terminal window and type in

foomatic-gui

this opened it for me....

---

### Post by david_e on 2006-03-27
[QUOTE=MotorCityMadMan]I'm having the same issue. Here is my happens: Opening Foomatic Printer Configuration tool / unlock keyring window:enter password for default keyring to unlock the application 'gksu' (/usr/bin/gksu) wants access to the default keyring, but it is lock. 

I never assigned a Password for foomatic and the keyring. So i try my log-in password and a new windows comes up: To run the program "/usr/bin/foomatic-gui" you need to enter the root password.

So i do and a new window opens: error: failed to run /usr/bin/foomatic: wrong password.

If someone has time to help i will be grateful[/QUOTE]

I'm having the same problem with Synaptic:

[http://www.ubuntuforums.org/showthread.php?p=861187#post861187](http://www.ubuntuforums.org/showthread.php?p=861187#post861187)

it seems that you can still run the application from terminal...

---

### Post by hyg53 on 2008-04-05
There is a difference between gksudo (graphical equivalent to sudo) and gksu which will prompt for the password of the so called "root" user (not superuser).

If an application uses gksu by mistake, you'll need to create a root user, assign a password (sudo passwd root) and use that password of the root user.

---

