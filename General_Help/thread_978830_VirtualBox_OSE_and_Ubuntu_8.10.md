---
title: "VirtualBox OSE and Ubuntu 8.10"
date: 2008-11-11
forum: General Help
---

### Post by boaty on 2008-11-11
Hello

I installed VirtualBox OSE earlier today so I could run Windows XP.  I went through the whole 'create a new virtual machine' wizard, and I think it went right, but when I try to start it, I get this error:

> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Also, the wizard never asked me where my Windows XP .iso file was, and I'm pretty sure I need to put that in somewhere.

Any help will be appreciated.

edit:

I managed to solve it by doing

```

uname -r

```
which gave me 2.6.24-21-generic
then I used that and entered
```

sudo apt-get install virtualbox-ose-modules-2.6.24-21-generic

```

So to be safe, do a
```

sudo /etc/init.d/vboxdrv restart

```
and I think the module or whatever it needed is now loaded.

You need to add yourself to the vboxuser group though,
so go to System -> Administration -> Users and Groups
Unlock if needed, and go to 'Manage Groups', go to 'vboxusers' and hit 'Properties'.  Check your name and root, hit ok and log off and back on.

edit2:
Now I still had no bootable media, which of course is a problem which I address above in saying that I didn't specify my WindowsXP .iso file.

Here is how to do it.

After running through the wizard and making your virtual machine, select it and hit the 'Settings' button.
Go to 'General' and select the 'Advanced' tab.  Change your boot order so that the CD option is first.  Now back on the left go to the 'CD/DVD-ROM' window and check 'Mount CD/DVD Drive'.  Hit the ISO radio button and browse to your Operation System's ISO file.  You should now be Good 2 Go!

---

