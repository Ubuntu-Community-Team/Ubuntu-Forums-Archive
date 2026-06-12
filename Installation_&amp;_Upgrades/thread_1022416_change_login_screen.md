---
title: "change login screen"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by herrbrand on 2008-12-26
hello

i want to make some changes in the login program of my ubuntu server edition 8.04 LTS. i downloaded the source file with apt-get source login. but i can't find the files. where are the put?

Robbert

---

### Post by linuxbastard on 2008-12-26
Hi,

TO change a login screen, go to system >> administration >> login window and then go to the "local" tab.

If you downloaded a login theme, just click on "+Add" and select the locate the package you downloaded.

Hope this helps.

---

### Post by herrbrand on 2008-12-26
ow... i work with the server edition, it has no desktop like gnome. it has only commandline.

Robbert

---

### Post by infamous-online on 2008-12-26
so are you trying to install a graphic display for the ubuntu server?

---

### Post by linuxbastard on 2008-12-26
Ok, My bad, I assumed you meant the login screen, so you must mean the login script.  What exactly are you trying to do?

---

### Post by herrbrand on 2008-12-26
when i login on the ubuntu server edition i get an text based login screen. i want to costomize that.

my question is where does apt-get source ***** put the source files i downloaded. because i downloaded the login source with apt-get and i want to change them.

Robbert

---

### Post by albinootje on 2008-12-26
> **herrbrand said:**
>  i want to make some changes in the login program of my ubuntu server edition 8.04 LTS. i downloaded the source file with apt-get source login. but i can't find the files. where are the put? 

Should be in your current directory :

$ ls -la shadow*
-rw-r--r--  1 root root   77622 2008-12-18 02:04 shadow_4.1.1-1ubuntu1.2.diff.gz
-rw-r--r--  1 root root    1702 2008-12-18 02:04 shadow_4.1.1-1ubuntu1.2.dsc
-rw-r--r--  1 root root 2720267 2008-06-09 21:06 shadow_4.1.1.orig.tar.gz

---

### Post by herrbrand on 2008-12-26
do you mean with current directory the ~ directorie?
i lookt already in it with ls -al but didn't see the file.

i also looked in the /var/cache/ folder.

Robbert

---

### Post by albinootje on 2008-12-26
> **herrbrand said:**
> do you mean with current directory the ~ directorie?
i lookt already in it with ls -al but didn't see the file.

i also looked in the /var/cache/ folder.


Try : ls -latr to sort on timestamps, perhaps easier to see the files.

I've used :
sudo apt-get source login
and it ended up in the home directory of my normal user (which was then my current directory).

(This is always the case if you use "apt-get source".
I've used "sudo apt-get -b source" many times in the past, and it always worked like that.)

---

### Post by herrbrand on 2008-12-27
i lookt again in my ~ folder and i found a map .gnupg in it are two files:
[email]root@~/.gnupg[/email]# ls -al

total 20
drwx------ 2 root root 4096 Dec 27 02:06 .
drwxr-xr-x 3 root root 4096 Dec 27 02:06 ..
-rw------- 1 root root 9417 Dec 27 02:06 gpg.conf
-rw------- 1 root root    0 Dec 27 02:06 pubring.gpg

are these the source files? :-S

Robbert

---

### Post by herrbrand on 2008-12-27
I don't understand it but i downloaded it again and now it works :S :D

Thanks for the help

---

### Post by albinootje on 2008-12-27
> **herrbrand said:**
> i lookt again in my ~ folder and i found a map .gnupg in it are two files:
[email]root@~/.gnupg[/email]# ls -al

total 20
drwx------ 2 root root 4096 Dec 27 02:06 .
drwxr-xr-x 3 root root 4096 Dec 27 02:06 ..
-rw------- 1 root root 9417 Dec 27 02:06 gpg.conf
-rw------- 1 root root    0 Dec 27 02:06 pubring.gpg

are these the source files? :-S

Hmmm, no.

You need this file for Intrepid/8.10 : shadow_4.1.1.orig.tar.gz

You can download it also from here :
[http://packages.ubuntu.com/hardy-updates/login](http://packages.ubuntu.com/hardy-updates/login) (hardy)
[http://packages.ubuntu.com/intrepid-updates/login](http://packages.ubuntu.com/intrepid-updates/login) (intrepid)

Look at the link at the right of the page,
called "Download Source Package shadow:"

[... edited later ...]
Okay.. good that you managed to download it now!

---

