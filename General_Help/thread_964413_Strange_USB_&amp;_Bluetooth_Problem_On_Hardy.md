---
title: "Strange USB &amp; Bluetooth Problem On Hardy"
date: 2008-10-30
forum: General Help
---

### Post by Suhendri on 2008-10-30
Since migrated from 7.04 to 8.04, i have problem with USB ports and Bluetooth ([USB & Bluetooth Problem...]("http://ubuntuforums.org/showthread.php?t=888401").)

Last week i tried to plug-in the USB Flash Disk to my notebook and its WORK..:-\" after that i tried to activated bluetooth and it WORK too..:guitar:

I don't know precisely since when both adapters running well on my Laptop. Because since i have problems with that devices (please take a look at my previous thread), i  never used that both devices.

This is a one Amazing week.. 8-)

If there are the system updates, i applied that updates. Maybe that updates fixed my devices problem..

And the latest applied system updates on October 28, output from dpkg.log on that time:
```

2008-10-28 20:34:27 startup archives unpack
2008-10-28 20:34:49 upgrade linux-image-2.6.24-21-generic 2.6.24-21.42 2.6.24-21.43
2008-10-28 20:34:49 status half-configured linux-image-2.6.24-21-generic 2.6.24-21.42
2008-10-28 20:34:49 status unpacked linux-image-2.6.24-21-generic 2.6.24-21.42
2008-10-28 20:34:49 status half-installed linux-image-2.6.24-21-generic 2.6.24-21.42
2008-10-28 20:35:01 status half-installed linux-image-2.6.24-21-generic 2.6.24-21.42
2008-10-28 20:35:07 status unpacked linux-image-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:35:09 status unpacked linux-image-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:35:09 upgrade wine 1.1.6~winehq0~ubuntu~8.04-0ubuntu1 1.1.7~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:35:09 status half-configured wine 1.1.6~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:35:09 status unpacked wine 1.1.6~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:35:09 status half-installed wine 1.1.6~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:35:13 status half-installed wine 1.1.6~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:35:17 status unpacked wine 1.1.7~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:35:21 status unpacked wine 1.1.7~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:35:21 upgrade tzdata-java 2008h-0ubuntu0.8.04 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:21 status half-configured tzdata-java 2008h-0ubuntu0.8.04
2008-10-28 20:35:21 status unpacked tzdata-java 2008h-0ubuntu0.8.04
2008-10-28 20:35:21 status half-installed tzdata-java 2008h-0ubuntu0.8.04
2008-10-28 20:35:22 status half-installed tzdata-java 2008h-0ubuntu0.8.04
2008-10-28 20:35:22 status unpacked tzdata-java 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:22 status unpacked tzdata-java 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:22 upgrade tzdata 2008h-0ubuntu0.8.04 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:22 status half-configured tzdata 2008h-0ubuntu0.8.04
2008-10-28 20:35:22 status unpacked tzdata 2008h-0ubuntu0.8.04
2008-10-28 20:35:22 status half-installed tzdata 2008h-0ubuntu0.8.04
2008-10-28 20:35:23 status half-installed tzdata 2008h-0ubuntu0.8.04
2008-10-28 20:35:23 status unpacked tzdata 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:23 status unpacked tzdata 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:24 startup packages configure
2008-10-28 20:35:24 configure tzdata 2008h-0ubuntu0.8.04.1 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:24 status unpacked tzdata 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:24 status half-configured tzdata 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:27 status installed tzdata 2008h-0ubuntu0.8.04.1
2008-10-28 20:35:28 startup archives unpack
2008-10-28 20:35:37 upgrade xkb-data 1.1~cvs.20080104.1-1ubuntu6 1.1~cvs.20080104.1-1ubuntu8
2008-10-28 20:35:37 status half-configured xkb-data 1.1~cvs.20080104.1-1ubuntu6
2008-10-28 20:35:38 status unpacked xkb-data 1.1~cvs.20080104.1-1ubuntu6
2008-10-28 20:35:38 status half-installed xkb-data 1.1~cvs.20080104.1-1ubuntu6
2008-10-28 20:35:38 status half-installed xkb-data 1.1~cvs.20080104.1-1ubuntu6
2008-10-28 20:35:38 status unpacked xkb-data 1.1~cvs.20080104.1-1ubuntu8
2008-10-28 20:35:38 status unpacked xkb-data 1.1~cvs.20080104.1-1ubuntu8
2008-10-28 20:35:38 upgrade gstreamer0.10-plugins-bad 0.10.6-5 0.10.6-5ubuntu0.1
2008-10-28 20:35:38 status half-configured gstreamer0.10-plugins-bad 0.10.6-5
2008-10-28 20:35:38 status unpacked gstreamer0.10-plugins-bad 0.10.6-5
2008-10-28 20:35:38 status half-installed gstreamer0.10-plugins-bad 0.10.6-5
2008-10-28 20:35:39 status half-installed gstreamer0.10-plugins-bad 0.10.6-5
2008-10-28 20:35:39 status unpacked gstreamer0.10-plugins-bad 0.10.6-5ubuntu0.1
2008-10-28 20:35:39 status unpacked gstreamer0.10-plugins-bad 0.10.6-5ubuntu0.1
2008-10-28 20:35:40 upgrade libgtk2.0-common 2.12.9-3ubuntu4 2.12.9-3ubuntu5
2008-10-28 20:35:40 status half-configured libgtk2.0-common 2.12.9-3ubuntu4
2008-10-28 20:35:40 status unpacked libgtk2.0-common 2.12.9-3ubuntu4
2008-10-28 20:35:40 status half-installed libgtk2.0-common 2.12.9-3ubuntu4
2008-10-28 20:35:40 status half-installed libgtk2.0-common 2.12.9-3ubuntu4
2008-10-28 20:35:40 status unpacked libgtk2.0-common 2.12.9-3ubuntu5
2008-10-28 20:35:40 status unpacked libgtk2.0-common 2.12.9-3ubuntu5
2008-10-28 20:35:40 upgrade gtk2-engines-pixbuf 2.12.9-3ubuntu4 2.12.9-3ubuntu5
2008-10-28 20:35:40 status half-configured gtk2-engines-pixbuf 2.12.9-3ubuntu4
2008-10-28 20:35:40 status unpacked gtk2-engines-pixbuf 2.12.9-3ubuntu4
2008-10-28 20:35:40 status half-installed gtk2-engines-pixbuf 2.12.9-3ubuntu4
2008-10-28 20:35:40 status half-installed gtk2-engines-pixbuf 2.12.9-3ubuntu4
2008-10-28 20:35:40 status unpacked gtk2-engines-pixbuf 2.12.9-3ubuntu5
2008-10-28 20:35:40 status unpacked gtk2-engines-pixbuf 2.12.9-3ubuntu5
2008-10-28 20:35:41 upgrade libgtk2.0-0 2.12.9-3ubuntu4 2.12.9-3ubuntu5
2008-10-28 20:35:41 status half-configured libgtk2.0-0 2.12.9-3ubuntu4
2008-10-28 20:35:41 status unpacked libgtk2.0-0 2.12.9-3ubuntu4
2008-10-28 20:35:41 status half-installed libgtk2.0-0 2.12.9-3ubuntu4
2008-10-28 20:35:41 status half-installed libgtk2.0-0 2.12.9-3ubuntu4
2008-10-28 20:35:41 status unpacked libgtk2.0-0 2.12.9-3ubuntu5
2008-10-28 20:35:41 status unpacked libgtk2.0-0 2.12.9-3ubuntu5
2008-10-28 20:35:41 upgrade libgtk2.0-bin 2.12.9-3ubuntu4 2.12.9-3ubuntu5
2008-10-28 20:35:41 status half-configured libgtk2.0-bin 2.12.9-3ubuntu4
2008-10-28 20:35:42 status unpacked libgtk2.0-bin 2.12.9-3ubuntu4
2008-10-28 20:35:42 status half-installed libgtk2.0-bin 2.12.9-3ubuntu4
2008-10-28 20:35:42 status half-installed libgtk2.0-bin 2.12.9-3ubuntu4
2008-10-28 20:35:42 status unpacked libgtk2.0-bin 2.12.9-3ubuntu5
2008-10-28 20:35:42 status unpacked libgtk2.0-bin 2.12.9-3ubuntu5
2008-10-28 20:35:42 upgrade linux-headers-2.6.24-21 2.6.24-21.42 2.6.24-21.43
2008-10-28 20:35:42 status half-configured linux-headers-2.6.24-21 2.6.24-21.42
2008-10-28 20:35:42 status unpacked linux-headers-2.6.24-21 2.6.24-21.42
2008-10-28 20:35:42 status half-installed linux-headers-2.6.24-21 2.6.24-21.42
2008-10-28 20:35:56 status half-installed linux-headers-2.6.24-21 2.6.24-21.42
2008-10-28 20:35:59 status unpacked linux-headers-2.6.24-21 2.6.24-21.43
2008-10-28 20:36:00 status unpacked linux-headers-2.6.24-21 2.6.24-21.43
2008-10-28 20:36:01 upgrade linux-headers-2.6.24-21-generic 2.6.24-21.42 2.6.24-21.43
2008-10-28 20:36:01 status half-configured linux-headers-2.6.24-21-generic 2.6.24-21.42
2008-10-28 20:36:01 status unpacked linux-headers-2.6.24-21-generic 2.6.24-21.42
2008-10-28 20:36:01 status half-installed linux-headers-2.6.24-21-generic 2.6.24-21.42
2008-10-28 20:36:02 status half-installed linux-headers-2.6.24-21-generic 2.6.24-21.42
2008-10-28 20:36:03 status unpacked linux-headers-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:36:03 status unpacked linux-headers-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:36:03 upgrade linux-libc-dev 2.6.24-21.42 2.6.24-21.43
2008-10-28 20:36:03 status half-configured linux-libc-dev 2.6.24-21.42
2008-10-28 20:36:03 status unpacked linux-libc-dev 2.6.24-21.42
2008-10-28 20:36:03 status half-installed linux-libc-dev 2.6.24-21.42
2008-10-28 20:36:04 status half-installed linux-libc-dev 2.6.24-21.42
2008-10-28 20:36:04 status unpacked linux-libc-dev 2.6.24-21.43
2008-10-28 20:36:04 status unpacked linux-libc-dev 2.6.24-21.43
2008-10-28 20:36:04 upgrade thunderbird-locale-en-gb 1:2.0.0.0+1-0ubuntu1 1:2.0.0.14+1-0ubuntu1~8.04.1
2008-10-28 20:36:04 status half-configured thunderbird-locale-en-gb 1:2.0.0.0+1-0ubuntu1
2008-10-28 20:36:04 status unpacked thunderbird-locale-en-gb 1:2.0.0.0+1-0ubuntu1
2008-10-28 20:36:04 status half-installed thunderbird-locale-en-gb 1:2.0.0.0+1-0ubuntu1
2008-10-28 20:36:04 status half-installed thunderbird-locale-en-gb 1:2.0.0.0+1-0ubuntu1
2008-10-28 20:36:04 status unpacked thunderbird-locale-en-gb 1:2.0.0.14+1-0ubuntu1~8.04.1
2008-10-28 20:36:04 status unpacked thunderbird-locale-en-gb 1:2.0.0.14+1-0ubuntu1~8.04.1
2008-10-28 20:36:05 startup packages configure
2008-10-28 20:36:05 configure linux-image-2.6.24-21-generic 2.6.24-21.43 2.6.24-21.43
2008-10-28 20:36:05 status unpacked linux-image-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:36:05 status half-configured linux-image-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:36:43 status installed linux-image-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:36:43 configure wine 1.1.7~winehq0~ubuntu~8.04-0ubuntu1 1.1.7~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:36:43 status unpacked wine 1.1.7~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:36:43 status unpacked wine 1.1.7~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:36:43 status half-configured wine 1.1.7~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:36:46 status installed wine 1.1.7~winehq0~ubuntu~8.04-0ubuntu1
2008-10-28 20:36:46 status triggers-pending libc6 2.7-10ubuntu4
2008-10-28 20:36:46 configure tzdata-java 2008h-0ubuntu0.8.04.1 2008h-0ubuntu0.8.04.1
2008-10-28 20:36:46 status unpacked tzdata-java 2008h-0ubuntu0.8.04.1
2008-10-28 20:36:46 status half-configured tzdata-java 2008h-0ubuntu0.8.04.1
2008-10-28 20:36:46 status installed tzdata-java 2008h-0ubuntu0.8.04.1
2008-10-28 20:36:46 configure xkb-data 1.1~cvs.20080104.1-1ubuntu8 1.1~cvs.20080104.1-1ubuntu8
2008-10-28 20:36:46 status unpacked xkb-data 1.1~cvs.20080104.1-1ubuntu8
2008-10-28 20:36:46 status unpacked xkb-data 1.1~cvs.20080104.1-1ubuntu8
2008-10-28 20:36:46 status half-configured xkb-data 1.1~cvs.20080104.1-1ubuntu8
2008-10-28 20:36:46 status installed xkb-data 1.1~cvs.20080104.1-1ubuntu8
2008-10-28 20:36:46 configure gstreamer0.10-plugins-bad 0.10.6-5ubuntu0.1 0.10.6-5ubuntu0.1
2008-10-28 20:36:46 status unpacked gstreamer0.10-plugins-bad 0.10.6-5ubuntu0.1
2008-10-28 20:36:46 status half-configured gstreamer0.10-plugins-bad 0.10.6-5ubuntu0.1
2008-10-28 20:36:46 status installed gstreamer0.10-plugins-bad 0.10.6-5ubuntu0.1
2008-10-28 20:36:46 configure libgtk2.0-common 2.12.9-3ubuntu5 2.12.9-3ubuntu5
2008-10-28 20:36:46 status unpacked libgtk2.0-common 2.12.9-3ubuntu5
2008-10-28 20:36:46 status half-configured libgtk2.0-common 2.12.9-3ubuntu5
2008-10-28 20:36:46 status installed libgtk2.0-common 2.12.9-3ubuntu5
2008-10-28 20:36:46 configure libgtk2.0-0 2.12.9-3ubuntu5 2.12.9-3ubuntu5
2008-10-28 20:36:46 status unpacked libgtk2.0-0 2.12.9-3ubuntu5
2008-10-28 20:36:46 status unpacked libgtk2.0-0 2.12.9-3ubuntu5
2008-10-28 20:36:46 status half-configured libgtk2.0-0 2.12.9-3ubuntu5
2008-10-28 20:36:46 status installed libgtk2.0-0 2.12.9-3ubuntu5
2008-10-28 20:36:46 configure gtk2-engines-pixbuf 2.12.9-3ubuntu5 2.12.9-3ubuntu5
2008-10-28 20:36:46 status unpacked gtk2-engines-pixbuf 2.12.9-3ubuntu5
2008-10-28 20:36:46 status half-configured gtk2-engines-pixbuf 2.12.9-3ubuntu5
2008-10-28 20:36:46 status installed gtk2-engines-pixbuf 2.12.9-3ubuntu5
2008-10-28 20:36:46 configure libgtk2.0-bin 2.12.9-3ubuntu5 2.12.9-3ubuntu5
2008-10-28 20:36:46 status unpacked libgtk2.0-bin 2.12.9-3ubuntu5
2008-10-28 20:36:46 status half-configured libgtk2.0-bin 2.12.9-3ubuntu5
2008-10-28 20:36:46 status installed libgtk2.0-bin 2.12.9-3ubuntu5
2008-10-28 20:36:46 configure linux-headers-2.6.24-21 2.6.24-21.43 2.6.24-21.43
2008-10-28 20:36:46 status unpacked linux-headers-2.6.24-21 2.6.24-21.43
2008-10-28 20:36:46 status half-configured linux-headers-2.6.24-21 2.6.24-21.43
2008-10-28 20:36:46 status installed linux-headers-2.6.24-21 2.6.24-21.43
2008-10-28 20:36:46 configure linux-headers-2.6.24-21-generic 2.6.24-21.43 2.6.24-21.43
2008-10-28 20:36:46 status unpacked linux-headers-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:36:46 status half-configured linux-headers-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:36:46 status installed linux-headers-2.6.24-21-generic 2.6.24-21.43
2008-10-28 20:36:46 configure linux-libc-dev 2.6.24-21.43 2.6.24-21.43
2008-10-28 20:36:46 status unpacked linux-libc-dev 2.6.24-21.43
2008-10-28 20:36:46 status half-configured linux-libc-dev 2.6.24-21.43
2008-10-28 20:36:46 status installed linux-libc-dev 2.6.24-21.43
2008-10-28 20:36:46 configure thunderbird-locale-en-gb 1:2.0.0.14+1-0ubuntu1~8.04.1 1:2.0.0.14+1-0ubuntu1~8.04.1
2008-10-28 20:36:46 status unpacked thunderbird-locale-en-gb 1:2.0.0.14+1-0ubuntu1~8.04.1
2008-10-28 20:36:46 status half-configured thunderbird-locale-en-gb 1:2.0.0.14+1-0ubuntu1~8.04.1
2008-10-28 20:36:46 status installed thunderbird-locale-en-gb 1:2.0.0.14+1-0ubuntu1~8.04.1
2008-10-28 20:36:46 trigproc libc6 2.7-10ubuntu4 2.7-10ubuntu4
2008-10-28 20:36:46 status half-configured libc6 2.7-10ubuntu4
2008-10-28 20:36:47 status installed libc6 2.7-10ubuntu4
2008-10-28 20:41:28 startup archives unpack
2008-10-28 20:41:48 upgrade rhino 1.6.R7-2 1.6.R7-2ubuntu1
2008-10-28 20:41:48 status half-configured rhino 1.6.R7-2
2008-10-28 20:41:48 status unpacked rhino 1.6.R7-2
2008-10-28 20:41:48 status half-installed rhino 1.6.R7-2
2008-10-28 20:41:48 status half-installed rhino 1.6.R7-2
2008-10-28 20:41:48 status unpacked rhino 1.6.R7-2ubuntu1
2008-10-28 20:41:48 status unpacked rhino 1.6.R7-2ubuntu1
2008-10-28 20:41:48 upgrade system-config-samba 1.2.50-0ubuntu2 1.2.50-0ubuntu2.2
2008-10-28 20:41:48 status half-configured system-config-samba 1.2.50-0ubuntu2
2008-10-28 20:41:50 status unpacked system-config-samba 1.2.50-0ubuntu2
2008-10-28 20:41:50 status half-installed system-config-samba 1.2.50-0ubuntu2
2008-10-28 20:41:50 status half-installed system-config-samba 1.2.50-0ubuntu2
2008-10-28 20:41:50 status unpacked system-config-samba 1.2.50-0ubuntu2.2
2008-10-28 20:41:51 status unpacked system-config-samba 1.2.50-0ubuntu2.2
2008-10-28 20:41:52 startup packages configure
2008-10-28 20:41:52 configure rhino 1.6.R7-2ubuntu1 1.6.R7-2ubuntu1
2008-10-28 20:41:52 status unpacked rhino 1.6.R7-2ubuntu1
2008-10-28 20:41:52 status half-configured rhino 1.6.R7-2ubuntu1
2008-10-28 20:41:52 status installed rhino 1.6.R7-2ubuntu1
2008-10-28 20:41:52 configure system-config-samba 1.2.50-0ubuntu2.2 1.2.50-0ubuntu2.2
2008-10-28 20:41:52 status unpacked system-config-samba 1.2.50-0ubuntu2.2
2008-10-28 20:41:52 status half-configured system-config-samba 1.2.50-0ubuntu2.2
2008-10-28 20:41:57 status installed system-config-samba 1.2.50-0ubuntu2.2

```

After applied that system updates, USB & Bluetooth devices are back to the first stage, NOT WORKING...](*,):cry:[-(

I thought the applied updated cause the devices NOT WORKING...

output from lsusb
```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```
At home, i have desktop using 8.04. On that desktop the usb devices working properly. I alse applied all system updates to my desktop.

From now on i dont know what i have to do to make that devices working properly on my laptop... :cry:

Please help me...[-o<

---

### Post by Suhendri on 2008-11-02
Any body can solve my problem ](*,)

---

### Post by Suhendri on 2008-11-20
Please...
any one can help and solve my problem...](*,)

---

