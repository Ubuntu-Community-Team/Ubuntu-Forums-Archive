---
title: "apt-get errors in Hardy"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by lesswatts on 2009-10-06
I am having a problem with my remote Hardy box when running apt-get:

```
aaron@aeichler:/var/lib/dpkg$ sudo apt-get install bmon                         
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
The following NEW packages will be installed:                                   
  bmon                                                                          
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.                  
Need to get 43.6kB of archives.                                                 
After this operation, 184kB of additional disk space will be used.              
Get:1 http://my.archive.ubuntu.com hardy/universe bmon 2.0.1-3 [43.6kB]         
Fetched 43.6kB in 1s (34.8kB/s)                                                 
Can't ignore signal CHLD, forcing to default.                                   
E: Waited for /usr/sbin/dpkg-preconfigure --apt || true but it wasn't there     
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true             
aaron@aeichler:/var/lib/dpkg$ 

```Also when running apt-get update I get errors like this:
```
Err http://security.ubuntu.com hardy-security/main Sources                      
  Waited for bzip2 but it wasn't there
```After some digging, I found it could be related to perl, but not sure where to go with that.

```
aaron@aeichler:/var/lib/dpkg$ perl -w                                           
Can't ignore signal CHLD, forcing to default. 
```Anyone have any hints that could point me in the right direction?

---

