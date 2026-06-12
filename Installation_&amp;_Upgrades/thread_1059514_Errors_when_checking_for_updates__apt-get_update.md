---
title: "Errors when checking for updates / apt-get update"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by noahTHEpurdy on 2009-02-03
Hi. When I run ```
sudo apt-get update
``` I get the following error. Any ideas?

```
Fetched 499B in 1s (296B/s)
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems

```

---

### Post by noahTHEpurdy on 2009-02-04
Bump?

---

### Post by plucky on 2009-02-04
> **noahTHEpurdy said:**
> Hi. When I run ```
sudo apt-get update
``` I get the following error. Any ideas?

```
Fetched 499B in 1s (296B/s)
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: You may want to run apt-get update to correct these problems

```

See this [link](http://www.winehq.org/download/deb) to install the Wine repository and signature.

and

See this [thread](http://ubuntuforums.org/showthread.php?t=1058580&highlight=GPG+error%3A) or  [link](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories) for adding ppa.launchpad signature

Good Luck

---

### Post by noahTHEpurdy on 2009-02-04
Thanks Plucky. That took care of the Wine issue, but with PPA, I get the following:

```
root@Mjlonir:~# gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg: WARNING: unsafe ownership on configuration file `/home/noah/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```

---

### Post by heatpumpcontrol on 2009-02-04
This [link]("http://ubuntuforums.org/showthread.php?t=1051577&page=2") has the answer... it fixed mine....


if it works please mark as solved so it can help others..

---

### Post by noahTHEpurdy on 2009-02-04
> **heatpumpcontrol said:**
> This [link]("http://ubuntuforums.org/showthread.php?t=1051577&page=2") has the answer... it fixed mine....


if it works please mark as solved so it can help others..

This worked!

For future reference:

```
What you need to do, is the following:

Open gnome-terminal and enter the following:

gpg --keyserver subkeys.pgp.net --recv C71839136CF5CE97
(replace "C71839136CF5CE97" by the code in your error message)

Then enter the following:

gpg --export --armor C71839136CF5CE97 | sudo apt-key add -
(here again, replace "C71839136CF5CE97" by the code in your error message)

Then, to finish off, enter the following:

sudo apt-get update
```

---

### Post by webaake on 2009-02-04
Worked fine here too! Thx!

---

### Post by forger on 2009-02-06
I made a script as well, it fixes the ppa link (needs an extra 'ppa' in the link):
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

