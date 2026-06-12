---
title: "Failure of Root Auth"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by lotusalive on 2009-09-23
Hi All: I configured my NTFS partition last night with System>Admin>NTFS 

Configuration Tool, and for some reason it showed up as an icon on my 

desktop.  I must have made an incorrect choice, since I have lost all 

root access to my system.

sol@sol-desktop:~$ -|.Xauthority
bash: -: command not found
bash: .Xauthority: command not found
sol@sol-desktop:~$

and

sol@sol-desktop:~$ su root
Password: 
su: Authentication failure
sol@sol-desktop:~$

and yet, command: sudo synaptic worked the first time, and successfully removed a package.  

On second try of sudo synaptic, 
Error messages are:

E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Is it possible that I unmounted my root partition, and mounted the NTFS partition in place of it ?  Is it possible to recover?  I'm afraid to reboot at this point...  All information appreciated.:confused:


A look at gparted (by sudo /usr/sbin/gparted, with Error: Input/Output error 

during read on /dev/sdc) shows NTFS mounted as /media/NTFS, and / is actually 

full at 54.99 GiB...  There is plenty of room in the home partition to resize, 

but that option is not offered me without root access.  Anything else I can do ?

(Am uninstalling two large programs from /, currently.)

---

### Post by lotusalive on 2009-09-23
Will anyone tell me what this means ?  Does it mean nothing is removed ?

sol@sol-desktop:~$ sudo apt-get autoremove wine
[sudo] password for sol: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdesdk-kio-plugins umbrello valgrind lokalize libkrosspython0 kbugbuster
  kcachegrind poxml kompare kdesdk-misc kate kdesdk-strigi-plugins
  kdesdk-scripts graphviz kuiviewer
The following packages will be REMOVED:
  graphviz kate kbugbuster kcachegrind kdesdk-kio-plugins kdesdk-misc
  kdesdk-scripts kdesdk-strigi-plugins kompare kuiviewer libkrosspython0
  lokalize poxml umbrello valgrind wine
0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
After this operation, 137MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 286617 files and directories currently installed.)
Removing graphviz ...
Removing kate ...
Removing kbugbuster ...
Removing kcachegrind ...
Removing kdesdk-kio-plugins ...
Removing kdesdk-misc ...
Removing kdesdk-scripts ...
Removing kdesdk-strigi-plugins ...
Removing kompare ...
Removing kuiviewer ...
Removing libkrosspython0 ...
Removing lokalize ...
Removing poxml ...
Removing umbrello ...
Removing valgrind ...
Removing wine ...
Processing triggers for menu ...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/fsstnd/31251: No space left on device
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
sol@sol-desktop:~$

---

### Post by lotusalive on 2009-09-23
I have uninstalled wine and all its connected programs, but that still has

not diminish the / partition from 54.99 GiB... ?

But I do have the capability to obtain / prompt in terminal, I just found out with:

sol@sol-desktop:~$ sudo su
root@sol-desktop:/home/sol# -|.Xauthority
bash: -: command not found
bash: .Xauthority: command not found
root@sol-desktop:/home/sol# /usr/sbin/gparted

Will someone please direct me to the correct command in root that will return my Xauthorization ?:confused:

---

### Post by lotusalive on 2009-09-26
After repartitioning with Live Disk, the only failures are:

a) Open Office still misbehaves with documents saved from internet cut 

and paste, that fail to retrieve, even one that wasn't from the net, that 

I spent over 8 hours working on as a 4-sided brochure, and did TWICE, 

since the first Save took out half the document...


AND:  

b)  My old trash will NOT EMPTY, nor will it put anything in it back on 

the desktop top alone so it can be removed that way...  It only makes 

another copy !


Where do I go for 'Trash' help ? ! LOL :)

---

### Post by rreese6 on 2009-09-26
I am not sure anyone that is online right now wants to touch this one.
I would, except I have no experience with the NTFS Function you used.
Plus I am not even sure what it is that you did.
I guess to made an NTFS partition, and most likely wiped out part of you Linux system...I still don't know why you need to run a Windows File System ... Linux can read and right to ntfs but it doesn't use it.
Since I am not really sure of why or how you did this, I might suggest, that you backup you files in your home folder and do a fresh install.
Hopefully Someone that has made you same mistake will read this post and help you out.

---

