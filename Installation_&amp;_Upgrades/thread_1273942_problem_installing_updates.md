---
title: "problem installing updates"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by boogey on 2009-09-24
I appologize for double posting this but no one might see it in the "general help" section.


update manager wants me to install:

kdelibs5 and kdelibs5-data

if I try I get this:

"you have 1 broken package on your system"

and: An error occurred:
E: /var/cache/apt/archives/kdelibs5-data_4%
3a4.0.5-0ubuntu1~hardy3_all.deb: failed in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/kdelibs5_4%3a4.0.5-0ubuntu1~hardy3_i386.deb: failed in buffer_write(fd) (10, ret=-1)

I tried to fix the broken package in the Synaptic Package Manager with "Fix broken packages" but after applying I get the same error message as above. details of the failure are:

/var/cache/apt/archives/kdelibs5-data_4%3a4.0.5-0ubuntu1~hardy3_all.deb
/var/cache/apt/archives/kdelibs5_4%3a4.0.5-0ubuntu1~hardy3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
dpkg: dependency problems prevent configuration of kde4libs-bin:
kde4libs-bin depends on kdelibs5 (= 4:4.0.5-0ubuntu1~hardy3); however:
Package kdelibs5 is not installed.
dpkg: error processing kde4libs-bin (--configure):
dependency problems - leaving unconfigured
Setting up network-manager (0.6.6-0ubuntu5.8.04.2) ...
* Reloading system message bus config...
...done.
* Restarting network connection manager NetworkManager
/usr/sbin/NetworkManager: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory
dpkg: error processing network-manager (--configure):
subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of network-manager-gnome:
network-manager-gnome depends on network-manager (>= 0.6.5); however:
Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
dependency problems - leaving unconfigured


anyone any idea how to fix this dependency problem?
thanks

---

### Post by rreese6 on 2009-09-24
try this: 
```

sudo updatedb
sudo dpkg --configure -a
```

---

### Post by boogey on 2009-09-24
> **rreese6 said:**
> try this: 
```

sudo updatedb
sudo dpkg --configure -a
```

thank you rreese6, unfortunately following your advice I get this:

> dpkg: dependency problems prevent configuration of kde4libs-bin:
 kde4libs-bin depends on kdelibs5 (= 4:4.0.5-0ubuntu1~hardy3); however:
  Package kdelibs5 is not installed.
dpkg: error processing kde4libs-bin (--configure):
 dependency problems - leaving unconfigured
Setting up network-manager (0.6.6-0ubuntu5.8.04.2) ...
 * Reloading system message bus config...                                [ OK ] 
 * Restarting network connection manager NetworkManager                         /usr/sbin/NetworkManager: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kde4libs-bin
 network-manager
 network-manager-gnome

---

### Post by rreese6 on 2009-09-24
How about this:```


sudo apt-get install -f
```

I have seen this before on my machine a couple years ago...just having memory issues ;)

We will get this fixed.

---

### Post by boogey on 2009-09-24
> **rreese6 said:**
> How about this:```


sudo apt-get install -f
```

I have seen this before on my machine a couple years ago...just having memory issues ;)

We will get this fixed.

thanks again, but isn't this basically the command that checks for upgrades (similar opening my update manager) which is exactly when the problems start...meaning: after that I get the error message.

---

### Post by rreese6 on 2009-09-24
yes but it forces things to install.

---

### Post by boogey on 2009-09-24
I now tried:
```
 sudo apt-get autoremove
```
and get this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kde4libs-bin: Depends: kdelibs5 (= 4:4.0.5-0ubuntu1~hardy3) but it is not installed
E: Unmet dependencies. Try using -f.


then I try the
```
sudo apt-get -f install
```
 and get this:
>  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl kdelibs5 glest-data kde-icons-oxygen
  libsoprano4 kdelibs5-data libstreamanalyzer0 libphonon4 libstreams0
  kdebase-runtime-data libxerces27 kde4libs-bin
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdelibs5 kdelibs5-data
The following NEW packages will be installed:
  kdelibs5 kdelibs5-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/11.3MB of archives.
After this operation, 43.4MB of additional disk space will be used.
Do you want to continue [Y/n]? 
I confirm and get:
> (Reading database ... 285665 files and directories currently installed.)
Unpacking kdelibs5-data (from .../kdelibs5-data_4%3a4.0.5-0ubuntu1~hardy3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdelibs5-data_4%3a4.0.5-0ubuntu1~hardy3_all.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/kde4/share/kde4/apps/katepart/syntax/euphoria.xml': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking kdelibs5 (from .../kdelibs5_4%3a4.0.5-0ubuntu1~hardy3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kdelibs5_4%3a4.0.5-0ubuntu1~hardy3_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/kde4/lib/kde4/katepart.so': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5-data_4%3a4.0.5-0ubuntu1~hardy3_all.deb
 /var/cache/apt/archives/kdelibs5_4%3a4.0.5-0ubuntu1~hardy3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by boogey on 2009-09-24
oh and yeah, I tried the
```
 sudo apt-get install -f
```

after which I get the initial error message.

thanks again, I really appreciate that you waste your time on this!

---

### Post by rreese6 on 2009-09-24
Man I am tired.. I just saw that your error says 
"No space left on device" Is your hard drive full?

---

### Post by boogey on 2009-09-24
no worries the "no space left" just came after I ran autoremove. This is what my harddrive looks like:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.4G  962M  305M  76% /
varrun                252M  128K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   40M  212M  16% /lib/modules/2.6.24-24-386/volatile
/dev/sda8              60G   26G   31G  46% /home
/dev/sda6             4.6G  4.6G     0 100% /usr
/dev/sda7             2.8G  827M  1.9G  31% /var


Is that the problem then? can I clean it up somehow?

---

### Post by boogey on 2009-09-24
ok, I decided to clean up as good as possible:

I removed al residual config packages with the Synaptic Package Manager
then did:

```
 sudo apt-get autoclean
```
and:
```
 sudo apt-get install localepurge
```
to remove all unnecessary local data

I still have:
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.4G  961M  307M  76% /
varrun                252M  128K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   40M  212M  16% /lib/modules/2.6.24-24-386/volatile
/dev/sda8              60G   26G   31G  46% /home
/dev/sda6             4.6G  4.5G     0 100% /usr
/dev/sda7             2.8G  826M  1.9G  31% /var


but the update manager is not telling me anymore that there are updates available and I have no broken files either!
If that's good or bad.... I don't know. :?:

---

### Post by rreese6 on 2009-09-24
This is the problem:


```
/dev/sda6 4.6G 4.5G 0 100% /usr
```

you don't have any more room in the /usr folder
you need to adjust your partitions to make more room for it.
Use gparted from a Live CD to make sda6 larger.

---

### Post by boogey on 2009-09-24
> **rreese6 said:**
> This is the problem:


```
/dev/sda6 4.6G 4.5G 0 100% /usr
```

you don't have any more room in the /usr folder
you need to adjust your partitions to make more room for it.
Use gparted from a Live CD to make sda6 larger.

forgive me rreese6 as this might be a dumb question, but how do I exactly do it:

just ```
sudo apt-get install gparted
```

or do I have to download an iso file like
> gparted-live-0.4.6-1.iso from [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")?
and if I have burned the iso image on a cd, what are my next steps? can I basically just resize sda7 and add the space to sda6? How?
Sorry about the load of questions and thanks again, I really appreciate your help... guess I should have posted this in the newbie section...

---

### Post by rreese6 on 2009-09-24
I actually like to use the gparted iso
burn the disk and boot it up
then when garted try to figure out where you can get more room from resizing other partitions. do that
then run a resize on sda6

---

### Post by boogey on 2009-09-25
very dumb question:

I run gparted freed and freed some 4 GiB (right now it's unallocated) but seem not be able to add it to sda6... how do I get there?

---

