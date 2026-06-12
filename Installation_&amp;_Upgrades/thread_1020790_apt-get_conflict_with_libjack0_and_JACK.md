---
title: "apt-get conflict with libjack0 and JACK"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by martron88 on 2008-12-24
Hi all,

I just upgraded a number of packages and one that's refusing to finish is libjack0.  So now apt-get is broken so I can't really install anything else until this is resolved.  Basically libjack0 won't upgrade because it's trying to overwrite a file contained in the package jack-audio-connection-kit.  This is probably happening because I installed a custom .deb a while ago that included some firewire stuff.

Anyway, I'm stuck at having this broken repository and would like to disable the upgrade of libjack or remove jack-audio-connection kit so that libjack0 can install properly.  Here's what happens when I run "sudo apt-get -f install":

```
(Reading database ... 247530 files and directories currently installed.)
Preparing to replace libjack0 1.8+svn3036ubuntu1 (using .../libjack0_1.9.0-0ubuntu1_amd64.deb) ...
Unpacking replacement libjack0 ...
dpkg: error processing /var/cache/apt/archives/libjack0_1.9.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libjack.so.0.1.0', which is also in package jack-audio-connection-kit
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace jackd 1.8+svn3036ubuntu1 (using .../jackd_1.9.0-0ubuntu1_amd64.deb) ...
Unpacking replacement jackd ...
dpkg: error processing /var/cache/apt/archives/jackd_1.9.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/jackd', which is also in package jack-audio-connection-kit
Errors were encountered while processing:
 /var/cache/apt/archives/libjack0_1.9.0-0ubuntu1_amd64.deb
 /var/cache/apt/archives/jackd_1.9.0-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm not so up on apt-get syntax so if anyone has suggestions on how to force this to work right I'd appreciate suggestions.

Thanks

---

### Post by Partyboi2 on 2008-12-24
To remove jack-audio-connection-kit in a terminal
```
sudo apt-get remove jack-audio-connection-kit
``` or
```
sudo apt-get remove --purge jack-audio-connection-kit
``` to remove all the config files as well.Then
```
sudo apt-get -f install
``````
sudo apt-get update && sudo apt-get upgrade
```If you still have a problem then try usig

---

### Post by marcelmasi on 2009-01-15
I have the same problem. However, when I enter

```
sudo apt-get remove jack-audio-connection-kit
```

I get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  jackd: Depends: jack-audio-connection-kit (>= 1.8+svn3036ubuntu1) but it is not going to be installed
  libjack0: Depends: jack-audio-connection-kit (>= 1.8+svn3036ubuntu1) but it is not going to be installed
  libjack0.100.0-0: Depends: libjack0 (>= 1.9.0-0ubuntu1) but 1.8+svn3036ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Typing ```
sudo apt-get -f install
``` gives me this (I typed "y" twice):

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libjack0
The following packages will be upgraded:
  libjack0
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/87.9kB of archives.
After this operation, 233kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libjack0
Install these packages without verification [y/N]? Y
(Reading database ... 317726 files and directories currently installed.)
Preparing to replace libjack0 1.8+svn3036ubuntu1 (using .../libjack0_1.9.0-0ubuntu1_i386.deb) ...
Unpacking replacement libjack0 ...
dpkg: error processing /var/cache/apt/archives/libjack0_1.9.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libjack.so.0.1.0', which is also in package jack-audio-connection-kit
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libjack0_1.9.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone help me how to get rid of this conflict?
Thanks a lot!

---

### Post by Partyboi2 on 2009-01-15
try to override the file.
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libjack0_1.9.0-0ubuntu1_i386.deb
``` then

```
sudo apt-get -f install
```

---

