---
title: "Unable to configure xserver-xorg"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by pumrel on 2009-10-29
Looks like I wasn't careful enough when upgrading to Karmic and now I am stuck with unconfigured and unfunctional xserver 

```
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ cd /mnt                  
ubuntu@ubuntu:/mnt$ sudo chroot /mnt
root@ubuntu:/# dpkg --configure -a
Setting up xserver-xorg (1:7.4+3ubuntu7) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused                                                        
invoke-rc.d: initscript hal, action "restart" failed.                           
dpkg: error processing xserver-xorg (--configure):                              
 subprocess installed post-installation script returned error exit status 1     
dpkg: dependency problems prevent configuration of xorg:                        
 xorg depends on xserver-xorg; however:                                         
  Package xserver-xorg is not configured yet.                                   
dpkg: error processing xorg (--configure):                                      
 dependency problems - leaving unconfigured                                     
dpkg: dependency problems prevent configuration of kubuntu-desktop:             
 kubuntu-desktop depends on xorg; however:                                      
  Package xorg is not configured yet.                                           
dpkg: error processing kubuntu-desktop (--configure):                           
 dependency problems - leaving unconfigured                                     
Errors were encountered while processing:                                       
 xserver-xorg                                                                   
 xorg
 kubuntu-desktop
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up xserver-xorg (1:7.4+3ubuntu7) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
invoke-rc.d: initscript hal, action "restart" failed.
dpkg: error processing xserver-xorg (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg; however:
  Package xserver-xorg is not configured yet.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 xserver-xorg
 xorg
 kubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/#

```

I had a similar problem with the new linux kernel having dependency problems as well, but I have managed to solve with the help of this forum, but now I'm completely lost and cannot find any help.
Don't you have any idea how to continue pls?:(

---

### Post by collinp on 2009-10-29
This should fix it:
```
sudo dpkg --configure -a
```From what I can tell, you have some unconfigured packages. That command should fix it, unless there is other problems.

---

### Post by pumrel on 2009-10-30
Thank you for the prompt reply. ;) Unfortunately, it returned the exact same error

```
root@ubuntu:/# dpkg --configure -a
Setting up xserver-xorg (1:7.4+3ubuntu7) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
invoke-rc.d: initscript hal, action "restart" failed.
dpkg: error processing xserver-xorg (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg; however:
  Package xserver-xorg is not configured yet.
dpkg: error processing xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on xorg; however:
  Package xorg is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xserver-xorg
 xorg
 kubuntu-desktop
root@ubuntu:/#

```

---

### Post by macogw on 2009-10-30
It says you need to configure them in this order:
xserver-xorg
xorg
kubuntu-desktop

So try doing ```
sudo dpkg --configure xserver-xorg
``` or maybe ```
sudo dpkg-reconfigure xserver-xorg
``` first.

---

### Post by moycano on 2009-10-30
GUYS!! I'm so glad I finally found another one with a similar problem (because I didn't even know how to express it myself):
**Could anyone point us to more documentation about the xserver reconfiguration?**

Is the third time under different flavor of Ubuntu 9.10 that I try-and-fail to login after a "successfully installation". I only get text-only terminals (tt1-6 I think) even when the live sessions were working without any problems.

---

### Post by zero4281 on 2009-10-30
THe key piece is:
  ```
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
```

Are you guys working in a VM or a chroot?  I am and I get the same error.  I found some mention of it here:
 [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224/comments/6](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430224/comments/6)
and here:
 [https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot](https://wiki.ubuntu.com/KarmicKoala/ReleaseNotes#Upstart%20jobs%20cannot%20be%20run%20in%20a%20chroot)

---

### Post by pumrel on 2009-10-31
Well, it finally works. Looks I was doing a great mistake working in chroot. I needed log in to Tty and the type ```
sudo dpkg --configure -a

``` and it worked.

But then I needed to restore my old xorg.conf, because without it it would't show my desktop.

---

