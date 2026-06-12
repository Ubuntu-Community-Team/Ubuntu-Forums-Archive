---
title: "Trouble with mdadm: Two drives improper for a raid 0 or a raid 1?"
date: 2013-03-24
forum: Hardware
---

### Post by Shammai on 2013-03-24
Full terminal output:
[http://paste.ubuntu.com/5644957/](http://paste.ubuntu.com/5644957/)
[HR][/HR]Briefly:
ubuntu@ubuntu:~$ sudo mdadm -C /dev/md0-v -n=2 -l=0 /dev/sd[ab]2 
mdadm: invalid number of raid devices: =2 

The same happens for level 1 raid. Is there something I am missing here? Does linux software raid for levels 1 and 0 only work with 3 drives?

Thanks in advance.

---

### Post by Shammai on 2013-03-24
Hmmm, it appears that I was using obsolete syntax. After writing the code out long form, it seems to work now:
# mdadm --create /dev/md0 --level=1 --raid-devices=2  /dev/sdc1 /dev/sdd1

you can close this thread and call it solved

---

### Post by steeldriver on 2013-03-24
I think the single letter command line switches don't want the = signs before the arguments


```
 sudo mdadm -C /dev/md0 -v **-n 2** **-l 0** /dev/sd[ab]2
```

The = is only when you're using the long forms e.g.

```
 sudo mdadm --create /dev/md0 --verbose **--raid-devices=2** **--level=0** /dev/sd[ab]2
```

see [http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/](http://www.ducea.com/2009/03/08/mdadm-cheat-sheet/)

---

