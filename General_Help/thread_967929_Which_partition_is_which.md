---
title: "Which partition is which?"
date: 2008-11-02
forum: General Help
---

### Post by domero on 2008-11-02
I had some trouble with another Ubuntu partition, so I reinstalled the OS onto another partition then transferred everything over.

I'm now wanting to remove the other, now useless, partition. However, I don't know which it is on gParted. I've got **/dev/sda1** and **/dev/sda2** listed. sda2 has a drop down menu listing sda6, sda7 and sda5.

which one is to be deleted?

---

### Post by aperomsik on 2008-11-02
If you open a terminal and type "df" you can see the mount points of all partitions. Hopefully that will make it clear which one is not being used... just DON'T delete the extended partition that contains  other partitions, even though it won't be listed in df output.

---

