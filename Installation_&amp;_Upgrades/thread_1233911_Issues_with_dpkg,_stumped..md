---
title: "Issues with dpkg, stumped."
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by ashesh0326 on 2009-08-07
Hey guys,

I'm running Ubuntu 8.04 on my machine and here's my problem:

While updating last night using the package manager GUI, my internet played up and some packages got missing. Foolishly enough, I continued with the installation of the packages, and the installation was aborted midway.

I got this message as the error message: 
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Now, I immediately rushed to a terminal and ran the command as told to, but no go, instead, I got this message:

```
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-24-generic:
 linux-ubuntu-modules-2.6.24-24-generic depends on linux-image-2.6.24-24-generic; however:
  Package linux-image-2.6.24-24-generic is not installed.
dpkg: error processing linux-ubuntu-modules-2.6.24-24-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1

```

Now, the thing is, I can't install anything. I keep getting the first error message on trying to install. 

Can anyone help please?

Thanks!

---

### Post by Partyboi2 on 2009-08-07
Hi, looks like you have ran out of space. Can you post the output to
```
df -h
```

---

### Post by ashesh0326 on 2009-08-07
Hi, thanks for replying.

Here's the output:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              19G  2.9G   15G  17% /
varrun                248M  284K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   64K  248M   1% /dev
devshm                248M   48K  248M   1% /dev/shm
lrm                   248M   38M  210M  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda6              16M   13M  2.2M  85% /boot
/dev/sda8             128G   10G  112G   9% /home
/dev/sdb1              45G   26G   17G  61% /home/indiashare/barracuda1
/dev/sdb2              29G   23G  5.0G  83% /home/indiashare/barracuda2
gvfs-fuse-daemon       19G  2.9G   15G  17% /home/ashesh/.gvfs

```

---

### Post by Partyboi2 on 2009-08-07
Open Synaptic Package Manager and do a search for 'linux-image' and remove all the old kernels that you don't need, keep your current one and the one before you current one as backup.
After you have removed the ones you don't need run
```
sudo dpkg --configure -a
```Another option if you still have problems with not enough space,  is to use gparted to increase the size of your /boot partition.

---

### Post by ashesh0326 on 2009-08-07
Synaptic Package Manager fails to run. 

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by Partyboi2 on 2009-08-07
try
```
sudo apt-get -f install
``` and then see if you are able to open up synaptic.
If not post the output to
```
dpkg --list | grep linux-image
```

---

### Post by ashesh0326 on 2009-08-07
sudo apt-get -f install throws:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

and 

dpkg --list | grep linux-image

```
ii  linux-image-2.6.24-19-generic              2.6.24-19.34                                         Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.19.21                                         Generic Linux kernel image

```

---

### Post by Partyboi2 on 2009-08-07
I would suggest booting a Ubuntu live cd and using gparted (System>Admin>Partition Editor) and use the resize option to shrink down your /dev/sda7 by about 500mb to 1 gig. Then resize your /boot (/dev/sda6) to use that extra space. Then reboot into Ubuntu and run
```
sudo dpkg --configure -a
```Because your /dev/sda6 (/boot) is only 16 mb you will keep having this problem unless you increase the size of your /dev/sda6 ( /boot) partition.

---

### Post by ashesh0326 on 2009-08-07
Is there any alternative to that? I mean, can't I run gparted from somewhere else?

---

### Post by Partyboi2 on 2009-08-07
> **ashesh0326 said:**
> Is there any alternative to that? I mean, can't I run gparted from somewhere else?
If you don't have a Ubuntu cd you can go to the [[COLOR=Blue]gparted[/COLOR]]("http://gparted.sourceforge.net/download.php") site and download gparted for cd or usb. Or have I miss understood?

---

### Post by ashesh0326 on 2009-08-08
okay, will do that and let you know how things go from there.

Thank you so much!

---

### Post by ashesh0326 on 2009-08-09
Thanks guys, worked like a charm!

---

