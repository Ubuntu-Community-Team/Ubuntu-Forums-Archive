---
title: "Fresh Install does not have Printing Menu Entry"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by mmorgan27 on 2009-02-01
I just did a fresh Ubuntu 8.10 Desktop install.  I'd like to add a printer but there is no *Printing* menu entry.

Under *System*->*Administration* I only have:
[LIST]
[*]Hardware Drivers
[*]NVIDIA X Server Settings
[*]Software Sources
[*]Update Manager
[/LIST]

 Do I need to add a package to get the *Printing* entry?

---

### Post by Partyboi2 on 2009-02-02
It should automatically be added. Try opening  "Main Menu" System>Admin>Main Menu and on the left select Admin and make sure the box is ticked for "Printing" or anything else that you want to add and is missing. Then see if it appears in the menu.

---

### Post by mmorgan27 on 2009-02-02
There is no "Main Menu" the 4 items I listed in my initial post are the only menu entries under "Admin".

---

### Post by Mark Phelps on 2009-02-02
Right-click Applications, select Edit Menus, scroll down to the bottom under System, and select the Administration menu. You should see the full set of menu items on the right.  Check the Printing menu item to have it appear in the list.

---

### Post by Partyboi2 on 2009-02-02
> **mmorgan27 said:**
> There is no "Main Menu" the 4 items I listed in my initial post are the only menu entries under "Admin".
My mistake, Main menu is under system>Pref not system admin.

---

### Post by mmorgan27 on 2009-02-02
> **Mark Phelps said:**
> Right-click Applications, select Edit Menus, scroll down to the bottom under System, and select the Administration menu. You should see the full set of menu items on the right.  Check the Printing menu item to have it appear in the list.
This response is exactly what I was looking for, but there is no *Printing* menu item to add.  Is my install hosed?  There were no warnings/errors during the install.

---

### Post by mmorgan27 on 2009-02-02
> **Partyboi2 said:**
> My mistake, Main menu is under system>Pref not system admin.
I have no "Main Menu" under Prefs.  Does this mean I need to re-install? The install proceeded without error so I'm not sure what could happen differently.

---

### Post by Partyboi2 on 2009-02-02
Open a terminal (Applications>Accessories>Terminal) and post the output to
```
dpkg -l alacarte
```

---

### Post by mmorgan27 on 2009-02-03
> **mmorgan27 said:**
> I have no "Main Menu" under Prefs.  Does this mean I need to re-install? The install proceeded without error so I'm not sure what could happen differently.
root@Desktop:~# dpkg -l alacarte
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alacarte       0.11.6-0ubuntu easy GNOME menu editing tool

---

### Post by Partyboi2 on 2009-02-03
You have Alacarte installed try starting it from the terminal by typing
```
alacarte
``` and post the output.

---

### Post by mmorgan27 on 2009-02-04
> **Partyboi2 said:**
> You have Alacarte installed try starting it from the terminal by typing
```
alacarte
``` and post the output.
It looks like alacarte is what runs when you right-click on the *Applications* menu and select *Edit Menus* (posted by Mark Phelps a few posts up).  It has no *Printing* entry anywhere.

Appreciate the help!

---

### Post by dpinho on 2009-02-04
this worked for me:

sudo apt-get install system-config-printer-gnome

---

### Post by mmorgan27 on 2009-02-05
root@Desktop:~# apt-get install system-config-printer-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
system-config-printer-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Desktop:~#

---

### Post by dpinho on 2009-02-05
hmm strange,

I didn't have the menu entry after i upgraded to intrepid, and doing that apt-get install fixed it nicely.

Try playing around with some of apt-get options (--reinstall etc.) to see if that helps.

Or you can just create the entry yourself. In my system it invokes /usr/bin/system-config-printer

---

