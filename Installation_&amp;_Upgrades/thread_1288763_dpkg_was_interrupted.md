---
title: "dpkg was interrupted"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by tedegordon on 2009-10-11
I'm running Ubuntu Studio 9.04.  I tried to install Open Office and the computer froze:

When I tried to reinstall, I got the following error message: 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

I've looked for fixes on the web and have tried the command above as well as several apt-get commands like apt-get -f install.  I have been unable to fix the problem.  

When I run sudo dpkg --configure -a I get the following output:

Setting up openoffice.org-writer2latex (0.5-8 ubuntu1)
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...

The computer then freezes solid.   

I have been unable to run any installer, update manager, or package manager without getting this error message.

Thanks in advance for help.
Ted

---

### Post by mac9416 on 2009-10-11
I'm just shooting in the dark, but this has worked for others:

```
$ sudo dpkg --configure -a
$ sudo apt-get -f install
$ sudo apt-get --fix-missing install
```

Please post the output of those commands. Good luck!

---

### Post by rreese6 on 2009-10-11
A shot in the dark:

Is your hardrive full?
Did you possibly not partition enough space for Ubuntu in a Dual Boot Scenario? 

try this command in Terminal to see if you have a space issue...if you don't understand the output, copy it and post it here.

```
df -a
```

---

### Post by tedegordon on 2009-10-13
Thanks for your replies.

```
tgordon@ubuntu1:~$ sudo apt-get -f install
[sudo] password for tgordon: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

tgordon@ubuntu1:~$ sudo apt-get --fix-missing install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

tgordon@ubuntu1:~$ sudo dpkg --configure -a
[sudo] password for tgordon: 
Setting up openoffice.org-writer2latex (0.5-8 ubuntu1)
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...
```Then the computer freezes.  Although the suggestion was to run the dpkg command first, I can't do that because the computer always freezes when I do.


Output from df -a:

```
tgordon@ubuntu1:~$ df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            230693168   4382720 214591836   3% /
tmpfs                  1669092         0   1669092   0% /lib/init/rw
proc                         0         0         0   -  /proc
sysfs                        0         0         0   -  /sys
varrun                 1669092        96   1668996   1% /var/run
varlock                1669092         0   1669092   0% /var/lock
udev                   1669092       156   1668936   1% /dev
tmpfs                  1669092     65608   1603484   4% /dev/shm
devpts                       0         0         0   -  /dev/pts
fusectl                      0         0         0   -  /sys/fs/fuse/connections
lrm                    1669092      2400   1666692   1% /lib/modules/2.6.28-3-rt/volatile
/dev/sdb1            240362656   1828808 226324048   1% /home
securityfs                   0         0         0   -  /sys/kernel/security
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon             0         0         0   -  /home/tgordon/.gvfs
```

I have plenty of space.

Is there some dpkg command that will clean up or reverse the process I started and can't finish?  I have tried a few, for example trying to remove the openoffice.org package, but that didn't do the job.

Thanks again.

---

### Post by rreese6 on 2009-10-13
ok you have tons of room on the HD..

Boot in recovery mode and choose "Fix Broken Packages"

then from the console, run dpkg --configure -a

---

### Post by tedegordon on 2009-10-14
Thank you - working from the recovery mode console changed the behavior a little, but ultimately the problem remains.  Now the message from dpkg is slightly different, but no package or update manager can get past the freezing behavior.  There seem to be some broken packages that, when I try to fix them, just break the fix process itself.  I've worked with various LInux distributions for several years, and I have never run into this kind of behavior before. 

Thanks again,
Ted

---

### Post by sousana on 2009-10-20
hi ted,
i have the same problem, it could be a bug in real-time kernel according to [bug 368570]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/368570") i haven't tried the solution yet: to try installing openoffice with generic kernel; i also don't know how to get a generic kernel with broken synaptic...

---

