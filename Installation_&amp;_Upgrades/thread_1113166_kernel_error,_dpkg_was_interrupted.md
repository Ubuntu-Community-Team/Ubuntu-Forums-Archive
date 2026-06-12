---
title: "kernel error, dpkg was interrupted"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by archeryguru2000 on 2009-04-01
Hello all.  I recently tried to do an upgrade and received this error message.
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```
So, I naturally ran that command with the following results:
```

$: sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28.4-ultimate
Cannot find /lib/modules/2.6.28.4-ultimate
update-initramfs: failed for /boot/initrd.img-2.6.28.4-ultimate
dpkg: subprocess post-installation script returned error exit status 1

```

I remember updating my kernel (like several months ago) to this "ultimate" mentioned above, but couldn't properly configure my nVidia card, so I eventually removed that kernel through apt-get remove.  Obviously I should have purged instead of removed. :roll:  Anyway, I've tried purging that kernel, but cannot find it in Synaptic.  I've been able to locate all files pertaining to that kernel by
```

$: locate 2.6.28.4-ultimate

```
My main question is... How do I go about removing (totally) all references to that kernel?

Also, I'm not sure if this helps anybody.  But I found on a couple of other forums/threads the following command was posted.  So here's mine:
```

sudo dpkg -l | grep -v ^ii
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                              Description
+++-==========================================-====================================================-============================================
rc  fast-user-switch-applet                    2.22.0-0ubuntu2                                      Applet for the GNOME panel providing a menu 
rc  glade-doc                                  2.12.2-0ubuntu1                                      Documentation for GTK+ 2 User Interface Buil
rc  grub                                       0.97-29ubuntu21                                      GRand Unified Bootloader
iF  initramfs-tools                            0.85eubuntu39.3                                      tools for generating an initramfs
rc  libawn0                                    0.2.1-0ubuntu2.2                                     library for avant-window-navigator
rc  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                      Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-19-generic 2.6.24.13-19.45                                      Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51                                      Non-free Linux 2.6.24 modules on x86/x86_64
rc  linux-ubuntu-modules-2.6.24-16-generic     2.6.24-16.23                                         Ubuntu supplied Linux modules for version 2.
rc  linux-ubuntu-modules-2.6.24-19-generic     2.6.24-19.28                                         Ubuntu supplied Linux modules for version 2.
rc  linux-ubuntu-modules-2.6.24-21-generic     2.6.24-21.33                                         Ubuntu supplied Linux modules for version 2.
rc  menu                                       2.1.38ubuntu2                                        generates programs menu for all menu-aware a
rc  usplash                                    0.5.19                                               Userspace bootsplash utility
rc  usplash-theme-ubuntu                       0.18                                                 Usplash theme for Ubuntu

```

~~archery~~

---

### Post by archeryguru2000 on 2009-04-01
Ok, I've also decided to post the following commands:
```

$: dpkg-query --show --showformat='${Package}\n' linux-image-\*
linux-image-2.6
linux-image-2.6.24-16-generic
linux-image-2.6.24-19-386
linux-image-2.6.24-19-generic
linux-image-2.6.24-19-openvz
linux-image-2.6.24-19-rt
linux-image-2.6.24-19-server
linux-image-2.6.24-19-virtual
linux-image-2.6.24-21-generic
linux-image-2.6.24-22-generic
linux-image-2.6.24-23-generic
**[COLOR="Red"]linux-image-2.6.28.4-ultimate[/COLOR]**
linux-image-generic

```

and

```

$: dpkg-query --show --showformat='${Package}\n' linux-headers-\*
linux-headers-2.6
linux-headers-2.6.24-16
linux-headers-2.6.24-16-generic
linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
linux-headers-2.6.24-21
linux-headers-2.6.24-21-generic
linux-headers-2.6.24-22
linux-headers-2.6.24-22-generic
linux-headers-2.6.24-23
linux-headers-2.6.24-23-generic
**[COLOR="Red"]linux-headers-2.6.28.4-ultimate[/COLOR]**
linux-headers-386
linux-headers-generic
linux-headers-lpia
linux-headers-lpiacompat
linux-headers-rt
linux-headers-server
linux-headers-ume
linux-headers-virtual
linux-headers-xen

```

The highlighted lines above should not be there.  Can anybody out there help me in making them disappear?  Please.

FYI:
```

$: uname -a
Linux <my-comp-name> **[COLOR="Red"]2.6.24-23-generic[/COLOR]** #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

```

I would simply reinstall the kernel in the Ubuntu repo, but I cannot install anything while I have this dpkg error!  Is it possible to somehow clear the dpkg error and then attempt an install?

~~archery~~

---

### Post by archeryguru2000 on 2009-04-02
Anybody out there?

~~archery~~

---

### Post by archeryguru2000 on 2009-04-23
Does anybody have ANY suggestions?  Please.

~~archery~~

---

### Post by drs305 on 2009-04-23
Since this happened long ago, I don't think the status-old file will help. Normally you could try replacing /var/lib/dpkg/status with /var/lib/dpkg/status-old, but in your case I suspect it would contain the same information. If the following doesn't work, you could try it anyway.

See if /var/lib/dpkg/status contains a reference to the offending package:
```

cat /var/lib/dpkg/status | grep "2.6.28.4-ultimate"
```

If you a get a return(s), make a backup of the file and then edit out the references:
```

sudo cp /var/lib/dpkg/status $HOME/Desktop/status
gksudo gedit /var/lib/dpkg/status &

```

If this doesn't solve things, return the original file:
```

sudo cp $HOME/Desktop/status /var/lib/dpkg/status

```

Delete the file on your Desktop using SHIFT-DELTE:
```

gksudo nautilus $HOME/Desktop &

```

---

### Post by archeryguru2000 on 2009-04-25
Thanks for the assistance drs305, but no luck.  After following your instructions, I ran

```

$: sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3)...

update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28.4-ultimate
Cannot find /lib/modules/2.6.28.4-ultimate
update-initramfs: failed for /boot/initrd.img-2.6.28.4-ultimate
dpkg: subprocess post-installation script returned error exit status 1

```

I wonder if there would be a way to pass an argument to initramfs *_through_* the dpkg command?  If I issue the following...

```

$: sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-2.6.28.4-ultimate
Cannot find /lib/modules/2.6.28.4-ultimate
update-initramfs: failed for /boot/initrd.img-2.6.28.4-ultimate
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

```

... I am able to update all kernel images.  Do you know of any way to do that?

Thanks again for your help,
~~archery~~

---

### Post by drs305 on 2009-04-25
Just on the boards for a few minutes. Try running this command to see if it kills the error messages:
```

sudo update-initramfs -k 2.6.28.4-ultimate -d

```
The "-k" switch identifies the kernel and the "-d" tells the command to remove it.

---

### Post by Triggerhapp on 2009-04-26
I'll probably get told Im telling you bad advise but I just recovered from this myself :)

For the named version that you already uninstalled and is now causing you problems 

```
triggerhapp@lollappy:/boot$ sudo rm /var/lib/initramfs-tools/2.6.29.1-ultimate
```

Naturally, replace with the kernel version that is causing you headache

---

### Post by archeryguru2000 on 2009-04-28
> **drs305 said:**
> Just on the boards for a few minutes. Try running this command to see if it kills the error messages:
```

sudo update-initramfs -k 2.6.28.4-ultimate -d

```
The "-k" switch identifies the kernel and the "-d" tells the command to remove it.

CRAP!
```

$: sudo update-initramfs -k 2.6.28.4-ultimate -d
Cannot delete /boot/initrd.img-2.6.28.4-ultimate, doesn't exist.

```

Sorry drs305, I thought maybe you were on to something here.  I appreciate your persistent help though.

~~archery~~

---

### Post by archeryguru2000 on 2009-04-28
> **Triggerhapp said:**
> I'll probably get told Im telling you bad advise but I just recovered from this myself :)

For the named version that you already uninstalled and is now causing you problems 

```
triggerhapp@lollappy:/boot$ sudo rm /var/lib/initramfs-tools/2.6.29.1-ultimate
```

Naturally, replace with the kernel version that is causing you headache

Hallelujah!  You saved my virtual life!  Actually what I did (since I was too chicken to actually remove it)  I simply (temporarily) moved it to a different directory.  Then ran the following;
```

$: sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.3) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
[1]+  Done                    nautilus /var/lib/initramfs-tools

```
Now all is (or at least appears to be) well again.  I am currently updating my system as I'm typing this.  I will attempt a reboot when all is finished as a verification.  I'll keep everyone posted.  I will permanently remove that file if all remains good.  Thanks big time Triggerhapp.

~~archery~~

---

### Post by archeryguru2000 on 2009-04-28
YEAH!  All is well in the land of Ubuntu!  This was starting to actually worry me.  A big thanks to Triggerhapp for the suggestion.

~~archery~~

---

### Post by archeryguru2000 on 2009-04-28
Umm, two more questions please.

1:  How do I mark this thread as solved?
    I do not see a "Mark as solved" option under the thread tools menu.

2:  How do give drs305 and Triggerhapp a Thank you?
    There is no way I would've figured this out without their awesome assistance.  I do not see a "thank me" icon in their posts.

~~archery~~

---

### Post by drs305 on 2009-04-28
The Solved and Thanks links were removed. Originally it was thought to be permanent but there is now a possibility they will be back. 

For "Solved", the Forum remedy is to add a "solved" tag. 

[COLOR="Red"]ADDED[/COLOR]: [COLOR="DarkRed"]The "add tags" feature is located a little below the last post on the right side. You don't have to open a specific post. Click on the "**Edit Tags**".  

Apparently at present anyone can add a tag. I  believe only the OP *should* be able to mark it "Solved". Since this isn't the case, the OP indicated it is solved, and I can, I have. ;-)[/COLOR]

---

### Post by archeryguru2000 on 2009-04-28
> **drs305 said:**
> The Solved and Thanks links were removed. Originally it was thought to be permanent but there is now a possibility they will be back.

That's quite unfortunate, but I could see how something like this could get abused/misused.  However, a big thanks for your help anyway.

> **drs305 said:**
> For "Solved", the Forum remedy is to add a "solved" [QUOTE=drs305;7167889]tag to the original post.

I edited the title to include [SOLVED], but was unable to access the tags option to make it official.

~~archery~~[QUOTE=drs305;7167889]

---

