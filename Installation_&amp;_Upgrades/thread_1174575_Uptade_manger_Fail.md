---
title: "Uptade manger Fail"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by stuart221 on 2009-05-31
when I run update manager it fails to update all so when I run apt-get update. I get this and nothing happens.
stuart@stuart-desktop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/main Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/main Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) intrepid-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-backports/main Packages
Reading package lists... Done

---

### Post by mcduck on 2009-05-31
That's all that's supposed to happen when you run "sudo apt-get update". It updates the information about available packages and their versions.

You need to run "sudo apt-get upgrade" to download & install new package versions.

---

### Post by stuart221 on 2009-05-31
I have done that now I am getting this massage 
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mcduck on 2009-05-31
> **stuart221 said:**
> I have done that now I am getting this massage 
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

You have added two extra repositories but didn't add their GPG keys.

While the error is not anything serious, you can get rid of it if you add the encryption keys. [https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")

Also you seem to have one repository that's for Hardy (8.10). You shouldn't mix repositories of different Ubuntu versions.

---

### Post by stuart221 on 2009-05-31
how do i delete this.

---

### Post by stuart221 on 2009-05-31
did it

---

