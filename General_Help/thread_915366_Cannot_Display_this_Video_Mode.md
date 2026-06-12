---
title: "Cannot Display this Video Mode"
date: 2008-09-09
forum: General Help
---

### Post by mike1234 on 2008-09-09
Is anyone having trouble with Supertux 2? For whatever reason Supertux 2 displays "Cannot display this video mode" when launched. Supertux 1 works fine. I have 1280x1024 display. Nvidia video with the correct driver. Just wondering if development of S2 is still  in progress. Another poster had same problem. No answers. The only time I ever had it working was in Debian etch without nvidia 3D enabled. I have Ubuntu 8.04 with Gnome, up to date and no other problems with anything. I also can hear sounds when game launches. Just no video. 

[http://ubuntuforums.org/showthread.php?t=804746&highlight=supertux](http://ubuntuforums.org/showthread.php?t=804746&highlight=supertux)

M.

---

### Post by fooman on 2008-09-09
maybe something in the config file is messed up.  try deleting the config file for supertux2.  look in your home directory for the ".supertux2" file and delete it.  then try starting the game again.

that file is hidden (thus the . before the name), so to see it you must open your home folder and in the toolbar go to view.  put a check next to "show hidden files".  then find .supertux2 and delete it.

---

### Post by mike1234 on 2008-09-09
> **fooman said:**
> maybe something in the config file is messed up.  try deleting the config file for supertux2.  look in your home directory for the ".supertux2" file and delete it.  then try starting the game again.

that file is hidden (thus the . before the name), so to see it you must open your home folder and in the toolbar go to view.  put a check next to "show hidden files".  then find .supertux2 and delete it.

 I'll try but this always happens when I install Supertux 2. Just wondering if anyne else has noticed this. Let you know.

M.

---

### Post by mike1234 on 2008-09-09
> **fooman said:**
> maybe something in the config file is messed up.  try deleting the config file for supertux2.  look in your home directory for the ".supertux2" file and delete it.  then try starting the game again.

that file is hidden (thus the . before the name), so to see it you must open your home folder and in the toolbar go to view.  put a check next to "show hidden files".  then find .supertux2 and delete it.


 No luck. Deleted S2 folder. (which obviously has nothing in it since game didn't launch). S2 doesn't seem to like nvidia 3D. I think (not sure) it worked for me in gutsy. I wonder if it just isn't compatible yet with hardy? Part of my original question.

M.

M.

---

### Post by fooman on 2008-09-09
sorry man.  

btw,  i have nvidia 8800gt on hardy and supertux2 runs fine here w/visual effects enabled.

---

### Post by mike1234 on 2008-09-09
> **fooman said:**
> sorry man.  

btw,  i have nvidia 8800gt on hardy and supertux2 runs fine here.

  I have the older PCI FX5500. Dell server SC420 onboard 8 meg Intel. Not sure if you're familiar with it. I cannot totally disable onboard. It co-exists with plugin card. Suse won't even install. Gets confused. Thanks anyway man. Funny I have had it working before. One of those linux things.

M.

---

