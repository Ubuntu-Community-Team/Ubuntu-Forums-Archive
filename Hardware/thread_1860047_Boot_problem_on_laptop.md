---
title: "Boot problem on laptop"
date: 2011-10-14
forum: Hardware
---

### Post by Callmestupid on 2011-10-14
My friend was upgrading to the newest Ubuntu 11.10 on re-boot he got the following:

Boot from (hd0,0) ext 3 db6e489f-b271-4221-8493-6ac51b29bbc2

Starting up ...

[ 2.424690] Kernel panic - not syncing: VFS: unable to mount root fs on unkwn-block(0,0)

[ 2.424743] Pid: 1, comm: swapper not tainted 2.6.38-10-generic #46-Ubuntu

[ 2.424786] Call Trace:

[ 2.424830] [<c15075f6>] ? panic+0x5c/0x157

[ 2.424875] [<c178dc26>] ? mount_block_root+0c1c2/0x25b

[ 2.424919] [<c1002930>] ? handle_signal+0x230/0x1d0

[ 2.424962] [<c11348fc>] ? sys_mknod+0x2c/0x30

[ 2.425003] [<c178de37>] ? mount_root+0x59/0x5f

[ 2.425046] [<c178df8b>] ? prepare_namespace+0x14e/0x192

[ 2.425089] [<c1126035>] ? sys_access+0x25/0x30

[ 2.425130] [<c178d9a1>] ? kernel_init+0x1b9/0x1c8

[ 2.425172] [<c178d7e8>] ? kernel_init+0x0/0x1c8

[ 2.425214] [<c100367e>] ? kernel_thread_helper+0x6/0x10

At this point the computer would do nothing more. It is an Acer Aspire 4720Z Laptop. Which had Ubuntu 11.04 for the operating system.


Have tried re-installing 11.04 32 bit. With same result when booting from CD.

Also attempted to boot with Puppy Linux 5.2 with same result and then on 2nd or 3rd reboot Puppy Linux did boot the computer from the CD.

---

### Post by LordNodens on 2011-10-20
I also had the same problem after upgrading from 11.04 x64 and rebooting for the first time. This is what I did and it solved my problem:


[LIST=1]
[*]Boot into Ubuntu Live CD
[*]Sudo as root, mount the / partition and chroot into that partition  (using a terminal). In my case /dev/sdb1 was where I installed my /  partition. Also mount proc and dev inside your mounted /dev/sdb1  directory
**sudo -i**
**mkdir -p /media/ubuntu**
[B]mount /dev/sdb1 /media/ubuntu
sudo mount -t proc none [/B]**/media/ubuntu/****proc**
**sudo mount -o bind /dev ****/media/ubuntu/****dev**
**chroot /media/ubuntu**
[*]After chrooting inside, reinstall the kernel
**apt-get update **
**apt-get install --reinstall linux-image-3.0.0-12-generic**
[*]Reboot
[/LIST]
Hope this helps.

---

