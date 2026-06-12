---
title: "update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by JustAnotherVagueAnon on 2008-12-07
Hello, I've had problems like this before, but usually they were easier to fix.

```

bbraun@bbraun-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
bbraun@bbraun-desktop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic
dpkg: subprocess post-installation script returned error exit status 1

```

In the past, I could fix this by running Synaptic and removing old kernels, but now when I try to run it it tells me to first use "dpkg --configur -a" which won't work until I make space. How can I manually remove free space on /boot?

---

### Post by Partyboi2 on 2008-12-07
Looks like you have ran out of room, what is the output to
```
df -h
```

---

### Post by JustAnotherVagueAnon on 2008-12-07
```

bbraun@bbraun-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              75G  4.0G   67G   6% /
varrun               1004M  104K 1004M   1% /var/run
varlock              1004M     0 1004M   0% /var/lock
udev                 1004M   84K 1004M   1% /dev
devshm               1004M   24K 1004M   1% /dev/shm
lrm                  1004M   44M  960M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb2              54M   47M  4.0M  93% /boot
/dev/sda1             294G   28G  267G  10% /media/SHARED
gvfs-fuse-daemon       75G  4.0G   67G   6% /home/bbraun/.gvfs

```
Yes, I am out of room but the problem is I'm not sure how to free it up... Synaptic won't run without first fixing this problem.

---

### Post by Partyboi2 on 2008-12-08
You can open up synaptic and do a search for linux-image and remove all the ones you know longer need, I would suggest keeping your current one and the previous version as a backup kernel. Then back in a terminal[FONT=monospace]
[/FONT]```
sudo apt-get install -f
```then
```
sudo dpkg --configure -a
```Another option you have is to increase the size of your /boot partition

---

### Post by JustAnotherVagueAnon on 2008-12-09
It won't even let me run Synaptic :(
It gives me
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```
and then closes right away. I can't just use rm in the terminal, can I? What is the best way to remove old kernels from the terminal?

is it safe for me to move certain contents of /boot somewhere else, run synaptic, and then replace whatever I had moved?

---

### Post by Partyboi2 on 2008-12-10
To remove old kernels from the terminal you would type (replacing the * with the correct numbers)
```
sudo apt-get remove linux-image-2.6.**-*-generic
```
I am not sure what would happen if you were to move things out of /boot but I would say you could run into problems.
You could always use gparted to increase the size of your boot partition by another 50 mb and then rerun 
```
sudo dpkg --configure -a
``` Then if that is successful remove your old kernels you know longer use and either keep the increase size of /boot partition or resize again back to its previous size.

---

### Post by rogers320 on 2009-11-14
Resolved on my Ubuntu 9.10 amd64.  It looks I or Computer Janitor deleted old/customized kernels in /boot and /lib/modules folders.  However, there're state files left in /var/lib/initramfs-tools/ that mislead update-initramfs.  So I do the following steps:

1, Delete only broken files in /var/lib/initramfs-tools/.  (Be careful)
2, sudo dpkg --configure -a
3, sudo dpkg --configure initramfs-tools  (make sure no errors, otherwise repeat step 1 & 2).
4, sudo update-initramfs -u  (Maybe not neccessary).

Hope this helps.

---

### Post by Contrast on 2009-12-15
Big thanks for sharing this vital information, rogers320. A few days ago, I had built and installed (and subsequently removed) a stock kernel in a vain attempt to resolve a suspend/resume issue I'm having. Apparently, when I removed it, just enough got left behind to throw initramfs for a loop when it was trying to update, preventing me from doing any package management tasks. Your post just saved me from a reinstall, so again, thank you. :)

---

### Post by H_a_D_3_z on 2010-01-28
Hey thanks Rogers, I just deleted everything in the initramfs file. I got an error when I processed #3 and didn't even make it to #4.  But, it updates now. :popcorn::popcorn:

---

### Post by Helix7 on 2010-03-19
YES! THANKS Alot This thread helped me out...

---

