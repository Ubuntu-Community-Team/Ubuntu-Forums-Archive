---
title: "E: dpkg was interrupted - run 'dpkg --configure -a'"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by k1008536 on 2009-02-24
Hi, I ran the update manager today and got the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now I when I open open Synaptic I get the same message. I have tried running sudo dpkg --configure -a as directed but this does not fix the problem. See output from terminal below. i have also run the following commands but it does not help.

sudo apt-get update
sudo apt-get upgrade

Thanks for any help anyone may have.

james@ubuntu:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.24-23-server (2.6.24-23.37) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-server

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-23-server
dpkg: error processing linux-ubuntu-modules-2.6.24-23-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-ubuntu-modules-2.6.24-23-server; however:
  Package linux-ubuntu-modules-2.6.24-23-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.24.23.25); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-server

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-23-server
dpkg: subprocess post-installation script returned error exit status 1
james@ubuntu:~$

---

### Post by snova on 2009-02-24
Well, the "No space left on device" messages don't look particularly good...

Please post the output of:

```
df -h
```

To get some filesystem information.

---

### Post by Hobgoblin on 2009-02-25
df -i

Might also yield something useful.

---

### Post by k1008536 on 2009-02-25
Thanks guys, see below

james@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             276G  3.6G  258G   2% /
varrun                363M  108K  363M   1% /var/run
varlock               363M     0  363M   0% /var/lock
udev                  363M   56K  363M   1% /dev
devshm                363M   12K  363M   1% /dev/shm
/dev/sdb1              92M   90M     0 100% /boot
gvfs-fuse-daemon      276G  3.6G  258G   2% /home/james/.gvfs
james@ubuntu:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sdb3            18178048  182263 17995785    2% /
varrun                 92828      58   92770    1% /var/run
varlock                92828       2   92826    1% /var/lock
udev                   92828    3035   89793    4% /dev
devshm                 92828       2   92826    1% /dev/shm
/dev/sdb1              24096      59   24037    1% /boot
gvfs-fuse-daemon     18178048  182263 17995785    2% /home/james/.gvfs
james@ubuntu:~$

---

### Post by k1008536 on 2009-02-25
I see the line below output from df -h shows 100% usage but I am not sure what this means? 

/dev/sdb1              92M   90M     0 100% /boot

---

### Post by taurus on 2009-02-25
It means it cannot install a new kernel to /boot since it doesn't have any/enough space.  How many kernels do you currently have in /boot anyway?

```
ls -la /boot
```

---

### Post by k1008536 on 2009-02-25
looks like a few??

james@ubuntu:~$ ls -la /boot
total 85767
drwxr-xr-x  4 root root    3072 2009-02-26 16:08 .
drwxr-xr-x 21 root root    4096 2009-02-25 13:07 ..
-rw-r--r--  1 root root  422667 2008-08-21 16:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  426444 2008-08-21 16:50 abi-2.6.24-19-server
-rw-r--r--  1 root root  422838 2008-10-22 16:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  426615 2008-10-22 16:16 abi-2.6.24-21-server
-rw-r--r--  1 root root  422838 2009-01-26 17:30 abi-2.6.24-23-generic
-rw-r--r--  1 root root  426615 2009-01-26 17:34 abi-2.6.24-23-server
-rw-r--r--  1 root root   80049 2008-08-21 16:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80181 2008-08-21 16:50 config-2.6.24-19-server
-rw-r--r--  1 root root   80062 2008-10-22 16:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80194 2008-10-22 16:16 config-2.6.24-21-server
-rw-r--r--  1 root root   80051 2009-01-26 17:30 config-2.6.24-23-generic
-rw-r--r--  1 root root   80183 2009-01-26 17:34 config-2.6.24-23-server
drwxr-xr-x  2 root root    1024 2009-02-25 13:07 grub
-rw-r--r--  1 root root 7348740 2008-09-19 15:30 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7099322 2008-09-19 14:59 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7697659 2008-09-19 15:29 initrd.img-2.6.24-19-server
-rw-r--r--  1 root root 7085953 2008-09-19 14:03 initrd.img-2.6.24-19-server.bak
-rw-r--r--  1 root root 7349130 2008-10-31 12:22 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7698957 2008-11-12 13:39 initrd.img-2.6.24-21-server
-rw-r--r--  1 root root 7698958 2008-10-31 12:23 initrd.img-2.6.24-21-server.bak
-rw-r--r--  1 root root 7347995 2009-02-25 13:06 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7696691 2009-02-25 13:07 initrd.img-2.6.24-23-server
drwx------  2 root root   12288 2008-09-19 13:58 lost+found
-rw-r--r--  1 root root  103204 2007-09-28 22:06 memtest86+.bin
-rw-r--r--  1 root root  905170 2008-08-21 16:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  933482 2008-08-21 16:50 System.map-2.6.24-19-server
-rw-r--r--  1 root root  905617 2008-10-22 16:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  933929 2008-10-22 16:16 System.map-2.6.24-21-server
-rw-r--r--  1 root root  905809 2009-01-26 17:30 System.map-2.6.24-23-generic
-rw-r--r--  1 root root  934121 2009-01-26 17:34 System.map-2.6.24-23-server
-rw-r--r--  1 root root 1921464 2008-08-21 16:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1987480 2008-08-21 16:50 vmlinuz-2.6.24-19-server
-rw-r--r--  1 root root 1920760 2008-10-22 16:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1988408 2008-10-22 16:16 vmlinuz-2.6.24-21-server
-rw-r--r--  1 root root 1922904 2009-01-26 17:30 vmlinuz-2.6.24-23-generic
-rw-r--r--  1 root root 1989368 2009-01-26 17:34 vmlinuz-2.6.24-23-server
james@ubuntu:~$

---

### Post by taurus on 2009-02-25
Which kernel are you running right now, generic or server?  If you are running the server kernel, perhaps it's time to remove the generic ones (vice versa) to create some space on /boot.  Also, remove the *.bak since they are just a backup copies.

```
uname -a
```

---

### Post by k1008536 on 2009-02-25
james@ubuntu:~$ uname -a
Linux ubuntu 2.6.24-23-server #1 SMP Mon Jan 26 00:55:21 UTC 2009 i686 GNU/Linux
james@ubuntu:~$ 

I have removed the *.bak files, is there a quick way to remove the generic kernel files? Also do i need the older files, pre 2.6.24-23? Is this build up in /boot normal? Cheers

---

### Post by taurus on 2009-02-25
Even thought you are running the server kernel, you have window manager because you use update manager.  Therefore, the easiest way is to go into synaptic and Search for linux-image-2.6.24-23-generic.  Then, remove those versions since you are not using the generic kernels, only the server ones.

That should free up some space on /boot to update your machine.
```
df -h
```

---

### Post by k1008536 on 2009-02-25
Thanks for the help taurus :), the dpkg --configure -a worked and all seems OK. Do I need to close this thread / mark it as solved etc?

---

### Post by taurus on 2009-02-25
You can edit the title of this thread and add the word **(SOLVED)** at the end.

---

### Post by snova on 2009-02-25
> **k1008536 said:**
> Thanks for the help taurus :), the dpkg --configure -a worked and all seems OK. Do I need to close this thread / mark it as solved etc?

Only a moderator can close a thread, and Solved was disabled a while back (see [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)).

---

### Post by k1008536 on 2009-02-25
Cheers everyone!

---

