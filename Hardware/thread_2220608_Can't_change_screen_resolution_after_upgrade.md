---
title: "Can't change screen resolution after upgrade"
date: 2014-04-28
forum: Hardware
---

### Post by timswait on 2014-04-28
I've just upgraded from Kubuntu 12.04LTS to 14.04LTS and now I only have 640x480 screen resolution. I've got an nVidia GT520 card and I use an HD TV connected via an HDMI port. Before the upgrade I was on 1920x1080, and had a full list of resolutions in system settings. Now when I go into system settings the list of available resolutions only show 640x480 and no others. What's gone wrong and how do I get the high resolutions back?

---

### Post by kyle19 on 2014-04-29
Ok, this may be caused by linux itself not your computer, Open Menu-->Additional Drivers-->Then let that load-->Choose Your Nvidia Driver

---

### Post by timswait on 2014-04-29
Cheers, but have already tried that. When I open the additional drivers window I get the message "There are no proprietary drivers available for your computer" (which I find slightly odd, as I would assume there would be an nVidia proprietary driver)

---

### Post by SeijiSensei on 2014-04-29
Open Muon Package Manager and choose "Settings > Configure Software Sources".  Is the "Proprietary Drivers" box checked?  If not, check it.  If Muon doesn't automatically update your sources, then click Check for Updates (or press Ctrl-R) to force an update.  Now try the Additional Drivers application again.

---

### Post by timswait on 2014-04-29
Fantastic! Thank you. No that box wasn't checked. When I checked it then it offered me the nVidia drivers, installed the first one on the list and now I'm back in HD :)

---

### Post by timswait on 2014-04-29
Oh dear, now since fixing the screen, my touchpad has stopped working :( When I go to System Settings>Input Devices>Touchpad there is a warning message at the top of the panel saying "Synaptics driver is not installed (or is not used)" However when I open package manager there is a package named "xserver-xorg-input-synaptics" which is marked as installed. I have tried re-installing it, but it hasn't helped.

---

### Post by timswait on 2014-05-01
Well, that's slightly embarrassing! It turned out to be complete coincidence that the trackpad stopped working after sorting out the video. The reason the trackpad stopped working was, ahem, the batteries in my wireless keyboard with trackpad were getting flat! The keyboard began responding erratically today, so I replaced the batteries et voila, both keyboard and trackpad now working perfectly!

---

