---
title: "Problems Installing Proprietary Drivers"
date: 2011-10-17
forum: Hardware
---

### Post by metal-mitch on 2011-10-17
Ok, so i'm pretty much a novice when it comes to Ubuntu, I've recently upgraded to 11.10 from 11.04 largely due to the better support of the Gnome 3 shell. After installing Gnome 3 shell through terminal using a guide I found on the internet, there were graphical glitches all over the place.

After some extensive research I found it was probably the drivers for my graphics card. I followed another guide found on the internet on removing FGLRX and installing native ubuntu drivers which were supposed to be better, and now i cannot even start gnome 3 shell, it reverts me to classic mode automatically.

I want  to try and install catalyst 11.9 via jockey but I cannot install the proprietary drivers, there is constantly a problem when it comes to installing FGLRX whether I try in synaptic package manager or through jockey. The problem is the following:[INDENT]> /usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the AMD driver
 is not installed, the AMD driver is only partially installed,
 or the current AMD driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).[/INDENT]I have checked and thats correct there is no path by those names, so whats the problem? i dont want it uninstalling anything i want it installing FGLRX

All i want is to install catalyst 11.9 drivers so I can run Gnome Shell 3 as was intended, please all help would be appreciated and apologies if I have missed anything out or seem to have misunderstood anything.

also here is my Laptop Setup in case this helps in any way:

ACER ASPIRE 5551
AMD Athlon II X2 Processor P320 (2.1 GHz)
ATI Mobile RadeonHD 4250 Graphics
3GB Memory

---

### Post by sandy8925 on 2011-10-17
try here: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

i'm having difficulty installing fglrx manually after using ubuntu's (11.04 64 bit) restricted drivers option. but it works perfectly on a clean install. i guess it screws things up.

---

