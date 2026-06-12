---
title: "[SOLVED] OpenAFS client will not compile correctly with module assistant"
date: 2008-11-22
forum: General Help
---

### Post by lbthrice on 2008-11-22
Hi all,

I am very frustrated that there is an issue with the module-assistant finding target kernel headers that should exist on my system.
Since I have never compiled kernel headers before I do not even know how to begin to troubleshoot this.

My goal is to install an open afs client on my Hardy 8.04 distro 

Here is what I run:

```
sudo apt-get install openafs-modules-source openafs-client
 openafs-krb5 krb5-config krb5-user module-assistant

cd /usr/src

sudo m-a auto-install openafs
```

here is what I get from module assistant:

```
Bad luck, the kernel headers for the target kernel version could
 not be found and you did not specify other valid kernel headers to use.

However, you can install the header files for your kernel which are
 provided by the linux-headers-2.6.24-21-generic package. For most
 modules packages, these files are perfectly sufficient without having
 the original kernel source.  To install the package, run the PREPARE
 command from the main menu, or on the command line:

module-assistant prepare 

or 

apt-get install linux-headers-2.6.24-21-generic
```

all packages that 
module-assistant prepare installs are up-to-date on my machine
linux-headers-2.6.24-21-generic is up-to-date

here is more info:

```
uname -a
``` gives:

```
Linux LisaLappy 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
```

and

```
ls /usr/src
``` gives:

```
kqemu-1.3.0~pre11
linux
linux-headers-2.6.24-21
linux-headers-2.6.24-21-386
linux-headers-2.6.24-21-generic
linux-headers-2.6.24-21-server
lzma.tar.bz2
modules
openafs-modules-2.6.24.3_1.4.6.dfsg1-2+2.6.24.3-10.00.Custom_i386.deb
openafs.tar.gz
rpm
```

any help will be greeted with gratitude.
this issue has proven to be far beyond my understanding of the system.

Thanks!

---

### Post by lbthrice on 2008-11-26
rtfm

simply point the module-assistant to the kernel headers in /usr/src
with the "--kernel-dir" argument.

```
sudo module-assistant --kernel-dir /usr/src/linux-headers-2.6.24-21-generic auto-build openafs-modules
```

---

