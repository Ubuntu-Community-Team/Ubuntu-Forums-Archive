---
title: "Installing Google Earth"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by gjoseph on 2009-01-14
Installed Google Earth in Ubuntu 8.10.

Followed these commands

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update
sudo aptitude install googleearth-4.3

I could use google earth after installation. But it didn&#8217;t login afterwards when I opened it from Application>Internet.

Also now I am getting these error messages in update manager and package manager. My software source is server in India.

E: Type &#8216;&#8211;2009-01-14&#8242; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Unable to lock the list directory

E: Type &#8216;&#8211;2009-01-14&#8242; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I am new to Linux & Ubuntu Please help to recover as well as installing Google Earth.

Regards

Ginu

---

### Post by iaculallad on 2009-01-14
Try to terminate other installation process:

```
ps aux | grep apt
```

and use the kill/killall command to terminate any apt installation process running on background.

---

### Post by Partyboi2 on 2009-01-14
Open a terminal (Applications>Accessories>Terminal) and remove the file 
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
then re add the repo
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```
then grab the key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

