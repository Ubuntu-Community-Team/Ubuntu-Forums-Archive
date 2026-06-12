---
title: "Update/Upgrade troubles - unmet dependencies and failed connections"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by eekrazyk on 2009-03-31
Posted in the Kubuntu forums, too.

I am attempting to update, but I'm receiving a bunch of errors.

```
$ sudo apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg
Hit http://security.ubuntu.com hardy-security Release.gpg
Hit http://archive.canonical.com hardy Release.gpg
Hit http://ppa.launchpad.net hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://archive.canonical.com hardy Release
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Hit http://ppa.launchpad.net hardy Release
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
```


```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kde4libs-bin: Depends: kdelibs5 (= 4:4.0.3-0ubuntu5.2) but it is not installed
  kdebase-runtime: Depends: kde-icons-oxygen (>= 4:4.0.3-0ubuntu2) but it is not installed
                   Depends: kdelibs5 (>= 4:4.0.3-0ubuntu3) but it is not installed
  kdebase-runtime-bin-kde4: Depends: kde-icons-oxygen but it is not installed
                            Depends: kdelibs5 (>= 4:4.0.3-0ubuntu3) but it is not installed
  kdebase-workspace-bin: Depends: kde-icons-oxygen but it is not installed
                         Depends: kdelibs5 (>= 4:4.0.3-0ubuntu1) but it is not installed
  kdm-kde4: Depends: kde-icons-oxygen but it is not installed
            Depends: kdelibs5 (>= 4:4.0.3-0ubuntu1) but it is not installed
  ksysguard-kde4: Depends: kde-icons-oxygen but it is not installed
                  Depends: kdelibs5 (>= 4:4.0.3-0ubuntu1) but it is not installed
  libkrosspython0: Depends: kde-icons-oxygen but it is not installed
                   Depends: kdelibs5 (>= 4:4.0.3-0ubuntu2) but it is not installed
  libkrossruby0: Depends: kde-icons-oxygen but it is not installed
                 Depends: kdelibs5 (>= 4:4.0.3-0ubuntu2) but it is not installed
  libplasma1: Depends: kde-icons-oxygen but it is not installed
              Depends: kdelibs5 (>= 4:4.0.3-0ubuntu1) but it is not installed
  superkaramba-kde4: Depends: kde-icons-oxygen but it is not installed
                     Depends: kdelibs5 (>= 4:4.0.3-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
```


Attempting it with the -f option:

```
$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  kde-icons-oxygen kdelibs5
The following packages have been kept back:
  awn-manager bind9-host dnsutils language-support-writing-en libbind9-30 libisccc30 libisccfg30 linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic openssh-client openssh-server ssl-cert
The following packages will be upgraded:
  ....  lots of packages listed here ....
369 upgraded, 2 newly installed, 0 to remove and 14 not upgraded.
10 not fully installed or removed.
Need to get 72.1MB/380MB of archives.
After this operation, 85.8MB of additional disk space will be used.
Do you want to continue [Y/n]?
Err http://us.archive.ubuntu.com hardy/universe kde-icons-oxygen 4:4.0.3-0ubuntu2
  Connection failed
Err http://us.archive.ubuntu.com hardy-updates/main openoffice.org-core 1:2.4.1-1ubuntu2.1
  Connection failed
Err http://security.ubuntu.com hardy-security/main openoffice.org-core 1:2.4.1-1ubuntu2.1
  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kdebase-runtime/kde-icons-oxygen_4.0.3-0ubuntu2_all.deb  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.4.1-1ubuntu2.1_i386.deb  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```


Hmmm.  Attempted update again with --fix-missing:

```
$ sudo apt-get -f install --fix-missing
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kde-icons-oxygen kdelibs5
Suggested packages:
  kdebase
Recommended packages:
  pmount kfreebsd-gnu hurd
The following NEW packages will be installed:
  kde-icons-oxygen kdelibs5
0 upgraded, 2 newly installed, 0 to remove and 383 not upgraded.
10 not fully installed or removed.
Need to get 45.4MB/53.4MB of archives.
After this operation, 85.0MB of additional disk space will be used.
Do you want to continue [Y/n]? yes
Err http://us.archive.ubuntu.com hardy/universe kde-icons-oxygen 4:4.0.3-0ubuntu2
  Connection failed
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/k/kdebase-runtime/kde-icons-oxygen_4.0.3-0ubuntu2_all.deb  Connection failed
Unable to correct missing packages.
E: Aborting install.
```

What the heck?  A straight up update wihtout any options works....

```
$ sudo apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg
Hit http://security.ubuntu.com hardy-security Release.gpg
Hit http://archive.canonical.com hardy Release.gpg
Hit http://ppa.launchpad.net hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Hit http://ppa.launchpad.net hardy Release
Hit http://archive.canonical.com hardy Release
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
```

I am behind a proxy and I have set the environment variables.  Updating has worked until very recently.

Anyone have any ideas??

---

