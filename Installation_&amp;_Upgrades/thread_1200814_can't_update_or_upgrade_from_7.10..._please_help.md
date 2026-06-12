---
title: "can't update or upgrade from 7.10... please help"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by shankscomp on 2009-06-30
Each time I run apt-get update, I get many errors.  below are the errors.  I know it's at EOL, but is there any way I can still upgrade this live machine without knocking it down???  I know this is an older system, but I currently have a couple of website running on it and a few other things.  Was hoping to find a simplier way to upgrade this machine.

Please any suggestions?

Tim

```

Get:1 http://download.webmin.com sarge Release.gpg [189B]
Ign http://download.webmin.com sarge/contrib Translation-en_US
Hit http://download.webmin.com sarge Release
Err http://download.webmin.com sarge Release

Get:2 http://download.webmin.com sarge Release [4367B]
Ign http://security.ubuntu.com gutsy-security Release.gpg
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US
Ign http://download.webmin.com sarge Release
Ign http://download.webmin.com sarge/contrib Packages
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com gutsy-security Release
Hit http://download.webmin.com sarge/contrib Packages
Ign http://security.ubuntu.com gutsy-security/main Packages
Ign http://de.archive.ubuntu.com gutsy Release.gpg
Ign http://de.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://de.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://de.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://de.archive.ubuntu.com gutsy/multiverse Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Packages
Ign http://security.ubuntu.com gutsy-security/main Sources
Ign http://security.ubuntu.com gutsy-security/restricted Sources
Ign http://security.ubuntu.com gutsy-security/universe Packages
Ign http://de.archive.ubuntu.com gutsy-updates Release.gpg
Ign http://de.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://de.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://de.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://de.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://de.archive.ubuntu.com gutsy Release
Ign http://security.ubuntu.com gutsy-security/universe Sources
Ign http://security.ubuntu.com gutsy-security/multiverse Packages
Ign http://security.ubuntu.com gutsy-security/multiverse Sources
Err http://security.ubuntu.com gutsy-security/main Packages
  404 Not Found
Err http://security.ubuntu.com gutsy-security/restricted Packages
  404 Not Found
Ign http://de.archive.ubuntu.com gutsy-updates Release
Err http://security.ubuntu.com gutsy-security/main Sources
  404 Not Found
Ign http://de.archive.ubuntu.com gutsy/main Packages
Ign http://de.archive.ubuntu.com gutsy/restricted Packages
Ign http://de.archive.ubuntu.com gutsy/main Sources
Ign http://de.archive.ubuntu.com gutsy/restricted Sources
Ign http://de.archive.ubuntu.com gutsy/universe Packages
Ign http://de.archive.ubuntu.com gutsy/universe Sources
Ign http://de.archive.ubuntu.com gutsy/multiverse Packages
Ign http://de.archive.ubuntu.com gutsy/multiverse Sources
Err http://security.ubuntu.com gutsy-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com gutsy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com gutsy-security/universe Sources
  404 Not Found
Err http://security.ubuntu.com gutsy-security/multiverse Packages
  404 Not Found
Err http://security.ubuntu.com gutsy-security/multiverse Sources
  404 Not Found
Ign http://de.archive.ubuntu.com gutsy-updates/main Packages
Ign http://de.archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://de.archive.ubuntu.com gutsy-updates/main Sources
Ign http://de.archive.ubuntu.com gutsy-updates/restricted Sources
Ign http://de.archive.ubuntu.com gutsy-updates/universe Packages
Ign http://de.archive.ubuntu.com gutsy-updates/universe Sources
Ign http://de.archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://de.archive.ubuntu.com gutsy-updates/multiverse Sources
Err http://de.archive.ubuntu.com gutsy/main Packages
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy/restricted Packages
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy/main Sources
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy/restricted Sources
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy/universe Packages
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy/universe Sources
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy/multiverse Packages
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy/multiverse Sources
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy-updates/main Packages
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy-updates/restricted Packages
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy-updates/main Sources
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy-updates/restricted Sources
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy-updates/universe Packages
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy-updates/universe Sources
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy-updates/multiverse Packages
  404 Not Found [IP: 141.76.2.130 80]
Err http://de.archive.ubuntu.com gutsy-updates/multiverse Sources
  404 Not Found [IP: 141.76.2.130 80]
Fetched 4556B in 2s (1579B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 141.76.2.130 80]
Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz  404 Not Found [IP: 141.76.2.130 80]
Reading package lists... Done
W: GPG error: http://download.webmin.com sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D97A3AE911F63C51
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@server1:~#

```

---

### Post by mcduck on 2009-06-30
This should help: [https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

edit: This could be useful information as well: [https://help.ubuntu.com/community/UpgradeNotes#Unsupported%20%28Obsolete%29%20Versions]("https://help.ubuntu.com/community/UpgradeNotes#Unsupported%20%28Obsolete%29%20Versions")

---

### Post by shankscomp on 2009-06-30
I jump down to where it says upgrading 7.10 to 8.04, type in the do-release-upgrade, but it errors out saying command not found...  I tried doing install update-manager-core, but that gives me basically the same errors as before.  I also tried copying over the source.list, and changing everything from edgy to gutsy, but that doesn't help either.

I seriously would like to not have to wipe the machine, since I do have some shopping cart websites running on it for our local county fair and another town festival.  I'd hate to have to go through the headache of setting up ISPConfig again.

Please advise...  Yes I did go through the two links that was suggested.

Tim

---

### Post by mcduck on 2009-06-30
> **shankscomp said:**
> I jump down to where it says upgrading 7.10 to 8.04, type in the do-release-upgrade, but it errors out saying command not found...  I tried doing install update-manager-core, but that gives me basically the same errors as before.  I also tried copying over the source.list, and changing everything from edgy to gutsy, but that doesn't help either.

I seriously would like to not have to wipe the machine, since I do have some shopping cart websites running on it for our local county fair and another town festival.  I'd hate to have to go through the headache of setting up ISPConfig again.

Please advise...  Yes I did go through the two links that was suggested.

Tim

I think you'll have to do the previous step (or at least part of it) first to change your sources.list to use the repository made for old releases, as 7.10 repositories are already closed. (in other words change the server to old-releases.ubuntu.com)

That's pretty much all I can tell to help, I've never done that as tend to update to latest release couple of weeks before they are released..

---

