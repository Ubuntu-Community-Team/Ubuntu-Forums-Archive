---
title: "In update check translations all fail"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by stozi on 2009-06-12
I guess it's not crucial, but it's annoying to see the message "failed" pop up every time I update. I use English Canadian. I don't see anything weird about my repositories, but all the packages called more or less translations-en-ca (it goes by pretty fast) fail. From what I could see as they wizz by the mostly seem to have something to do with security. I went into system>language support and it said the language wasn't entirely installed, but correcting that didn't seem to affect the update failings.

---

### Post by Partyboi2 on 2009-06-13
Hi, try changing your download server in Software Sources(System>Admin>Software Sources) under the 1st tab to another server.

---

### Post by stozi on 2009-06-13
Thanks, have tried a few now, all the same.

---

### Post by Partyboi2 on 2009-06-13
Can you open a terminal and please post the output to
```
sudo apt-get update
```

---

### Post by stozi on 2009-06-15
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty Release.gpg
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty/main Translation-en_CA                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_CA   
Ign [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty/universe Translation-en_CA             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_CA       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_CA 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_CA 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                      
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty/restricted Translation-en_CA           
Ign [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty/multiverse Translation-en_CA          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages            
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Ign [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates/universe Translation-en_CA
Ign [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates/main Translation-en_CA
Ign [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates/multiverse Translation-en_CA
Ign [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates/restricted Translation-en_CA
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty Release          
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates Release                       
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty/main Packages                         
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty/universe Packages
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty/restricted Packages
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty/multiverse Packages
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates/universe Packages
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates/main Packages
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates/multiverse Packages
Hit [http://mirror.uoregon.edu](http://mirror.uoregon.edu) jaunty-updates/restricted Packages
Reading package lists... Done

---

### Post by Partyboi2 on 2009-06-15
According to the output there is no problem with updating. Are you still having the problem or has it cleared  up?

---

### Post by stozi on 2009-06-15
All the ones that say "ign" in command line say "failed" in update manager. I don't know how much of a problem this is, isn't causing problems for me, but seeing "failed" keep flashing by is concerning.

---

### Post by stra0529 on 2009-10-27
I have the same problem, did you find any solution?
Thanks.

---

