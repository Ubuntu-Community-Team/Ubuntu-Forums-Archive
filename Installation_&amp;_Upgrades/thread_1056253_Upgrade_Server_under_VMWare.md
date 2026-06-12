---
title: "Upgrade Server under VMWare"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by nesnub on 2009-01-31
Hello,

I am having a lot of trouble with Ubuntu Server. Now I don't know if it will be limited to Ubuntu or if other distros will be a problem too.

Basically, I download Ubuntu Server LTS iso. I install into a new VM, 2-cpu, 1GB of RAM, the classic stuff. During install I select additional software: LAMP and OpenSSH. Keyboard US, all the rest of the stuff is all default...

I boot up. I do:
sudo apt-get update
>> Starts updating, then fails (corrupted) on a package list it is downloading. I repeat a couple times and eventually it gets it right.
sudo apt-get upgrade
>> Starts downloading linux-image-2.6.24.23-server. Downloads seems to work. Then starts installing. Then it starts failing:


```
Preparing to replace linux-image-2.6.24-23-server 2.6.24-23.46 (using .../linux-image-2.6.24-23-server_2.6.24-23.48_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-23-server ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-23-server_2.6.24-23.48_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-23-server_2.6.24-23.48_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have done nothing between the initial reboot and the apt-get.

I have repeated this over and over again in VMWare. I have no problem with any versions of Windows in VMs on that server. I am running VMWare Workstation latest version, on a host Windows XP 64.

Anyone has any ideas? I have messed around with this for far too long. Anyone has any suggestions of Linux distos that might work better?

---

### Post by rbhkamal on 2009-01-31
Normally I would've suggested fedora but lately they have been very careless in releasing new code... 

Fedora 8 reached end of life but it's very solid and has very few bugs. I've installed many 64bit and 32bit servers with that distro and had (almost) no problems... stripping it down from all the services and GUI is pain through....

---

### Post by nesnub on 2009-01-31
Humm, thanks. I have done some reading and as you say, the biggest disadvantage is that there is no GUI-less version. 

It's strange that several people have suggested to me that Ubuntu server may not be the best distribution for a serious server, but after some searching I fail to find a "serious" (big) distribution that offers a GUI-less version and does not cost money.

I would really rather find the problem with the Ubuntu Server install than finding another distribution I have to spend a lot of time stripping down. :-/

---

### Post by nesnub on 2009-01-31
So I have been trying to understand a bit better the problem. I tried all possible permutations of the Virtual hardware I could think oh, 1 vs 2 cpu, less RAM, more RAM, disable USB2.0 acceleration etc... Nothing.

However, I used aptitude to download the deb file that is always breaking.:

```
sudo aptitude download linux-image-2.6.24-23-server
```

I then did a md5sum of the file. Deleted the downloaded file. Then did another download using aptitude followed by another md5sum.

Well that's the problem. Different md5sum. So it seems like somehow the file gets corrupted while downloading. I am VERY surprised as I would have assumed apt would do a md5 of the packages it downloads, seems like the least of thing...

Anyway, has anyone ever heard of VMWare somehow corrupting the file transfers?

This seems odd, since I run a web server on one of my Ubuntu VMs with the same problem, but the web server runs fine, no problem viewing the pages etc.

This is all just so strange, what gives.

PLEASE, any ideas?

Thanks

---

### Post by slakkie on 2009-01-31
> **nesnub said:**
> 
It's strange that several people have suggested to me that Ubuntu server may not be the best distribution for a serious server, but after some searching I fail to find a "serious" (big) distribution that offers a GUI-less version and does not cost money.

I would really rather find the problem with the Ubuntu Server install than finding another distribution I have to spend a lot of time stripping down. :-/
Debian? FreeBSD, OpenBSD, NetBSD (aka the BSD family).


But back to your problem could you tell me which version you are running: uname -a and lsb_release -a output is enough.

---

### Post by nesnub on 2009-01-31
Yeah, the BSD direction scares me a bit :-)

Here is the output:

```
Linux webserver2 2.6.24-23-server #1 SMP Thu Nov 27 19:19:15 UTC 2008 i686 GNU/Linux


No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy

```

---

### Post by slakkie on 2009-01-31
From the uname -a i would say you are already at the desired kernel image..

---

### Post by nesnub on 2009-02-01
Interesting, seems like the apt is trying to upgrade me from *.46 to *.48. Is that a minor revision number?

I would assume this upgrade is necessary since I just installed ubuntu from the CD I downloaded, so I doubt it would be up to date...

And in any case, this situation (corrupted download) arises on another Ubuntu Server box I maintain...

---

### Post by slakkie on 2009-02-03
Yes, that is a minor revision, I personally pin my kernel, and only upgrade it when I upgrade my complete OS (eg 8.04.x to 8.10).


Put this in /etc/apt/preferences and you will pin all these packages to version 2.6.24.19.21 (which I currently use).
 
```

Package: linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic linux-server linux-image-server
Pin: version 2.6.24.19.21
Pin-Priority: 1001

```

This won't help you with your problem though... I'm currently busy with something else, but I could check if I have the same problem as you if I don't pin the kernel packages.

---

