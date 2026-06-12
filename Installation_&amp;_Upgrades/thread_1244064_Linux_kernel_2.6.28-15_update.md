---
title: "Linux kernel 2.6.28-15 update"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by Riaku on 2009-08-19
I just updated my kernel image and now I;m gettin a kernel update that can't be authenticated. Safe to download?And apparently it's the same kernel I have..

---

### Post by dabang on 2009-08-19
Same problem here. security.ubuntu.com seems to experience some problems at the moment. 

It's a minor kernel update:

```
# apt-cache policy linux-image-2.6.28-15-generic                                                                     
linux-image-2.6.28-15-generic:                                                                                                        
  Installiert: 2.6.28-15.48                                                                                                           
  Kandidat: 2.6.28-15.49                                                                                                              
  Versions-Tabelle:                                                                                                                   
     2.6.28-15.49 0                                                                                                                   
        500 http://security.ubuntu.com jaunty-security/main Packages                                                                  
 *** 2.6.28-15.48 0                                                                                                                   
        500 http://de.archive.ubuntu.com jaunty-updates/main Packages                                                                 
        100 /var/lib/dpkg/status       
```

I guess, time will solve the problem! :-)

---

### Post by virtualtom on 2009-08-19
I'm having the same issue, here's a screen shot of the attempt

[IMG]http://yfrog.com/15screenshotuiwp[/IMG]http://yfrog.com/15screenshotuiwp

---

