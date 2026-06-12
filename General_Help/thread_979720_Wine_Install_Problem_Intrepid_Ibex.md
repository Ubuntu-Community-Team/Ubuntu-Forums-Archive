---
title: "Wine Install Problem Intrepid Ibex"
date: 2008-11-12
forum: General Help
---

### Post by russ5811 on 2008-11-12
I had wine installed, but there were lots of menu items in the wine start list that were not really installed (due to incompatibility with wine). So, I uninstalled wine thinking it would clear it out. 

After uninstalling, the wine options were gone, but the worthless windows program links were still there. So I went to System> Preferences > Main Menu and manually deleted the windows links. 

When I reinstalled Wine, there are NO wine links in applications!! I have uninstalled again and reinstalled. Nothing I do gets wine links back to my applications window. I have gone back to system > preferences > main menu to see if I can manually add them...this option is not available.

I am using 8.10 AMD 64 edition.

Please Help!! Thank you.

---

### Post by eternalnewbee on 2008-11-12
Maybe you should reinstall the Applications you want to run with **wine** again?

---

### Post by AndyCooll on 2008-11-12
This is a problem with the "Menu" rather than Wine itself. You could probably delete the config file (for it should automatically create a new one). 

Something along the line of the following IIRC:
```
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bak
```

Logging out and back in again should create a new default listing

:cool:

---

### Post by russ5811 on 2008-11-12
that worked to get wine back on the menu. Thank you. However, there is a new problem now. The old windows apps that I don't have installed are still showing in the menu??

---

