---
title: "After Jaunty upgrade - package manager broken"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by broomie on 2009-05-03
Hi folks I wonder if you could help me out here:

After successful upgrade to 9.04  Update manager gives me the following:
Version 1.0.6-9ubuntu4.9.04.3: 

  * Update /etc/acpi/powerbtn.sh for KDE 4
    Closes LP: #368497


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

after trying: sudo dpkg --configure -a' 

It fails with:

broomie@broomie-desktop:~$ sudo sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.11.15); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-11-generic:
 linux-restricted-modules-2.6.28-11-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-14-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-14-generic
dpkg: subprocess post-installation script returned error exit status 1


I have tried various offered solutions:

Normally around -

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove

However still stuck


many thanks if anyone can help em out here.



Paul

---

### Post by broomie on 2009-05-05
Bump - Hi folks can anyone help - Jaunty went OK on my dell laptop - but my desktop has this package manger issue.

---

### Post by broomie on 2009-05-06
Bump....

---

### Post by crom.osec on 2009-05-06
please run again
 sudo dpkg --configure -a

and copy here the console output.

---

### Post by broomie on 2009-05-06
Cheers Crom 

here it is but I also found this bug after lots of research

[https://bugs.launchpad.net/ubuntu/+source/live-initramfs/+bug/343735](https://bugs.launchpad.net/ubuntu/+source/live-initramfs/+bug/343735)

"The scipt /usr/share/initramfs-tools/hooks/live in the package live-initramfs contains the following line:
   copy_exec /usr/bin/udevinfo /bin

This should be changed to udevadm. But I'm not sure if there are other scripts that still call udevinfo instead of "udevadm info". If so, these scripts should use udevadm, too "

anyway here is the output...

broomie@broomie-desktop:~$ sudo dpkg --configure -a
[sudo] password for broomie: 
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.11.15); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-11-generic:
 linux-restricted-modules-2.6.28-11-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-14-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-14-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by crom.osec on 2009-05-06
try to create in /bin folder a file called 
 udevinfo

put in it 
[COLOR="BLUE"]#!/bin/sh

udevadm info[/COLOR]

and change its mode to executable:
[COLOR="BLUE"]chmod g+rx,u+wxr /bin/udevinfo[/COLOR]

Then try again.
From what I've know, "udevinfo" was replaced by "udevadm info".

---

### Post by broomie on 2009-05-06
Thanks for that sadly I got :

chopped earlier bit....

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-14-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-14-generic
dpkg: subprocess post-installation script returned error exit status 1
broomie@broomie-desktop:/bin$ ls
bash          bzmore                dd             fusermount  ls          nc              rbash       su               unicode_start
bunzip2       cat                   df             grep        lsmod       nc.traditional  readlink    sync             vdir
busybox       chgrp                 dir            gunzip      mkdir       netcat          rm          tailf            which
bzcat         chmod                 dmesg          gzexe       mknod       netstat         rmdir       tar              zcat
bzcmp         chown                 dnsdomainname  gzip        mktemp      ntfs-3g         rnano       tempfile         zcmp
bzdiff        chvt                  dumpkeys       hostname    more        ntfs-3g.probe   run-parts   touch            zdiff
bzegrep       cp                    echo           ip          mount       open            sed         true             zegrep
bzexe         cpio                  ed             kbd_mode    mount.orig  openvt          setfont     udevinfo         zfgrep
bzfgrep       dash                  egrep          kill        mountpoint  pidof           setupcon    ulockmgr_server  zforce
bzgrep        date                  false          ld_static   mt          ping            sh          umount           zgrep
bzip2         dbus-cleanup-sockets  fgconsole      ln          mt-gnu      ping6           sh.distrib  umount.orig      zless
bzip2recover  dbus-daemon           fgrep          loadkeys    mv          ps              sleep       uname            zmore
bzless        dbus-uuidgen          fuser          login       nano        pwd             stty        uncompress       znew
broomie@broomie-desktop:/bin$ cat udevinfo
#!/bin/sh

udevadm info
broomie@broomie-desktop:/bin$ 


How odd!!!


Paul

---

### Post by crom.osec on 2009-05-06
try ls -l
and check if has executable flag and root owner.

---

### Post by broomie on 2009-05-06
Crom  - you'll start to hate me soon!

no joy....

 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-14-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-14-generic
dpkg: subprocess post-installation script returned error exit status 1

broomie@broomie-desktop:/bin$ ls -l udevinfo
-rwxrwxrwx 1 root root 24 2009-05-06 12:00 udevinfo

---

### Post by crom.osec on 2009-05-06
yes, is strange (it seems that error message is incomplete).

Have you tried:
 sudo dpkg --force all --configure -a
?

---

### Post by broomie on 2009-05-06
Sadly no joy same issues.... oh dear sorry to be a pain!

sudo dpkg --force all --configure -a


Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: linux-restricted-modules-2.6.28-11-generic: dependency problems, but configuring anyway as you request:
 linux-restricted-modules-2.6.28-11-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
Setting up linux-restricted-modules-2.6.28-11-generic (2.6.28-11.15) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: linux-image-generic: dependency problems, but configuring anyway as you request:
 linux-image-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
Setting up linux-image-generic (2.6.28.11.15) ...
dpkg: linux-restricted-modules-generic: dependency problems, but configuring anyway as you request:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
Setting up linux-restricted-modules-generic (2.6.28.11.15) ...
Setting up linux-generic (2.6.28.11.15) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-14-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-14-generic
dpkg: subprocess post-installation script returned error exit status 1

---

### Post by jdevney on 2009-05-21
Hi there,

I know that this is a somewhat old thread, but I resolved the issue by creating the directory: /usr/bin/udevinfo

The problem went away for me. Not sure if there are any repercussions to doing this though!

JD.

---

### Post by theOtherMarino on 2009-05-21
Hello,

Unfortunately, same problem for me. During the dist-upgrade, "something" went wrong and some linux-restricted-modules-***-generic packages happen to be broken. Here is the result of a dpkg --audit:

```
The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-restricted-modules-2.6.27-9-generic Non-free Linux kernel modules for ve
 linux-restricted-modules-2.6.27-14-generic Non-free Linux kernel modules for v
 linux-restricted-modules-2.6.27-11-generic Non-free Linux kernel modules for v
```

I tried a apt-get update, apt-get upgrade, dpkg --configure -a, a dpkg --remove -a, but even with a --force-all on both, the result is still the same:

```
(Reading database ... 205937 files and directories currently installed.)
Removing linux-restricted-modules-2.6.27-9-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-9-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-9-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
cpio: ./sbin/udevadm: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-9-generic
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-restricted-modules-2.6.27-14-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-14-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-14-generic
cpio: ./sbin/udevadm: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-14-generic
dpkg: error processing linux-restricted-modules-2.6.27-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-restricted-modules-2.6.27-11-generic ...
rmdir: failed to remove `/lib/modules/2.6.27-11-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-11-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
cpio: ./sbin/udevadm: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.27-11-generic
dpkg: error processing linux-restricted-modules-2.6.27-11-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.27-9-generic
 linux-restricted-modules-2.6.27-14-generic
 linux-restricted-modules-2.6.27-11-generic
```

I have a /usr/bin/udevinfo and a /sbin/udevadm (AFAIK ok).

What is confusing is that some files seem missing for the process to complete:

```
rmdir: failed to remove `/lib/modules/2.6.27-9-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-9-generic': No such file or directory

rmdir: failed to remove `/lib/modules/2.6.27-14-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-14-generic': No such file or directory

rmdir: failed to remove `/lib/modules/2.6.27-11-generic/volatile/': No such file or directory
FATAL: Could not open '/boot/System.map-2.6.27-11-generic': No such file or directory
```

I tried to con the system creating empty ones, but nope.

I tried to re-install these three packages... nope.

The system will not boot if these problem remain. Any help appreciated.

Marino

---

### Post by theOtherMarino on 2009-05-21
I've tried the solution given earlier in this thread... 

> try to create in /bin folder a file called
udevinfo

put in it
#!/bin/sh

udevadm info

and change its mode to executable:
chmod g+rx,u+wxr /bin/udevinfo

Nope...

---

### Post by theOtherMarino on 2009-05-21
I tried the solution given earlier regarding initramfs-tool, but on my sytem, there is no "/usr/share/initramfs-tools/hooks/live" file.

There is a "/usr/share/initramfs-tools/hooks/udev" file, ans it contains the right line to copy_exec ... udevadm

Nope again

---

### Post by theOtherMarino on 2009-05-21
an apt-get -f install does not work either...

---

### Post by theOtherMarino on 2009-05-21
I've read tons of threads. Some say the error may be caused by a lack of free space on /boot...

I typed a df -h, but /boot do not show up (?)

Any advice?

---

### Post by theOtherMarino on 2009-05-21
Okay, I got rid of these broken packages error. Have a look to this page : [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-06/msg00483.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-06/msg00483.html)

What I did:

Drop to recovery mode at boot and enter a root terminal.

Run "dpkg --audit" from terminal:

```
The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-restricted-modules-2.6.27-9-generic Non-free Linux kernel modules for ve
 linux-restricted-modules-2.6.27-14-generic Non-free Linux kernel modules for v
 linux-restricted-modules-2.6.27-11-generic Non-free Linux kernel modules for v
```

OK, now you have the list of the broken packages

[LIST]
[*]linux-restricted-modules-2.6.27-9-generic
[*]linux-restricted-modules-2.6.27-11-generic
[*]linux-restricted-modules-2.6.27-14-generic
[/LIST]

Let's go to /var/lib/dpkg/info

```
cd  /var/lib/dpkg/info
```

Let's you the list in which you should find the targeted files corresponding to the broken packages;

```
marino@marino-desktop:/var/lib/dpkg/info$ ls -l ./linux-restricted*.postrm*
-rwxr-xr-x 1 root root 301 2008-06-11 12:55 ./linux-restricted-modules-2.6.22-15-generic.postrm
-rwxr-xr-x 1 root root 301 2008-07-09 18:06 ./linux-restricted-modules-2.6.24-19-generic.postrm
-rwxr-xr-x 1 root root 301 2008-10-10 19:18 ./linux-restricted-modules-2.6.24-21-generic.postrm
-rwxr-xr-x 1 root root 332 2008-10-15 14:44 ./linux-restricted-modules-2.6.27-7-generic.postrm
[COLOR="Red"]-rwxr-xr-x 1 root root 332 2008-11-24 18:25 ./linux-restricted-modules-2.6.27-9-generic.postrm
-rwxr-xr-x 1 root root 338 2009-01-03 17:49 ./linux-restricted-modules-2.6.27-11-generic.postrm
-rwxr-xr-x 1 root root 301 2007-11-02 02:22 ./linux-restricted-modules-2.6.27-14-generic.postrm[/COLOR]
-rwxr-xr-x 1 root root 338 2009-04-03 16:18 ./linux-restricted-modules-2.6.28-11-generic.postrm
-rwxr-xr-x 1 root root 197 2009-04-03 16:17 ./linux-restricted-modules-common.postrm
marino@marino-desktop:/var/lib/dpkg/info$[CODE]

Now, as I don't like hard removals, let's rename the file to ".bak". For each of them, just do:

[CODE]mv ./linux-restricted-modules-2.6.27-9-generic.postrm ./linux-restricted-modules-2.6.27-9-generic.postrm.bak
```

Then, do a dpkg --remove -a. It should run with no errors. Then an apt-get -f install to get broken dependencies -one never knows. A dpkg --audit should have no echo any more.

Yet another day toying with unmastered black magic... Is there a wizard here to tell us about all that?

---

### Post by Timmyson on 2009-06-01
I just figured it out, in my case at least.  I was upgrading from Hardy to Intrepid, and something happened (I was asleep), and it failed. Could not boot Ubuntu, could still boot Windows.

I tried to "recover" and got the error message everyone's talking about
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
```So I dropped to root command line, and when I ran it, I got a really long string of errors culminating in **dpkg** failing.

So, instead of configuring all installed packages (which is what the **-a** switch does, I believe, I tried to configure one of the missing packages:
```
dpkg --configure [some random package]
```It said I was missing a dependent package, so then I tried that one.  Eventually, I got a different error when I tried to install **dbus** (which is described by **synaptic** as an "inter-process messaging system"), saying that it couldn't find or create a particular folder: **/var/run/dbus**. I had another symptom too, **more**, **less**, and **cat** wouldn't run (fortunately Vim was fine, so I could still look at, and edit files), and gave error messages about **dbus** too, I*think.

So I created that directory, ```
mkdir /var/run/dbus
``` (with liberal permissions, just in case), and ran ```
dpkg --configure dbus]
``` and it worked, then I ran ```
dpkg --configure -a
``` and now everything works, and I'm posting from Ubuntu Intrepid.

I hope this helps someone. I feel very clever right now, but I couldn't have done it without this thread getting me thinking along the right lines, thanks guys! (This is also my first time actually contributing, rather than leaching off forums.:D)

---

### Post by apalacheno on 2009-06-04
> **jdevney said:**
> Hi there,

I know that this is a somewhat old thread, but I resolved the issue by creating the directory: /usr/bin/udevinfo

The problem went away for me. Not sure if there are any repercussions to doing this though!

Thanks, that solved it for me as well!

---

### Post by big_lou on 2009-06-28
i've had the same error for three days now. all i've found is 'sudo dpkg --remove --pending' now i can access synaptic but any time i try to install or upgrade i get the same error message. i read some where some one fixed a similar issue by copying some one elses getopt file and replacing their own with it.?.? i dont know what thats about.

---

### Post by big_lou on 2009-06-29
hey< i fixed it. i made the directory they were talking about earlier and dont if that had anything to do with it because immediatly after i ran 
1) sudo dpkg --remove --pending
2)sudo apt-get update 
3)sudo apt-get upgrade
      then it threw some errors at me and requested a reboot- so i did, then i ran the update manager in system>admin and it all went thru ok and havent had a problem since.

---

### Post by alexwalkey on 2010-03-17
> **theOtherMarino said:**
> ```
mv ./linux-restricted-modules-2.6.27-9-generic.postrm ./linux-restricted-modules-2.6.27-9-generic.postrm.bak
```

Then, do a dpkg --remove -a. It should run with no errors. Then an apt-get -f install to get broken dependencies -one never knows. A dpkg --audit should have no echo any more.

Yet another day toying with unmastered black magic... Is there a wizard here to tell us about all that?

Cheers, that did it for me! :D

---

### Post by nemebean on 2010-05-07
> **theOtherMarino said:**
> Okay, I got rid of these broken packages error. Have a look to this page : [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-06/msg00483.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-06/msg00483.html)

[snip]

Yet another day toying with unmastered black magic... Is there a wizard here to tell us about all that?
Just wanted to say thanks for this.  I ran into it during my upgrade to Lucid and was, needless to say, less than pleased to discover that the upgrade had left my system in a highly inconsistent state with some packages upgraded and others not.  And here I thought it was a pretty smooth upgrade.  Turns out that was just because the stuff I was using hadn't actually been. :rolleyes:

Anyway, this did the trick and I'm now waiting for all of the packages that didn't get upgraded to download, and hopefully I'll be in good shape after that.

---

