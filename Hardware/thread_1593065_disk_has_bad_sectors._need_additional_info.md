---
title: "disk has bad sectors. need additional info"
date: 2010-10-11
forum: Hardware
---

### Post by crkerns on 2010-10-11
disk utility reads:
self-tests: failed
28 bad sectors

id 5: reallocated sector count: warning
normalized 100
worst 100
threshold: 36
value: 23 sectors 

id 197: current pending sector count: warning
normalized 100 
worst 100
threshold 0
value 5 sectors

many n/a tests

its running good overall w one issue of not accessing my secondary harddrive. is it worry time?

---

### Post by crkerns on 2010-10-11
also, the thread over the issue with the secondary harddrive is located here [http://ubuntuforums.org/showthread.php?t=1593045](http://ubuntuforums.org/showthread.php?t=1593045)  if anyone can shed some light

---

### Post by jahLux on 2010-10-11
Replace the ailing HDD as soon as possible - back-up as much as possible from the failing drive  to CD, then, you could try using Clonezilla to image the data on the failing HDD - act before disaster strikes.

---

### Post by crkerns on 2010-10-11
:/  
thanks a bunch though

---

### Post by ubunterooster on 2010-10-11
sudo smartctl -d ata -a /dev/sdb 

(might be another letter than b but you need to try to scan the disk, might be be sdc)

Note:back up the Drive first before naything else

---

