---
title: "eeepc 4g can't boot any live distros"
date: 2012-06-20
forum: Hardware
---

### Post by Shadowstripe on 2012-06-20
someone dropped off an EEE PC 4g[FONT=monospace] 512 mb for me to reinstall and no matter what linux image I tried I couldn't get one to boot via usb flash drive or usb cdrom so last attempt I figured I would install on a different pc and clone the drive across (the internal hard disk is flash and not removable) 

so far so good it boots grub comes up I press enter

no such partition
[/FONT][FONT=monospace]no such partition
[/FONT][FONT=monospace]no such partition

press any key to continue.. seems the drive uuids changed when I mirrored leaving the system unbootable and I am told it can be fixed with a live cd but they fail to boot.

is it possible to boot from within the grub console ? linux is installed on /dev/sda1 I know the path to the kernel and init

I tried but failed to boot lubuntu, xubunt, xubunt alternative (worse), debain (does not even get past enter on boot menu) got vector on the to try list but may just end up installing windoze for him

Thanks
[/FONT]

---

### Post by wilee-nilee on 2012-06-20
Are you familiar with the eeepc only a particular usb port allows a boot from, not sure which one or how many.

There is also a out of the bios boot from menu as well.

---

### Post by Shadowstripe on 2012-06-20
thanks for the reply but I just solved the problem and It was so stupid.

long story short vector detail boot info told me the boot hanging was something todo with sdb so I ejected the sd card now all the live cds boot flawlessly.

why I have no idea and I put more time into and have gone through more cd burns than I like to admit but at least I got it working in the end :)

hope this will be helpful to someone else

-Thanks

---

