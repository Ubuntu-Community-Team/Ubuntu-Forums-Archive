---
title: "My Vaio has just crashed - how do I diagnose this?"
date: 2008-07-08
forum: Hardware
---

### Post by pompeyjohn on 2008-07-08
The model is a VAIO VGN-FZ283BN
The version of Ubuntu is 8.04

The machine crashed, and two of the lights on the front display [1 & A] began flashing in green.

I have been mining the forums for information, and this may be because of ACPI. I dont know, the laptop gets very hot. Much hotter than when I was using windows. I do fear that Ubuntu is killing my hardware.

One thing I know is that hibernation is currently not working - closing the lid does nothing. So I wonder if this is an ACPI issue. Unplugging the power cable prompts the battery icon to show. I trust that it is working as I can see it slowly dropping down. It does seem to be on 40% for a lot of time. I am not worried too much about that though.

So, I have the system log file from /var/logs - how do I 

1. locate the first commands written at startup? Once I have found those, I can work my way up to hopefully find some error information.

Many many thanks in advance,
John

---

### Post by pompeyjohn on 2008-07-08
Please, somebody, I really need help with this urgently

many thanks

---

### Post by pompeyjohn on 2008-07-09
Ok - it died again last night.

My wife is going nuts over this as we really need this laptop to be up and running all the time. I want to stick with Linux, but cant justify it if this keeps happening.

As the machine died late at night, I can see time stamps of its death throes.... I'll copy and paste that information from the syslog in here - any help much appreciated.

Thanks again in advance,
John

```

ul  8 20:43:55 barcelona NetworkManager: <debug> [1215546235.962109] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_ST350083_0AS_973FFFFFFFFF_0_0'). 
Jul  8 20:43:56 barcelona NetworkManager: <debug> [1215546236.078140] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_D03E6A503E6A3020'). 
Jul  8 20:43:56 barcelona ntfs-3g[8045]: Version 1.2216 external FUSE 27 
Jul  8 20:43:56 barcelona ntfs-3g[8045]: Mounted /dev/sdb1 (Read-Write, label "USB3_500GB", NTFS 3.1) 
Jul  8 20:43:56 barcelona ntfs-3g[8045]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_GB.UTF-8 
Jul  8 20:43:56 barcelona ntfs-3g[8045]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,noatime,fsname=/dev/sdb1,blkdev,blksize=4096 
Jul  8 20:43:56 barcelona hald: mounted /dev/sdb1 on behalf of uid 1000
Jul  8 20:58:04 barcelona -- MARK --
Jul  8 21:02:11 barcelona pulseaudio[6352]: shm.c: shm_open() failed: No such file or directory
Jul  8 21:02:11 barcelona pulseaudio[6352]: pstream.c: Failed to import memory block.
Jul  8 21:09:02 barcelona /USR/SBIN/CRON[9596]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul  8 21:17:02 barcelona /USR/SBIN/CRON[10055]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  8 21:38:05 barcelona -- MARK --
Jul  8 21:39:02 barcelona /USR/SBIN/CRON[11015]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul  8 21:58:05 barcelona -- MARK --
Jul  8 22:09:02 barcelona /USR/SBIN/CRON[12514]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul  8 22:10:35 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:11:03 barcelona last message repeated 2 times
Jul  8 22:11:24 barcelona last message repeated 3 times
Jul  8 22:13:04 barcelona last message repeated 3 times
Jul  8 22:13:52 barcelona last message repeated 2 times
Jul  8 22:14:59 barcelona last message repeated 3 times
Jul  8 22:15:23 barcelona last message repeated 2 times
Jul  8 22:17:01 barcelona /USR/SBIN/CRON[12953]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  8 22:17:30 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:18:17 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:19:16 barcelona last message repeated 7 times
Jul  8 22:20:33 barcelona last message repeated 6 times
Jul  8 22:24:50 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:27:21 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:27:21 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:28:16 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:28:16 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:28:28 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:28:28 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:31:41 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:31:41 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:33:12 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:33:13 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:33:18 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:33:18 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:33:27 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:33:27 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:33:30 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:33:30 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:34:01 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:34:01 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:34:08 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:34:08 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:35:10 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:35:10 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:39:02 barcelona /USR/SBIN/CRON[14055]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul  8 22:39:49 barcelona anacron[14157]: Anacron 2.3 started on 2008-07-08
Jul  8 22:39:50 barcelona anacron[14157]: Normal exit (0 jobs run)
Jul  8 22:43:25 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:43:26 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:44:27 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:44:27 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:45:01 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:45:01 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:45:31 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:45:31 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:45:59 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:45:59 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:46:43 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:46:43 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:48:42 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:48:42 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:48:49 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:48:49 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:48:56 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:48:56 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:49:00 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:49:00 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:49:30 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:49:30 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:49:48 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:49:48 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:50:01 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:50:01 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:50:05 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:50:06 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:50:09 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:50:09 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:50:23 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:50:23 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:50:47 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:50:47 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:50:58 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:50:58 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:51:12 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:51:12 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:51:21 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:51:21 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:51:50 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:51:50 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:51:56 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:51:56 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:52:03 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:52:03 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:52:23 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:52:23 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:52:33 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:52:33 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:56:00 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:56:00 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:56:27 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:56:27 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:57:29 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:57:29 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:58:17 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:58:17 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:58:30 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:58:30 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:58:40 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:58:40 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:58:43 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:58:43 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:59:44 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:59:44 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 22:59:53 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 22:59:53 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:00:03 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:00:03 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:02:20 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:02:20 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:02:38 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:02:38 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:02:46 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:02:46 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:02:54 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:02:54 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:03:21 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:03:21 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:03:29 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:03:29 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:03:38 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:03:38 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:04:00 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:04:00 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:04:18 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:04:18 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:05:06 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:05:06 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:05:33 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:05:33 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:05:45 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:05:45 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:07:16 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:07:16 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:07:18 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:07:18 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:08:00 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:08:00 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:08:08 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:08:08 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:08:48 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:08:48 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:08:58 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:08:58 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:09:01 barcelona /USR/SBIN/CRON[15879]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul  8 23:09:10 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:09:10 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:09:40 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:09:40 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:09:48 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:09:48 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:11:44 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:11:44 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:11:49 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:11:49 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:12:01 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:12:01 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:12:55 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:12:55 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:13:32 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:13:32 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:13:54 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:13:54 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:14:02 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:14:02 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:16:53 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:16:53 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:17:02 barcelona /USR/SBIN/CRON[16253]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  8 23:17:02 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:17:02 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:17:08 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:17:08 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:17:11 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:17:11 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:17:13 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:17:13 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:17:45 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:17:45 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:17:50 barcelona pulseaudio[6352]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul  8 23:17:50 barcelona pulseaudio[6352]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jul  8 23:38:07 barcelona -- MARK --
Jul  8 23:39:15 barcelona /USR/SBIN/CRON[17279]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul  8 23:58:15 barcelona -- MARK --
Jul  9 00:09:01 barcelona /USR/SBIN/CRON[18623]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jul  9 00:17:01 barcelona /USR/SBIN/CRON[18951]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  9 08:05:08 barcelona syslogd 1.5.0#1ubuntu1: restart.

```

---

