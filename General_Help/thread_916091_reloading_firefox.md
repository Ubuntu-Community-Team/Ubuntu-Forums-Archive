---
title: "reloading firefox"
date: 2008-09-10
forum: General Help
---

### Post by xGutsAndGloryx on 2008-09-10
i am having to reload firefox. its not allowing me to reinstall through synaptic package manager.  can anyone help me?

---

### Post by Titan8990 on 2008-09-10
What error are you getting?

---

### Post by dabang on 2008-09-10
You mean "reinstall"? That would be simple: open a terminal and type 

```
sudo apt-get install --reinstall firefox
```

Or remove it completely via synaptic and install again.

---

### Post by xGutsAndGloryx on 2008-09-10
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo apt-get install --reinstall firefox
[sudo] password for xgutsandgloryx:
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
  firefox: Depends: firefox-3.0 but it is not going to be installed
E: Broken packages
xgutsandgloryx@xgutsandgloryx-laptop:~$

---

### Post by Titan8990 on 2008-09-10
Try:

sudo apt-get remove --purge firefox && sudo apt-get install firefox

---

### Post by xGutsAndGloryx on 2008-09-10
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo apt-get remove --purge firefox && sudo apt-get install firefox
[sudo] password for xgutsandgloryx:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 232 not upgraded.
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
  firefox: Depends: firefox-3.0 but it is not going to be installed
E: Broken packages
xgutsandgloryx@xgutsandgloryx-laptop:~$

---

### Post by Titan8990 on 2008-09-10
Try:

sudo dpkg --configure -a

---

### Post by xGutsAndGloryx on 2008-09-10
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo apt-get remove --purge firefox && sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 232 not upgraded.
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
  firefox: Depends: firefox-3.0 but it is not going to be installed
E: Broken packages
xgutsandgloryx@xgutsandgloryx-laptop:~$ 
xgutsandgloryx@xgutsandgloryx-laptop:~$ 
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo dpkg --configure -a
xgutsandgloryx@xgutsandgloryx-laptop:~$

---

### Post by Titan8990 on 2008-09-10
Are you having other issues with aptitude? It doesn't appear to making an attempt to download a new package nor does it have a package waiting from a failed install.

Temporarily you can download firefox from their website. It does not need to be compiled and can be executed directly.

Hopefully someone will drop in and give some better insight on the issue.

---

### Post by xGutsAndGloryx on 2008-09-10
no i am not having any other problems. when the problem started. i downloaded opera without any problems. any other ideas.

---

### Post by xGutsAndGloryx on 2008-09-10
.

---

### Post by xGutsAndGloryx on 2008-09-10
.

---

### Post by dabang on 2008-09-14
OK, firefox is only a metapackage. Please open synaptic and search for "firefox". I'd guess firefox is not installed, but firefox-3.0 is. If so, try the following:

```
# sudo apt-get clean (optional)
# sudo apt-get apt-get remove --purge firefox-3.0
# sudo apt-get install firefox firefox-3.0
```

---

