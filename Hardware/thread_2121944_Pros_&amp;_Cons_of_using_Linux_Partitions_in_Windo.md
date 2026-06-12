---
title: "Pros &amp; Cons of using Linux Partitions in Windows"
date: 2013-03-03
forum: Hardware
---

### Post by thilina1024 on 2013-03-03
Hi All,

I'm gonna buy a laptop soon. So, I'm thinking about partitioning. I've been using Ubuntu for more than 2yrs. I hope to use it along with Windows. So, I will have to allocate partitions for both Windows & Linux systems. Besides that, regarding my personal data such as docs, projects, photos, & software installers etc., I will create another partition. Although at first, I had planned to create that partition as a NTFS, later I got another idea. That's what regarding which I want to know any ideas, advices from you guys. :) What if I create that data partition as a Linux (ext4) & mount & unmount it in Windows using a tool like "[Ext2Fsd]("http://www.ext2fsd.com")"?. What I was thinking was, since I can unmount that partition when I don't need it, if my computer got infected, that partition will be intact. Actually, I just assumed that an unmounted partition won't be affected by viruses, malware, etc. Not that I know that fact for sure. So, I want to know facts regarding security, safety & performance regarding using partitions like that.

Thank You :)

---

### Post by dabl on 2013-03-03
I would advise you to test your theory -- that Windows can read some data on an ext4 partition.  If it works, then that's definitely the way to go.

---

