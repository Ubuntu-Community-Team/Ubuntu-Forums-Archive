---
title: "changing kernels and Nvidia drivers!!!!"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by reformedgeek on 2005-05-17
Ok, 
so here's the deal.  I want to change my current kernel (2.6.10-386) to the more appropriate ~-k7 kernel as i have a 1900+ athlon xp.  Now i've read that there's minimal increase in performance, but still, i'd like to see for myself.
When i install the new kernel, my nvidia drivers die.  I've tried apt-get remove nvidia* and then reinstall them, but no dice.
I tried installing them with the nvidia installer, but it keeps screaming that it doesn't have the kernel sources.
Being a fairly big n00b, and having only dabbled with RH and Gentoo and am not sure what to do.


WHAT DO I DO NOW?
any help would be good.
thanks

---

### Post by alastair on 2005-05-17
It's probably because your "architecture" has changed i.e. i386 -> K7.

Make sure you also update the modules e.g.
From : 

linux-restricted-modules-2.6.10-5-386

to :

linux-restricted-modules-2.6.10-5-k7

or similar.

You might also need the K7 linux kernel headers :

linux-headers-2.6.10-5-k7

---

### Post by Xian on 2005-05-17
Yeah, its those restricted modules that you need.
Just install this via apt (or synaptic):

```
$ sudo apt-get install linux-restricted-modules-k7
```

That package will always depend on the latest k7 restricted modules.
Use the matching package for the headers too:

```
$ sudo apt-get install linux-headers-k7
```

---

### Post by reformedgeek on 2005-05-18
Tried it, and it worked!
GENIUS!
brilliant.  now i have k7 support. and my nvidia drivers back! nice one!
thanks so much

s

---

### Post by Vin_L on 2005-05-23
I am trying to update my Kernel from 386 to k7 as well and was met with Error code 1 and other errors sorry they went away and I don't know where they are stored (if they are stored in a log file somewhere. I am a total noob. I tried the commands above and this is what I got

Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-k7 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-image-k7: Depends: linux-image-2.6.10-5-k7 but it is not going to be installed
  linux-restricted-modules-2.6.10-5-k7: Depends: linux-image-2.6.10-5-k7 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@Main:/home/vin # apt-get install linux-headers-k7
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-headers-k7: Depends: linux-headers-2.6.10-5-k7 but it is not going to be installed
  linux-image-k7: Depends: linux-image-2.6.10-5-k7 but it is not going to be installed
  linux-restricted-modules-2.6.10-5-k7: Depends: linux-image-2.6.10-5-k7 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Can anyone help me learn.

---

### Post by Xian on 2005-05-23
What is the output when you run the following command:

```
$ sudo apt-get -f install
```

---

### Post by Vin_L on 2005-05-23
Thanks for your reply. This is what I get with the -f install command


root@Main:/home/vin # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.10-5-k7
Suggested packages:
  lilo linux-doc-2.6.10 linux-source-2.6.10
The following NEW packages will be installed:
  linux-image-2.6.10-5-k7
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
4 not fully installed or removed.
Need to get 0B/16.7MB of archives.
After unpacking 48.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 82228 files and directories currently installed.)
Unpacking linux-image-2.6.10-5-k7 (from .../linux-image-2.6.10-5-k7_2.6.10-34.1_ i386.deb) ...
The directory /lib/modules/2.6.10-5-k7 still exists. Continuing as directed.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.10-5-k7_2.6.10-34 .1_i386.deb (--unpack):
 failed in buffer_write(fd) (8, ret=-1): backend dpkg-deb during `./boot/vmlinuz -2.6.10-5-k7': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /vmlinuz-2.6.10-5-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Main:/home/vin #

Thanks

Vin

---

### Post by Xian on 2005-05-23
[QUOTE=Vin_L]Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Main:/home/vin #[/QUOTE]

Issue the following commands in a terminal:
```
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb
$ sudo dpkg --configure -a
$ sudo apt-get -f install
```

---

### Post by Vin_L on 2005-05-23
I get this upon 1st command:

root@Main:/home/vin # dpkg -i --force-overwrite /var/cache/apt/archives/linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb
(Reading database ... 82228 files and directories currently installed.)
Unpacking linux-image-2.6.10-5-k7 (from .../linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb) ...
The directory /lib/modules/2.6.10-5-k7 still exists. Continuing as directed.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb (--install):
 failed in buffer_write(fd) (8, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.10-5-k7': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /vmlinuz-2.6.10-5-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb
root@Main:/home/vin #

Do I need to free up hdd space somewhere? My root directory is 4.7G but I don't know how to check for available space.

---

### Post by Xian on 2005-05-23
[QUOTE=Vin_L] failed in buffer_write(fd) (8, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.10-5-k7': No space left on device

Do I need to free up hdd space somewhere? My root directory is 4.7G but I don't know how to check for available space.[/QUOTE]
Yes, that is an odd error message. 
To check for drive space enter this command:

```
$ df -h
```
If you do have the space needed then it might be worth the time to try that 'dpkg -i --force-overwrite' command again on your next boot and see if you get a different result.

---

### Post by Vin_L on 2005-05-23
Okay, This is good I am learning more every day thank you for that command. It looks like there is only 733M on the root. I am sure I could ditch some apps but I don't know what I am doing yet so instead I will try partition magic from my Windoze boot and enlarge the partition. Funny thing is I did this the other day and obviously enlarged the wrong partition because my boot partition is 8.2G. It looks like that is where its choking though so I am going to assume I'll be all set once I get the space.

Thanks

Vin

---

