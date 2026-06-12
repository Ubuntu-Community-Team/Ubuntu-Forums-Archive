---
title: "tvtime channels"
date: 2005-01-23
forum: Hardware &amp; Laptops
---

### Post by wmfox3 on 2005-01-23
I'm experiencing what TVTime says is a common issue. Channels are off by one detuned so that they appear in black and white. TVTime solution says it's a problem with the bttv card getting set to PAL. But I'm not sure how to fix. Says:

To fix this, the tuner type must be told explicitly when loading your capture driver. For example, with the bttv driver use the following:

    modprobe bttv tuner=2

You may have to first remove the bttv module if it is already loaded. To make this change automatic, in your /etc/modules.conf file, add the following line:

    options bttv tuner=2

But the modules.conf file seems to suggest not making edits to that file. And even when I do add options bttv tuner=2 and reboot, it doesn't seem to work.

---

