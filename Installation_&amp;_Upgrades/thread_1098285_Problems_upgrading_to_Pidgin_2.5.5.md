---
title: "Problems upgrading to Pidgin 2.5.5"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Nellie on 2009-03-16
Hello.  I was trying to upgrade my Pidgin messenger to Pidgin 2.5.5 with the getdeb packages.

I got through the Pidgin data, libpurple0 and libpurple-bin fine.  When I got to the last file, pidgin, it gave me an error.  

Error:  Dependency is not satisfiable: libpango 1.0.0


I'm on Hardy, 32 bits.

Thanks.

---

### Post by Partyboi2 on 2009-03-16
Have you tried to install the libpango1.0-0 package? You can search for it in synaptic and install or open a terminal (Applications>Accessories>Terminal) and install with
```
sudo apt-get install libpango1.0-0
```

---

### Post by Nellie on 2009-03-17
When I do that, I get this.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpango1.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Now it's giving me the Error: Dependency is not satisfiable: libgtk2.0-0 when I tried to run it again.  :-?

Just on the chance that it would take the same issue to do, I did:

sudo apt-get install libgtk2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

2nd try to reinstall:

 sudo apt-get --reinstall install libgtk2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 2067kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main libgtk2.0-0 2.12.9-3ubuntu2 [2067kB]
Fetched 2067kB in 22s (92.4kB/s)                                               
(Reading database ... 162084 files and directories currently installed.)
Preparing to replace libgtk2.0-0 2.12.9-3ubuntu2 (using .../libgtk2.0-0_2.12.9-3ubuntu2_i386.deb) ...
Unpacking replacement libgtk2.0-0 ...
Setting up libgtk2.0-0 (2.12.9-3ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Still getting the error in regards to the libgtk file.

---

### Post by Nellie on 2009-03-30
bump

Still having problems when I get to the last packet to load and get that error.

---

