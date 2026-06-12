---
title: "HDD failure?"
date: 2017-11-21
forum: Hardware
---

### Post by aske.c on 2017-11-21
Hey my laptop HDD is about 3 years old. Sometimes then i move the laptop, it freezes and i have to restart it. I have run a SMART analyes and it says: "Disk is okay, one failing attribute is failing".

I have dual boot with windows and wont to make a clean install soon, to try new linux distribution and get less windows. 

I was wondering if my HDD needs to be replaced before i do that?

[ATTACH=CONFIG]277628[/ATTACH]

---

### Post by jaweewo on 2017-11-21
Did it freezes when you are in windows? if it is i recommend you to replace it, but maybe its not the disk, try to check the temperature and rams. Because that thing happened to me in a 12 years old laptop and it was not the HDD because i have it now in my PC, i check it and it was my motherboard. So you should check other thinks before replace it. 

Hope it helps.

---

### Post by aske.c on 2017-11-21
Thanks it happens in then im in linux. The analyse off the disk tells there is an end-to-end-error, but i dont know what that means?

---

### Post by Bashing-om on 2017-11-21
aske.c; Hello; Welcome to the forum .

> 
 Sometimes then i move the laptop, it freezes and i have to restart it. 


In this case my suggestion(s):
1. Check the system log file and see what it reports.
```

cat /var/log/syslog

```
and have a long read.

2. systemd ? Check the boot log:
```

journalctl -b -0

``` 
Again a long read .

3. Run a file system check from the liveDVD(USB):
so you know the target ID;
```

sudo parted -l

```
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s) as shown from 'parted -l' .
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```
fsck [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

Depending on what is found is what you do .

[INDENT][INDENT]all in the process[/INDENT][/INDENT]

---

