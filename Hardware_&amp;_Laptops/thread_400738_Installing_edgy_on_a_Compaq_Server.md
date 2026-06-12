---
title: "Installing edgy on a Compaq Server"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by darkrose on 2007-04-03
Hi everyone,
I know there was a thread on this a couple of years ago, but thought it better to start a fresh one rather than dig up an old thread.

No questions, just answers. For those trying to install Edgy on a Compaq server, the installation goes fine but on reboot you get an error with ACPI and the Array Controller. This is the fix.

For the record, the server I installed on was a Compaq DL380 G1, although apparently the problem exists with most Compaq servers.

The problem is that initramfs doesn't have cpqarray built in by default, so it needs to be added, and a new initrd.img created before the system will boot.

So, install as usual.
Then when rebooting after the install, boot from the cd again and enter recovery mode.
You'll most likely get an error with the cd telling you it can't enter recovery mode, this is ok. Hit enter to continue, and from the menu select 'execute shell'

The frist thing you need to do is mount your installation, my root partition is on /dev/ida/c0d0p2 and I have a seperate /boot partition on /dev/ida/c0d0p1 and this is reflected below. Change the partitions to suit your install.

make a new directory and mount the root partition
1. mkdir /target
2. mount /dev/ida/c0d0p2 /target

then mount the /boot and/or /usr partitions if you have them inside the root directory of your installation (your are recreating the installation's file system)
3. mount /dev/ida/c0d0p1 /target/boot

then change root to /target so you are working inside your installation
4. chroot /target

now you need to tell initramfs to include cpqarray, ths is done by adding cpqarray to /etc/initramfs-tools/modules
5. vi /etc/initramfs-tools/modules 
and add "cpqarray" as the last line, save and close.

now make a new initrd.img
6. initramfs-update -u

unmount the partitions and reboot.
7. umount /target/boot
8. umount /target
9. exit
10. reboot

and you're done, ubuntu should now boot.

Hope that helps someone.

---

### Post by keithnorris on 2007-05-08
I just want to add this for those folks with 6.06LTS issues going onto the **Compaq DL380**. I did have to re-gen the kernel file as above to add the **_cpqarray _**into play, but I had a secondary issue as well. The solution was found off-site somewhere, and I forget where.

Basically, just following the directions above didn't get rid of my problems mounting c0d0p1 at bootup, so I thought I was lost. Another article pointed out that the hard drive controller may be "allocated" to some other module that was already included by default, in particular the SYM53 goodies.

So, after following the instructions above without a solution, I followed one more step: I added two lines to my blacklist file (/etc/modprobe.d/blacklist):

> blacklist sym53c416
blacklist sym53c8xx

The next reboot went without a hitch.

Hope that helps someone out there.

---

