---
title: "Dpkg malfunction (subtitle: Dpkg shows no love)"
date: 2008-08-15
forum: General Help
---

### Post by rei-jin on 2008-08-15
All right, here goes:

It started innocently enough-- I happened to have a problem with getting some new applications off of the add/remove repository of glorious things.  

Then I noticed that I wasn't getting update notices anymore.  

When I tried to do either of these manually, I got a message saying that I needed to run:
dpkg --configure -a

...to which I was told I needed to be a superuser.

Using my sudo powers did nothing to help, and I got a large chunk of text spit out at me:

rei-jin@Tyrai:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-20-generic (2.6.24-20.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-20-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-20-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-20-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-20-generic:
 linux-restricted-modules-2.6.24-20-generic depends on linux-image-2.6.24-20-generic; however:
  Package linux-image-2.6.24-20-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-20-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-20-generic; however:
  Package linux-image-2.6.24-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-20-generic; however:
  Package linux-restricted-modules-2.6.24-20-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-20-generic:
 linux-ubuntu-modules-2.6.24-20-generic depends on linux-image-2.6.24-20-generic; however:
  Package linux-image-2.6.24-20-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-20-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.20.22); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.20.22); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1
rei-jin@Tyrai:~$ 


Looking around on the forums, I found several potential solutions.  One was to try apt-get clean, which did not help.

Another was to try sudo apt-get install -f.  This led to this message:
rei-jin@Tyrai:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

...which leads me back to my initial problem.

Any ideas out there?

---

### Post by jerome1232 on 2008-08-15
Looks like you are out of space on your / or /boot (if you made a seperate /boot) Could you post the output of df -h?

---

### Post by rei-jin on 2008-08-15
rei-jin@Tyrai:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              23G   12G   11G  53% /
varrun                747M  116K  747M   1% /var/run
varlock               747M     0  747M   0% /var/lock
udev                  747M   72K  747M   1% /dev
devshm                747M   12K  747M   1% /dev/shm
lrm                   747M   39M  709M   6% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3             101M   96M     0 100% /boot
/dev/sda8             4.9G  3.2G  1.8G  64% /windows
rei-jin@Tyrai:~$ 


Hey...would you look at that?
...next question.
Um... about that...what do I do?

---

### Post by jerome1232 on 2008-08-15
yup unfortunately I'm not sure how to safely free up space in there, at least we know what the problem is.

<jerome1232 starts waiting for someone more knowledgeable>

---

### Post by unutbu on 2008-08-15
Please post
```
dpkg --get-selections | grep linux
```
This will show what packages you have installed that have the string "linux" in its name.

You probably have a couple "linux-image-*" packages installed. If you have an old one in there that you no longer use, you could remove that package to create some space.

Post the list if you are unsure.

That may work as a temporary solution. For the future you may want to think about increasing the size of your /boot partition. It is best to backup before you do this. Then boot from a LiveCD, click System>Administration>Partition Editor. A GUI will appear which should allow you to resize the partitions.

---

### Post by jerome1232 on 2008-08-15
----IGNORE THIS---- (unless someone says this won't harm anything)
----IGNORE THIS----
----IGNORE THIS----
Well I THINK you could safely delete an old kernel I'm going to use my /boot as a reference

ok from this I can see I have 3 kernels in there, I know they all work so lets delete (actually just move it into /home so that we can return it if we run into problems)
```
jeremy@desktop:~$ ls -lah /boot
total 55M
drwxr-xr-x  3 root root 4.0K 2008-08-14 22:13 .
drwxr-xr-x 22 root root 4.0K 2008-08-14 22:13 ..
-rw-r--r--  1 root root 411K 2008-07-11 18:20 abi-2.6.24-19-generic
-rw-r--r--  1 root root 411K 2008-07-28 08:38 abi-2.6.24-20-generic
-rw-r--r--  1 root root 411K 2008-08-12 08:43 abi-2.6.24-21-generic
-rw-r--r--  1 root root  73K 2008-07-11 18:20 config-2.6.24-19-generic
-rw-r--r--  1 root root  73K 2008-07-28 08:38 config-2.6.24-20-generic
-rw-r--r--  1 root root  73K 2008-08-12 08:43 config-2.6.24-21-generic
drwxr-xr-x  2 root root 4.0K 2008-08-14 22:13 grub
-rw-r--r--  1 root root 7.4M 2008-08-11 11:52 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 6.9M 2008-08-11 03:41 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7.4M 2008-08-12 00:35 initrd.img-2.6.24-20-generic
-rw-r--r--  1 root root 7.4M 2008-08-12 00:35 initrd.img-2.6.24-20-generic.bak
-rw-r--r--  1 root root 7.4M 2008-08-14 22:13 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7.4M 2008-08-14 22:13 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 101K 2007-09-28 04:03 memtest86+.bin
-rw-r--r--  1 root root 1.1M 2008-07-11 18:20 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1.1M 2008-07-28 08:38 System.map-2.6.24-20-generic
-rw-r--r--  1 root root 1.1M 2008-08-12 08:43 System.map-2.6.24-21-generic
-rw-r--r--  1 root root 1.9M 2008-07-11 18:20 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1.9M 2008-07-28 08:38 vmlinuz-2.6.24-20-generic
-rw-r--r--  1 root root 1.9M 2008-08-12 08:43 vmlinuz-2.6.24-21-generic

```
basically remove anything with the oldest numbers out of /boot
```
sudo mv /boot/abi-2.6.24-19-generic ~/
sudo mv /boot/config-2.6.24-19-generic ~/
sudo mv initrd.img-2.6.24-19-generic* ~/
sudo mv /boot/System.map-2.6.24-19-generic ~/
sudo mv vmlinuz-2.6.24-19-generic ~/
```

now try to do the sudo dpkg --configure -a

edit: this is untested so...
double edit: I think unutbu's solution is the correct way of doing what I'm trying to get at :)

---

### Post by rei-jin on 2008-08-15
> **unutbu said:**
> Please post
```
dpkg --get-selections | grep linux
```
This will show what packages you have installed that have the string "linux" in its name.

You probably have a couple "linux-image-*" packages installed. If you have an old one in there that you no longer use, you could remove that package to create some space.

Post the list if you are unsure.

rei-jin@Tyrai:~$ dpkg --get-selections | grep linux
libselinux1					install
linux-generic					install
linux-headers-2.6.24-16				install
linux-headers-2.6.24-16-generic			install
linux-headers-2.6.24-17				install
linux-headers-2.6.24-17-generic			install
linux-headers-2.6.24-18				install
linux-headers-2.6.24-18-generic			install
linux-headers-2.6.24-19				install
linux-headers-2.6.24-19-generic			install
linux-headers-2.6.24-20				install
linux-headers-2.6.24-20-generic			install
linux-headers-generic				install
linux-image-2.6.22-14-generic			install
linux-image-2.6.24-16-generic			install
linux-image-2.6.24-17-generic			install
linux-image-2.6.24-18-generic			install
linux-image-2.6.24-19-generic			install
linux-image-2.6.24-20-generic			install
linux-image-generic				install
linux-restricted-modules-2.6.22-14-generic	install
linux-restricted-modules-2.6.24-16-generic	install
linux-restricted-modules-2.6.24-17-generic	install
linux-restricted-modules-2.6.24-18-generic	install
linux-restricted-modules-2.6.24-19-generic	install
linux-restricted-modules-2.6.24-20-generic	install
linux-restricted-modules-common			install
linux-restricted-modules-generic		install
linux-sound-base				install
linux-ubuntu-modules-2.6.22-14-generic		install
linux-ubuntu-modules-2.6.24-16-generic		install
linux-ubuntu-modules-2.6.24-17-generic		install
linux-ubuntu-modules-2.6.24-18-generic		install
linux-ubuntu-modules-2.6.24-19-generic		install
linux-ubuntu-modules-2.6.24-20-generic		install
util-linux					install
util-linux-locales				install

---

### Post by unutbu on 2008-08-15
When you boot up, I'm assuming you use either the 2.6.24-19 or the 2.6.24-20 kernel. I'm assuming you do NOT use the 2.6.22-14 and 2.6.24-{16,17,18} kernels.

If the above assumptions are true, use synaptic to remove the following packages:
```

linux-restricted-modules-2.6.22-14-generic 
linux-ubuntu-modules-2.6.22-14-generic 
linux-image-2.6.22-14-generic 

```
Then run 
```

df -h     # See if you have some space now
sudo dpkg --configure -a
sudo apt-get update

```

If that works, great. Now reboot to test that that works too. I don't think there will be any problem, but there's no harm to trying things slowly.

If you reboot with no problems, then go ahead and remove these packages as well (again, assuming you are booting with either 2.6.24-19 or 2.6.24-20.)

```
linux-headers-2.6.24-16 
linux-headers-2.6.24-16-generic 
linux-headers-2.6.24-17 
linux-headers-2.6.24-17-generic 
linux-headers-2.6.24-18 
linux-headers-2.6.24-18-generic 
linux-image-2.6.24-16-generic 
linux-image-2.6.24-17-generic 
linux-image-2.6.24-18-generic 
linux-restricted-modules-2.6.24-16-generic 
linux-restricted-modules-2.6.24-17-generic 
linux-restricted-modules-2.6.24-18-generic 
linux-ubuntu-modules-2.6.24-16-generic 
linux-ubuntu-modules-2.6.24-17-generic 
linux-ubuntu-modules-2.6.24-18-generic 
```

Note that it is a very good idea to keep at least one backup kernel. So if you use 2.6.24-20, keep 2.6.24-19 just in case something happens to your main kernel.

---

### Post by rei-jin on 2008-08-15
Actually...when I try to open Synaptic, I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

...which leads me back to my initial problem.

---

### Post by unutbu on 2008-08-15
What happens when you type

```

sudo apt-get remove linux-image-2.6.22-14-generic

```
Do you get any error message when you do it this way?

---

### Post by rei-jin on 2008-08-15
Yep.  Same message.

---

### Post by jerome1232 on 2008-08-15
Would my solution be in order then? (manually moving files out of /boot) 

You really need to make /boot bigger though 512MB would be more than enough space.

---

### Post by unutbu on 2008-08-15
Ok, how about this then: Try drs305's instructions [http://ubuntuforums.org/showpost.php?p=5537695&postcount=18](http://ubuntuforums.org/showpost.php?p=5537695&postcount=18), except for you when you edit your package-list, remove any line referencing 2.6.24-20. This should relieve your dpkg system from the urge to install it. 
Then you should be able to remove some packages the normal way, and then, when you have more room, to install the 2.6.24-20 packages.

jerome1232's solution may work, but from reading other forum posts it appears that manually moving files associated with packages can sometimes also cause the package system to fail when trying to later remove those packages. I'm not an expert at apt problems, but I get the feeling it is better to try to find an apt-way of solving the problem first, before circumventing it.

---

### Post by rei-jin on 2008-08-15
rei-jin@Tyrai:~$ sudo apt-get remove linux-image-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-2.6.22-14-generic is not installed, so not removed
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9843kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 142231 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
 

this is my latest error.

---

### Post by unutbu on 2008-08-15
Whenever a computer command fails, look in the output for the first line that looks like a complaint. In this case it is 
```

FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
```

Try this:
```

sudo touch /boot/System.map-2.6.22-14-generic
```

This will make a System.map-2.6.22-14-generic file of zero size. 
Then try 
```

sudo apt-get remove linux-image-2.6.22-14-generic
```

again. If it comes back with another complaint of a file not found, repeat the "sudo touch" trick.

If you get a different error, post and we'll puzzle it out.

---

### Post by rei-jin on 2008-08-15
Thank you!  That solved it. :KS

---

