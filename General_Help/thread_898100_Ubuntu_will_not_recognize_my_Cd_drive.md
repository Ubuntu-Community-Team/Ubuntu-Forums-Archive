---
title: "Ubuntu will not recognize my Cd drive"
date: 2008-08-22
forum: General Help
---

### Post by Dan6 on 2008-08-22
I'm trying to burn a cd and Ubuntu won't recognize my cd drive. I tried putting in an audio cd and nothing came up either. It's not hardware issues as I can still boot from the live cd. What can I do to get it to recognize me cd drive?

---

### Post by Dan6 on 2008-08-22
bump

---

### Post by mb_webguy on 2008-08-22
Type the command "cat /etc/fstab" in the terminal and post the output.

---

### Post by Dan6 on 2008-08-22
This is what I get 
dan@Dans:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#
proc /proc proc defaults 0 0
# /dev/sdb5
UUID=9afc1144-55e5-491d-a418-a74a5d3db6a0 / ext3
relatime,errors=remount-ro 0 1
# /dev/sda2
UUID=137b9667-6fd0-498d-ba5e-24ee21683c44 none swap sw
0 0
# /dev/sdb1
UUID=eec01c8b-ea86-46e6-9c8b-106ab0a7851b none swap sw
0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

---

### Post by mb_webguy on 2008-08-23
Well, I don't see anything obvious problems there...  (I'm assuming you have two optical drives on your computer...?)

What about the output of "mount"?

---

### Post by Dan6 on 2008-08-23
yea I do, this is what I get
dan@Dans:~$ mount
ext3 on / type unknown (rw,-t)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)

---

### Post by mb_webguy on 2008-08-23
Sorry...  I should have mentioned this, but could you put in a (non-blank) CD in the drive and try "mount" again?

---

### Post by Dan6 on 2008-08-23
I've got an audio cd in the drive right now

---

### Post by Dan6 on 2008-08-23
This is with my ubuntu cd
dan@Dans:~$ mount
ext3 on / type unknown (rw,-t)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)

---

### Post by mb_webguy on 2008-08-23
Okaaayyyy...

Let's try manually mounting the drive.  I don't know which of your drives it is -- and you *do* have two optical drives, right? -- so let's try both.  Type "sudo mount -t iso9660 /dev/hdc /media/cdrom0 && sudo mount -t iso9660 /dev/scd0 /media/cdrom1" and post the output.

---

### Post by Dan6 on 2008-08-23
this is what I get
dan@Dans:~$ sudo mount -t iso9660 /dev/hdc /media/cdrom0 
[sudo] password for dan: 
mount: special device /dev/hdc does not exist
and
dan@Dans:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom1
mount: special device /dev/scd0 does not exist

---

### Post by Dan6 on 2008-08-23
what do I do now?

---

### Post by mb_webguy on 2008-08-23
Interesting.  What do you get with "dmesg | grep CD"?

---

### Post by Dan6 on 2008-08-23
dan@Dans:~$ dmesg | grep CD
[   41.266288] hdd: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
[   42.050013] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
[  109.024904] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[  109.025174] Uniform CD-ROM driver Revision: 3.20

---

### Post by mb_webguy on 2008-08-23
Well, the system is at least recognizing the hardware...

Give me a few minutes to look up a few things and I'll get back to you.

---

### Post by Dan6 on 2008-08-23
ok

---

### Post by mb_webguy on 2008-08-23
Ok... let's see what devices are being recognized.  Since fstab seems to think that the drives are hdc and scd0, try "ls -l /dev | grep hdc; ls -l /dev | grep scd0; ls -l /dev | grep cd".

If that doesn't give you anything (and I pray to all that is warm and fluffy that it does), give me the output of "ls /dev".

---

### Post by Dan6 on 2008-08-23
dan@Dans:~$ ls -l /dev | grep hdc; ls -l /dev | grep scd0; ls -l /dev | grep cd
crw-rw-rw-  1 root   tty         2, 221 2008-08-22 23:36 ptycd
crw-rw-rw-  1 root   tty         3, 221 2008-08-22 23:36 ttycd

---

### Post by Dan6 on 2008-08-23
should I post results of ls /dev

---

### Post by mb_webguy on 2008-08-23
*insert mild expletive*

Ok, I was really hoping it wouldn't get to this, but...  Reboot, then type "gksu gedit /var/log/syslog" and post the contents.  Close that, then type "gksu gedit /var/log/dmesg" and post the contents.  

Then go to bed, or whatever would be appropriate for the time zone you're in.  

There's going to be a lot of data to sift through to see exactly what's going on, and I don't know that I'll be able to get to it until tomorrow.  And considering that it's late Friday night or very early Saturday morning for the majority of Ubuntu users, it's not incredibly likely anyone else will, either.

---

### Post by Dan6 on 2008-08-23
ok

---

### Post by Dan6 on 2008-08-23
Aug 22 13:02:30 Dans syslogd 1.5.0#1ubuntu1: restart.
Aug 22 13:02:30 Dans anacron[7538]: Job `cron.daily' terminated
Aug 22 13:02:30 Dans anacron[7538]: Normal exit (1 job run)
Aug 22 13:03:22 Dans kernel: [ 1661.159566] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:03:25 Dans kernel: [ 1664.158565] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:03:25 Dans kernel: [ 1664.158573] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:03:25 Dans kernel: [ 1664.158579] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:03:25 Dans kernel: [ 1664.158587] eth0:  Tx descriptor 1 is 0008a052.
Aug 22 13:03:25 Dans kernel: [ 1664.158592] eth0:  Tx descriptor 2 is 0008a10e.
Aug 22 13:03:25 Dans kernel: [ 1664.158597] eth0:  Tx descriptor 3 is 0008a0f7.
Aug 22 13:03:25 Dans kernel: [ 1664.158654] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:07:16 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 13:07:24 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Aug 22 13:07:39 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 13:07:47 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:07:47 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:10:22 Dans kernel: [ 2081.016269] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:10:25 Dans kernel: [ 2084.015262] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:10:25 Dans kernel: [ 2084.015270] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:10:25 Dans kernel: [ 2084.015278] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:10:25 Dans kernel: [ 2084.015283] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:10:25 Dans kernel: [ 2084.015289] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:10:25 Dans kernel: [ 2084.015294] eth0:  Tx descriptor 3 is 0008a10e.
Aug 22 13:10:25 Dans kernel: [ 2084.015377] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:15:14 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 22 13:15:18 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 13:15:26 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 13:15:34 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug 22 13:15:34 Dans kernel: [ 2392.909819] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:15:37 Dans kernel: [ 2395.908813] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:15:37 Dans kernel: [ 2395.908820] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:15:37 Dans kernel: [ 2395.908825] eth0:  Tx descriptor 0 is 0008a0f7. (queue head)
Aug 22 13:15:37 Dans kernel: [ 2395.908830] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:15:37 Dans kernel: [ 2395.908834] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:15:37 Dans kernel: [ 2395.908838] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 13:15:37 Dans kernel: [ 2395.908893] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:15:45 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:15:45 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:17:01 Dans /USR/SBIN/CRON[10556]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 13:18:15 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug 22 13:18:18 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 22 13:18:22 Dans kernel: [ 2560.852493] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:18:24 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 22 13:18:25 Dans kernel: [ 2563.851487] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:18:25 Dans kernel: [ 2563.851496] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:18:25 Dans kernel: [ 2563.851504] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:18:25 Dans kernel: [ 2563.851510] eth0:  Tx descriptor 1 is 0008a10e.
Aug 22 13:18:25 Dans kernel: [ 2563.851515] eth0:  Tx descriptor 2 is 0008a0f7.
Aug 22 13:18:25 Dans kernel: [ 2563.851522] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 13:18:25 Dans kernel: [ 2563.851581] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:18:31 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Aug 22 13:18:46 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:18:46 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:19:34 Dans kernel: [ 2632.827929] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:19:37 Dans kernel: [ 2635.826928] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:19:37 Dans kernel: [ 2635.826935] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:19:37 Dans kernel: [ 2635.826941] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:19:37 Dans kernel: [ 2635.826947] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:19:37 Dans kernel: [ 2635.826954] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:19:37 Dans kernel: [ 2635.826959] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 13:19:37 Dans kernel: [ 2635.827042] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:24:12 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 13:24:20 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Aug 22 13:24:39 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 22 13:24:43 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:24:43 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:27:22 Dans kernel: [ 3100.668253] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:27:25 Dans kernel: [ 3103.671245] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:27:25 Dans kernel: [ 3103.671253] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:27:25 Dans kernel: [ 3103.671261] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:27:25 Dans kernel: [ 3103.671267] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:27:25 Dans kernel: [ 3103.671272] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:27:25 Dans kernel: [ 3103.671279] eth0:  Tx descriptor 3 is 0008a10e.
Aug 22 13:27:25 Dans kernel: [ 3103.671339] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:30:47 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 13:30:55 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Aug 22 13:31:16 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Aug 22 13:31:18 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:31:18 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:31:22 Dans kernel: [ 3340.586370] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:31:25 Dans kernel: [ 3343.585358] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:31:25 Dans kernel: [ 3343.585366] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:31:25 Dans kernel: [ 3343.585374] eth0:  Tx descriptor 0 is 0008a0f7. (queue head)
Aug 22 13:31:25 Dans kernel: [ 3343.585382] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:31:25 Dans kernel: [ 3343.585387] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:31:25 Dans kernel: [ 3343.585393] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 13:31:25 Dans kernel: [ 3343.585452] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:36:46 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 22 13:36:51 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 22 13:37:01 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Aug 22 13:37:17 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:37:17 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:37:22 Dans kernel: [ 3700.463540] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:37:25 Dans kernel: [ 3703.462532] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:37:25 Dans kernel: [ 3703.462540] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:37:25 Dans kernel: [ 3703.462549] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:37:25 Dans kernel: [ 3703.462555] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:37:25 Dans kernel: [ 3703.462560] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:37:25 Dans kernel: [ 3703.462567] eth0:  Tx descriptor 3 is 0008a10e.
Aug 22 13:37:25 Dans kernel: [ 3703.462625] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:44:26 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 22 13:44:31 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 22 13:44:38 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 22 13:44:46 Dans kernel: [ 4144.312055] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:44:48 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug 22 13:44:49 Dans kernel: [ 4147.311052] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:44:49 Dans kernel: [ 4147.311059] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:44:49 Dans kernel: [ 4147.311066] eth0:  Tx descriptor 0 is 0008a0f7. (queue head)
Aug 22 13:44:49 Dans kernel: [ 4147.311072] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:44:49 Dans kernel: [ 4147.311077] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:44:49 Dans kernel: [ 4147.311082] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 13:44:49 Dans kernel: [ 4147.311140] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:44:57 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:44:57 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:47:50 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 22 13:47:56 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 22 13:48:06 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 22 13:48:16 Dans kernel: [ 4354.240403] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:48:19 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Aug 22 13:48:19 Dans kernel: [ 4357.239394] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:48:19 Dans kernel: [ 4357.239402] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:48:19 Dans kernel: [ 4357.239409] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:48:19 Dans kernel: [ 4357.239417] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:48:19 Dans kernel: [ 4357.239422] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:48:19 Dans kernel: [ 4357.239427] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 13:48:19 Dans kernel: [ 4357.239485] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:48:21 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:48:21 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:52:05 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 22 13:52:10 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 22 13:52:16 Dans kernel: [ 4594.162514] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:52:19 Dans kernel: [ 4597.157522] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:52:19 Dans kernel: [ 4597.157530] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:52:19 Dans kernel: [ 4597.157536] eth0:  Tx descriptor 0 is 0008a10e. (queue head)
Aug 22 13:52:19 Dans kernel: [ 4597.157542] eth0:  Tx descriptor 1 is 0008a0f7.
Aug 22 13:52:19 Dans kernel: [ 4597.157549] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:52:19 Dans kernel: [ 4597.157554] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 13:52:19 Dans kernel: [ 4597.157609] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:52:23 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 13:52:31 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 22 13:52:36 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:52:36 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:53:40 Dans kernel: [ 4678.129858] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:53:43 Dans kernel: [ 4681.128858] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:53:43 Dans kernel: [ 4681.128865] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:53:43 Dans kernel: [ 4681.128872] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:53:43 Dans kernel: [ 4681.128878] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:53:43 Dans kernel: [ 4681.128885] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:53:43 Dans kernel: [ 4681.128890] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 13:53:43 Dans kernel: [ 4681.128946] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 13:57:21 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 22 13:57:27 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug 22 13:57:38 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 22 13:57:51 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Aug 22 13:57:52 Dans dhclient: No DHCPOFFERS received.
Aug 22 13:57:52 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 13:57:58 Dans kernel: [ 4936.041833] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 13:58:01 Dans kernel: [ 4939.040829] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 13:58:01 Dans kernel: [ 4939.040837] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 13:58:01 Dans kernel: [ 4939.040844] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 13:58:01 Dans kernel: [ 4939.040852] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 13:58:01 Dans kernel: [ 4939.040857] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 13:58:01 Dans kernel: [ 4939.040862] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 13:58:01 Dans kernel: [ 4939.040919] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:02:09 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 22 14:02:15 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Aug 22 14:02:22 Dans kernel: [ 5199.951760] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:02:25 Dans kernel: [ 5202.950754] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:02:25 Dans kernel: [ 5202.950763] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:02:25 Dans kernel: [ 5202.950770] eth0:  Tx descriptor 0 is 0008a10e. (queue head)
Aug 22 14:02:25 Dans kernel: [ 5202.950776] eth0:  Tx descriptor 1 is 0008a0f7.
Aug 22 14:02:25 Dans kernel: [ 5202.950783] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:02:25 Dans kernel: [ 5202.950788] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:02:25 Dans kernel: [ 5202.950846] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:02:34 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 22 14:02:40 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:02:40 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:06:56 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 22 14:07:02 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 22 14:07:15 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug 22 14:07:22 Dans kernel: [ 5499.849400] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:07:24 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug 22 14:07:25 Dans kernel: [ 5502.848399] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:07:25 Dans kernel: [ 5502.848406] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:07:25 Dans kernel: [ 5502.848413] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:07:25 Dans kernel: [ 5502.848421] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 14:07:25 Dans kernel: [ 5502.848426] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:07:25 Dans kernel: [ 5502.848432] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:07:25 Dans kernel: [ 5502.848488] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:07:27 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:07:27 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:11:08 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 22 14:11:12 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug 22 14:11:23 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 22 14:11:30 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug 22 14:11:34 Dans kernel: [ 5751.763423] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:11:37 Dans kernel: [ 5754.762418] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:11:37 Dans kernel: [ 5754.762425] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:11:37 Dans kernel: [ 5754.762432] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:11:37 Dans kernel: [ 5754.762440] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 14:11:37 Dans kernel: [ 5754.762445] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:11:37 Dans kernel: [ 5754.762451] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:11:37 Dans kernel: [ 5754.762534] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:11:39 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:11:39 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:14:58 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 22 14:15:03 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 22 14:15:04 Dans kernel: [ 5961.691774] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:15:07 Dans kernel: [ 5964.690769] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:15:07 Dans kernel: [ 5964.690777] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:15:07 Dans kernel: [ 5964.690784] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:15:07 Dans kernel: [ 5964.690790] eth0:  Tx descriptor 1 is 0008a10e.
Aug 22 14:15:07 Dans kernel: [ 5964.690797] eth0:  Tx descriptor 2 is 0008a0f7.
Aug 22 14:15:07 Dans kernel: [ 5964.690802] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:15:07 Dans kernel: [ 5964.690860] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:15:16 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Aug 22 14:15:29 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:15:29 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:17:01 Dans /USR/SBIN/CRON[11408]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 14:18:59 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 22 14:19:03 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug 22 14:19:10 Dans kernel: [ 6207.607843] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:19:13 Dans kernel: [ 6210.606838] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:19:13 Dans kernel: [ 6210.606846] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:19:13 Dans kernel: [ 6210.606852] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:19:13 Dans kernel: [ 6210.606860] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 14:19:13 Dans kernel: [ 6210.606865] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:19:13 Dans kernel: [ 6210.606871] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:19:13 Dans kernel: [ 6210.606928] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:19:14 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Aug 22 14:19:30 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:19:30 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:25:54 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 14:26:02 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 14:26:04 Dans kernel: [ 6621.466591] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:26:07 Dans kernel: [ 6624.465584] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:26:07 Dans kernel: [ 6624.465591] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:26:07 Dans kernel: [ 6624.465598] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:26:07 Dans kernel: [ 6624.465606] eth0:  Tx descriptor 1 is 0008a10e.
Aug 22 14:26:07 Dans kernel: [ 6624.465611] eth0:  Tx descriptor 2 is 0008a0f7.
Aug 22 14:26:07 Dans kernel: [ 6624.465617] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:26:07 Dans kernel: [ 6624.465674] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:26:10 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Aug 22 14:26:25 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:26:25 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:30:48 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 22 14:30:52 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 22 14:30:57 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug 22 14:30:58 Dans kernel: [ 6915.366295] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:31:01 Dans kernel: [ 6918.365278] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:31:01 Dans kernel: [ 6918.365285] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:31:01 Dans kernel: [ 6918.365292] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:31:01 Dans kernel: [ 6918.365300] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 14:31:01 Dans kernel: [ 6918.365305] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:31:01 Dans kernel: [ 6918.365310] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:31:01 Dans kernel: [ 6918.365366] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:31:08 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Aug 22 14:31:19 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:31:19 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:33:49 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug 22 14:33:52 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 22 14:33:58 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Aug 22 14:33:58 Dans kernel: [ 7095.304869] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:34:01 Dans kernel: [ 7098.303863] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:34:01 Dans kernel: [ 7098.303870] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:34:01 Dans kernel: [ 7098.303877] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:34:01 Dans kernel: [ 7098.303886] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 14:34:01 Dans kernel: [ 7098.303891] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:34:01 Dans kernel: [ 7098.303896] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:34:01 Dans kernel: [ 7098.303953] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:34:10 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 22 14:34:20 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:34:20 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:36:22 Dans kernel: [ 7239.255732] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:36:25 Dans kernel: [ 7242.258723] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:36:25 Dans kernel: [ 7242.258731] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:36:25 Dans kernel: [ 7242.258740] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:36:25 Dans kernel: [ 7242.258746] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 14:36:25 Dans kernel: [ 7242.258751] eth0:  Tx descriptor 2 is 0008a10e.
Aug 22 14:36:25 Dans kernel: [ 7242.258757] eth0:  Tx descriptor 3 is 0008a0f7.
Aug 22 14:36:25 Dans kernel: [ 7242.258816] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:41:11 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 22 14:41:16 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 22 14:41:23 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Aug 22 14:41:41 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
Aug 22 14:41:42 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:41:42 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:41:52 Dans kernel: [ 7569.143146] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:41:55 Dans kernel: [ 7572.142146] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:41:55 Dans kernel: [ 7572.142154] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:41:55 Dans kernel: [ 7572.142161] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:41:55 Dans kernel: [ 7572.142170] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 14:41:55 Dans kernel: [ 7572.142175] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:41:55 Dans kernel: [ 7572.142180] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:41:55 Dans kernel: [ 7572.142237] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:44:39 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Aug 22 14:44:45 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 14:44:53 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Aug 22 14:45:03 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 22 14:45:10 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:45:10 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:45:10 Dans kernel: [ 7767.079584] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:45:13 Dans kernel: [ 7770.074597] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:45:13 Dans kernel: [ 7770.074607] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:45:13 Dans kernel: [ 7770.074614] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:45:13 Dans kernel: [ 7770.074621] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 14:45:13 Dans kernel: [ 7770.074628] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:45:13 Dans kernel: [ 7770.074633] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:45:13 Dans kernel: [ 7770.074691] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:52:07 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 22 14:52:14 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Aug 22 14:52:22 Dans kernel: [ 8198.928216] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:52:25 Dans kernel: [ 8201.927191] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:52:25 Dans kernel: [ 8201.927199] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:52:25 Dans kernel: [ 8201.927205] eth0:  Tx descriptor 0 is 0008a10e. (queue head)
Aug 22 14:52:25 Dans kernel: [ 8201.927211] eth0:  Tx descriptor 1 is 0008a0f7.
Aug 22 14:52:25 Dans kernel: [ 8201.927218] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:52:25 Dans kernel: [ 8201.927223] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:52:25 Dans kernel: [ 8201.927282] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:52:34 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 22 14:52:38 Dans dhclient: No DHCPOFFERS received.
Aug 22 14:52:38 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 14:59:34 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 22 14:59:38 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 14:59:46 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Aug 22 14:59:46 Dans kernel: [ 8642.776704] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 14:59:49 Dans kernel: [ 8645.775712] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 14:59:49 Dans kernel: [ 8645.775719] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 14:59:49 Dans kernel: [ 8645.775726] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 14:59:49 Dans kernel: [ 8645.775734] eth0:  Tx descriptor 1 is 0008a052.
Aug 22 14:59:49 Dans kernel: [ 8645.775740] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 14:59:49 Dans kernel: [ 8645.775745] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 14:59:49 Dans kernel: [ 8645.775800] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 14:59:55 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Aug 22 15:00:02 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug 22 15:00:05 Dans dhclient: No DHCPOFFERS received.
Aug 22 15:00:05 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 15:00:22 Dans kernel: [ 8678.764425] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 15:00:25 Dans kernel: [ 8681.763415] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 15:00:25 Dans kernel: [ 8681.763423] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 15:00:25 Dans kernel: [ 8681.763432] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 15:00:25 Dans kernel: [ 8681.763438] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 15:00:25 Dans kernel: [ 8681.763443] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 15:00:25 Dans kernel: [ 8681.763447] eth0:  Tx descriptor 3 is 0008a10e.
Aug 22 15:00:25 Dans kernel: [ 8681.763506] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 15:05:21 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Aug 22 15:05:26 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 15:05:34 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Aug 22 15:05:40 Dans kernel: [ 8996.655924] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 15:05:43 Dans kernel: [ 8999.658913] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 15:05:43 Dans kernel: [ 8999.658920] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 15:05:43 Dans kernel: [ 8999.658929] eth0:  Tx descriptor 0 is 0008a0f7. (queue head)
Aug 22 15:05:43 Dans kernel: [ 8999.658935] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 15:05:43 Dans kernel: [ 8999.658941] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 15:05:43 Dans kernel: [ 8999.658948] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 15:05:43 Dans kernel: [ 8999.659005] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 15:05:52 Dans dhclient: No DHCPOFFERS received.
Aug 22 15:05:52 Dans dhclient: No working leases in persistent database - sleeping.
Aug 22 15:11:29 Dans kernel: [ 9345.774430] usb 3-7: USB disconnect, address 3
Aug 22 15:11:29 Dans avahi-daemon[7151]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug 22 15:11:29 Dans avahi-daemon[7151]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 22 15:11:29 Dans kernel: [ 9345.784815] zd1211rw 3-7:1.0: error ioread32(CR_REG1): -22
Aug 22 15:11:29 Dans dhclient: receive_packet failed on eth1: Network is down
Aug 22 15:11:30 Dans NetworkManager: <debug> [1219432290.031914] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_17_3f_34_c1_de'). 
Aug 22 15:11:30 Dans avahi-daemon[7151]: Withdrawing address record for fe80::217:3fff:fe34:c1de on eth1.
Aug 22 15:11:30 Dans avahi-daemon[7151]: Withdrawing address record for 192.168.2.10 on eth1.
Aug 22 15:11:30 Dans NetworkManager: <debug> [1219432290.049175] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_50d_705c_noserial_if0'). 
Aug 22 15:11:30 Dans NetworkManager: <debug> [1219432290.055103] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_50d_705c_noserial'). 
Aug 22 15:11:38 Dans kernel: [ 9354.331757] usb 3-7: new high speed USB device using ehci_hcd and address 5
Aug 22 15:11:38 Dans kernel: [ 9354.135059] usb 3-7: configuration #1 chosen from 1 choice
Aug 22 15:11:38 Dans NetworkManager: <debug> [1219432298.353383] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_50d_705c_noserial'). 
Aug 22 15:11:38 Dans NetworkManager: <debug> [1219432298.435504] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Aug 22 15:11:38 Dans kernel: [ 9354.249894] usb 3-7: reset high speed USB device using ehci_hcd and address 5
Aug 22 15:11:38 Dans kernel: [ 9354.384103] zd1211rw 3-7:1.0: eth1
Aug 22 15:11:38 Dans NetworkManager: <debug> [1219432298.607280] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_17_3f_34_c1_de'). 
Aug 22 15:11:38 Dans kernel: [ 9354.456464] zd1211rw 3-7:1.0: firmware version 4725
Aug 22 15:11:38 Dans kernel: [ 9354.496468] zd1211rw 3-7:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
Aug 22 15:11:38 Dans kernel: [ 9354.515564] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 22 15:11:46 Dans kernel: [ 9362.531050] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 15:11:49 Dans kernel: [ 9365.531758] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 15:11:49 Dans kernel: [ 9365.531766] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 15:11:49 Dans kernel: [ 9365.531775] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Aug 22 15:11:49 Dans kernel: [ 9365.531781] eth0:  Tx descriptor 1 is 0008a03c.
Aug 22 15:11:49 Dans kernel: [ 9365.531786] eth0:  Tx descriptor 2 is 0008a03c.
Aug 22 15:11:49 Dans kernel: [ 9365.531792] eth0:  Tx descriptor 3 is 0008a03c.
Aug 22 15:11:49 Dans kernel: [ 9365.531850] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 15:11:52 Dans init: tty4 main process (6699) killed by TERM signal
Aug 22 15:11:52 Dans init: tty5 main process (6700) killed by TERM signal
Aug 22 15:11:52 Dans init: tty2 main process (6702) killed by TERM signal
Aug 22 15:11:52 Dans init: tty3 main process (6704) killed by TERM signal
Aug 22 15:11:52 Dans init: tty6 main process (6706) killed by TERM signal
Aug 22 15:11:52 Dans init: tty1 main process (7672) killed by TERM signal
Aug 22 15:11:53 Dans gdm[7513]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Aug 22 15:11:53 Dans gdm[7513]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Aug 22 15:11:55 Dans avahi-daemon[7151]: Got SIGTERM, quitting.
Aug 22 15:11:55 Dans avahi-daemon[7151]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.5.131.
Aug 22 15:11:57 Dans kernel: [ 9373.335147] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 22 15:11:58 Dans kernel: [ 9374.526953] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 15:11:58 Dans exiting on signal 15
Aug 22 15:24:16 Dans syslogd 1.5.0#1ubuntu1: restart.
Aug 22 15:24:16 Dans kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 22 15:24:16 Dans kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 22 15:24:16 Dans kernel: Symbols match kernel version 2.6.24.
Aug 22 15:24:16 Dans kernel: Loaded 20039 symbols from 92 modules.
Aug 22 15:24:16 Dans kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 22 15:24:16 Dans kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 22 15:24:16 Dans kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 22 15:24:16 Dans kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 22 15:24:16 Dans kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 22 15:24:16 Dans kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 22 15:24:16 Dans kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Aug 22 15:24:16 Dans kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bfd0000 (usable)
Aug 22 15:24:16 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfd0000 - 000000007bfde000 (ACPI data)
Aug 22 15:24:16 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfde000 - 000000007c000000 (ACPI NVS)
Aug 22 15:24:16 Dans kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 22 15:24:16 Dans kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Aug 22 15:24:16 Dans kernel: [    0.000000] 1087MB HIGHMEM available.
Aug 22 15:24:16 Dans kernel: [    0.000000] 896MB LOWMEM available.
Aug 22 15:24:16 Dans kernel: [    0.000000] found SMP MP-table at 000ff780
Aug 22 15:24:16 Dans kernel: [    0.000000] Entering add_active_range(0, 0, 507856) 0 entries of 256 used
Aug 22 15:24:16 Dans kernel: [    0.000000] Zone PFN ranges:
Aug 22 15:24:16 Dans kernel: [    0.000000]   DMA             0 ->     4096
Aug 22 15:24:16 Dans kernel: [    0.000000]   Normal       4096 ->   229376
Aug 22 15:24:16 Dans kernel: [    0.000000]   HighMem    229376 ->   507856
Aug 22 15:24:16 Dans kernel: [    0.000000] Movable zone start PFN for each node
Aug 22 15:24:16 Dans kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 22 15:24:16 Dans kernel: [    0.000000]     0:        0 ->   507856
Aug 22 15:24:16 Dans kernel: [    0.000000] On node 0 totalpages: 507856
Aug 22 15:24:16 Dans kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 22 15:24:16 Dans kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 22 15:24:16 Dans kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 22 15:24:16 Dans kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 22 15:24:16 Dans kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 22 15:24:16 Dans kernel: [    0.000000]   HighMem zone: 2175 pages used for memmap
Aug 22 15:24:16 Dans kernel: [    0.000000]   HighMem zone: 276305 pages, LIFO batch:31
Aug 22 15:24:16 Dans kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 22 15:24:16 Dans kernel: [    0.000000] DMI present.
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8890 checksum 0
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: RSDP 000F8890, 0014 (r0 HP-CPC)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: RSDT 7BFD0000, 0038 (r1 HP-CPC OEMRSDT  11000518 MSFT       97)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: FACP 7BFD0200, 0084 (r2 HP-CPC OEMFACP  11000518 MSFT       97)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: DSDT 7BFD0440, 43B0 (r1 HP-CPC  RC410-M        0 INTL  2002026)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: FACS 7BFDE000, 0040
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: APIC 7BFD0390, 006C (r1 HP-CPC OEMAPIC  11000518 MSFT       97)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: MCFG 7BFD0400, 003C (r1 HP-CPC OEMMCFG  11000518 MSFT       97)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: OEMB 7BFDE040, 005B (r1 HP-CPC AMI_OEM  11000518 MSFT       97)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: HPET 7BFD47F0, 0038 (r1 HP-CPC OEMHPET  11000518 MSFT       97)
Aug 22 15:24:16 Dans kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 22 15:24:16 Dans kernel: [    0.000000] Processor #0 15:4 APIC version 20
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 22 15:24:16 Dans kernel: [    0.000000] Processor #1 15:4 APIC version 20
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
Aug 22 15:24:16 Dans kernel: [    0.000000] ACPI: HPET id: 0x0 base: 0xfed00000
Aug 22 15:24:16 Dans kernel: [    0.000000] Using ACPI for processor (LAPIC) configuration information
Aug 22 15:24:16 Dans kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Aug 22 15:24:16 Dans kernel: [    0.000000]     Virtual Wire compatibility mode.
Aug 22 15:24:16 Dans kernel: [    0.000000] OEM ID: ATI      Product ID: RS400        APIC at: 0xFEE00000
Aug 22 15:24:16 Dans kernel: [    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
Aug 22 15:24:16 Dans kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 22 15:24:16 Dans kernel: [    0.000000] Processors: 2
Aug 22 15:24:16 Dans kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7c000000:82e00000)
Aug 22 15:24:16 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 22 15:24:16 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
Aug 22 15:24:16 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Aug 22 15:24:16 Dans kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503889
Aug 22 15:24:16 Dans kernel: [    0.000000] Kernel command line: root=UUID=e9a7cff5-d8ae-4fb4-a348-d2db06aed623 ro quiet splash noapic
Aug 22 15:24:16 Dans kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 22 15:24:16 Dans kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 22 15:24:16 Dans kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 22 15:24:16 Dans kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 22 15:24:16 Dans kernel: [    0.000000] Initializing CPU#0
Aug 22 15:24:16 Dans kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 22 15:24:16 Dans kernel: [    0.000000] Detected 3199.345 MHz processor.
Aug 22 15:24:16 Dans kernel: [  343.731865] Console: colour VGA+ 80x25
Aug 22 15:24:16 Dans kernel: [  343.731869] console [tty0] enabled
Aug 22 15:24:16 Dans kernel: [  343.733474] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 22 15:24:16 Dans kernel: [  343.734200] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 22 15:24:16 Dans kernel: [  343.842130] Memory: 2001980k/2031424k available (2177k kernel code, 28188k reserved, 1006k data, 368k init, 1113920k highmem)
Aug 22 15:24:16 Dans kernel: [  343.842141] virtual kernel memory layout:
Aug 22 15:24:16 Dans kernel: [  343.842142]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 22 15:24:16 Dans kernel: [  343.842143]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 22 15:24:16 Dans kernel: [  343.842144]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 22 15:24:16 Dans kernel: [  343.842145]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 22 15:24:16 Dans kernel: [  343.842146]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 22 15:24:16 Dans kernel: [  343.842147]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 22 15:24:16 Dans kernel: [  343.842148]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 22 15:24:16 Dans kernel: [  343.842151] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 22 15:24:16 Dans kernel: [  343.842221] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 22 15:24:16 Dans kernel: [  343.842331] hpet clockevent registered
Aug 22 15:24:16 Dans kernel: [  344.895080] Calibrating delay using timer specific routine.. 88488.95 BogoMIPS (lpj=176977918)
Aug 22 15:24:16 Dans kernel: [  344.895112] Security Framework initialized
Aug 22 15:24:16 Dans kernel: [  344.895121] SELinux:  Disabled at boot.
Aug 22 15:24:16 Dans kernel: [  344.895141] AppArmor: AppArmor initialized
Aug 22 15:24:16 Dans kernel: [  344.895146] Failure registering capabilities with primary security module.
Aug 22 15:24:16 Dans kernel: [  344.895156] Mount-cache hash table entries: 512
Aug 22 15:24:16 Dans kernel: [  344.895317] Initializing cgroup subsys ns
Aug 22 15:24:16 Dans kernel: [  344.895323] Initializing cgroup subsys cpuacct
Aug 22 15:24:16 Dans kernel: [  344.895338] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 22 15:24:16 Dans kernel: [  344.895348] monitor/mwait feature present.
Aug 22 15:24:16 Dans kernel: [  344.895349] using mwait in idle threads.
Aug 22 15:24:16 Dans kernel: [  344.895356] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 22 15:24:16 Dans kernel: [  344.895359] CPU: L2 cache: 2048K
Aug 22 15:24:16 Dans kernel: [  344.895361] CPU: Physical Processor ID: 0
Aug 22 15:24:16 Dans kernel: [  344.895364] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 22 15:24:16 Dans kernel: [  344.895376] Compat vDSO mapped to ffffe000.
Aug 22 15:24:16 Dans kernel: [  344.895395] Checking 'hlt' instruction... OK.
Aug 22 15:24:16 Dans kernel: [  345.115219] SMP alternatives: switching to UP code
Aug 22 15:24:16 Dans kernel: [  345.117149] Early unpacking initramfs... done
Aug 22 15:24:16 Dans kernel: [  345.402573] ACPI: Core revision 20070126
Aug 22 15:24:16 Dans kernel: [  345.402634] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 22 15:24:16 Dans kernel: [  345.404494] ACPI: setting ELCR to 0200 (from 0c38)
Aug 22 15:24:16 Dans kernel: [  345.405157] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 22 15:24:16 Dans kernel: [  345.405179] SMP alternatives: switching to SMP code
Aug 22 15:24:16 Dans kernel: [  345.406012] Booting processor 1/1 eip 3000
Aug 22 15:24:16 Dans kernel: [  345.766158] Initializing CPU#1
Aug 22 15:24:16 Dans kernel: [  346.817268] Calibrating delay using timer specific routine.. 87884.55 BogoMIPS (lpj=175769109)
Aug 22 15:24:16 Dans kernel: [  346.817279] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 22 15:24:16 Dans kernel: [  346.817286] monitor/mwait feature present.
Aug 22 15:24:16 Dans kernel: [  346.817293] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 22 15:24:16 Dans kernel: [  346.817295] CPU: L2 cache: 2048K
Aug 22 15:24:16 Dans kernel: [  346.817298] CPU: Physical Processor ID: 0
Aug 22 15:24:16 Dans kernel: [  346.817300] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 22 15:24:16 Dans kernel: [  346.488060] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 22 15:24:16 Dans kernel: [  346.488104] Total of 2 processors activated (176373.51 BogoMIPS).
Aug 22 15:24:16 Dans kernel: [  347.969988] APIC calibration not consistent with PM Timer: 1373ms instead of 100ms
Aug 22 15:24:16 Dans kernel: [  347.969992] APIC delta adjusted to PM-Timer: 1249643 (17159307)
Aug 22 15:24:16 Dans kernel: [  347.970143] checking TSC synchronization [CPU#0 -> CPU#1]:
Aug 22 15:24:16 Dans kernel: [  347.990145] Measured 1055513456 cycles TSC warp between CPUs, turning off TSC clock.
Aug 22 15:24:16 Dans kernel: [  347.990149] Marking TSC unstable due to: check_tsc_sync_source failed.
Aug 22 15:24:16 Dans kernel: [  347.990168] Brought up 2 CPUs
Aug 22 15:24:16 Dans kernel: [  347.990189] CPU0 attaching sched-domain:
Aug 22 15:24:16 Dans kernel: [  347.990193]  domain 0: span 03
Aug 22 15:24:16 Dans kernel: [  347.990195]   groups: 01 02
Aug 22 15:24:16 Dans kernel: [  347.990199]   domain 1: span 03
Aug 22 15:24:16 Dans kernel: [  347.990201]    groups: 03
Aug 22 15:24:16 Dans kernel: [  347.990203] CPU1 attaching sched-domain:
Aug 22 15:24:16 Dans kernel: [  347.990205]  domain 0: span 03
Aug 22 15:24:16 Dans kernel: [  347.990206]   groups: 02 01
Aug 22 15:24:16 Dans kernel: [  347.990209]   domain 1: span 03
Aug 22 15:24:16 Dans kernel: [  347.990211]    groups: 03
Aug 22 15:24:16 Dans kernel: [  347.990487] net_namespace: 64 bytes
Aug 22 15:24:16 Dans kernel: [  347.990497] Booting paravirtualized kernel on bare hardware
Aug 22 15:24:16 Dans kernel: [  347.991084] Time: 19:17:56  Date: 08/22/08
Aug 22 15:24:16 Dans kernel: [  347.991111] NET: Registered protocol family 16
Aug 22 15:24:16 Dans kernel: [  347.991371] EISA bus registered
Aug 22 15:24:16 Dans kernel: [  347.991377] ACPI: bus type pci registered
Aug 22 15:24:16 Dans kernel: [  347.991600] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
Aug 22 15:24:16 Dans kernel: [  347.991602] PCI: Using configuration type 1
Aug 22 15:24:16 Dans kernel: [  347.991619] Setting up standard PCI resources
Aug 22 15:24:16 Dans kernel: [  348.004015] ACPI: EC: Look up EC in DSDT
Aug 22 15:24:16 Dans kernel: [  348.010248] ACPI: Interpreter enabled
Aug 22 15:24:16 Dans kernel: [  348.010252] ACPI: (supports S0 S1 S3 S4 S5)
Aug 22 15:24:16 Dans kernel: [  348.010270] ACPI: Using PIC for interrupt routing
Aug 22 15:24:16 Dans kernel: [  348.020712] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 22 15:24:16 Dans kernel: [  348.022344] PCI: Transparent bridge - 0000:00:14.4
Aug 22 15:24:16 Dans kernel: [  348.022382] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 22 15:24:16 Dans kernel: [  348.022515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Aug 22 15:24:16 Dans kernel: [  348.022617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Aug 22 15:24:16 Dans kernel: [  348.029044] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *4 5 7 10 11 12 14 15)
Aug 22 15:24:16 Dans kernel: [  348.029156] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 22 15:24:16 Dans kernel: [  348.029267] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 22 15:24:16 Dans kernel: [  348.029377] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
Aug 22 15:24:16 Dans kernel: [  348.029491] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 *15)
Aug 22 15:24:16 Dans kernel: [  348.029602] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
Aug 22 15:24:16 Dans kernel: [  348.029708] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
Aug 22 15:24:16 Dans kernel: [  348.029817] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
Aug 22 15:24:16 Dans kernel: [  348.029962] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  A8, should be 9C [20070126]
Aug 22 15:24:16 Dans kernel: [  348.029975] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 22 15:24:16 Dans kernel: [  348.030021] pnp: PnP ACPI init
Aug 22 15:24:16 Dans kernel: [  348.030031] ACPI: bus type pnp registered
Aug 22 15:24:16 Dans kernel: [  348.036506] pnp: PnP ACPI: found 14 devices
Aug 22 15:24:16 Dans kernel: [  348.036509] ACPI: ACPI bus type pnp unregistered
Aug 22 15:24:16 Dans kernel: [  348.036514] PnPBIOS: Disabled by ACPI PNP
Aug 22 15:24:16 Dans kernel: [  348.366681] PCI: Using ACPI for IRQ routing
Aug 22 15:24:16 Dans kernel: [  348.366685] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 22 15:24:16 Dans kernel: [  348.366693] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Aug 22 15:24:16 Dans kernel: [  348.403995] NET: Registered protocol family 8
Aug 22 15:24:16 Dans kernel: [  348.403998] NET: Registered protocol family 20
Aug 22 15:24:16 Dans kernel: [  348.404048] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 22 15:24:16 Dans kernel: [  348.404054] hpet0: 4 32-bit timers, 14318180 Hz
Aug 22 15:24:16 Dans kernel: [  348.405100] AppArmor: AppArmor Filesystem Enabled
Aug 22 15:24:16 Dans kernel: [  348.077985] Time: hpet clocksource has been installed.
Aug 22 15:24:16 Dans kernel: [  348.078001] Switched to high resolution mode on CPU 0
Aug 22 15:24:16 Dans kernel: [  348.408000] Switched to high resolution mode on CPU 1
Aug 22 15:24:16 Dans kernel: [  348.420884] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420888] system 00:07: ioport range 0x40b-0x40b has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420891] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420894] system 00:07: ioport range 0xc00-0xc01 has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420896] system 00:07: ioport range 0xc14-0xc14 has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420899] system 00:07: ioport range 0xc50-0xc51 has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420902] system 00:07: ioport range 0xc52-0xc52 has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420904] system 00:07: ioport range 0xc6c-0xc6c has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420907] system 00:07: ioport range 0xc6f-0xc6f has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420910] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420917] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420919] system 00:07: ioport range 0xcd8-0xcdf has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420922] system 00:07: ioport range 0x800-0x89f has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420924] system 00:07: ioport range 0x900-0x90f has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420927] system 00:07: ioport range 0x910-0x91f has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420930] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
Aug 22 15:24:16 Dans kernel: [  348.420938] system 00:0a: ioport range 0xa00-0xa0f has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420940] system 00:0a: ioport range 0xa10-0xa1f has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420942] system 00:0a: ioport range 0xa20-0xa2f has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420945] system 00:0a: ioport range 0xa30-0xa3f has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420951] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420954] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 22 15:24:16 Dans kernel: [  348.420960] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Aug 22 15:24:16 Dans kernel: [  348.420966] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Aug 22 15:24:16 Dans kernel: [  348.420969] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Aug 22 15:24:16 Dans kernel: [  348.420972] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Aug 22 15:24:16 Dans kernel: [  348.420974] system 00:0d: iomem range 0x100000-0x7bffffff could not be reserved
Aug 22 15:24:16 Dans kernel: [  348.420977] system 00:0d: iomem range 0x0-0x0 could not be reserved
Aug 22 15:24:16 Dans kernel: [  348.121721] PCI: Bridge: 0000:00:01.0
Aug 22 15:24:16 Dans kernel: [  348.121724]   IO window: d000-dfff
Aug 22 15:24:16 Dans kernel: [  348.121728]   MEM window: fea00000-feafffff
Aug 22 15:24:16 Dans kernel: [  348.121732]   PREFETCH window: d0000000-dfffffff
Aug 22 15:24:16 Dans kernel: [  348.121747] PCI: Bridge: 0000:00:14.4
Aug 22 15:24:16 Dans kernel: [  348.121751]   IO window: e000-efff
Aug 22 15:24:16 Dans kernel: [  348.121758]   MEM window: feb00000-febfffff
Aug 22 15:24:16 Dans kernel: [  348.121763]   PREFETCH window: disabled.
Aug 22 15:24:16 Dans kernel: [  348.121795] NET: Registered protocol family 2
Aug 22 15:24:16 Dans kernel: [  348.166032] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 22 15:24:16 Dans kernel: [  348.166385] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 22 15:24:16 Dans kernel: [  348.167017] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 22 15:24:16 Dans kernel: [  348.167421] TCP: Hash tables configured (established 131072 bind 65536)
Aug 22 15:24:16 Dans kernel: [  348.167423] TCP reno registered
Aug 22 15:24:16 Dans kernel: [  348.178119] checking if image is initramfs... it is
Aug 22 15:24:16 Dans kernel: [  348.747519] Freeing initrd memory: 7312k freed
Aug 22 15:24:16 Dans kernel: [  349.078408] audit: initializing netlink socket (disabled)
Aug 22 15:24:16 Dans kernel: [  349.078431] audit(1219432671.960:1): initialized
Aug 22 15:24:16 Dans kernel: [  349.078717] highmem bounce pool size: 64 pages
Aug 22 15:24:16 Dans kernel: [  348.751380] VFS: Disk quotas dquot_6.5.1
Aug 22 15:24:16 Dans kernel: [  348.751474] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 22 15:24:16 Dans kernel: [  348.751632] io scheduler noop registered
Aug 22 15:24:16 Dans kernel: [  348.751634] io scheduler anticipatory registered
Aug 22 15:24:16 Dans kernel: [  348.751636] io scheduler deadline registered
Aug 22 15:24:16 Dans kernel: [  348.751648] io scheduler cfq registered (default)
Aug 22 15:24:16 Dans kernel: [  348.751659] PCI: MSI quirk detected. MSI deactivated.
Aug 22 15:24:16 Dans kernel: [  348.809819] Boot video device is 0000:01:05.0
Aug 22 15:24:16 Dans kernel: [  348.810191] isapnp: Scanning for PnP cards...
Aug 22 15:24:16 Dans kernel: [  349.871073] isapnp: No Plug & Play device found
Aug 22 15:24:16 Dans kernel: [  349.909187] Real Time Clock Driver v1.12ac
Aug 22 15:24:16 Dans kernel: [  349.909323] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 22 15:24:16 Dans kernel: [  350.240753] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 22 15:24:16 Dans kernel: [  350.240837] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 22 15:24:16 Dans kernel: [  350.240967] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Aug 22 15:24:16 Dans kernel: [  349.914902] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 22 15:24:16 Dans kernel: [  349.914909] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 22 15:24:16 Dans kernel: [  349.937482] mice: PS/2 mouse device common for all mice
Aug 22 15:24:16 Dans kernel: [  349.937641] EISA: Probing bus 0 at eisa.0
Aug 22 15:24:16 Dans kernel: [  349.937655] Cannot allocate resource for EISA slot 2
Aug 22 15:24:16 Dans kernel: [  349.937657] Cannot allocate resource for EISA slot 3
Aug 22 15:24:16 Dans kernel: [  349.937659] Cannot allocate resource for EISA slot 4
Aug 22 15:24:16 Dans kernel: [  349.937661] Cannot allocate resource for EISA slot 5
Aug 22 15:24:16 Dans kernel: [  349.937663] Cannot allocate resource for EISA slot 6
Aug 22 15:24:16 Dans kernel: [  349.937665] Cannot allocate resource for EISA slot 7
Aug 22 15:24:16 Dans kernel: [  349.937666] Cannot allocate resource for EISA slot 8
Aug 22 15:24:16 Dans kernel: [  349.937668] EISA: Detected 0 cards.
Aug 22 15:24:16 Dans kernel: [  349.937673] cpuidle: using governor ladder
Aug 22 15:24:16 Dans kernel: [  349.937674] cpuidle: using governor menu
Aug 22 15:24:16 Dans kernel: [  349.937766] NET: Registered protocol family 1
Aug 22 15:24:16 Dans kernel: [  349.937798] Using IPI No-Shortcut mode
Aug 22 15:24:16 Dans kernel: [  349.937834] registered taskstats version 1
Aug 22 15:24:16 Dans kernel: [  349.937944]   Magic number: 4:401:294
Aug 22 15:24:16 Dans kernel: [  349.937948]   hash matches device hpet
Aug 22 15:24:16 Dans kernel: [  349.937961]   hash matches device ttyz8
Aug 22 15:24:16 Dans kernel: [  349.937972]   hash matches device ttywb
Aug 22 15:24:16 Dans kernel: [  349.938075]   hash matches device tty27
Aug 22 15:24:16 Dans kernel: [  349.938096] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 22 15:24:16 Dans kernel: [  349.938099] EDD information not available.
Aug 22 15:24:16 Dans kernel: [  349.938501] Freeing unused kernel memory: 368k freed
Aug 22 15:24:16 Dans kernel: [  350.285900] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 22 15:24:16 Dans kernel: [  351.161505] fuse init (API version 7.9)
Aug 22 15:24:16 Dans kernel: [  351.514765] ACPI: SSDT 7BFD4830, 02FE (r1    AMI   CPU1PM        1 INTL  2002026)
Aug 22 15:24:16 Dans kernel: [  351.514968] ACPI: duty_cycle spans bit 4
Aug 22 15:24:16 Dans kernel: [  351.515036] ACPI: SSDT 7BFD4B30, 02FE (r1    AMI   CPU2PM        1 INTL  2002026)
Aug 22 15:24:16 Dans kernel: [  351.515219] ACPI: duty_cycle spans bit 4
Aug 22 15:24:16 Dans kernel: [  351.515238] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 22 15:24:16 Dans kernel: [  351.515251] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 22 15:24:16 Dans kernel: [  351.350037] SCSI subsystem initialized
Aug 22 15:24:16 Dans kernel: [  351.405045] libata version 3.00 loaded.
Aug 22 15:24:16 Dans kernel: [  351.417011] sata_sil 0000:00:11.0: version 2.3
Aug 22 15:24:16 Dans kernel: [  351.417310] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
Aug 22 15:24:16 Dans ntpdate[8600]: adjust time server 91.189.94.4 offset 0.270010 sec
Aug 22 15:24:16 Dans kernel: [  351.417315] PCI: setting IRQ 5 as level-triggered
Aug 22 15:24:16 Dans kernel: [  351.417321] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 22 15:24:16 Dans kernel: [  351.425529] scsi0 : sata_sil
Aug 22 15:24:16 Dans kernel: [  351.430555] scsi1 : sata_sil
Aug 22 15:24:16 Dans kernel: [  351.430621] ata1: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff080 irq 5
Aug 22 15:24:16 Dans kernel: [  351.430627] ata2: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff0c0 irq 5
Aug 22 15:24:16 Dans kernel: [  351.926274] usbcore: registered new interface driver usbfs
Aug 22 15:24:16 Dans kernel: [  351.926317] usbcore: registered new interface driver hub
Aug 22 15:24:16 Dans kernel: [  351.927053] usbcore: registered new device driver usb
Aug 22 15:24:16 Dans kernel: [  351.929411] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 22 15:24:16 Dans kernel: [  351.740800] ata1: SATA link down (SStatus 0 SControl 310)
Aug 22 15:24:16 Dans kernel: [  351.786038] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 22 15:24:16 Dans kernel: [  351.786046] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 22 15:24:16 Dans kernel: [  351.789797] 8139too Fast Ethernet driver 0.9.28
Aug 22 15:24:16 Dans kernel: [  351.876716] FDC 0 is a post-1991 82077
Aug 22 15:24:16 Dans kernel: [  352.387566] ata2: SATA link down (SStatus 0 SControl 310)
Aug 22 15:24:16 Dans kernel: [  352.058136] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
Aug 22 15:24:16 Dans kernel: [  352.058143] PCI: setting IRQ 11 as level-triggered
Aug 22 15:24:16 Dans kernel: [  352.058149] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
Aug 22 15:24:16 Dans kernel: [  352.058938] scsi2 : sata_sil
Aug 22 15:24:16 Dans kernel: [  352.059646] scsi3 : sata_sil
Aug 22 15:24:16 Dans kernel: [  352.059691] ata3: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff880 irq 11
Aug 22 15:24:16 Dans kernel: [  352.059695] ata4: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff8c0 irq 11
Aug 22 15:24:16 Dans kernel: [  352.524531] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug 22 15:24:16 Dans kernel: [  352.533109] ata3.00: ATA-7: WDC WD2500JS-60MHB1, 10.02E02, max UDMA/100
Aug 22 15:24:16 Dans kernel: [  352.533116] ata3.00: 488397168 sectors, multi 16: LBA48 
Aug 22 15:24:16 Dans kernel: [  352.870905] ata3.00: configured for UDMA/100
Aug 22 15:24:16 Dans kernel: [  353.198257] ata4: SATA link down (SStatus 0 SControl 310)
Aug 22 15:24:16 Dans kernel: [  352.868589] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JS-60M 10.0 PQ: 0 ANSI: 5
Aug 22 15:24:16 Dans kernel: [  353.198868] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
Aug 22 15:24:16 Dans kernel: [  353.198873] PCI: setting IRQ 3 as level-triggered
Aug 22 15:24:16 Dans kernel: [  353.198879] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 15:24:16 Dans kernel: [  353.198902] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 22 15:24:16 Dans kernel: [  353.199317] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Aug 22 15:24:16 Dans kernel: [  353.199343] ohci_hcd 0000:00:13.0: irq 3, io mem 0xfe9fe000
Aug 22 15:24:16 Dans kernel: [  353.265937] usb usb1: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  353.265979] hub 1-0:1.0: USB hub found
Aug 22 15:24:16 Dans kernel: [  353.265993] hub 1-0:1.0: 4 ports detected
Aug 22 15:24:16 Dans kernel: [  353.366320] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 15:24:16 Dans kernel: [  353.366339] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 22 15:24:16 Dans kernel: [  353.366372] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Aug 22 15:24:16 Dans kernel: [  353.366392] ohci_hcd 0000:00:13.1: irq 3, io mem 0xfe9fd000
Aug 22 15:24:16 Dans kernel: [  353.434858] usb usb2: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  353.434895] hub 2-0:1.0: USB hub found
Aug 22 15:24:16 Dans kernel: [  353.434908] hub 2-0:1.0: 4 ports detected
Aug 22 15:24:16 Dans kernel: [  353.539213] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
Aug 22 15:24:16 Dans kernel: [  353.539428] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 4
Aug 22 15:24:16 Dans kernel: [  353.539432] PCI: setting IRQ 4 as level-triggered
Aug 22 15:24:16 Dans kernel: [  353.539437] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 22 15:24:16 Dans kernel: [  353.539448] ATIIXP: not 100% native mode: will probe irqs later
Aug 22 15:24:16 Dans kernel: [  353.539459]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:pio
Aug 22 15:24:16 Dans kernel: [  353.539475]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Aug 22 15:24:16 Dans kernel: [  353.539485] Probing IDE interface ide0...
Aug 22 15:24:16 Dans kernel: [  353.340225] usb 1-2: new full speed USB device using ohci_hcd and address 2
Aug 22 15:24:16 Dans kernel: [  353.549358] usb 1-2: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  354.121934] Probing IDE interface ide1...
Aug 22 15:24:16 Dans kernel: [  353.840050] usb 1-4: new full speed USB device using ohci_hcd and address 3
Aug 22 15:24:16 Dans kernel: [  354.047218] usb 1-4: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  354.335885] usb 2-4: new full speed USB device using ohci_hcd and address 2
Aug 22 15:24:16 Dans kernel: [  354.545073] usb 2-4: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  354.930148] hdd: &#131;^N2^B^P&#137;&#133;À, ATAPI cdrom or floppy?, assuming FLOPPY drive
Aug 22 15:24:16 Dans kernel: [  355.713880] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
Aug 22 15:24:16 Dans kernel: [  355.713897] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 22 15:24:16 Dans kernel: [  355.714041] hdc: UDMA/33 mode selected
Aug 22 15:24:16 Dans kernel: [  355.714286] hdd: host max PIO4 wanted PIO255(auto-tune) selected PIO0
Aug 22 15:24:16 Dans kernel: [  355.714320] hdd: host max PIO4 wanted PIO255(auto-tune) selected PIO0
Aug 22 15:24:16 Dans kernel: [  355.714400] ide1 at 0x170-0x177,0x376 on irq 15
Aug 22 15:24:16 Dans kernel: [  355.717930] PCI: Enabling device 0000:02:05.0 (0000 -> 0003)
Aug 22 15:24:16 Dans kernel: [  355.718163] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 15
Aug 22 15:24:16 Dans kernel: [  355.718168] PCI: setting IRQ 15 as level-triggered
Aug 22 15:24:16 Dans kernel: [  355.718174] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 15 (level, low) -> IRQ 15
Aug 22 15:24:16 Dans kernel: [  355.718193] PCI: Setting latency timer of device 0000:02:05.0 to 64
Aug 22 15:24:16 Dans kernel: [  355.388720] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 15:24:16 Dans kernel: [  355.388760] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug 22 15:24:16 Dans kernel: [  355.388879] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Aug 22 15:24:16 Dans kernel: [  355.389014] ehci_hcd 0000:00:13.2: irq 3, io mem 0xfe9fc000
Aug 22 15:24:16 Dans kernel: [  355.389231] usb 1-2: USB disconnect, address 2
Aug 22 15:24:16 Dans kernel: [  355.722959] eth0: RealTek RTL8139 at 0xe400, 00:14:2a:b6:ae:32, IRQ 15
Aug 22 15:24:16 Dans kernel: [  355.722962] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Aug 22 15:24:16 Dans kernel: [  355.725999] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Aug 22 15:24:16 Dans kernel: [  355.403512] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 22 15:24:16 Dans kernel: [  355.403667] usb usb3: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  355.403706] hub 3-0:1.0: USB hub found
Aug 22 15:24:16 Dans kernel: [  355.403716] hub 3-0:1.0: 8 ports detected
Aug 22 15:24:16 Dans kernel: [  355.503747] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 22 15:24:16 Dans kernel: [  355.853382] usb 1-4: USB disconnect, address 3
Aug 22 15:24:16 Dans kernel: [  355.983239] usb 2-4: USB disconnect, address 2
Aug 22 15:24:16 Dans kernel: [  355.662080] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 22 15:24:16 Dans kernel: [  355.788102] Driver 'sd' needs updating - please use bus_type methods
Aug 22 15:24:16 Dans kernel: [  355.788236] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 22 15:24:16 Dans kernel: [  355.788266] sd 2:0:0:0: [sda] Write Protect is off
Aug 22 15:24:16 Dans kernel: [  355.788271] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 15:24:16 Dans kernel: [  355.788305] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 15:24:16 Dans kernel: [  355.788386] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 22 15:24:16 Dans kernel: [  355.788404] sd 2:0:0:0: [sda] Write Protect is off
Aug 22 15:24:16 Dans kernel: [  355.788407] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 15:24:16 Dans kernel: [  355.788437] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 15:24:16 Dans kernel: [  355.788443]  sda:ide-floppy driver 0.99.newide
Aug 22 15:24:16 Dans kernel: [  355.810299]  sda1 sda2 < sda5 >
Aug 22 15:24:16 Dans kernel: [  355.843973] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 22 15:24:16 Dans kernel: [  355.849804] sd 2:0:0:0: Attached scsi generic sg0 type 0
Aug 22 15:24:16 Dans kernel: [  356.259222] usb 3-7: new high speed USB device using ehci_hcd and address 3
Aug 22 15:24:16 Dans kernel: [  356.392194] usb 3-7: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  356.961006] usbcore: registered new interface driver libusual
Aug 22 15:24:16 Dans kernel: [  356.938985] usb 1-2: new full speed USB device using ohci_hcd and address 4
Aug 22 15:24:16 Dans kernel: [  357.281024] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff3db232]
Aug 22 15:24:16 Dans kernel: [  357.157338] usb 1-2: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  357.446818] usb 2-4: new full speed USB device using ohci_hcd and address 3
Aug 22 15:24:16 Dans kernel: [  357.640206] usb 2-4: configuration #1 chosen from 1 choice
Aug 22 15:24:16 Dans kernel: [  357.984455] Initializing USB Mass Storage driver...
Aug 22 15:24:16 Dans kernel: [  357.985445] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 22 15:24:16 Dans kernel: [  357.985693] usbcore: registered new interface driver usb-storage
Aug 22 15:24:16 Dans kernel: [  357.985698] USB Mass Storage support registered.
Aug 22 15:24:16 Dans kernel: [  357.985826] usb-storage: device found at 3
Aug 22 15:24:16 Dans kernel: [  357.985829] usb-storage: waiting for device to settle before scanning
Aug 22 15:24:16 Dans kernel: [  362.654667] usb-storage: device scan complete
Aug 22 15:24:16 Dans kernel: [  362.990515] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Aug 22 15:24:16 Dans kernel: [  362.996511] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Aug 22 15:24:16 Dans kernel: [  363.002513] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Aug 22 15:24:16 Dans kernel: [  363.008511] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Aug 22 15:24:16 Dans kernel: [  363.018553] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug 22 15:24:16 Dans kernel: [  363.018611] sd 4:0:0:0: Attached scsi generic sg1 type 0
Aug 22 15:24:16 Dans kernel: [  363.028559] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Aug 22 15:24:16 Dans kernel: [  363.028618] sd 4:0:0:1: Attached scsi generic sg2 type 0
Aug 22 15:24:16 Dans kernel: [  363.038563] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Aug 22 15:24:16 Dans kernel: [  363.038626] sd 4:0:0:2: Attached scsi generic sg3 type 0
Aug 22 15:24:16 Dans kernel: [  363.048565] sd 4:0:0:3: [sde] Attached SCSI removable disk
Aug 22 15:24:16 Dans kernel: [  363.048627] sd 4:0:0:3: Attached scsi generic sg4 type 0
Aug 22 15:24:16 Dans kernel: [  362.768999] ide-cd: cmd 0x5a timed out
Aug 22 15:24:16 Dans kernel: [  362.769010] hdc: lost interrupt
Aug 22 15:24:16 Dans kernel: [  422.748527] ide-cd: cmd 0x5a timed out
Aug 22 15:24:16 Dans kernel: [  422.748536] hdc: lost interrupt
Aug 22 15:24:16 Dans kernel: [  422.748563] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Aug 22 15:24:16 Dans kernel: [  422.748573] Uniform CD-ROM driver Revision: 3.20
Aug 22 15:24:16 Dans kernel: [  482.728057] hdc: lost interrupt
Aug 22 15:24:16 Dans kernel: [  535.696614] Attempting manual resume
Aug 22 15:24:16 Dans kernel: [  535.696618] swsusp: Resume From Partition 8:5
Aug 22 15:24:16 Dans kernel: [  535.696620] PM: Checking swsusp image.
Aug 22 15:24:16 Dans kernel: [  535.696852] PM: Resume from disk failed.
Aug 22 15:24:16 Dans kernel: [  536.067774] kjournald starting.  Commit interval 5 seconds
Aug 22 15:24:16 Dans kernel: [  535.737937] EXT3-fs: mounted filesystem with ordered data mode.
Aug 22 15:24:16 Dans kernel: [  546.772382] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 22 15:24:16 Dans kernel: [  547.001081] ide-cd: cmd 0x3 timed out
Aug 22 15:24:16 Dans kernel: [  547.001091] hdc: lost interrupt
Aug 22 15:24:16 Dans kernel: [  547.488200] parport_pc 00:06: reported by Plug and Play ACPI
Aug 22 15:24:16 Dans kernel: [  547.488318] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Aug 22 15:24:16 Dans kernel: [  547.526090] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 22 15:24:16 Dans kernel: [  547.558961] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 22 15:24:16 Dans kernel: [  547.584857] Linux agpgart interface v0.102
Aug 22 15:24:16 Dans kernel: [  548.008877] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug 22 15:24:16 Dans kernel: [  548.220960] input: Power Button (FF) as /devices/virtual/input/input3
Aug 22 15:24:16 Dans kernel: [  548.272734] ACPI: Power Button (FF) [PWRF]
Aug 22 15:24:16 Dans kernel: [  548.272883] input: Power Button (CM) as /devices/virtual/input/input4
Aug 22 15:24:16 Dans kernel: [  548.320729] ACPI: Power Button (CM) [PWRB]
Aug 22 15:24:16 Dans kernel: [  549.331389] sysfs: duplicate filename 'pcspkr' can not be created
Aug 22 15:24:16 Dans kernel: [  549.331396] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
Aug 22 15:24:16 Dans kernel: [  549.331402] Pid: 3223, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 22 15:24:16 Dans kernel: [  549.331424]  [sysfs_add_one+0x9f/0xe0] sysfs_add_one+0x9f/0xe0
Aug 22 15:24:16 Dans kernel: [  549.331455]  [create_dir+0x48/0x90] create_dir+0x48/0x90
Aug 22 15:24:16 Dans kernel: [  549.331473]  [sysfs_create_dir+0x29/0x50] sysfs_create_dir+0x29/0x50
Aug 22 15:24:16 Dans kernel: [  549.331483]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
Aug 22 15:24:16 Dans kernel: [  549.331493]  [kobject_add+0x93/0x1b0] kobject_add+0x93/0x1b0
Aug 22 15:24:16 Dans kernel: [  549.331512]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 22 15:24:16 Dans kernel: [  549.331523]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 22 15:24:16 Dans kernel: [  549.331542]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 22 15:24:16 Dans kernel: [  549.331594]  [<c013f260>] param_get_int+0x0/0x20
Aug 22 15:24:16 Dans kernel: [  549.331617]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 22 15:24:16 Dans kernel: [  549.331643]  =======================
Aug 22 15:24:16 Dans kernel: [  549.331649] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
Aug 22 15:24:16 Dans kernel: [  549.331719] Pid: 3223, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 22 15:24:16 Dans kernel: [  549.331728]  [kobject_add+0x113/0x1b0] kobject_add+0x113/0x1b0
Aug 22 15:24:16 Dans kernel: [  549.331746]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 22 15:24:16 Dans kernel: [  549.331756]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 22 15:24:16 Dans kernel: [  549.331770]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 22 15:24:16 Dans kernel: [  549.331817]  [<c013f260>] param_get_int+0x0/0x20
Aug 22 15:24:16 Dans kernel: [  549.331836]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 22 15:24:16 Dans kernel: [  549.331860]  =======================
Aug 22 15:24:16 Dans kernel: [  549.856395] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 15:24:16 Dans kernel: [  549.887103] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 22 15:24:16 Dans kernel: [  550.128143] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4D11
Aug 22 15:24:16 Dans kernel: [  550.128170] usbcore: registered new interface driver usblp
Aug 22 15:24:16 Dans kernel: [  550.276027] ieee80211_crypt: registered algorithm 'NULL'
Aug 22 15:24:16 Dans kernel: [  550.336071] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 22 15:24:16 Dans kernel: [  550.349453] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 22 15:24:16 Dans kernel: [  550.349459] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 22 15:24:16 Dans kernel: [  550.362846] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Aug 22 15:24:16 Dans kernel: [  550.571892] usb 3-7: reset high speed USB device using ehci_hcd and address 3
Aug 22 15:24:16 Dans kernel: [  550.709120] zd1211rw 3-7:1.0: eth1
Aug 22 15:24:16 Dans kernel: [  550.709150] usbcore: registered new interface driver zd1211rw
Aug 22 15:24:16 Dans kernel: [  550.806858] zd1211rw 3-7:1.0: firmware version 4725
Aug 22 15:24:16 Dans kernel: [  550.846725] zd1211rw 3-7:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
Aug 22 15:24:16 Dans kernel: [  550.991858] NET: Registered protocol family 17
Aug 22 15:24:16 Dans kernel: [  551.180305] SoftMAC: Open Authentication completed with 00:18:d1:28:4f:05
Aug 22 15:24:16 Dans kernel: [  726.610988] lp0: using parport0 (interrupt-driven).
Aug 22 15:24:16 Dans kernel: [  726.368682] Adding 5887780k swap on /dev/sda5.  Priority:-1 extents:1 across:5887780k
Aug 22 15:24:16 Dans kernel: [  726.788282] EXT3 FS on sda1, internal journal
Aug 22 15:24:16 Dans kernel: [  727.486730] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 22 15:24:16 Dans kernel: [  727.935313] No dock devices found.
Aug 22 15:24:16 Dans kernel: [  728.292596] NET: Registered protocol family 10
Aug 22 15:24:16 Dans kernel: [  728.293026] lo: Disabled Privacy Extensions
Aug 22 15:24:16 Dans NetworkManager: <info>  starting... 
Aug 22 15:24:17 Dans avahi-daemon[8882]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 22 15:24:17 Dans avahi-daemon[8882]: Successfully dropped root privileges.
Aug 22 15:24:17 Dans avahi-daemon[8882]: avahi-daemon 0.6.22 starting up.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Successfully called chroot().
Aug 22 15:24:17 Dans avahi-daemon[8882]: Successfully dropped remaining capabilities.
Aug 22 15:24:17 Dans avahi-daemon[8882]: No service file found in /etc/avahi/services.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 22 15:24:17 Dans avahi-daemon[8882]: New relevant interface eth1.IPv4 for mDNS.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 22 15:24:17 Dans avahi-daemon[8882]: New relevant interface eth0.IPv4 for mDNS.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Network interface enumeration completed.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Registering new address record for fe80::217:3fff:fe34:c1de on eth1.*.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Registering new address record for 192.168.2.10 on eth1.IPv4.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Registering new address record for fe80::214:2aff:feb6:ae32 on eth0.*.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Registering new address record for 192.168.2.11 on eth0.IPv4.
Aug 22 15:24:17 Dans avahi-daemon[8882]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 22 15:24:17 Dans kernel: [  729.265224] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 22 15:24:17 Dans kernel: [  729.265232] apm: disabled - APM is not SMP safe.
Aug 22 15:24:17 Dans kernel: [  729.778491] ppdev: user-space parallel port driver
Aug 22 15:24:17 Dans kernel: [  729.623980] audit(1219433057.435:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8926 profile="/usr/sbin/cupsd" namespace="default"
Aug 22 15:24:17 Dans ntpdate[8832]: adjust time server 91.189.94.4 offset 0.269714 sec
Aug 22 15:24:17 Dans avahi-daemon[8882]: Server startup complete. Host name is Dans.local. Local service cookie is 4210510720.
Aug 22 15:24:19 Dans kernel: [  731.819729] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Aug 22 15:24:19 Dans kernel: [  731.819737] vboxdrv: Successfully done.
Aug 22 15:24:19 Dans kernel: [  731.819740] vboxdrv: Found 2 processor cores.
Aug 22 15:24:19 Dans kernel: [  731.819774] vboxdrv: fAsync=1 u64DiffCores=1055514800.
Aug 22 15:24:19 Dans kernel: [  731.820947] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Aug 22 15:24:19 Dans kernel: [  731.820954] vboxdrv: Successfully loaded version 1.6.4 (interface 0x00080000).
Aug 22 15:24:19 Dans dhcdbd: Started up.
Aug 22 15:24:20 Dans NetworkManager: <debug> [1219433060.886557] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_USB_MS_Reader_2004888_0_3'). 
Aug 22 15:24:21 Dans anacron[9270]: Anacron 2.3 started on 2008-08-22
Aug 22 15:24:21 Dans anacron[9270]: Normal exit (0 jobs run)
Aug 22 15:24:21 Dans /usr/sbin/cron[9297]: (CRON) INFO (pidfile fd = 3)
Aug 22 15:24:21 Dans /usr/sbin/cron[9300]: (CRON) STARTUP (fork ok)
Aug 22 15:24:21 Dans /usr/sbin/cron[9300]: (CRON) INFO (Running @reboot jobs)
Aug 22 15:24:22 Dans hal_lpadmin: add
Aug 22 15:24:23 Dans hal_lpadmin: URIs: ['hp:/usb/PSC_1400_series?serial=CN53EV62HV04BN', 'usb://HP/PSC%201400%20series?serial=CN53EV62HV04BN', 'hal:///org/freedesktop/Hal/devices/usb_device_3f0_4d11_CN53EV62HV04BN_if1_printer_CN53EV62HV04BN']
Aug 22 15:24:23 Dans python: hp-makeuri[9418]: error: Device does not support fax.
Aug 22 15:24:23 Dans hal_lpadmin: HPLIP Fax URIs: None
Aug 22 15:24:23 Dans hal_lpadmin: Not adding printer: PSC_1400_series already exists
Aug 22 15:24:23 Dans NetworkManager: <debug> [1219433063.510553] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4d11_CN53EV62HV04BN_if1_printer_CN53EV62HV04BN'). 
Aug 22 15:24:26 Dans kernel: [  738.323839] eth0: no IPv6 routers present
Aug 22 15:24:26 Dans kernel: [  738.555158] eth1: no IPv6 routers present
Aug 22 15:24:28 Dans kernel: [  740.446286] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 22 15:30:15 Dans kernel: [ 1087.840336] usb 1-2: USB disconnect, address 4
Aug 22 15:30:15 Dans kernel: [ 1087.840950] usblp0: removed
Aug 22 15:30:15 Dans NetworkManager: <debug> [1219433415.965699] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4d11_CN53EV62HV04BN_if0'). 
Aug 22 15:30:17 Dans hal_lpadmin: remove
Aug 22 15:30:17 Dans hal_lpadmin: Found configured printer: PSC_1400_series
Aug 22 15:30:17 Dans NetworkManager: <debug> [1219433417.037541] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4d11_CN53EV62HV04BN_if1_printer_CN53EV62HV04BN'). 
Aug 22 15:30:17 Dans NetworkManager: <debug> [1219433417.042612] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4d11_CN53EV62HV04BN_if1'). 
Aug 22 15:30:17 Dans NetworkManager: <debug> [1219433417.046414] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4d11_CN53EV62HV04BN_if2'). 
Aug 22 15:30:17 Dans NetworkManager: <debug> [1219433417.047074] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4d11_CN53EV62HV04BN'). 
Aug 22 15:34:19 Dans kernel: [ 1331.208474] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:586: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x306f000a
Aug 22 15:34:20 Dans kernel: [ 1332.211640] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x306f000a
Aug 22 15:34:24 Dans NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 22 15:34:24 Dans NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 22 15:34:24 Dans NetworkManager: <info>  User request to disable wireless. 
Aug 22 16:04:16 Dans -- MARK --
Aug 22 16:17:01 Dans /USR/SBIN/CRON[10290]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 16:44:16 Dans -- MARK --
Aug 22 17:04:16 Dans -- MARK --
Aug 22 17:17:01 Dans /USR/SBIN/CRON[11046]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 17:44:16 Dans -- MARK --
Aug 22 18:04:16 Dans -- MARK --
Aug 22 18:17:01 Dans /USR/SBIN/CRON[12920]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 18:44:16 Dans -- MARK --
Aug 22 19:04:16 Dans -- MARK --
Aug 22 19:17:02 Dans /USR/SBIN/CRON[14367]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 19:44:16 Dans -- MARK --
Aug 22 20:04:16 Dans -- MARK --
Aug 22 20:17:01 Dans /USR/SBIN/CRON[15140]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 20:44:16 Dans -- MARK --
Aug 22 21:04:16 Dans -- MARK --
Aug 22 21:12:20 Dans kernel: [21605.391322] usb 3-5: new high speed USB device using ehci_hcd and address 5
Aug 22 21:12:20 Dans kernel: [21605.525747] usb 3-5: configuration #1 chosen from 1 choice
Aug 22 21:12:20 Dans NetworkManager: <debug> [1219453940.531963] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b2_30_no_serial_number'). 
Aug 22 21:12:20 Dans NetworkManager: <debug> [1219453940.914947] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b2_30_no_serial_number_if1'). 
Aug 22 21:12:20 Dans NetworkManager: <debug> [1219453940.954992] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b2_30_no_serial_number_if0'). 
Aug 22 21:17:01 Dans /USR/SBIN/CRON[16088]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 21:44:16 Dans -- MARK --
Aug 22 21:53:09 Dans init: tty4 main process (8404) killed by TERM signal
Aug 22 21:53:09 Dans init: tty5 main process (8405) killed by TERM signal
Aug 22 21:53:09 Dans init: tty2 main process (8407) killed by TERM signal
Aug 22 21:53:09 Dans init: tty3 main process (8409) killed by TERM signal
Aug 22 21:53:09 Dans init: tty6 main process (8411) killed by TERM signal
Aug 22 21:53:09 Dans init: tty1 main process (9404) killed by TERM signal
Aug 22 21:53:12 Dans avahi-daemon[8882]: Got SIGTERM, quitting.
Aug 22 21:53:12 Dans avahi-daemon[8882]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 22 21:53:12 Dans avahi-daemon[8882]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 22 21:53:14 Dans kernel: [24058.537592] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 22 21:53:16 Dans exiting on signal 15
Aug 22 22:03:35 Dans syslogd 1.5.0#1ubuntu1: restart.
Aug 22 22:03:35 Dans kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 22 22:03:35 Dans kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 22 22:03:35 Dans kernel: Symbols match kernel version 2.6.24.
Aug 22 22:03:36 Dans kernel: Loaded 19456 symbols from 87 modules.
Aug 22 22:03:36 Dans kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 22 22:03:36 Dans kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 22 22:03:36 Dans kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 22 22:03:36 Dans kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 22 22:03:36 Dans kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 22 22:03:36 Dans kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 22 22:03:36 Dans kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Aug 22 22:03:36 Dans kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bfd0000 (usable)
Aug 22 22:03:36 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfd0000 - 000000007bfde000 (ACPI data)
Aug 22 22:03:36 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfde000 - 000000007c000000 (ACPI NVS)
Aug 22 22:03:36 Dans kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 22 22:03:36 Dans kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Aug 22 22:03:36 Dans kernel: [    0.000000] 1087MB HIGHMEM available.
Aug 22 22:03:36 Dans kernel: [    0.000000] 896MB LOWMEM available.
Aug 22 22:03:36 Dans kernel: [    0.000000] found SMP MP-table at 000ff780
Aug 22 22:03:36 Dans kernel: [    0.000000] Entering add_active_range(0, 0, 507856) 0 entries of 256 used
Aug 22 22:03:36 Dans kernel: [    0.000000] Zone PFN ranges:
Aug 22 22:03:36 Dans kernel: [    0.000000]   DMA             0 ->     4096
Aug 22 22:03:36 Dans kernel: [    0.000000]   Normal       4096 ->   229376
Aug 22 22:03:36 Dans kernel: [    0.000000]   HighMem    229376 ->   507856
Aug 22 22:03:36 Dans kernel: [    0.000000] Movable zone start PFN for each node
Aug 22 22:03:36 Dans kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 22 22:03:36 Dans kernel: [    0.000000]     0:        0 ->   507856
Aug 22 22:03:36 Dans kernel: [    0.000000] On node 0 totalpages: 507856
Aug 22 22:03:36 Dans kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 22 22:03:36 Dans kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 22 22:03:36 Dans kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 22 22:03:36 Dans kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 22 22:03:36 Dans kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 22 22:03:36 Dans kernel: [    0.000000]   HighMem zone: 2175 pages used for memmap
Aug 22 22:03:36 Dans kernel: [    0.000000]   HighMem zone: 276305 pages, LIFO batch:31
Aug 22 22:03:36 Dans kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 22 22:03:36 Dans kernel: [    0.000000] DMI present.
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8890 checksum 0
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: RSDP 000F8890, 0014 (r0 HP-CPC)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: RSDT 7BFD0000, 0038 (r1 HP-CPC OEMRSDT  11000518 MSFT       97)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: FACP 7BFD0200, 0084 (r2 HP-CPC OEMFACP  11000518 MSFT       97)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: DSDT 7BFD0440, 43B0 (r1 HP-CPC  RC410-M        0 INTL  2002026)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: FACS 7BFDE000, 0040
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: APIC 7BFD0390, 006C (r1 HP-CPC OEMAPIC  11000518 MSFT       97)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: MCFG 7BFD0400, 003C (r1 HP-CPC OEMMCFG  11000518 MSFT       97)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: OEMB 7BFDE040, 005B (r1 HP-CPC AMI_OEM  11000518 MSFT       97)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: HPET 7BFD47F0, 0038 (r1 HP-CPC OEMHPET  11000518 MSFT       97)
Aug 22 22:03:36 Dans kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 22 22:03:36 Dans kernel: [    0.000000] Processor #0 15:4 APIC version 20
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 22 22:03:36 Dans kernel: [    0.000000] Processor #1 15:4 APIC version 20
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
Aug 22 22:03:36 Dans kernel: [    0.000000] ACPI: HPET id: 0x0 base: 0xfed00000
Aug 22 22:03:36 Dans kernel: [    0.000000] Using ACPI for processor (LAPIC) configuration information
Aug 22 22:03:36 Dans kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Aug 22 22:03:36 Dans kernel: [    0.000000]     Virtual Wire compatibility mode.
Aug 22 22:03:36 Dans kernel: [    0.000000] OEM ID: ATI      Product ID: RS400        APIC at: 0xFEE00000
Aug 22 22:03:36 Dans kernel: [    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
Aug 22 22:03:36 Dans kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 22 22:03:36 Dans kernel: [    0.000000] Processors: 2
Aug 22 22:03:36 Dans kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7c000000:82e00000)
Aug 22 22:03:36 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 22 22:03:36 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
Aug 22 22:03:36 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Aug 22 22:03:36 Dans kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503889
Aug 22 22:03:36 Dans kernel: [    0.000000] Kernel command line: root=UUID=e9a7cff5-d8ae-4fb4-a348-d2db06aed623 ro single noapic
Aug 22 22:03:36 Dans kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 22 22:03:36 Dans kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 22 22:03:36 Dans kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 22 22:03:36 Dans kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 22 22:03:36 Dans kernel: [    0.000000] Initializing CPU#0
Aug 22 22:03:36 Dans kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 22 22:03:36 Dans kernel: [    0.000000] Detected 3199.167 MHz processor.
Aug 22 22:03:36 Dans kernel: [   22.888222] Console: colour VGA+ 80x25
Aug 22 22:03:36 Dans kernel: [   22.888227] console [tty0] enabled
Aug 22 22:03:36 Dans kernel: [   22.891886] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 22 22:03:36 Dans kernel: [   22.892638] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 22 22:03:36 Dans kernel: [   23.001773] Memory: 2001980k/2031424k available (2177k kernel code, 28188k reserved, 1006k data, 368k init, 1113920k highmem)
Aug 22 22:03:36 Dans kernel: [   23.001847] virtual kernel memory layout:
Aug 22 22:03:36 Dans kernel: [   23.001848]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 22 22:03:36 Dans kernel: [   23.001849]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 22 22:03:36 Dans kernel: [   23.001850]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 22 22:03:36 Dans kernel: [   23.001851]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 22 22:03:36 Dans kernel: [   23.001852]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 22 22:03:36 Dans kernel: [   23.001853]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 22 22:03:36 Dans kernel: [   23.001854]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 22 22:03:36 Dans kernel: [   23.002215] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 22 22:03:36 Dans kernel: [   23.002369] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 22 22:03:36 Dans kernel: [   23.002529] hpet clockevent registered
Aug 22 22:03:36 Dans kernel: [   24.057434] Calibrating delay using timer specific routine.. 88438.35 BogoMIPS (lpj=176876716)
Aug 22 22:03:36 Dans kernel: [   24.057555] Security Framework initialized
Aug 22 22:03:36 Dans kernel: [   24.057610] SELinux:  Disabled at boot.
Aug 22 22:03:36 Dans kernel: [   24.057675] AppArmor: AppArmor initialized
Aug 22 22:03:36 Dans kernel: [   24.057723] Failure registering capabilities with primary security module.
Aug 22 22:03:36 Dans kernel: [   24.057780] Mount-cache hash table entries: 512
Aug 22 22:03:36 Dans kernel: [   24.057994] Initializing cgroup subsys ns
Aug 22 22:03:36 Dans kernel: [   24.058045] Initializing cgroup subsys cpuacct
Aug 22 22:03:36 Dans kernel: [   24.058103] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 22 22:03:36 Dans kernel: [   24.058112] monitor/mwait feature present.
Aug 22 22:03:36 Dans kernel: [   24.058158] using mwait in idle threads.
Aug 22 22:03:36 Dans kernel: [   24.058208] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 22 22:03:36 Dans kernel: [   24.058291] CPU: L2 cache: 2048K
Aug 22 22:03:36 Dans kernel: [   24.058337] CPU: Physical Processor ID: 0
Aug 22 22:03:36 Dans kernel: [   24.058382] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 22 22:03:36 Dans kernel: [   24.058396] Compat vDSO mapped to ffffe000.
Aug 22 22:03:36 Dans kernel: [   24.058460] Checking 'hlt' instruction... OK.
Aug 22 22:03:36 Dans kernel: [   24.277616] SMP alternatives: switching to UP code
Aug 22 22:03:36 Dans kernel: [   24.280374] Early unpacking initramfs... done
Aug 22 22:03:36 Dans kernel: [   24.565202] ACPI: Core revision 20070126
Aug 22 22:03:36 Dans kernel: [   24.565306] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 22 22:03:36 Dans kernel: [   24.567309] ACPI: setting ELCR to 0200 (from 0c38)
Aug 22 22:03:36 Dans kernel: [   24.568027] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 22 22:03:36 Dans kernel: [   24.568166] SMP alternatives: switching to SMP code
Aug 22 22:03:36 Dans kernel: [   24.569045] Booting processor 1/1 eip 3000
Aug 22 22:03:36 Dans kernel: [   24.929354] Initializing CPU#1
Aug 22 22:03:36 Dans kernel: [   25.979566] Calibrating delay using timer specific routine.. 87905.35 BogoMIPS (lpj=175810717)
Aug 22 22:03:36 Dans kernel: [   25.979577] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 22 22:03:36 Dans kernel: [   25.979584] monitor/mwait feature present.
Aug 22 22:03:36 Dans kernel: [   25.979591] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 22 22:03:36 Dans kernel: [   25.979593] CPU: L2 cache: 2048K
Aug 22 22:03:36 Dans kernel: [   25.979596] CPU: Physical Processor ID: 0
Aug 22 22:03:36 Dans kernel: [   25.979598] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 22 22:03:36 Dans kernel: [   25.650436] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 22 22:03:36 Dans kernel: [   25.650881] Total of 2 processors activated (176343.71 BogoMIPS).
Aug 22 22:03:36 Dans kernel: [   27.132345] APIC calibration not consistent with PM Timer: 1373ms instead of 100ms
Aug 22 22:03:36 Dans kernel: [   27.132403] APIC delta adjusted to PM-Timer: 1249643 (17159264)
Aug 22 22:03:36 Dans kernel: [   27.132601] checking TSC synchronization [CPU#0 -> CPU#1]:
Aug 22 22:03:36 Dans kernel: [   27.152685] Measured 1055311320 cycles TSC warp between CPUs, turning off TSC clock.
Aug 22 22:03:36 Dans kernel: [   27.152742] Marking TSC unstable due to: check_tsc_sync_source failed.
Aug 22 22:03:36 Dans kernel: [   27.152809] Brought up 2 CPUs
Aug 22 22:03:36 Dans kernel: [   27.152873] CPU0 attaching sched-domain:
Aug 22 22:03:36 Dans kernel: [   27.152876]  domain 0: span 03
Aug 22 22:03:36 Dans kernel: [   27.152879]   groups: 01 02
Aug 22 22:03:36 Dans kernel: [   27.152882]   domain 1: span 03
Aug 22 22:03:36 Dans kernel: [   27.152884]    groups: 03
Aug 22 22:03:36 Dans kernel: [   27.152887] CPU1 attaching sched-domain:
Aug 22 22:03:36 Dans kernel: [   27.152888]  domain 0: span 03
Aug 22 22:03:36 Dans kernel: [   27.152890]   groups: 02 01
Aug 22 22:03:36 Dans kernel: [   27.152893]   domain 1: span 03
Aug 22 22:03:36 Dans kernel: [   27.152895]    groups: 03
Aug 22 22:03:36 Dans kernel: [   27.153170] net_namespace: 64 bytes
Aug 22 22:03:36 Dans kernel: [   27.153223] Booting paravirtualized kernel on bare hardware
Aug 22 22:03:36 Dans kernel: [   27.153858] Time:  1:57:17  Date: 08/23/08
Aug 22 22:03:36 Dans kernel: [   27.153930] NET: Registered protocol family 16
Aug 22 22:03:36 Dans kernel: [   27.154233] EISA bus registered
Aug 22 22:03:36 Dans kernel: [   27.154283] ACPI: bus type pci registered
Aug 22 22:03:36 Dans kernel: [   27.154550] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
Aug 22 22:03:36 Dans kernel: [   27.154599] PCI: Using configuration type 1
Aug 22 22:03:36 Dans kernel: [   27.154659] Setting up standard PCI resources
Aug 22 22:03:36 Dans kernel: [   27.497657] ACPI: EC: Look up EC in DSDT
Aug 22 22:03:36 Dans kernel: [   27.503884] ACPI: Interpreter enabled
Aug 22 22:03:36 Dans kernel: [   27.503933] ACPI: (supports S0 S1 S3 S4 S5)
Aug 22 22:03:36 Dans kernel: [   27.504175] ACPI: Using PIC for interrupt routing
Aug 22 22:03:36 Dans kernel: [   27.513959] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 22 22:03:36 Dans kernel: [   27.515646] PCI: Transparent bridge - 0000:00:14.4
Aug 22 22:03:36 Dans kernel: [   27.515729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 22 22:03:36 Dans kernel: [   27.515862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Aug 22 22:03:36 Dans kernel: [   27.515965] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Aug 22 22:03:36 Dans kernel: [   27.522408] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *4 5 7 10 11 12 14 15)
Aug 22 22:03:36 Dans kernel: [   27.522974] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 22 22:03:36 Dans kernel: [   27.523529] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 22 22:03:36 Dans kernel: [   27.524162] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
Aug 22 22:03:36 Dans kernel: [   27.524715] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 22 22:03:36 Dans kernel: [   27.525269] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
Aug 22 22:03:36 Dans kernel: [   27.525604] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
Aug 22 22:03:36 Dans kernel: [   27.526157] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
Aug 22 22:03:36 Dans kernel: [   27.526749] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  A8, should be 9C [20070126]
Aug 22 22:03:36 Dans kernel: [   27.526890] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 22 22:03:36 Dans kernel: [   27.526980] pnp: PnP ACPI init
Aug 22 22:03:36 Dans kernel: [   27.527033] ACPI: bus type pnp registered
Aug 22 22:03:36 Dans kernel: [   27.534308] pnp: PnP ACPI: found 14 devices
Aug 22 22:03:36 Dans kernel: [   27.534357] ACPI: ACPI bus type pnp unregistered
Aug 22 22:03:36 Dans kernel: [   27.534406] PnPBIOS: Disabled by ACPI PNP
Aug 22 22:03:36 Dans kernel: [   27.534745] PCI: Using ACPI for IRQ routing
Aug 22 22:03:36 Dans kernel: [   27.534794] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 22 22:03:36 Dans kernel: [   27.534853] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Aug 22 22:03:36 Dans kernel: [   27.558583] NET: Registered protocol family 8
Aug 22 22:03:36 Dans kernel: [   27.558631] NET: Registered protocol family 20
Aug 22 22:03:36 Dans kernel: [   27.558731] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 22 22:03:36 Dans kernel: [   27.558961] hpet0: 4 32-bit timers, 14318180 Hz
Aug 22 22:03:36 Dans kernel: [   27.560052] AppArmor: AppArmor Filesystem Enabled
Aug 22 22:03:36 Dans kernel: [   27.232453] Time: hpet clocksource has been installed.
Aug 22 22:03:36 Dans kernel: [   27.232518] Switched to high resolution mode on CPU 0
Aug 22 22:03:36 Dans kernel: [   27.562588] Switched to high resolution mode on CPU 1
Aug 22 22:03:36 Dans kernel: [   27.571286] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Aug 22 22:03:36 Dans kernel: [   27.571959] system 00:07: ioport range 0x40b-0x40b has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572009] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572057] system 00:07: ioport range 0xc00-0xc01 has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572104] system 00:07: ioport range 0xc14-0xc14 has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572152] system 00:07: ioport range 0xc50-0xc51 has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572200] system 00:07: ioport range 0xc52-0xc52 has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572248] system 00:07: ioport range 0xc6c-0xc6c has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572295] system 00:07: ioport range 0xc6f-0xc6f has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572344] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572392] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572439] system 00:07: ioport range 0xcd8-0xcdf has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572487] system 00:07: ioport range 0x800-0x89f has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572535] system 00:07: ioport range 0x900-0x90f has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572583] system 00:07: ioport range 0x910-0x91f has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572631] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
Aug 22 22:03:36 Dans kernel: [   27.572690] system 00:0a: ioport range 0xa00-0xa0f has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572739] system 00:0a: ioport range 0xa10-0xa1f has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572786] system 00:0a: ioport range 0xa20-0xa2f has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572834] system 00:0a: ioport range 0xa30-0xa3f has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572886] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
Aug 22 22:03:36 Dans kernel: [   27.572935] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 22 22:03:36 Dans kernel: [   27.572991] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Aug 22 22:03:36 Dans kernel: [   27.573044] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Aug 22 22:03:36 Dans kernel: [   27.573568] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Aug 22 22:03:36 Dans kernel: [   27.573616] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Aug 22 22:03:36 Dans kernel: [   27.573665] system 00:0d: iomem range 0x100000-0x7bffffff could not be reserved
Aug 22 22:03:36 Dans kernel: [   27.573719] system 00:0d: iomem range 0x0-0x0 could not be reserved
Aug 22 22:03:36 Dans kernel: [   27.604334] PCI: Bridge: 0000:00:01.0
Aug 22 22:03:36 Dans kernel: [   27.604381]   IO window: d000-dfff
Aug 22 22:03:36 Dans kernel: [   27.604428]   MEM window: fea00000-feafffff
Aug 22 22:03:36 Dans kernel: [   27.604475]   PREFETCH window: d0000000-dfffffff
Aug 22 22:03:36 Dans kernel: [   27.604523] PCI: Bridge: 0000:00:14.4
Aug 22 22:03:36 Dans kernel: [   27.604570]   IO window: e000-efff
Aug 22 22:03:36 Dans kernel: [   27.604620]   MEM window: feb00000-febfffff
Aug 22 22:03:36 Dans kernel: [   27.604669]   PREFETCH window: disabled.
Aug 22 22:03:36 Dans kernel: [   27.604745] NET: Registered protocol family 2
Aug 22 22:03:36 Dans kernel: [   27.643285] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 22 22:03:36 Dans kernel: [   27.643712] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 22 22:03:36 Dans kernel: [   27.644406] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 22 22:03:36 Dans kernel: [   27.644836] TCP: Hash tables configured (established 131072 bind 65536)
Aug 22 22:03:36 Dans kernel: [   27.644885] TCP reno registered
Aug 22 22:03:36 Dans kernel: [   27.655385] checking if image is initramfs... it is
Aug 22 22:03:36 Dans kernel: [   28.224041] Freeing initrd memory: 7312k freed
Aug 22 22:03:36 Dans kernel: [   28.225149] audit: initializing netlink socket (disabled)
Aug 22 22:03:36 Dans kernel: [   28.225215] audit(1219456633.944:1): initialized
Aug 22 22:03:36 Dans kernel: [   28.225548] highmem bounce pool size: 64 pages
Aug 22 22:03:36 Dans kernel: [   28.228091] VFS: Disk quotas dquot_6.5.1
Aug 22 22:03:36 Dans kernel: [   28.228236] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 22 22:03:36 Dans kernel: [   28.228442] io scheduler noop registered
Aug 22 22:03:36 Dans kernel: [   28.228490] io scheduler anticipatory registered
Aug 22 22:03:36 Dans kernel: [   28.228536] io scheduler deadline registered
Aug 22 22:03:36 Dans kernel: [   28.228591] io scheduler cfq registered (default)
Aug 22 22:03:36 Dans kernel: [   28.228645] PCI: MSI quirk detected. MSI deactivated.
Aug 22 22:03:36 Dans kernel: [   28.294078] Boot video device is 0000:01:05.0
Aug 22 22:03:36 Dans kernel: [   28.294449] isapnp: Scanning for PnP cards...
Aug 22 22:03:36 Dans kernel: [   29.321708] isapnp: No Plug & Play device found
Aug 22 22:03:36 Dans kernel: [   29.359428] Real Time Clock Driver v1.12ac
Aug 22 22:03:36 Dans kernel: [   29.359613] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 22 22:03:36 Dans kernel: [   29.361235] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 22 22:03:36 Dans kernel: [   29.361370] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 22 22:03:36 Dans kernel: [   29.361552] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Aug 22 22:03:36 Dans kernel: [   29.035453] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 22 22:03:36 Dans kernel: [   29.035506] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 22 22:03:36 Dans kernel: [   29.385836] mice: PS/2 mouse device common for all mice
Aug 22 22:03:36 Dans kernel: [   29.386041] EISA: Probing bus 0 at eisa.0
Aug 22 22:03:36 Dans kernel: [   29.386101] Cannot allocate resource for EISA slot 2
Aug 22 22:03:36 Dans kernel: [   29.386148] Cannot allocate resource for EISA slot 3
Aug 22 22:03:36 Dans kernel: [   29.386194] Cannot allocate resource for EISA slot 4
Aug 22 22:03:36 Dans kernel: [   29.386241] Cannot allocate resource for EISA slot 5
Aug 22 22:03:36 Dans kernel: [   29.386287] Cannot allocate resource for EISA slot 6
Aug 22 22:03:36 Dans kernel: [   29.386333] Cannot allocate resource for EISA slot 7
Aug 22 22:03:36 Dans kernel: [   29.386379] Cannot allocate resource for EISA slot 8
Aug 22 22:03:36 Dans kernel: [   29.386425] EISA: Detected 0 cards.
Aug 22 22:03:36 Dans kernel: [   29.386472] cpuidle: using governor ladder
Aug 22 22:03:36 Dans kernel: [   29.386518] cpuidle: using governor menu
Aug 22 22:03:36 Dans kernel: [   29.386667] NET: Registered protocol family 1
Aug 22 22:03:36 Dans kernel: [   29.386745] Using IPI No-Shortcut mode
Aug 22 22:03:36 Dans kernel: [   29.386824] registered taskstats version 1
Aug 22 22:03:36 Dans kernel: [   29.386983]   Magic number: 4:286:964
Aug 22 22:03:36 Dans kernel: [   29.387031]   hash matches device rtc
Aug 22 22:03:36 Dans kernel: [   29.387083]   hash matches device ttyb5
Aug 22 22:03:36 Dans kernel: [   29.387270] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 22 22:03:36 Dans kernel: [   29.387317] EDD information not available.
Aug 22 22:03:36 Dans kernel: [   29.387744] Freeing unused kernel memory: 368k freed
Aug 22 22:03:36 Dans kernel: [   29.074659] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 22 22:03:36 Dans kernel: [   29.587321] fuse init (API version 7.9)
Aug 22 22:03:36 Dans kernel: [   29.610348] ACPI: SSDT 7BFD4830, 02FE (r1    AMI   CPU1PM        1 INTL  2002026)
Aug 22 22:03:36 Dans kernel: [   29.610708] ACPI: duty_cycle spans bit 4
Aug 22 22:03:36 Dans kernel: [   29.610884] ACPI: SSDT 7BFD4B30, 02FE (r1    AMI   CPU2PM        1 INTL  2002026)
Aug 22 22:03:36 Dans kernel: [   29.611192] ACPI: duty_cycle spans bit 4
Aug 22 22:03:36 Dans kernel: [   29.611255] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 22 22:03:36 Dans kernel: [   29.611394] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 22 22:03:36 Dans kernel: [   29.449807] SCSI subsystem initialized
Aug 22 22:03:36 Dans kernel: [   29.511807] usbcore: registered new interface driver usbfs
Aug 22 22:03:36 Dans kernel: [   29.511896] usbcore: registered new interface driver hub
Aug 22 22:03:36 Dans kernel: [   29.523718] libata version 3.00 loaded.
Aug 22 22:03:36 Dans kernel: [   29.526987] usbcore: registered new device driver usb
Aug 22 22:03:36 Dans kernel: [   29.535803] sata_sil 0000:00:11.0: version 2.3
Aug 22 22:03:36 Dans kernel: [   29.536116] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
Aug 22 22:03:36 Dans kernel: [   29.536171] PCI: setting IRQ 5 as level-triggered
Aug 22 22:03:36 Dans kernel: [   29.536177] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 22 22:03:36 Dans kernel: [   29.548470] scsi0 : sata_sil
Aug 22 22:03:36 Dans kernel: [   29.549295] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 22 22:03:36 Dans kernel: [   29.559691] scsi1 : sata_sil
Aug 22 22:03:36 Dans kernel: [   29.559808] ata1: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff080 irq 5
Aug 22 22:03:36 Dans kernel: [   29.559864] ata2: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff0c0 irq 5
Aug 22 22:03:36 Dans kernel: [   30.174976] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 22 22:03:36 Dans kernel: [   30.175036] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 22 22:03:36 Dans kernel: [   29.853503] 8139too Fast Ethernet driver 0.9.28
Aug 22 22:03:36 Dans kernel: [   29.871603] ata1: SATA link down (SStatus 0 SControl 310)
Aug 22 22:03:36 Dans kernel: [   30.330253] FDC 0 is a post-1991 82077
Aug 22 22:03:36 Dans kernel: [   30.510284] ata2: SATA link down (SStatus 0 SControl 310)
Aug 22 22:03:36 Dans kernel: [   30.180964] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
Aug 22 22:03:36 Dans kernel: [   30.181022] PCI: setting IRQ 11 as level-triggered
Aug 22 22:03:36 Dans kernel: [   30.181028] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
Aug 22 22:03:36 Dans kernel: [   30.181268] scsi2 : sata_sil
Aug 22 22:03:36 Dans kernel: [   30.181409] scsi3 : sata_sil
Aug 22 22:03:36 Dans kernel: [   30.181520] ata3: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff880 irq 11
Aug 22 22:03:36 Dans kernel: [   30.181580] ata4: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff8c0 irq 11
Aug 22 22:03:36 Dans kernel: [   30.651355] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug 22 22:03:36 Dans kernel: [   30.989669] ata3.00: ATA-7: WDC WD2500JS-60MHB1, 10.02E02, max UDMA/100
Aug 22 22:03:36 Dans kernel: [   30.989720] ata3.00: 488397168 sectors, multi 16: LBA48 
Aug 22 22:03:36 Dans kernel: [   30.997667] ata3.00: configured for UDMA/100
Aug 22 22:03:36 Dans kernel: [   31.309010] ata4: SATA link down (SStatus 0 SControl 310)
Aug 22 22:03:36 Dans kernel: [   30.979461] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JS-60M 10.0 PQ: 0 ANSI: 5
Aug 22 22:03:36 Dans kernel: [   31.310040] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
Aug 22 22:03:36 Dans kernel: [   31.310095] PCI: setting IRQ 3 as level-triggered
Aug 22 22:03:36 Dans kernel: [   31.310102] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 22:03:36 Dans kernel: [   31.310268] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 22 22:03:36 Dans kernel: [   31.310710] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Aug 22 22:03:36 Dans kernel: [   31.310791] ohci_hcd 0000:00:13.0: irq 3, io mem 0xfe9fe000
Aug 22 22:03:36 Dans kernel: [   31.376718] usb usb1: configuration #1 chosen from 1 choice
Aug 22 22:03:36 Dans kernel: [   31.376810] hub 1-0:1.0: USB hub found
Aug 22 22:03:36 Dans kernel: [   31.376869] hub 1-0:1.0: 4 ports detected
Aug 22 22:03:36 Dans kernel: [   31.477072] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 22:03:36 Dans kernel: [   31.477227] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 22 22:03:36 Dans kernel: [   31.477315] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Aug 22 22:03:36 Dans kernel: [   31.477389] ohci_hcd 0000:00:13.1: irq 3, io mem 0xfe9fd000
Aug 22 22:03:36 Dans kernel: [   31.544612] usb usb2: configuration #1 chosen from 1 choice
Aug 22 22:03:36 Dans kernel: [   31.544699] hub 2-0:1.0: USB hub found
Aug 22 22:03:36 Dans kernel: [   31.544757] hub 2-0:1.0: 4 ports detected
Aug 22 22:03:36 Dans kernel: [   31.315639] ACPI: PCI Interrupt Link [LNKE] BIOS reported IRQ 15, using IRQ 10
Aug 22 22:03:36 Dans kernel: [   31.315708] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
Aug 22 22:03:36 Dans kernel: [   31.315765] PCI: setting IRQ 10 as level-triggered
Aug 22 22:03:36 Dans kernel: [   31.315770] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
Aug 22 22:03:36 Dans kernel: [   31.646076] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
Aug 22 22:03:36 Dans kernel: [   31.646796] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 4
Aug 22 22:03:36 Dans kernel: [   31.646848] PCI: setting IRQ 4 as level-triggered
Aug 22 22:03:36 Dans kernel: [   31.646854] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 22 22:03:36 Dans kernel: [   31.647003] ATIIXP: not 100% native mode: will probe irqs later
Aug 22 22:03:36 Dans kernel: [   31.647062]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:pio
Aug 22 22:03:36 Dans kernel: [   31.647207]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Aug 22 22:03:36 Dans kernel: [   31.317523] eth0: RealTek RTL8139 at 0xe400, 00:14:2a:b6:ae:32, IRQ 10
Aug 22 22:03:36 Dans kernel: [   31.317532] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Aug 22 22:03:36 Dans kernel: [   31.647401] Probing IDE interface ide0...
Aug 22 22:03:36 Dans kernel: [   31.343663] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Aug 22 22:03:36 Dans kernel: [   31.451045] usb 1-3: new full speed USB device using ohci_hcd and address 2
Aug 22 22:03:36 Dans kernel: [   31.660202] usb 1-3: configuration #1 chosen from 1 choice
Aug 22 22:03:36 Dans kernel: [   32.228684] Probing IDE interface ide1...
Aug 22 22:03:36 Dans kernel: [   31.962867] usb 1-4: new full speed USB device using ohci_hcd and address 3
Aug 22 22:03:36 Dans kernel: [   32.174048] usb 1-4: configuration #1 chosen from 1 choice
Aug 22 22:03:36 Dans kernel: [   32.478693] usb 2-4: new full speed USB device using ohci_hcd and address 2
Aug 22 22:03:36 Dans kernel: [   32.687905] usb 2-4: configuration #1 chosen from 1 choice
Aug 22 22:03:36 Dans kernel: [   32.700542] usbcore: registered new interface driver libusual
Aug 22 22:03:36 Dans kernel: [   32.707050] Initializing USB Mass Storage driver...
Aug 22 22:03:36 Dans kernel: [   32.707227] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 22 22:03:36 Dans kernel: [   32.707386] usbcore: registered new interface driver usb-storage
Aug 22 22:03:36 Dans kernel: [   32.707446] USB Mass Storage support registered.
Aug 22 22:03:36 Dans kernel: [   32.707625] usb-storage: device found at 2
Aug 22 22:03:36 Dans kernel: [   32.707628] usb-storage: waiting for device to settle before scanning
Aug 22 22:03:36 Dans kernel: [   33.037857] hdd: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
Aug 22 22:03:36 Dans kernel: [   33.820573] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
Aug 22 22:03:36 Dans kernel: [   33.820747] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 22 22:03:36 Dans kernel: [   33.821020] hdc: UDMA/33 mode selected
Aug 22 22:03:36 Dans kernel: [   33.821326] hdd: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 22 22:03:36 Dans kernel: [   33.821563] hdd: host side 80-wire cable detection failed, limiting max speed to UDMA33
Aug 22 22:03:36 Dans kernel: [   33.821618] hdd: UDMA/33 mode selected
Aug 22 22:03:36 Dans kernel: [   33.822963] ide1 at 0x170-0x177,0x376 on irq 15
Aug 22 22:03:36 Dans kernel: [   37.705366] usb-storage: device scan complete
Aug 22 22:03:36 Dans kernel: [   38.041150] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Aug 22 22:03:36 Dans kernel: [   38.047143] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Aug 22 22:03:36 Dans kernel: [   38.053141] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Aug 22 22:03:36 Dans kernel: [   38.059787] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Aug 22 22:03:36 Dans kernel: [   38.073383] Driver 'sd' needs updating - please use bus_type methods
Aug 22 22:03:36 Dans kernel: [   38.073574] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 22 22:03:36 Dans kernel: [   38.073649] sd 2:0:0:0: [sda] Write Protect is off
Aug 22 22:03:36 Dans kernel: [   38.073704] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 22:03:36 Dans kernel: [   38.073752] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 22:03:36 Dans kernel: [   38.073910] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 22 22:03:36 Dans kernel: [   38.073991] sd 2:0:0:0: [sda] Write Protect is off
Aug 22 22:03:36 Dans kernel: [   38.074047] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 22:03:36 Dans kernel: [   38.074085] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 22:03:36 Dans kernel: [   38.074159]  sda: sda1 sda2 < sda5 >
Aug 22 22:03:36 Dans kernel: [   37.785141] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 22 22:03:36 Dans kernel: [   38.124166] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug 22 22:03:36 Dans kernel: [   38.134167] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Aug 22 22:03:36 Dans kernel: [   38.144150] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Aug 22 22:03:36 Dans kernel: [   38.154146] sd 4:0:0:3: [sde] Attached SCSI removable disk
Aug 22 22:03:36 Dans kernel: [   37.833429] sd 2:0:0:0: Attached scsi generic sg0 type 0
Aug 22 22:03:36 Dans kernel: [   37.833526] sd 4:0:0:0: Attached scsi generic sg1 type 0
Aug 22 22:03:36 Dans kernel: [   37.833611] sd 4:0:0:1: Attached scsi generic sg2 type 0
Aug 22 22:03:36 Dans kernel: [   37.833689] sd 4:0:0:2: Attached scsi generic sg3 type 0
Aug 22 22:03:36 Dans kernel: [   37.833767] sd 4:0:0:3: Attached scsi generic sg4 type 0
Aug 22 22:03:36 Dans kernel: [   63.809896] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [   93.799670] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  123.789436] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  153.780185] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  183.768954] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  209.817911] Attempting manual resume
Aug 22 22:03:36 Dans kernel: [  209.817960] swsusp: Resume From Partition 8:5
Aug 22 22:03:36 Dans kernel: [  209.817962] PM: Checking swsusp image.
Aug 22 22:03:36 Dans kernel: [  209.818188] PM: Resume from disk failed.
Aug 22 22:03:36 Dans kernel: [  210.205218] kjournald starting.  Commit interval 5 seconds
Aug 22 22:03:36 Dans kernel: [  209.875450] EXT3-fs: mounted filesystem with ordered data mode.
Aug 22 22:03:36 Dans kernel: [  213.758826] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  217.362772] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 22 22:03:36 Dans kernel: [  217.849604] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 22 22:03:36 Dans kernel: [  217.627711] parport_pc 00:06: reported by Plug and Play ACPI
Aug 22 22:03:36 Dans kernel: [  217.627895] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Aug 22 22:03:36 Dans kernel: [  217.715834] Linux agpgart interface v0.102
Aug 22 22:03:36 Dans kernel: [  218.175566] input: Power Button (FF) as /devices/virtual/input/input3
Aug 22 22:03:36 Dans kernel: [  218.227337] ACPI: Power Button (FF) [PWRF]
Aug 22 22:03:36 Dans kernel: [  218.227527] input: Power Button (CM) as /devices/virtual/input/input4
Aug 22 22:03:36 Dans kernel: [  218.287334] ACPI: Power Button (CM) [PWRB]
Aug 22 22:03:36 Dans kernel: [  218.683479] sysfs: duplicate filename 'pcspkr' can not be created
Aug 22 22:03:36 Dans kernel: [  218.683545] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
Aug 22 22:03:36 Dans kernel: [  218.683612] Pid: 8357, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 22 22:03:36 Dans kernel: [  218.683687]  [sysfs_add_one+0x9f/0xe0] sysfs_add_one+0x9f/0xe0
Aug 22 22:03:36 Dans kernel: [  218.683797]  [create_dir+0x48/0x90] create_dir+0x48/0x90
Aug 22 22:03:36 Dans kernel: [  218.683898]  [sysfs_create_dir+0x29/0x50] sysfs_create_dir+0x29/0x50
Aug 22 22:03:36 Dans kernel: [  218.683999]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
Aug 22 22:03:36 Dans kernel: [  218.684098]  [kobject_add+0x93/0x1b0] kobject_add+0x93/0x1b0
Aug 22 22:03:36 Dans kernel: [  218.684202]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 22 22:03:36 Dans kernel: [  218.684304]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 22 22:03:36 Dans kernel: [  218.684406]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 22 22:03:36 Dans kernel: [  218.684537]  [<c013f260>] param_get_int+0x0/0x20
Aug 22 22:03:36 Dans kernel: [  218.684645]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 22 22:03:36 Dans kernel: [  218.684750]  =======================
Aug 22 22:03:36 Dans kernel: [  218.684804] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
Aug 22 22:03:36 Dans kernel: [  218.684872] Pid: 8357, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 22 22:03:36 Dans kernel: [  218.684934]  [kobject_add+0x113/0x1b0] kobject_add+0x113/0x1b0
Aug 22 22:03:36 Dans kernel: [  218.685035]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 22 22:03:36 Dans kernel: [  218.685134]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 22 22:03:36 Dans kernel: [  218.685234]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 22 22:03:36 Dans kernel: [  218.685352]  [<c013f260>] param_get_int+0x0/0x20
Aug 22 22:03:36 Dans kernel: [  218.685448]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 22 22:03:36 Dans kernel: [  218.685546]  =======================
Aug 22 22:03:36 Dans kernel: [  219.593769] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 22 22:03:36 Dans kernel: [  219.646941] ieee80211_crypt: registered algorithm 'NULL'
Aug 22 22:03:36 Dans kernel: [  219.660025] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 22 22:03:36 Dans kernel: [  219.660089] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 22 22:03:36 Dans kernel: [  220.365527] usb 1-4: reset full speed USB device using ohci_hcd and address 3
Aug 22 22:03:36 Dans kernel: [  220.240779] zd1211rw 1-4:1.0: eth1
Aug 22 22:03:36 Dans kernel: [  220.240850] usbcore: registered new interface driver zd1211rw
Aug 22 22:03:36 Dans kernel: [  220.999263] zd1211rw 1-4:1.0: firmware version 4725
Aug 22 22:03:36 Dans kernel: [  221.039255] zd1211rw 1-4:1.0: zd1211b chip 050d:705c v4810 full 00-17-3f AL2230_RF pa0 g--NS
Aug 22 22:03:36 Dans kernel: [  222.282268] NET: Registered protocol family 17
Aug 22 22:03:36 Dans kernel: [  233.823613] SoftMAC: Open Authentication completed with 00:18:d1:28:4f:05
Aug 22 22:03:36 Dans kernel: [  243.749478] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  273.739243] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  303.729017] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  333.718771] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  363.708535] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  393.698299] hdc: lost interrupt
Aug 22 22:03:36 Dans kernel: [  399.086933] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:03:36 Dans kernel: [  401.216348] lp0: using parport0 (interrupt-driven).
Aug 22 22:03:36 Dans kernel: [  401.304536] Adding 5887780k swap on /dev/sda5.  Priority:-1 extents:1 across:5887780k
Aug 22 22:03:36 Dans kernel: [  401.732951] EXT3 FS on sda1, internal journal
Aug 22 22:03:36 Dans kernel: [  402.396764] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 22 22:03:36 Dans kernel: [  403.144693] NET: Registered protocol family 10
Aug 22 22:03:36 Dans kernel: [  403.145134] lo: Disabled Privacy Extensions
Aug 22 22:03:36 Dans kernel: [  405.783972] No dock devices found.
Aug 22 22:03:36 Dans NetworkManager: <info>  starting... 
Aug 22 22:03:36 Dans avahi-daemon[12272]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 22 22:03:36 Dans avahi-daemon[12272]: Successfully dropped root privileges.
Aug 22 22:03:36 Dans avahi-daemon[12272]: avahi-daemon 0.6.22 starting up.
Aug 22 22:03:36 Dans avahi-daemon[12272]: Successfully called chroot().
Aug 22 22:03:36 Dans avahi-daemon[12272]: Successfully dropped remaining capabilities.
Aug 22 22:03:36 Dans avahi-daemon[12272]: No service file found in /etc/avahi/services.
Aug 22 22:03:36 Dans avahi-daemon[12272]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 22 22:03:36 Dans avahi-daemon[12272]: New relevant interface eth1.IPv4 for mDNS.
Aug 22 22:03:36 Dans avahi-daemon[12272]: Network interface enumeration completed.
Aug 22 22:03:36 Dans avahi-daemon[12272]: Registering new address record for fe80::217:3fff:fe34:c1de on eth1.*.
Aug 22 22:03:36 Dans avahi-daemon[12272]: Registering new address record for 192.168.2.10 on eth1.IPv4.
Aug 22 22:03:36 Dans avahi-daemon[12272]: Registering new address record for fe80::214:2aff:feb6:ae32 on eth0.*.
Aug 22 22:03:36 Dans avahi-daemon[12272]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 22 22:03:36 Dans kernel: [  406.998454] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 22 22:03:36 Dans kernel: [  406.998461] apm: disabled - APM is not SMP safe.
Aug 22 22:03:36 Dans kernel: [  407.189782] ppdev: user-space parallel port driver
Aug 22 22:03:36 Dans kernel: [  407.348465] audit(1219457016.786:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=12318 profile="/usr/sbin/cupsd" namespace="default"
Aug 22 22:03:37 Dans avahi-daemon[12272]: Server startup complete. Host name is Dans.local. Local service cookie is 1224132518.
Aug 22 22:03:38 Dans kernel: [  409.744384] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Aug 22 22:03:38 Dans kernel: [  409.744395] vboxdrv: Successfully done.
Aug 22 22:03:38 Dans kernel: [  409.744398] vboxdrv: Found 2 processor cores.
Aug 22 22:03:38 Dans kernel: [  409.744427] vboxdrv: fAsync=1 u64DiffCores=1055312816.
Aug 22 22:03:38 Dans kernel: [  409.744984] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Aug 22 22:03:38 Dans kernel: [  409.744990] vboxdrv: Successfully loaded version 1.6.4 (interface 0x00080000).
Aug 22 22:03:39 Dans dhcdbd: Started up.
Aug 22 22:03:40 Dans dhclient: DHCPREQUEST of 192.168.2.11 on eth0 to 255.255.255.255 port 67
Aug 22 22:03:40 Dans NetworkManager: <debug> [1219457020.090223] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_USB_MS_Reader_2004888_0_3'). 
Aug 22 22:03:40 Dans kernel: [  411.135346] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 22:03:40 Dans anacron[12662]: Anacron 2.3 started on 2008-08-22
Aug 22 22:03:40 Dans anacron[12662]: Normal exit (0 jobs run)
Aug 22 22:03:40 Dans /usr/sbin/cron[12696]: (CRON) INFO (pidfile fd = 3)
Aug 22 22:03:40 Dans /usr/sbin/cron[12700]: (CRON) STARTUP (fork ok)
Aug 22 22:03:40 Dans /usr/sbin/cron[12700]: (CRON) INFO (Running @reboot jobs)
Aug 22 22:03:42 Dans kernel: [  413.280713] eth1: no IPv6 routers present
Aug 22 22:03:43 Dans kernel: [  413.588607] eth0: no IPv6 routers present
Aug 22 22:03:43 Dans kernel: [  414.134344] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 22:03:43 Dans kernel: [  414.134349] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 22:03:43 Dans kernel: [  414.134356] eth0:  Tx descriptor 0 is 0008a05a. (queue head)
Aug 22 22:03:43 Dans kernel: [  414.134361] eth0:  Tx descriptor 1 is 0008a04e.
Aug 22 22:03:43 Dans kernel: [  414.134368] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 22:03:43 Dans kernel: [  414.134373] eth0:  Tx descriptor 3 is 0008a05a.
Aug 22 22:03:43 Dans kernel: [  414.134426] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:03:50 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug 22 22:03:52 Dans kernel: [  423.132249] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 22:03:53 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 22 22:03:55 Dans kernel: [  426.134555] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 22:03:55 Dans kernel: [  426.134566] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 22:03:55 Dans kernel: [  426.134576] eth0:  Tx descriptor 0 is 0008a046. (queue head)
Aug 22 22:03:55 Dans kernel: [  426.134584] eth0:  Tx descriptor 1 is 0008a046.
Aug 22 22:03:55 Dans kernel: [  426.134591] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 22:03:55 Dans kernel: [  426.134599] eth0:  Tx descriptor 3 is 0008a046.
Aug 22 22:03:55 Dans kernel: [  426.134687] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:04:00 Dans NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 22 22:04:00 Dans NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 22 22:04:01 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Aug 22 22:04:01 Dans NetworkManager: <info>  User request to disable wireless. 
Aug 22 22:04:17 Dans dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Aug 22 22:04:21 Dans dhclient: No DHCPOFFERS received.
Aug 22 22:04:21 Dans dhclient: Trying recorded lease 192.168.2.11
Aug 22 22:04:21 Dans avahi-daemon[12272]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 22 22:04:21 Dans avahi-daemon[12272]: New relevant interface eth0.IPv4 for mDNS.
Aug 22 22:04:21 Dans avahi-daemon[12272]: Registering new address record for 192.168.2.11 on eth0.IPv4.
Aug 22 22:04:21 Dans avahi-autoipd(eth0)[13090]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Aug 22 22:04:21 Dans avahi-autoipd(eth0)[13090]: Successfully called chroot().
Aug 22 22:04:21 Dans avahi-autoipd(eth0)[13090]: Successfully dropped root privileges.
Aug 22 22:04:21 Dans avahi-autoipd(eth0)[13090]: Starting with address 169.254.5.131
Aug 22 22:04:21 Dans avahi-autoipd(eth0)[13090]: Routable address already assigned, sleeping.
Aug 22 22:04:21 Dans dhclient: bound: renewal in 102566 seconds.
Aug 22 22:04:21 Dans ntpdate[13124]: adjust time server 91.189.94.4 offset -0.002823 sec
Aug 22 22:04:25 Dans kernel: [  455.799796] hdc: lost interrupt
Aug 22 22:04:28 Dans kernel: [  459.123052] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 22:04:31 Dans kernel: [  462.123190] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 22:04:31 Dans kernel: [  462.123197] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 22:04:31 Dans kernel: [  462.123206] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 22:04:31 Dans kernel: [  462.123212] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 22:04:31 Dans kernel: [  462.123217] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 22:04:31 Dans kernel: [  462.123224] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 22:04:31 Dans kernel: [  462.123276] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:04:40 Dans kernel: [  471.119107] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 22:04:43 Dans kernel: [  474.118102] eth0: Transmit timeout, status 0d 0004 c07f media 10.
Aug 22 22:04:43 Dans kernel: [  474.118108] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 22:04:43 Dans kernel: [  474.118113] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Aug 22 22:04:43 Dans kernel: [  474.118118] eth0:  Tx descriptor 1 is 0008a052.
Aug 22 22:04:43 Dans kernel: [  474.118122] eth0:  Tx descriptor 2 is 0008a160.
Aug 22 22:04:43 Dans kernel: [  474.118126] eth0:  Tx descriptor 3 is 0008a099.
Aug 22 22:04:43 Dans kernel: [  474.118176] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:04:52 Dans kernel: [  483.116009] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 22:04:55 Dans kernel: [  486.114006] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 22:04:55 Dans kernel: [  486.114012] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 22:04:55 Dans kernel: [  486.114019] eth0:  Tx descriptor 0 is 0008a160. (queue head)
Aug 22 22:04:55 Dans kernel: [  486.114024] eth0:  Tx descriptor 1 is 0008a160.
Aug 22 22:04:55 Dans kernel: [  486.114031] eth0:  Tx descriptor 2 is 0008a148.
Aug 22 22:04:55 Dans kernel: [  486.114036] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 22:04:55 Dans kernel: [  486.114086] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:05:04 Dans kernel: [  495.111914] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 22:05:07 Dans kernel: [  498.110911] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 22:05:07 Dans kernel: [  498.110918] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 22:05:07 Dans kernel: [  498.110923] eth0:  Tx descriptor 0 is 0008a099. (queue head)
Aug 22 22:05:07 Dans kernel: [  498.110928] eth0:  Tx descriptor 1 is 0008a148.
Aug 22 22:05:07 Dans kernel: [  498.110932] eth0:  Tx descriptor 2 is 0008a052.
Aug 22 22:05:07 Dans kernel: [  498.110936] eth0:  Tx descriptor 3 is 0008a0eb.
Aug 22 22:05:07 Dans kernel: [  498.110986] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:05:16 Dans kernel: [  507.106824] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 22:05:19 Dans kernel: [  510.105821] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 22:05:19 Dans kernel: [  510.105828] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 22:05:19 Dans kernel: [  510.105834] eth0:  Tx descriptor 0 is 0008a148. (queue head)
Aug 22 22:05:19 Dans kernel: [  510.105840] eth0:  Tx descriptor 1 is 0008a03c.
Aug 22 22:05:19 Dans kernel: [  510.105847] eth0:  Tx descriptor 2 is 0008a052.
Aug 22 22:05:19 Dans kernel: [  510.105851] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 22:05:19 Dans kernel: [  510.105903] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:05:49 Dans kernel: [  539.767819] hdc: lost interrupt
Aug 22 22:06:19 Dans kernel: [  569.755546] hdc: lost interrupt
Aug 22 22:06:49 Dans kernel: [  599.745316] hdc: lost interrupt
Aug 22 22:07:19 Dans kernel: [  629.735085] hdc: lost interrupt
Aug 22 22:07:49 Dans kernel: [  659.724861] hdc: lost interrupt
Aug 22 22:08:19 Dans kernel: [  689.714621] hdc: lost interrupt
Aug 22 22:08:46 Dans kernel: [  717.035174] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 22:08:49 Dans kernel: [  719.704381] hdc: lost interrupt
Aug 22 22:08:49 Dans kernel: [  720.034200] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 22:08:49 Dans kernel: [  720.034205] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 22:08:49 Dans kernel: [  720.034212] eth0:  Tx descriptor 0 is 0008a052. (queue head)
Aug 22 22:08:49 Dans kernel: [  720.034220] eth0:  Tx descriptor 1 is 0008a052.
Aug 22 22:08:49 Dans kernel: [  720.034228] eth0:  Tx descriptor 2 is 0008a052.
Aug 22 22:08:49 Dans kernel: [  720.034234] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 22:08:49 Dans kernel: [  720.034285] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 22:09:19 Dans kernel: [  749.694135] hdc: lost interrupt
Aug 22 22:09:49 Dans kernel: [  779.687896] hdc: lost interrupt
Aug 22 22:10:19 Dans kernel: [  809.673662] hdc: lost interrupt
Aug 22 22:10:49 Dans kernel: [  839.663430] hdc: lost interrupt
Aug 22 22:11:19 Dans kernel: [  869.653196] hdc: lost interrupt
Aug 22 22:11:49 Dans kernel: [  899.642959] hdc: lost interrupt
Aug 22 22:12:19 Dans kernel: [  929.632721] hdc: lost interrupt
Aug 22 22:12:49 Dans kernel: [  959.622488] hdc: lost interrupt
Aug 22 22:13:19 Dans kernel: [  989.612257] hdc: lost interrupt
Aug 22 22:13:49 Dans kernel: [ 1019.602018] hdc: lost interrupt
Aug 22 22:14:19 Dans kernel: [ 1049.591778] hdc: lost interrupt
Aug 22 22:14:49 Dans kernel: [ 1079.581569] hdc: lost interrupt
Aug 22 22:15:19 Dans kernel: [ 1109.571330] hdc: lost interrupt
Aug 22 22:15:49 Dans kernel: [ 1139.561070] hdc: lost interrupt
Aug 22 22:16:19 Dans kernel: [ 1169.554831] hdc: lost interrupt
Aug 22 22:16:49 Dans kernel: [ 1199.544596] hdc: lost interrupt
Aug 22 22:17:01 Dans /USR/SBIN/CRON[13431]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 22:17:19 Dans kernel: [ 1229.530368] hdc: lost interrupt
Aug 22 22:17:49 Dans kernel: [ 1259.520149] hdc: lost interrupt
Aug 22 22:18:19 Dans kernel: [ 1289.509901] hdc: lost interrupt
Aug 22 22:18:49 Dans kernel: [ 1319.501651] hdc: lost interrupt
Aug 22 22:19:19 Dans kernel: [ 1349.489430] hdc: lost interrupt
Aug 22 22:19:49 Dans kernel: [ 1379.479205] hdc: lost interrupt
Aug 22 22:20:19 Dans kernel: [ 1409.468959] hdc: lost interrupt
Aug 22 22:20:49 Dans kernel: [ 1439.458726] hdc: lost interrupt
Aug 22 22:21:19 Dans kernel: [ 1469.448509] hdc: lost interrupt
Aug 22 22:21:49 Dans kernel: [ 1499.438265] hdc: lost interrupt
Aug 22 22:22:19 Dans kernel: [ 1529.428008] hdc: lost interrupt
Aug 22 22:22:49 Dans kernel: [ 1559.421770] hdc: lost interrupt
Aug 22 22:23:09 Dans NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 22 22:23:09 Dans NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 22 22:23:19 Dans kernel: [ 1589.407561] hdc: lost interrupt
Aug 22 22:23:49 Dans kernel: [ 1619.397322] hdc: lost interrupt
Aug 22 22:24:19 Dans kernel: [ 1649.387684] hdc: lost interrupt
Aug 22 22:24:49 Dans kernel: [ 1679.376831] hdc: lost interrupt
Aug 22 22:25:19 Dans kernel: [ 1709.366615] hdc: lost interrupt
Aug 22 22:25:49 Dans kernel: [ 1739.360354] hdc: lost interrupt
Aug 22 22:26:19 Dans kernel: [ 1769.346121] hdc: lost interrupt
Aug 22 22:26:49 Dans kernel: [ 1799.335888] hdc: lost interrupt
Aug 22 22:27:19 Dans kernel: [ 1829.329647] hdc: lost interrupt
Aug 22 22:27:49 Dans kernel: [ 1859.315435] hdc: lost interrupt
Aug 22 22:28:19 Dans kernel: [ 1889.305187] hdc: lost interrupt
Aug 22 22:28:49 Dans kernel: [ 1919.294971] hdc: lost interrupt
Aug 22 22:29:19 Dans kernel: [ 1949.284710] hdc: lost interrupt
Aug 22 22:29:49 Dans kernel: [ 1979.274482] hdc: lost interrupt
Aug 22 22:30:19 Dans kernel: [ 2009.264236] hdc: lost interrupt
Aug 22 22:30:49 Dans kernel: [ 2039.253999] hdc: lost interrupt
Aug 22 22:31:19 Dans kernel: [ 2069.243766] hdc: lost interrupt
Aug 22 22:31:49 Dans kernel: [ 2099.233533] hdc: lost interrupt
Aug 22 22:32:19 Dans kernel: [ 2129.223313] hdc: lost interrupt
Aug 22 22:32:49 Dans kernel: [ 2159.213062] hdc: lost interrupt
Aug 22 22:33:19 Dans kernel: [ 2189.206819] hdc: lost interrupt
Aug 22 22:33:49 Dans kernel: [ 2219.192595] hdc: lost interrupt
Aug 22 22:34:19 Dans kernel: [ 2249.182354] hdc: lost interrupt
Aug 22 22:34:49 Dans kernel: [ 2279.176112] hdc: lost interrupt
Aug 22 22:34:57 Dans kernel: [ 2287.617264] usb 1-3: USB disconnect, address 2
Aug 22 22:34:57 Dans NetworkManager: <debug> [1219458897.699037] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b2_30_no_serial_number_if0'). 
Aug 22 22:34:57 Dans NetworkManager: <debug> [1219458897.702768] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b2_30_no_serial_number_if1'). 
Aug 22 22:34:57 Dans NetworkManager: <debug> [1219458897.705970] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_13b2_30_no_serial_number'). 
Aug 22 22:35:19 Dans kernel: [ 2309.161902] hdc: lost interrupt
Aug 22 22:35:49 Dans kernel: [ 2339.151645] hdc: lost interrupt
Aug 22 22:36:19 Dans kernel: [ 2369.141413] hdc: lost interrupt
Aug 22 22:36:49 Dans kernel: [ 2399.131190] hdc: lost interrupt
Aug 22 22:37:19 Dans kernel: [ 2429.120963] hdc: lost interrupt
Aug 22 22:37:49 Dans kernel: [ 2459.110730] hdc: lost interrupt
Aug 22 22:38:19 Dans kernel: [ 2489.100486] hdc: lost interrupt
Aug 22 22:38:49 Dans kernel: [ 2519.090241] hdc: lost interrupt
Aug 22 22:39:19 Dans kernel: [ 2549.080023] hdc: lost interrupt
Aug 22 22:39:49 Dans kernel: [ 2579.069759] hdc: lost interrupt
Aug 22 22:40:19 Dans kernel: [ 2609.059522] hdc: lost interrupt
Aug 22 22:40:49 Dans kernel: [ 2639.049291] hdc: lost interrupt
Aug 22 22:41:19 Dans kernel: [ 2669.039081] hdc: lost interrupt
Aug 22 22:41:49 Dans kernel: [ 2699.028830] hdc: lost interrupt
Aug 22 22:42:19 Dans kernel: [ 2729.018584] hdc: lost interrupt
Aug 22 22:42:49 Dans kernel: [ 2759.008357] hdc: lost interrupt
Aug 22 22:43:19 Dans kernel: [ 2789.002107] hdc: lost interrupt
Aug 22 22:43:49 Dans kernel: [ 2818.987874] hdc: lost interrupt
Aug 22 22:44:19 Dans kernel: [ 2848.977658] hdc: lost interrupt
Aug 22 22:44:49 Dans kernel: [ 2878.967412] hdc: lost interrupt
Aug 22 22:45:19 Dans kernel: [ 2908.957177] hdc: lost interrupt
Aug 22 22:45:49 Dans kernel: [ 2938.946950] hdc: lost interrupt
Aug 22 22:46:19 Dans kernel: [ 2968.940696] hdc: lost interrupt
Aug 22 22:46:49 Dans kernel: [ 2998.930459] hdc: lost interrupt
Aug 22 22:47:19 Dans kernel: [ 3028.920224] hdc: lost interrupt
Aug 22 22:47:49 Dans kernel: [ 3058.909992] hdc: lost interrupt
Aug 22 22:48:19 Dans kernel: [ 3088.901168] hdc: lost interrupt
Aug 22 22:48:49 Dans kernel: [ 3118.893512] hdc: lost interrupt
Aug 22 22:49:19 Dans kernel: [ 3148.879280] hdc: lost interrupt
Aug 22 22:49:49 Dans kernel: [ 3178.869063] hdc: lost interrupt
Aug 22 22:50:19 Dans kernel: [ 3208.858811] hdc: lost interrupt
Aug 22 22:50:49 Dans kernel: [ 3238.848575] hdc: lost interrupt
Aug 22 22:51:19 Dans kernel: [ 3268.838344] hdc: lost interrupt
Aug 22 22:51:49 Dans kernel: [ 3298.828104] hdc: lost interrupt
Aug 22 22:52:19 Dans kernel: [ 3328.817869] hdc: lost interrupt
Aug 22 22:52:49 Dans kernel: [ 3358.807632] hdc: lost interrupt
Aug 22 22:53:19 Dans kernel: [ 3388.797395] hdc: lost interrupt
Aug 22 22:53:49 Dans kernel: [ 3418.791156] hdc: lost interrupt
Aug 22 22:54:19 Dans kernel: [ 3448.776925] hdc: lost interrupt
Aug 22 22:54:29 Dans init: tty4 main process (11797) killed by TERM signal
Aug 22 22:54:29 Dans init: tty5 main process (11798) killed by TERM signal
Aug 22 22:54:29 Dans init: tty2 main process (11800) killed by TERM signal
Aug 22 22:54:29 Dans init: tty3 main process (11803) killed by TERM signal
Aug 22 22:54:29 Dans init: tty6 main process (11804) killed by TERM signal
Aug 22 22:54:29 Dans init: tty1 main process (12805) killed by TERM signal
Aug 22 22:54:29 Dans gdm[12636]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Aug 22 22:54:29 Dans gdm[12636]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Aug 22 22:54:32 Dans avahi-daemon[12272]: Got SIGTERM, quitting.
Aug 22 22:54:32 Dans avahi-daemon[12272]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 22 22:54:32 Dans avahi-daemon[12272]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 22 22:54:33 Dans kernel: [ 3463.080633] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 22 22:54:33 Dans exiting on signal 15
Aug 22 23:15:04 Dans syslogd 1.5.0#1ubuntu1: restart.
Aug 22 23:15:04 Dans kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 22 23:15:04 Dans kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 22 23:15:04 Dans kernel: Symbols match kernel version 2.6.24.
Aug 22 23:15:04 Dans kernel: Loaded 20154 symbols from 92 modules.
Aug 22 23:15:04 Dans kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 22 23:15:04 Dans kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 22 23:15:04 Dans kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 22 23:15:04 Dans kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 22 23:15:04 Dans kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 22 23:15:04 Dans kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 22 23:15:04 Dans kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Aug 22 23:15:04 Dans kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bfd0000 (usable)
Aug 22 23:15:04 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfd0000 - 000000007bfde000 (ACPI data)
Aug 22 23:15:04 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfde000 - 000000007c000000 (ACPI NVS)
Aug 22 23:15:04 Dans kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 22 23:15:04 Dans kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Aug 22 23:15:04 Dans kernel: [    0.000000] 1087MB HIGHMEM available.
Aug 22 23:15:04 Dans kernel: [    0.000000] 896MB LOWMEM available.
Aug 22 23:15:04 Dans kernel: [    0.000000] found SMP MP-table at 000ff780
Aug 22 23:15:04 Dans kernel: [    0.000000] Entering add_active_range(0, 0, 507856) 0 entries of 256 used
Aug 22 23:15:04 Dans kernel: [    0.000000] Zone PFN ranges:
Aug 22 23:15:04 Dans kernel: [    0.000000]   DMA             0 ->     4096
Aug 22 23:15:04 Dans kernel: [    0.000000]   Normal       4096 ->   229376
Aug 22 23:15:04 Dans kernel: [    0.000000]   HighMem    229376 ->   507856
Aug 22 23:15:04 Dans kernel: [    0.000000] Movable zone start PFN for each node
Aug 22 23:15:04 Dans kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 22 23:15:04 Dans kernel: [    0.000000]     0:        0 ->   507856
Aug 22 23:15:04 Dans kernel: [    0.000000] On node 0 totalpages: 507856
Aug 22 23:15:04 Dans kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 22 23:15:04 Dans kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 22 23:15:04 Dans kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 22 23:15:04 Dans kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 22 23:15:04 Dans kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 22 23:15:04 Dans kernel: [    0.000000]   HighMem zone: 2175 pages used for memmap
Aug 22 23:15:04 Dans kernel: [    0.000000]   HighMem zone: 276305 pages, LIFO batch:31
Aug 22 23:15:04 Dans kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 22 23:15:04 Dans kernel: [    0.000000] DMI present.
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8890 checksum 0
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: RSDP 000F8890, 0014 (r0 HP-CPC)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: RSDT 7BFD0000, 0038 (r1 HP-CPC OEMRSDT  11000518 MSFT       97)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: FACP 7BFD0200, 0084 (r2 HP-CPC OEMFACP  11000518 MSFT       97)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: DSDT 7BFD0440, 43B0 (r1 HP-CPC  RC410-M        0 INTL  2002026)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: FACS 7BFDE000, 0040
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: APIC 7BFD0390, 006C (r1 HP-CPC OEMAPIC  11000518 MSFT       97)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: MCFG 7BFD0400, 003C (r1 HP-CPC OEMMCFG  11000518 MSFT       97)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: OEMB 7BFDE040, 005B (r1 HP-CPC AMI_OEM  11000518 MSFT       97)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: HPET 7BFD47F0, 0038 (r1 HP-CPC OEMHPET  11000518 MSFT       97)
Aug 22 23:15:04 Dans kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 22 23:15:04 Dans kernel: [    0.000000] Processor #0 15:4 APIC version 20
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 22 23:15:04 Dans kernel: [    0.000000] Processor #1 15:4 APIC version 20
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
Aug 22 23:15:04 Dans kernel: [    0.000000] ACPI: HPET id: 0x0 base: 0xfed00000
Aug 22 23:15:04 Dans kernel: [    0.000000] Using ACPI for processor (LAPIC) configuration information
Aug 22 23:15:04 Dans kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Aug 22 23:15:04 Dans kernel: [    0.000000]     Virtual Wire compatibility mode.
Aug 22 23:15:04 Dans kernel: [    0.000000] OEM ID: ATI      Product ID: RS400        APIC at: 0xFEE00000
Aug 22 23:15:04 Dans kernel: [    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
Aug 22 23:15:04 Dans kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 22 23:15:04 Dans kernel: [    0.000000] Processors: 2
Aug 22 23:15:04 Dans kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7c000000:82e00000)
Aug 22 23:15:04 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 22 23:15:04 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
Aug 22 23:15:04 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Aug 22 23:15:04 Dans kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503889
Aug 22 23:15:04 Dans kernel: [    0.000000] Kernel command line: root=UUID=e9a7cff5-d8ae-4fb4-a348-d2db06aed623 ro single noapic
Aug 22 23:15:04 Dans kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 22 23:15:04 Dans kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 22 23:15:04 Dans kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 22 23:15:04 Dans kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 22 23:15:04 Dans kernel: [    0.000000] Initializing CPU#0
Aug 22 23:15:04 Dans kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 22 23:15:04 Dans kernel: [    0.000000] Detected 3199.175 MHz processor.
Aug 22 23:15:04 Dans kernel: [   59.434291] Console: colour VGA+ 80x25
Aug 22 23:15:04 Dans kernel: [   59.434296] console [tty0] enabled
Aug 22 23:15:04 Dans kernel: [   59.437964] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 22 23:15:04 Dans kernel: [   59.438717] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 22 23:15:04 Dans kernel: [   59.547975] Memory: 2001980k/2031424k available (2177k kernel code, 28188k reserved, 1006k data, 368k init, 1113920k highmem)
Aug 22 23:15:04 Dans kernel: [   59.548049] virtual kernel memory layout:
Aug 22 23:15:04 Dans kernel: [   59.548050]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 22 23:15:04 Dans kernel: [   59.548051]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 22 23:15:04 Dans kernel: [   59.548052]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 22 23:15:04 Dans kernel: [   59.548053]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 22 23:15:04 Dans kernel: [   59.548053]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 22 23:15:04 Dans kernel: [   59.548054]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 22 23:15:04 Dans kernel: [   59.548055]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 22 23:15:04 Dans kernel: [   59.548416] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 22 23:15:04 Dans kernel: [   59.548569] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 22 23:15:04 Dans kernel: [   59.548732] hpet clockevent registered
Aug 22 23:15:04 Dans kernel: [   60.627905] Calibrating delay using timer specific routine.. 88384.36 BogoMIPS (lpj=176768734)
Aug 22 23:15:04 Dans kernel: [   60.628027] Security Framework initialized
Aug 22 23:15:04 Dans kernel: [   60.628080] SELinux:  Disabled at boot.
Aug 22 23:15:04 Dans kernel: [   60.628147] AppArmor: AppArmor initialized
Aug 22 23:15:04 Dans kernel: [   60.628196] Failure registering capabilities with primary security module.
Aug 22 23:15:04 Dans kernel: [   60.628252] Mount-cache hash table entries: 512
Aug 22 23:15:04 Dans kernel: [   60.628468] Initializing cgroup subsys ns
Aug 22 23:15:04 Dans kernel: [   60.628520] Initializing cgroup subsys cpuacct
Aug 22 23:15:04 Dans kernel: [   60.628579] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 22 23:15:04 Dans kernel: [   60.628588] monitor/mwait feature present.
Aug 22 23:15:04 Dans kernel: [   60.628633] using mwait in idle threads.
Aug 22 23:15:04 Dans kernel: [   60.628684] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 22 23:15:04 Dans kernel: [   60.628767] CPU: L2 cache: 2048K
Aug 22 23:15:04 Dans kernel: [   60.628812] CPU: Physical Processor ID: 0
Aug 22 23:15:04 Dans kernel: [   60.628858] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 22 23:15:04 Dans kernel: [   60.628871] Compat vDSO mapped to ffffe000.
Aug 22 23:15:04 Dans kernel: [   60.628934] Checking 'hlt' instruction... OK.
Aug 22 23:15:04 Dans kernel: [   60.848077] SMP alternatives: switching to UP code
Aug 22 23:15:04 Dans kernel: [   60.850042] Early unpacking initramfs... done
Aug 22 23:15:04 Dans kernel: [   61.136635] ACPI: Core revision 20070126
Aug 22 23:15:04 Dans kernel: [   61.136739] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 22 23:15:04 Dans kernel: [   61.138744] ACPI: setting ELCR to 0200 (from 0c38)
Aug 22 23:15:04 Dans kernel: [   61.139454] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 22 23:15:04 Dans kernel: [   61.139592] SMP alternatives: switching to SMP code
Aug 22 23:15:04 Dans kernel: [   61.140472] Booting processor 1/1 eip 3000
Aug 22 23:15:04 Dans kernel: [   61.501119] Initializing CPU#1
Aug 22 23:15:04 Dans kernel: [   62.550174] Calibrating delay using timer specific routine.. 87854.92 BogoMIPS (lpj=175709856)
Aug 22 23:15:04 Dans kernel: [   62.550185] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 22 23:15:04 Dans kernel: [   62.550192] monitor/mwait feature present.
Aug 22 23:15:04 Dans kernel: [   62.550199] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 22 23:15:04 Dans kernel: [   62.550201] CPU: L2 cache: 2048K
Aug 22 23:15:04 Dans kernel: [   62.550204] CPU: Physical Processor ID: 0
Aug 22 23:15:04 Dans kernel: [   62.550206] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 22 23:15:04 Dans kernel: [   62.220882] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 22 23:15:04 Dans kernel: [   62.221329] Total of 2 processors activated (176239.29 BogoMIPS).
Aug 22 23:15:04 Dans kernel: [   63.702822] APIC calibration not consistent with PM Timer: 1373ms instead of 100ms
Aug 22 23:15:04 Dans kernel: [   63.702879] APIC delta adjusted to PM-Timer: 1249643 (17159332)
Aug 22 23:15:04 Dans kernel: [   63.703078] checking TSC synchronization [CPU#0 -> CPU#1]:
Aug 22 23:15:04 Dans kernel: [   63.723161] Measured 1055774576 cycles TSC warp between CPUs, turning off TSC clock.
Aug 22 23:15:04 Dans kernel: [   63.723218] Marking TSC unstable due to: check_tsc_sync_source failed.
Aug 22 23:15:04 Dans kernel: [   63.723284] Brought up 2 CPUs
Aug 22 23:15:04 Dans kernel: [   63.723349] CPU0 attaching sched-domain:
Aug 22 23:15:04 Dans kernel: [   63.723352]  domain 0: span 03
Aug 22 23:15:04 Dans kernel: [   63.723354]   groups: 01 02
Aug 22 23:15:04 Dans kernel: [   63.723358]   domain 1: span 03
Aug 22 23:15:04 Dans kernel: [   63.723360]    groups: 03
Aug 22 23:15:04 Dans kernel: [   63.723362] CPU1 attaching sched-domain:
Aug 22 23:15:04 Dans kernel: [   63.723364]  domain 0: span 03
Aug 22 23:15:04 Dans kernel: [   63.723366]   groups: 02 01
Aug 22 23:15:04 Dans kernel: [   63.723369]   domain 1: span 03
Aug 22 23:15:04 Dans kernel: [   63.723370]    groups: 03
Aug 22 23:15:04 Dans kernel: [   63.723643] net_namespace: 64 bytes
Aug 22 23:15:04 Dans kernel: [   63.723696] Booting paravirtualized kernel on bare hardware
Aug 22 23:15:04 Dans kernel: [   63.724290] Time:  3:08:40  Date: 08/23/08
Aug 22 23:15:04 Dans kernel: [   63.724362] NET: Registered protocol family 16
Aug 22 23:15:04 Dans kernel: [   63.724666] EISA bus registered
Aug 22 23:15:04 Dans kernel: [   63.724716] ACPI: bus type pci registered
Aug 22 23:15:04 Dans kernel: [   63.724982] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
Aug 22 23:15:04 Dans kernel: [   63.725030] PCI: Using configuration type 1
Aug 22 23:15:04 Dans kernel: [   63.725091] Setting up standard PCI resources
Aug 22 23:15:04 Dans kernel: [   64.068262] ACPI: EC: Look up EC in DSDT
Aug 22 23:15:04 Dans kernel: [   64.075243] ACPI: Interpreter enabled
Aug 22 23:15:04 Dans kernel: [   64.075292] ACPI: (supports S0 S1 S3 S4 S5)
Aug 22 23:15:04 Dans kernel: [   64.075535] ACPI: Using PIC for interrupt routing
Aug 22 23:15:04 Dans kernel: [   64.085272] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 22 23:15:04 Dans kernel: [   64.086946] PCI: Transparent bridge - 0000:00:14.4
Aug 22 23:15:04 Dans kernel: [   64.087029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 22 23:15:04 Dans kernel: [   64.087774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Aug 22 23:15:04 Dans kernel: [   64.087878] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Aug 22 23:15:04 Dans kernel: [   64.093743] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *4 5 7 10 11 12 14 15)
Aug 22 23:15:04 Dans kernel: [   64.094298] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 22 23:15:04 Dans kernel: [   64.094852] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 22 23:15:04 Dans kernel: [   64.095484] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
Aug 22 23:15:04 Dans kernel: [   64.096038] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 22 23:15:04 Dans kernel: [   64.096592] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
Aug 22 23:15:04 Dans kernel: [   64.096939] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
Aug 22 23:15:04 Dans kernel: [   64.097500] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
Aug 22 23:15:04 Dans kernel: [   64.098086] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  A8, should be 9C [20070126]
Aug 22 23:15:04 Dans kernel: [   64.098227] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 22 23:15:04 Dans kernel: [   64.098317] pnp: PnP ACPI init
Aug 22 23:15:04 Dans kernel: [   64.098371] ACPI: bus type pnp registered
Aug 22 23:15:04 Dans kernel: [   64.104868] pnp: PnP ACPI: found 14 devices
Aug 22 23:15:04 Dans kernel: [   64.104916] ACPI: ACPI bus type pnp unregistered
Aug 22 23:15:04 Dans kernel: [   64.104965] PnPBIOS: Disabled by ACPI PNP
Aug 22 23:15:04 Dans kernel: [   64.105309] PCI: Using ACPI for IRQ routing

This is half, keeps messing up, will post other half next

---

### Post by mc4man on 2008-08-23
Run this with a disk in the drive (if possible something with a filesystem like a data cd/dvd or a dvd movie 
```
sudo lshw -C disk
```

Also post this (run from maximized terminal for readability

```
cat /etc/udev/rules.d/70-persistent-cd.rules 
```

---

### Post by Dan6 on 2008-08-23
heres the rest
Aug 22 23:15:04 Dans kernel: [   64.105357] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 22 23:15:04 Dans kernel: [   64.105417] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Aug 22 23:15:04 Dans kernel: [   64.129203] NET: Registered protocol family 8
Aug 22 23:15:04 Dans kernel: [   64.129252] NET: Registered protocol family 20
Aug 22 23:15:04 Dans kernel: [   64.129351] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 22 23:15:04 Dans kernel: [   64.129581] hpet0: 4 32-bit timers, 14318180 Hz
Aug 22 23:15:04 Dans kernel: [   64.130669] AppArmor: AppArmor Filesystem Enabled
Aug 22 23:15:04 Dans kernel: [   63.802929] Time: hpet clocksource has been installed.
Aug 22 23:15:04 Dans kernel: [   63.802993] Switched to high resolution mode on CPU 0
Aug 22 23:15:04 Dans kernel: [   64.133208] Switched to high resolution mode on CPU 1
Aug 22 23:15:04 Dans kernel: [   64.141908] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142579] system 00:07: ioport range 0x40b-0x40b has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142628] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142676] system 00:07: ioport range 0xc00-0xc01 has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142724] system 00:07: ioport range 0xc14-0xc14 has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142772] system 00:07: ioport range 0xc50-0xc51 has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142820] system 00:07: ioport range 0xc52-0xc52 has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142867] system 00:07: ioport range 0xc6c-0xc6c has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142915] system 00:07: ioport range 0xc6f-0xc6f has been reserved
Aug 22 23:15:04 Dans kernel: [   64.142963] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143011] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143058] system 00:07: ioport range 0xcd8-0xcdf has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143106] system 00:07: ioport range 0x800-0x89f has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143154] system 00:07: ioport range 0x900-0x90f has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143202] system 00:07: ioport range 0x910-0x91f has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143250] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
Aug 22 23:15:04 Dans kernel: [   64.143310] system 00:0a: ioport range 0xa00-0xa0f has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143358] system 00:0a: ioport range 0xa10-0xa1f has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143405] system 00:0a: ioport range 0xa20-0xa2f has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143453] system 00:0a: ioport range 0xa30-0xa3f has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143504] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143553] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 22 23:15:04 Dans kernel: [   64.143609] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Aug 22 23:15:04 Dans kernel: [   64.143662] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Aug 22 23:15:04 Dans kernel: [   64.144186] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Aug 22 23:15:04 Dans kernel: [   64.144234] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Aug 22 23:15:04 Dans kernel: [   64.144284] system 00:0d: iomem range 0x100000-0x7bffffff could not be reserved
Aug 22 23:15:04 Dans kernel: [   64.144339] system 00:0d: iomem range 0x0-0x0 could not be reserved
Aug 22 23:15:04 Dans kernel: [   64.174951] PCI: Bridge: 0000:00:01.0
Aug 22 23:15:04 Dans kernel: [   64.174999]   IO window: d000-dfff
Aug 22 23:15:04 Dans kernel: [   64.175046]   MEM window: fea00000-feafffff
Aug 22 23:15:04 Dans kernel: [   64.175094]   PREFETCH window: d0000000-dfffffff
Aug 22 23:15:04 Dans kernel: [   64.175143] PCI: Bridge: 0000:00:14.4
Aug 22 23:15:04 Dans kernel: [   64.175190]   IO window: e000-efff
Aug 22 23:15:04 Dans kernel: [   64.175240]   MEM window: feb00000-febfffff
Aug 22 23:15:04 Dans kernel: [   64.175289]   PREFETCH window: disabled.
Aug 22 23:15:04 Dans kernel: [   64.175364] NET: Registered protocol family 2
Aug 22 23:15:04 Dans kernel: [   64.213928] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 22 23:15:04 Dans kernel: [   64.214299] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 22 23:15:04 Dans kernel: [   64.214992] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 22 23:15:04 Dans kernel: [   64.215425] TCP: Hash tables configured (established 131072 bind 65536)
Aug 22 23:15:04 Dans kernel: [   64.215473] TCP reno registered
Aug 22 23:15:04 Dans kernel: [   64.226003] checking if image is initramfs... it is
Aug 22 23:15:04 Dans kernel: [   64.794514] Freeing initrd memory: 7312k freed
Aug 22 23:15:04 Dans kernel: [   64.795618] audit: initializing netlink socket (disabled)
Aug 22 23:15:04 Dans kernel: [   64.795684] audit(1219460915.944:1): initialized
Aug 22 23:15:04 Dans kernel: [   64.466088] highmem bounce pool size: 64 pages
Aug 22 23:15:04 Dans kernel: [   64.798581] VFS: Disk quotas dquot_6.5.1
Aug 22 23:15:04 Dans kernel: [   64.468791] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 22 23:15:04 Dans kernel: [   64.469002] io scheduler noop registered
Aug 22 23:15:04 Dans kernel: [   64.469049] io scheduler anticipatory registered
Aug 22 23:15:04 Dans kernel: [   64.469095] io scheduler deadline registered
Aug 22 23:15:04 Dans kernel: [   64.469150] io scheduler cfq registered (default)
Aug 22 23:15:04 Dans kernel: [   64.469204] PCI: MSI quirk detected. MSI deactivated.
Aug 22 23:15:04 Dans kernel: [   64.530762] Boot video device is 0000:01:05.0
Aug 22 23:15:04 Dans kernel: [   64.531129] isapnp: Scanning for PnP cards...
Aug 22 23:15:04 Dans kernel: [   65.583688] isapnp: No Plug & Play device found
Aug 22 23:15:04 Dans kernel: [   65.951086] Real Time Clock Driver v1.12ac
Aug 22 23:15:04 Dans kernel: [   65.951274] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 22 23:15:04 Dans kernel: [   65.952909] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 22 23:15:04 Dans kernel: [   65.953044] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 22 23:15:04 Dans kernel: [   65.953225] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Aug 22 23:15:04 Dans kernel: [   65.627851] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 22 23:15:04 Dans kernel: [   65.627904] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 22 23:15:04 Dans kernel: [   65.972534] mice: PS/2 mouse device common for all mice
Aug 22 23:15:04 Dans kernel: [   65.972741] EISA: Probing bus 0 at eisa.0
Aug 22 23:15:04 Dans kernel: [   65.972801] Cannot allocate resource for EISA slot 2
Aug 22 23:15:04 Dans kernel: [   65.972847] Cannot allocate resource for EISA slot 3
Aug 22 23:15:04 Dans kernel: [   65.972893] Cannot allocate resource for EISA slot 4
Aug 22 23:15:04 Dans kernel: [   65.972940] Cannot allocate resource for EISA slot 5
Aug 22 23:15:04 Dans kernel: [   65.972986] Cannot allocate resource for EISA slot 6
Aug 22 23:15:04 Dans kernel: [   65.973032] Cannot allocate resource for EISA slot 7
Aug 22 23:15:04 Dans kernel: [   65.973078] Cannot allocate resource for EISA slot 8
Aug 22 23:15:04 Dans kernel: [   65.973124] EISA: Detected 0 cards.
Aug 22 23:15:04 Dans kernel: [   65.973172] cpuidle: using governor ladder
Aug 22 23:15:04 Dans kernel: [   65.973217] cpuidle: using governor menu
Aug 22 23:15:04 Dans kernel: [   65.973362] NET: Registered protocol family 1
Aug 22 23:15:04 Dans kernel: [   65.973439] Using IPI No-Shortcut mode
Aug 22 23:15:04 Dans kernel: [   65.973515] registered taskstats version 1
Aug 22 23:15:04 Dans kernel: [   65.973668]   Magic number: 4:121:109
Aug 22 23:15:04 Dans kernel: [   65.973868] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 22 23:15:04 Dans kernel: [   65.973915] EDD information not available.
Aug 22 23:15:04 Dans kernel: [   65.974338] Freeing unused kernel memory: 368k freed
Aug 22 23:15:04 Dans kernel: [   65.661228] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 22 23:15:04 Dans kernel: [   66.174781] fuse init (API version 7.9)
Aug 22 23:15:04 Dans kernel: [   66.196886] ACPI: SSDT 7BFD4830, 02FE (r1    AMI   CPU1PM        1 INTL  2002026)
Aug 22 23:15:04 Dans kernel: [   66.197253] ACPI: duty_cycle spans bit 4
Aug 22 23:15:04 Dans kernel: [   66.197427] ACPI: SSDT 7BFD4B30, 02FE (r1    AMI   CPU2PM        1 INTL  2002026)
Aug 22 23:15:04 Dans kernel: [   66.197735] ACPI: duty_cycle spans bit 4
Aug 22 23:15:04 Dans kernel: [   66.197798] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 22 23:15:04 Dans kernel: [   66.197937] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 22 23:15:04 Dans kernel: [   66.037364] SCSI subsystem initialized
Aug 22 23:15:04 Dans kernel: [   66.106279] usbcore: registered new interface driver usbfs
Aug 22 23:15:04 Dans kernel: [   66.106369] usbcore: registered new interface driver hub
Aug 22 23:15:04 Dans kernel: [   66.115900] libata version 3.00 loaded.
Aug 22 23:15:04 Dans kernel: [   66.119990] usbcore: registered new device driver usb
Aug 22 23:15:04 Dans kernel: [   66.120786] sata_sil 0000:00:11.0: version 2.3
Aug 22 23:15:04 Dans kernel: [   66.121112] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
Aug 22 23:15:04 Dans kernel: [   66.121169] PCI: setting IRQ 5 as level-triggered
Aug 22 23:15:04 Dans kernel: [   66.121176] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 22 23:15:04 Dans kernel: [   66.131277] scsi0 : sata_sil
Aug 22 23:15:04 Dans kernel: [   66.138169] scsi1 : sata_sil
Aug 22 23:15:04 Dans kernel: [   66.138280] ata1: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff080 irq 5
Aug 22 23:15:04 Dans kernel: [   66.138335] ata2: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff0c0 irq 5
Aug 22 23:15:04 Dans kernel: [   66.156200] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 22 23:15:04 Dans kernel: [   66.737912] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 22 23:15:04 Dans kernel: [   66.737973] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 22 23:15:04 Dans kernel: [   66.450073] ata1: SATA link down (SStatus 0 SControl 310)
Aug 22 23:15:04 Dans kernel: [   66.482343] 8139too Fast Ethernet driver 0.9.28
Aug 22 23:15:04 Dans kernel: [   66.570235] FDC 0 is a post-1991 82077
Aug 22 23:15:04 Dans kernel: [   66.762960] ata2: SATA link down (SStatus 0 SControl 310)
Aug 22 23:15:04 Dans kernel: [   66.763451] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
Aug 22 23:15:04 Dans kernel: [   66.763506] PCI: setting IRQ 11 as level-triggered
Aug 22 23:15:04 Dans kernel: [   66.763512] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
Aug 22 23:15:04 Dans kernel: [   66.763784] scsi2 : sata_sil
Aug 22 23:15:04 Dans kernel: [   66.763919] scsi3 : sata_sil
Aug 22 23:15:04 Dans kernel: [   66.764018] ata3: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff880 irq 11
Aug 22 23:15:04 Dans kernel: [   66.764075] ata4: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff8c0 irq 11
Aug 22 23:15:04 Dans kernel: [   67.229830] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug 22 23:15:04 Dans kernel: [   67.568277] ata3.00: ATA-7: WDC WD2500JS-60MHB1, 10.02E02, max UDMA/100
Aug 22 23:15:04 Dans kernel: [   67.568328] ata3.00: 488397168 sectors, multi 16: LBA48 
Aug 22 23:15:04 Dans kernel: [   67.576272] ata3.00: configured for UDMA/100
Aug 22 23:15:04 Dans kernel: [   67.887620] ata4: SATA link down (SStatus 0 SControl 310)
Aug 22 23:15:04 Dans kernel: [   67.557919] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JS-60M 10.0 PQ: 0 ANSI: 5
Aug 22 23:15:04 Dans kernel: [   67.889465] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
Aug 22 23:15:04 Dans kernel: [   67.889519] PCI: setting IRQ 3 as level-triggered
Aug 22 23:15:04 Dans kernel: [   67.889525] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 23:15:04 Dans kernel: [   67.889672] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 22 23:15:04 Dans kernel: [   67.890102] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Aug 22 23:15:04 Dans kernel: [   67.890181] ohci_hcd 0000:00:13.0: irq 3, io mem 0xfe9fe000
Aug 22 23:15:04 Dans kernel: [   67.955294] usb usb1: configuration #1 chosen from 1 choice
Aug 22 23:15:04 Dans kernel: [   67.955385] hub 1-0:1.0: USB hub found
Aug 22 23:15:04 Dans kernel: [   67.955444] hub 1-0:1.0: 4 ports detected
Aug 22 23:15:04 Dans kernel: [   68.055699] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 23:15:04 Dans kernel: [   68.055849] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 22 23:15:04 Dans kernel: [   68.055941] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Aug 22 23:15:04 Dans kernel: [   68.056015] ohci_hcd 0000:00:13.1: irq 3, io mem 0xfe9fd000
Aug 22 23:15:04 Dans kernel: [   68.123194] usb usb2: configuration #1 chosen from 1 choice
Aug 22 23:15:04 Dans kernel: [   68.123282] hub 2-0:1.0: USB hub found
Aug 22 23:15:04 Dans kernel: [   68.123340] hub 2-0:1.0: 4 ports detected
Aug 22 23:15:04 Dans kernel: [   68.224601] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
Aug 22 23:15:04 Dans kernel: [   68.224855] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 4
Aug 22 23:15:04 Dans kernel: [   68.224904] PCI: setting IRQ 4 as level-triggered
Aug 22 23:15:04 Dans kernel: [   68.224909] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 22 23:15:04 Dans kernel: [   68.225044] ATIIXP: not 100% native mode: will probe irqs later
Aug 22 23:15:04 Dans kernel: [   68.225100]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:pio
Aug 22 23:15:04 Dans kernel: [   68.225238]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Aug 22 23:15:04 Dans kernel: [   68.225373] Probing IDE interface ide0...
Aug 22 23:15:04 Dans kernel: [   68.033517] usb 1-4: new full speed USB device using ohci_hcd and address 2
Aug 22 23:15:04 Dans kernel: [   68.240656] usb 1-4: configuration #1 chosen from 1 choice
Aug 22 23:15:04 Dans kernel: [   68.807307] Probing IDE interface ide1...
Aug 22 23:15:04 Dans kernel: [   68.545343] usb 2-4: new full speed USB device using ohci_hcd and address 2
Aug 22 23:15:04 Dans kernel: [   68.754683] usb 2-4: configuration #1 chosen from 1 choice
Aug 22 23:15:04 Dans kernel: [   69.615458] hdd: , ATAPI TAPE drive
Aug 22 23:15:04 Dans kernel: [   70.400184] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
Aug 22 23:15:04 Dans kernel: [   70.400356] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 22 23:15:04 Dans kernel: [   70.400581] hdc: UDMA/33 mode selected
Aug 22 23:15:04 Dans kernel: [   70.401041] hdd: tPIO > 2, assuming tPIO = 2
Aug 22 23:15:04 Dans kernel: [   70.401087] hdd: applying conservative PIO "downgrade"
Aug 22 23:15:04 Dans kernel: [   70.401134] hdd: host max PIO4 wanted PIO255(auto-tune) selected PIO1
Aug 22 23:15:04 Dans kernel: [   70.401458] hdd: tPIO > 2, assuming tPIO = 2
Aug 22 23:15:04 Dans kernel: [   70.401504] hdd: applying conservative PIO "downgrade"
Aug 22 23:15:04 Dans kernel: [   70.401551] hdd: host max PIO4 wanted PIO255(auto-tune) selected PIO1
Aug 22 23:15:04 Dans kernel: [   70.402335] ide1 at 0x170-0x177,0x376 on irq 15
Aug 22 23:15:04 Dans kernel: [   70.075894] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 23:15:04 Dans kernel: [   70.076052] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug 22 23:15:04 Dans kernel: [   70.076139] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Aug 22 23:15:04 Dans kernel: [   70.076263] ehci_hcd 0000:00:13.2: irq 3, io mem 0xfe9fc000
Aug 22 23:15:04 Dans kernel: [   70.076413] usb 1-4: USB disconnect, address 2
Aug 22 23:15:04 Dans kernel: [   70.084813] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 22 23:15:04 Dans kernel: [   70.084996] usb usb3: configuration #1 chosen from 1 choice
Aug 22 23:15:04 Dans kernel: [   70.085080] hub 3-0:1.0: USB hub found
Aug 22 23:15:04 Dans kernel: [   70.085134] hub 3-0:1.0: 8 ports detected
Aug 22 23:15:04 Dans kernel: [   70.519153] ACPI: PCI Interrupt Link [LNKE] BIOS reported IRQ 15, using IRQ 10
Aug 22 23:15:04 Dans kernel: [   70.519215] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
Aug 22 23:15:04 Dans kernel: [   70.519269] PCI: setting IRQ 10 as level-triggered
Aug 22 23:15:04 Dans kernel: [   70.519276] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
Aug 22 23:15:04 Dans kernel: [   70.520658] eth0: RealTek RTL8139 at 0xe400, 00:14:2a:b6:ae:32, IRQ 10
Aug 22 23:15:04 Dans kernel: [   70.520706] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Aug 22 23:15:04 Dans kernel: [   70.194440] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 22 23:15:04 Dans kernel: [   70.540933] usb 2-4: USB disconnect, address 2
Aug 22 23:15:04 Dans kernel: [   70.351823] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 22 23:15:04 Dans kernel: [   70.698751] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Aug 22 23:15:04 Dans kernel: [   70.402346] Driver 'sd' needs updating - please use bus_type methods
Aug 22 23:15:04 Dans kernel: [   70.402558] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 22 23:15:04 Dans kernel: [   70.402630] sd 2:0:0:0: [sda] Write Protect is off
Aug 22 23:15:04 Dans kernel: [   70.402685] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 23:15:04 Dans kernel: [   70.402725] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 23:15:04 Dans kernel: [   70.402868] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 22 23:15:04 Dans kernel: [   70.402942] sd 2:0:0:0: [sda] Write Protect is off
Aug 22 23:15:04 Dans kernel: [   70.402998] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 23:15:04 Dans kernel: [   70.403026] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 23:15:04 Dans kernel: [   70.403092]  sda: sda1 sda2 < sda5 >
Aug 22 23:15:04 Dans kernel: [   70.447741] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 22 23:15:04 Dans kernel: [   70.787643] sd 2:0:0:0: Attached scsi generic sg0 type 0
Aug 22 23:15:04 Dans kernel: [   70.911578] usb 3-7: new high speed USB device using ehci_hcd and address 2
Aug 22 23:15:04 Dans kernel: [   70.713657] usb 3-7: configuration #1 chosen from 1 choice
Aug 22 23:15:04 Dans kernel: [   71.282513] usbcore: registered new interface driver libusual
Aug 22 23:15:04 Dans kernel: [   71.412367] usb 2-4: new full speed USB device using ohci_hcd and address 3
Aug 22 23:15:04 Dans kernel: [   71.621706] usb 2-4: configuration #1 chosen from 1 choice
Aug 22 23:15:04 Dans kernel: [   71.632863] Initializing USB Mass Storage driver...
Aug 22 23:15:04 Dans kernel: [   71.633025] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 22 23:15:04 Dans kernel: [   71.633187] usbcore: registered new interface driver usb-storage
Aug 22 23:15:04 Dans kernel: [   71.633248] USB Mass Storage support registered.
Aug 22 23:15:04 Dans kernel: [   71.633449] usb-storage: device found at 3
Aug 22 23:15:04 Dans kernel: [   71.633453] usb-storage: waiting for device to settle before scanning
Aug 22 23:15:04 Dans kernel: [   71.971414] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff3db232]
Aug 22 23:15:04 Dans kernel: [   76.631177] usb-storage: device scan complete
Aug 22 23:15:04 Dans kernel: [   76.967103] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Aug 22 23:15:04 Dans kernel: [   76.973096] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Aug 22 23:15:04 Dans kernel: [   76.979102] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Aug 22 23:15:04 Dans kernel: [   76.985101] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Aug 22 23:15:04 Dans kernel: [   76.995145] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug 22 23:15:04 Dans kernel: [   76.995263] sd 4:0:0:0: Attached scsi generic sg1 type 0
Aug 22 23:15:04 Dans kernel: [   77.005143] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Aug 22 23:15:04 Dans kernel: [   77.005249] sd 4:0:0:1: Attached scsi generic sg2 type 0
Aug 22 23:15:04 Dans kernel: [   77.015143] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Aug 22 23:15:04 Dans kernel: [   77.015261] sd 4:0:0:2: Attached scsi generic sg3 type 0
Aug 22 23:15:04 Dans kernel: [   77.025147] sd 4:0:0:3: [sde] Attached SCSI removable disk
Aug 22 23:15:04 Dans kernel: [   77.025261] sd 4:0:0:3: Attached scsi generic sg4 type 0
Aug 22 23:15:04 Dans kernel: [   77.740317] ide-cd: cmd 0x5a timed out
Aug 22 23:15:04 Dans kernel: [   77.740378] hdc: lost interrupt
Aug 22 23:15:04 Dans kernel: [  137.719772] ide-cd: cmd 0x5a timed out
Aug 22 23:15:04 Dans kernel: [  137.719824] hdc: lost interrupt
Aug 22 23:15:04 Dans kernel: [  137.719900] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Aug 22 23:15:04 Dans kernel: [  137.720170] Uniform CD-ROM driver Revision: 3.20
Aug 22 23:15:04 Dans kernel: [  197.699316] hdc: lost interrupt
Aug 22 23:15:04 Dans kernel: [  250.365602] Attempting manual resume
Aug 22 23:15:04 Dans kernel: [  250.365651] swsusp: Resume From Partition 8:5
Aug 22 23:15:04 Dans kernel: [  250.365653] PM: Checking swsusp image.
Aug 22 23:15:04 Dans kernel: [  250.365873] PM: Resume from disk failed.
Aug 22 23:15:04 Dans kernel: [  250.729729] kjournald starting.  Commit interval 5 seconds
Aug 22 23:15:04 Dans kernel: [  250.399808] EXT3-fs: mounted filesystem with ordered data mode.
Aug 22 23:15:04 Dans kernel: [  261.838454] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 22 23:15:04 Dans kernel: [  261.973328] hdc: lost interrupt
Aug 22 23:15:04 Dans kernel: [  262.222374] parport_pc 00:06: reported by Plug and Play ACPI
Aug 22 23:15:04 Dans kernel: [  262.222570] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Aug 22 23:15:04 Dans kernel: [  262.259440] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 22 23:15:04 Dans kernel: [  262.298334] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 22 23:15:04 Dans kernel: [  262.719124] Linux agpgart interface v0.102
Aug 22 23:15:04 Dans kernel: [  262.783147] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug 22 23:15:04 Dans kernel: [  263.213214] input: Power Button (FF) as /devices/virtual/input/input3
Aug 22 23:15:04 Dans kernel: [  263.264943] ACPI: Power Button (FF) [PWRF]
Aug 22 23:15:04 Dans kernel: [  263.265131] input: Power Button (CM) as /devices/virtual/input/input4
Aug 22 23:15:04 Dans kernel: [  263.308959] ACPI: Power Button (CM) [PWRB]
Aug 22 23:15:04 Dans kernel: [  264.357241] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:15:04 Dans kernel: [  264.470254] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 22 23:15:04 Dans kernel: [  265.276309] ieee80211_crypt: registered algorithm 'NULL'
Aug 22 23:15:04 Dans kernel: [  265.349897] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 22 23:15:04 Dans kernel: [  265.374940] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Aug 22 23:15:04 Dans kernel: [  265.085822] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 22 23:15:04 Dans kernel: [  265.085896] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 22 23:15:04 Dans kernel: [  265.115780] sysfs: duplicate filename 'pcspkr' can not be created
Aug 22 23:15:04 Dans kernel: [  265.115852] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
Aug 22 23:15:04 Dans kernel: [  265.115915] Pid: 3199, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 22 23:15:04 Dans kernel: [  265.115986]  [sysfs_add_one+0x9f/0xe0] sysfs_add_one+0x9f/0xe0
Aug 22 23:15:04 Dans kernel: [  265.116099]  [create_dir+0x48/0x90] create_dir+0x48/0x90
Aug 22 23:15:04 Dans kernel: [  265.116208]  [sysfs_create_dir+0x29/0x50] sysfs_create_dir+0x29/0x50
Aug 22 23:15:04 Dans kernel: [  265.116305]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
Aug 22 23:15:04 Dans kernel: [  265.116409]  [kobject_add+0x93/0x1b0] kobject_add+0x93/0x1b0
Aug 22 23:15:04 Dans kernel: [  265.116528]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 22 23:15:04 Dans kernel: [  265.116632]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 22 23:15:04 Dans kernel: [  265.116749]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 22 23:15:04 Dans kernel: [  265.116923]  [<c013f260>] param_get_int+0x0/0x20
Aug 22 23:15:04 Dans kernel: [  265.117040]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 22 23:15:04 Dans kernel: [  265.117168]  =======================
Aug 22 23:15:04 Dans kernel: [  265.117246] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
Aug 22 23:15:04 Dans kernel: [  265.117319] Pid: 3199, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 22 23:15:04 Dans kernel: [  265.117377]  [kobject_add+0x113/0x1b0] kobject_add+0x113/0x1b0
Aug 22 23:15:04 Dans kernel: [  265.117485]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 22 23:15:04 Dans kernel: [  265.117589]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 22 23:15:04 Dans kernel: [  265.117713]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 22 23:15:04 Dans kernel: [  265.117866]  [<c013f260>] param_get_int+0x0/0x20
Aug 22 23:15:04 Dans kernel: [  265.117974]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 22 23:15:04 Dans kernel: [  265.118088]  =======================
Aug 22 23:15:04 Dans kernel: [  265.293176] usb 3-7: reset high speed USB device using ehci_hcd and address 2
Aug 22 23:15:04 Dans kernel: [  265.426403] zd1211rw 3-7:1.0: eth1
Aug 22 23:15:04 Dans kernel: [  265.426479] usbcore: registered new interface driver zd1211rw
Aug 22 23:15:04 Dans kernel: [  265.527001] zd1211rw 3-7:1.0: firmware version 4725
Aug 22 23:15:04 Dans kernel: [  265.567005] zd1211rw 3-7:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
Aug 22 23:15:04 Dans kernel: [  266.150417] NET: Registered protocol family 17
Aug 22 23:15:04 Dans kernel: [  265.897586] SoftMAC: Open Authentication completed with 00:18:d1:28:4f:05
Aug 22 23:15:04 Dans kernel: [  294.551168] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:15:04 Dans kernel: [  297.550158] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:15:04 Dans kernel: [  297.550162] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:15:04 Dans kernel: [  297.550167] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 23:15:04 Dans kernel: [  297.550172] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 23:15:04 Dans kernel: [  297.550176] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 23:15:04 Dans kernel: [  297.550180] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 23:15:04 Dans kernel: [  297.550259] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:15:04 Dans kernel: [  441.009640] lp0: using parport0 (interrupt-driven).
Aug 22 23:15:04 Dans kernel: [  441.199601] EXT3 FS on sda1, internal journal
Aug 22 23:15:04 Dans kernel: [  442.106986] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 22 23:15:04 Dans kernel: [  442.688812] NET: Registered protocol family 10
Aug 22 23:15:04 Dans kernel: [  442.689280] lo: Disabled Privacy Extensions
Aug 22 23:15:04 Dans kernel: [  447.438487] No dock devices found.
Aug 22 23:15:04 Dans ntpdate[8036]: adjust time server 91.189.94.4 offset 0.453595 sec
Aug 22 23:15:04 Dans NetworkManager: <info>  starting... 
Aug 22 23:15:04 Dans avahi-daemon[8539]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 22 23:15:04 Dans avahi-daemon[8539]: Successfully dropped root privileges.
Aug 22 23:15:04 Dans avahi-daemon[8539]: avahi-daemon 0.6.22 starting up.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Successfully called chroot().
Aug 22 23:15:04 Dans avahi-daemon[8539]: Successfully dropped remaining capabilities.
Aug 22 23:15:04 Dans avahi-daemon[8539]: No service file found in /etc/avahi/services.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 22 23:15:04 Dans avahi-daemon[8539]: New relevant interface eth1.IPv4 for mDNS.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 22 23:15:04 Dans avahi-daemon[8539]: New relevant interface eth0.IPv4 for mDNS.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Network interface enumeration completed.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Registering new address record for fe80::217:3fff:fe34:c1de on eth1.*.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Registering new address record for 192.168.2.10 on eth1.IPv4.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Registering new address record for fe80::214:2aff:feb6:ae32 on eth0.*.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Registering new address record for 192.168.2.11 on eth0.IPv4.
Aug 22 23:15:04 Dans avahi-daemon[8539]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 22 23:15:04 Dans kernel: [  448.662840] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 22 23:15:04 Dans kernel: [  448.662848] apm: disabled - APM is not SMP safe.
Aug 22 23:15:04 Dans kernel: [  448.855675] ppdev: user-space parallel port driver
Aug 22 23:15:05 Dans kernel: [  449.015272] audit(1219461305.106:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8585 profile="/usr/sbin/cupsd" namespace="default"
Aug 22 23:15:05 Dans ntpdate[8054]: adjust time server 91.189.94.4 offset 0.453580 sec
Aug 22 23:15:05 Dans avahi-daemon[8539]: Server startup complete. Host name is Dans.local. Local service cookie is 1851543712.
Aug 22 23:15:06 Dans kernel: [  450.685130] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:15:07 Dans kernel: [  451.319165] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Aug 22 23:15:07 Dans kernel: [  451.319177] vboxdrv: Successfully done.
Aug 22 23:15:07 Dans kernel: [  451.319180] vboxdrv: Found 2 processor cores.
Aug 22 23:15:07 Dans kernel: [  451.319206] vboxdrv: fAsync=1 u64DiffCores=1055776040.
Aug 22 23:15:07 Dans kernel: [  451.319920] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Aug 22 23:15:07 Dans kernel: [  451.319927] vboxdrv: Successfully loaded version 1.6.4 (interface 0x00080000).
Aug 22 23:15:07 Dans dhcdbd: Started up.
Aug 22 23:15:08 Dans NetworkManager: <debug> [1219461308.424133] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_USB_MS_Reader_2004888_0_3'). 
Aug 22 23:15:08 Dans anacron[8938]: Anacron 2.3 started on 2008-08-22
Aug 22 23:15:08 Dans anacron[8938]: Normal exit (0 jobs run)
Aug 22 23:15:08 Dans /usr/sbin/cron[8972]: (CRON) INFO (pidfile fd = 3)
Aug 22 23:15:08 Dans /usr/sbin/cron[8975]: (CRON) STARTUP (fork ok)
Aug 22 23:15:08 Dans /usr/sbin/cron[8975]: (CRON) INFO (Running @reboot jobs)
Aug 22 23:15:08 Dans kernel: [  452.815336] eth1: no IPv6 routers present
Aug 22 23:15:09 Dans kernel: [  453.434816] eth0: no IPv6 routers present
Aug 22 23:15:09 Dans kernel: [  453.678632] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:15:09 Dans kernel: [  453.678638] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:15:09 Dans kernel: [  453.678643] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 23:15:09 Dans kernel: [  453.678648] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 23:15:09 Dans kernel: [  453.678652] eth0:  Tx descriptor 2 is 0008a05a.
Aug 22 23:15:09 Dans kernel: [  453.678656] eth0:  Tx descriptor 3 is 0008a04e.
Aug 22 23:15:09 Dans kernel: [  453.678710] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:15:15 Dans kernel: [  458.962890] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 22 23:15:18 Dans kernel: [  462.671041] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:15:21 Dans kernel: [  465.668536] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:15:21 Dans kernel: [  465.668543] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:15:21 Dans kernel: [  465.668548] eth0:  Tx descriptor 0 is 0008a046. (queue head)
Aug 22 23:15:21 Dans kernel: [  465.668552] eth0:  Tx descriptor 1 is 0008a046.
Aug 22 23:15:21 Dans kernel: [  465.668556] eth0:  Tx descriptor 2 is 0008a03c.
Aug 22 23:15:21 Dans kernel: [  465.668560] eth0:  Tx descriptor 3 is 0008a10e.
Aug 22 23:15:21 Dans kernel: [  465.668614] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:15:30 Dans kernel: [  473.957548] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:586: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x306f000a
Aug 22 23:15:30 Dans kernel: [  474.660952] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:15:31 Dans kernel: [  474.960709] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x306f000a
Aug 22 23:15:33 Dans kernel: [  477.658452] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:15:33 Dans kernel: [  477.658460] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:15:33 Dans kernel: [  477.658468] eth0:  Tx descriptor 0 is 0008a10e. (queue head)
Aug 22 23:15:33 Dans kernel: [  477.658474] eth0:  Tx descriptor 1 is 0008a10e.
Aug 22 23:15:33 Dans kernel: [  477.658479] eth0:  Tx descriptor 2 is 0008a0fc.
Aug 22 23:15:33 Dans kernel: [  477.658485] eth0:  Tx descriptor 3 is 0008a092.
Aug 22 23:15:33 Dans kernel: [  477.658542] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:15:36 Dans NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 22 23:15:36 Dans NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 22 23:15:36 Dans NetworkManager: <info>  User request to disable wireless. 
Aug 22 23:15:42 Dans kernel: [  486.650866] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:15:45 Dans kernel: [  489.648361] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:15:45 Dans kernel: [  489.648368] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:15:45 Dans kernel: [  489.648373] eth0:  Tx descriptor 0 is 0008a092. (queue head)
Aug 22 23:15:45 Dans kernel: [  489.648378] eth0:  Tx descriptor 1 is 0008a05a.
Aug 22 23:15:45 Dans kernel: [  489.648382] eth0:  Tx descriptor 2 is 0008a092.
Aug 22 23:15:45 Dans kernel: [  489.648386] eth0:  Tx descriptor 3 is 0008a0eb.
Aug 22 23:15:45 Dans kernel: [  489.648440] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:15:54 Dans kernel: [  498.640795] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:15:57 Dans kernel: [  501.638284] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:15:57 Dans kernel: [  501.638291] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:15:57 Dans kernel: [  501.638296] eth0:  Tx descriptor 0 is 0008a0d0. (queue head)
Aug 22 23:15:57 Dans kernel: [  501.638301] eth0:  Tx descriptor 1 is 0008a0eb.
Aug 22 23:15:57 Dans kernel: [  501.638305] eth0:  Tx descriptor 2 is 0008a046.
Aug 22 23:15:57 Dans kernel: [  501.638309] eth0:  Tx descriptor 3 is 0008a0fc.
Aug 22 23:15:57 Dans kernel: [  501.638363] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:16:06 Dans kernel: [  510.630688] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:16:09 Dans kernel: [  513.628212] eth0: Transmit timeout, status 0d 0004 c07f media 10.
Aug 22 23:16:09 Dans kernel: [  513.628219] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:16:09 Dans kernel: [  513.628224] eth0:  Tx descriptor 0 is 0008a0eb. (queue head)
Aug 22 23:16:09 Dans kernel: [  513.628228] eth0:  Tx descriptor 1 is 0008a03c.
Aug 22 23:16:09 Dans kernel: [  513.628232] eth0:  Tx descriptor 2 is 0008a052.
Aug 22 23:16:09 Dans kernel: [  513.628236] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 23:16:09 Dans kernel: [  513.628292] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:16:18 Dans kernel: [  522.620620] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:16:21 Dans kernel: [  525.618103] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:16:21 Dans kernel: [  525.618109] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:16:21 Dans kernel: [  525.618114] eth0:  Tx descriptor 0 is 0008a052. (queue head)
Aug 22 23:16:21 Dans kernel: [  525.618119] eth0:  Tx descriptor 1 is 0008a052.
Aug 22 23:16:21 Dans kernel: [  525.618123] eth0:  Tx descriptor 2 is 0008a052.
Aug 22 23:16:21 Dans kernel: [  525.618127] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 23:16:21 Dans kernel: [  525.618182] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:17:01 Dans /USR/SBIN/CRON[9395]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 23:17:16 Dans init: tty4 main process (8058) killed by TERM signal
Aug 22 23:17:16 Dans init: tty5 main process (8059) killed by TERM signal
Aug 22 23:17:16 Dans init: tty2 main process (8061) killed by TERM signal
Aug 22 23:17:16 Dans init: tty3 main process (8063) killed by TERM signal
Aug 22 23:17:16 Dans init: tty6 main process (8065) killed by TERM signal
Aug 22 23:17:16 Dans init: tty1 main process (9083) killed by TERM signal
Aug 22 23:17:16 Dans gdm[8914]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Aug 22 23:17:16 Dans gdm[8914]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Aug 22 23:17:18 Dans avahi-daemon[8539]: Got SIGTERM, quitting.
Aug 22 23:17:18 Dans avahi-daemon[8539]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 22 23:17:18 Dans avahi-daemon[8539]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 22 23:17:19 Dans kernel: [  583.359838] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 22 23:17:20 Dans exiting on signal 15
Aug 22 23:43:11 Dans syslogd 1.5.0#1ubuntu1: restart.
Aug 22 23:43:12 Dans kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 22 23:43:12 Dans kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 22 23:43:12 Dans kernel: Symbols match kernel version 2.6.24.
Aug 22 23:43:12 Dans kernel: Loaded 20004 symbols from 91 modules.
Aug 22 23:43:12 Dans kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 22 23:43:12 Dans kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 22 23:43:12 Dans kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 22 23:43:12 Dans kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 22 23:43:12 Dans kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 22 23:43:12 Dans kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 22 23:43:12 Dans kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Aug 22 23:43:12 Dans kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bfd0000 (usable)
Aug 22 23:43:12 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfd0000 - 000000007bfde000 (ACPI data)
Aug 22 23:43:12 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfde000 - 000000007c000000 (ACPI NVS)
Aug 22 23:43:12 Dans kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 22 23:43:12 Dans kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Aug 22 23:43:12 Dans kernel: [    0.000000] 1087MB HIGHMEM available.
Aug 22 23:43:12 Dans kernel: [    0.000000] 896MB LOWMEM available.
Aug 22 23:43:12 Dans kernel: [    0.000000] found SMP MP-table at 000ff780
Aug 22 23:43:12 Dans kernel: [    0.000000] Entering add_active_range(0, 0, 507856) 0 entries of 256 used
Aug 22 23:43:12 Dans kernel: [    0.000000] Zone PFN ranges:
Aug 22 23:43:12 Dans kernel: [    0.000000]   DMA             0 ->     4096
Aug 22 23:43:12 Dans kernel: [    0.000000]   Normal       4096 ->   229376
Aug 22 23:43:12 Dans kernel: [    0.000000]   HighMem    229376 ->   507856
Aug 22 23:43:12 Dans kernel: [    0.000000] Movable zone start PFN for each node
Aug 22 23:43:12 Dans kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 22 23:43:12 Dans kernel: [    0.000000]     0:        0 ->   507856
Aug 22 23:43:12 Dans kernel: [    0.000000] On node 0 totalpages: 507856
Aug 22 23:43:12 Dans kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 22 23:43:12 Dans kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 22 23:43:12 Dans kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 22 23:43:12 Dans kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 22 23:43:12 Dans kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 22 23:43:12 Dans kernel: [    0.000000]   HighMem zone: 2175 pages used for memmap
Aug 22 23:43:12 Dans kernel: [    0.000000]   HighMem zone: 276305 pages, LIFO batch:31
Aug 22 23:43:12 Dans kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 22 23:43:12 Dans kernel: [    0.000000] DMI present.
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8890 checksum 0
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: RSDP 000F8890, 0014 (r0 HP-CPC)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: RSDT 7BFD0000, 0038 (r1 HP-CPC OEMRSDT  11000518 MSFT       97)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: FACP 7BFD0200, 0084 (r2 HP-CPC OEMFACP  11000518 MSFT       97)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: DSDT 7BFD0440, 43B0 (r1 HP-CPC  RC410-M        0 INTL  2002026)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: FACS 7BFDE000, 0040
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: APIC 7BFD0390, 006C (r1 HP-CPC OEMAPIC  11000518 MSFT       97)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: MCFG 7BFD0400, 003C (r1 HP-CPC OEMMCFG  11000518 MSFT       97)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: OEMB 7BFDE040, 005B (r1 HP-CPC AMI_OEM  11000518 MSFT       97)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: HPET 7BFD47F0, 0038 (r1 HP-CPC OEMHPET  11000518 MSFT       97)
Aug 22 23:43:12 Dans kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 22 23:43:12 Dans kernel: [    0.000000] Processor #0 15:4 APIC version 20
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 22 23:43:12 Dans kernel: [    0.000000] Processor #1 15:4 APIC version 20
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
Aug 22 23:43:12 Dans kernel: [    0.000000] ACPI: HPET id: 0x0 base: 0xfed00000
Aug 22 23:43:12 Dans kernel: [    0.000000] Using ACPI for processor (LAPIC) configuration information
Aug 22 23:43:12 Dans kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Aug 22 23:43:12 Dans kernel: [    0.000000]     Virtual Wire compatibility mode.
Aug 22 23:43:12 Dans kernel: [    0.000000] OEM ID: ATI      Product ID: RS400        APIC at: 0xFEE00000
Aug 22 23:43:12 Dans kernel: [    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
Aug 22 23:43:12 Dans kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 22 23:43:12 Dans kernel: [    0.000000] Processors: 2
Aug 22 23:43:12 Dans kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7c000000:82e00000)
Aug 22 23:43:12 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 22 23:43:12 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
Aug 22 23:43:12 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Aug 22 23:43:12 Dans kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503889
Aug 22 23:43:12 Dans kernel: [    0.000000] Kernel command line: root=UUID=e9a7cff5-d8ae-4fb4-a348-d2db06aed623 ro single noapic
Aug 22 23:43:12 Dans kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 22 23:43:12 Dans kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 22 23:43:12 Dans kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 22 23:43:12 Dans kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 22 23:43:12 Dans kernel: [    0.000000] Initializing CPU#0
Aug 22 23:43:12 Dans kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 22 23:43:12 Dans kernel: [    0.000000] Detected 3199.391 MHz processor.
Aug 22 23:43:12 Dans kernel: [   31.049377] Console: colour VGA+ 80x25
Aug 22 23:43:12 Dans kernel: [   31.049382] console [tty0] enabled
Aug 22 23:43:12 Dans kernel: [   31.053021] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 22 23:43:12 Dans kernel: [   31.053797] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 22 23:43:12 Dans kernel: [   31.162082] Memory: 2001980k/2031424k available (2177k kernel code, 28188k reserved, 1006k data, 368k init, 1113920k highmem)
Aug 22 23:43:12 Dans kernel: [   31.162156] virtual kernel memory layout:
Aug 22 23:43:12 Dans kernel: [   31.162157]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 22 23:43:12 Dans kernel: [   31.162158]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 22 23:43:12 Dans kernel: [   31.162159]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 22 23:43:12 Dans kernel: [   31.162160]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 22 23:43:12 Dans kernel: [   31.162161]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 22 23:43:12 Dans kernel: [   31.162162]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 22 23:43:12 Dans kernel: [   31.162163]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 22 23:43:12 Dans kernel: [   31.162527] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 22 23:43:12 Dans kernel: [   31.162684] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 22 23:43:12 Dans kernel: [   31.162845] hpet clockevent registered
Aug 22 23:43:12 Dans kernel: [   32.238858] Calibrating delay using timer specific routine.. 88436.69 BogoMIPS (lpj=176873380)
Aug 22 23:43:12 Dans kernel: [   32.238979] Security Framework initialized
Aug 22 23:43:12 Dans kernel: [   32.239033] SELinux:  Disabled at boot.
Aug 22 23:43:12 Dans kernel: [   32.239099] AppArmor: AppArmor initialized
Aug 22 23:43:12 Dans kernel: [   32.239148] Failure registering capabilities with primary security module.
Aug 22 23:43:12 Dans kernel: [   32.239204] Mount-cache hash table entries: 512
Aug 22 23:43:12 Dans kernel: [   32.239418] Initializing cgroup subsys ns
Aug 22 23:43:12 Dans kernel: [   32.239469] Initializing cgroup subsys cpuacct
Aug 22 23:43:12 Dans kernel: [   32.239528] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 22 23:43:12 Dans kernel: [   32.239537] monitor/mwait feature present.
Aug 22 23:43:12 Dans kernel: [   32.239582] using mwait in idle threads.
Aug 22 23:43:12 Dans kernel: [   32.239632] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 22 23:43:12 Dans kernel: [   32.239716] CPU: L2 cache: 2048K
Aug 22 23:43:12 Dans kernel: [   32.239762] CPU: Physical Processor ID: 0
Aug 22 23:43:12 Dans kernel: [   32.239807] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 22 23:43:12 Dans kernel: [   32.239820] Compat vDSO mapped to ffffe000.
Aug 22 23:43:12 Dans kernel: [   32.239885] Checking 'hlt' instruction... OK.
Aug 22 23:43:12 Dans kernel: [   32.459036] SMP alternatives: switching to UP code
Aug 22 23:43:12 Dans kernel: [   32.461015] Early unpacking initramfs... done
Aug 22 23:43:12 Dans kernel: [   32.745903] ACPI: Core revision 20070126
Aug 22 23:43:12 Dans kernel: [   32.746007] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 22 23:43:12 Dans kernel: [   32.748010] ACPI: setting ELCR to 0200 (from 0c38)
Aug 22 23:43:12 Dans kernel: [   32.748727] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 22 23:43:12 Dans kernel: [   32.748865] SMP alternatives: switching to SMP code
Aug 22 23:43:12 Dans kernel: [   32.749742] Booting processor 1/1 eip 3000
Aug 22 23:43:12 Dans kernel: [   33.110308] Initializing CPU#1
Aug 22 23:43:12 Dans kernel: [   34.161007] Calibrating delay using timer specific routine.. 87855.90 BogoMIPS (lpj=175711807)
Aug 22 23:43:12 Dans kernel: [   34.161018] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 22 23:43:12 Dans kernel: [   34.161025] monitor/mwait feature present.
Aug 22 23:43:12 Dans kernel: [   34.161032] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 22 23:43:12 Dans kernel: [   34.161034] CPU: L2 cache: 2048K
Aug 22 23:43:12 Dans kernel: [   34.161037] CPU: Physical Processor ID: 0
Aug 22 23:43:12 Dans kernel: [   34.161039] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 22 23:43:12 Dans kernel: [   33.831829] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 22 23:43:12 Dans kernel: [   33.832275] Total of 2 processors activated (176292.59 BogoMIPS).
Aug 22 23:43:12 Dans kernel: [   35.313768] APIC calibration not consistent with PM Timer: 1373ms instead of 100ms
Aug 22 23:43:12 Dans kernel: [   35.313825] APIC delta adjusted to PM-Timer: 1249643 (17159341)
Aug 22 23:43:12 Dans kernel: [   35.314023] checking TSC synchronization [CPU#0 -> CPU#1]:
Aug 22 23:43:12 Dans kernel: [   35.334108] Measured 1055414416 cycles TSC warp between CPUs, turning off TSC clock.
Aug 22 23:43:12 Dans kernel: [   35.334166] Marking TSC unstable due to: check_tsc_sync_source failed.
Aug 22 23:43:12 Dans kernel: [   35.334232] Brought up 2 CPUs
Aug 22 23:43:12 Dans kernel: [   35.334296] CPU0 attaching sched-domain:
Aug 22 23:43:12 Dans kernel: [   35.334300]  domain 0: span 03
Aug 22 23:43:12 Dans kernel: [   35.334302]   groups: 01 02
Aug 22 23:43:12 Dans kernel: [   35.334306]   domain 1: span 03
Aug 22 23:43:12 Dans kernel: [   35.334307]    groups: 03
Aug 22 23:43:12 Dans kernel: [   35.334310] CPU1 attaching sched-domain:
Aug 22 23:43:12 Dans kernel: [   35.334312]  domain 0: span 03
Aug 22 23:43:12 Dans kernel: [   35.334313]   groups: 02 01
Aug 22 23:43:12 Dans kernel: [   35.334316]   domain 1: span 03
Aug 22 23:43:12 Dans kernel: [   35.334318]    groups: 03
Aug 22 23:43:12 Dans kernel: [   35.334595] net_namespace: 64 bytes
Aug 22 23:43:12 Dans kernel: [   35.334648] Booting paravirtualized kernel on bare hardware
Aug 22 23:43:12 Dans kernel: [   35.335282] Time:  3:36:16  Date: 08/23/08
Aug 22 23:43:12 Dans kernel: [   35.335353] NET: Registered protocol family 16
Aug 22 23:43:12 Dans kernel: [   35.335658] EISA bus registered
Aug 22 23:43:12 Dans kernel: [   35.335708] ACPI: bus type pci registered
Aug 22 23:43:12 Dans kernel: [   35.335976] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
Aug 22 23:43:12 Dans kernel: [   35.336024] PCI: Using configuration type 1
Aug 22 23:43:12 Dans kernel: [   35.336085] Setting up standard PCI resources
Aug 22 23:43:12 Dans kernel: [   35.348599] ACPI: EC: Look up EC in DSDT
Aug 22 23:43:12 Dans kernel: [   35.354815] ACPI: Interpreter enabled
Aug 22 23:43:12 Dans kernel: [   35.354864] ACPI: (supports S0 S1 S3 S4 S5)
Aug 22 23:43:12 Dans kernel: [   35.355106] ACPI: Using PIC for interrupt routing
Aug 22 23:43:12 Dans kernel: [   35.364867] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 22 23:43:12 Dans kernel: [   35.366548] PCI: Transparent bridge - 0000:00:14.4
Aug 22 23:43:12 Dans kernel: [   35.366631] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 22 23:43:12 Dans kernel: [   35.366763] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Aug 22 23:43:12 Dans kernel: [   35.366866] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Aug 22 23:43:12 Dans kernel: [   35.703181] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *4 5 7 10 11 12 14 15)
Aug 22 23:43:12 Dans kernel: [   35.703743] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 22 23:43:12 Dans kernel: [   35.704335] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 22 23:43:12 Dans kernel: [   35.704967] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
Aug 22 23:43:12 Dans kernel: [   35.705520] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 22 23:43:12 Dans kernel: [   35.706072] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
Aug 22 23:43:12 Dans kernel: [   35.706405] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
Aug 22 23:43:12 Dans kernel: [   35.706956] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
Aug 22 23:43:12 Dans kernel: [   35.707556] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  A8, should be 9C [20070126]
Aug 22 23:43:12 Dans kernel: [   35.707699] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 22 23:43:12 Dans kernel: [   35.707787] pnp: PnP ACPI init
Aug 22 23:43:12 Dans kernel: [   35.707841] ACPI: bus type pnp registered
Aug 22 23:43:12 Dans kernel: [   35.715070] pnp: PnP ACPI: found 14 devices
Aug 22 23:43:12 Dans kernel: [   35.715118] ACPI: ACPI bus type pnp unregistered
Aug 22 23:43:12 Dans kernel: [   35.715167] PnPBIOS: Disabled by ACPI PNP
Aug 22 23:43:12 Dans kernel: [   35.385697] PCI: Using ACPI for IRQ routing
Aug 22 23:43:12 Dans kernel: [   35.385749] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 22 23:43:12 Dans kernel: [   35.385809] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Aug 22 23:43:12 Dans kernel: [   35.425874] NET: Registered protocol family 8
Aug 22 23:43:12 Dans kernel: [   35.425923] NET: Registered protocol family 20
Aug 22 23:43:12 Dans kernel: [   35.426018] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 22 23:43:12 Dans kernel: [   35.426249] hpet0: 4 32-bit timers, 14318180 Hz
Aug 22 23:43:12 Dans kernel: [   35.427339] AppArmor: AppArmor Filesystem Enabled
Aug 22 23:43:12 Dans kernel: [   35.429871] Time: hpet clocksource has been installed.
Aug 22 23:43:12 Dans kernel: [   35.429933] Switched to high resolution mode on CPU 0
Aug 22 23:43:12 Dans kernel: [   35.760038] Switched to high resolution mode on CPU 1
Aug 22 23:43:12 Dans kernel: [   35.445922] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Aug 22 23:43:12 Dans kernel: [   35.445977] system 00:07: ioport range 0x40b-0x40b has been reserved
Aug 22 23:43:12 Dans kernel: [   35.446025] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
Aug 22 23:43:12 Dans kernel: [   35.446073] system 00:07: ioport range 0xc00-0xc01 has been reserved
Aug 22 23:43:12 Dans kernel: [   35.446121] system 00:07: ioport range 0xc14-0xc14 has been reserved
Aug 22 23:43:12 Dans kernel: [   35.446169] system 00:07: ioport range 0xc50-0xc51 has been reserved
Aug 22 23:43:12 Dans kernel: [   35.446217] system 00:07: ioport range 0xc52-0xc52 has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447016] system 00:07: ioport range 0xc6c-0xc6c has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447064] system 00:07: ioport range 0xc6f-0xc6f has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447112] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447160] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447208] system 00:07: ioport range 0xcd8-0xcdf has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447255] system 00:07: ioport range 0x800-0x89f has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447303] system 00:07: ioport range 0x900-0x90f has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447351] system 00:07: ioport range 0x910-0x91f has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447400] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
Aug 22 23:43:12 Dans kernel: [   35.447459] system 00:0a: ioport range 0xa00-0xa0f has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447507] system 00:0a: ioport range 0xa10-0xa1f has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447555] system 00:0a: ioport range 0xa20-0xa2f has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447603] system 00:0a: ioport range 0xa30-0xa3f has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447654] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447703] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 22 23:43:12 Dans kernel: [   35.447760] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Aug 22 23:43:12 Dans kernel: [   35.447813] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Aug 22 23:43:12 Dans kernel: [   35.448336] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Aug 22 23:43:12 Dans kernel: [   35.448385] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Aug 22 23:43:12 Dans kernel: [   35.448434] system 00:0d: iomem range 0x100000-0x7bffffff could not be reserved
Aug 22 23:43:12 Dans kernel: [   35.448487] system 00:0d: iomem range 0x0-0x0 could not be reserved
Aug 22 23:43:12 Dans kernel: [   35.479102] PCI: Bridge: 0000:00:01.0
Aug 22 23:43:12 Dans kernel: [   35.479150]   IO window: d000-dfff
Aug 22 23:43:12 Dans kernel: [   35.479197]   MEM window: fea00000-feafffff
Aug 22 23:43:12 Dans kernel: [   35.479244]   PREFETCH window: d0000000-dfffffff
Aug 22 23:43:12 Dans kernel: [   35.479292] PCI: Bridge: 0000:00:14.4
Aug 22 23:43:12 Dans kernel: [   35.479340]   IO window: e000-efff
Aug 22 23:43:12 Dans kernel: [   35.479390]   MEM window: feb00000-febfffff
Aug 22 23:43:12 Dans kernel: [   35.479439]   PREFETCH window: disabled.
Aug 22 23:43:12 Dans kernel: [   35.479515] NET: Registered protocol family 2
Aug 22 23:43:12 Dans kernel: [   35.522435] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 22 23:43:12 Dans kernel: [   35.522826] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 22 23:43:12 Dans kernel: [   35.523518] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 22 23:43:12 Dans kernel: [   35.523976] TCP: Hash tables configured (established 131072 bind 65536)
Aug 22 23:43:12 Dans kernel: [   35.524025] TCP reno registered
Aug 22 23:43:12 Dans kernel: [   35.534018] checking if image is initramfs... it is
Aug 22 23:43:12 Dans kernel: [   36.103090] Freeing initrd memory: 7312k freed
Aug 22 23:43:12 Dans kernel: [   36.434015] audit: initializing netlink socket (disabled)
Aug 22 23:43:12 Dans kernel: [   36.434088] audit(1219462572.973:1): initialized
Aug 22 23:43:12 Dans kernel: [   36.434418] highmem bounce pool size: 64 pages
Aug 22 23:43:12 Dans kernel: [   36.436968] VFS: Disk quotas dquot_6.5.1
Aug 22 23:43:12 Dans kernel: [   36.437105] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 22 23:43:12 Dans kernel: [   36.437312] io scheduler noop registered
Aug 22 23:43:12 Dans kernel: [   36.437359] io scheduler anticipatory registered
Aug 22 23:43:12 Dans kernel: [   36.437405] io scheduler deadline registered
Aug 22 23:43:12 Dans kernel: [   36.437461] io scheduler cfq registered (default)
Aug 22 23:43:12 Dans kernel: [   36.437514] PCI: MSI quirk detected. MSI deactivated.
Aug 22 23:43:12 Dans kernel: [   36.503514] Boot video device is 0000:01:05.0
Aug 22 23:43:12 Dans kernel: [   36.503887] isapnp: Scanning for PnP cards...
Aug 22 23:43:12 Dans kernel: [   37.525360] isapnp: No Plug & Play device found
Aug 22 23:43:12 Dans kernel: [   37.562583] Real Time Clock Driver v1.12ac
Aug 22 23:43:12 Dans kernel: [   37.562772] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 22 23:43:12 Dans kernel: [   37.234658] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 22 23:43:12 Dans kernel: [   37.234797] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 22 23:43:12 Dans kernel: [   37.234979] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Aug 22 23:43:12 Dans kernel: [   37.239614] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 22 23:43:12 Dans kernel: [   37.239667] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 22 23:43:12 Dans kernel: [   37.257394] mice: PS/2 mouse device common for all mice
Aug 22 23:43:12 Dans kernel: [   37.257600] EISA: Probing bus 0 at eisa.0
Aug 22 23:43:12 Dans kernel: [   37.257659] Cannot allocate resource for EISA slot 2
Aug 22 23:43:12 Dans kernel: [   37.257705] Cannot allocate resource for EISA slot 3
Aug 22 23:43:12 Dans kernel: [   37.257751] Cannot allocate resource for EISA slot 4
Aug 22 23:43:12 Dans kernel: [   37.257798] Cannot allocate resource for EISA slot 5
Aug 22 23:43:12 Dans kernel: [   37.257844] Cannot allocate resource for EISA slot 6
Aug 22 23:43:12 Dans kernel: [   37.257890] Cannot allocate resource for EISA slot 7
Aug 22 23:43:12 Dans kernel: [   37.257936] Cannot allocate resource for EISA slot 8
Aug 22 23:43:12 Dans kernel: [   37.257982] EISA: Detected 0 cards.
Aug 22 23:43:12 Dans kernel: [   37.258030] cpuidle: using governor ladder
Aug 22 23:43:12 Dans kernel: [   37.258075] cpuidle: using governor menu
Aug 22 23:43:12 Dans kernel: [   37.258210] NET: Registered protocol family 1
Aug 22 23:43:12 Dans kernel: [   37.258291] Using IPI No-Shortcut mode
Aug 22 23:43:12 Dans kernel: [   37.258367] registered taskstats version 1
Aug 22 23:43:12 Dans kernel: [   37.258523]   Magic number: 4:636:614
Aug 22 23:43:12 Dans kernel: [   37.258619]   hash matches device ptye4
Aug 22 23:43:12 Dans kernel: [   37.258750]   hash matches device PNP0303:00
Aug 22 23:43:12 Dans kernel: [   37.258800] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 22 23:43:12 Dans kernel: [   37.258847] EDD information not available.
Aug 22 23:43:12 Dans kernel: [   37.259292] Freeing unused kernel memory: 368k freed
Aug 22 23:43:12 Dans kernel: [   37.605804] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 22 23:43:12 Dans kernel: [   37.789946] fuse init (API version 7.9)
Aug 22 23:43:12 Dans kernel: [   37.811881] ACPI: SSDT 7BFD4830, 02FE (r1    AMI   CPU1PM        1 INTL  2002026)
Aug 22 23:43:12 Dans kernel: [   37.812304] ACPI: duty_cycle spans bit 4
Aug 22 23:43:12 Dans kernel: [   37.812418] ACPI: SSDT 7BFD4B30, 02FE (r1    AMI   CPU2PM        1 INTL  2002026)
Aug 22 23:43:12 Dans kernel: [   37.812723] ACPI: duty_cycle spans bit 4
Aug 22 23:43:12 Dans kernel: [   37.812785] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 22 23:43:12 Dans kernel: [   37.812924] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 22 23:43:12 Dans kernel: [   37.650191] SCSI subsystem initialized
Aug 22 23:43:12 Dans kernel: [   37.760040] usbcore: registered new interface driver usbfs
Aug 22 23:43:12 Dans kernel: [   37.760132] usbcore: registered new interface driver hub
Aug 22 23:43:12 Dans kernel: [   37.760203] libata version 3.00 loaded.
Aug 22 23:43:12 Dans kernel: [   37.762986] usbcore: registered new device driver usb
Aug 22 23:43:12 Dans kernel: [   37.763146] sata_sil 0000:00:11.0: version 2.3
Aug 22 23:43:12 Dans kernel: [   37.763494] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
Aug 22 23:43:12 Dans kernel: [   37.763553] PCI: setting IRQ 5 as level-triggered
Aug 22 23:43:12 Dans kernel: [   37.763561] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 22 23:43:12 Dans kernel: [   37.765794] scsi0 : sata_sil
Aug 22 23:43:12 Dans kernel: [   37.765956] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 22 23:43:12 Dans kernel: [   37.765994] scsi1 : sata_sil
Aug 22 23:43:12 Dans kernel: [   37.766091] ata1: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff080 irq 5
Aug 22 23:43:12 Dans kernel: [   37.766147] ata2: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff0c0 irq 5
Aug 22 23:43:12 Dans kernel: [   37.984544] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 22 23:43:12 Dans kernel: [   37.984616] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 22 23:43:12 Dans kernel: [   38.081008] ata1: SATA link down (SStatus 0 SControl 310)
Aug 22 23:43:12 Dans kernel: [   38.161896] 8139too Fast Ethernet driver 0.9.28
Aug 22 23:43:12 Dans kernel: [   38.180900] FDC 0 is a post-1991 82077
Aug 22 23:43:12 Dans kernel: [   38.719731] ata2: SATA link down (SStatus 0 SControl 310)
Aug 22 23:43:12 Dans kernel: [   38.390410] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
Aug 22 23:43:12 Dans kernel: [   38.390470] PCI: setting IRQ 11 as level-triggered
Aug 22 23:43:12 Dans kernel: [   38.390477] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
Aug 22 23:43:12 Dans kernel: [   38.390745] scsi2 : sata_sil
Aug 22 23:43:12 Dans kernel: [   38.390882] scsi3 : sata_sil
Aug 22 23:43:12 Dans kernel: [   38.390987] ata3: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff880 irq 11
Aug 22 23:43:12 Dans kernel: [   38.391047] ata4: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff8c0 irq 11
Aug 22 23:43:12 Dans kernel: [   39.186590] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug 22 23:43:12 Dans kernel: [   38.866283] ata3.00: ATA-7: WDC WD2500JS-60MHB1, 10.02E02, max UDMA/100
Aug 22 23:43:12 Dans kernel: [   38.866335] ata3.00: 488397168 sectors, multi 16: LBA48 
Aug 22 23:43:12 Dans kernel: [   38.874281] ata3.00: configured for UDMA/100
Aug 22 23:43:12 Dans kernel: [   39.200626] ata4: SATA link down (SStatus 0 SControl 310)
Aug 22 23:43:12 Dans kernel: [   39.530675] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JS-60M 10.0 PQ: 0 ANSI: 5
Aug 22 23:43:12 Dans kernel: [   39.201329] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
Aug 22 23:43:12 Dans kernel: [   39.201383] PCI: setting IRQ 3 as level-triggered
Aug 22 23:43:12 Dans kernel: [   39.201389] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 23:43:12 Dans kernel: [   39.201543] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 22 23:43:12 Dans kernel: [   39.201975] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Aug 22 23:43:12 Dans kernel: [   39.202073] ohci_hcd 0000:00:13.0: irq 3, io mem 0xfe9fe000
Aug 22 23:43:12 Dans kernel: [   39.268688] usb usb1: configuration #1 chosen from 1 choice
Aug 22 23:43:12 Dans kernel: [   39.268783] hub 1-0:1.0: USB hub found
Aug 22 23:43:12 Dans kernel: [   39.268843] hub 1-0:1.0: 4 ports detected
Aug 22 23:43:12 Dans kernel: [   39.372686] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 23:43:12 Dans kernel: [   39.372836] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 22 23:43:12 Dans kernel: [   39.372920] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Aug 22 23:43:12 Dans kernel: [   39.372994] ohci_hcd 0000:00:13.1: irq 3, io mem 0xfe9fd000
Aug 22 23:43:12 Dans kernel: [   39.441030] usb usb2: configuration #1 chosen from 1 choice
Aug 22 23:43:12 Dans kernel: [   39.441116] hub 2-0:1.0: USB hub found
Aug 22 23:43:12 Dans kernel: [   39.441174] hub 2-0:1.0: 4 ports detected
Aug 22 23:43:12 Dans kernel: [   39.874574] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
Aug 22 23:43:12 Dans kernel: [   39.874815] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 4
Aug 22 23:43:12 Dans kernel: [   39.874864] PCI: setting IRQ 4 as level-triggered
Aug 22 23:43:12 Dans kernel: [   39.874869] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 22 23:43:12 Dans kernel: [   39.875004] ATIIXP: not 100% native mode: will probe irqs later
Aug 22 23:43:12 Dans kernel: [   39.875061]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:pio
Aug 22 23:43:12 Dans kernel: [   39.875199]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Aug 22 23:43:12 Dans kernel: [   39.875345] Probing IDE interface ide0...
Aug 22 23:43:12 Dans kernel: [   39.664461] usb 1-4: new full speed USB device using ohci_hcd and address 2
Aug 22 23:43:12 Dans kernel: [   39.871592] usb 1-4: configuration #1 chosen from 1 choice
Aug 22 23:43:12 Dans kernel: [   40.458141] Probing IDE interface ide1...
Aug 22 23:43:12 Dans kernel: [   40.176282] usb 2-4: new full speed USB device using ohci_hcd and address 2
Aug 22 23:43:12 Dans kernel: [   40.385437] usb 2-4: configuration #1 chosen from 1 choice
Aug 22 23:43:12 Dans kernel: [   41.266288] hdd: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
Aug 22 23:43:12 Dans kernel: [   42.050013] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
Aug 22 23:43:12 Dans kernel: [   42.050185] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 22 23:43:12 Dans kernel: [   42.050457] hdc: UDMA/33 mode selected
Aug 22 23:43:12 Dans kernel: [   42.050761] hdd: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 22 23:43:12 Dans kernel: [   42.051096] hdd: host side 80-wire cable detection failed, limiting max speed to UDMA33
Aug 22 23:43:12 Dans kernel: [   42.051150] hdd: UDMA/33 mode selected
Aug 22 23:43:12 Dans kernel: [   42.052498] ide1 at 0x170-0x177,0x376 on irq 15
Aug 22 23:43:12 Dans kernel: [   41.726344] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 22 23:43:12 Dans kernel: [   41.884157] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 22 23:43:12 Dans kernel: [   41.899567] ACPI: PCI Interrupt Link [LNKE] BIOS reported IRQ 15, using IRQ 10
Aug 22 23:43:12 Dans kernel: [   41.899634] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
Aug 22 23:43:12 Dans kernel: [   41.899706] PCI: setting IRQ 10 as level-triggered
Aug 22 23:43:12 Dans kernel: [   41.899713] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
Aug 22 23:43:12 Dans kernel: [   41.901278] eth0: RealTek RTL8139 at 0xe400, 00:14:2a:b6:ae:32, IRQ 10
Aug 22 23:43:12 Dans kernel: [   41.901338] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Aug 22 23:43:12 Dans kernel: [   41.901414] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 22 23:43:12 Dans kernel: [   41.901565] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug 22 23:43:12 Dans kernel: [   41.901662] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Aug 22 23:43:12 Dans kernel: [   41.901780] ehci_hcd 0000:00:13.2: irq 3, io mem 0xfe9fc000
Aug 22 23:43:12 Dans kernel: [   41.901934] usb 1-4: USB disconnect, address 2
Aug 22 23:43:12 Dans kernel: [   41.902962] usbcore: registered new interface driver libusual
Aug 22 23:43:12 Dans kernel: [   41.911695] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 22 23:43:12 Dans kernel: [   41.912388] usb usb3: configuration #1 chosen from 1 choice
Aug 22 23:43:12 Dans kernel: [   41.912473] hub 3-0:1.0: USB hub found
Aug 22 23:43:12 Dans kernel: [   41.912529] hub 3-0:1.0: 8 ports detected
Aug 22 23:43:12 Dans kernel: [   42.243278] Initializing USB Mass Storage driver...
Aug 22 23:43:12 Dans kernel: [   41.916382] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Aug 22 23:43:12 Dans kernel: [   42.357512] usb 2-4: USB disconnect, address 2
Aug 22 23:43:12 Dans kernel: [   42.043785] Driver 'sd' needs updating - please use bus_type methods
Aug 22 23:43:12 Dans kernel: [   42.045705] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 22 23:43:12 Dans kernel: [   42.045778] sd 2:0:0:0: [sda] Write Protect is off
Aug 22 23:43:12 Dans kernel: [   42.045829] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 23:43:12 Dans kernel: [   42.045860] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 23:43:12 Dans kernel: [   42.045991] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 22 23:43:12 Dans kernel: [   42.046059] sd 2:0:0:0: [sda] Write Protect is off
Aug 22 23:43:12 Dans kernel: [   42.046109] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 22 23:43:12 Dans kernel: [   42.046139] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 22 23:43:12 Dans kernel: [   42.046201]  sda: sda1 sda2 < sda5 >
Aug 22 23:43:12 Dans kernel: [   42.092207] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 22 23:43:12 Dans kernel: [   42.426982] sd 2:0:0:0: Attached scsi generic sg0 type 0
Aug 22 23:43:12 Dans kernel: [   42.725348] usb 3-7: new high speed USB device using ehci_hcd and address 2
Aug 22 23:43:12 Dans kernel: [   42.528549] usb 3-7: configuration #1 chosen from 1 choice
Aug 22 23:43:12 Dans kernel: [   43.097272] usbcore: registered new interface driver usb-storage
Aug 22 23:43:12 Dans kernel: [   43.097331] USB Mass Storage support registered.
Aug 22 23:43:12 Dans kernel: [   43.405118] usb 2-4: new full speed USB device using ohci_hcd and address 3
Aug 22 23:43:12 Dans kernel: [   43.501318] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff3db232]
Aug 22 23:43:12 Dans kernel: [   43.284610] usb 2-4: configuration #1 chosen from 1 choice
Aug 22 23:43:12 Dans kernel: [   43.286614] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 22 23:43:12 Dans kernel: [   43.286896] usb-storage: device found at 3
Aug 22 23:43:12 Dans kernel: [   43.286899] usb-storage: waiting for device to settle before scanning
Aug 22 23:43:12 Dans kernel: [   48.282102] usb-storage: device scan complete
Aug 22 23:43:12 Dans kernel: [   48.617915] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Aug 22 23:43:12 Dans kernel: [   48.623906] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Aug 22 23:43:12 Dans kernel: [   48.629915] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Aug 22 23:43:12 Dans kernel: [   48.635914] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Aug 22 23:43:12 Dans kernel: [   48.645952] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug 22 23:43:12 Dans kernel: [   48.646075] sd 4:0:0:0: Attached scsi generic sg1 type 0
Aug 22 23:43:12 Dans kernel: [   48.655950] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Aug 22 23:43:12 Dans kernel: [   48.656055] sd 4:0:0:1: Attached scsi generic sg2 type 0
Aug 22 23:43:12 Dans kernel: [   48.665948] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Aug 22 23:43:12 Dans kernel: [   48.666055] sd 4:0:0:2: Attached scsi generic sg3 type 0
Aug 22 23:43:12 Dans kernel: [   48.675961] sd 4:0:0:3: [sde] Attached SCSI removable disk
Aug 22 23:43:12 Dans kernel: [   48.676069] sd 4:0:0:3: Attached scsi generic sg4 type 0
Aug 22 23:43:12 Dans kernel: [   49.045251] ide-cd: cmd 0x5a timed out
Aug 22 23:43:12 Dans kernel: [   49.045313] hdc: lost interrupt
Aug 22 23:43:12 Dans kernel: [  109.024776] ide-cd: cmd 0x5a timed out
Aug 22 23:43:12 Dans kernel: [  109.024828] hdc: lost interrupt
Aug 22 23:43:12 Dans kernel: [  109.024904] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Aug 22 23:43:12 Dans kernel: [  109.025174] Uniform CD-ROM driver Revision: 3.20
Aug 22 23:43:12 Dans kernel: [  169.004304] hdc: lost interrupt
Aug 22 23:43:12 Dans kernel: [  221.998373] Attempting manual resume
Aug 22 23:43:12 Dans kernel: [  221.998421] swsusp: Resume From Partition 8:5
Aug 22 23:43:12 Dans kernel: [  221.998423] PM: Checking swsusp image.
Aug 22 23:43:12 Dans kernel: [  221.998655] PM: Resume from disk failed.
Aug 22 23:43:12 Dans kernel: [  222.364128] kjournald starting.  Commit interval 5 seconds
Aug 22 23:43:12 Dans kernel: [  222.034319] EXT3-fs: mounted filesystem with ordered data mode.
Aug 22 23:43:12 Dans kernel: [  228.983833] ide-cd: cmd 0x3 timed out
Aug 22 23:43:12 Dans kernel: [  228.983899] hdc: lost interrupt
Aug 22 23:43:12 Dans kernel: [  229.294120] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 22 23:43:12 Dans kernel: [  229.553287] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 22 23:43:12 Dans kernel: [  229.600806] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 22 23:43:12 Dans kernel: [  230.046471] Linux agpgart interface v0.102
Aug 22 23:43:12 Dans kernel: [  230.122506] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug 22 23:43:12 Dans kernel: [  230.303783] parport_pc 00:06: reported by Plug and Play ACPI
Aug 22 23:43:12 Dans kernel: [  230.303953] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Aug 22 23:43:12 Dans kernel: [  230.469144] input: Power Button (FF) as /devices/virtual/input/input3
Aug 22 23:43:12 Dans kernel: [  230.515432] ACPI: Power Button (FF) [PWRF]
Aug 22 23:43:12 Dans kernel: [  230.515627] input: Power Button (CM) as /devices/virtual/input/input4
Aug 22 23:43:12 Dans kernel: [  230.543370] ACPI: Power Button (CM) [PWRB]
Aug 22 23:43:12 Dans kernel: [  231.678310] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:43:12 Dans kernel: [  231.718532] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 22 23:43:12 Dans kernel: [  232.508991] ieee80211_crypt: registered algorithm 'NULL'
Aug 22 23:43:12 Dans kernel: [  232.513071] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 22 23:43:12 Dans kernel: [  232.513132] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 22 23:43:12 Dans kernel: [  232.467742] sysfs: duplicate filename 'pcspkr' can not be created
Aug 22 23:43:12 Dans kernel: [  232.467810] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
Aug 22 23:43:12 Dans kernel: [  232.467881] Pid: 3206, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 22 23:43:12 Dans kernel: [  232.467951]  [sysfs_add_one+0x9f/0xe0] sysfs_add_one+0x9f/0xe0
Aug 22 23:43:12 Dans kernel: [  232.468066]  [create_dir+0x48/0x90] create_dir+0x48/0x90
Aug 22 23:43:12 Dans kernel: [  232.468171]  [sysfs_create_dir+0x29/0x50] sysfs_create_dir+0x29/0x50
Aug 22 23:43:12 Dans kernel: [  232.468267]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
Aug 22 23:43:12 Dans kernel: [  232.468362]  [kobject_add+0x93/0x1b0] kobject_add+0x93/0x1b0
Aug 22 23:43:12 Dans kernel: [  232.468464]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 22 23:43:12 Dans kernel: [  232.468558]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 22 23:43:12 Dans kernel: [  232.468667]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 22 23:43:12 Dans kernel: [  232.468843]  [<c013f260>] param_get_int+0x0/0x20
Aug 22 23:43:12 Dans kernel: [  232.468975]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 22 23:43:12 Dans kernel: [  232.469111]  =======================
Aug 22 23:43:12 Dans kernel: [  232.469161] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
Aug 22 23:43:12 Dans kernel: [  232.469228] Pid: 3206, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 22 23:43:12 Dans kernel: [  232.469285]  [kobject_add+0x113/0x1b0] kobject_add+0x113/0x1b0
Aug 22 23:43:12 Dans kernel: [  232.469391]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 22 23:43:12 Dans kernel: [  232.469484]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 22 23:43:12 Dans kernel: [  232.469587]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 22 23:43:12 Dans kernel: [  232.469736]  [<c013f260>] param_get_int+0x0/0x20
Aug 22 23:43:12 Dans kernel: [  232.469844]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 22 23:43:12 Dans kernel: [  232.469958]  =======================
Aug 22 23:43:12 Dans kernel: [  232.880037] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 22 23:43:12 Dans kernel: [  232.904247] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Aug 22 23:43:12 Dans kernel: [  232.614619] usb 3-7: reset high speed USB device using ehci_hcd and address 2
Aug 22 23:43:12 Dans kernel: [  232.748456] zd1211rw 3-7:1.0: eth1
Aug 22 23:43:12 Dans kernel: [  232.748543] usbcore: registered new interface driver zd1211rw
Aug 22 23:43:12 Dans kernel: [  233.278906] NET: Registered protocol family 17
Aug 22 23:43:12 Dans kernel: [  233.432108] zd1211rw 3-7:1.0: firmware version 4725
Aug 22 23:43:12 Dans kernel: [  233.472113] zd1211rw 3-7:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
Aug 22 23:43:12 Dans kernel: [  233.794689] SoftMAC: Open Authentication completed with 00:18:d1:28:4f:05
Aug 22 23:43:12 Dans kernel: [  267.866568] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:43:12 Dans kernel: [  270.865553] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:43:12 Dans kernel: [  270.865558] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:43:12 Dans kernel: [  270.865563] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 23:43:12 Dans kernel: [  270.865568] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 23:43:12 Dans kernel: [  270.865572] eth0:  Tx descriptor 2 is 0008a156.
Aug 22 23:43:12 Dans kernel: [  270.865576] eth0:  Tx descriptor 3 is 0008a156.
Aug 22 23:43:12 Dans kernel: [  270.865637] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:43:12 Dans kernel: [  408.279259] lp0: using parport0 (interrupt-driven).
Aug 22 23:43:12 Dans kernel: [  408.469047] EXT3 FS on sda1, internal journal
Aug 22 23:43:12 Dans kernel: [  413.240142] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 22 23:43:12 Dans kernel: [  413.829948] NET: Registered protocol family 10
Aug 22 23:43:12 Dans kernel: [  413.830385] lo: Disabled Privacy Extensions
Aug 22 23:43:12 Dans kernel: [  422.292458] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:43:12 Dans kernel: [  424.183803] eth0: no IPv6 routers present
Aug 22 23:43:12 Dans kernel: [  424.655650] eth1: no IPv6 routers present
Aug 22 23:43:12 Dans kernel: [  425.291450] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:43:12 Dans kernel: [  425.291453] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:43:12 Dans kernel: [  425.291458] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 22 23:43:12 Dans kernel: [  425.291462] eth0:  Tx descriptor 1 is 0008a156.
Aug 22 23:43:12 Dans kernel: [  425.291466] eth0:  Tx descriptor 2 is 0008a05a.
Aug 22 23:43:12 Dans kernel: [  425.291470] eth0:  Tx descriptor 3 is 0008a04e.
Aug 22 23:43:12 Dans kernel: [  425.291530] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:43:12 Dans kernel: [  434.288437] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:43:12 Dans kernel: [  437.287354] eth0: Transmit timeout, status 0d 0004 c07f media 10.
Aug 22 23:43:12 Dans kernel: [  437.287357] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:43:12 Dans kernel: [  437.287362] eth0:  Tx descriptor 0 is 0008a046. (queue head)
Aug 22 23:43:12 Dans kernel: [  437.287366] eth0:  Tx descriptor 1 is 0008a046.
Aug 22 23:43:12 Dans kernel: [  437.287370] eth0:  Tx descriptor 2 is 0008a046.
Aug 22 23:43:12 Dans kernel: [  437.287374] eth0:  Tx descriptor 3 is 0008a05a.
Aug 22 23:43:12 Dans kernel: [  437.287430] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:43:12 Dans kernel: [  449.312006] No dock devices found.
Aug 22 23:43:12 Dans NetworkManager: <info>  starting... 
Aug 22 23:43:12 Dans avahi-daemon[8485]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 22 23:43:12 Dans avahi-daemon[8485]: Successfully dropped root privileges.
Aug 22 23:43:12 Dans avahi-daemon[8485]: avahi-daemon 0.6.22 starting up.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Successfully called chroot().
Aug 22 23:43:12 Dans avahi-daemon[8485]: Successfully dropped remaining capabilities.
Aug 22 23:43:12 Dans avahi-daemon[8485]: No service file found in /etc/avahi/services.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 22 23:43:12 Dans avahi-daemon[8485]: New relevant interface eth1.IPv4 for mDNS.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 22 23:43:12 Dans avahi-daemon[8485]: New relevant interface eth0.IPv4 for mDNS.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Network interface enumeration completed.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Registering new address record for fe80::217:3fff:fe34:c1de on eth1.*.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Registering new address record for 192.168.2.10 on eth1.IPv4.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Registering new address record for fe80::214:2aff:feb6:ae32 on eth0.*.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Registering new address record for 192.168.2.11 on eth0.IPv4.
Aug 22 23:43:12 Dans avahi-daemon[8485]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 22 23:43:12 Dans kernel: [  450.563167] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 22 23:43:12 Dans kernel: [  450.563175] apm: disabled - APM is not SMP safe.
Aug 22 23:43:12 Dans kernel: [  450.755246] ppdev: user-space parallel port driver
Aug 22 23:43:12 Dans kernel: [  450.921859] audit(1219462992.990:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8531 profile="/usr/sbin/cupsd" namespace="default"
Aug 22 23:43:13 Dans avahi-daemon[8485]: Server startup complete. Host name is Dans.local. Local service cookie is 3955161200.
Aug 22 23:43:15 Dans kernel: [  453.002864] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Aug 22 23:43:15 Dans kernel: [  453.002876] vboxdrv: Successfully done.
Aug 22 23:43:15 Dans kernel: [  453.002879] vboxdrv: Found 2 processor cores.
Aug 22 23:43:15 Dans kernel: [  453.002905] vboxdrv: fAsync=1 u64DiffCores=1055420056.
Aug 22 23:43:15 Dans kernel: [  453.002978] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Aug 22 23:43:15 Dans kernel: [  453.002982] vboxdrv: Successfully loaded version 1.6.4 (interface 0x00080000).
Aug 22 23:43:15 Dans dhcdbd: Started up.
Aug 22 23:43:16 Dans NetworkManager: <debug> [1219462996.409737] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_USB_MS_Reader_2004888_0_3'). 
Aug 22 23:43:16 Dans anacron[8885]: Anacron 2.3 started on 2008-08-22
Aug 22 23:43:16 Dans anacron[8885]: Normal exit (0 jobs run)
Aug 22 23:43:16 Dans /usr/sbin/cron[8917]: (CRON) INFO (pidfile fd = 3)
Aug 22 23:43:16 Dans /usr/sbin/cron[8918]: (CRON) STARTUP (fork ok)
Aug 22 23:43:16 Dans /usr/sbin/cron[8918]: (CRON) INFO (Running @reboot jobs)
Aug 22 23:43:20 Dans kernel: [  458.280173] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:43:23 Dans kernel: [  461.120926] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 22 23:43:23 Dans kernel: [  461.279169] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:43:23 Dans kernel: [  461.279177] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:43:23 Dans kernel: [  461.279182] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Aug 22 23:43:23 Dans kernel: [  461.279186] eth0:  Tx descriptor 1 is 0008a10e.
Aug 22 23:43:23 Dans kernel: [  461.279190] eth0:  Tx descriptor 2 is 0008a03c.
Aug 22 23:43:23 Dans kernel: [  461.279194] eth0:  Tx descriptor 3 is 0008a10e.
Aug 22 23:43:23 Dans kernel: [  461.279249] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:43:32 Dans kernel: [  470.276077] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:43:35 Dans kernel: [  473.275123] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:43:35 Dans kernel: [  473.275160] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:43:35 Dans kernel: [  473.275183] eth0:  Tx descriptor 0 is 0008a10e. (queue head)
Aug 22 23:43:35 Dans kernel: [  473.275203] eth0:  Tx descriptor 1 is 0008a0fc.
Aug 22 23:43:35 Dans kernel: [  473.275223] eth0:  Tx descriptor 2 is 0008a092.
Aug 22 23:43:35 Dans kernel: [  473.275243] eth0:  Tx descriptor 3 is 0008a092.
Aug 22 23:43:35 Dans kernel: [  473.275373] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:43:37 Dans kernel: [  474.982473] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:586: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x306f000a
Aug 22 23:43:38 Dans kernel: [  475.986142] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x306f000a
Aug 22 23:43:42 Dans NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 22 23:43:42 Dans NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 22 23:43:43 Dans NetworkManager: <info>  User request to disable wireless. 
Aug 22 23:43:44 Dans kernel: [  482.271989] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:43:47 Dans kernel: [  485.270984] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:43:47 Dans kernel: [  485.270991] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:43:47 Dans kernel: [  485.270996] eth0:  Tx descriptor 0 is 0008a092. (queue head)
Aug 22 23:43:47 Dans kernel: [  485.271001] eth0:  Tx descriptor 1 is 0008a0eb.
Aug 22 23:43:47 Dans kernel: [  485.271005] eth0:  Tx descriptor 2 is 0008a0d0.
Aug 22 23:43:47 Dans kernel: [  485.271009] eth0:  Tx descriptor 3 is 0008a0eb.
Aug 22 23:43:47 Dans kernel: [  485.271065] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:43:56 Dans kernel: [  494.267892] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:43:59 Dans kernel: [  497.266886] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:43:59 Dans kernel: [  497.266893] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:43:59 Dans kernel: [  497.266901] eth0:  Tx descriptor 0 is 0008a0fc. (queue head)
Aug 22 23:43:59 Dans kernel: [  497.266909] eth0:  Tx descriptor 1 is 0008a0eb.
Aug 22 23:43:59 Dans kernel: [  497.266914] eth0:  Tx descriptor 2 is 0008a052.
Aug 22 23:43:59 Dans kernel: [  497.266919] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 23:43:59 Dans kernel: [  497.266976] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:44:14 Dans kernel: [  512.261750] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:44:17 Dans kernel: [  515.260745] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:44:17 Dans kernel: [  515.260751] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:44:17 Dans kernel: [  515.260758] eth0:  Tx descriptor 0 is 0008a052. (queue head)
Aug 22 23:44:17 Dans kernel: [  515.260766] eth0:  Tx descriptor 1 is 0008a052.
Aug 22 23:44:17 Dans kernel: [  515.260771] eth0:  Tx descriptor 2 is 0008a052.
Aug 22 23:44:17 Dans kernel: [  515.260776] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 23:44:17 Dans kernel: [  515.260834] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:52:14 Dans kernel: [  992.097977] NETDEV WATCHDOG: eth0: transmit timed out
Aug 22 23:52:17 Dans kernel: [  995.096983] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 22 23:52:17 Dans kernel: [  995.096991] eth0: Tx queue start entry 4  dirty entry 0.
Aug 22 23:52:17 Dans kernel: [  995.096998] eth0:  Tx descriptor 0 is 0008a052. (queue head)
Aug 22 23:52:17 Dans kernel: [  995.097005] eth0:  Tx descriptor 1 is 0008a052.
Aug 22 23:52:17 Dans kernel: [  995.097010] eth0:  Tx descriptor 2 is 0008a052.
Aug 22 23:52:17 Dans kernel: [  995.097015] eth0:  Tx descriptor 3 is 0008a052.
Aug 22 23:52:17 Dans kernel: [  995.097095] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 22 23:56:59 Dans kernel: [ 1277.284647] hdc: lost interrupt
Aug 22 23:57:59 Dans kernel: [ 1337.264169] ide-cd: cmd 0x3 timed out
Aug 22 23:57:59 Dans kernel: [ 1337.264181] hdc: lost interrupt
Aug 23 00:17:01 Dans /USR/SBIN/CRON[9956]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 23 00:43:11 Dans -- MARK --
Aug 23 01:03:11 Dans -- MARK --
Aug 23 01:15:36 Dans init: tty4 main process (8005) killed by TERM signal
Aug 23 01:15:36 Dans init: tty5 main process (8006) killed by TERM signal
Aug 23 01:15:36 Dans init: tty2 main process (8008) killed by TERM signal
Aug 23 01:15:36 Dans init: tty3 main process (8010) killed by TERM signal
Aug 23 01:15:36 Dans init: tty6 main process (8012) killed by TERM signal
Aug 23 01:15:36 Dans init: tty1 main process (9028) killed by TERM signal
Aug 23 01:15:38 Dans avahi-daemon[8485]: Got SIGTERM, quitting.
Aug 23 01:15:38 Dans avahi-daemon[8485]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 23 01:15:38 Dans avahi-daemon[8485]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 23 01:15:40 Dans kernel: [ 5996.591021] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 23 01:15:41 Dans exiting on signal 15
Aug 23 01:24:19 Dans syslogd 1.5.0#1ubuntu1: restart.
Aug 23 01:24:19 Dans kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 23 01:24:19 Dans kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 23 01:24:19 Dans kernel: Symbols match kernel version 2.6.24.
Aug 23 01:24:19 Dans kernel: Loaded 20004 symbols from 91 modules.
Aug 23 01:24:19 Dans kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 23 01:24:19 Dans kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 23 01:24:19 Dans kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 23 01:24:19 Dans kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 23 01:24:19 Dans kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Aug 23 01:24:19 Dans kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Aug 23 01:24:19 Dans kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Aug 23 01:24:19 Dans kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007bfd0000 (usable)
Aug 23 01:24:19 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfd0000 - 000000007bfde000 (ACPI data)
Aug 23 01:24:19 Dans kernel: [    0.000000]  BIOS-e820: 000000007bfde000 - 000000007c000000 (ACPI NVS)
Aug 23 01:24:19 Dans kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug 23 01:24:19 Dans kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Aug 23 01:24:19 Dans kernel: [    0.000000] 1087MB HIGHMEM available.
Aug 23 01:24:19 Dans kernel: [    0.000000] 896MB LOWMEM available.
Aug 23 01:24:19 Dans kernel: [    0.000000] found SMP MP-table at 000ff780
Aug 23 01:24:19 Dans kernel: [    0.000000] Entering add_active_range(0, 0, 507856) 0 entries of 256 used
Aug 23 01:24:19 Dans kernel: [    0.000000] Zone PFN ranges:
Aug 23 01:24:19 Dans kernel: [    0.000000]   DMA             0 ->     4096
Aug 23 01:24:19 Dans kernel: [    0.000000]   Normal       4096 ->   229376
Aug 23 01:24:19 Dans kernel: [    0.000000]   HighMem    229376 ->   507856
Aug 23 01:24:19 Dans kernel: [    0.000000] Movable zone start PFN for each node
Aug 23 01:24:19 Dans kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 23 01:24:19 Dans kernel: [    0.000000]     0:        0 ->   507856
Aug 23 01:24:19 Dans kernel: [    0.000000] On node 0 totalpages: 507856
Aug 23 01:24:19 Dans kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 23 01:24:19 Dans kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 23 01:24:19 Dans kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 23 01:24:19 Dans kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 23 01:24:19 Dans kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 23 01:24:19 Dans kernel: [    0.000000]   HighMem zone: 2175 pages used for memmap
Aug 23 01:24:19 Dans kernel: [    0.000000]   HighMem zone: 276305 pages, LIFO batch:31
Aug 23 01:24:19 Dans kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 23 01:24:19 Dans kernel: [    0.000000] DMI present.
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8890 checksum 0
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: RSDP 000F8890, 0014 (r0 HP-CPC)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: RSDT 7BFD0000, 0038 (r1 HP-CPC OEMRSDT  11000518 MSFT       97)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: FACP 7BFD0200, 0084 (r2 HP-CPC OEMFACP  11000518 MSFT       97)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: DSDT 7BFD0440, 43B0 (r1 HP-CPC  RC410-M        0 INTL  2002026)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: FACS 7BFDE000, 0040
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: APIC 7BFD0390, 006C (r1 HP-CPC OEMAPIC  11000518 MSFT       97)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: MCFG 7BFD0400, 003C (r1 HP-CPC OEMMCFG  11000518 MSFT       97)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: OEMB 7BFDE040, 005B (r1 HP-CPC AMI_OEM  11000518 MSFT       97)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: HPET 7BFD47F0, 0038 (r1 HP-CPC OEMHPET  11000518 MSFT       97)
Aug 23 01:24:19 Dans kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug 23 01:24:19 Dans kernel: [    0.000000] Processor #0 15:4 APIC version 20
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Aug 23 01:24:19 Dans kernel: [    0.000000] Processor #1 15:4 APIC version 20
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
Aug 23 01:24:19 Dans kernel: [    0.000000] ACPI: HPET id: 0x0 base: 0xfed00000
Aug 23 01:24:19 Dans kernel: [    0.000000] Using ACPI for processor (LAPIC) configuration information
Aug 23 01:24:19 Dans kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Aug 23 01:24:19 Dans kernel: [    0.000000]     Virtual Wire compatibility mode.
Aug 23 01:24:19 Dans kernel: [    0.000000] OEM ID: ATI      Product ID: RS400        APIC at: 0xFEE00000
Aug 23 01:24:19 Dans kernel: [    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
Aug 23 01:24:19 Dans kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 23 01:24:19 Dans kernel: [    0.000000] Processors: 2
Aug 23 01:24:19 Dans kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7c000000:82e00000)
Aug 23 01:24:19 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 23 01:24:19 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
Aug 23 01:24:19 Dans kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Aug 23 01:24:19 Dans kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503889
Aug 23 01:24:19 Dans kernel: [    0.000000] Kernel command line: root=UUID=e9a7cff5-d8ae-4fb4-a348-d2db06aed623 ro single noapic
Aug 23 01:24:19 Dans kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 23 01:24:19 Dans kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 23 01:24:19 Dans kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 23 01:24:19 Dans kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 23 01:24:19 Dans kernel: [    0.000000] Initializing CPU#0
Aug 23 01:24:19 Dans kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 23 01:24:19 Dans kernel: [    0.000000] Detected 3199.406 MHz processor.
Aug 23 01:24:19 Dans kernel: [   31.991529] Console: colour VGA+ 80x25
Aug 23 01:24:19 Dans kernel: [   31.991534] console [tty0] enabled
Aug 23 01:24:19 Dans kernel: [   31.995157] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 23 01:24:19 Dans kernel: [   31.995950] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 23 01:24:19 Dans kernel: [   32.105046] Memory: 2001980k/2031424k available (2177k kernel code, 28188k reserved, 1006k data, 368k init, 1113920k highmem)
Aug 23 01:24:19 Dans kernel: [   32.105120] virtual kernel memory layout:
Aug 23 01:24:19 Dans kernel: [   32.105121]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 23 01:24:19 Dans kernel: [   32.105123]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 23 01:24:19 Dans kernel: [   32.105123]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 23 01:24:19 Dans kernel: [   32.105124]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 23 01:24:19 Dans kernel: [   32.105125]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 23 01:24:19 Dans kernel: [   32.105126]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 23 01:24:19 Dans kernel: [   32.105127]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 23 01:24:19 Dans kernel: [   32.105488] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 23 01:24:19 Dans kernel: [   32.105646] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 23 01:24:19 Dans kernel: [   32.105807] hpet clockevent registered
Aug 23 01:24:19 Dans kernel: [   33.172355] Calibrating delay using timer specific routine.. 88385.27 BogoMIPS (lpj=176770540)
Aug 23 01:24:19 Dans kernel: [   33.172478] Security Framework initialized
Aug 23 01:24:19 Dans kernel: [   33.172532] SELinux:  Disabled at boot.
Aug 23 01:24:19 Dans kernel: [   33.172599] AppArmor: AppArmor initialized
Aug 23 01:24:19 Dans kernel: [   33.172648] Failure registering capabilities with primary security module.
Aug 23 01:24:19 Dans kernel: [   33.172705] Mount-cache hash table entries: 512
Aug 23 01:24:19 Dans kernel: [   33.172920] Initializing cgroup subsys ns
Aug 23 01:24:19 Dans kernel: [   33.172971] Initializing cgroup subsys cpuacct
Aug 23 01:24:19 Dans kernel: [   33.173030] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 23 01:24:19 Dans kernel: [   33.173039] monitor/mwait feature present.
Aug 23 01:24:19 Dans kernel: [   33.173085] using mwait in idle threads.
Aug 23 01:24:19 Dans kernel: [   33.173135] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 23 01:24:19 Dans kernel: [   33.173218] CPU: L2 cache: 2048K
Aug 23 01:24:19 Dans kernel: [   33.173265] CPU: Physical Processor ID: 0
Aug 23 01:24:19 Dans kernel: [   33.173311] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 23 01:24:19 Dans kernel: [   33.173324] Compat vDSO mapped to ffffe000.
Aug 23 01:24:19 Dans kernel: [   33.173388] Checking 'hlt' instruction... OK.
Aug 23 01:24:19 Dans kernel: [   33.392539] SMP alternatives: switching to UP code
Aug 23 01:24:19 Dans kernel: [   33.394525] Early unpacking initramfs... done
Aug 23 01:24:19 Dans kernel: [   33.680551] ACPI: Core revision 20070126
Aug 23 01:24:19 Dans kernel: [   33.680655] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 23 01:24:19 Dans kernel: [   33.682660] ACPI: setting ELCR to 0200 (from 0c38)
Aug 23 01:24:19 Dans kernel: [   33.683372] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 23 01:24:19 Dans kernel: [   33.683510] SMP alternatives: switching to SMP code
Aug 23 01:24:19 Dans kernel: [   33.684385] Booting processor 1/1 eip 3000
Aug 23 01:24:19 Dans kernel: [   34.044405] Initializing CPU#1
Aug 23 01:24:19 Dans kernel: [   35.094656] Calibrating delay using timer specific routine.. 87826.80 BogoMIPS (lpj=175653604)
Aug 23 01:24:19 Dans kernel: [   35.094667] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000649d 00000000 00000000 00000000
Aug 23 01:24:19 Dans kernel: [   35.094674] monitor/mwait feature present.
Aug 23 01:24:19 Dans kernel: [   35.094681] CPU: Trace cache: 12K uops, L1 D cache: 16K
Aug 23 01:24:19 Dans kernel: [   35.094683] CPU: L2 cache: 2048K
Aug 23 01:24:19 Dans kernel: [   35.094686] CPU: Physical Processor ID: 0
Aug 23 01:24:19 Dans kernel: [   35.094688] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000649d 00000000 00000000 00000000
Aug 23 01:24:19 Dans kernel: [   34.765340] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
Aug 23 01:24:19 Dans kernel: [   34.766539] Total of 2 processors activated (176212.07 BogoMIPS).
Aug 23 01:24:19 Dans kernel: [   36.247269] APIC calibration not consistent with PM Timer: 1373ms instead of 100ms
Aug 23 01:24:19 Dans kernel: [   36.247326] APIC delta adjusted to PM-Timer: 1249642 (17159340)
Aug 23 01:24:19 Dans kernel: [   36.247525] checking TSC synchronization [CPU#0 -> CPU#1]:
Aug 23 01:24:19 Dans kernel: [   36.267610] Measured 1055866816 cycles TSC warp between CPUs, turning off TSC clock.
Aug 23 01:24:19 Dans kernel: [   36.267668] Marking TSC unstable due to: check_tsc_sync_source failed.
Aug 23 01:24:19 Dans kernel: [   36.267735] Brought up 2 CPUs
Aug 23 01:24:19 Dans kernel: [   36.267800] CPU0 attaching sched-domain:
Aug 23 01:24:19 Dans kernel: [   36.267803]  domain 0: span 03
Aug 23 01:24:19 Dans kernel: [   36.267806]   groups: 01 02
Aug 23 01:24:19 Dans kernel: [   36.267809]   domain 1: span 03
Aug 23 01:24:19 Dans kernel: [   36.267811]    groups: 03
Aug 23 01:24:19 Dans kernel: [   36.267814] CPU1 attaching sched-domain:
Aug 23 01:24:19 Dans kernel: [   36.267815]  domain 0: span 03
Aug 23 01:24:19 Dans kernel: [   36.267817]   groups: 02 01
Aug 23 01:24:19 Dans kernel: [   36.267820]   domain 1: span 03
Aug 23 01:24:19 Dans kernel: [   36.267822]    groups: 03
Aug 23 01:24:19 Dans kernel: [   36.268097] net_namespace: 64 bytes
Aug 23 01:24:19 Dans kernel: [   36.268151] Booting paravirtualized kernel on bare hardware
Aug 23 01:24:19 Dans kernel: [   36.268786] Time:  5:17:57  Date: 08/23/08
Aug 23 01:24:19 Dans kernel: [   36.268858] NET: Registered protocol family 16
Aug 23 01:24:19 Dans kernel: [   36.269161] EISA bus registered
Aug 23 01:24:19 Dans kernel: [   36.269210] ACPI: bus type pci registered
Aug 23 01:24:19 Dans kernel: [   36.269478] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
Aug 23 01:24:19 Dans kernel: [   36.269526] PCI: Using configuration type 1
Aug 23 01:24:19 Dans kernel: [   36.269587] Setting up standard PCI resources
Aug 23 01:24:19 Dans kernel: [   36.282079] ACPI: EC: Look up EC in DSDT
Aug 23 01:24:19 Dans kernel: [   36.288285] ACPI: Interpreter enabled
Aug 23 01:24:19 Dans kernel: [   36.288333] ACPI: (supports S0 S1 S3 S4 S5)
Aug 23 01:24:19 Dans kernel: [   36.288576] ACPI: Using PIC for interrupt routing
Aug 23 01:24:19 Dans kernel: [   36.299109] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 23 01:24:19 Dans kernel: [   36.300789] PCI: Transparent bridge - 0000:00:14.4
Aug 23 01:24:19 Dans kernel: [   36.300872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 23 01:24:19 Dans kernel: [   36.302369] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Aug 23 01:24:19 Dans kernel: [   36.302469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
Aug 23 01:24:19 Dans kernel: [   36.308304] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *4 5 7 10 11 12 14 15)
Aug 23 01:24:19 Dans kernel: [   36.308863] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 23 01:24:19 Dans kernel: [   36.309420] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Aug 23 01:24:19 Dans kernel: [   36.310054] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
Aug 23 01:24:19 Dans kernel: [   36.310610] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
Aug 23 01:24:19 Dans kernel: [   36.311165] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
Aug 23 01:24:19 Dans kernel: [   36.311505] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
Aug 23 01:24:19 Dans kernel: [   36.312061] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
Aug 23 01:24:19 Dans kernel: [   36.312643] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  A8, should be 9C [20070126]
Aug 23 01:24:19 Dans kernel: [   36.312782] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 23 01:24:19 Dans kernel: [   36.312870] pnp: PnP ACPI init
Aug 23 01:24:19 Dans kernel: [   36.312922] ACPI: bus type pnp registered
Aug 23 01:24:19 Dans kernel: [   36.319424] pnp: PnP ACPI: found 14 devices
Aug 23 01:24:19 Dans kernel: [   36.319472] ACPI: ACPI bus type pnp unregistered
Aug 23 01:24:19 Dans kernel: [   36.319522] PnPBIOS: Disabled by ACPI PNP
Aug 23 01:24:19 Dans kernel: [   36.649843] PCI: Using ACPI for IRQ routing
Aug 23 01:24:19 Dans kernel: [   36.649893] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 23 01:24:19 Dans kernel: [   36.649953] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Aug 23 01:24:19 Dans kernel: [   36.689685] NET: Registered protocol family 8
Aug 23 01:24:19 Dans kernel: [   36.689734] NET: Registered protocol family 20
Aug 23 01:24:19 Dans kernel: [   36.689830] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Aug 23 01:24:19 Dans kernel: [   36.690061] hpet0: 4 32-bit timers, 14318180 Hz
Aug 23 01:24:19 Dans kernel: [   36.691151] AppArmor: AppArmor Filesystem Enabled
Aug 23 01:24:19 Dans kernel: [   36.363379] Time: hpet clocksource has been installed.
Aug 23 01:24:19 Dans kernel: [   36.363443] Switched to high resolution mode on CPU 0
Aug 23 01:24:19 Dans kernel: [   36.693690] Switched to high resolution mode on CPU 1
Aug 23 01:24:19 Dans kernel: [   36.706388] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706444] system 00:07: ioport range 0x40b-0x40b has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706492] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706540] system 00:07: ioport range 0xc00-0xc01 has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706588] system 00:07: ioport range 0xc14-0xc14 has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706636] system 00:07: ioport range 0xc50-0xc51 has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706684] system 00:07: ioport range 0xc52-0xc52 has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706732] system 00:07: ioport range 0xc6c-0xc6c has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706780] system 00:07: ioport range 0xc6f-0xc6f has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706827] system 00:07: ioport range 0xcd4-0xcd5 has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706875] system 00:07: ioport range 0xcd6-0xcd7 has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706923] system 00:07: ioport range 0xcd8-0xcdf has been reserved
Aug 23 01:24:19 Dans kernel: [   36.706971] system 00:07: ioport range 0x800-0x89f has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707019] system 00:07: ioport range 0x900-0x90f has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707067] system 00:07: ioport range 0x910-0x91f has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707115] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
Aug 23 01:24:19 Dans kernel: [   36.707175] system 00:0a: ioport range 0xa00-0xa0f has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707223] system 00:0a: ioport range 0xa10-0xa1f has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707271] system 00:0a: ioport range 0xa20-0xa2f has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707319] system 00:0a: ioport range 0xa30-0xa3f has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707370] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707419] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
Aug 23 01:24:19 Dans kernel: [   36.707476] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Aug 23 01:24:19 Dans kernel: [   36.707528] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Aug 23 01:24:19 Dans kernel: [   36.708053] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Aug 23 01:24:19 Dans kernel: [   36.708102] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Aug 23 01:24:19 Dans kernel: [   36.708150] system 00:0d: iomem range 0x100000-0x7bffffff could not be reserved
Aug 23 01:24:19 Dans kernel: [   36.708203] system 00:0d: iomem range 0x0-0x0 could not be reserved
Aug 23 01:24:19 Dans kernel: [   36.408875] PCI: Bridge: 0000:00:01.0
Aug 23 01:24:19 Dans kernel: [   36.408924]   IO window: d000-dfff
Aug 23 01:24:19 Dans kernel: [   36.408971]   MEM window: fea00000-feafffff
Aug 23 01:24:19 Dans kernel: [   36.409018]   PREFETCH window: d0000000-dfffffff
Aug 23 01:24:19 Dans kernel: [   36.409067] PCI: Bridge: 0000:00:14.4
Aug 23 01:24:19 Dans kernel: [   36.409114]   IO window: e000-efff
Aug 23 01:24:19 Dans kernel: [   36.409164]   MEM window: feb00000-febfffff
Aug 23 01:24:19 Dans kernel: [   36.409212]   PREFETCH window: disabled.
Aug 23 01:24:19 Dans kernel: [   36.409288] NET: Registered protocol family 2
Aug 23 01:24:19 Dans kernel: [   36.455428] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 23 01:24:19 Dans kernel: [   36.455826] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 23 01:24:19 Dans kernel: [   36.456514] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 23 01:24:19 Dans kernel: [   36.456971] TCP: Hash tables configured (established 131072 bind 65536)
Aug 23 01:24:19 Dans kernel: [   36.457020] TCP reno registered
Aug 23 01:24:19 Dans kernel: [   36.467520] checking if image is initramfs... it is
Aug 23 01:24:19 Dans kernel: [   37.036662] Freeing initrd memory: 7312k freed
Aug 23 01:24:19 Dans kernel: [   37.367688] audit: initializing netlink socket (disabled)
Aug 23 01:24:19 Dans kernel: [   37.367755] audit(1219468673.972:1): initialized
Aug 23 01:24:19 Dans kernel: [   37.368089] highmem bounce pool size: 64 pages
Aug 23 01:24:19 Dans kernel: [   37.370655] VFS: Disk quotas dquot_6.5.1
Aug 23 01:24:19 Dans kernel: [   37.370794] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 23 01:24:19 Dans kernel: [   37.371010] io scheduler noop registered
Aug 23 01:24:19 Dans kernel: [   37.371057] io scheduler anticipatory registered
Aug 23 01:24:19 Dans kernel: [   37.371103] io scheduler deadline registered
Aug 23 01:24:19 Dans kernel: [   37.371157] io scheduler cfq registered (default)
Aug 23 01:24:19 Dans kernel: [   37.371211] PCI: MSI quirk detected. MSI deactivated.
Aug 23 01:24:19 Dans kernel: [   37.437164] Boot video device is 0000:01:05.0
Aug 23 01:24:19 Dans kernel: [   37.437541] isapnp: Scanning for PnP cards...
Aug 23 01:24:19 Dans kernel: [   38.458893] isapnp: No Plug & Play device found
Aug 23 01:24:19 Dans kernel: [   38.166153] Real Time Clock Driver v1.12ac
Aug 23 01:24:19 Dans kernel: [   38.166341] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 23 01:24:19 Dans kernel: [   38.498395] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 23 01:24:19 Dans kernel: [   38.499152] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 23 01:24:19 Dans kernel: [   38.499338] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Aug 23 01:24:19 Dans kernel: [   38.173324] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 23 01:24:19 Dans kernel: [   38.173377] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 23 01:24:19 Dans kernel: [   38.520876] mice: PS/2 mouse device common for all mice
Aug 23 01:24:19 Dans kernel: [   38.521079] EISA: Probing bus 0 at eisa.0
Aug 23 01:24:19 Dans kernel: [   38.521137] Cannot allocate resource for EISA slot 2
Aug 23 01:24:19 Dans kernel: [   38.521184] Cannot allocate resource for EISA slot 3
Aug 23 01:24:19 Dans kernel: [   38.521230] Cannot allocate resource for EISA slot 4
Aug 23 01:24:19 Dans kernel: [   38.521276] Cannot allocate resource for EISA slot 5
Aug 23 01:24:19 Dans kernel: [   38.521323] Cannot allocate resource for EISA slot 6
Aug 23 01:24:19 Dans kernel: [   38.521369] Cannot allocate resource for EISA slot 7
Aug 23 01:24:19 Dans kernel: [   38.521415] Cannot allocate resource for EISA slot 8
Aug 23 01:24:19 Dans kernel: [   38.521461] EISA: Detected 0 cards.
Aug 23 01:24:19 Dans kernel: [   38.521509] cpuidle: using governor ladder
Aug 23 01:24:19 Dans kernel: [   38.521554] cpuidle: using governor menu
Aug 23 01:24:19 Dans kernel: [   38.521692] NET: Registered protocol family 1
Aug 23 01:24:19 Dans kernel: [   38.521782] Using IPI No-Shortcut mode
Aug 23 01:24:19 Dans kernel: [   38.521860] registered taskstats version 1
Aug 23 01:24:19 Dans kernel: [   38.522015]   Magic number: 4:986:264
Aug 23 01:24:19 Dans kernel: [   38.522083]   hash matches device ttyx6
Aug 23 01:24:19 Dans kernel: [   38.522253] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 23 01:24:19 Dans kernel: [   38.522299] EDD information not available.
Aug 23 01:24:19 Dans kernel: [   38.522736] Freeing unused kernel memory: 368k freed
Aug 23 01:24:19 Dans kernel: [   38.209950] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 23 01:24:19 Dans kernel: [   38.393614] fuse init (API version 7.9)
Aug 23 01:24:19 Dans kernel: [   38.746009] ACPI: SSDT 7BFD4830, 02FE (r1    AMI   CPU1PM        1 INTL  2002026)
Aug 23 01:24:19 Dans kernel: [   38.746343] ACPI: duty_cycle spans bit 4
Aug 23 01:24:19 Dans kernel: [   38.746455] ACPI: SSDT 7BFD4B30, 02FE (r1    AMI   CPU2PM        1 INTL  2002026)
Aug 23 01:24:19 Dans kernel: [   38.746760] ACPI: duty_cycle spans bit 4
Aug 23 01:24:19 Dans kernel: [   38.746823] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 23 01:24:19 Dans kernel: [   38.746961] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug 23 01:24:19 Dans kernel: [   38.915971] SCSI subsystem initialized
Aug 23 01:24:19 Dans kernel: [   38.989666] usbcore: registered new interface driver usbfs
Aug 23 01:24:19 Dans kernel: [   38.989758] usbcore: registered new interface driver hub
Aug 23 01:24:19 Dans kernel: [   38.990464] libata version 3.00 loaded.
Aug 23 01:24:19 Dans kernel: [   38.997654] usbcore: registered new device driver usb
Aug 23 01:24:19 Dans kernel: [   39.005685] sata_sil 0000:00:11.0: version 2.3
Aug 23 01:24:19 Dans kernel: [   39.006003] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
Aug 23 01:24:19 Dans kernel: [   39.006058] PCI: setting IRQ 5 as level-triggered
Aug 23 01:24:19 Dans kernel: [   39.006064] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 23 01:24:19 Dans kernel: [   39.017742] scsi0 : sata_sil
Aug 23 01:24:19 Dans kernel: [   39.018611] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 23 01:24:19 Dans kernel: [   39.029607] scsi1 : sata_sil
Aug 23 01:24:19 Dans kernel: [   39.029722] ata1: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff080 irq 5
Aug 23 01:24:19 Dans kernel: [   39.029777] ata2: SATA max UDMA/100 mmio m512@0xfe9ff000 tf 0xfe9ff0c0 irq 5
Aug 23 01:24:19 Dans kernel: [   38.934575] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug 23 01:24:19 Dans kernel: [   38.934645] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug 23 01:24:19 Dans kernel: [   39.341494] ata1: SATA link down (SStatus 0 SControl 310)
Aug 23 01:24:19 Dans kernel: [   39.070938] 8139too Fast Ethernet driver 0.9.28
Aug 23 01:24:19 Dans kernel: [   39.429378] FDC 0 is a post-1991 82077
Aug 23 01:24:19 Dans kernel: [   39.323413] ata2: SATA link down (SStatus 0 SControl 310)
Aug 23 01:24:19 Dans kernel: [   39.653846] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
Aug 23 01:24:19 Dans kernel: [   39.653909] PCI: setting IRQ 11 as level-triggered
Aug 23 01:24:19 Dans kernel: [   39.653915] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
Aug 23 01:24:19 Dans kernel: [   39.654162] scsi2 : sata_sil
Aug 23 01:24:19 Dans kernel: [   39.654296] scsi3 : sata_sil
Aug 23 01:24:19 Dans kernel: [   39.654396] ata3: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff880 irq 11
Aug 23 01:24:19 Dans kernel: [   39.654452] ata4: SATA max UDMA/100 mmio m512@0xfe9ff800 tf 0xfe9ff8c0 irq 11
Aug 23 01:24:19 Dans kernel: [   40.120241] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug 23 01:24:19 Dans kernel: [   39.798802] ata3.00: ATA-7: WDC WD2500JS-60MHB1, 10.02E02, max UDMA/100
Aug 23 01:24:19 Dans kernel: [   39.798853] ata3.00: 488397168 sectors, multi 16: LBA48 
Aug 23 01:24:19 Dans kernel: [   39.806801] ata3.00: configured for UDMA/100
Aug 23 01:24:19 Dans kernel: [   40.134128] ata4: SATA link down (SStatus 0 SControl 310)
Aug 23 01:24:19 Dans kernel: [   40.464318] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500JS-60M 10.0 PQ: 0 ANSI: 5
Aug 23 01:24:19 Dans kernel: [   40.136167] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
Aug 23 01:24:19 Dans kernel: [   40.136221] PCI: setting IRQ 3 as level-triggered
Aug 23 01:24:19 Dans kernel: [   40.136227] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 23 01:24:19 Dans kernel: [   40.136374] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug 23 01:24:19 Dans kernel: [   40.136798] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Aug 23 01:24:19 Dans kernel: [   40.136877] ohci_hcd 0000:00:13.0: irq 3, io mem 0xfe9fe000
Aug 23 01:24:19 Dans kernel: [   40.202166] usb usb1: configuration #1 chosen from 1 choice
Aug 23 01:24:19 Dans kernel: [   40.202257] hub 1-0:1.0: USB hub found
Aug 23 01:24:19 Dans kernel: [   40.202316] hub 1-0:1.0: 4 ports detected
Aug 23 01:24:19 Dans kernel: [   40.306197] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 23 01:24:19 Dans kernel: [   40.306347] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug 23 01:24:19 Dans kernel: [   40.306444] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Aug 23 01:24:19 Dans kernel: [   40.306517] ohci_hcd 0000:00:13.1: irq 3, io mem 0xfe9fd000
Aug 23 01:24:19 Dans kernel: [   40.374517] usb usb2: configuration #1 chosen from 1 choice
Aug 23 01:24:19 Dans kernel: [   40.374604] hub 2-0:1.0: USB hub found
Aug 23 01:24:19 Dans kernel: [   40.374661] hub 2-0:1.0: 4 ports detected
Aug 23 01:24:19 Dans kernel: [   40.478125] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
Aug 23 01:24:19 Dans kernel: [   40.478379] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 4
Aug 23 01:24:19 Dans kernel: [   40.478428] PCI: setting IRQ 4 as level-triggered
Aug 23 01:24:19 Dans kernel: [   40.478433] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 23 01:24:19 Dans kernel: [   40.478568] ATIIXP: not 100% native mode: will probe irqs later
Aug 23 01:24:19 Dans kernel: [   40.478625]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:pio, hdb:pio
Aug 23 01:24:19 Dans kernel: [   40.478763]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
Aug 23 01:24:19 Dans kernel: [   40.478897] Probing IDE interface ide0...
Aug 23 01:24:19 Dans kernel: [   40.939928] usb 1-4: new full speed USB device using ohci_hcd and address 2
Aug 23 01:24:19 Dans kernel: [   40.817098] usb 1-4: configuration #1 chosen from 1 choice
Aug 23 01:24:19 Dans kernel: [   41.061811] Probing IDE interface ide1...
Aug 23 01:24:19 Dans kernel: [   41.451744] usb 2-4: new full speed USB device using ohci_hcd and address 2
Aug 23 01:24:19 Dans kernel: [   41.330944] usb 2-4: configuration #1 chosen from 1 choice
Aug 23 01:24:19 Dans kernel: [   41.869973] hdd: IDE-DVD DROM6216, ATAPI CD/DVD-ROM drive
Aug 23 01:24:19 Dans kernel: [   42.653696] hdc: HP DVD Writer 740b, ATAPI CD/DVD-ROM drive
Aug 23 01:24:19 Dans kernel: [   42.653868] hdc: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 23 01:24:19 Dans kernel: [   42.654140] hdc: UDMA/33 mode selected
Aug 23 01:24:19 Dans kernel: [   42.654447] hdd: host max PIO4 wanted PIO255(auto-tune) selected PIO4
Aug 23 01:24:19 Dans kernel: [   42.654663] hdd: host side 80-wire cable detection failed, limiting max speed to UDMA33
Aug 23 01:24:19 Dans kernel: [   42.654718] hdd: UDMA/33 mode selected
Aug 23 01:24:19 Dans kernel: [   42.656018] ide1 at 0x170-0x177,0x376 on irq 15
Aug 23 01:24:19 Dans kernel: [   42.659907] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
Aug 23 01:24:19 Dans kernel: [   42.990640] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Aug 23 01:24:19 Dans kernel: [   42.990785] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug 23 01:24:19 Dans kernel: [   42.990869] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Aug 23 01:24:19 Dans kernel: [   42.990983] ehci_hcd 0000:00:13.2: irq 3, io mem 0xfe9fc000
Aug 23 01:24:19 Dans kernel: [   42.991246] usb 1-4: USB disconnect, address 2
Aug 23 01:24:19 Dans kernel: [   43.000209] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 23 01:24:19 Dans kernel: [   43.000384] usb usb3: configuration #1 chosen from 1 choice
Aug 23 01:24:19 Dans kernel: [   43.000464] hub 3-0:1.0: USB hub found
Aug 23 01:24:19 Dans kernel: [   43.000517] hub 3-0:1.0: 8 ports detected
Aug 23 01:24:19 Dans kernel: [   43.120177] usb 2-4: USB disconnect, address 2
Aug 23 01:24:19 Dans kernel: [   42.817320] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug 23 01:24:19 Dans kernel: [   43.162560] ACPI: PCI Interrupt Link [LNKE] BIOS reported IRQ 15, using IRQ 10
Aug 23 01:24:19 Dans kernel: [   43.162634] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
Aug 23 01:24:19 Dans kernel: [   43.162692] PCI: setting IRQ 10 as level-triggered
Aug 23 01:24:19 Dans kernel: [   43.162698] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
Aug 23 01:24:19 Dans kernel: [   43.164915] eth0: RealTek RTL8139 at 0xe400, 00:14:2a:b6:ae:32, IRQ 10
Aug 23 01:24:19 Dans kernel: [   43.164972] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Aug 23 01:24:19 Dans kernel: [   43.180073] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Aug 23 01:24:19 Dans kernel: [   42.893820] Driver 'sd' needs updating - please use bus_type methods
Aug 23 01:24:19 Dans kernel: [   42.894259] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 23 01:24:19 Dans kernel: [   42.894333] sd 2:0:0:0: [sda] Write Protect is off
Aug 23 01:24:19 Dans kernel: [   42.894385] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 23 01:24:19 Dans kernel: [   42.894420] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 23 01:24:19 Dans kernel: [   42.894564] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Aug 23 01:24:19 Dans kernel: [   42.894633] sd 2:0:0:0: [sda] Write Protect is off
Aug 23 01:24:19 Dans kernel: [   42.894685] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 23 01:24:19 Dans kernel: [   42.894716] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 23 01:24:19 Dans kernel: [   42.894784]  sda: sda1 sda2 < sda5 >
Aug 23 01:24:19 Dans kernel: [   42.935857] sd 2:0:0:0: [sda] Attached SCSI disk
Aug 23 01:24:19 Dans kernel: [   43.271235] sd 2:0:0:0: Attached scsi generic sg0 type 0
Aug 23 01:24:19 Dans kernel: [   43.487083] usb 3-7: new high speed USB device using ehci_hcd and address 2
Aug 23 01:24:19 Dans kernel: [   43.290170] usb 3-7: configuration #1 chosen from 1 choice
Aug 23 01:24:19 Dans kernel: [   43.858985] usbcore: registered new interface driver libusual
Aug 23 01:24:19 Dans kernel: [   44.164929] usb 2-4: new full speed USB device using ohci_hcd and address 3
Aug 23 01:24:19 Dans kernel: [   44.042025] usb 2-4: configuration #1 chosen from 1 choice
Aug 23 01:24:19 Dans kernel: [   44.053722] Initializing USB Mass Storage driver...
Aug 23 01:24:19 Dans kernel: [   44.053879] scsi4 : SCSI emulation for USB Mass Storage devices
Aug 23 01:24:19 Dans kernel: [   44.054035] usbcore: registered new interface driver usb-storage
Aug 23 01:24:19 Dans kernel: [   44.054105] USB Mass Storage support registered.
Aug 23 01:24:19 Dans kernel: [   44.054310] usb-storage: device found at 3
Aug 23 01:24:19 Dans kernel: [   44.054313] usb-storage: waiting for device to settle before scanning
Aug 23 01:24:19 Dans kernel: [   44.434943] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff3db232]
Aug 23 01:24:19 Dans kernel: [   49.051490] usb-storage: device scan complete
Aug 23 01:24:19 Dans kernel: [   49.387443] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Aug 23 01:24:19 Dans kernel: [   49.393435] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Aug 23 01:24:19 Dans kernel: [   49.399443] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Aug 23 01:24:19 Dans kernel: [   49.405442] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Aug 23 01:24:19 Dans kernel: [   49.415481] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Aug 23 01:24:19 Dans kernel: [   49.415595] sd 4:0:0:0: Attached scsi generic sg1 type 0
Aug 23 01:24:19 Dans kernel: [   49.425486] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Aug 23 01:24:19 Dans kernel: [   49.426248] sd 4:0:0:1: Attached scsi generic sg2 type 0
Aug 23 01:24:19 Dans kernel: [   49.435484] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Aug 23 01:24:19 Dans kernel: [   49.435590] sd 4:0:0:2: Attached scsi generic sg3 type 0
Aug 23 01:24:19 Dans kernel: [   49.445491] sd 4:0:0:3: [sde] Attached SCSI removable disk
Aug 23 01:24:19 Dans kernel: [   49.445612] sd 4:0:0:3: Attached scsi generic sg4 type 0
Aug 23 01:24:19 Dans kernel: [   50.197757] ide-cd: cmd 0x5a timed out
Aug 23 01:24:19 Dans kernel: [   50.197819] hdc: lost interrupt
Aug 23 01:24:19 Dans kernel: [  110.176277] ide-cd: cmd 0x5a timed out
Aug 23 01:24:19 Dans kernel: [  110.176329] hdc: lost interrupt
Aug 23 01:24:19 Dans kernel: [  110.176404] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Aug 23 01:24:19 Dans kernel: [  110.176675] Uniform CD-ROM driver Revision: 3.20
Aug 23 01:24:19 Dans kernel: [  170.155820] hdc: lost interrupt
Aug 23 01:24:19 Dans kernel: [  222.853835] Attempting manual resume
Aug 23 01:24:19 Dans kernel: [  222.853883] swsusp: Resume From Partition 8:5
Aug 23 01:24:19 Dans kernel: [  222.853885] PM: Checking swsusp image.
Aug 23 01:24:19 Dans kernel: [  222.854119] PM: Resume from disk failed.
Aug 23 01:24:19 Dans kernel: [  223.234678] kjournald starting.  Commit interval 5 seconds
Aug 23 01:24:19 Dans kernel: [  222.904733] EXT3-fs: mounted filesystem with ordered data mode.
Aug 23 01:24:19 Dans kernel: [  230.136341] hdc: lost interrupt
Aug 23 01:24:19 Dans kernel: [  230.688377] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug 23 01:24:19 Dans kernel: [  230.541787] parport_pc 00:06: reported by Plug and Play ACPI
Aug 23 01:24:19 Dans kernel: [  230.541979] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Aug 23 01:24:19 Dans kernel: [  230.605214] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 23 01:24:19 Dans kernel: [  230.637298] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 23 01:24:19 Dans kernel: [  230.745215] Linux agpgart interface v0.102
Aug 23 01:24:19 Dans kernel: [  230.927150] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug 23 01:24:19 Dans kernel: [  231.672100] input: Power Button (FF) as /devices/virtual/input/input3
Aug 23 01:24:19 Dans kernel: [  231.743867] ACPI: Power Button (FF) [PWRF]
Aug 23 01:24:19 Dans kernel: [  231.744061] input: Power Button (CM) as /devices/virtual/input/input4
Aug 23 01:24:19 Dans kernel: [  231.787921] ACPI: Power Button (CM) [PWRB]
Aug 23 01:24:19 Dans kernel: [  232.207187] sysfs: duplicate filename 'pcspkr' can not be created
Aug 23 01:24:19 Dans kernel: [  232.207259] WARNING: at /build/buildd/linux-2.6.24/fs/sysfs/dir.c:424 sysfs_add_one()
Aug 23 01:24:19 Dans kernel: [  232.207332] Pid: 3183, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 23 01:24:19 Dans kernel: [  232.207409]  [sysfs_add_one+0x9f/0xe0] sysfs_add_one+0x9f/0xe0
Aug 23 01:24:19 Dans kernel: [  232.207533]  [create_dir+0x48/0x90] create_dir+0x48/0x90
Aug 23 01:24:19 Dans kernel: [  232.207633]  [sysfs_create_dir+0x29/0x50] sysfs_create_dir+0x29/0x50
Aug 23 01:24:19 Dans kernel: [  232.207733]  [kobject_get+0xf/0x20] kobject_get+0xf/0x20
Aug 23 01:24:19 Dans kernel: [  232.207834]  [kobject_add+0x93/0x1b0] kobject_add+0x93/0x1b0
Aug 23 01:24:19 Dans kernel: [  232.207941]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 23 01:24:19 Dans kernel: [  232.208040]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 23 01:24:19 Dans kernel: [  232.208160]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 23 01:24:19 Dans kernel: [  232.208311]  [<c013f260>] param_get_int+0x0/0x20
Aug 23 01:24:19 Dans kernel: [  232.208430]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 23 01:24:19 Dans kernel: [  232.208563]  =======================
Aug 23 01:24:19 Dans kernel: [  232.208620] kobject_add failed for pcspkr with -EEXIST, don't try to register things with the same name in the same directory.
Aug 23 01:24:19 Dans kernel: [  232.208692] Pid: 3183, comm: modprobe Not tainted 2.6.24-19-generic #1
Aug 23 01:24:19 Dans kernel: [  232.208756]  [kobject_add+0x113/0x1b0] kobject_add+0x113/0x1b0
Aug 23 01:24:19 Dans kernel: [  232.208861]  [pci_hotplug:kobject_register+0x21/0x2df0] kobject_register+0x21/0x50
Aug 23 01:24:19 Dans kernel: [  232.208965]  [bus_add_driver+0x71/0x1e0] bus_add_driver+0x71/0x1e0
Aug 23 01:24:19 Dans kernel: [  232.209087]  [sys_init_module+0x126/0x19c0] sys_init_module+0x126/0x19c0
Aug 23 01:24:19 Dans kernel: [  232.209237]  [<c013f260>] param_get_int+0x0/0x20
Aug 23 01:24:19 Dans kernel: [  232.209348]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug 23 01:24:19 Dans kernel: [  232.209454]  =======================
Aug 23 01:24:19 Dans kernel: [  232.486244] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:24:19 Dans kernel: [  232.803874] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Aug 23 01:24:19 Dans kernel: [  233.004891] ieee80211_crypt: registered algorithm 'NULL'
Aug 23 01:24:19 Dans kernel: [  233.027301] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug 23 01:24:19 Dans kernel: [  233.027377] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug 23 01:24:19 Dans kernel: [  233.185529] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [LNKA] -> GSI 4 (level, low) -> IRQ 4
Aug 23 01:24:19 Dans kernel: [  233.230116] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Aug 23 01:24:19 Dans kernel: [  233.328193] usb 3-7: reset high speed USB device using ehci_hcd and address 2
Aug 23 01:24:19 Dans kernel: [  233.463687] zd1211rw 3-7:1.0: eth1
Aug 23 01:24:19 Dans kernel: [  233.463776] usbcore: registered new interface driver zd1211rw
Aug 23 01:24:19 Dans kernel: [  234.213352] zd1211rw 3-7:1.0: firmware version 4725
Aug 23 01:24:19 Dans kernel: [  234.253355] zd1211rw 3-7:1.0: zd1211b chip 050d:705c v4810 high 00-17-3f AL2230_RF pa0 g--NS
Aug 23 01:24:19 Dans kernel: [  234.303687] NET: Registered protocol family 17
Aug 23 01:24:19 Dans kernel: [  234.583940] SoftMAC: Open Authentication completed with 00:18:d1:28:4f:05
Aug 23 01:24:19 Dans kernel: [  274.798021] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:24:19 Dans kernel: [  277.801009] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 23 01:24:19 Dans kernel: [  277.801014] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:24:19 Dans kernel: [  277.801019] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 23 01:24:19 Dans kernel: [  277.801023] eth0:  Tx descriptor 1 is 0008a156.
Aug 23 01:24:19 Dans kernel: [  277.801027] eth0:  Tx descriptor 2 is 0008a156.
Aug 23 01:24:19 Dans kernel: [  277.801031] eth0:  Tx descriptor 3 is 0008a156.
Aug 23 01:24:19 Dans kernel: [  277.801111] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:24:19 Dans kernel: [  414.188862] lp0: using parport0 (interrupt-driven).
Aug 23 01:24:19 Dans kernel: [  414.388811] EXT3 FS on sda1, internal journal
Aug 23 01:24:19 Dans kernel: [  415.194789] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 23 01:24:19 Dans kernel: [  415.942531] NET: Registered protocol family 10
Aug 23 01:24:19 Dans kernel: [  415.942968] lo: Disabled Privacy Extensions
Aug 23 01:24:19 Dans kernel: [  417.437181] No dock devices found.
Aug 23 01:24:19 Dans NetworkManager: <info>  starting... 
Aug 23 01:24:19 Dans avahi-daemon[8463]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 23 01:24:19 Dans avahi-daemon[8463]: Successfully dropped root privileges.
Aug 23 01:24:19 Dans avahi-daemon[8463]: avahi-daemon 0.6.22 starting up.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Successfully called chroot().
Aug 23 01:24:19 Dans avahi-daemon[8463]: Successfully dropped remaining capabilities.
Aug 23 01:24:19 Dans avahi-daemon[8463]: No service file found in /etc/avahi/services.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.10.
Aug 23 01:24:19 Dans avahi-daemon[8463]: New relevant interface eth1.IPv4 for mDNS.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.11.
Aug 23 01:24:19 Dans avahi-daemon[8463]: New relevant interface eth0.IPv4 for mDNS.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Network interface enumeration completed.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Registering new address record for fe80::217:3fff:fe34:c1de on eth1.*.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Registering new address record for 192.168.2.10 on eth1.IPv4.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Registering new address record for fe80::214:2aff:feb6:ae32 on eth0.*.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Registering new address record for 192.168.2.11 on eth0.IPv4.
Aug 23 01:24:19 Dans avahi-daemon[8463]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 23 01:24:19 Dans kernel: [  418.655161] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 23 01:24:19 Dans kernel: [  418.655169] apm: disabled - APM is not SMP safe.
Aug 23 01:24:20 Dans kernel: [  418.839099] ppdev: user-space parallel port driver
Aug 23 01:24:20 Dans kernel: [  418.997307] audit(1219469060.288:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8509 profile="/usr/sbin/cupsd" namespace="default"
Aug 23 01:24:20 Dans avahi-daemon[8463]: Server startup complete. Host name is Dans.local. Local service cookie is 2742378360.
Aug 23 01:24:22 Dans kernel: [  420.953413] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Aug 23 01:24:22 Dans kernel: [  420.953426] vboxdrv: Successfully done.
Aug 23 01:24:22 Dans kernel: [  420.953429] vboxdrv: Found 2 processor cores.
Aug 23 01:24:22 Dans kernel: [  420.953453] vboxdrv: fAsync=1 u64DiffCores=1055872120.
Aug 23 01:24:22 Dans kernel: [  421.285457] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Aug 23 01:24:22 Dans kernel: [  421.285464] vboxdrv: Successfully loaded version 1.6.4 (interface 0x00080000).
Aug 23 01:24:22 Dans dhcdbd: Started up.
Aug 23 01:24:23 Dans NetworkManager: <debug> [1219469063.646136] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Generic_USB_MS_Reader_2004888_0_3'). 
Aug 23 01:24:23 Dans anacron[8862]: Anacron 2.3 started on 2008-08-23
Aug 23 01:24:23 Dans anacron[8862]: Will run job `cron.daily' in 5 min.
Aug 23 01:24:23 Dans anacron[8862]: Jobs will be executed sequentially
Aug 23 01:24:24 Dans /usr/sbin/cron[8896]: (CRON) INFO (pidfile fd = 3)
Aug 23 01:24:24 Dans /usr/sbin/cron[8902]: (CRON) STARTUP (fork ok)
Aug 23 01:24:24 Dans /usr/sbin/cron[8902]: (CRON) INFO (Running @reboot jobs)
Aug 23 01:24:26 Dans kernel: [  424.926711] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:24:27 Dans kernel: [  426.433430] eth1: no IPv6 routers present
Aug 23 01:24:27 Dans kernel: [  426.693222] eth0: no IPv6 routers present
Aug 23 01:24:29 Dans kernel: [  427.924199] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 23 01:24:29 Dans kernel: [  427.924207] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:24:29 Dans kernel: [  427.924212] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Aug 23 01:24:29 Dans kernel: [  427.924217] eth0:  Tx descriptor 1 is 0008a156.
Aug 23 01:24:29 Dans kernel: [  427.924221] eth0:  Tx descriptor 2 is 0008a156.
Aug 23 01:24:29 Dans kernel: [  427.924225] eth0:  Tx descriptor 3 is 0008a05a.
Aug 23 01:24:29 Dans kernel: [  427.924281] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:24:30 Dans kernel: [  428.820159] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug 23 01:24:38 Dans kernel: [  436.920627] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:24:40 Dans kernel: [  439.364787] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:586: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x306f000a
Aug 23 01:24:41 Dans kernel: [  439.914104] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 23 01:24:41 Dans kernel: [  439.914111] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:24:41 Dans kernel: [  439.914117] eth0:  Tx descriptor 0 is 0008a04e. (queue head)
Aug 23 01:24:41 Dans kernel: [  439.914123] eth0:  Tx descriptor 1 is 0008a046.
Aug 23 01:24:41 Dans kernel: [  439.914127] eth0:  Tx descriptor 2 is 0008a05a.
Aug 23 01:24:41 Dans kernel: [  439.914132] eth0:  Tx descriptor 3 is 0008a03c.
Aug 23 01:24:41 Dans kernel: [  439.914190] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:24:41 Dans kernel: [  440.367941] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x306f000a
Aug 23 01:24:45 Dans NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 23 01:24:45 Dans NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 23 01:24:45 Dans NetworkManager: <info>  User request to disable wireless. 
Aug 23 01:24:50 Dans kernel: [  448.906524] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:24:53 Dans kernel: [  451.908011] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 23 01:24:53 Dans kernel: [  451.908018] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:24:53 Dans kernel: [  451.908023] eth0:  Tx descriptor 0 is 0008a10e. (queue head)
Aug 23 01:24:53 Dans kernel: [  451.908027] eth0:  Tx descriptor 1 is 0008a10e.
Aug 23 01:24:53 Dans kernel: [  451.908031] eth0:  Tx descriptor 2 is 0008a10e.
Aug 23 01:24:53 Dans kernel: [  451.908035] eth0:  Tx descriptor 3 is 0008a0fc.
Aug 23 01:24:53 Dans kernel: [  451.908090] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:25:02 Dans kernel: [  460.896431] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:25:05 Dans kernel: [  463.893925] eth0: Transmit timeout, status 0d 0004 c07f media 10.
Aug 23 01:25:05 Dans kernel: [  463.893933] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:25:05 Dans kernel: [  463.893938] eth0:  Tx descriptor 0 is 0008a092. (queue head)
Aug 23 01:25:05 Dans kernel: [  463.893942] eth0:  Tx descriptor 1 is 0008a092.
Aug 23 01:25:05 Dans kernel: [  463.893946] eth0:  Tx descriptor 2 is 0008a092.
Aug 23 01:25:05 Dans kernel: [  463.893950] eth0:  Tx descriptor 3 is 0008a0eb.
Aug 23 01:25:05 Dans kernel: [  463.894005] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:25:14 Dans kernel: [  472.886344] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:25:17 Dans kernel: [  475.883865] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 23 01:25:17 Dans kernel: [  475.883874] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:25:17 Dans kernel: [  475.883881] eth0:  Tx descriptor 0 is 0008a0d0. (queue head)
Aug 23 01:25:17 Dans kernel: [  475.883886] eth0:  Tx descriptor 1 is 0008a046.
Aug 23 01:25:17 Dans kernel: [  475.883892] eth0:  Tx descriptor 2 is 0008a0eb.
Aug 23 01:25:17 Dans kernel: [  475.883897] eth0:  Tx descriptor 3 is 0008a0fc.
Aug 23 01:25:17 Dans kernel: [  475.883956] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:25:26 Dans kernel: [  484.880245] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:25:29 Dans kernel: [  487.873760] eth0: Transmit timeout, status 0d 0004 c07f media 10.
Aug 23 01:25:29 Dans kernel: [  487.873767] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:25:29 Dans kernel: [  487.873772] eth0:  Tx descriptor 0 is 0008a0eb. (queue head)
Aug 23 01:25:29 Dans kernel: [  487.873777] eth0:  Tx descriptor 1 is 0008a03c.
Aug 23 01:25:29 Dans kernel: [  487.873781] eth0:  Tx descriptor 2 is 0008a046.
Aug 23 01:25:29 Dans kernel: [  487.873784] eth0:  Tx descriptor 3 is 0008a052.
Aug 23 01:25:29 Dans kernel: [  487.873839] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:25:38 Dans kernel: [  496.866167] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:25:41 Dans kernel: [  499.863659] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 23 01:25:41 Dans kernel: [  499.863666] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:25:41 Dans kernel: [  499.863671] eth0:  Tx descriptor 0 is 0008a052. (queue head)
Aug 23 01:25:41 Dans kernel: [  499.863676] eth0:  Tx descriptor 1 is 0008a052.
Aug 23 01:25:41 Dans kernel: [  499.863680] eth0:  Tx descriptor 2 is 0008a052.
Aug 23 01:25:41 Dans kernel: [  499.863684] eth0:  Tx descriptor 3 is 0008a052.
Aug 23 01:25:41 Dans kernel: [  499.863740] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:29:02 Dans kernel: [  700.749395] NETDEV WATCHDOG: eth0: transmit timed out
Aug 23 01:29:05 Dans kernel: [  703.748405] eth0: Transmit timeout, status 0c 0005 c07f media 10.
Aug 23 01:29:05 Dans kernel: [  703.748415] eth0: Tx queue start entry 4  dirty entry 0.
Aug 23 01:29:05 Dans kernel: [  703.748423] eth0:  Tx descriptor 0 is 0008a052. (queue head)
Aug 23 01:29:05 Dans kernel: [  703.748429] eth0:  Tx descriptor 1 is 0008a052.
Aug 23 01:29:05 Dans kernel: [  703.748434] eth0:  Tx descriptor 2 is 0008a052.
Aug 23 01:29:05 Dans kernel: [  703.748440] eth0:  Tx descriptor 3 is 0008a052.
Aug 23 01:29:05 Dans kernel: [  703.748499] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Aug 23 01:29:23 Dans anacron[8862]: Job `cron.daily' started
Aug 23 01:29:23 Dans anacron[9352]: Updated timestamp for job `cron.daily' to 2008-08-23

---

### Post by Dan6 on 2008-08-23
> **mc4man said:**
> Run this with a disk in the drive (if possible something with a filesystem like a data cd/dvd or a dvd movie 
```
sudo lshw -C disk
```

Also post this (run from maximized terminal for readability

```
cat /etc/udev/rules.d/70-persistent-cd.rules 
```



second thing gets me this: dan@Dans:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

first gets this  
*-disk                  
       description: ATA Disk
       product: WDC WD2500JS-60M
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 10.0
       serial: WD-WCANK1501805
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=1549f232
  *-disk:0
       description: SCSI Disk
       product: USB SD Reader
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 1.00
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: USB CF Reader
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdc
       version: 1.01
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       product: USB SM Reader
       vendor: Generic
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sdd
       version: 1.02
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:3
       description: SCSI Disk
       product: USB MS Reader
       vendor: Generic
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sde
       version: 1.03
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
  *-cdrom:0
       product: HP DVD Writer 740b
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       capacity: 3789MiB (3973MB)
  *-cdrom:1
       product: IDE-DVD DROM6216
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd

---

### Post by mb_webguy on 2008-08-23
Well, your cd/dvd-rom drive (IDE-DVD DROM6216) looks like it should be working, though it seems like it's using /dev/hdd instead of the /dev/scd0 in fstab.  At the very least, it's not triggering any error messages...  Try "sudo mount -t iso9660 /dev/hdd" after inserting a disk in that drive.  If that works, open fstab with "gksu gedit /etc/fstab" and change "/dev/scd0" to "/dev/hdd".

As for your dvd-rw drive (HP DVD Writer 740b), you're definitely having a problem of some sort, but not one that I'm able to accurately diagnose.  Those "lost interrupt" messages tend to mean either bad hardware or a bad driver, but could mean a lot of other things besides.  Hopefully one of the dev-level members will pop in and be able to help...

:frown:

---

### Post by mc4man on 2008-08-23
You may want to try booting with a noapic boot parameter.

How did you install hardy?, a fresh install or as an upgrade? If an upgrade, then from what?

If you have a hardy livecd it would be interesting to see results of sudo lshw.... and what's in 70.....rules after booting to it. (boot without any external usb devices connected if possible
Also look thru your logs as a comparison to what's presently shown

---

### Post by Dan6 on 2008-08-23
I have to boot with noapic or I get an error something like ms bios timeout + I0 apic not working. My internet connection comes from a usb wireless adapter, should I unplug it and reboot? That all I have connected.

---

### Post by Dan6 on 2008-08-23
> **mc4man said:**
> You may want to try booting with a noapic boot parameter.

How did you install hardy?, a fresh install or as an upgrade? If an upgrade, then from what?

If you have a hardy livecd it would be interesting to see results of sudo lshw.... and what's in 70.....rules after booting to it. (boot without any external usb devices connected if possible
Also look thru your logs as a comparison to what's presently shown

Also hardy was from a fresh install. I have a live cd should I put it in before trying sudo lshw?

---

### Post by Dan6 on 2008-08-23
here's the results of sudo lshw with the hardy live cd in the drive
dan@Dans:~$ sudo lshw
[sudo] password for dan: 
dans                      
    description: Desktop Computer
    product: EL470AA-ABA a1340n
    vendor: HP Pavilion 061
    version: 0ny1114RE101ASTER00
    serial: CNN5490FDW NA650
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=743DB279-D962-DA11-8269-07E04AC326F4
  *-core
       description: Motherboard
       product: Asterope
       vendor: Hewleet-Packard
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.03 (11/18/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.3
          serial: 0000-0F43-0000-0000-0000-0000
          slot: CPU 1
          size: 2800MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est cid cx16 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi vga_controller bus_master cap_list
                configuration: latency=64 mingnt=8
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: ATA Disk
                product: WDC WD2500JS-60M
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANK1501805
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1549f232
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: e9a7cff5-d8ae-4fb4-a348-d2db06aed623
                   size: 227GiB
                   capacity: 227GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-08-18 18:06:13 filesystem=ext3 modified=2008-08-23 08:59:59 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-08-23 01:24:15 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 5749MiB
                   capacity: 5749MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5749MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.24-19-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=4 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.24-19-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: maxpower=0mA slots=4 speed=12.0MB/s
              *-usb
                   description: Generic USB device
                   product: USB Reader
                   physical id: 4
                   bus info: usb@3:4
                   logical name: scsi4
                   version: 1.00
                   serial: 2004888
                   capabilities: usb-1.10 emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk:0
                      description: SCSI Disk
                      product: USB SD Reader
                      vendor: Generic
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdb
                      version: 1.00
                      capabilities: removable
                    *-medium
                         physical id: 0
                         logical name: /dev/sdb
                 *-disk:1
                      description: SCSI Disk
                      product: USB CF Reader
                      vendor: Generic
                      physical id: 0.0.1
                      bus info: scsi@4:0.0.1
                      logical name: /dev/sdc
                      version: 1.01
                      capabilities: removable
                    *-medium
                         physical id: 0
                         logical name: /dev/sdc
                 *-disk:2
                      description: SCSI Disk
                      product: USB SM Reader
                      vendor: Generic
                      physical id: 0.0.2
                      bus info: scsi@4:0.0.2
                      logical name: /dev/sdd
                      version: 1.02
                      capabilities: removable
                    *-medium
                         physical id: 0
                         logical name: /dev/sdd
                 *-disk:3
                      description: SCSI Disk
                      product: USB MS Reader
                      vendor: Generic
                      physical id: 0.0.3
                      bus info: scsi@4:0.0.3
                      logical name: /dev/sde
                      version: 1.03
                      capabilities: removable
                    *-medium
                         physical id: 0
                         logical name: /dev/sde
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.24-19-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: maxpower=0mA slots=8 speed=480.0MB/s
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: USB2.0 WLAN
                   vendor: Belkin
                   physical id: 7
                   bus info: usb@1:7
                   version: 48.10
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 81
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
           *-ide
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom:0
                   product: HP DVD Writer 740b
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 2240MiB (2349MB)
              *-cdrom:1
                   product: IDE-DVD DROM6216
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: Agere Systems
                vendor: Agere Systems
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:14:2a:b6:ae:32
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.11 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:3f:34:c1:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.10 multicast=yes wireless=IEEE 802.11b/g

---

### Post by Dan6 on 2008-08-23
> **mb_webguy said:**
> Well, your cd/dvd-rom drive (IDE-DVD DROM6216) looks like it should be working, though it seems like it's using /dev/hdd instead of the /dev/scd0 in fstab.  At the very least, it's not triggering any error messages...  Try "sudo mount -t iso9660 /dev/hdd" after inserting a disk in that drive.  If that works, open fstab with "gksu gedit /etc/fstab" and change "/dev/scd0" to "/dev/hdd".

As for your dvd-rw drive (HP DVD Writer 740b), you're definitely having a problem of some sort, but not one that I'm able to accurately diagnose.  Those "lost interrupt" messages tend to mean either bad hardware or a bad driver, but could mean a lot of other things besides.  Hopefully one of the dev-level members will pop in and be able to help...

:frown:

I don't think that it's a hardware issue, as I was able to use both just a couple of days ago on windows. Is there somewhere I could try to reinstall the driver? would that help?

---

### Post by Dan6 on 2008-08-23
also I can boot the live cd from the drive I'm trying to use if that helps at all

---

### Post by Dan6 on 2008-08-23
anyone?

---

### Post by Dan6 on 2008-08-23
help?

---

### Post by leepesjee on 2008-08-23
Did you try mb_webguy's advize?

"sudo mount -t iso9660 /dev/hdd" after inserting a disk in that drive. If that works, open fstab with "gksu gedit /etc/fstab" and change "/dev/scd0" to "/dev/hdd".

That seems sensible. If it does not work, what's the output of the mount command?

---

### Post by Dan6 on 2008-08-23
yah but it doesn't seem to work the output is this:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by leepesjee on 2008-08-23
ah, it's a dvd drive isn't it, try:

"sudo mount -t udf,iso9660 /dev/hdd"

---

### Post by Dan6 on 2008-08-23
supposed to be cd/dvd the output seems the same
[sudo] password for dan: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by leepesjee on 2008-08-23
Hm, this seems tot be a standard error message. Apparently there's still something wrong with the device file. Do you have Device Manager installed?
If so, could you try to find the optical drives, and report what's in the Device File: fields.

---

### Post by Dan6 on 2008-08-23
I don't see optical drives in the window what would they normally be under?

---

### Post by leepesjee on 2008-08-23
It should be somewhere under under IDE controller.

---

### Post by Dan6 on 2008-08-23
What should I do now?

---

### Post by mb_webguy on 2008-08-23
*slaps self*  The reason that mount command isn't working is that I accidentally left off the mount point...  

Try "sudo mount -t iso9660 /dev/hdd /media/cdrom1".

---

### Post by Dan6 on 2008-08-23
under IDE controller says IDE device (master), IDE device (slave)
in each I have summary, properties.
Summary of IDE device (master) says:
Model: IDE device (master)
subsytem: ide
properties says:
Key                Type    value
ide.channel        int32   0 (0x0)
ide.host           int32   1 (0x1)
info.linux.driver  string  ide-cdrom
info.parent        string /org/freedesktop/Hal/devices/pci_1002_4376
info.product       string  IDE device (master)
info.subsytem      string  ide
info.udi           string /org/freedesktop/hal/devices/pci_1002_4376_ide_1_0
linux.hotplug_type int32  2(0x2)
linux.subsystem    string ide
linux.sysfs_path   string /sys/devices/pcis0000:00/0000:00:14.1/ide/1.0
I'll post slave next, sorry I took so long I didn't see your post

---

### Post by Dan6 on 2008-08-23
> **mb_webguy said:**
> *slaps self*  The reason that mount command isn't working is that I accidentally left off the mount point...  

Try "sudo mount -t iso9660 /dev/hdd /media/cdrom1".

still says 
dan@Dans:~$ sudo mount -t iso9660 /dev/hdd /media/cdrom1
mount: special device /dev/hdd does not exist

---

### Post by Dan6 on 2008-08-23
summary of IDE device (slave)
model: IDE device (slave)
subsytem: ide

properties:
Key                Type     Value
ide.channel        int32    1(0x1)
ide.host           int32    1(0x1)
info.parent        string    /org/freedesktop/hal/devices/pci_1002_4376
info.product       string   IDE device (slave)
info.subsystem     string    ide
info.udi           string   /org/freedesktop/Hal/devices/pci_1002_4376_ide_1_1
linux.hotplug_type  int32   2(0x2)
linux.subsytem      string   ide
linux.sysfs_path     string  sys/devices/pci0000:00/0000:00:14.1/ide1/1.1

---

### Post by leepesjee on 2008-08-23
This is from the controller itself. Somewhere (on the left pane of Device Manager) there should be a device listed under 'IDE Controller' which is your dvd-drive. You might have to dig a few leves deep. Mine is under 'IDE Controller' - 'SCSI Host Adapater' - 'SCSI Device' - 'Optical Drive'
When you click the drive you should find on right pane the under the Summary tab the field 'Device file'. That's what we need.

---

### Post by Dan6 on 2008-08-23
I have scsi device-scsi generic interface which doesn't have device file
and underneath that is mass storage drive whish lists 1.0kb volume
5.6GB volume
227.3GB volume

---

### Post by leepesjee on 2008-08-23
Well, if your drives are not listed in the Device Manager somewhere, than the kernel hasn't been able to connect to them. The kernel messages have to be reviewed then, to see if there's any clue.

---

### Post by Dan6 on 2008-08-23
so what should I do now

---

### Post by Dan6 on 2008-08-23
anyone?

---

### Post by Dan6 on 2008-08-23
help?

---

### Post by leepesjee on 2008-08-24
> *slaps self* The reason that mount command isn't working is that I accidentally left off the mount point... 
Another *slap* here. I completely overlooked that. However it appears not be the problem. The "hdc: lost interrupt" seems to be related. There's no error message about hdd, that's strange. Could it be something with master/slave settings? A half-loose connector or something?
Just a few guesses. I'am afraid I can't help you any further. You can try to repost, with the part of the kernel-messages concerning hdc/hdd. Maybe there's some kernel-hacker around that can help you.
Leo.

---

### Post by Dan6 on 2008-08-24
Ok thanks for your help anyway.

---

