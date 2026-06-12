---
title: "Please recommend me a partitioning scheme"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Pidgin on 2009-04-23
Now I am preparing to install Ubuntu 9.04. In the past I was keeping using Ubuntu with only one ext3 partition mounted as root and a swap partition, which I know is not a good scheme. I have about 15 GB space for Ubuntu and 2 GB RAM. Please recommend me a partitioning scheme. Thank you!

---

### Post by caprajack on 2009-05-05
Check out the site below for sample partitioning configurations.

[http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html)

---

### Post by wpshooter on 2009-05-05
> **Pidgin said:**
> Now I am preparing to install Ubuntu 9.04. In the past I was keeping using Ubuntu with only one ext3 partition mounted as root and a swap partition, which I know is not a good scheme. I have about 15 GB space for Ubuntu and 2 GB RAM. Please recommend me a partitioning scheme. Thank you!

If you have 2gb of RAM it is unlikely that you will ever use SWAP, therefore you might want to consider foregoing the SWAP.

Consider:

/ = root - 6gb ext4
/home = home - 8gb ext4
/SWAP = swap - 1gb or possibly no swap and put this extra 1gb on /home

---

