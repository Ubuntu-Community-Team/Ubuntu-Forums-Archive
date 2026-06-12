---
title: "Synaptic shortcoming"
date: 2008-08-06
forum: General Help
---

### Post by the real omni on 2008-08-06
Hey folks.

Just a general gripe/suggestion for the next update to synaptic package manager.

I've installed a lot of packages through Synaptic and the one common thread I find among every installation is that NOTHING seems to explain how to actually launch the installed application, so I have to try hacking around in the terminal window to find out what I'm supposed to type in order to launch something. 

There are lots that are pretty obvious - for example, to launch thunderbird you just type thunderbird... but there are some that have a launch command that's completely different (or abbreviated or..) from the package name.

It would be great if Synaptic would look inside a package as soon as it finishes downloading, looks for the name of the binary to be launched, and displays the launch command in the installation report.

---

### Post by unoodles on 2008-08-06
The way I find the application, is go to synaptic, right click on the package, click properties, then go to installed files tab, and find the executable. The executable will be the one in a */bin folder (for example /usr/bin).

---

### Post by issih on 2008-08-06
Not a perfect solution, but if you select an installed package in synaptic, then hit properties, the installed files tab will list all the files that package dropped into your ubuntu distribution.

Actually telling you the name of the binary in a prominent way wouldn't be a bad idea though.

---

### Post by billgoldberg on 2008-08-06
99% of the time, you launch the application with the exact same name the package has.

Or you could just find it in gnomes menu's or use alt+f2 or in a terminal use tab completetion.

---

### Post by the real omni on 2008-08-06
> **billgoldberg said:**
> 99% of the time, you launch the application with the exact same name the package has.

Or you could just find it in gnomes menu's or use alt+f2 or in a terminal use tab completetion.

I'd say realistically about 70% of the time the application will launch with the package name as the command, not 99%.

20% of the time the app will launch if you type the name of the package and strip out the version number.

5% of the time the app will launch if you type the name of the package and *append* the version number.

5% of the time the app will launch if you type something else altogether.


I would love it if I could just find it in gnome's menus but 99% of the time nothing is installed into the gnome menus. (Ok, maybe closer to 96% of the time but out of the dozens and dozens of apps I've installed, only 3 or 4 have installed menu launchers.)


Anyway not so much a gripe inasmuch as a suggestion - it would be great to see a feature like this in the next revision :)

---

