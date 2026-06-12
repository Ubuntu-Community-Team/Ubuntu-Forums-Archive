---
title: "Laptop &quot;hangs&quot; on shutdown/restart"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by bcr821 on 2007-11-12
I recently did a clean install of Gutsy and everything seemed to be working fine.  After using it for like a week the laptop started to "hang" when i do a shutdown/restart.  As soon as i tell the laptop to shutdown or restart, the screen goes black and it just sits there until i'm forced to turn it off manually by holding the power button.

Is there something i'm doing wrong?

---

### Post by bcr821 on 2007-11-12
well i seem to have fixed it but i'm not sure how.  I went to a terminal and did a ```
sudo shutdown -h now
``` and watched it shut down.  I saw it had some troubles with the eth1 but other than that shut down perfectly fine.  

After the sucessful shutdown, everything seems to be working much better.  I don't know what i did to fix it but i'm proud of myself

---

