---
title: "Ubuntu thinks your laptop has a floppy"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by magicfab on 2004-12-29
I have an Averatec 3250 series laptop and it has no floppy disk, like many recent notebooks / laptops. However Ubuntu kept insisting to load the floppy module and showed a nasty " FATAL: can't insert /..../...../floppy/... module".

After a quick trip in the IRC channel, someone suggested I added the floppy module to the /etc/hotplug/blacklist file. This file lists modules that are NOT loaded at boot time. Simply adding a new line with only the word "floppy" on it did the trick.

Now I boot .00006 seconds faster too ;)

---

### Post by BillF on 2005-01-02
Hi!  I have the same problem! How did you edit the file?  I ask this because I tried to follow your instructions, however, I did not have write permission for the file or partition.  So, I am still stuck.  How do you obtain the write permission to edit the file?

Thanks,

Bill

---

### Post by roongpatoong on 2005-01-02
hey magicfab

this is all I did to get it to skip floppy loading ...

sudo echo "floppy" >> /etc/hotplug/blacklist

btw - thanks alot BillF - I have an averatec 3250 too and was searching for the floppy fix too!

had any luck with suspend?

oops - got the two posters mixed up then :)

---

### Post by magicfab on 2005-01-20
I have also noticed that if you are performing a fresh install and use "expert" instead of just pressing enter to start the process, you will get a much more detailed install process including several questions about including the floppy support.

---

