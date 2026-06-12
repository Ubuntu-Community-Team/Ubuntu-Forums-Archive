---
title: "Kernel 2.6.24-19 problem"
date: 2008-07-12
forum: General Help
---

### Post by pixnaps on 2008-07-12
Hi, my computer won't load properly on the default option of kernel 2.6.24-19.  The command line mentions a "fatal error" (something about the binfmt_misc module not being found), and then a screen comes up saying it can't find the graphics card, so it's running in low graphics mode, but my mouse/touchpad doesn't work either.

It works fine if I instead load 2.6.24-18 on startup.

Is there any way to fix this, or at least change the default startup kernel?

---

### Post by Vivaldi Gloria on 2008-07-12
> **pixnaps said:**
> change the default startup kernel?


Press Alt+F2 and start

```
gksudo gedit /boot/grub/menu.lst
```

You should see kernels at the end. Part of it in my computer looks like this:

```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro single
initrd		/boot/initrd.img-2.6.24-18-generic

```

Of course your uuids are different. Now comment out lines belonging to kernel 2.6.24-19 by putting # in front of them.

```
#title		Ubuntu 8.04, kernel 2.6.24-19-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet

#title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro single
#initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro single
initrd		/boot/initrd.img-2.6.24-18-generic

```

That should do it.

---

### Post by Master Chief on 2008-07-12
binfmt_misc.ko is an important kernel module which normally can be found here:

```
/lib/modules/2.6.24-19-generic/kernel/fs/binfmt_misc.ko
```

Just do a:

```
locate binfmt_misc.ko
```

And that'll show the locations of this file, but do NOT copy it from another kernel!

What you should do is menu: System -> Administrator -> Update Manager and check for updates.  
If it finds any updates, please install them!

Next thing is to re-install the failing kernel with: System -> Administrator -> Synoptic Package Manager 
(search filter "linux generic") and reboot into the new working kernel after the installation.

---

### Post by pixnaps on 2008-07-12
Thanks, reinstalling the kernel (first the 'module' package, then the 'image' one) seems to have fixed things, except that it then loses wireless capability. (Maybe it fails to load my Atheros proprietary drivers?)

So for now I'm just using the 24-18, and commenting out 24-19 as per Vivaldi's instructions. (Are there advantages to 24-19 that would make it worth trying to fix?)

---

### Post by Vivaldi Gloria on 2008-07-12
> **pixnaps said:**
> Are there advantages to 24-19 that would make it worth trying to fix?

See

[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.24-19.34/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux/linux_2.6.24-19.34/changelog)

for the changelog.

---

### Post by dcstar on 2008-07-12
> **pixnaps said:**
> 
.........
Is there any way to fix this, or at least change the default startup kernel?

You simply change your /etc/boot/grub/menu.lst file with the following:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		**saved**
```

And then add the last highlighted word to each block of code as per this example from my system:

```


## should update-grub add savedefault to the default options
## can be true or false
# savedefault=**true**

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=34a084d1-8db0-4fa6-9454-ddc72dd4c59c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
**savedefault**
```

Grub will now "remember" the last boot option you used and default to that.

---

### Post by Master Chief on 2008-07-12
> **pixnaps said:**
> Thanks, reinstalling the kernel (first the 'module' package, then the 'image' one) seems to have fixed things, except that it then loses wireless capability. (Maybe it fails to load my Atheros proprietary drivers?)...

Ok, one thing at a time.  I'm glad to see that you managed to re-install the kernel, but it might also explain why you ran into trouble in the first place.

Please do a search for "Atheros" first and see if that gets you any further, and if not, we're here to help.

> ...So for now I'm just using the 24-18, and commenting out 24-19 as per Vivaldi's instructions. (Are there advantages to 24-19 that would make it worth trying to fix?)

Ok, so you can start Ubuntu without errors again, and use the Internet. Fine, but I wonder what hardware you are using.  Did you use the ndiswrapper?  Does that ring a bell?

---

