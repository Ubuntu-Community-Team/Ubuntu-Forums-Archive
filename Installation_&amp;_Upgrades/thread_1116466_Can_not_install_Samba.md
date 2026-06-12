---
title: "Can not install Samba"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by jondgls on 2009-04-04
When I attempt installation through Synaptic Package Manager I receive the following error:
samba:
  Depends: samba-common (=2:3.2.3-1ubuntu3.4) but 2:3.2.3-1ubuntu3.5 is to be installed

When I attempt installation through Terminal I receive the following error:
XXXX@XXXXXX:~$ sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 2:3.2.3-1ubuntu3.4) but 2:3.2.3-1ubuntu3.5 is to be installed
  smbfs: Depends: samba-common (= 2:3.2.3-1ubuntu3.4) but 2:3.2.3-1ubuntu3.5 is to be installed
E: Broken packages

Not sure how to resolve this. I have tried using a custom source.list for the repositories. Didn't work.

Synaptic Package Manager shows samba-common 2:3.2.3-1ubuntu3.5 is already installed.

Any help is appreciated.

---

### Post by bertolo on 2009-04-04
you can use ntfs that is already installed by default.
try remove samba common and try again.
gl

---

### Post by inobe on 2009-04-04
do not install from synaptic, follow the instructions from the ubuntu documentation.

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

if you don't know what to do' start a new thread in networking and wireless forum.

---

### Post by jondgls on 2009-04-04
> **inobe said:**
> do not install from synaptic, follow the instructions from the ubuntu documentation.

[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)


Followed the instructions from the ubuntu documentation. I receive the error msg described in step 5:

"STEP 5 - You may receive a message which says Sharing services are not installed. If this happens, ensure that the two checkboxes in the message box are checked and press Install services. Sharing service support will then be downloaded and installed; this may take a while."

When i try to install services I receive the following error msg:

"Could not apply changes! Fix broken packages first."

I am unable to continue through the ubuntu documentation beyond step 5.

---

### Post by inobe on 2009-04-05
open synaptic package manager and click edit' then click "fix broken packages"

---

### Post by Partyboi2 on 2009-04-05
> **jondgls said:**
> When I attempt installation through Synaptic Package Manager I receive the following error:
samba:
  Depends: samba-common (=2:3.2.3-1ubuntu3.4) but 2:3.2.3-1ubuntu3.5 is to be installed

When I attempt installation through Terminal I receive the following error:
XXXX@XXXXXX:~$ sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 2:3.2.3-1ubuntu3.4) but 2:3.2.3-1ubuntu3.5 is to be installed
  smbfs: Depends: samba-common (= 2:3.2.3-1ubuntu3.4) but 2:3.2.3-1ubuntu3.5 is to be installed
E: Broken packages

Not sure how to resolve this. I have tried using a custom source.list for the repositories. Didn't work.

Synaptic Package Manager shows samba-common 2:3.2.3-1ubuntu3.5 is already installed.

Any help is appreciated.
Open up Synaptic and search for samba-common and see if you can force an earlier version by selecting samba-common and going to Package>Force version.

---

### Post by jondgls on 2009-04-05
Samba install issue resolved:

1. Using Synaptic Package Manager I removed completely "samba-common" which was pre-installed with ubuntu 8.10.
2. Using Synaptic Package  Manager I then installed the "Samba" package which includes "samba-common".

3. I was then able to follow the ubuntu documentation found here:
[https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

Thank you all for your assistance! :p

JonDgls

---

