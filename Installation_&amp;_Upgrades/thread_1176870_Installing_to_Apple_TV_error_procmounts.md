---
title: "Installing to Apple TV error /proc/mounts"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by iitywygms on 2009-06-02
Posted this on the mythbuntu forums but no help there.  My goal is to get mythbuntu installed on the atv but at this point getting anything installed would be a plus.

Anyway.  Here it is.

Okay guys, I need some help
Been at this all weekend and still no joy.
I have followed this guide exactly

[http://code.google.com/p/atv-bootloa...titioningLinux](http://code.google.com/p/atv-bootloa...titioningLinux)
Everything goes well and no errors seen.

I then follow this guide.

[http://code.google.com/p/atv-bootloa.../BootingLiveCD](http://code.google.com/p/atv-bootloa.../BootingLiveCD)
I do the netboot install and all goes well.

This is what I do.

Boot the AppleTV using atv-bootloader and connect using telnet. Then

mkdir tmp

mount /dev/sdb1 tmp

kexec --load tmp/linux --initrd=tmp/initrd.gz --command-line="vga=normal vesa video=vesafb"

kexec -e

I install ubuntu, no errors noticed. I install system to partition 4 and swap to 5.

Now here is where I am stuck.
When I reboot the atv, nothing happens and the atv logo with the question mark appears.
So I stick in the atv-bootloader usb stick and it boots to give me the login prompt.

I can login. I just don't know where to go from here??????
How do I start linux? Should it start automatically?

If I run boot_linux.sh this is what I get.


boot_linux.sh
sda4/boot/brub menu.list found
/bin/bash/
kexec – load /mnt/rootfs/boot/vmlinux (alot of numbers and stuff I am to tired to type)

kexec jump to new kernel


mount: /proc/mounts: No such file or directory
mount: /proc/mounts: No such file or directory

I have been at this all weekend and my eyes are shot.

Any idea what I am doing wrong?

---

### Post by Wieshka on 2009-11-01
I had similar problem, but i figured out by using auto mode, also, copying recovery stick content to recovery partition, than i was able to boot with out USB flash inserted. 

I supouse that next step, what i need to do, is make OS partition (HSF boot partition of apple TV) valid to boot without recovery status my ubuntu ...

When i will figure out, i can make some manual.

About partitions - what size of is OS & Recovery for you, and what size is your HDD ?

---

