---
title: "Install Over Previous Version"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Sidhiel on 2009-04-26
I just recently started using Ubuntu, and found out that I was actually five version behind the current one....since upgrading was not an option, I am going simply to install Jaunty over it. How do I handle the partitioning? Just delete the old partition and install over it?

---

### Post by Arathon on 2009-04-26
That will work fine, as long as there's nothing on that partition that you want to save.  If you're using the manual partitioning option, tell it to format the partition as ext3 or ext4, and mount the partition as "/" (without the quotation marks).

---

### Post by Sidhiel on 2009-04-26
All right, thanks.

---

### Post by lovinglinux on 2009-04-27
You might also want to create a separate partition and mount it as /home. Make it big, because this is were you save all your personal files and most of the configuration files.

When you decide to install a new release, you can keep the /home and format only the system partition. This way you can "upgrade" with a fresh install, but keeping all your stuff and personal adjustments. It will look the same, but will be a fresh new system.

To learn more about this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

