---
title: "No pubkey"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by sideaway on 2009-04-08
I've tried a few fixes, can someone help me with this?

[I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE



W: Failed to fetch [http://ppa.launchpad.net/netbook-remix-team/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/netbook-remix-team/ubuntu/dists/intrepid/Release)  



W: Some index files failed to download, they have been ignored, or old ones used instead.[/I]

---

### Post by Partyboi2 on 2009-04-08
Hi, you can add the key by opening a terminal (Applications>Accessories>Terminal) and type or paste
```
gpg --keyserver keyserver.ubuntu.com --recv 3F2A5EE4B796B6FE
gpg --export --armor 3F2A5EE4B796B6FE | sudo apt-key add - 
```
then
```
sudo apt-get update
```

---

### Post by sideaway on 2009-04-08
Hey there, thanks for that, it didn't work. But i tried it just with the last eight digits and that did. So cheers for the help though!

---

### Post by cigtoxdoc on 2009-04-09
I tried suggestions and got the following error messages:

john@john-desktop:~$ gpg --keyserver keyserver.ubuntu.com --recv 247D1CFF
gpg: WARNING: unsafe permissions on configuration file `/home/john/.gnupg/gpg.conf'
gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/john/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error


What do I do next?

John

---

### Post by upchucky on 2009-04-09
cig, 

you may want to create your own thread, it is better that way.

it looks like some configuration files are in your home directory, how they got there is a good question. this is very bad because if they are in the home directory then the system could be brought down by error.


the permissions you are seeing are protecting you from running an install that is vulnerable.

normally I would not suggest this but to be safe a re-install is in order, If you have files you want to keep back them up to a cd, usb drive, flash drive, network.

get gparted live bootable cd, delete the ubuntu partiton, and re-install ubuntu.

---

