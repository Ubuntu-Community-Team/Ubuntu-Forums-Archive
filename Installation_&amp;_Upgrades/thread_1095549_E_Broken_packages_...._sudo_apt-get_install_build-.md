---
title: "E: Broken packages .... sudo apt-get install build-essential"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by donalt on 2009-03-13
Hi, New User and need some help with the following error message...anyone able to help me with this...

administrator@doniecom:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages

---

### Post by taurus on 2009-03-13
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

p.s.  Did you remember to run **sudo apt-get update** first?

---

### Post by donalt on 2009-03-14
Hey Taurus,
Below is the sources.list, Im unsure whether i ran sudo apt-get update first, i think i ran it after i had attempted to install a number of programs, if this is any use to you...


administrator@doniecom:~$ cat /etc/apt/sources.list
    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
    deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

---

### Post by taurus on 2009-03-14
Do you still get the same message when you run these two commands from a terminal, one at a time?

```
sudo apt-get update
sudo apt-get install build-essential
```

p.s.  Do you still have Ubuntu install CD?

---

### Post by donalt on 2009-03-14
ok ran

sudo apt-get update

the following was the error, it took ages to connect to the last file before it timed out i guess...



Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg    
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_IE
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_IE
  Unable to connect to packages.freecontrib.org http:
Reading package lists... Done                             
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_IE.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_IE.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_IE.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_IE.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems



then i ran 

sudo apt-get install build-essential

administrator@doniecom:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages

and yup i still have the ubuntu install cd...what would you suggest next? thanks for your assistance...donal

---

