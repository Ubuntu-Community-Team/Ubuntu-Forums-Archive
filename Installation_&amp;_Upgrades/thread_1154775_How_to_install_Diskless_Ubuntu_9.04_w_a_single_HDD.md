---
title: "How to install Diskless Ubuntu 9.04 w/ a single HDD and a router (w/ dhcp enabled)"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by angellsl on 2009-05-10
References
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)
[http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless)

I spent 12 hours saturday and figured out how to setup diskless ubuntu 9.04 desktop version on my linux cluster w/ just one hdd at the moment for 5 quad core nodes. The following is the steps:

0) H/W purchase, assembly.

1) attach the single/only hdd to one of the machine, call it "master", install ubuntu 9.04 there, I did it via usb stick created using unetbootin
Setup all the environment ready for your final use before moving on the next step, including all the drivers, networks, tools, software, etc.

2) My private network is set behind a router (my own, part of my h/w purchase). Use static dhcp in the router to set static ip for "master" and "slaves" (the rest). 

3) On "master", install dhcp3-server, initrams-tools, tftpd-server, nfs-kernel-server, syslinux, etc.

4) setup dhcp3-server, by first editing /etc/dhcp3/dhcp3.conf, be careful, since we have a router set the ip for each node, so no need set ip for "master", but the rest nodes need to set the same ip as the router. more importantly, you need to set the range, router ip, filename (pxe*.0), hosts (different nodes can load different kernel/images via mac/ip specifying). NO NEED for next-server and root-path here. start dhcp3-server.

5) setup tftpd-hda, by first editing /etc/default/tftpd.conf, change it to daemon mode, and point the default directory to /tftpdroot (suppose you want /tftpdroot be your netboot directory). start tftpd-hda

6) CAUTION: change /usr/share/initramfs-tools/scripts/functions as following
comment out line "ipconfig -t 60 -c ${IPOPTS} -d ${DEVICE}"
put line "ifconfig ${DEVICE} the_ip_you_want" there
comment out line ". /tmp/net-${DEVICE}.conf" near the end of function "configure_networking"

And then cp /sbin/ifconfig /usr/*/klib/

And then change /etc/mkinitramfs/initramfs.conf to BOOT=nfs, call mkinitramfs or update-initramfs and make initrd.img, copy it to /tftpdroot/ w/ specified name for each node

7) cp /usr/lib/syslinux/pxelinux.0 /tftpdroot/

8) copy / on "master" to directories such as /slave1 (for node "slave1), etc. via cp -ax /. /slave1

9) edit /etc/exports, exporting /slave1, etc. and then exportfs -rv
if you have home at a different partition, export it to, so that each node can share the same home directory
Basic layout, each node can its own copy OR share w/ other of binary/executable/root directories (such as /bin /usr /etc), but they can share home directory via nfs...

10) edit /tftpdroot/pxelinx.cfg/default as follows:
default slavex

label slave1
   kernel vmlinux...
   append ...nfsroot=the_directory_for_slave1... initrd=the_img_for_slave1 ... rw --
label slave2 (repeat as slave2, change corresponding parameters)

11) times to start each slaves, by first specifying the default option in pxelinux.cfg/default or enable menu.c32

CAUTION: check router firewall setting to make sure all nodes have access to the private network.

Major Hacks: 
1) The dhcp server in router usually does not support filename parameter, so here I used the dhcp server on "master" to overwrite the setting on the router, even though all the nodes are connected via the router
2) There is another hack, after kernel is loaded, the network will be lost due to some bug in ipconfig, manually enable the ethernet w/ specific ip in configure_networking function

Further improvement, put swap file for each node via nbd-server/client

If you don't quite understand some steps, please follow the reference, since they have more detailed information on what I ignored the most,

Good luck

More udpate will be installing SGE, condor, etc...

---

