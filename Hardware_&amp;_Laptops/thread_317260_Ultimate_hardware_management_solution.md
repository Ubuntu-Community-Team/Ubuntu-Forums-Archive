---
title: "Ultimate hardware management solution"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by sjunaidn on 2006-12-12
Hi All,


I am looking for a hardware management tool which can give me all the information about all the hardware attached to my machine.

I am particularly interested in knowing about a tool which can give me all the info about hard disks attached to my machine.

Hard disks that are mounted as well as those that are not mounted and are not formatted with a file system.

It should also show which partitition is mapped to which logical mount point ( I know about /etc/fstab) and so on.

Looking for good replies.

---

### Post by 5-HT on 2006-12-12
> **sjunaidn said:**
> 
I am particularly interested in knowing about... 
* fdisk *and *mount* are your friends. Please read their man pages for more information.
With respect to an 'ultimate HW management solution', sorry but you'll need to look at different apps depending on what you want to find out.

---

### Post by sjunaidn on 2006-12-12
what about the rest of hardware?

fdisk and mount are stroage related commands.

---

### Post by 5-HT on 2006-12-12
> **sjunaidn said:**
> what about the rest of hardware? 
As I mentioned, the needed commands depend on what information you are looking for. Is there anything you want specifically? 
If you're just looking for a list of detected hardware, *lspci* and *lshw *would be worth looking into.

HTH

---

### Post by houstonbofh on 2006-12-12
'sudo lshw' comes to mind.

---

### Post by kpkeerthi on 2006-12-12
Or 'ls /proc' and 'cat' the files

---

### Post by technodigifreak on 2006-12-12
> **houstonbofh said:**
> 'sudo lshw' comes to mind.

> **kpkeerthi said:**
> Or 'ls /proc' and 'cat' the files

You can simply output the info to a file and then save it to your documentation store. 

```
sudo lshw > $(hostname)-$(date +%Y%m%d).txt
```

This will create a file with the machine's hostname and the date that the command was run.  For example on 'machineX' for today's date, the file would look like 'machineX-20061212.txt' very useful for machines that are used for testing and their hardware may be changed on a constant basis.  Perfect for copying and pasting into your wiki!

---

