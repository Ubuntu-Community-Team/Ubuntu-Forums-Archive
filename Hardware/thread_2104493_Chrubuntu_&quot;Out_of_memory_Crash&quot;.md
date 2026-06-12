---
title: "Chrubuntu &quot;Out of memory Crash&quot;"
date: 2013-01-13
forum: Hardware
---

### Post by AlstonA on 2013-01-13
Hello, I am on an Acer C7 notebook and I've been using Chrubuntu (ubuntu on chromebook). So far, I've been having this problem when I close the top of the chromebook netbook. After a while ubuntu would crash causing for me to hold the power button to restart. Is their any way for me to fix this?

---

### Post by Mainkarmic on 2013-02-20
I was having the same problem until I found out that there was no swap space configured during the installation. 

To check do:
swapon -s

To avoid repartitioning the disk to create a swap partition, I just created a swap file. The following link has the instructions for that, just remember to add "sudo" in front of each command.

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

---

