---
title: "i cant remove any program because of &quot;bandwidthd&quot;"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by M_JaGuar on 2009-06-13
hi

i installed a programe called "bandwidthd"
and now i want to remove it but i cant and i cant remove any other 
program because of it i tryed (add/remove) , synaptic and from the terminal
i cant remove it and it give me this error :

> E: /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb: subprocess new pre-removal script returned error exit status 2

if i want to remove any program

---

### Post by zvacet on 2009-06-13
```
sudo apt-get --purge remove bandwidthd
```

or 

```
sudo dpkg --remove --force-remove-reinstreq bandwidthd
```

---

### Post by M_JaGuar on 2009-06-13
thanks for replying 

ok , the first comanned 

> sudo apt-get --purge remove bandwidthd

it fails and this is the output : 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bandwidthd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing bandwidthd (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd


and the second one also did not work this is the out put :

> dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 172342 files and directories currently installed.)
Removing bandwidthd ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing bandwidthd (--remove):
 subprocess pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB style header
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 bandwidthd


and i reinstall the program then tryed to remove it did not work ether :(

---

### Post by M_JaGuar on 2009-06-14
up ... please help !!

---

### Post by M_JaGuar on 2009-06-17
up up

---

### Post by cariboo on 2009-06-17
I would suggest you stop the service first, before trying to uninstall it. Try in a terminal:

```
sudo /etc/init.d/bandwidthd stop
```

THen go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages.

Once you have gone through the above steps, you should be able to install new packages.

---

### Post by M_JaGuar on 2009-06-17
no it is not working 

this is the output for the command :

> /etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected

---

### Post by stalkerh on 2009-11-12
Follow the steps in this post [http://ubuntuforums.org/showthread.php?t=455541](http://ubuntuforums.org/showthread.php?t=455541) , go straight to post 4. When searching in the file just search for bandwidthd instead of the example given there.

Hope it helps , solved the problem for me

---

