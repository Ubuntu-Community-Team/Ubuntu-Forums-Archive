---
title: "Error with public key"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-04-18
I have been trying to install OpenOffice 3 through the software sources and followed instructions I found when browsing but, when I tried to reload I got this error message;

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

Any ideas - please keep it simple as I am not brilliant with Linux yet...

Ta.

Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems

---

### Post by kelsey.chris on 2009-04-18
I have the same issue, and found this:

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304")

---

### Post by kelsey.chris on 2009-04-18
Got it.  I had the wrong permissions on my home folder.  It gave me the error: gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/chris/.gnupg/gpg.conf

solved it by running:

 sudo chmod -R 700 /home/chris

(unless your home folder is also called /chris, you will have to adjust your name accordingly)

Hope this helps

---

### Post by dougalkerr on 2009-04-18
Tried sudo apt-get but, didn't work. See ammended thread text with copied error advice.

---

### Post by kelsey.chris on 2009-04-18
I've been reading the man pages for gpg.  It's humbling.

You could try opening a terminal and running:

gpg --keyserver keyserver.ubuntu.com --refresh-keys

If that doesn't work, have a look at Leo Albert Jackson Jr.'s step-by-step instructions on this page:

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304")

You would have to modify the commands you are copy/pasting into your terminal screen to match the keys that you are missing.

Any idea what you did to make it lose its keys?

---

