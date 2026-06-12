---
title: "cant update ubuntu"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by spencerlewis on 2009-02-17
Hello ,
everytine i go and to updat ubuntu 8.10 thu the update manager i get an error message telling me "Not all changes and updates succeeded..." and attached a pic of the error window.
i tried to install dpkg because it was corrupt. i got this error
root@ubuntu:/home/spencer# apt-get install dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  dpkg
1 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

i have no clue what to do 
i would really like to be able to update!
Thanks in advance:)

---

### Post by abn91c on 2009-02-17
did you try sudo apt-get install -f

---

### Post by spencerlewis on 2009-02-18
> **abn91c said:**
> did you try sudo apt-get install -f
yes i did and to no avail. i am really stumped here! I recently removed  some software thu terminal, could that be the cause?

---

### Post by theozzlives on 2009-02-18
```
sudo dpkg --configure -a
```

```
sudo apt-get upgrade
```

---

### Post by spencerlewis on 2009-02-18
still cant get it... i used these commands started to DL the updates then failed... (btw my audio wont work now either!)
here r the commands i used
sudo dpkg --clear-avail
sudo dpkg --configure --pending
sudo dpkg --configure -a

sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove

And to reinstall dpkg:

sudo apt-get update
sudo apt-get --reinstall install dpkg
:KS

:P

---

### Post by spencerlewis on 2009-02-18
> **theozzlives said:**
> ```
sudo dpkg --configure -a
```

```
sudo apt-get upgrade
```

after this i got this spencer@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for spencer: 
spencer@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  consolekit dpkg fglrx-modaliases gvfs gvfs-backends gvfs-bin gvfs-fuse
  hal-info libck-connector0 libgvfscommon0 libpam-ck-connector libpq5 libxine1
  libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x rhythmbox
  sudo
19 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9817kB of archives.
After this operation, 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: statoverride file contains empty line
E: Sub-process /usr/bin/dpkg returned an error code (2)
spencer@ubuntu:~$

---

### Post by spencerlewis on 2009-02-18
update i did update-manager -d and got
spencer@ubuntu:~$ update-manager -d
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

not sure if it helps but it cant hurt

---

### Post by Partyboi2 on 2009-02-18
Have a look at your  /var/lib/dpkg/statoverride file and make sure that you have no empty lines in the file or at the end of the file.
```
gksu gedit /var/lib/dpkg/statoverride
```

---

### Post by spencerlewis on 2009-02-18
there is nothing in the file. its just blank.

:(
hmmm...

---

### Post by Partyboi2 on 2009-02-18
If the file is empty then try using the old one.
```
sudo cp /var/lib/dpkg/statoverride-old /var/lib/dpkg/statoverride
```
then
```
sudo dpkg --configure -a
```

---

### Post by spencerlewis on 2009-02-19
ok i think i got it i removed everything in the statoverride file but "hplip root 755 /var/run/hplip"  (as instructed on anoter forum) now it updates. but now whenever i try to install, uninstall, edit, or do virtually any other command in terminal i get his message
"Setting up qt4-qtconfig (4.4.3-0ubuntu1.1) ... update-alternatives: internal error: /var/lib/dpkg/alternatives/qtconfig corrupt: invalid update mode dpkg: error processing qt4-qtconfig (--configure):  subprocess post-installation script returned error exit status 2 Errors were encountered while processing:  qt4-qtconfig"
any ideas>

thank you all for your help so far!

---

### Post by Partyboi2 on 2009-02-20
Try reinstalling qt4-qtconfig

```
sudo apt-get --reinstall install qt4-qtconfig
```

---

### Post by spencerlewis on 2009-02-20
wen i try to re install i get 

spencer@ubuntu:~$ sudo apt-get --reinstall install qt4-qtconfig
[sudo] password for spencer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up qt4-qtconfig (4.4.3-0ubuntu1.2) ...
update-alternatives: internal error: /var/lib/dpkg/alternatives/qtconfig corrupt: invalid update mode
dpkg: error processing qt4-qtconfig (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 qt4-qtconfig
E: Sub-process /usr/bin/dpkg returned an error code (1)

:(  :(:(:(:(: :|

---

