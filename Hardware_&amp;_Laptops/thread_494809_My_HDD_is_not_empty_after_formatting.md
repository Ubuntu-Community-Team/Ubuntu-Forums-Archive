---
title: "My HDD is not empty after formatting"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by siDDis on 2007-07-07
I just formatted two 500 GB harddisk drives, both of them had 7.5GB of data afterwards.

What is that? Can I get rid of it?

---

### Post by taurus on 2007-07-07
How did you format it and what filesystem did you create?

---

### Post by siDDis on 2007-07-07
I used Gnome Partition editor, I formatted as ext3.

---

### Post by taurus on 2007-07-07
Are you talking about lost+found directory on those drives?  Have you mounted them?  **_Assuming_** you've mounted one of them to /media/extra, what's the output of this command from a terminal?

```
sudo du -h /media/extra
```

---

### Post by siDDis on 2007-07-08
The lost+found directory were a shortcut, so I just deleted them. however I found out that some disc  space get automaticly reserved for root.

I adjusted this to 0 with tune2fs -m 0 /dev/sdc1

---

