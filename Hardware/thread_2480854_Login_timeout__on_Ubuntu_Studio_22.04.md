---
title: "Login timeout  on Ubuntu Studio 22.04"
date: 2022-11-12
forum: Hardware
---

### Post by wavesound on 2022-11-12
Hi All
If I boot the box and wonder off while it's booting When I get back after a certain time IE: 10 mins
my login screen is frozen I then need to hardboot the box.

Is there a setting I need to change to stop this?

Not really a problem more annoying. 

Cheers All.

---

### Post by ajgreeny on 2022-11-12
The command ```
lightdm-gtk-greeter-settings-pkexec
``` should open the settings dialogue for lightdm (I'm assuming Ubuntu-studio uses lightdm) and in the 4th ***Misc*** tab of ghat there is a setting to change the ***Timeout until screen blanks*** or set it to never if you wish.

---

### Post by ajgreeny on 2022-11-12
Having searched I see that Ubuntu-Studio uses sddm not lightdm but nevertheless there may be a similar settings application for sddm so search through the menu to see if you can find anything that looks appropriate.

---

