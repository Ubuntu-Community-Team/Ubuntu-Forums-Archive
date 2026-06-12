---
title: "Gutsy Refuses to Boot From USB HD after last update"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by uncloned on 2008-02-25
I was wondering if anyone else had this problem. 
I am running an Acer Aspire 5102WLMi 1.6 GHz AMD Turion 4 gig ram,
Ubuntu installed on a 40 gig HD connected by USB (and booting from there)
After the update yesterday (which included a CD driver update) my system started to act funny 
when trying to convert a DVD to mpeg with acidrip and Theoggen. (It had trouble seeing the DVD)
So I rebooted and found that while GRUB seems to load the screen goes blank and 
nothing shows up after the Grub status messages. 
I have waited about 15 minutes a couple times, and have repbooted a few times.
 
Does anyone have any words of wisdom before I format and reinstall?
(That wouldn't be the end of the world but I do have most everything working now and have configured
Ubuntu nicely.)
 
Thanks,
 
Chris

PS I was able to access the drive with NFS from windows and found this file .xsession-errors


(process:5974): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5978): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
can't lock memory: Cannot allocate memoryWARNING: not using secure memory for passwords
SESSION_MANAGER=local/chris-laptop:/tmp/.ICE-unix/5971
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5975 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: seahorse nautilus module initialized
Initializing gnome-mount extension
present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in Xorg.conf or XFree86.conf to use GSynaptics
** Message: Not starting remote desktop server
evolution-alarm-notify-Message: Setting timeout for 7916 1203915600 1203907684
evolution-alarm-notify-Message:  Mon Feb 25 00:00:00 2008

evolution-alarm-notify-Message:  Sun Feb 24 21:48:04 2008

alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1870 (alarm_queue_init)
alarm-queue.c:200 (queue_midnight_refresh) - Refresh at Mon Feb 25 00:00:00 2008
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/chris/.evolution/calendar/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/chris/.evolution/calendar/local/system - Calendar Open Async... 0x80c2690
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:462 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80de330
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/chris/.evolution/tasks/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/chris/.evolution/tasks/local/system - Calendar Open Async... 0x80de480
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/chris/.evolution/memos/local/system 
alarm-notify.c:462 (alarm_notify_add_calendar) file:///home/chris/.evolution/memos/local/system - Calendar Open Async... 0x80e19b0
alarm-notify.c:393 (cal_opened_cb) file:///home/chris/.evolution/calendar/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/chris/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x80e0210: Received at thread b5dc3b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80c2690
alarm-queue.c:581 (load_alarms_for_today) - From Sun Feb 24 21:48:16 2008
 to Sun Feb 24 21:48:16 2008

alarm-queue.c:518 (load_alarms) 
alarm-notify.c:393 (cal_opened_cb) contacts:/// - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:393 (cal_opened_cb) file:///home/chris/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80e12e0: Received at thread b5dc3b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80de480
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e0210: Replied to GUI thread
alarm-queue.c:581 (load_alarms_for_today) - From Sun Feb 24 21:48:17 2008
 to Sun Feb 24 21:48:17 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80deec0: Received at thread b5dc3b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80de330
alarm-notify.c:337 (alarm_msgport_replied) - 0x80e12e0: Replied to GUI thread
alarm-queue.c:581 (load_alarms_for_today) - From Sun Feb 24 21:48:17 2008
 to Sun Feb 24 21:48:17 2008

alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:349 (alarm_msg_received) - 0x80dfe40: Received at thread b5dc3b90
alarm-queue.c:2003 (alarm_queue_add_async) - 0x80/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
  PID TTY          TIME CMD

(gnome-panel:6043): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24

---

### Post by uncloned on 2008-02-26
Could someone tell me where to start looking? The xsession file suggests GTK is broke. 

I just need a little direction if someone could help. I am not a total begininner with computers - just new to Linux.

Thanks,

Chris

---

### Post by uncloned on 2008-02-26
This is from the dpkg.log file - a list of the updates before the loss of Ubuntu functionality

2008-02-24 21:49:40 startup archives unpack
2008-02-24 21:49:58 upgrade libcdio6 0.76-1ubuntu2 0.76-1ubuntu2.7.10.1
2008-02-24 21:49:58 status half-configured libcdio6 0.76-1ubuntu2
2008-02-24 21:49:58 status unpacked libcdio6 0.76-1ubuntu2
2008-02-24 21:49:58 status half-installed libcdio6 0.76-1ubuntu2
2008-02-24 21:49:58 status half-installed libcdio6 0.76-1ubuntu2
2008-02-24 21:49:58 status unpacked libcdio6 0.76-1ubuntu2.7.10.1
2008-02-24 21:49:58 status unpacked libcdio6 0.76-1ubuntu2.7.10.1
2008-02-24 21:49:58 upgrade libiso9660-4 0.76-1ubuntu2 0.76-1ubuntu2.7.10.1
2008-02-24 21:49:58 status half-configured libiso9660-4 0.76-1ubuntu2
2008-02-24 21:49:58 status unpacked libiso9660-4 0.76-1ubuntu2
2008-02-24 21:49:58 status half-installed libiso9660-4 0.76-1ubuntu2
2008-02-24 21:49:59 status half-installed libiso9660-4 0.76-1ubuntu2
2008-02-24 21:49:59 status unpacked libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-24 21:49:59 status unpacked libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-24 21:49:59 upgrade libpcre3 7.4-0ubuntu0.7.10.1 7.4-0ubuntu0.7.10.2
2008-02-24 21:49:59 status half-configured libpcre3 7.4-0ubuntu0.7.10.1
2008-02-24 21:49:59 status unpacked libpcre3 7.4-0ubuntu0.7.10.1
2008-02-24 21:49:59 status half-installed libpcre3 7.4-0ubuntu0.7.10.1
2008-02-24 21:49:59 status half-installed libpcre3 7.4-0ubuntu0.7.10.1
2008-02-24 21:49:59 status unpacked libpcre3 7.4-0ubuntu0.7.10.2
2008-02-24 21:49:59 status unpacked libpcre3 7.4-0ubuntu0.7.10.2
2008-02-24 21:49:59 upgrade libpcrecpp0 7.4-0ubuntu0.7.10.1 7.4-0ubuntu0.7.10.2
2008-02-24 21:49:59 status half-configured libpcrecpp0 7.4-0ubuntu0.7.10.1
2008-02-24 21:49:59 status unpacked libpcrecpp0 7.4-0ubuntu0.7.10.1
2008-02-24 21:49:59 status half-installed libpcrecpp0 7.4-0ubuntu0.7.10.1
2008-02-24 21:50:00 status half-installed libpcrecpp0 7.4-0ubuntu0.7.10.1
2008-02-24 21:50:00 status unpacked libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:00 status unpacked libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:00 upgrade libqt4-core 4.3.2-0ubuntu3.1 4.3.2-0ubuntu3.2
2008-02-24 21:50:00 status half-configured libqt4-core 4.3.2-0ubuntu3.1
2008-02-24 21:50:00 status unpacked libqt4-core 4.3.2-0ubuntu3.1
2008-02-24 21:50:00 status half-installed libqt4-core 4.3.2-0ubuntu3.1
2008-02-24 21:50:00 status half-installed libqt4-core 4.3.2-0ubuntu3.1
2008-02-24 21:50:01 status unpacked libqt4-core 4.3.2-0ubuntu3.2
2008-02-24 21:50:01 status unpacked libqt4-core 4.3.2-0ubuntu3.2
2008-02-24 21:50:01 upgrade libqt4-gui 4.3.2-0ubuntu3.1 4.3.2-0ubuntu3.2
2008-02-24 21:50:01 status half-configured libqt4-gui 4.3.2-0ubuntu3.1
2008-02-24 21:50:01 status unpacked libqt4-gui 4.3.2-0ubuntu3.1
2008-02-24 21:50:01 status half-installed libqt4-gui 4.3.2-0ubuntu3.1
2008-02-24 21:50:02 status half-installed libqt4-gui 4.3.2-0ubuntu3.1
2008-02-24 21:50:03 status unpacked libqt4-gui 4.3.2-0ubuntu3.2
2008-02-24 21:50:03 status unpacked libqt4-gui 4.3.2-0ubuntu3.2
2008-02-24 21:50:03 startup packages configure
2008-02-24 21:50:03 configure libcdio6 0.76-1ubuntu2.7.10.1 0.76-1ubuntu2.7.10.1
2008-02-24 21:50:03 status unpacked libcdio6 0.76-1ubuntu2.7.10.1
2008-02-24 21:50:04 status half-configured libcdio6 0.76-1ubuntu2.7.10.1
2008-02-24 21:50:04 status installed libcdio6 0.76-1ubuntu2.7.10.1
2008-02-24 21:50:04 status triggers-pending libc6 2.6.1-1ubuntu10
2008-02-24 21:50:04 configure libiso9660-4 0.76-1ubuntu2.7.10.1 0.76-1ubuntu2.7.10.1
2008-02-24 21:50:04 status unpacked libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-24 21:50:04 status half-configured libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-24 21:50:04 status installed libiso9660-4 0.76-1ubuntu2.7.10.1
2008-02-24 21:50:04 configure libpcre3 7.4-0ubuntu0.7.10.2 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:04 status unpacked libpcre3 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:04 status half-configured libpcre3 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:04 status installed libpcre3 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:04 configure libpcrecpp0 7.4-0ubuntu0.7.10.2 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:04 status unpacked libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:04 status half-configured libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:04 status installed libpcrecpp0 7.4-0ubuntu0.7.10.2
2008-02-24 21:50:04 configure libqt4-core 4.3.2-0ubuntu3.2 4.3.2-0ubuntu3.2
2008-02-24 21:50:04 status unpacked libqt4-core 4.3.2-0ubuntu3.2
2008-02-24 21:50:04 status half-configured libqt4-core 4.3.2-0ubuntu3.2
2008-02-24 21:50:04 status installed libqt4-core 4.3.2-0ubuntu3.2
2008-02-24 21:50:04 configure libqt4-gui 4.3.2-0ubuntu3.2 4.3.2-0ubuntu3.2
2008-02-24 21:50:04 status unpacked libqt4-gui 4.3.2-0ubuntu3.2
2008-02-24 21:50:04 status half-configured libqt4-gui 4.3.2-0ubuntu3.2
2008-02-24 21:50:04 status installed libqt4-gui 4.3.2-0ubuntu3.2
2008-02-24 21:50:04 trigproc libc6 2.6.1-1ubuntu10 2.6.1-1ubuntu10
2008-02-24 21:50:04 status half-configured libc6 2.6.1-1ubuntu10
2008-02-24 21:50:17 status installed libc6 2.6.1-1ubuntu10

---

### Post by uncloned on 2008-02-27
Well after a couple days of no replies on the mailing list or here I finally figured out what to do.
The key was to boot into recovery mode - yeah stupid I didn't think of it first.
Then I had to run fsck manually to repair the clusters that were messed up on the disk.

This was great and all.... but being new to Ubuntu  had not a clue that recovery mode would
do this for me. Recovery mode in Windows or especially in the days of DOS could mean something very bad..... 

Norton made a lot of money selling Norton tools for a reason.

Chris

---

