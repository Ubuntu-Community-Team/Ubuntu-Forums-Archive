---
title: "Upgrade Manager Install error"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by WildeBeest on 2009-07-17
What does the error mean and how do I fix it?

```
E: kubuntu-docs: subprocess post-installation script returned error exit status 1
```I have an Ubuntu install, then I added the KDE desktop.

---

### Post by WildeBeest on 2009-07-19
ttt

---

### Post by Partyboi2 on 2009-07-19
Hi, open a terminal and post the output's to
```
sudo apt-get -f install
sudo dpkg --configure -a
``` so we can have a better look on what might be causing the problem.

---

### Post by wabbalee on 2009-07-19
status 1 means not all dependencies were met or something else did not succeed during installation. have you enabled all repositories?

---

### Post by WildeBeest on 2009-07-20
> **Partyboi2 said:**
> Hi, open a terminal and post the output's to
```
sudo apt-get -f install
sudo dpkg --configure -a
``` so we can have a better look on what might be causing the problem.

**sudo apt-get -f install**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up kubuntu-docs (9.04.2) ...
ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**sudo dpkg --configure -a**
```
Setting up kubuntu-docs (9.04.2) ...
ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kubuntu-docs

```

---

### Post by Partyboi2 on 2009-07-20
Try creating the directory first
```
cd /usr/share/doc/kde/HTML/en
sudo mkdir kubuntu

```
```
sudo apt-get --reinstall install kubuntu-docs
```

---

### Post by WildeBeest on 2009-07-20
Thanks, I'll try that when I get home.
 
I have created the kubuntu folder a few times, but it always gets deleted.
 
But, I have never ran the reinstall afterwards.

---

### Post by WildeBeest on 2009-07-20
This is what I got when I ran the "sudo apt-get --reinstall install kubuntu-docs".

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up kubuntu-docs (9.04.2) ...
ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by WildeBeest on 2009-07-21
Ttt

---

### Post by wabbalee on 2009-07-21
do you have synaptic on that system? usually when you start synaptic and you have such errors it tells you at the bottom that you have broken packages. you could locate and uninstall these packages, upgrade your system and then try reinstalling the kubuntu-desktop meta package. it should then auto select everything you need for a kubuntu environment.

see if that solves your problem.
Ron

---

### Post by WildeBeest on 2009-07-22
Synaptic indicates no broken packages.

The KDE desktop works fine.

I just continue to get the error.

```
Setting up kubuntu-docs (9.04.2) ...
ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory
dpkg: error processing kubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wabbalee on 2009-07-22
Initially you say:
> I have an Ubuntu install, then I added the KDE desktop.

I haven't done this myself in this way yet but I have plans to do so in the future: install ubuntu first and then install both the Kubuntu-desktop and Xubuntu-desktop meta packages which should auto select everything you need. That is not the same as installing KDE and XFCE.

have you tried this?

---

### Post by WildeBeest on 2009-07-23
That's what I meant. Installed Ubuntu and then added kubuntu-desktop.

---

### Post by wabbalee on 2009-07-23
well this is where my humble knowledge ends for now, I hope some one else who has more know how of this subject is watching this thread over our shoulders and give a hint of some kind.

some googling got me this:
[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/]("http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/")

[http://ubuntuforums.org/showthread.php?t=541998]("http://ubuntuforums.org/showthread.php?t=541998")

[http://ubuntuforums.org/archive/index.php/t-21672.html]("http://ubuntuforums.org/archive/index.php/t-21672.html")

all to do with similar error.

good luck.
Ron

---

### Post by Partyboi2 on 2009-07-23
Just to add, there is also an open bug report about this (see [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/kubuntu-docs/+bug/377671")). Feel free to add any further information that might help to get the bug fixed.

---

### Post by CFBauer on 2009-07-30
Bamp. Tried all the suggestions in this thread to no avail.

---

### Post by Soul-Sing on 2009-07-30
remove with purge the kubuntu-docs package.

---

### Post by jonglee1 on 2009-08-27
I believe that others found the solution already. But, FYI, here is the solution to this problem.

[https://bugs.launchpad.net/ubuntu/+source/kubuntu-docs/+bug/377671/comments/7](https://bugs.launchpad.net/ubuntu/+source/kubuntu-docs/+bug/377671/comments/7)

---

