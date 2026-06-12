---
title: "[SOLVED] Erro with Security Updates"
date: 2008-09-04
forum: General Help
---

### Post by LindaLou on 2008-09-04
I was downloading the security updates last week and received the error messages as shown.  I entered the http but came up with a 404 error.

Is there a way for me to check all the security updates that have been installed?  Where can I located this security update for installation, if it is not, indeed, installed?

Thanks in advance

---

### Post by LindaLou on 2008-09-09
bump

---

### Post by Ryadt on 2008-09-09
Try updating```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by zvacet on 2008-09-09
Try to change server in system>admin>software sources to** main**.

---

### Post by Rocket2DMn on 2008-09-09
Try the apt-get update and upgrade and see if it picks it up this time (sometimes the repositories just have issues).

If it still doesn't work, can you please post your sources.list file for us?
```
cat /etc/apt/sources.list
```

---

### Post by Sycron on 2008-09-09
Are you using Hardy Heron ?

---

### Post by LindaLou on 2008-09-14
I'm using the latest version of Ubuntu Ok, I entered into terminal sudo apt-get update && sudo apt-get upgrade, and received the following output:

[sudo] password for linda: 
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy Release.gpg            
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy Release 
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates Release              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Packages
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Packages
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/main Sources
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/restricted Sources
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Packages
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Sources
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Am I correct in saying that from the final 2 lines, it looks like there is nothing missing (i.e. the one in question)?

---

### Post by Rocket2DMn on 2008-09-14
It would seem to me that your Ubuntu install is up to date :)

---

### Post by Sycron on 2008-09-15
Yes, it is.

---

### Post by LindaLou on 2008-09-15
My thanks to all concerned for solving this issue!!!O:)  :D

---

