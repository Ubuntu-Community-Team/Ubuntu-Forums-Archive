---
title: "&quot;welcome to my [(compiz)] nightmare&quot;"
date: 2008-10-28
forum: General Help
---

### Post by GumboLinux on 2008-10-28
Okay this is just my luck. Everytime I install intrepid something breaks as soon as i get the updates T_T last time it was sound and the time before that wireless. Well its officially compiz Ima keep this short and sweet

my problem arose after I used the sphere plugin to show my buddy the effect. It froze my session and i had to turn it off via the power button. Well I turned it back on and much to my displeasure it did not work. I used the ctrl + alt left click to try and activate the cube desktop. it just created a drag box. I then use shift + f9 for the water plugin...NOTHING ><

well I then reset the computer to try and fix it but that failed so I tried to uninstall it using these commands

 ```
sudo apt-get remove --purge compiz* libcompizconfig* -s
```

then

```
sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev
```

which yielded the results

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "libgnome-compiz-manager0"
Couldn't find any package whose name or description matched "compiz-settings"
Couldn't find any package whose name or description matched "compiz-config-ini"
Note: selecting "emerald" instead of the
      virtual package "gcompizthemer"
Couldn't find any package whose name or description matched "libgnome-compiz-manager-dev"
Couldn't find any package whose name or description matched "compizconfig-backend-kde"
Couldn't find any package whose name or description matched "compiz-config-gnome"
Couldn't find package "taskbar-compiz".  However, the following
packages contain "taskbar-compiz" in their name:
  kicker-taskbar-compiz 
Couldn't find any package whose name or description matched "compizconfig-plugin"
Couldn't find any package whose name or description matched "compiz-freedesktop-dev"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-unofficial"
Couldn't find any package whose name or description matched "compiz-ccs-settings-manager"
Couldn't find any package whose name or description matched "libgnome-compiz-manager"
Couldn't find any package whose name or description matched "compiztools"
Couldn't find any package whose name or description matched "compizconfig-settings-legacy"
Couldn't find any package whose name or description matched "compiz-extra-plugins"
Couldn't find any package whose name or description matched "compiz-decorator"
Couldn't find any package whose name or description matched "gnome-compiz-manager"
Couldn't find any package whose name or description matched "libcompizconfig-dev"
Couldn't find any package whose name or description matched "libgnome-compiz-manager0-dev"
Couldn't find any package whose name or description matched "libcompizconfig-dev"
Couldn't find any package whose name or description matched "libgnome-compiz-manager0"
Couldn't find any package whose name or description matched "compiz-settings"
Couldn't find any package whose name or description matched "compiz-config-ini"
Couldn't find any package whose name or description matched "libgnome-compiz-manager-dev"
Couldn't find any package whose name or description matched "compizconfig-backend-kde"
Couldn't find any package whose name or description matched "compiz-config-gnome"
Couldn't find package "taskbar-compiz".  However, the following
packages contain "taskbar-compiz" in their name:
  kicker-taskbar-compiz 
Couldn't find any package whose name or description matched "compizconfig-plugin"
Couldn't find any package whose name or description matched "compiz-freedesktop-dev"
Couldn't find any package whose name or description matched "compiz-fusion-plugins-unofficial"
Couldn't find any package whose name or description matched "compiz-ccs-settings-manager"
Couldn't find any package whose name or description matched "libgnome-compiz-manager"
Couldn't find any package whose name or description matched "compiztools"
Couldn't find any package whose name or description matched "compizconfig-settings-legacy"
Couldn't find any package whose name or description matched "compiz-extra-plugins"
Couldn't find any package whose name or description matched "compiz-decorator"
Couldn't find any package whose name or description matched "gnome-compiz-manager"
Couldn't find any package whose name or description matched "libcompizconfig-dev"
Couldn't find any package whose name or description matched "libgnome-compiz-manager0-dev"
Couldn't find any package whose name or description matched "libcompizconfig-dev"
The following packages are BROKEN:
  compizconfig-backend-gconf fusion-icon simple-ccsm 
The following packages will be REMOVED:
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main 
  compiz-gnome compiz-plugins compizconfig-settings-manager 
  libcompizconfig0 python-compizconfig 
0 packages upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 25.4MB will be freed.
The following packages have unmet dependencies:
  compizconfig-backend-gconf: Depends: libcompizconfig0 but it is not installable
  simple-ccsm: Depends: python-compizconfig (>= 0.7.8) but it is not installable
               Depends: compizconfig-settings-manager (>= 0.7.8) but it is not installable
  fusion-icon: Depends: python-compizconfig but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
compizconfig-backend-gconf
fusion-icon
simple-ccsm

Leave the following dependencies unresolved:
ubuntu-desktop recommends compiz
cairo-clock recommends compiz
Score is -497

Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main 
  compiz-gnome compiz-plugins compizconfig-backend-gconf{a} 
  compizconfig-settings-manager fusion-icon{a} libcompizconfig0 
  python-compizconfig simple-ccsm{a} 
0 packages upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 26.4MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 124844 files and directories currently installed.)
Removing compiz ...
Removing compiz-gnome ...
Removing compiz-plugins ...
Removing compiz-fusion-plugins-main ...
Removing compiz-fusion-plugins-extra ...
Removing compiz-core ...
Removing compizconfig-backend-gconf ...
Removing simple-ccsm ...
Removing compizconfig-settings-manager ...
Removing fusion-icon ...
Removing python-compizconfig ...
Removing libcompizconfig0 ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information        
Initializing package states... Done
Writing extended state information... Done

then


I then reinstalled it and it still somehow had saved all of my custom settings one example is opacity on cube revolution

well I went to select and unselect them and I could not put a check in the box. None of the effects worked.

whats going on? Anyone who can help gets a big thanks from me =]

---

### Post by k33bz on 2008-10-28
i will be watchin this post, I too started having problems as soon as I upgraded from 0.7.4 to 0.7.6 so I could have the sphere effect. Everynow and then my computer freezes up, and when I reboot, nothing seems to work riht until I reload compiz. :(

---

### Post by GumboLinux on 2008-10-28
:lolflag: >< compiz ftw

---

### Post by GumboLinux on 2008-10-28
=] bump

---

### Post by GumboLinux on 2008-10-29
buuuuuuuuuuuuuumps T_T

---

### Post by overdrank on 2008-10-29
Moved to  Desktop Effects & Customization  :)

---

