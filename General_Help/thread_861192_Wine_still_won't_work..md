---
title: "Wine still won't work."
date: 2008-07-16
forum: General Help
---

### Post by edward fish on 2008-07-16
I just opened up all my software sources except source code, and now when I try to 

sudo apt-get install wine

I get this error

The following packages have unmet dependencies:
wine: Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages

Being uber new to Ubuntu I'm at a total lose, halp?

---

### Post by SuperSonic4 on 2008-07-16
Have you tried in looking in Synaptic Package manager?

---

### Post by rraj.be on 2008-07-16
This may help:```

System -->Administartion --> Synaptic package manager
```

Then select  **Custom filters **at bottom of left pane.

Now select** Broken **at the Top of left pan.

Just remove any entry in this list and try installing using synaptic or by entering the following in terminal
```

sudo apt-get install wine
```

---

### Post by edward fish on 2008-07-16
No, but what am I looking for Super??

---

### Post by edward fish on 2008-07-16
edward@Cthulhu:~$ sudo apt-get install wine
[sudo] password for edward:
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
  wine: Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages



Thats what I'm getting, no broken packages where found D=

---

### Post by rraj.be on 2008-07-16
Download wine here and install.

```
[http://winehq.org/site/download-deb]("http://winehq.org/site/download-deb")
```

---

### Post by MaindotC on 2008-07-16
Try using aptitude instead of apt.  It fixed all my broken packages and dependencies per [this thread]("http://ubuntuforums.org/showthread.php?t=804294").

---

### Post by edward fish on 2008-07-16
> **rraj.be said:**
> Download wine here and install.

```
[http://winehq.org/site/download-deb]("http://winehq.org/site/download-deb")
```

Found Wine on the list in Apps -> Add/Remove -> Serach"Wine" 

When trying to install though:

Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

---

### Post by edward fish on 2008-07-16
> **strAlan said:**
> Try using aptitude instead of apt.  It fixed all my broken packages and dependencies per [this thread]("http://ubuntuforums.org/showthread.php?t=804294").

Tada! It appears to have installed! Trying to install a windows program now, I'll update in a few minutes. Thanks!

---

