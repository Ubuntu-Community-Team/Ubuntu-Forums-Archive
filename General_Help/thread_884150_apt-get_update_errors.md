---
title: "apt-get update errors"
date: 2008-08-08
forum: General Help
---

### Post by Forvak on 2008-08-08
Hello,

I just added the medibuntu repository using the instructions here.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Unfortunately I am now getting proxy errors on several. Also, does anyone know how to fix the fact that all Translation-en_CA ones are failing?

Thank you!
```

user@computer:~$ sudo apt-get update
Ign http://packages.medibuntu.org hardy Release.gpg
Get:1 http://archive.ubuntu.com hardy Release.gpg [191B]
Ign http://packages.medibuntu.org hardy/free Translation-en_CA                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_CA             
Ign http://packages.medibuntu.org hardy Release
Ign http://archive.ubuntu.com hardy/main Translation-en_CA
Ign http://packages.medibuntu.org hardy/free Packages    
Ign http://archive.ubuntu.com hardy/universe Translation-en_CA
Ign http://packages.medibuntu.org hardy/non-free Packages
Err http://packages.medibuntu.org hardy/free Packages    
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com hardy/restricted Translation-en_CA
Err http://packages.medibuntu.org hardy/non-free Packages
  407 Proxy Authentication Required
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_CA
Get:2 http://archive.ubuntu.com hardy-updates Release.gpg [189B]
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_CA
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_CA         
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_CA       
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_CA       
Get:3 http://archive.ubuntu.com hardy-security Release.gpg [189B]              
Ign http://archive.ubuntu.com hardy-security/main Translation-en_CA                                                                                                           
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_CA                                                                                                       
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_CA                                                                                                     
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_CA                                                                                                     
Get:4 http://archive.ubuntu.com hardy Release [65.9kB]                                                                                                                        
Get:5 http://archive.ubuntu.com hardy-updates Release [58.5kB]                                                                                                                
Get:6 http://archive.ubuntu.com hardy-security Release [58.5kB]                                                                                                               
Get:7 http://archive.ubuntu.com hardy/main Packages [1178kB]                                                                                                                  
Hit http://archive.ubuntu.com hardy/universe Packages                                                                                                                         
Get:8 http://archive.ubuntu.com hardy/restricted Packages [6986B]                                                                                                             
Get:9 http://archive.ubuntu.com hardy/multiverse Packages [179kB]                                                                                                             
Get:10 http://archive.ubuntu.com hardy-updates/main Packages [293kB]                                                                                                          
Get:11 http://archive.ubuntu.com hardy-updates/universe Packages [81.7kB]                                                                                                     
Get:12 http://archive.ubuntu.com hardy-updates/restricted Packages [6636B]                                                                                                    
Get:13 http://archive.ubuntu.com hardy-updates/multiverse Packages [16.4kB]                                                                                                   
Get:14 http://archive.ubuntu.com hardy-security/main Packages [53.8kB]                                                                                                        
Get:15 http://archive.ubuntu.com hardy-security/universe Packages [27.8kB]                                                                                                    
Get:16 http://archive.ubuntu.com hardy-security/restricted Packages [6636B]                                                                                                   
Get:17 http://archive.ubuntu.com hardy-security/multiverse Packages [8222B]                                                                                                   
Fetched 2042kB in 1min37s (20.9kB/s)                                                                                                                                          
W: Failed to fetch http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz  407 Proxy Authentication Required

W: Failed to fetch http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz  407 Proxy Authentication Required

E: Some index files failed to download, they have been ignored, or old ones used instead.



```

---

### Post by pytheas22 on 2008-08-08
In Synaptic (System>Administration menu) if you go to Settings>Preferences>Network, you can set proxy-server information.  Do that and see if it will then allow you to update the sources list by using the "Reload" button in the top-left corner of Synaptic.

I don't know whether setting the proxy settings in Synaptic will also apply the fix to apt-get when used from the command-line, but it might.  If not, take a look at this [thread]("http://ubuntuforums.org/showthread.php?p=364026").

---

### Post by Forvak on 2008-08-13
Sorry should have mentioned this, there is no proxy between me and the internet. I connect directly.

EDIT: I used to use a proxy for work, now I'm at home and no longer need it. I plugged the proxy back in and it updates without errors. I'll try removing the proxy after the updates finish.

---

### Post by TheSurak on 2009-09-27
Also, you may need to type as root:

unset http_proxy

I believe this being sort of a bug in Ubuntu, that persists untill 9.04. I've just had this problem because I used a proxy at work and couldn't update at home. Good luck.

---

