---
title: "Size vs % free not adding up"
date: 2010-03-26
forum: Hardware
---

### Post by lsutiger on 2010-03-26
from df -h
/dev/sda2             171G  155G  7.4G  96% /home


As you can see it shows only 7.4 GB free but the difference between the two (171-155) is 17 GB.
I have my swap on another partition and my trash is free.
Where is this lost space?

---

### Post by jmate24 on 2010-03-26
you have got to remember about the super user which uses 5% of your total drive space when it formats ext3 and ext4

---

### Post by lsutiger on 2010-03-26
Where is that located?

---

