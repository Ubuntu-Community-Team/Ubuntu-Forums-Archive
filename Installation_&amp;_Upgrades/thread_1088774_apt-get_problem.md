---
title: "apt-get problem"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by gpnet on 2009-03-06
Hi to all

I would had liked to install  monodevelop 1.9.2 on my ubuntu 8.10. After I didn't find this package I googled and I found this repo with all packages ( mono and monodevelop ) updated to 1.9.2 version. ( from Eric Butler ) 

deb [http://ppa.launchpad.net/firerabbit/ubuntu](http://ppa.launchpad.net/firerabbit/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/firerabbit/ubuntu](http://ppa.launchpad.net/firerabbit/ubuntu) intrepid main

so I launched the synaptic manager and add this repository and the sign key in the third-party tab.

after that I opened a terminal and typed this command:
joss@joss-ubuntu:~$ sudo apt-get install mono
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mono

What does it mean? Am I wrong something ?

Does this command searches the repository I gave in sources.list ? or what else ?

Could any one help me please ?

---

### Post by taurus on 2009-03-06
Did you remember to update your list first after you have modified /etc/apt/sources.list?

```
sudo apt-get update
```

---

### Post by gpnet on 2009-03-06
No, I have to ?

If I do not , the command doesn't take place ?

---

### Post by taurus on 2009-03-06
If you do not, you are still using the old list so whatever repo(s) you have added won't get updated.  Therefore, no "new" packages will be found.

---

### Post by gpnet on 2009-03-06
Okay ,

I run apt-get update and at the bottom of the update list I got this message :

Fetched 6806kB in 33s201kB/s)                                                
Reading package lists... Done

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04508D5C1654E635
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 04508D5C1654E635
W: You may want to run apt-get update to correct these problems

I created a file with the signature as suggested by the instructions and I attached in the authentication tab. I am missing something ?

Could in any case re-do the apt-get install mono and the othes packages now ?

---

### Post by gpnet on 2009-03-06
Okay, I solved !

After I launched apt-get monodevelop the system ask me :
..
..
..
WARNING: The following packages cannot be authenticated! continue ?
I said Yes and I got all installed and running.

Ome more question : where the download did put the files downloaded ? ( I mean the folder) I want to backup these files.
thanks

---

### Post by taurus on 2009-03-06
```
ls -la /var/cache/apt/archives
```

---

### Post by gpnet on 2009-03-06
Thanks very much for your help.

---

