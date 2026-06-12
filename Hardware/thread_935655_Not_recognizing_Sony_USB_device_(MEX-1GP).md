---
title: "Not recognizing Sony USB device (MEX-1GP)?"
date: 2008-10-01
forum: Hardware
---

### Post by perryrt on 2008-10-01
So I recently bought this used car.... a 1997 Honda Civic. It's got an aftermarket Sony stereo in it - a MEX-1GP. Neat feature to this radio is that it's got a 1G MP3 player built in - all you do is remove the faceplace, take it inside and plug it into the computer and download MP3's to it. No software to install.

Windows recognizes it as a mass storage drive and mounts it no problem. Drag and drop. 

Not so much with Ubuntu.

When plugged in, there's a little LED on the unit that in Windows flashes when accessed. In Ubuntu it flashes every 30 seconds more or less.

This kind makes sense.... here's what /var/log/syslog shows:

```
Oct  1 20:34:19 dell-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct  1 20:34:19 dell-desktop anacron[5707]: Job `cron.daily' terminated (mailing output)
Oct  1 20:34:19 dell-desktop anacron[5707]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Oct  1 20:34:19 dell-desktop anacron[5707]: Job `cron.weekly' started
Oct  1 20:34:19 dell-desktop anacron[7590]: Updated timestamp for job `cron.weekly' to 2008-10-01
Oct  1 20:34:21 dell-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct  1 20:34:21 dell-desktop anacron[5707]: Job `cron.weekly' terminated
Oct  1 20:34:21 dell-desktop anacron[5707]: Normal exit (2 jobs run)
Oct  1 20:50:20 dell-desktop -- MARK --
Oct  1 20:59:21 dell-desktop ntpd[6734]: synchronized to 199.212.17.21, stratum 2
Oct  1 20:59:24 dell-desktop ntpd[6734]: synchronized to 128.4.40.12, stratum 2
Oct  1 21:01:34 dell-desktop ntpd[6734]: synchronized to 199.212.17.21, stratum 2
Oct  1 21:07:58 dell-desktop kernel: [ 1143.519652] usb 4-1: new high speed USB device using ehci_hcd and address 3
Oct  1 21:08:23 dell-desktop kernel: [ 1153.254235] usb 4-1: new high speed USB device using ehci_hcd and address 4
Oct  1 21:08:53 dell-desktop kernel: [ 1164.916564] usb 4-1: new high speed USB device using ehci_hcd and address 5
Oct  1 21:09:23 dell-desktop kernel: [ 1174.440754] usb 4-1: new high speed USB device using ehci_hcd and address 6
Oct  1 21:09:53 dell-desktop kernel: [ 1189.628521] usb 4-1: new high speed USB device using ehci_hcd and address 7
Oct  1 21:10:23 dell-desktop kernel: [ 1206.211974] usb 4-1: new high speed USB device using ehci_hcd and address 8
Oct  1 21:10:53 dell-desktop kernel: [ 1218.663529] usb 4-1: new high speed USB device using ehci_hcd and address 9
Oct  1 21:11:23 dell-desktop kernel: [ 1231.464073] usb 4-1: new high speed USB device using ehci_hcd and address 10
Oct  1 21:11:53 dell-desktop kernel: [ 1244.041333] usb 4-1: new high speed USB device using ehci_hcd and address 11
Oct  1 21:12:23 dell-desktop kernel: [ 1255.203678] usb 4-1: new high speed USB device using ehci_hcd and address 12
Oct  1 21:12:53 dell-desktop kernel: [ 1263.765785] usb 4-1: new high speed USB device using ehci_hcd and address 13
Oct  1 21:17:01 dell-desktop /USR/SBIN/CRON[9293]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  1 21:22:55 dell-desktop kernel: [ 1530.181551] usb 4-2: new high speed USB device using ehci_hcd and address 14
Oct  1 21:23:23 dell-desktop kernel: [ 1541.745755] usb 4-2: new high speed USB device using ehci_hcd and address 15
Oct  1 21:23:35 dell-desktop kernel: [ 1546.692879] set_rtc_mmss: can't update from 4 to 53
Oct  1 21:23:53 dell-desktop kernel: [ 1553.273650] usb 4-2: new high speed USB device using ehci_hcd and address 16
Oct  1 21:24:23 dell-desktop kernel: [ 1566.294993] usb 4-2: new high speed USB device using ehci_hcd and address 17
Oct  1 21:24:53 dell-desktop kernel: [ 1575.997911] usb 4-2: new high speed USB device using ehci_hcd and address 18
Oct  1 21:25:05 dell-desktop ntpd[6734]: synchronized to 128.4.40.12, stratum 2
Oct  1 21:25:23 dell-desktop kernel: [ 1586.373902] usb 4-2: new high speed USB device using ehci_hcd and address 19
Oct  1 21:25:53 dell-desktop kernel: [ 1597.640991] usb 4-2: new high speed USB device using ehci_hcd and address 20
Oct  1 21:26:23 dell-desktop kernel: [ 1605.592089] usb 4-2: new high speed USB device using ehci_hcd and address 21
Oct  1 21:26:53 dell-desktop kernel: [ 1616.102810] usb 4-2: new high speed USB device using ehci_hcd and address 22
Oct  1 21:27:23 dell-desktop kernel: [ 1626.673941] usb 4-2: new high speed USB device using ehci_hcd and address 23
Oct  1 21:27:53 dell-desktop kernel: [ 1636.438930] usb 4-2: new high speed USB device using ehci_hcd and address 24
Oct  1 21:28:23 dell-desktop kernel: [ 1650.637691] usb 4-2: new high speed USB device using ehci_hcd and address 25
Oct  1 21:28:53 dell-desktop kernel: [ 1662.830478] usb 4-2: new high speed USB device using ehci_hcd and address 26
Oct  1 21:29:23 dell-desktop kernel: [ 1678.226119] usb 4-2: new high speed USB device using ehci_hcd and address 27
Oct  1 21:29:53 dell-desktop kernel: [ 1689.690898] usb 4-2: new high speed USB device using ehci_hcd and address 28
Oct  1 21:30:23 dell-desktop kernel: [ 1699.505195] usb 4-2: new high speed USB device using ehci_hcd and address 29
Oct  1 21:30:53 dell-desktop kernel: [ 1714.160388] usb 4-2: new high speed USB device using ehci_hcd and address 30
Oct  1 21:31:23 dell-desktop kernel: [ 1729.344037] usb 4-2: new high speed USB device using ehci_hcd and address 31
Oct  1 21:31:53 dell-desktop kernel: [ 1743.915343] usb 4-2: new high speed USB device using ehci_hcd and address 32
Oct  1 21:35:08 dell-desktop kernel: [ 1831.025468] usb 4-2: new high speed USB device using ehci_hcd and address 33
Oct  1 21:35:23 dell-desktop kernel: [ 1837.331954] usb 4-2: new high speed USB device using ehci_hcd and address 34
Oct  1 21:35:53 dell-desktop kernel: [ 1850.059980] usb 4-2: new high speed USB device using ehci_hcd and address 35
Oct  1 21:36:23 dell-desktop kernel: [ 1859.026714] usb 4-2: new high speed USB device using ehci_hcd and address 36
Oct  1 21:36:53 dell-desktop kernel: [ 1866.865586] usb 4-2: new high speed USB device using ehci_hcd and address 37
Oct  1 21:37:23 dell-desktop kernel: [ 1877.043846] usb 4-2: new high speed USB device using ehci_hcd and address 38
Oct  1 21:37:53 dell-desktop kernel: [ 1889.375538] usb 4-2: new high speed USB device using ehci_hcd and address 39
Oct  1 21:38:23 dell-desktop kernel: [ 1900.634568] usb 4-2: new high speed USB device using ehci_hcd and address 40
Oct  1 21:38:53 dell-desktop kernel: [ 1912.911494] usb 4-2: new high speed USB device using ehci_hcd and address 41
Oct  1 21:39:23 dell-desktop kernel: [ 1926.814676] usb 4-2: new high speed USB device using ehci_hcd and address 42
Oct  1 21:39:53 dell-desktop kernel: [ 1936.431905] usb 4-2: new high speed USB device using ehci_hcd and address 43
Oct  1 21:40:23 dell-desktop kernel: [ 1949.864155] usb 4-2: new high speed USB device using ehci_hcd and address 44
Oct  1 21:40:53 dell-desktop kernel: [ 1961.094321] usb 4-2: new high speed USB device using ehci_hcd and address 45
Oct  1 21:41:23 dell-desktop kernel: [ 1975.249390] usb 4-2: new high speed USB device using ehci_hcd and address 46
Oct  1 21:41:53 dell-desktop kernel: [ 1996.220843] usb 4-2: new high speed USB device using ehci_hcd and address 47
Oct  1 21:42:23 dell-desktop kernel: [ 2004.073494] usb 4-2: new high speed USB device using ehci_hcd and address 48
Oct  1 21:42:53 dell-desktop kernel: [ 2019.123832] usb 4-2: new high speed USB device using ehci_hcd and address 49
Oct  1 21:43:23 dell-desktop kernel: [ 2030.239414] usb 4-2: new high speed USB device using ehci_hcd and address 50
Oct  1 21:43:53 dell-desktop kernel: [ 2037.672270] usb 4-2: new high speed USB device using ehci_hcd and address 51
Oct  1 21:44:23 dell-desktop kernel: [ 2048.089907] usb 4-2: new high speed USB device using ehci_hcd and address 52
Oct  1 21:44:53 dell-desktop kernel: [ 2059.940216] usb 4-2: new high speed USB device using ehci_hcd and address 53
Oct  1 21:45:23 dell-desktop kernel: [ 2072.485169] usb 4-2: new high speed USB device using ehci_hcd and address 54
Oct  1 21:45:53 dell-desktop kernel: [ 2082.124019] usb 4-2: new high speed USB device using ehci_hcd and address 55
Oct  1 21:46:23 dell-desktop kernel: [ 2091.317117] usb 4-2: new high speed USB device using ehci_hcd and address 56
Oct  1 21:46:53 dell-desktop kernel: [ 2101.220622] usb 4-2: new high speed USB device using ehci_hcd and address 57
Oct  1 21:47:23 dell-desktop kernel: [ 2114.650228] usb 4-2: new high speed USB device using ehci_hcd and address 58
Oct  1 21:47:53 dell-desktop kernel: [ 2124.275676] usb 4-2: new high speed USB device using ehci_hcd and address 59
Oct  1 21:48:23 dell-desktop kernel: [ 2134.820441] usb 4-2: new high speed USB device using ehci_hcd and address 60
Oct  1 21:48:53 dell-desktop kernel: [ 2142.885771] usb 4-2: new high speed USB device using ehci_hcd and address 61
Oct  1 21:49:23 dell-desktop kernel: [ 2152.311963] usb 4-2: new high speed USB device using ehci_hcd and address 62
Oct  1 21:49:53 dell-desktop kernel: [ 2161.589296] usb 4-2: new high speed USB device using ehci_hcd and address 63
Oct  1 21:50:23 dell-desktop kernel: [ 2170.867002] usb 4-2: new high speed USB device using ehci_hcd and address 64
Oct  1 21:50:53 dell-desktop kernel: [ 2185.287452] usb 4-2: new high speed USB device using ehci_hcd and address 65
Oct  1 21:51:23 dell-desktop kernel: [ 2194.653483] usb 4-2: new high speed USB device using ehci_hcd and address 66
Oct  1 21:51:53 dell-desktop kernel: [ 2206.163162] usb 4-2: new high speed USB device using ehci_hcd and address 67
Oct  1 21:52:23 dell-desktop kernel: [ 2220.250765] usb 4-2: new high speed USB device using ehci_hcd and address 68
Oct  1 21:52:53 dell-desktop kernel: [ 2235.055823] usb 4-2: new high speed USB device using ehci_hcd and address 69
Oct  1 21:53:23 dell-desktop kernel: [ 2253.719465] usb 4-2: new high speed USB device using ehci_hcd and address 70
Oct  1 21:53:53 dell-desktop kernel: [ 2270.177696] usb 4-2: new high speed USB device using ehci_hcd and address 71
Oct  1 21:54:23 dell-desktop kernel: [ 2281.850563] usb 4-2: new high speed USB device using ehci_hcd and address 72
Oct  1 21:54:53 dell-desktop kernel: [ 2293.606468] usb 4-2: new high speed USB device using ehci_hcd and address 73
Oct  1 21:55:23 dell-desktop kernel: [ 2304.757817] usb 4-2: new high speed USB device using ehci_hcd and address 74
Oct  1 21:55:53 dell-desktop kernel: [ 2317.347561] usb 4-2: new high speed USB device using ehci_hcd and address 75
Oct  1 21:56:23 dell-desktop kernel: [ 2329.167805] usb 4-2: new high speed USB device using ehci_hcd and address 76
Oct  1 21:56:53 dell-desktop kernel: [ 2339.711302] usb 4-2: new high speed USB device using ehci_hcd and address 77
Oct  1 21:57:23 dell-desktop kernel: [ 2351.182235] usb 4-2: new high speed USB device using ehci_hcd and address 78
Oct  1 21:57:53 dell-desktop kernel: [ 2362.062801] usb 4-2: new high speed USB device using ehci_hcd and address 79
Oct  1 21:58:23 dell-desktop kernel: [ 2373.597704] usb 4-2: new high speed USB device using ehci_hcd and address 80
Oct  1 21:58:53 dell-desktop kernel: [ 2386.574118] usb 4-2: new high speed USB device using ehci_hcd and address 81
Oct  1 21:59:23 dell-desktop kernel: [ 2398.340842] usb 4-2: new high speed USB device using ehci_hcd and address 82
Oct  1 21:59:53 dell-desktop kernel: [ 2411.150220] usb 4-2: new high speed USB device using ehci_hcd and address 83
Oct  1 22:00:23 dell-desktop kernel: [ 2426.095204] usb 4-2: new high speed USB device using ehci_hcd and address 84
```


var/log/messages and /var/log/kern.log show the same entries.

fdisk shows nothing mounted:

```
perryrt@dell-desktop:~$ sudo fdisk -l
[sudo] password for perryrt: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e5731

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18704   150239848+  83  Linux
/dev/sda2           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
perryrt@dell-desktop:~$ 

```

and fstab doesn't show anything either....

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5902bc68-d145-46ae-a4fe-7f8c63574267 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=81586525-21dd-4a5a-9dcd-50f1f8f9a2a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Any ideas? Or is this just one of those "just not compatible with Linux" things? If so, pity. The closest I've gotten this to work is to connect the device to a windows computer on my home network, then grabbing the music from my Ubuntu machine via the network.

---

### Post by DropEffect on 2008-10-02
This is strange.  If the stereo is just acting as a mass storage device there should be no reason why it isn't being detected.

---

### Post by perryrt on 2008-10-03
Yeah, I would agree. I've had some problems with USB drives before, but that was because they were the type that tried to install handling software (U3).

Anyone have an idea?

---

### Post by perryrt on 2008-10-04
Bump ... any ideas?

---

### Post by perryrt on 2008-10-06
Still nothing, huh?

---

