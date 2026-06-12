---
title: "HP Deskjet f4180 scanner not scanning"
date: 2011-06-12
forum: Hardware
---

### Post by marsgorski on 2011-06-12
Hi. I just installed Lubuntu 11.04 on an old Compaq desktop. I have an HP Deskjet f4180 all-in-one. To get the printer working I had to install hplip from Synaptic. However, scanner is not recognized by either xsane or simplesscan. I have searched the forums but I have not found anything useful. Does anyone have any suggestions?

---

### Post by mizzou_tiger on 2011-10-13
I was having the same problem. I did a little research and I found this thread: [https://answers.launchpad.net/hplip/+question/57468](https://answers.launchpad.net/hplip/+question/57468)

If you look at the last comment in the thread (#21) the commenter suggests to remove everything to do with "sane, hplip, scanners, etc.," I personally did not do this and everything works ok. But It does suggest some other programs that were not installed on my computer like libsane, libsane-extras, sane-utils, xsane, xsane-common and hplip from the synaptic repository. I don't think you'll need xsane or xsane-common but I downloaded it anyway, and everything works great now. Hope this helps!

---

