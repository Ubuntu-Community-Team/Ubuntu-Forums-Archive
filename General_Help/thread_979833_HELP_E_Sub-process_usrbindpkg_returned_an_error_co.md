---
title: "HELP: E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2008-11-12
forum: General Help
---

### Post by abh83 on 2008-11-12
When installing new updates I get this error message every single time. I recall first seeing this message when I installed wine. I was presented with the error message right after the installation process had finished.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up winbind (2:3.2.3-1ubuntu3) ...
 * Starting the Winbind daemon winbind                                   [fail] 
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried several solutions with no luck.

```
sudo dpkg --configure -a
```

or

```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/gxine.list
```


Help is greatly appreciated!

---

### Post by Ryadt on 2008-11-12
Can you post the output of ```
df -Th
```

---

### Post by abh83 on 2008-11-12
Sure. There you go!

```
:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    108G   13G   90G  13% /
tmpfs        tmpfs    504M     0  504M   0% /lib/init/rw
varrun       tmpfs    504M   92K  504M   1% /var/run
varlock      tmpfs    504M     0  504M   0% /var/lock
udev         tmpfs    504M  2.8M  502M   1% /dev
tmpfs        tmpfs    504M  424K  504M   1% /dev/shm
lrm          tmpfs    504M  2.0M  502M   1% /lib/modules/2.6.27-7-generic/volatile

```

---

### Post by Ryadt on 2008-11-12
There is a bug report about this in launchpad. You may want to confirm it.
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/288496](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/288496)

---

