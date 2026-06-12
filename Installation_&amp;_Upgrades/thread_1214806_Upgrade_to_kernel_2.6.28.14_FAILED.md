---
title: "Upgrade to kernel 2.6.28.14 FAILED"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by kebabbaro on 2009-07-16
Hi everybody,

upgrade manager tried to install the latest kernel 2.6.28.14.18 but the process failed and because of that now i have one broken dependency on my system.

Tried to fix the issue with both Synaptic and the Terminal but i was not successful.
With the terminal i ran the "sudo apt-get -f install" command, with synaptic i tried to reinstall the broken package which is "linux-restricted-modules-generic version 2.6.28.14.18

Here's the error message:

E: /var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./lib/linux-restricted-modules/2.6.28-14-generic/wl/wlc_hybrid.o_shipped_x86_64')


Here's what is reported in the Details view:

(Reading database ... 145628 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.28-14-generic (from .../linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing  /var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during './lib/linux-restricted-modules/2.6.28-14-generic/wl/wlc_hybrid.o_shipped_x86_64')
Errors were encountered while processing:   
/var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.    Trying to recover:
dpkg: dependecy problems prevent configuration of linux-restricted-modules-generic:
   linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-14-generic; however:
   Package linux-restricted-modules-2.6.28-14-generic is not installed.
dpkg: error processing  linux-restricted-modules-generic (--configure):
   dependency problem - leaving unconfigured
dpkg: dependency problem prevent configuration of linux-generic:
   linux-generic depends on linux-restricted-modules-generic (=2.6.28.14.18); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing  linux-generic (--configure):
 dependency problems - leaving unconfigured
Error were encountered while processing
 linux-restriced-modules-generic
 linux-generic

Of course at startup the kernel 2.6.28-14 boot process fails, giving a message like this

crc problem
process halted

How can i fix the problem? OS is jaunty 9.04 desktop amd64, and I am a non-geek and linux newbie ;)

KEB

---

### Post by dstew on 2009-07-16
I saw this is a few places:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb
```But honestly, I do not know what exactly the problem is, or why this would work. I just saw a few people who said it solved a problem similar to yours. These are the web pages:

[http://biostat.mc.vanderbilt.edu/wiki/Main/DependFixDebian](http://biostat.mc.vanderbilt.edu/wiki/Main/DependFixDebian)
[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

---

### Post by kebabbaro on 2009-07-17
> **dstew said:**
> I saw this is a few places:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb
```But honestly, I do not know what exactly the problem is, or why this would work. I just saw a few people who said it solved a problem similar to yours. These are the web pages:

[http://biostat.mc.vanderbilt.edu/wiki/Main/DependFixDebian](http://biostat.mc.vanderbilt.edu/wiki/Main/DependFixDebian)
[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

Tried that but here's the terminal output:

(Reading database ... 145628 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.28-14-generic (from .../linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./lib/linux-restricted-modules/2.6.28-14-generic/wl/wlc_hybrid.o_shipped_x86_64')
Errors were encountered while processing:
 /var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb

So thank you very much for your help but i'm still left with this problem
 
Anyone care to give me some more fix :confused:

KEB

---

### Post by kebabbaro on 2009-07-17
> **kebabbaro said:**
> Tried that but here's the terminal output:

(Reading database ... 145628 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.28-14-generic (from .../linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./lib/linux-restricted-modules/2.6.28-14-generic/wl/wlc_hybrid.o_shipped_x86_64')
Errors were encountered while processing:
 /var/cache/apt/archives/linux-restricted-modules-2.6.28-14-generic_2.6.28-14.18_amd64.deb

So thank you very much for your help but i'm still left with this problem
 
Anyone care to give me some more fix :confused:

KEB
Up

---

### Post by cyberfin on 2009-08-02
Bumping... have exactly the same problem. Same config too (Jaunty, Desktop, AMD64)

Any help or pointers very appreciated!

Thanks.

---

### Post by Soul-Sing on 2009-08-02
Do you have proposed or backports sources enabled?
If so disable them, and run a ```
sudo apt-get update
```,
and ```
sudo apt-get upgrade
```

---

### Post by cyberfin on 2009-08-02
Nope had both disabled.

Are you suggesting a rollback?

---

### Post by Soul-Sing on 2009-08-02
cyberfin try:
```
sudo apt-get install linux-restricted-modules-generic `uname -r`
```
whats the outcome of this command?

---

### Post by cyberfin on 2009-08-02
Output as follows:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  python-reportlab libestools1.2 python-renderpm python-sqlalchemy
  python-reportlab-accel
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-restricted-modules-2.6.28-14-generic (2.6.28-14.19) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-14-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.28-14-generic
dpkg: error processing linux-restricted-modules-2.6.28-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-14-generic; however:
  Package linux-restricted-modules-2.6.28-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.14.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-restricted-modules-2.6.28-14-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Soul-Sing on 2009-08-02
> gzip: stdout: No space left on device
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```

---

### Post by cyberfin on 2009-08-02
Duh... should learn to read through my own messages.

Thanks, discovered that my /boot is 98% full.

Yey.

(Rolls up sleves)

Thanks for the help!

---

### Post by Soul-Sing on 2009-08-02
succes!:D

---

### Post by kebabbaro on 2009-08-16
> **leoquant said:**
> Do you have proposed or backports sources enabled?
If so disable them, and run a ```
sudo apt-get update
```,
and ```
sudo apt-get upgrade
```

FYI my problem was exactly that: this kernel upgrade is a "proposed one", or a pre-release.

So I just disabled  the proposed and backports sources , cleaned the system and the problem was solved.

Regards

---

