---
title: "trouble getting Virtualbox to run"
date: 2008-09-24
forum: General Help
---

### Post by PlayEdUdE on 2008-09-24
Ok so i want to run a virtualbox off my WinXP hard drive, so i run the following:

```
****@****-desktop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinXP.vmdk -rawdisk /media/disk -register
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.
VirtualBox Command Line Management Interface Version 1.5.6_OSE
(C) 2005-2008 innotek GmbH
All rights reserved.

Usage: VBoxManage internalcommands <command> [command arguments]

Commands:

  loadsyms <vmname>|<uuid> <symfile> [delta] [module] [module address]
      This will instruct DBGF to load the given symbolfile
      during initialization.

  unloadsyms <vmname>|<uuid> <symfile>
      Removes <symfile> from the list of symbol files that
      should be loaded during DBF initialization.

  setvdiuuid <filepath>
       Assigns a new UUID to the given VDI file. This way, multiple copies
       of VDI containers can be registered.

WARNING: This is a development tool and shall only be used to analyse
         problems. It is completely unsupported and will change in
         incompatible ways without warning.

Syntax error: Invalid command 'createrawvmdk'
```

Ok so that sounds easy enough so i install the required package
```

****@****-desktop:~$ sudo apt-get install virtualbox-ose-modules-2.6.24-16-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.24-16-generic
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
  linux-image-2.6.24-16-generic virtualbox-ose-modules-2.6.24-16-generic
0 upgraded, 2 newly installed, 0 to remove and 25 not upgraded.
Need to get 18.7MB of archives.
After this operation, 62.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com hardy/main linux-image-2.6.24-16-generic 2.6.24-16.30 [18.4MB]
Get:2 http://archive.ubuntu.com hardy/universe virtualbox-ose-modules-2.6.24-16-generic 24 [326kB]
Fetched 18.7MB in 6min5s (51.1kB/s)                                            
Selecting previously deselected package linux-image-2.6.24-16-generic.
(Reading database ... 114434 files and directories currently installed.)
Unpacking linux-image-2.6.24-16-generic (from .../linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb) ...
Done.
Selecting previously deselected package virtualbox-ose-modules-2.6.24-16-generic.
Unpacking virtualbox-ose-modules-2.6.24-16-generic (from .../virtualbox-ose-modules-2.6.24-16-generic_24_i386.deb) ...
Setting up linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /vmlinuz-2.6.24-16-386
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms

Setting up virtualbox-ose-modules-2.6.24-16-generic (24) ...
```

I give it another shot

```
****@****-desktop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinXP.vmdk -rawdisk /media/disk -register
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-modules package for your kernel,
	 which is likely virtualbox-ose-modules-generic.

	 You will not be able to start VMs until this problem is fixed.
VirtualBox Command Line Management Interface Version 1.5.6_OSE
(C) 2005-2008 innotek GmbH
All rights reserved.

Usage: VBoxManage internalcommands <command> [command arguments]

Commands:

  loadsyms <vmname>|<uuid> <symfile> [delta] [module] [module address]
      This will instruct DBGF to load the given symbolfile
      during initialization.

  unloadsyms <vmname>|<uuid> <symfile>
      Removes <symfile> from the list of symbol files that
      should be loaded during DBF initialization.

  setvdiuuid <filepath>
       Assigns a new UUID to the given VDI file. This way, multiple copies
       of VDI containers can be registered.

WARNING: This is a development tool and shall only be used to analyse
         problems. It is completely unsupported and will change in
         incompatible ways without warning.

Syntax error: Invalid command 'createrawvmdk'

```

Says i don't have the pkg i just installed...
So i run Apt-get again
```
****@****-desktop:~$ sudo apt-get install virtualbox-ose-modules-2.6.24-16-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-ose-modules-2.6.24-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
****@****-desktop:~$ 

```
apt-get says its installed but virtualbox says it isn't.

also noticed "Syntax error: Invalid command 'createrawvmdk'" Is there an updated cmd i should use?

What am I doing wrong here? Am I missing something obvious?

---

### Post by PlayEdUdE on 2008-09-24
bump/ plz help Im getting frustrated :confused:

---

