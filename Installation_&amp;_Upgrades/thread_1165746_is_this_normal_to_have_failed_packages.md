---
title: "is this normal to have failed packages?"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by lozenges on 2009-05-20
hi all!
i am using kubuntu 9.04 and after i installed mediubuntu, i followed the instructions from the site. i got these errors trying to update, at first i thought it's the servers or they haven't put up the finishes packages but it's been a week already. so could anyone tell me if this is normal? how do i fix it?
thanks in advance!

---

### Post by lozenges on 2009-05-21
anyone?

---

### Post by mcduck on 2009-05-21
Your screenshot is so small it's absolutely impossible to say anything based on that.

Could you open a terminal, run following commands
 and then post the output here (as text..):

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by lozenges on 2009-05-21
sorry, didn't notice it was so small. i guess it was compressed automatically.

[http://www.flickr.com/photos/9942549@N02/3551814572/](http://www.flickr.com/photos/9942549@N02/3551814572/)

i don't know how to post images here so i uploaded it to flickr and pasted a link. sorry, total tech idiot your dealing with here.
thanks again!

the output from konsole was
```
Hit http://security.ubuntu.com jaunty-security Release.gpg      
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_CA
Ign http://security.ubuntu.com jaunty-security/main Translation-en_CA      
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_CA  
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com jaunty-security Release                     
Hit http://security.ubuntu.com jaunty-security/restricted Packages         
Hit http://security.ubuntu.com jaunty-security/main Packages               
Hit http://security.ubuntu.com jaunty-security/restricted Sources          
Hit http://security.ubuntu.com jaunty-security/universe Packages           
Hit http://security.ubuntu.com jaunty-security/universe Sources            
Hit http://security.ubuntu.com jaunty-security/multiverse Packages         
Hit http://security.ubuntu.com jaunty-security/multiverse Sources          
Hit http://ca.archive.ubuntu.com jaunty Release.gpg                        
Hit http://ca.archive.ubuntu.com jaunty/restricted Translation-en_CA       
Hit http://ca.archive.ubuntu.com jaunty/main Translation-en_CA
Ign http://ca.archive.ubuntu.com jaunty/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com jaunty/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://ca.archive.ubuntu.com jaunty-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com jaunty-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com jaunty-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com jaunty-updates/multiverse Translation-en_CA
Hit http://ca.archive.ubuntu.com jaunty Release
Hit http://ca.archive.ubuntu.com jaunty-updates Release
Hit http://ca.archive.ubuntu.com jaunty/restricted Packages
Hit http://ca.archive.ubuntu.com jaunty/main Packages
Hit http://ca.archive.ubuntu.com jaunty/restricted Sources
Hit http://ca.archive.ubuntu.com jaunty/universe Packages
Hit http://ca.archive.ubuntu.com jaunty/universe Sources
Hit http://ca.archive.ubuntu.com jaunty/multiverse Packages
Hit http://ca.archive.ubuntu.com jaunty/multiverse Sources
Hit http://ca.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://ca.archive.ubuntu.com jaunty-updates/main Packages
Hit http://ca.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://ca.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://ca.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://ca.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by mcduck on 2009-05-21
No problem, I pretty much assumed you simply didn't notice that the linked image was that small. :)

Anyway, based on the terminal output everything seems to be working fine.

---

### Post by lozenges on 2009-05-21
ok! thanks again!

---

### Post by donkyhotay on 2009-05-21
A failed package simply means the package manager couldn't reach one of the servers. This happens occasionally especially during times of heavy load or if you non-ubuntu repositories that aren't as solid. 99% of the time that happens you just hit 'reload' again and it'll work.

---

