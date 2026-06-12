---
title: "Periodic Hangs"
date: 2005-12-02
forum: General Help
---

### Post by Stormspace on 2005-12-02
Ubuntu hangs every few seconds. For instance if I'm typing an e-mail the machine will suddenly go unresponsive for about 10-15 seconds and then if I had kept typing the buffer will spit out all the text I typed during the hang. Is there any way to see what's causing this or does someone here have an idea?

---

### Post by MarcoL on 2005-12-02
The gnome-system-monitor gives infos about CPU usage and programs loaded in memory.

---

### Post by arctic on 2005-12-02
sounds like a DMA problem with your harddisk. Check if you find any error messages for accessing the harddsik in your /var/log/messages file. (beware, it is huge most times). If you find any indications of a DMA timeout, try the following:

open a terminal and launch:
sudo hdparm -d0 /dev/hda

If you harddrive is not hda, then replace it respectively with hdb, hdc, hdd, whatever you use. 
The hdparm comamnd will disable DMA on your harddisk for now. Now check if your system still has these hickups. If not, you know where the problem lies. If you still encounter hiccups, check if e.g. your RAM is bad with Memtest86 (Live cds like Knoppix have a Memtest feature).

---

