---
title: "Booting Grief - Can't boot - vgchange missing"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by paul_a_bennett on 2009-04-11
Hello!

I'm hoping someone can help me resolve my problem booting my headless ubuntu server.  That is to say that it's headless in the sense that I normally access it through ssh and not through a monitor connected to it directly.  The server doesn't have an X server on it.)

I have been happily running this machine for a year or so.  It's an AMD64 machine.

Recently, I did a apt-get dist-upgrade.  Afterwards, the machine would not boot, complaining that vgchange was not present.  

That's when I burned myself a CD of 8.04 server and booted off the CD, using a locally connected monitor.

Having booted the CD, I went into the 'Repair a broken system option' and created a shell on the Ubunto_root.

Sure enough, vgchange was not present in /sbin.  I rand apt-get install lvm2 which appeared to correct the problem (/sbin/vgchange was now present).

I attempted to reboot but the boot failed in exactly the same way.  Within the initramfs, I checked /sbin and vgchange was NOT present.

I rebooted the CD, went back into the 'Repair' mode and ran update-initramfs -uv.  I saw it include the lvm module, though there was no mention of vgchange.  I rebooted, the same results: vgchange was not present in /sbin and the boot process complained accordingly and stopped.

Back into the 'Repair' mode from the CD.  Here, I tried update-initramfs -d -k all, followed by update-initramfs -c -k all.  On rebooting, I'm still in the same situation.

I would appreciate help in understanding what's going on.  I should say that by no means am I any kind of boot or kernel guru.  I'm just a guy trying to get his system going and being forced to poke around where I've never gone before.  Your help will be greatly appreciated.

---

### Post by paul_a_bennett on 2009-04-13
Further to my previous message, I have come to realize that the initramfs file system is created during the kernel make process (please correct me if I'm wrong).

I've checked and the file in the /boot directory appears to be present and of the right order of magnitude, size-wise.

However, my system still won't boot.  I'm still looking for help.

I have tried to run an apt-get install linux-server.  It exits with an error message, apparently after it has created the initramfs file but before it can complete whatever it needs to do in order to create a functioning system.  Despite what appears to be a 'proper' initramfs, when the machine tries to boot, it still can't find vgchange and calls into an initramfs file system.

Unfortunately, I can't report any errors as this is a server machine which I normally access through ssh, over my network.  Since the machine won't boot, I'm using a 17" monitor and the messages scroll by too fast to read.  I've tried piping the output to more and using CTRL-S/CTRL-Q but I can't slow the thing down enough to see what's really going on.

Help would be greatly appreciated.

---

### Post by paul_a_bennett on 2009-04-15
Well, this is leading me into the abyss, I'm afraid.

I still can't get my system booted.

It seems that, somehow, I have to get vgchange into the initramfs but I don't seem to be able to figure out how.

I tried editing /etc/initramfs-tools/modules to add dm_mod in the expectation that dm_mod contains vgchange.  I then ran update-initramfs -uv but when I rebooted, vgchange still wasn't present.

Thus, I have a couple of questions:

How can I tell what commands are in what modules?

How can I tell what modules are in what (Ubuntu) packages?

I can't help but wish that things were better documented.  I know I'm only five minutes away from having a working system.  The problem is what do I have to do during those five minutes?

---

### Post by Tormented Tapir on 2009-06-26
What I did  to solve the matter (after fiddling with initramfs), was to install the _**lvm2 **_package which was somehow missing, it probably was removed by a conflict left from the dapper days while I wasn't paying attention.

I had the same message from update-initramfs just now, when updating a hardy server that was upgraded from dapper about a year ago.

The rootfs in my server works on top of LVM:
```
/dev/evms/lvm2/Ubuntu/root on / type reiserfs (rw)
```So after the update the box would be unable to boot.

What gave me a clue was the output of vgchange (which is a symlink to lvmiopversion, a program that redirects you to the proper version of lvm tool needed):
```
# vgchange 
No program "vgchange" found for your current version of LVM
```To be able to install lvm2, I had to do 'fix' the dependencies with an:
```
 apt-get -f install
``` It went smoothly afterwards and the vgchange error dissapeared.



```
# apt-get install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-server: Depends: linux-image-server (= 2.6.24.24.26) but 2.6.24.19.21 is to be installed
  lvm2: Conflicts: lvm-common but 1.5.20ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@box:/sbin# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  netkit-inetd
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-server
The following packages will be upgraded:
  linux-image-server
1 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B/26.6kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 110490 files and directories currently installed.)
Preparing to replace linux-image-server 2.6.24.19.21 (using .../linux-image-server_2.6.24.24.26_i386.deb) ...
Unpacking replacement linux-image-server ...
Setting up linux-image-server (2.6.24.24.26) ...
root@ntp:/sbin# apt-get install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  netkit-inetd
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  lvm-common
The following NEW packages will be installed:
  lvm2
0 upgraded, 1 newly installed, 1 to remove and 9 not upgraded.
Need to get 325kB of archives.
After this operation, 750kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://mx.archive.ubuntu.com hardy/main lvm2 2.02.26-1ubuntu9 [325kB]
Fetched 325kB in 4s (76.1kB/s)
(Reading database ... 110490 files and directories currently installed.)
Removing lvm-common ...
Selecting previously deselected package lvm2.
(Reading database ... 110480 files and directories currently installed.)
Unpacking lvm2 (from .../lvm2_2.02.26-1ubuntu9_i386.deb) ...
Setting up lvm2 (2.02.26-1ubuntu9) ...
Installing new version of config file /etc/lvm/lvm.conf ...
Backing up any LVM2 metadata that may exist...done.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-24-server
```


Greetings

 JG

---

