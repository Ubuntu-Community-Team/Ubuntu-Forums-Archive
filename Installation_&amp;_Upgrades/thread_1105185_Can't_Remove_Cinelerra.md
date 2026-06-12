---
title: "Can't Remove Cinelerra"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by kut77less on 2009-03-24
When I try to remove this program I get error 

> E: cinelerracv: subprocess post-removal script returned error exit status 1

 When I click more detail it says when it is trying to remove no such file exist, or something like that

---

### Post by Partyboi2 on 2009-03-25
hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to 
```
sudo apt-get remove cinelerra
```

---

### Post by kut77less on 2009-03-25
> > **Partyboi2 said:**
> hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to 
```
sudo apt-get remove cinelerra
```
  

I did it and I get the following 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cinelerra is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libmlt-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cinelerracv (2.1.1-git20090201akirad3) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: error processing cinelerracv (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 cinelerracv
E: Sub-process /usr/bin/dpkg returned an error code (1)



Do you have any Ideas. Thanks for all your help

---

### Post by Partyboi2 on 2009-03-25
In a terminal try reconfiguring the locales and see if it completes without any problems.
```
sudo dpkg-reconfigure locales
```

---

### Post by kut77less on 2009-04-18
> **Partyboi2 said:**
> In a terminal try reconfiguring the locales and see if it completes without any problems.
```
sudo dpkg-reconfigure locales
```

Sorry for talking so long. I reinstalled Ubuntu but soon go the same Problem. This is what I got 



> en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... cannot open locale definition file `da_DK': No such file or directory
failed
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... cannot open locale definition file `hi_IN': No such file or directory
failed
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date


---

