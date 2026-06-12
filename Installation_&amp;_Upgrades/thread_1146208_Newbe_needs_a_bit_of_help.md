---
title: "Newbe needs a bit of help"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by free_hat on 2009-05-02
Ok, im pretty new to ubuntu so I fired it up today (9.04) and it worked great.  I did the install on the XP partition.

Problem is, now its saying it need to install updates, but when it tries to it runs out of space (?).  Ive got aroung 100gb free, and im sure it put ubuntu on the same partition as xp.  Im guessing it maybe created a small partition for 9.04?

Any idea how to fix this?

Ps. go easy on me, im new to unix!

Thanks!

---

### Post by rdmike on 2009-05-02
I had Vista Home Premium on my new desktop PC and wanted to do the same thing with 9.04. After the initial set up I had the same problem even though there was 320GB of free space for Ubuntu to set up in. I just went ahead and reinstalled using the whole disk but that may not be a workable solution for you.

---

### Post by Kareeser on 2009-05-02
> **free_hat said:**
> Ok, im pretty new to ubuntu so I fired it up today (9.04) and it worked great.  I did the install on the XP partition.

Ubuntu won't install on the same partition as a Windows install. Multiple operating systems just don't co-exist peacefully.

What likely happened is that you resized your Windows partition, but it wasn't big enough to contain your Ubuntu install with updates.

Let's take a look at your Ubuntu partition, shall we?

Click "Applications -> Accessories -> Terminal", and when that comes up, type in "df -h" (without the quotes).

Paste the output here (use "Ctrl-Shift-C" to copy from the terminal)

---

### Post by free_hat on 2009-05-02
thanks for the quick replies!

here u go:

ikklehummer@ikklehummer-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G   19M 100% /
tmpfs                 496M     0  496M   0% /lib/init/rw
varrun                496M  144K  496M   1% /var/run
varlock               496M     0  496M   0% /var/lock
udev                  496M  152K  496M   1% /dev
tmpfs                 496M  160K  496M   1% /dev/shm
lrm                   496M  2.4M  494M   1% /lib/modules/2.6.28-11-generic/volatile
ikklehummer@ikklehummer-laptop:~$

---

### Post by free_hat on 2009-05-02
ok, more readable:

[FONT="Courier New"]ikklehummer@ikklehummer-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G   19M 100% /
tmpfs                 496M     0  496M   0% /lib/init/rw
varrun                496M  144K  496M   1% /var/run
varlock               496M     0  496M   0% /var/lock
udev                  496M  152K  496M   1% /dev
tmpfs                 496M  160K  496M   1% /dev/shm
lrm                   496M  2.4M  494M   1% /lib/modules/2.6.28-11-generic/volatile
ikklehummer@ikklehummer-laptop:~$ 
[/FONT]

---

### Post by Keith Hedger on 2009-05-02
First backup all important data, just in case!

Defrag your windows partition (from windows), boot into a live CD,run gparted, should be in System->Administration, shrink your windows partition and expand your linux partition (go and have meal while you wait!) then reboot and you should be OK.

---

### Post by Kareeser on 2009-05-02
+1 for Keith's advice.

Again, we can't stress this importantly enough, **BACK UP YOUR IMPORTANT DATA** before you begin, on both partitions!

GParted is front end to parted, a very low-level program (which means it interacts directly with the hardware). Proceed with caution.

---

