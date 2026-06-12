---
title: "&quot;No space left on device&quot;"
date: 2008-11-15
forum: General Help
---

### Post by enderal on 2008-11-15
Getting the message "No space left on device" from a number of places. I did empty the trash. I seem to have plenty of space left.

Thank you for help.

---

### Post by taurus on 2008-11-15
Can you post the output of this command from a terminal?

```
df -h
```

---

### Post by enderal on 2008-11-15
Yes thanks taurus

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   13G     0 100% /
varrun               1001M  112K 1001M   1% /var/run
varlock              1001M     0 1001M   0% /var/lock
udev                 1001M   40K 1001M   1% /dev
devshm               1001M     0 1001M   0% /dev/shm
lrm                  1001M   39M  962M   4% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M   36K  988K   4% /tmp

---

### Post by taurus on 2008-11-15
> **enderal said:**
> Yes thanks taurus

Filesystem            Size  Used Avail Use% Mounted on
[B][COLOR="Blue"]/host/ubuntu/disks/root.disk
                       13G   13G     0 100% /[/COLOR][/B]
varrun               1001M  112K 1001M   1% /var/run
varlock              1001M     0 1001M   0% /var/lock
udev                 1001M   40K 1001M   1% /dev
devshm               1001M     0 1001M   0% /dev/shm
lrm                  1001M   39M  962M   4% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M   36K  988K   4% /tmp

Well, you max out your / filesystem so no space left.  When you said you empty trash, did you actually delete the files in there?  Also, check your /tmp, /var (and /var/backups) to make sure there are no large files in there, eating up your disk space.

```
sudo du -h /tmp
sudo du -h /var
```

---

### Post by cdtech on 2008-11-15
What flavor are you running?

---

### Post by enderal on 2008-11-15
What types of files can I delete out of /var (and /var/backups)?

I did find a couple gigs I had saved before making a full ubuntu backup to disk and did not delete but it is still saying full. Maybe I should reboot.

I'm running ubuntu Hardy Heron 8.04.

---

### Post by taurus on 2008-11-15
You can delete stuff in /var/backups.  And for /var/log, you can delete all the files that end with .gz because those are just backup files of your logs.  You can also clean out the cache.

```
sudo apt-get clean
df -h
```

---

### Post by cdtech on 2008-11-16
Looks like a virtual disk via Wubi. If you want to resize the virtual disk try this procedure:
[https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?](https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?)

---

