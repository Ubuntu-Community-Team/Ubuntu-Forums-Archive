---
title: "virtualbox help"
date: 2008-11-11
forum: General Help
---

### Post by Forbees on 2008-11-11
i went to the site, downloaded and installed virtualbox2.0

it did nothing

terminal i typed virtualbox, said it wasn't installed

so i removed virtualbox2.0 cuz it didn't work

i installed virtualbox through terminal this time

install seemed fine

```

forbees@forbees-desktop:~$ virtualbox
WARNING: The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-source package and the appropriate
         headers, most likely  linux-headers-generic.

	 You will not be able to start VMs until this problem is fixed.

```

but it still opens up

i set up a windows xp machine on it

but i can't start it

when i click start i get

```


Virtual machine 'Windows XP' has terminated unexpectedly during startup.


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

```

and in another window

```

VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```

so i tired to do what it told me and nothing happened

```

forbees@forbees-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
forbees@forbees-desktop:~$ 

```



what am i doing wrong?

---

### Post by soro2005 on 2008-11-11
As you can see in the first window, it's going to fail until you correct the problem and install the drivers correctly.

However, you don't want the open source edition. Go [here](http://www.virtualbox.org/wiki/Linux_Downloads) and follow the instructions. Add the Intrepid line to your sources (You can do that in Synaptic if you prefer), then update and install the package virtualbox-2.0 from Synaptic. It'll fetch everything it needs.

---

### Post by Forbees on 2008-11-11
```

VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-<version> whereby <version> can be determined by 'uname -r') and execute

  /etc/init.d/vboxdrv setup

as root.

```

so i went to the instal log

```

Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/2.0.4/source ->
                 /usr/src/vboxdrv-2.0.4

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.24-19-generic cannot be found at
/lib/modules/2.6.24-19-generic/build or /lib/modules/2.6.24-19-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

```

something is wrong with my kernal???

---

### Post by Forbees on 2008-11-12
anyone?

---

### Post by soro2005 on 2008-11-12
Try
```
sudo apt-get isntall linux-headers-generic
```
and then
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Forbees on 2008-11-12
> **soro2005 said:**
> Try
```
sudo apt-get isntall linux-headers-generic
```
and then
```
sudo /etc/init.d/vboxdrv setup
```

headers are already newist version >,<

---

### Post by Forbees on 2008-11-18
any other ideas?

---

### Post by thinkdez on 2008-11-18
I just upgraded my system and had to re-install drivers.  To be sure you are getting the Linux headers for your kernel run the following:

```
$sudo apt-get isntall linux-headers-`uname -r`
$sudo /etc/init.d/vboxdrv setup
```

That should get you the proper headers for your kernel version. From the error in your  logs it appears that your not running the generic kernel.  

If the above doesn't work can you provide the output from $uname -r?  Also did you compile a custom kernel?

---

### Post by Forbees on 2008-11-18
> **thinkdez said:**
> I just upgraded my system and had to re-install drivers.  To be sure you are getting the Linux headers for your kernel run the following:

```
$sudo apt-get isntall linux-headers-`uname -r`
$sudo /etc/init.d/vboxdrv setup
```

That should get you the proper headers for your kernel version. From the error in your  logs it appears that your not running the generic kernel.  

If the above doesn't work can you provide the output from $uname -r?  Also did you compile a custom kernel?

```

forbees@forbees-desktop:~$ sudo apt-get install linux-headers-`uname -r`
[sudo] password for forbees: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-19-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-19-generic has no installation candidate
forbees@forbees-desktop:~$ 

```

---

### Post by thinkdez on 2008-11-18
Hmmm. that seems odd.  When was the last time you updated apt?  Can you try running an sudo apt-get update and then run the commands I provided.

If that doesn't work you can download the headers package from the link below:
[http://packages.ubuntu.com/hardy-updates/linux-headers-2.6.24-19-generic]("http://packages.ubuntu.com/hardy-updates/linux-headers-2.6.24-19-generic")

Then install the above package and try the /etc/init.d/vboxdrv setup again.

Its a good idea to make sure your system is up to date as it might solve many of your issues.

---

### Post by Forbees on 2008-11-19
i had to reinstall windows to get left 4 dead running . . . . great game for all you valve lovers


so i think it might be fixed cuz i recompiled kernal to get grub back up

```

forbees@forbees-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Removing old VirtualBox kernel module                                         *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.

```


so whats the command to open virtual box?

i thought it was Vbox
but that doesn't work

---

### Post by howefield on 2008-11-19
try VirtualBox

watch the capitalisation..

---

### Post by Forbees on 2008-11-19
cool that worked

one last question i hope

when i run, i need a windows xp cd in the drive to install XP on the virtual machine right?

i ran it and said i didn't have any bootable media in the drive, so  . . . yeah, need to kinda install windows to virtual machine?

---

### Post by Forbees on 2008-11-20
well i didn't  feel like waiting, so i'm installing windows on vbox now, figured it out

but the real question is

can i play my steam games on here w/o lag and glitches?
audiosurf, counterstrick source, left 4 dead

---

