---
title: "Western Digital head parking issue"
date: 2021-03-25
forum: Hardware
---

### Post by kenshep11 on 2021-03-25
I have formatted two Western Digital Iron Wolf 16 tb hdds in Ext4 and when I mount them they make a slight noise every second.  It has been described on other forums as a power saving parameter that is attempting to save power by parking the heads.  The sudo hdparm -b 255 and -b 254 did not turn this off.  

any thoughts on how to stop this?  They go silent when unmounted.

---

### Post by mikewhatever on 2021-03-25
It should be <hdparm -B 254>, as <hdparm -b> is for something else.

---

