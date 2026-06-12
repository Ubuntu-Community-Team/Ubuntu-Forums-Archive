---
title: "[SOLVED] Home drive has 0 free bytes"
date: 2008-08-12
forum: General Help
---

### Post by sipickles on 2008-08-12
Hi,

I have not used my Ubuntu partition for a few weeks and now it seems to have a problem.

I cannot write to my home drive, a seperate partition. I get error messages saying I have zero bytes available, when there are about 400MBs free (according to GParted).

This also means I can't open Firefox or Thunderbird, since I cant write to the home folder....

Here's some data I copied from the machine, as you can see, creating a file as root works, so it must be a permissions problem.

```
simon@simon-linux:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             6.0G  5.6G   27M 100% /
varrun               1014M  228K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M   80K 1014M   1% /proc/bus/usb
udev                 1014M   80K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda8              22G   22G     0 100% /home
/dev/sda5              23G   19G  4.0G  83% /media/PROJECTS
gvfs-fuse-daemon      6.0G  5.6G   27M 100% /home/simon/.gvfs
/dev/sdb1             481M   92M  389M  20% /media/UDISK25X

simon@simon-linux:~$ df -h >> /home/simon/test.txt
df: write error: No space left on device

simon@simon-linux:~$ sudo df -h >> /home/simon/test.txt
[sudo] password for simon: 
simon@simon-linux:~$ 

```

/dev/sda8 has 395MB free in GParted

I checked the properties of the home folder and I have read and write access for folders. For files, there was no entry so I changed that to read and write, applied to all subfolders, but no change.

Please help! My Ubuntu box is just a brick like this! :)

Thanks

-----

EDIT I tried gksudo nautilus and changed the folder and file permissions there. No effect.

Is it normal for the File entry of the permissions to always show "---" when opened?

---

### Post by lisati on 2008-08-12
Do the following help?
```
sudo apt-get clean
```
```
sudo apt-get autoclean
```

---

### Post by sipickles on 2008-08-12
Thanks for the reply, but those commands have no effect.

I don't think my Home drive is actually full, and GParted agrees. Just for some reason, my user cannot write to it.

---

### Post by lisati on 2008-08-12
Short of finding a way to enlarge the partition/free up space, I'm kinda stuck for suggestions.

Anyone else?

---

### Post by sipickles on 2008-08-12
I thought clean installs were part of Windows World, but I am rapidly heading for one!

;)

---

### Post by sipickles on 2008-08-12
OK, so Ubuntu differs from windows in this repect. As the disk fills upin windows you can keep going, slowly grinding to a halt.

In ubuntu, it just locks you out when there are only a few % of the disk free.

A quick clean up and emptying the trash has cured it.

So simple! lol

---

