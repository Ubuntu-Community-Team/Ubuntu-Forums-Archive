---
title: "Trying to install Brother HL-1440 Printer..."
date: 2012-11-04
forum: Hardware
---

### Post by undeadmechanic on 2012-11-04
Trying to install a Brother HL-1440 Laser Printer on my headless 12.04 system and having all sorts of fun.

According to packages.ubuntu.com, the package containing the driver for my printer is "brother-lpr-drivers-laser1". This is the result I get when I run apt-get install brother-lpr-drivers-laser1.

```
david@server:~$ sudo apt-get install brother-lpr-drivers-laser1
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 brother-lpr-drivers-laser1 : Depends: brother-lpr-drivers-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```Ok, so I try sudo apt-get -f install and get:

```
david@server:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-23-generic linux-headers-3.2.0-31-generic
  linux-headers-3.2.0-23 linux-headers-3.2.0-31 linux-headers-3.2.0-29
  linux-headers-3.2.0-29-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  brother-lpr-drivers-common brother-lpr-drivers-laser1
The following NEW packages will be installed:
  brother-lpr-drivers-common
The following packages will be upgraded:
  brother-lpr-drivers-laser1
1 upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
6 not fully installed or removed.
Need to get 0 B/786 kB of archives.
After this operation, 1,376 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 136874 files and directories currently installed.)
Unpacking brother-lpr-drivers-common (from .../brother-lpr-drivers-common_1.0.0-4-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/brother-lpr-drivers-common_1.0.0-4-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/Brother/inf/brPrintList', which is also in package brother-lpr-drivers-laser1 1.0.0-3-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/brother-lpr-drivers-common_1.0.0-4-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Suggestions, please? The machine is used as a torrent slave and network storage. I use Samba for the network fileshares and would like to use it for sharing this printer as well.

Thanks for any assistance,
David

---

### Post by undeadmechanic on 2012-11-05
Got it. Apparently I screwed up when I downloaded and installed the .deb pkg from brother. Removed it with dpkg, then ran apt-get -f install and everything worked beautifully.

Sometimes it's the dumbest things... :/

---

### Post by pdc on 2012-11-06
so I see the -f option is

> [COLOR="Red"]-f, --fix-broken[/COLOR]
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. 

If packages are specified, these have to completely correct the problem.

The option is sometimes necessary when running APT for the first time; APT itself does not allow broken package dependencies to exist on a
system. 

It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(1) or dpkg --remove to eliminate some of the offending packages). 

Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.


---

