---
title: "Can't update my system - something about broken package"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by lmicu on 2009-10-09
To begin with i have a red square with a white cross on my toolbar instead of the Update Manager Notification icon.

I try to click it and update manager start with no problem, says that are some updates to be installed, i click to install them, it downloads it and the system notifies me about 13 broken packages ( i already try to fix them with synaptic - did not work), i click ok, the system continues with the installation and then I get this:


E: /var/cache/apt/archives/openoffice.org-calc_1%3a3.0.1-9ubuntu3.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.0/program/libscli.so')
E: /var/cache/apt/archives/openoffice.org-core_1%3a3.0.1-9ubuntu3.1_i386.deb: conflicting packages - not installing openoffice.org-core

Let me know if you have the same problem or any ideea.

my system:

dell inspiron e1705
ubuntu 9.04
gnome 2.26.1
plenty of disk space


btw:

tryed also apt-get install -f

this is the result:

root@lucian-laptop:/home/lucian# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-calc openoffice.org-core
The following packages will be upgraded:
  openoffice.org-calc openoffice.org-core
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B/30.1MB of archives.
After this operation, 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 253427 files and directories currently installed.)
Preparing to replace openoffice.org-calc 1:3.0.1-9ubuntu3 (using .../openoffice.org-calc_1%3a3.0.1-9ubuntu3.1_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-calc_1%3a3.0.1-9ubuntu3.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.0/program/libscli.so')
dpkg: regarding .../openoffice.org-core_1%3a3.0.1-9ubuntu3.1_i386.deb containing openoffice.org-core:
 openoffice.org-core conflicts with openoffice.org-calc (<< 1:3.0.1-9ubuntu3.1)
  openoffice.org-calc (version 1:3.0.1-9ubuntu3) is present and installed.
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a3.0.1-9ubuntu3.1_i386.deb (--unpack):
 conflicting packages - not installing openoffice.org-core
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-calc_1%3a3.0.1-9ubuntu3.1_i386.deb
 /var/cache/apt/archives/openoffice.org-core_1%3a3.0.1-9ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Partyboi2 on 2009-10-10
Open a terminal and try clearing the cache first with
```
sudo apt-get clean
```
then try
```
sudo apt-get -f install
```

---

### Post by garvinrick4 on 2009-10-10
I would say also to clean your cache of existing packages damaged
and reload new from source would be first thing to do. 
 Throw out the bad and bring in the new. (X-wife taught me that when cloth's were in yard)

---

### Post by lmicu on 2009-10-10
> **Partyboi2 said:**
> Open a terminal and try clearing the cache first with
```
sudo apt-get clean
```
then try
```
sudo apt-get -f install
```

This worked like a miracle. Thank you Partyboy!

Keep Ubuntu going, love the free stuff that work well.

---

### Post by lmicu on 2009-10-10
> **garvinrick4 said:**
> I would say also to clean your cache of existing packages damaged
and reload new from source would be first thing to do. 
 Throw out the bad and bring in the new. (X-wife taught me that when cloth's were in yard)

The method above work, but it seams your was the same, Thank you! Appreciate your help.

---

### Post by LarryJ2 on 2009-10-17
Thank you Partyboi2.  This fixed my Jaunty 9.04 complaint that openoffice.org-core was "short read"   [3a3.0.1-9ubuntu3.1_i386.deb: short read in buffer_copy]

I think this error can be marked   SOLVED.

---

### Post by Fungyo on 2009-10-19
cleaning cache solved a similar problem i had, thanks and hooroo! :guitar:

---

