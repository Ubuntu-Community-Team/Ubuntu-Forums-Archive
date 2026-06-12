---
title: "[SOLVED] Synaptic Manager broken"
date: 2008-08-02
forum: General Help
---

### Post by sumpm1 on 2008-08-02
Hi, running 8.04.1. I get these errors when I try to open the Synaptic Manager and the "Add/Remove" wizard:

I tried to uninstall firefox 3 from Synaptic and it told me that c couple of things did not complete. But now I am completely unable to open the Synaptic at all.

Thanks

[IMG]http://img501.imageshack.us/img501/9769/screenshot001wi6.png[/IMG]

[IMG]http://img501.imageshack.us/img501/1369/screenshot000ov8.png[/IMG]

---

### Post by coffeecat on 2008-08-02
Firstly, have you ever run one of those third-party extra software installation scripts like Automatix or Ultamatix? They can be bad, bad news.

Secondly, post the entire contents of your /etc/apt/sources.list file. We need to see if the contents have been corrupted.

Thirdly, have you yet tried to run:

```
sudo apt-get update
sudo apt-get install -f
```... in a terminal and, if so, what happened? If you haven't done this yet, it may be safer to delay doing it until after the sources.list file has been checked.

---

### Post by Kevbert on 2008-08-02
Another old favourite is
```
sudo dpkg-configure-a
```
But the 'install -f' is the best one.

---

### Post by sumpm1 on 2008-08-02
I haven't run any third party installers no. Here is the sources.list zipped.

This is what happens when I run the update command in terminal, this is the same error I am getting with Synaptic.

dave@dave-desktop:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [49.3kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [293kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6636B]   
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [84.9kB]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [11.0kB]    
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [908B]    
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [75.1kB]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [16.9kB]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [16.4kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [2612B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]    
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [26.6kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [3708B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3874B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]
Fetched 716kB in 2s (279kB/s)
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing xscreensaver-gl (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
dave@dave-desktop:~$

---

### Post by coffeecat on 2008-08-02
It's probably easier for forum members if you post the actual file in a code or quote box. So I've downloaded the zip file, unpacked it and I'm reposting it for you.

Here's the OP's sources.list file:

```
# 
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```I've only had a quick look (I've got to go out in a moment) and I can't see anything wrong, but perhaps someone else might see something I've missed.

The other thing is that both Synaptic and apt-get are complaining about xscreensaver-gl. It might be worth searching the forum for this. Or someone else may have a suggestion.

---

### Post by sisco311 on 2008-08-02
try:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by sumpm1 on 2008-08-02
> **sisco311 said:**
> try:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

This did the trick. Synaptic is up and running fine and allowed me to remove Firefox 3. 

Thanks sisco

---

### Post by sadako1 on 2008-09-06
I had this issue and you helped resolve - thanks
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

---

