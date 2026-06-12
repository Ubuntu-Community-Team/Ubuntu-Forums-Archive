---
title: "Software Index is Broken"
date: 2008-08-23
forum: General Help
---

### Post by jtizmo on 2008-08-23
When I try to start synaptic, I get:

> E: The package dcp130ccupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

This doesn't seem to help...
> justin@justin-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package dcp130ccupswrapper needs to be reinstalled, but I can't find an archive for it.


At one time, I was trying to install a cupswrapper for my Brother printer.  The installation did not go as planned and I decided to start over.  I removed as much as I could regarding cups from synaptic only to end up not even being able to update, repair, or remove any packages.  I have tried to reinstall but am still stuck:

> justin@justin-desktop:~/Desktop$ sudo dpkg -i dcp130ccupswrapper-1.0.1-1.i386.deb 
Selecting previously deselected package dcp130ccupswrapper.
(Reading database ... 118040 files and directories currently installed.)
Preparing to replace dcp130ccupswrapper 1.0.0-10 (using dcp130ccupswrapper-1.0.1-1.i386.deb) ...
/var/lib/dpkg/info/dcp130ccupswrapper.prerm: 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: not found
dpkg: error processing dcp130ccupswrapper-1.0.1-1.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/dcp130ccupswrapper.postinst: 3: /usr/local/Brother/Printer/dcp130c/cupswrapper/cupswrapperdcp130c: not found
cp: cannot stat `/usr/share/cups/model/brdcp130c.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dcp130ccupswrapper-1.0.1-1.i386.deb


Any help would be appreciated.  Thanks!

---

### Post by unutbu on 2008-08-23
According to 
[https://answers.launchpad.net/ubuntu/+source/gnome-utils/+question/7350](https://answers.launchpad.net/ubuntu/+source/gnome-utils/+question/7350) (See last post)
[https://answers.launchpad.net/synaptic/+question/8337](https://answers.launchpad.net/synaptic/+question/8337) (See last post)

the quick and dirty way seems to be 

```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-20080823   # backup just to be safe
gksu gedit /var/lib/dpkg/status
```
Delete the stanza having to do with dcp130ccupswrapper

Then perhaps
```

sudo apt-get update

```
and try synaptic again.

If any files related to dcp130ccupswrapper are still installed on your system, install the package and then remove the package. This should then remove those files.

---

### Post by colobix on 2008-08-23
If you've borked your system with a dependency or version conflict (which is why it can't upgrade - the wrong package conflicting packages or wrong version or multiple versions installed somewhere), then you have two ways out.

The clever way - you can figure out which package(s) are causing the problem and resolve the conflict, thereby breaking the logjam. This may be time-consuming. Start by comparing the output between the following two commands to get clues:
Code:

sudo apt-get -sv dist-upgrade
sudo apt-get -sv dselect-upgrade

The brute force way - install one of the meta-packages and upgrade.
Code:

sudo apt-get install ubuntu-desktop && sudo apt-get dist-upgrade

Since your system is probably customized (you removed a meta-package, for example) this approach might undo some of your customization, and might break any specialty packages or .debs that were relying on specific dependencies that you just upgraded from.

---

### Post by jtizmo on 2008-08-23
> **unutbu said:**
> According to 
[https://answers.launchpad.net/ubuntu/+source/gnome-utils/+question/7350](https://answers.launchpad.net/ubuntu/+source/gnome-utils/+question/7350) (See last post)
[https://answers.launchpad.net/synaptic/+question/8337](https://answers.launchpad.net/synaptic/+question/8337) (See last post)

the quick and dirty way seems to be 

```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-20080823   # backup just to be safe
gksu gedit /var/lib/dpkg/status
```
Delete the stanza having to do with dcp130ccupswrapper

Then perhaps
```

sudo apt-get update

```
and try synaptic again.

If any files related to dcp130ccupswrapper are still installed on your system, install the package and then remove the package. This should then remove those files.
That removed the error.  Hopefully I will have time to try to set up the printer before I go to school.  I may have to check out colobix's suggestion.

---

### Post by jtizmo on 2008-08-24
OK, that worked.  The printer is set up!

Thanks!

---

