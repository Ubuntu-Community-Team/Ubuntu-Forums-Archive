---
title: "Can't Update... Ubuntu 8.10"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2009-02-08
I'm using Ubuntu 8.10 and from a few days ago, I can't update properly through terminal. It has been happening since the last update when it installed the new kernel version. After rebooting I wanted to update so that it would recognize old packages and ask me to remove them. But all I get is:
> ~$ sudo apt-get update
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                 
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Sources
Fetched 308B in 2s (132B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems


And also, after that update, my old kernels that I have removed and deleted from the grub list and Vista showed up again, even after I made a clean install of Ubuntu, deleting Vista.

---

### Post by taurus on 2009-02-08
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)

---

### Post by arashiko28 on 2009-02-08
The problem remains even after downloading and running in terminal the file of that thread.:(

---

### Post by arashiko28 on 2009-02-08
I found the second version at the post and it worked, thanks a lot!;)

........................

Post's aren't marked as solved anymore? I don't see the option...

---

