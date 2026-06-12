---
title: "Usb Automount not working when network cable disconnected (!?)"
date: 2008-08-01
forum: Hardware
---

### Post by Xian00 on 2008-08-01
Hello everybody, I'm trying to solve a problem with a laptop of a collegue.

The problem sounds strange: the laptop is configured for a network connection throught the ethernet card with a fixed IP address.

When the cable is connected everything just works fine.

When the laptop is switched on without connecting it to the ethernet cable, something wrong happens and I noticed at least two strange behaviours:

[LIST=1]
[*]automount does not work attaching any usb key to the laptop
[*]no battery/power icon appears on the tray icon, where it used to.
[/LIST]

I've tried to search for problems related to usb automount, but couldn't find anything useful...

I've watched dmesg logs, hal (verbose) output, udev output, but I didn't find anything strange.

I have to add that, while automount doesn't work, I can still manually mount each usb removable drive that is attached, so the problem is not that drive isn't detected.

I made logs while attaching a usb-key as described in the wiki page: [https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

Please notice also that the system is running Kubuntu (8.04 Hardy), so I have not any gnome-volume-manager, gconf-editor, etc...

Thanks in advance to anybody who will try to help me!

---

### Post by Xian00 on 2008-08-04
After lots of searching, reading and troubleshooting of many problems and bugs about automount, hal, udev, fstab, etc... I finally managed to solve the problem!!

Even if the problem was happening only when the network cable was disconnected, it wasn't depending on network... but it came out that a wrong entry about cdrom in fstab was causing every other automount to fail.

The entry was referring to cdrom as /dev/hdc, but is seems that now cdrom is /dev/scd0... anyway, after commenting out the line of /etc/fstab reguarding cdrom mount, now everything works ok!!

...and when I mean everything I mean: automount of cdrom, but also automount of usb removable keys and drives, battery power/icon, power management options (there were no "hibernate" and "suspend" icons on the "Logout" panel)...

I still wonder why this was only happening when the network cable wasn't connected... anyway I can mark the thread as solved ;)

---

### Post by pwabrahams on 2008-09-01
On my system (Kubuntu8.04, Acer laptop), the correct device for the CD drive is /dev/hda.  /dev/scd0 does not work.  And I have all of the problems: no USB automount, missing items in power management options.

---

### Post by Xian00 on 2008-09-01
Hi pwabrahams, I think you're right.
My collegue has just came back from holidays and he encountered again the same problem, so I marked the thread as unsolved again.

I made some check again today and I found that these problems occur only at first log-in to the system. If I log out and log in again (with the same user or another as well), everything seems to work well again, even if network cable is not connected.

I think that the problem could be with some daemon not loading completely at startup... but I still did not found which and why...

Xian

---

### Post by IntuitiveNipple on 2008-09-01
This *could* be related to failing name resolution of the local PC. Can you post the contents of:
[list]
[*] /etc/hosts
[*] /etc/resolv.conf
[*] /etc/fstab
[/list]
and the results of:
[code]
ls -l /dev/disk/by-path
[/list]

---

### Post by Xian00 on 2008-09-02
Hi IntuitiveNipple,
I made another test and found that if I boot the machine (disconnected from network) and wait a few minutes before logging in, then everything works fine. If I boot and immediately log in, I encounter the problem described.

Anyway, here are the files you asked for.
Thanks for your interest!
    Xian

==== /etc/hosts ====

```
127.0.0.1 localhost nb3
192.168.1.13 server

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

==== /etc/resolv.conf ====

```
nameserver 213.140.2.43
nameserver 213.140.2.49

```


==== /etc/fstab ====

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# Entry for /dev/sda1 (windows restore partition):
#UUID=06B63491B63482EB /media/sda1 ntfs-3g defaults,locale=it_IT.UTF-8 0 0

# Entry for /dev/sda3 (Ubuntu boot partition):
UUID=28e2f10a-29e8-40ab-b64b-8f36122c2151 / ext3 defaults,errors=remount-ro 0 1

# Entry for /dev/sda2 (/home/ partition)
/dev/sda2 /home ext3 defaults,errors=remount-ro 0 1

# Entry for /dev/sda5 (swap partition):
#UUID=613dadf3-f0ea-4a05-8d6c-aa8b9617f762 none swap sw 0 0
/dev/sda5 none swap sw 0 0

# Entry for CD/DVD-Recorder
#/dev/scd0 /media/cdrom0 udf,iso9660,user,noauto,exec 0 0

# Samba shares
//SERVER/transito /mnt/transito cifs auto,user,rw,ip=192.168.1.13,guest,nosetuids,noperm 0 0
//SERVER/server /mnt/server cifs auto,user,rw,ip=192.168.1.13,guest,nosetuids,noperm 0 0

```


==== ls -l /dev/disk/by-path ====

```

lrwxrwxrwx 1 root root 10 2008-09-02 10:58 pci-0000:00:0d.0-scsi-1:0:0:0 -> ../../scd0
lrwxrwxrwx 1 root root  9 2008-09-02 10:58 pci-0000:00:0e.0-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-09-02 10:58 pci-0000:00:0e.0-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-09-02 10:58 pci-0000:00:0e.0-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-09-02 10:58 pci-0000:00:0e.0-scsi-0:0:0:0-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-09-02 10:58 pci-0000:00:0e.0-scsi-0:0:0:0-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-09-02 10:58 pci-0000:00:0e.0-scsi-0:0:0:0-part5 -> ../../sda5

```

---

### Post by IntuitiveNipple on 2008-09-02
Here's the problem, in fstab:
```

# Samba shares
//SERVER/transito /mnt/transito cifs auto,user,rw,ip=192.168.1.13,guest,nosetuids,noperm 0 0
//SERVER/server /mnt/server cifs auto,user,rw,ip=192.168.1.13,guest,nosetuids,noperm 0 0

```
Both of those have the **auto** option so the system will attempt to mount them at start-up. If the network isn't available it won't be able to:
[list=a]
[*] resolve the names to IP addresses
[*] route to the IP addresses ( since there's no network connection)
[/list]
So there will be a long delay while the system waits and finally times out trying to reach them, and it'll do it twice.

---

### Post by Xian00 on 2008-09-02
Thanks IntuitiveNipple, but in the last weeks I already did tests commenting out the rows about samba shares, but the problem still occurs, so I think it is not related to this.

Anyway I just made this test again, to be sure that I'm not losing anything... but it doesn't work.

:(

---

### Post by IntuitiveNipple on 2008-09-02
> **Xian00 said:**
> Thanks IntuitiveNipple, but in the last weeks I already did tests commenting out the rows about samba shares, but the problem still occurs, so I think it is not related to this.

Anyway I just made this test again, to be sure that I'm not losing anything... but it doesn't work.

:(
These lines certainly aren't going to help since they require network and name resolution.

Have you started the PC without the splash-screen, and with "quiet" removed from the kernel command line?

If you do that you'll see everything that is happening including any clues in the messages, plus you'll see from the timestamps of the kernel messages where precisely the delay is occurring.

If you move/delete the current /var/log/kern.log and /var/log/daemon.log and immediately re-start the PC so those log files are recreated from empty, you'll also have a couple of log-files to use to analyse the issue.

---

### Post by IntuitiveNipple on 2008-09-02
From the debug logs attached to your first post in this thread, it shows the delay:
```

[   40.182149]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[   40.182157]  CIFS VFS: cifs_mount failed w/return code = -113
[   46.185321]  CIFS VFS: Error connecting to IPv4 socket. Aborting operation
[   46.185329]  CIFS VFS: cifs_mount failed w/return code = -113
[   46.610100] NET: Registered protocol family 10
[   46.610314] lo: Disabled Privacy Extensions
[   46.610752] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  155.689414] EXT3 FS on sda3, internal journal
[  155.779375] device-mapper: uevent: version 1.0.3

```
Look at the differences in those time-stamps as it errors on the CIFS connections. That PC has something configured DURING KERNEL BOOT to access the network.

---

### Post by Xian00 on 2008-09-02
> Have you started the PC without the splash-screen, and with "quiet" removed from the kernel command line?

Yes, but i didn't notice anything strange. No error.

> **IntuitiveNipple said:**
> From the debug logs attached to your first post in this thread, it shows the delay
...
Look at the differences in those time-stamps as it errors on the CIFS connections. That PC has something configured DURING KERNEL BOOT to access the network.

Yes, I think you're right. But I cannot find what exactly is trying to access the network during startup.
I'll do as you suggested, remove the line relative to samba (cifs) shares, delete the current /var/log/kern.log and /var/log/daemon.log and re-start the PC.

I'll keep you up to date ;)
Thanks!!!

---

### Post by IntuitiveNipple on 2008-09-02
Xian - an idea!

Is it possible that the mounts are being attempted early in the initrd image?

That would explain why your changes to /etc/fstab aren't having an effect. Looking at the timings it does look as if this is happening during initial boot from the initrd.

---

### Post by Xian00 on 2008-09-02
> **IntuitiveNipple said:**
> Xian - an idea!

Is it possible that the mounts are being attempted early in the initrd image?

That would explain why your changes to /etc/fstab aren't having an effect. Looking at the timings it does look as if this is happening during initial boot from the initrd.

Uh! I don't know... It would be really a strange behavior...

Anyway I cannot make any test because my collegue is using his laptop now. I planned to do more research during his lunch break.
I will post the logs after lunch...

Anyway... if it's initrd fault, how could I update the initrd image to make it aware of the new /etc/fstab?

---

### Post by Xian00 on 2008-09-02
Ok, I commented the lines about cifs shares in /etc/fstab, temporary moved kern.log and daemon.log, disconnected the network cable and rebooted the laptop.

Attached are the two logs (compressed).
I cannot notice anything really strange...

<thinking aloud>
The only thing I know related to automount, is HAL... and I see in the logs that NetworkManager calls the HAL daemon... maybe something fails in the process and hal hangs?
</thinking aloud>

...only thinking aloud... I have no clear evidence...

---

### Post by IntuitiveNipple on 2008-09-02
> **Xian00 said:**
> 
Attached are the two logs (compressed).
I cannot notice anything really strange...

Ok, let me look at them :)

---

### Post by IntuitiveNipple on 2008-09-02
This is interesting, from the daemon log:
```

Sep  2 13:47:54 nb3 avahi-daemon[5392]: Server startup complete. Host name is nb3.local. Local service cookie is 3739049207.
Sep  2 13:48:24 nb3 ntpdate[3517]: can't find host ntp.ubuntu.com 
Sep  2 13:48:24 nb3 ntpdate[3517]: no servers can be used, exiting

```
That delay corresponds with this from kern.log:
```

Sep  2 13:47:54 nb3 kernel: [   93.884986] ppdev: user-space parallel port driver
Sep  2 13:47:54 nb3 kernel: [   94.457208] audit(1220356074.672:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5427 profile="/usr/sbin/cupsd" namespace="default"
Sep  2 13:48:56 nb3 kernel: [  156.388480] Clocksource tsc unstable (delta = -206032246 ns)
Sep  2 13:49:00 nb3 kernel: [  157.659491] Bluetooth: Core ver 2.11

```
Look at the time-delays between the log messages. The culprit is there somewhere.

It looks as if one of two things, or a combination of both, is causing this.

ntpdate is running to sync the time and is timing out due to lack of network connectivity (can't find ntp.ubuntu.com). This is weird since comparing that to the daemon.log on this PC shows ntpd, the server-service runs, but not the client-tool ntpdate. That is worth investigating.

The other possibility is the failure reported in kern.log for the cupds access to the printer. This is revealing since in Hardy there is a new security mechanism, AppArmor, and there are several well-known issues with it refusing permissions for printers.

Does the PC have a printer connected when it starts? If so, try disconnecting it. Also, try disabling the Printer service (cupsys) and reboot.

---

### Post by Xian00 on 2008-09-02
> **IntuitiveNipple said:**
> This is interesting, The other possibility is the failure reported in kern.log for the cupds access to the printer. This is revealing since in Hardy the new security mechanism, AppArmor, and there are several well-known issues with it refusing permissions for printers.

Does the PC have a printer connected when it starts? If so, try disconnecting it. Also, try disabling the Printer service (cupsys) and reboot.

Hey, you're right!
There are two network printers configured... I didn't think about that!
Maybe the system is searching for printers and doesn't find them...

You gave me some more thing to investigate on.

The difficult thing with these issues is that I cannot make every test I want to do, because my collegue needs the laptop to work. :-)

Tomorrow morning will be the right moment for a deeper research.

Thank you, TJ!

---

### Post by Xian00 on 2008-09-04
No good news.
I think I've tried almost everything:

[LIST]
[*]removed from /etc/fstab lines for automounting samba (cifs) network shares
[*]disabled ntpdate synchronization commenting servers in /etc/default/ntpdate, plus added additional options for debug and 1 second timeout (NTPOPTIONS="-d -t 1")
[*]disabled starting of cups deamon on boot
[*]added at boot time kernel option "notsc" for delay caused by problem related to "Clocksource tsc unstable"
[*]removed every script in /etc/network/if-up.d/
[*]disabled starting of samba daemon and dhcdbd on boot
[/LIST]
The only thing working is disabling the network interface from coming up on boot commenting the option "auto eth0" in /etc/network/interfaces.
But obviously this is not a nice solution, because most of the times the machine is in the office and attached to the network, and one should connect manually to the network every time.

Anyone has a better idea?

I think that the first work-around - waiting one minute after booting, before logging in - is the easiest ...and one minute spent waiting, from time to time, is not worth hours spent in deeper investigation...

---

### Post by IntuitiveNipple on 2008-09-04
Are you still seeing those delays in the kernel timestamps? If so, post a new daemon.log taken with "quiet splash" removed from the kernel command-line and, presumably, all those changes you mention still in place.

That delay was 30 seconds precisely. If it is the same each time then that looks like an engineered value, not a coincidence. That suggests one or more time-outs on some action. As programmers often retry things three times (convention only) that indicates something waits ten seconds, and retries twice.

---

### Post by Xian00 on 2008-09-05
Hi TJ,
I've just taken the logs.
There is a 1 minute delay... and no line in any log during that minute.
Obviously if I log in after that delay everything works ok, if I log in before: no battery icon, no automount of cd, dvd, usb, etc... as usually.

I attached auth.log too, so you can see exactly the log in timestamp.

---

### Post by Xian00 on 2008-09-05
This is only the daemon.log. You can see the delay beetween: 08:43:55 and 08:44:58

```
Sep  5 08:43:53 nb3 NetworkManager: <info>  starting... 
Sep  5 08:43:53 nb3 kdm[5377]: StartServerSucces
Sep  5 08:43:54 nb3 avahi-daemon[5432]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Sep  5 08:43:54 nb3 avahi-daemon[5432]: Successfully dropped root privileges.
Sep  5 08:43:54 nb3 avahi-daemon[5432]: avahi-daemon 0.6.22 starting up.
Sep  5 08:43:54 nb3 avahi-daemon[5432]: Successfully called chroot().
Sep  5 08:43:54 nb3 avahi-daemon[5432]: Successfully dropped remaining capabilities.
Sep  5 08:43:54 nb3 avahi-daemon[5432]: No service file found in /etc/avahi/services.
Sep  5 08:43:54 nb3 avahi-daemon[5432]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.15.
Sep  5 08:43:54 nb3 avahi-daemon[5432]: New relevant interface eth0.IPv4 for mDNS.
Sep  5 08:43:54 nb3 avahi-daemon[5432]: Network interface enumeration completed.
Sep  5 08:43:54 nb3 avahi-daemon[5432]: Registering new address record for 192.168.1.15 on eth0.IPv4.
Sep  5 08:43:54 nb3 avahi-daemon[5432]: Registering HINFO record with values 'X86_64'/'LINUX'.
Sep  5 08:43:55 nb3 avahi-daemon[5432]: Server startup complete. Host name is nb3.local. Local service cookie is 1477528184.
Sep  5 08:44:58 nb3 NetworkManager: <info>  ath0: Device is fully-supported using driver 'ath_pci'. 
Sep  5 08:44:58 nb3 NetworkManager: <info>  ath0: driver does not support SSID scans (scan_capa 0x00). 
Sep  5 08:44:58 nb3 NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep  5 08:44:58 nb3 NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep  5 08:44:58 nb3 NetworkManager: <info>  Now managing wireless (802.11) device 'ath0'. 
Sep  5 08:44:58 nb3 NetworkManager: <info>  Deactivating device ath0. 
Sep  5 08:44:58 nb3 NetworkManager: <debug> [1220597098.501914] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_5540A'). 
Sep  5 08:44:58 nb3 hcid[6221]: Bluetooth HCI daemon
Sep  5 08:44:58 nb3 hcid[6221]: Starting SDP server
Sep  5 08:44:58 nb3 hcid[6221]: Created local server at unix:abstract=/var/run/dbus-Irbowo0HJN,guid=3cac03b1f1c97d26406387a448c0d56a
Sep  5 08:44:58 nb3 audio[6240]: Bluetooth Audio daemon
Sep  5 08:44:58 nb3 audio[6240]: Unix socket created: 5
Sep  5 08:44:58 nb3 audio[6240]: audio.conf: Key file does not have key 'Enable'
Sep  5 08:44:58 nb3 audio[6240]: audio.conf: Key file does not have key 'Disable'
Sep  5 08:44:58 nb3 input[6247]: Bluetooth Input daemon
Sep  5 08:44:58 nb3 input[6247]: Registered input manager path:/org/bluez/input
Sep  5 08:44:58 nb3 audio[6240]: add_service_record: got record id 0x10000
Sep  5 08:44:58 nb3 audio[6240]: audio.conf: Key file does not have key 'Disable'
Sep  5 08:44:58 nb3 audio[6240]: audio.conf: Key file does not have group 'A2DP'
Sep  5 08:44:58 nb3 last message repeated 3 times
Sep  5 08:44:58 nb3 audio[6240]: SEP 0x62d670 registered: type:0 codec:0 seid:1
Sep  5 08:44:58 nb3 audio[6240]: add_service_record: got record id 0x10001
Sep  5 08:44:58 nb3 audio[6240]: add_service_record: got record id 0x10002
Sep  5 08:44:58 nb3 audio[6240]: add_service_record: got record id 0x10003
Sep  5 08:44:58 nb3 audio[6240]: Registered manager path:/org/bluez/audio
Sep  5 08:44:58 nb3 NetworkManager: <debug> [1220597098.693807] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 

```

---

### Post by Xian00 on 2008-09-05
What about disabling avahi-daemon?
Do you think that is worth trying?

Or maybe I should try to disable the wifi adapter... maybe without a cable connection it tries to find a wireless connection... anyway there was never been any "auto ath0" option in /etc/network/interfaces ...

---

### Post by Xian00 on 2008-09-05
No way! Disabling avahi-daemon didn't change anything.

Still a 1 minute delay between 10:00:31 and 10:01:36.
The new daemon log:
```
Sep  5 10:00:31 nb3 NetworkManager: <info>  starting... 
Sep  5 10:00:31 nb3 kdm[5372]: StartServerSucces
Sep  5 10:01:36 nb3 NetworkManager: <info>  ath0: Device is fully-supported using driver 'ath_pci'. 
Sep  5 10:01:36 nb3 NetworkManager: <info>  ath0: driver does not support SSID scans (scan_capa 0x00). 
Sep  5 10:01:36 nb3 NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep  5 10:01:36 nb3 NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep  5 10:01:36 nb3 NetworkManager: <info>  Now managing wireless (802.11) device 'ath0'. 
Sep  5 10:01:36 nb3 NetworkManager: <info>  Deactivating device ath0. 
Sep  5 10:01:36 nb3 NetworkManager: <debug> [1220601696.340688] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_5540A'). 
Sep  5 10:01:36 nb3 hcid[6187]: Bluetooth HCI daemon
Sep  5 10:01:36 nb3 hcid[6187]: Starting SDP server
Sep  5 10:01:36 nb3 hcid[6187]: Created local server at unix:abstract=/var/run/dbus-ctSGnIpbGF,guid=340741b04f57edf32c74d5a148c0e760
Sep  5 10:01:36 nb3 input[6210]: Bluetooth Input daemon
Sep  5 10:01:36 nb3 input[6210]: Registered input manager path:/org/bluez/input
Sep  5 10:01:36 nb3 audio[6204]: Bluetooth Audio daemon
Sep  5 10:01:36 nb3 audio[6204]: Unix socket created: 5
Sep  5 10:01:36 nb3 audio[6204]: audio.conf: Key file does not have key 'Enable'
Sep  5 10:01:36 nb3 audio[6204]: audio.conf: Key file does not have key 'Disable'
Sep  5 10:01:36 nb3 audio[6204]: add_service_record: got record id 0x10000
Sep  5 10:01:36 nb3 audio[6204]: audio.conf: Key file does not have key 'Disable'
Sep  5 10:01:36 nb3 audio[6204]: audio.conf: Key file does not have group 'A2DP'
Sep  5 10:01:36 nb3 last message repeated 3 times
Sep  5 10:01:36 nb3 audio[6204]: SEP 0x62d670 registered: type:0 codec:0 seid:1
Sep  5 10:01:36 nb3 audio[6204]: add_service_record: got record id 0x10001
Sep  5 10:01:36 nb3 audio[6204]: add_service_record: got record id 0x10002
Sep  5 10:01:36 nb3 audio[6204]: add_service_record: got record id 0x10003
Sep  5 10:01:36 nb3 audio[6204]: Registered manager path:/org/bluez/audio
Sep  5 10:01:36 nb3 NetworkManager: <debug> [1220601696.519748] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').
```

---

