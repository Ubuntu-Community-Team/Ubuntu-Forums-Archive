---
title: "[SOLVED] I can't package manage."
date: 2008-10-09
forum: General Help
---

### Post by I_Failed_C++ on 2008-10-09
I can't use synaptic or apt-get b/c the machine keeps telling me I need something I don't want.  I'm trying to get some ham radio software installed.  How do you completely remove a restricted driver?  I think this is all caused by winmodem I tried to get to work but have since removed.  I've tried removing the package.
Here are some outputs that may help...
```

admin@gateway750:~$ sudo dpkg --configure -a
Password:
admin@gateway750:~$ sudo apt-get install hamlibs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
admin@gateway750:~$ sudo apt-get remove conexant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
admin@gateway750:~$ sudo apt-get remove --purge conexant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package conexant needs to be reinstalled, but I can't find an archive for it.
admin@gateway750:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [189B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/main Packages        
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/restricted Packages  
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Fetched 3B in 0s (3B/s)  
Reading package lists... Done
admin@gateway750:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package conexant needs to be reinstalled, but I can't find an archive for it

```

---

### Post by I_Failed_C++ on 2008-10-11
So no one knows?
Guess I'll have to reinstall.  Does anyone know an easy way to backup a single users settings/preferences and private files with out using the HomeUserBackup which I can't install?

---

### Post by drs305 on 2008-10-11
Try running this to see if conexant is listed in dpkg's status:
```
cat /var/lib/dpkg/status | grep  conexant
```

If it is found, here are two things you can try:
Replace 'status' with 'status.old':
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.111008
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update && sudo apt-get upgrade
```

If that doesn't work, restore to original:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-old
sudo mv /var/lib/dkpg/status.111008 /var/lib/dpkg/status

```

Edit status to remove mention of conexant:
```

gksudo gedit /var/lib/dpkg/status

```
Remove the section concerning conexant, save the file but leave it open;  then:
```

sudo apt-get update && sudo apt-get upgrade

```
If it still doesn't work, return to the editor, undo the change and save the file to restore it to the original state.

---

### Post by I_Failed_C++ on 2008-10-13
Thank you, drs!
The second method worked like a champ!  I knew there had to be a way to make the machine forget it ever had that on there... Just didn't know where to look.

---

