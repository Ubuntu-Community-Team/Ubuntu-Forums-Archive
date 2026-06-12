---
title: "No Intrepid Updates in the Last Week?"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by timking on 2009-01-03
I've noticed in the past week that when I do a "apt-get update", it completes very quickly and it has not found updates.  Is something broken on my system or have there not been any updates for the past week? Here is the output from "sudo apt-get update":

```
Hit http://security.ubuntu.com intrepid-security Release.gpg
Hit http://archive.canonical.com intrepid Release.gpg                                              
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US                            
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US                      
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US                        
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US                      
Ign http://archive.canonical.com intrepid/partner Translation-en_US                                
Hit http://security.ubuntu.com intrepid-security Release                      
Hit http://security.ubuntu.com intrepid-security/main Packages                                     
Hit http://security.ubuntu.com intrepid-security/restricted Packages          
Hit http://security.ubuntu.com intrepid-security/main Sources                                       
Hit http://security.ubuntu.com intrepid-security/restricted Sources                                 
Hit http://security.ubuntu.com intrepid-security/universe Packages                                  
Hit http://security.ubuntu.com intrepid-security/universe Sources                                   
Hit http://security.ubuntu.com intrepid-security/multiverse Packages                                
Hit http://security.ubuntu.com intrepid-security/multiverse Sources                                 
Hit http://archive.canonical.com intrepid Release                                                   
Hit http://archive.canonical.com intrepid/partner Packages                    
Hit http://archive.canonical.com intrepid/partner Sources                     
Hit http://us.archive.ubuntu.com intrepid Release.gpg   
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://us.archive.ubuntu.com intrepid-updates Release
Hit http://us.archive.ubuntu.com intrepid-backports Release
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-backports/main Sources
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Sources
Reading package lists... Done
```

I don't remember seeing "Hit" and "Ign" before. What do they mean?  "How do I check (outside of the update manager) if there have been recent updates?

Thanks,
Tim

---

### Post by Ionna on 2009-01-03
I'm also having the same problem. I checked with a friend and he's getting the updates, but I'm not. Not sure what the problem is. 

From what I know, "hit" means they've reached the server, while "ign" means that source was ignored.

---

### Post by agrouo on 2009-01-18
same here.. just returned from a journey and i didn't get any intrepid updates!???? 
is there an online-query for the last updates, so i could check myself if there actually were updates?

thanks,a

---

### Post by HarmonicaGoldfish on 2009-01-18
there were definitely updates. some broke my system this morning - or is at least wreaking havoc within it! Consider yourself lucky :)

---

### Post by Jimmey on 2009-01-18
I'm betting that it entirely depends on which repositories you have enabled. If your friend is getting updates, maybe he's got different repositories added/enabled.

---

### Post by Archmage on 2009-01-18
In this week I got updates for:

libcups2 1.3.9-2ubuntu6
cups-common 1.3.9-2ubuntu6
cups-bsd 1.3.9-2ubuntu6
cups-client 1.3.9-2ubuntu6
acpi-support 0.114-0intrepid1

---

