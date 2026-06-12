---
title: "how do i get access to the rest of my storage?"
date: 2020-04-28
forum: Hardware
---

### Post by oskarax on 2020-04-28
how can i get access to the rest of my drive? it was previously a windows 8 drive but i converted the laptop to a ubuntu server running 18.04.4 LTS (GNU/Linux 4.15.0-96-generic x86_64). i do have the possibility to reinstall if nothing else works.

---

### Post by Dennis N on 2020-04-28
Most of your drive space is an LVM volume group existing in sda3 in which a small root logical volume exists. Do you know LVM? You will need to use some LVM commands to create other logical volumes in that 930 GB space for your use, or to enlarge the root. If you don't know LVM, you might look at this:

[Ubuntu LVM Guide]("https://tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html") 

Here's another that's worth reading:

[LVM Demystified]("https://www.linuxjournal.com/content/lvm-demystified")

It's a beginning.

---

### Post by oskarax on 2020-04-28
Thanks!
I have to look about that.

---

### Post by oskarax on 2020-04-28
Got it done!
in the end for my case it was just the process of running this command: sudo lvextend --resizefs --size 912G /dev/ubuntu-vg/ubuntu-lv

---

