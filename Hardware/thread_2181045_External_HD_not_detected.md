---
title: "External HD not detected"
date: 2013-10-16
forum: Hardware
---

### Post by thedoctor818772 on 2013-10-16
I am running Ubuntu 13.10 beta, and have a Toshiba 1.0 TB external HD. Lately (even sometimes under 13,04) but now all the time under 13,10, I have never been able to get my linux box to be able to detect the HD. 

sudo fdisk -l    gives the following:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b9283

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   620972031   310484992   83  Linux
/dev/sda2       620974078   625141759     2083841    5  Extended
/dev/sda5       620974080   625141759     2083840   82  Linux swap / Solaris


I am uncertain as to what to do next. Any help is most welcome. I have tried different cables, and all of my usb flash drives are recognized just fine. Thanks!

The result of  dmseg | tail is :

[   27.699619] type=1400 audit(1381879631.895:15): apparmor="STATUS" operation="profile_load" parent=803 profile="unconfined" name="chromium_browser" pid=809 comm="apparmor_parser"
[   27.699832] type=1400 audit(1381879631.895:16): apparmor="STATUS" operation="profile_replace" parent=803 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=811 comm="apparmor_parser"
[   27.699865] type=1400 audit(1381879631.895:17): apparmor="STATUS" operation="profile_replace" parent=803 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=811 comm="apparmor_parser"
[   27.700416] type=1400 audit(1381879631.899:18): apparmor="STATUS" operation="profile_load" parent=803 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=810 comm="apparmor_parser"
[   27.700447] type=1400 audit(1381879631.899:19): apparmor="STATUS" operation="profile_load" parent=803 profile="unconfined" name="chromium_browser" pid=810 comm="apparmor_parser"
[   27.701664] type=1400 audit(1381879631.899:20): apparmor="STATUS" operation="profile_replace" parent=803 profile="unconfined" name="chromium_browser" pid=809 comm="apparmor_parser"
[  279.952796] perf samples too long (2513 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 1698.307002] perf samples too long (5009 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 2949.480926] systemd-hostnamed[4098]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3266.374008] perf samples too long (10060 > 10000), lowering kernel.perf_event_max_sample_rate to 12500

---

### Post by sudodus on 2013-10-16
Welcome to the Ubuntu Forums :-)

I am testing Lubuntu Saucy, and I have used the beta 1 and beta 2, but I have not had that problem. And I have a Toshiba USB3 320 GB HDD.

- What kind of drive is it? USB 2,3 or eSATA?
- Is it recognized by a live system (if you boot from an Ubuntu install CD/DVD/USB drive)?
- Have you tried all ports (if more than one are available)?
- Is it recognized by another computer?

---

### Post by inariays on 2013-10-25
i have the same problem..can't detect all the usb devices. it can be detected in lsusb but not at fdisk and cant be mounted
```

root@pnqiu:~# lsusb
Bus 002 Device 004: ID 0411:01e7 BUFFALO INC. (formerly MelCo., Inc.) 
Bus 002 Device 003: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@pnqiu:~# fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046a7b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   617164799   308581376   83  Linux
/dev/sda2       617166846   625141759     3987457    5  Extended
/dev/sda5       617166848   625141759     3987456   82  Linux swap / Solaris

```



the buffalo is my external and alcor is my usb thumbdrive...it can be detected in live cd(i used usb though)..both on usb 2...

---

### Post by sudodus on 2013-10-28
> **inariays said:**
> i have the same problem..can't detect all the usb devices. it can be detected in lsusb but not at fdisk and cant be mounted
```

root@pnqiu:~# lsusb
Bus 002 Device 004: ID 0411:01e7 BUFFALO INC. (formerly MelCo., Inc.) 
Bus 002 Device 003: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@pnqiu:~# fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046a7b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   617164799   308581376   83  Linux
/dev/sda2       617166846   625141759     3987457    5  Extended
/dev/sda5       617166848   625141759     3987456   82  Linux swap / Solaris

```



the buffalo is my external and alcor is my usb thumbdrive...it can be detected in live cd(i used usb though)..both on usb 2...

Which version and flavour of Ubuntu are *you* running? Please reply to the questions in post #2!

---

