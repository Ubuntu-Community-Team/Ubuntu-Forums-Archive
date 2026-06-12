---
title: "USB external hard drive disconnecting after sleep"
date: 2012-04-19
forum: Hardware
---

### Post by Vgui on 2012-04-19
Hi,

I'm running Xubuntu 10.04 and have a 3TB USB external hard drive formatted to ext4 as part of my media center. It works fine and will spin down and suspend/sleep the drive after a period of inactivity. However sometimes when this sleep goes for TOO long the drive will disconnect the next time I try to access it. Normally 1 or 2 days without accessing the drive will cause this.
After this happens the device (/dev/sdb1) isn't recognized, and I can't remount it without unplugging the drive, rebooting the computer, and plugging it back in, and then manually mounting it.
This isn't an issue when I'm home, but more of an issue when I'm travelling and can't physically access it to fix the problem.

Has anyone run into this before? Couldn't find any related threads.
I'm thinking of running a script for cron.hourly and making it read/touch the drive to ensure it doesn't sleep for too long...but obviously I'd rather just have it work.

There isn't much in /var/log/messages, it just acts like the drive disconnected naturally and without error.

```

Apr  8 20:42:32 hostname kernel: [607107.372301] ===>rt_ioctl_giwscan. 19(19) BSS returned, data->length = 2934
Apr  8 20:44:32 hostname kernel: [607227.372080] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 2023
**Apr  8 20:44:58 hostname kernel: [607253.610208] usb 1-2: USB disconnect, address 4**
Apr  8 20:45:43 hostname kernel: Kernel logging (proc) stopped.
Apr  8 20:45:44 hostname rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="646" x-info="http://www.rsyslog.com"] exiting on signal 15.
Apr  8 20:46:36 hostname kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr  8 20:46:36 hostname rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="658" x-info="http://www.rsyslog.com"] (re)start

```

EDIT: The drive is a Seagate 3TB USB 3.0 (although I'm connected using USB 2 as far as I know). I think the full name is "GoFlex External Hard Drive".

Ideas appreciated!

---

