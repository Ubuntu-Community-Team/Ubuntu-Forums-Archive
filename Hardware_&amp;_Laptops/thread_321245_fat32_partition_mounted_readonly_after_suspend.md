---
title: "fat32 partition mounted readonly after suspend"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by vikasrawal on 2006-12-18
I upgraded my laptop from Dapper drake to Edgy. Suspend/hibernate facility did not work out of the box because of bug [42299]("https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/42299") . This was however sorted out. I still continue to have a strange problem though. My machine has a fat32 partition on which I keep some data. Every now and then, this partition becomes readonly. On such occassions, I am unable to umount the partition. The output of "fuser -muv /mnt/dwin" shows (see below) almost everything running on the fat32 partition!! Isn't this odd? My sense is that there is still something wrong with suspend-to-disk setup. But I am not sure.

Can anyone guide me on how to diagnose correctly/sort out the problem.

VR
-----------------------

                     USER        PID ACCESS COMMAND
/mnt/dwin:           root          1 ....m (root)init
                     root       2208 ....m (root)udevd
                     daemon     3582 ....m (daemon)portmap
                     root       3606 ....m (root)getty
                     root       3607 ....m (root)getty
                     root       3608 ....m (root)getty
                     root       3609 ....m (root)getty
                     root       3610 ....m (root)getty
                     root       3611 ....m (root)getty
                     root       3821 ....m (root)acpid
                     root       3929 ....m (root)dd
                     klog       3931 ....m (klog)klogd
                     root       4005 ....m (root)gdm
                     root       4013 ....m (root)gdm
                     root       4016 ....m (root)Xorg
                     root       4045 ....m (root)hpiod
                     hplip      4070 ....m (hplip)python
                     messagebus   4172 ....m (messagebus)dbus-daemon
                     haldaemon   4187 ....m (haldaemon)hald
                     root       4188 ....m (root)hald-runner
                     haldaemon   4194 ....m (haldaemon)hald-addon-acpi
                     haldaemon   4202 ....m (haldaemon)hald-addon-keyb
                     haldaemon   4218 ....m (haldaemon)hald-addon-stor
                     root       4238 ....m (root)perl
                     ivman      4286 ....m (ivman)ivman
                     root       4325 ....m (root)mysqld_safe
                     mysql      4389 ....m (mysql)mysqld
                     root       4390 ....m (root)logger
                     root       4549 ....m (root)master
                     postfix    4576 ....m (postfix)pickup
                     postfix    4577 ....m (postfix)qmgr
                     root       4579 ....m (root)nmbd
                     root       4581 ....m (root)smbd
                     root       4589 ....m (root)smbd
                     root       4600 ....m (root)sshd
                     vikas      4687 .rce. (vikas)gnome-session
                     statd      4688 ....m (statd)rpc.statd
                     root       4722 ....m (root)hcid
                     root       4731 ....m (root)sdpd
                     root       4751 ....m (root)hidd
                     root       4777 ....m (root)mdadm
                     vikas      4826 ....m (vikas)ssh-agent
                     vikas      4827 ....m (vikas)ssh-agent
                     daemon     4828 ....m (daemon)atd
                     vikas      4843 .rce. (vikas)dbus-launch
                     root       4844 ....m (root)cron
                     vikas      4857 .rce. (vikas)dbus-daemon
                     vikas      4870 .rce. (vikas)beryl-manager
                     root       4903 ....m (root)miniserv.pl
                     root       4913 ....m (root)vmnet-bridge
                     root       4927 ....m (root)vmnet-natd
                     vikas      5026 .rce. (vikas)emerald
                     vikas      5030 .rce. (vikas)beryl
                     root       5031 ....m (root)apache2
                     www-data   5032 ....m (www-data)apache2
                     www-data   5033 ....m (www-data)apache2
                     www-data   5035 ....m (www-data)apache2
                     vikas      5180 Frce. (vikas)gconfd-2
                     vikas      5183 .rce. (vikas)gnome-keyring-d
                     vikas      5186 .rce. (vikas)gnome-settings-
                     vikas      5195 .rce. (vikas)sh
                     vikas      5196 .rce. (vikas)esd
                     vikas      5208 .rce. (vikas)gnome-panel
                     vikas      5212 .rce. (vikas)nautilus
                     root       5214 ....m (root)vmnet-netifup
                     root       5224 ....m (root)vmnet-netifup
                     root       5245 ....m (root)vmnet-dhcpd
                     vikas      5250 .rce. (vikas)bonobo-activati
                     dhcp       5256 ....m (dhcp)dhclient3
                     root       5262 ....m (root)vmnet-dhcpd
                     vikas      5290 .rce. (vikas)gnome-vfs-daemo
                     vikas      5310 .rce. (vikas)mapping-daemon
                     vikas      5321 .rce. (vikas)tsclient-applet
                     vikas      5327 .rce. (vikas)gnome-terminal
                     vikas      5336 .rce. (vikas)gnome-netstatus
                     vikas      5338 frce. (vikas)tomboy
                     vikas      5340 .rce. (vikas)trashapplet
                     vikas      5342 frce. (vikas)deskbar-applet
                     vikas      5359 ....m (vikas)gnome-pty-helpe
                     vikas      5360 .rce. (vikas)bash
                     vikas      5385 .rce. (vikas)battstat-applet
                     vikas      5400 .rce. (vikas)mixer_applet2
                     vikas      5403 .rce. (vikas)gnome-screensav
                     vikas      5409 .rce. (vikas)gnome-power-man
                     vikas      5564 .rce. (vikas)mail-notificati
                     vikas      5566 .rce. (vikas)update-notifier
                     vikas      5568 .rce. (vikas)evolution-alarm
                     vikas      5574 .rce. (vikas)gnome-cups-icon
                     vikas      5588 .rce. (vikas)remind
                     vikas      5606 .rce. (vikas)evolution-excha
                     vikas      5611 Frce. (vikas)evolution-data-
                     cupsys     5920 ....m (cupsys)cupsd
                     vikas      8139 Frce. (vikas)firefox-bin
                     vikas      8790 .rce. (vikas)notification-da
                     root       9085 ....m (root)syslogd
-------------------

---

