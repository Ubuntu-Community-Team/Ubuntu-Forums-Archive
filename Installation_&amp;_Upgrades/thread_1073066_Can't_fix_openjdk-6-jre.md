---
title: "Can't fix openjdk-6-jre"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-02-17
I keep trying to upgrade my machine and I get the following errors:
```

Reading package lists... Done
root@amd64-desktop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b11-2ubuntu2.1) but 6b11-2ubuntu2 is installed
E: Unmet dependencies. Try using -f.
root@amd64-desktop:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openjdk-6-jre-headless openjdk-6-jre-lib
Suggested packages:
  sun-java6-fonts ttf-bengali-fonts ttf-kannada-fonts ttf-oriya-fonts
  ttf-telugu-fonts ttf-wqy-zenhei
Recommended packages:
  ca-certificates-java
The following packages will be upgraded:
  openjdk-6-jre-headless openjdk-6-jre-lib
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
Need to get 0B/27.2MB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 210028 files and directories currently installed.)
Preparing to replace openjdk-6-jre-lib 6b11-2ubuntu2 (using .../openjdk-6-jre-lib_6b11-2ubuntu2.1_all.deb) ...
Unpacking replacement openjdk-6-jre-lib ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-lib_6b11-2ubuntu2.1_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar')
Preparing to replace openjdk-6-jre-headless 6b11-2ubuntu2 (using .../openjdk-6-jre-headless_6b11-2ubuntu2.1_amd64.deb) ...
Unpacking replacement openjdk-6-jre-headless ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-headless_6b11-2ubuntu2.1_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar')
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-lib_6b11-2ubuntu2.1_all.deb
 /var/cache/apt/archives/openjdk-6-jre-headless_6b11-2ubuntu2.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@amd64-desktop:~#

```

I've googled this and I've tried the following which don't work:
```

apt-get install -f
apt-get --configure -a

```
I also tried using Synaptic, Software Updater, and aptitude but still having a problem with these packages.  How can I resolve this?

---

### Post by Partyboi2 on 2009-02-17
Open a terminal and
```
sudo apt-get clean
sudo apt-get upgrade
```

---

### Post by MaindotC on 2009-02-18
You are right - I am wrong.  I ran the commands you listed and although there were still errors, apt eventually fixed everything.

---

