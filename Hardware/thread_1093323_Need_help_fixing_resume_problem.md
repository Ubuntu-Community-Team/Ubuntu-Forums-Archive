---
title: "Need help fixing resume problem"
date: 2009-03-11
forum: Hardware
---

### Post by Mark Phelps on 2009-03-11
Found a thread dealing with fixing suspend and hibernate on laptops involving the installation and use of "uswsusp".  So, I installed that package and ran the configuration.

But, I supplied the wrong parameters (which is probably why resume does not work), and now, I can't fix it.

The configuration file is /etc/uswsusp.conf and is edited using dpkg-reconfigure uswsusp.

That regenerates the kernels (wish I had known this before I ran it!), and in the process, generates an error message like the following for each kernel in the menu.lst file:

```

update-initramfs: Generating /boot/initrd.img-2.6.24-23-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sda8
                     UUID=dd3e0f19-06e6-447b-b625-457d9ebe1d19

```
I've run the dpkg-reconfigure several times, supplied the correct responses, but it still generates this same error message.

I've removed the config file, run dpk-reconfigure again, get the same error messages.

I've checked the config file, and it appears to be correct, as follows:
```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda8
image size = 728169431
RSA key file = /etc/uswsusp.key
shutdown method = platform

```
You will notice there's only one Resume Device in the config file.

So, apart from reloading my entire partition from backup (to get the original kernels back), is there any way to fix this to remove the extra Resume Device?

---

### Post by Mark Phelps on 2009-03-11
Replying to myself hoping that someone will comment ...

Remembered reading about using Synaptic to clean out the /boot folder of old kernels, so figured I might be able to use it to replace the existing kernels.  

Use synaptic to reinstall the following packages:
[LIST]
[*]Linux-headers-2.6.24-22
[*]Linux-headers-2.6.24-22-generic
[*]Linux-image-2.6.24-22-generic
[*]Linux-restricted-modules-2.6.24-22-generic
[/LIST]

Did the same for 2.6.24-23 packages.

Rebooted after each set of replacements.

So, am I OK now, or do I still need to restore from back to get the kernels back?

---

### Post by Mark Phelps on 2009-04-10
WOW -- no replies at all in 4 weeks!! So much for community support!

---

### Post by mistry on 2009-12-08
I don't know if you just want to remove the extra resume device or still needed further help on resume issues, but here goes the following:

When you get:
```
update-initramfs: Generating /boot/initrd.img-<some kernel>-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/<some device>
                     UUID=<some uuid>
```

On my machine it was due to the difference between */etc/fstab* and */etc/uswsusp.conf*.  Although these references were to the same device partition, I changed */etc/uswsusp.conf* to reflect what was in */etc/fstab* as follows:

```
 /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
# Change the following line to match the swap in /etc/fstab such as
# resume device = UUID=hfheiu3nd-27na-9d3n-ekek3-91823u498238
resume device = UUID=<your specific swap partition UUID>
splash = y
compress = y
early writeout = y
image size = 1442313175
RSA key file = /etc/uswsusp.key
shutdown method = platform
```

This solved the *cryptsetup* warning for me.  Hopefully it helps you further with resuming.  The following may point you with further help, but I don't want you to lose your data or mess up your system trying this if you don't feel comfortable fixing it through a live CD:
[http://ubuntuforums.org/showthread.php?t=750216]("http://ubuntuforums.org/showthread.php?t=750216")

---

