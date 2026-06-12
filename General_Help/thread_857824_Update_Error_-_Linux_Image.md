---
title: "Update Error - Linux Image"
date: 2008-07-12
forum: General Help
---

### Post by emerc01 on 2008-07-12
I have been getting the following error message when updating for about a month:

E: linux-image-2.6.24-19-generic: subprocess post-installation script returned error exit status 2
E: linux-ubuntu-modules-2.6.24-19-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-19-generic: dependency problems - leaving unconfigured

I've change repositories and it doesn't work.

How do I solve this?

---

### Post by rraj.be on 2008-07-12
Your boot partition may be full.
Try this.

Type the following in terminal to check it

```
df -h
```

If so type the following

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg --configure -a
```

---

### Post by emerc01 on 2008-07-12
thanks, my boot directory was full.

results from df -h

/dev/sda3             4.8G  3.5G  1.1G  77% /
varrun                375M  108K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
udev                  375M   48K  375M   1% /dev
devshm                375M   12K  375M   1% /dev/shm
/dev/sda1              92M   86M  978K  99% /boot
/dev/sda4              32G   13G   18G  43% /home


then i ran sudo apt-get clean.

results from sudo apt-get update:

vanir@vanir:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy Release.gpg               
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/main Translation-en_US    
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US 
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security Release.gpg
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy Release
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates Release
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security Release          
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/main Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/restricted Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/universe Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/main Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/restricted Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/universe Sources  
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/multiverse Packages
Get:1 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-updates/multiverse Sources [2279B]
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/main Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/main Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/universe Sources
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) hardy-security/multiverse Sources
Fetched 1B in 2s (0B/s)  
W: Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2](http://tw.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.


results from sudo apt-get upgrade:

vanir@vanir:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-image-generic
 linux-generic
 linux-restricted-modules-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


how do i fix this??  thanks for your help.

---

### Post by drs305 on 2008-07-12
Your /boot partition is getting pretty full so it would be a good idea to make some room. This is normally done by removing older kernels. You should keep at least two - the one you are using plus one you used previously. 

If you go into, synaptic, you can search for "linux-image" and it will show all the kernels on your system. It is safe to remove older ones. The files will have names such as "linux-image-2.6.24-14" or "linux-image-2.6.24.14-generic". Make sure you keep your current kernel, which you can check with:
```
uname -r
```

---

