---
title: "32-bit CUPS missing"
date: 2023-07-26
forum: Hardware
---

### Post by techguy378 on 2023-07-26
I just did a clean install of Ubuntu 23.04. I'm trying to set up a Xerox Phaser 6000b printer which only has 32-bit Linux drivers. At a terminal window when I run the command "sudo apt install libcupsimage2:i386" I get an error message that the package cannot be found. The other packages I need such as 32-bit ncurses6 install without issue. For some reason I cannot install 32-bit CUPS. How do I fix this? I was able to install 32-bit CUPS in Ubuntu 22.10 and 22.04.

---

### Post by Xian on 2023-07-26
You can download package from [https://packages.ubuntu.com/lunar/i386/libcupsimage2/download](https://packages.ubuntu.com/lunar/i386/libcupsimage2/download)

Then install:

$ sudo apt-get install /path/to/libcupsimage2_2.4.2-3ubuntu2.2_i386.deb

---

### Post by techguy378 on 2023-07-27
> **Xian said:**
> You can download package from [https://packages.ubuntu.com/lunar/i386/libcupsimage2/download](https://packages.ubuntu.com/lunar/i386/libcupsimage2/download)

Then install:

$ sudo apt-get install /path/to/libcupsimage2_2.4.2-3ubuntu2.2_i386.deb

Thanks for the tip, however this leads to dependency hell. For some reason the Ubuntu developers have removed all of the dependencies for that package as well. Also, Lunar Lobster really, really does not want 32-bit packages to be installed on a 64-bit system. I had to use the --force-architecture option with dpkg to even attempt to install the libcupsimage2_2.4.2-3ubuntu2.2_i386.deb package. This was not required in Ubuntu 22.10.

---

### Post by #&amp;thj^% on 2023-07-27
This is the old way:
```
sudo dpkg --add-architecture i386
```
update
```
sudo apt update
```
I downloaded to my "Downloads so"
```
sudo apt install '/home/me/Downloads/libcupsimage2_2.4.2-3ubuntu2.2_i386.deb' 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'libcupsimage2:i386' instead of '/home/me/Downloads/libcupsimage2_2.4.2-3ubuntu2.2_i386.deb'
The following packages were automatically installed and are no longer required:
  linux-headers-6.2.0-24 linux-headers-6.2.0-24-generic
  linux-image-6.2.0-24-generic linux-modules-6.2.0-24-generic
  linux-modules-extra-6.2.0-24-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libavahi-client3:i386 libavahi-common3:i386 libcap2:i386 libcups2:i386
  libdbus-1-3:i386 libgcrypt20:i386 libgmp10:i386 libgnutls30:i386
  libgpg-error-l10n libgpg-error0:i386 libhogweed6:i386 liblz4-1:i386
  libnettle8:i386 libp11-kit0:i386 libsystemd0:i386 libtasn1-6:i386
Suggested packages:
  rng-tools:i386 gnutls-bin:i386
Recommended packages:
  libcupsfilters2:i386
The following NEW packages will be installed:
  libavahi-client3:i386 libavahi-common3:i386 libcap2:i386 libcups2:i386
  libcupsimage2:i386 libdbus-1-3:i386 libgcrypt20:i386 libgmp10:i386
  libgnutls30:i386 libgpg-error-l10n libgpg-error0:i386 libhogweed6:i386
  liblz4-1:i386 libnettle8:i386 libp11-kit0:i386 libsystemd0:i386
  libtasn1-6:i386
0 upgraded, 17 newly installed, 0 to remove and 1 not upgraded.
Need to get 3,597 kB of archives.
After this operation, 9,905 kB of additional disk space will be used.
Do you want to continue? [Y/n] 


```
Here is what installed:
```
Get:1 http://us.archive.ubuntu.com/ubuntu lunar-updates/main i386 libcap2 i386 1:2.66-3ubuntu2.1 [31.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libgpg-error0 i386 1.46-1 [77.0 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libgcrypt20 i386 1.10.1-3ubuntu1 [503 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libgmp10 i386 2:6.2.1+dfsg1-1.1ubuntu1 [265 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu lunar/main i386 liblz4-1 i386 1.9.4-1 [68.7 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libsystemd0 i386 252.5-2ubuntu3 [413 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libdbus-1-3 i386 1.14.4-1ubuntu1 [220 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libnettle8 i386 3.8.1-2 [182 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libhogweed6 i386 3.8.1-2 [203 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libp11-kit0 i386 0.24.1-2ubuntu1 [235 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libtasn1-6 i386 4.19.0-2 [43.4 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu lunar/main i386 libgnutls30 i386 3.7.8-5ubuntu1 [1,004 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu lunar-updates/main i386 libavahi-common3 i386 0.8-6ubuntu1.23.04.1 [25.5 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu lunar-updates/main i386 libavahi-client3 i386 0.8-6ubuntu1.23.04.1 [30.0 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu lunar-updates/main i386 libcups2 i386 2.4.2-3ubuntu2.2 [283 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu lunar-updates/main i386 libcupsimage2 i386 2.4.2-3ubuntu2.2 [6,724 B]
Get:17 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 libgpg-error-l10n all 1.46-1 [6,960 B]
Fetched 3,597 kB in 4s (827 kB/s)              
Selecting previously unselected package libcap2:i386.
(Reading database ... 549588 files and directories currently installed.)
Preparing to unpack .../00-libcap2_1%3a2.66-3ubuntu2.1_i386.deb ...
Unpacking libcap2:i386 (1:2.66-3ubuntu2.1) ...
Selecting previously unselected package libgpg-error0:i386.
Preparing to unpack .../01-libgpg-error0_1.46-1_i386.deb ...
Unpacking libgpg-error0:i386 (1.46-1) ...
Selecting previously unselected package libgcrypt20:i386.
Preparing to unpack .../02-libgcrypt20_1.10.1-3ubuntu1_i386.deb ...
Unpacking libgcrypt20:i386 (1.10.1-3ubuntu1) ...
Selecting previously unselected package libgmp10:i386.
Preparing to unpack .../03-libgmp10_2%3a6.2.1+dfsg1-1.1ubuntu1_i386.deb ...
Unpacking libgmp10:i386 (2:6.2.1+dfsg1-1.1ubuntu1) ...
Selecting previously unselected package liblz4-1:i386.
Preparing to unpack .../04-liblz4-1_1.9.4-1_i386.deb ...
Unpacking liblz4-1:i386 (1.9.4-1) ...
Selecting previously unselected package libsystemd0:i386.
Preparing to unpack .../05-libsystemd0_252.5-2ubuntu3_i386.deb ...
Unpacking libsystemd0:i386 (252.5-2ubuntu3) ...
Selecting previously unselected package libdbus-1-3:i386.
Preparing to unpack .../06-libdbus-1-3_1.14.4-1ubuntu1_i386.deb ...
Unpacking libdbus-1-3:i386 (1.14.4-1ubuntu1) ...
Selecting previously unselected package libnettle8:i386.
Preparing to unpack .../07-libnettle8_3.8.1-2_i386.deb ...
Unpacking libnettle8:i386 (3.8.1-2) ...
Selecting previously unselected package libhogweed6:i386.
Preparing to unpack .../08-libhogweed6_3.8.1-2_i386.deb ...
Unpacking libhogweed6:i386 (3.8.1-2) ...
Selecting previously unselected package libp11-kit0:i386.
Preparing to unpack .../09-libp11-kit0_0.24.1-2ubuntu1_i386.deb ...
Unpacking libp11-kit0:i386 (0.24.1-2ubuntu1) ...
Selecting previously unselected package libtasn1-6:i386.
Preparing to unpack .../10-libtasn1-6_4.19.0-2_i386.deb ...
Unpacking libtasn1-6:i386 (4.19.0-2) ...
Selecting previously unselected package libgnutls30:i386.
Preparing to unpack .../11-libgnutls30_3.7.8-5ubuntu1_i386.deb ...
Unpacking libgnutls30:i386 (3.7.8-5ubuntu1) ...
Selecting previously unselected package libavahi-common3:i386.
Preparing to unpack .../12-libavahi-common3_0.8-6ubuntu1.23.04.1_i386.deb ...
Unpacking libavahi-common3:i386 (0.8-6ubuntu1.23.04.1) ...
Selecting previously unselected package libavahi-client3:i386.
Preparing to unpack .../13-libavahi-client3_0.8-6ubuntu1.23.04.1_i386.deb ...
Unpacking libavahi-client3:i386 (0.8-6ubuntu1.23.04.1) ...
Selecting previously unselected package libcups2:i386.
Preparing to unpack .../14-libcups2_2.4.2-3ubuntu2.2_i386.deb ...
Unpacking libcups2:i386 (2.4.2-3ubuntu2.2) ...
Selecting previously unselected package libcupsimage2:i386.
Preparing to unpack .../15-libcupsimage2_2.4.2-3ubuntu2.2_i386.deb ...
Unpacking libcupsimage2:i386 (2.4.2-3ubuntu2.2) ...
Selecting previously unselected package libgpg-error-l10n.
Preparing to unpack .../16-libgpg-error-l10n_1.46-1_all.deb ...
Unpacking libgpg-error-l10n (1.46-1) ...
Setting up libgpg-error0:i386 (1.46-1) ...
Setting up liblz4-1:i386 (1.9.4-1) ...
Setting up libavahi-common3:i386 (0.8-6ubuntu1.23.04.1) ...
Setting up libgcrypt20:i386 (1.10.1-3ubuntu1) ...
Setting up libcap2:i386 (1:2.66-3ubuntu2.1) ...
Setting up libnettle8:i386 (3.8.1-2) ...
Setting up libgmp10:i386 (2:6.2.1+dfsg1-1.1ubuntu1) ...
Setting up libp11-kit0:i386 (0.24.1-2ubuntu1) ...
Setting up libtasn1-6:i386 (4.19.0-2) ...
Setting up libgpg-error-l10n (1.46-1) ...
Setting up libhogweed6:i386 (3.8.1-2) ...
Setting up libsystemd0:i386 (252.5-2ubuntu3) ...
Setting up libgnutls30:i386 (3.7.8-5ubuntu1) ...
Setting up libdbus-1-3:i386 (1.14.4-1ubuntu1) ...
Setting up libavahi-client3:i386 (0.8-6ubuntu1.23.04.1) ...
Setting up libcups2:i386 (2.4.2-3ubuntu2.2) ...
Setting up libcupsimage2:i386 (2.4.2-3ubuntu2.2) ...
Processing triggers for libc-bin (2.37-0ubuntu2) ...

```
And:
```
apt policy libcupsimage2
libcupsimage2:
  Installed: 2.4.2-3ubuntu2.2
  Candidate: 2.4.2-3ubuntu2.2
  Version table:
 *** 2.4.2-3ubuntu2.2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu lunar-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.4.2-3ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages

```

Easy Peazy

---

### Post by deadflowr on 2023-07-27
it will be installable directly from the repos once you run the add-architecture command and run apt update.
No need to download it separately.

It's not dependency hell, it's the system does not know anything about i386 packages, so ignores those until you add the arch and run an update.

---

### Post by techguy378 on 2023-07-27
Thanks everyone for the help. Leave it to the Ubuntu devs to make stupid decisions. Ubuntu is the only major Linux distro to disable multilib by default.

---

