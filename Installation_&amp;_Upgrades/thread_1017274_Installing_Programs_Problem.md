---
title: "Installing Programs Problem"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by BillBillJr on 2008-12-20
I'm using Ubuntu 8.10.

I get two errors when installing some programs. The first error reads:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```

And the second error, I don't know exactly what it says, but it says I need to close any management programs, even though I don't have any open. These error only occur when I try to install something. Like when I tried to install Flash and Java. Any help with them? Thanks! :)

---

### Post by Rocket2DMn on 2008-12-20
Can you please run
```
sudo dpkg --configure -a
```
That will likely fix your problem, otherwise post back with the error messages please.

The problem you are experiencing appears when a package manager is interrupted while doing something important.

---

### Post by BillBillJr on 2008-12-20
When it asks for my password I can't enter anything it. I'm entering my password but nothing it typing in...

---

### Post by Partyboi2 on 2008-12-20
When you enter your password in from a terminal you will not see it displayed on screen. Go ahead and type it and press enter.

---

### Post by BillBillJr on 2008-12-20
Ok, I've entered my password and the Terminal did it's thing. Now when I try to go to the Add/Remove I get the error:

```
Failed to check for installed and avaible applications.

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources/list' and reload the software information with 'sudo apt-get update' and 'sudo apt-get install -f'.
```

---

### Post by Rocket2DMn on 2008-12-20
Can you please try running
```
sudo apt-get install -f
```
and post the output back here.  Also try
```
sudo apt-get update
sudo apt-get upgrade
```
Please copy and paste all output if you can't tell what's going on (highlight it in terminal and right click -> Copy)

---

### Post by BillBillJr on 2008-12-20
It asked me if I wanted to install a few Open Office programs and I said Yes. Here was what happened:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-base-core openoffice.org-core openoffice.org-gnome
  openoffice.org-gtk openoffice.org-math openoffice.org-writer python-uno
Suggested packages:
  openoffice.org-base openoffice.org-evolution openoffice.org-gcj
  openoffice.org-filter-binfilter default-jre java-gcj-compat openjdk-6-jre
  sun-java5-jre sun-java6-jre java5-runtime openoffice.org-java-common
  openoffice.org-writer2latex
The following packages will be upgraded:
  openoffice.org-base-core openoffice.org-core openoffice.org-gnome
  openoffice.org-gtk openoffice.org-math openoffice.org-writer python-uno
7 upgraded, 0 newly installed, 0 to remove and 172 not upgraded.
3 not fully installed or removed.
Need to get 0B/32.3MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 102682 files and directories currently installed.)
Preparing to replace openoffice.org-gtk 1:2.4.1-11ubuntu2 (using .../openoffice.org-gtk_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-gtk ...
Preparing to replace openoffice.org-gnome 1:2.4.1-11ubuntu2 (using .../openoffice.org-gnome_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-gnome ...
Preparing to replace openoffice.org-writer 1:2.4.1-11ubuntu2 (using .../openoffice.org-writer_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-writer ...
Preparing to replace openoffice.org-base-core 1:2.4.1-11ubuntu2 (using .../openoffice.org-base-core_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-base-core ...
Preparing to replace python-uno 1:2.4.1-11ubuntu2 (using .../python-uno_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement python-uno ...
Preparing to replace openoffice.org-math 1:2.4.1-11ubuntu2 (using .../openoffice.org-math_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-math ...
Preparing to replace openoffice.org-core 1:2.4.1-11ubuntu2 (using .../openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
Processing triggers for man-db ...
Setting up openoffice.org-core (1:2.4.1-11ubuntu2.1) ...
Setting up openoffice.org-gtk (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-gnome (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-base-core (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-writer (1:2.4.1-11ubuntu2.1) ...

Setting up python-uno (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-math (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-calc (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-draw (1:2.4.1-11ubuntu2.1) ...

Setting up openoffice.org-impress (1:2.4.1-11ubuntu2.1) ...

```

---

### Post by Rocket2DMn on 2008-12-20
Well until you cut it off, it looks like it is proceeding normally.  Did it give you any errors?  Did you run the update and upgrade commands I gave?

---

