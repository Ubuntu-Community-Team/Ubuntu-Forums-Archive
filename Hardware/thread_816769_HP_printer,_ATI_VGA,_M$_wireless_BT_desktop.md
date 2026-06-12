---
title: "HP printer, ATI VGA, M$ wireless BT desktop"
date: 2008-06-03
forum: Hardware
---

### Post by G~[thc] on 2008-06-03
I recently made the switch from Windows to Feisty Fawn and I'm slowly 
getting hardware and software working.  I'm hoping for a little help with
the following:

1) HP Deskjet 4180 printer/scanner
   I found the HP universal driver package, hplip-2.8.5.run 
   my model -is- supported. Downloaded the package, won't install
   when I double-click the icon.  Archive manager opens up automatically 
   and tells me 'Cannot open hplip-2.8.5.run .  Archive type not 
   supported'.  In downloading a host of other plugins/apps (ex: flash, 
   java, adobe reader, azureus, picasa, google earth, opera) and I get the    
   same result.

2) ATI X1950 Driver package: ati-driver-installer-8-5-x86.x86_64.run 
   Same result as above.  All the downloaded packages are Linux driver 
   offerings from product manufacturers or software developer sites.

3) Partial success: I have a 'Micro$oft Keyboard Elite For Bluetooth'
   and 'Micro$oft Intellimouse Explorer For Bluetooth'.  I searched and
   found how to enable bluetooth devices using Terminal, and that's done 
   successfully.  Now I want to find a way to make the mouse's tilt-wheel
   and additional back/forward buttons, as well as the multimedia buttons 
   on the Keyboard work.    

Thanks in advance to anyone for any help with these devices.  
So far my recent conversion (as an average desktop user) 
to Linux is going well.  

G~[thc]

---

### Post by zoiks on 2008-06-03
> **'G~[thc] said:**
> 
1) HP Deskjet 4180 printer/scanner
   I found the HP universal driver package, hplip-2.8.5.run 
   my model -is- supported. Downloaded the package, won't install
   when I double-click the icon.  Archive manager opens up automatically 
   and tells me 'Cannot open hplip-2.8.5.run .  Archive type not 
   supported'.  In downloading a host of other plugins/apps (ex: flash, 
   java, adobe reader, azureus, picasa, google earth, opera) and I get the    
   same result.

G~[thc]

I would suggest abandoning the attempts to install printer drivers directly from executable files, unless you find there's no other way. The *much* better way is to let your Gnome (or KDE, etc) desktop software handle it for you.

If you are using regular ubuntu with Gnome, go to System -> Administration -> Printing, and add a new printer from there.

Many of the other programs you're trying to install are available in the repositories. (flash, java, azureus). I'm not sure you need adobe reader, as the "Evince Document Viewer" may be fine for your needs (check for yourself). Anyway, I'd suggest always searching what's available in the repo's using System -> Administration -> Synaptic Package Manager before attempting to install from binaries.

As for picasa and googleearth, follow the instructions on the google websites for installation.

---

