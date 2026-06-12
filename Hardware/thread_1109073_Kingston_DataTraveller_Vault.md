---
title: "Kingston DataTraveller Vault"
date: 2009-03-28
forum: Hardware
---

### Post by daoud7 on 2009-03-28
Has anyone solved the problem of accessing this encrypted memory stick?

If not, does anyone know how it can be configured to use with Ubuntu?

And no, I didn't buy it. It was a present! :(

---

### Post by cellison on 2009-04-06
I'm having the exact same problem. It turns out that the DTSP Launcher partition is being read as a CD, which is stopping me from formatting it.

Is there some sort of workaround so I can get my drive to stop failing?

I'm in Windows right now so I can't print outputs, but when I get in there I'll do so.

I'm running on Ubuntu Hardy.

Thank you.

---

### Post by abn91c on 2009-04-06
on mine i formated in windows to use in kubuntu

---

### Post by cellison on 2009-04-07
It allowed me to format the second partition that shows up after you login through the ISO 9660 but not the latter. Is there any way to trick my computer into recognizing it's a hard disk so I can format it using gparted?

---

### Post by abn91c on 2009-04-07
> **cellison said:**
> It allowed me to format the second partition that shows up after you login through the ISO 9660 but not the latter. Is there any way to trick my computer into recognizing it's a hard disk so I can format it using gparted?
if you  dont want the drive security just delete the included program then format in windows to get the full space

---

### Post by cellison on 2009-04-07
How does one do that?

---

### Post by cellison on 2009-04-08
so here's some output from running df -h:

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 248M   18M  231M   7% /lib/modules/2.6.24-23-generic/volatile
tmpfs                 248M   18M  231M   7% /lib/modules/2.6.24-23-generic/volatile
varrun                248M  100K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   72K  248M   1% /dev
devshm                248M   12K  248M   1% /dev/shm
tmpfs                 248M   16K  248M   1% /tmp
gvfs-fuse-daemon      248M   27M  222M  11% /home/ubuntu/.gvfs
/dev/scd1             6.7M  6.7M     0 100% /media/DTSP Launcher
/dev/sdc1             466G  183G  284G  40% /media/My Book

where /dev/scd1 is the cdfs partition which is read-only (I tried deleting the files and formating the drive in windows but it would only format the secondary portion). I can access the secondary portion after logging into the secure portion in windows but wine won't run the launcher, so I can't do it in ubuntu and it won't let me access the secondary partition...

Thank you for taking the time to read this.

---

