---
title: "Unwanted Screenlets Loading At Boot Up"
date: 2008-11-15
forum: General Help
---

### Post by MTGap on 2008-11-15
There are a ton of unwanted screenlets that keep loading when I turn on my computer and I have to get rid of them every time by hitting delete screenlet, yet they still come up. Why are they doing this?

---

### Post by binbash on 2008-11-15
open screenlet manager, select the screenlet you want to disable auto start(select it inside the screenlet manager), there is 2 options left side of the manager, one of them is auto star on login (something like that), untick that.

---

### Post by ddarsow on 2008-11-15
I had this same thing happen where (in my case) multiple instances of each of my screenlets would load at startup resulting in a mess. I resolved it by going to **System > Preferences > Sessions** and removing the multiple entries from the **Startup Programs** tab.

I have no idea why it happened though!

If that does not work, you may need to edit the .screenlets/config.ini file in your Home directory. [Ctrl][h] to show the hidden .screenlets directory

---

### Post by MTGap on 2008-11-15
The main problem is I don't even want the screenlets that are starting, I keep hitting delete screenlet and it keeps coming back...

---

### Post by binbash on 2008-11-15
dude it will come back because you selected autoload before.Do ddarsow's way or mine.or you can remove the screenlets via sudo apt-get remove screenlets : )

---

### Post by pjizz on 2008-11-15
hi...i'm having a similar problem.

i also have two instances of every screenlet load everytime i reboot.  i checked the startup programs in sessions (nice tip) but didn't see any double entries.  looking at config.ini didn't give me any other ideas.  help?

---

### Post by pjizz on 2008-11-17
bump

---

### Post by sirjoebob on 2008-11-17
Go to applications>preferences>screenlets.

Highlight each on that keeps popping up and uncheck autostart on login or w/e the option is and then uncheck the start/stop checkbox. This should resolve it. Otherwise, completely remove and reinstall screenlets.

---

### Post by pjizz on 2008-12-07
i uninstalled and reinstalled several times, but every time I install and turn on even one screenlet, when I pull up the widget layer, I have two of them.  I even deleted the .screenlets folder in the home directory, but still I get double screenlets.

---

