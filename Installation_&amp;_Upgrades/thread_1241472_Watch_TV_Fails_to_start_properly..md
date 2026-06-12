---
title: "Watch TV Fails to start properly."
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by Buntubailey on 2009-08-16
Hello,

I am having some major issues to something that vis probably quite simple. I tried installing Mythbuntu 9.04 for the first time yesterday. Installation was a breeze and I followed a nice walkthrough guide I found [here.]("http://andrewmanugian.wordpress.com/2009/07/26/andrewsmythtvguide/")

Anyway, after following the guide. I tried to use watch tv but it just flashed the screen for a second then returned to the menu. I read that this may be because there is no directory vreated for LiveTV so I created one in /var/lib/mythtv/livetv and set the permissions of that folder to a+rwx. I also changed ownership to the mythbuntu user I had set up from the beginning. This had some effect. Now when I click on the "Watch TV" the screen goes black for about 30 seconds then returns to the menu. 

I should also mention that I changed the TVSettings and playback setting to MPEG4 instead of the default. 

Please find attached an output of the log file.

> /var/log/mythtv/mtd.log <==
mtd started at Sun Aug 16 11:46:32 2009
mtd is running on a host called mythbuntu-desktop
11:46:32: Waiting for connections/jobs
11:46:32: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-08-16 03:13:41.414 TVRec(1): Changing from WatchingLiveTV to None
2009-08-16 03:13:41.420 Finished recording Unknown: channel 1084
2009-08-16 03:16:26.841 Expiring 0 MBytes for 1084 @ Sun Aug 16 03:13:00 2009 => Unknown
2009-08-16 03:18:26.845 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-16 03:18:41.892 MainServer::HandleAnnounce Playback
2009-08-16 03:18:41.894 adding: mythbuntu-desktop as a client (events: 0)
2009-08-16 03:18:41.895 TVRec(1): Changing from None to WatchingLiveTV
2009-08-16 03:18:42.374 TVRec(1): HW Tuner: 1->1
2009-08-16 03:18:42.423 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2009-08-16 03:18:43.479 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[mpeg4 @ 0xb7421744]removing common factors from framerate
2009-08-16 03:18:43.497 NVR(/dev/video0): Won't work with the streaming interface, falling back
strange error flushing buffer ... 
VIDIOCGMBUF:: Invalid argument
2009-08-16 03:19:23.500 TVRec(1): Changing from WatchingLiveTV to None
2009-08-16 03:19:23.504 Finished recording Unknown: channel 1084
2009-08-16 03:20:26.856 Expiring 0 MBytes for 1084 @ Sun Aug 16 03:18:42 2009 => Unknown
2009-08-16 03:22:34.912 Reschedule requested for id 0.
2009-08-16 03:22:34.979 Scheduled 0 items in 0.1 = 0.06 match + 0.01 place
2009-08-16 03:23:29.841 Reloading backend settings
2009-08-16 03:23:34.815 MainServer::HandleAnnounce Playback
2009-08-16 03:23:34.815 adding: mythbuntu-desktop as a client (events: 0)
2009-08-16 03:23:34.816 TVRec(1): Changing from None to WatchingLiveTV
2009-08-16 03:23:34.827 TVRec(1): HW Tuner: 1->1
2009-08-16 03:23:34.879 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
[mpeg4 @ 0xb7421744]2009-08-16 03:23:35.932 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
removing common factors from framerate
2009-08-16 03:23:35.939 NVR(/dev/video0): Won't work with the streaming interface, falling back
strange error flushing buffer ... 
VIDIOCGMBUF:: Invalid argument
2009-08-16 03:24:15.943 TVRec(1): Changing from WatchingLiveTV to None
2009-08-16 03:24:15.948 Finished recording Unknown: channel 1084
2009-08-16 03:26:26.867 Expiring 0 MBytes for 1084 @ Sun Aug 16 03:23:34 2009 => Unknown
2009-08-16 03:30:31.369 MainServer::HandleAnnounce Playback
2009-08-16 03:30:31.375 adding: mythbuntu-desktop as a client (events: 0)
2009-08-16 03:30:31.376 TVRec(1): Changing from None to WatchingLiveTV
2009-08-16 03:30:31.379 TVRec(1): HW Tuner: 1->1
2009-08-16 03:30:31.427 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
[mpeg4 @ 0xb7421744]2009-08-16 03:30:32.485 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
removing common factors from framerate
2009-08-16 03:30:32.491 NVR(/dev/video0): Won't work with the streaming interface, falling back
strange error flushing buffer ... 
VIDIOCGMBUF:: Invalid argument
2009-08-16 03:31:12.498 TVRec(1): Changing from WatchingLiveTV to None
2009-08-16 03:31:12.505 Finished recording Unknown: channel 1084
2009-08-16 03:32:26.878 Expiring 0 MBytes for 1084 @ Sun Aug 16 03:30:31 2009 => Unknown
2009-08-16 03:33:26.884 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-16 03:39:45.208 MainServer::HandleAnnounce Playback
2009-08-16 03:39:45.211 adding: mythbuntu-desktop as a client (events: 0)
2009-08-16 03:39:45.212 TVRec(1): Changing from None to WatchingLiveTV
2009-08-16 03:39:45.215 TVRec(1): HW Tuner: 1->1
2009-08-16 03:39:45.265 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
[mpeg4 @ 0xb7421744]2009-08-16 03:39:46.325 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
removing common factors from framerate
2009-08-16 03:39:46.339 NVR(/dev/video0): Won't work with the streaming interface, falling back
strange error flushing buffer ... 
VIDIOCGMBUF:: Invalid argument
2009-08-16 03:40:26.342 TVRec(1): Changing from WatchingLiveTV to None
2009-08-16 03:40:26.348 Finished recording Unknown: channel 1084
2009-08-16 03:42:26.904 Expiring 0 MBytes for 1084 @ Sun Aug 16 03:39:45 2009 => Unknown
2009-08-16 11:46:26.822 Using runtime prefix = /usr
2009-08-16 11:46:26.911 Empty LocalHostName.
2009-08-16 11:46:26.971 Using localhost value of mythbuntu-desktop
2009-08-16 11:46:27.061 New DB connection, total: 1
2009-08-16 11:46:27.108 Connected to database 'mythconverg' at host: localhost
2009-08-16 11:46:27.145 Closing DB connection named 'DBManager0'
2009-08-16 11:46:27.150 Connected to database 'mythconverg' at host: localhost
2009-08-16 11:46:27.151 New DB connection, total: 2
2009-08-16 11:46:27.151 Connected to database 'mythconverg' at host: localhost
2009-08-16 11:46:27.287 Current Schema Version: 1214
Starting up as the master server.
2009-08-16 11:46:27.757 New DB connection, total: 3
2009-08-16 11:46:27.817 Connected to database 'mythconverg' at host: localhost
2009-08-16 11:46:28.504 New DB scheduler connection
2009-08-16 11:46:28.613 Connected to database 'mythconverg' at host: localhost
2009-08-16 11:46:28.647 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2009-08-16 11:46:28.648 Main::Registering HttpStatus Extension
2009-08-16 11:46:28.649 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-16 11:46:28.653 Enabled verbose msgs:  important general
2009-08-16 11:46:28.668 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-08-16 11:46:31.617 Reschedule requested for id -1.
2009-08-16 11:46:31.941 Scheduled 0 items in 0.3 = 0.32 match + 0.01 place
2009-08-16 11:46:32.135 Seem to be woken up by USER
2009-08-16 11:46:54.393 MainServer::HandleAnnounce Monitor
2009-08-16 11:46:54.398 adding: mythbuntu-desktop as a client (events: 0)
2009-08-16 11:46:54.399 MainServer::HandleAnnounce Monitor
2009-08-16 11:46:54.399 adding: mythbuntu-desktop as a client (events: 1)
2009-08-16 11:46:54.404 MainServer::HandleAnnounce Playback
2009-08-16 11:46:54.435 adding: mythbuntu-desktop as a client (events: 0)
2009-08-16 11:46:54.438 TVRec(1): Changing from None to WatchingLiveTV
2009-08-16 11:46:54.444 TVRec(1): HW Tuner: 1->1
2009-08-16 11:46:54.485 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2009-08-16 11:46:55.590 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
[mpeg4 @ 0xb7480744]removing common factors from framerate
2009-08-16 11:46:55.738 NVR(/dev/video0): Won't work with the streaming interface, falling back
strange error flushing buffer ... 
VIDIOCGMBUF:: Invalid argument
2009-08-16 11:47:35.732 TVRec(1): Changing from WatchingLiveTV to None
2009-08-16 11:47:35.736 Finished recording Unknown: channel 1084
2009-08-16 11:47:48.619 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

==> /var/log/mythtv/mythfrontend.log <==
2009-08-16 03:03:06.515 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-16 03:03:06.515 TV Error: LiveTV not successfully started
2009-08-16 03:03:06.609 TV: Deleting TV Chain in destructor
2009-08-16 03:03:06.614 DPMS Reactivated.
2009-08-16 03:13:00.287 TV: Attempting to change from None to WatchingLiveTV
2009-08-16 03:13:00.288 Using protocol version 40
2009-08-16 03:13:01.489 DPMS Deactivated 
2009-08-16 03:13:41.412 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-16 03:13:41.412 TV Error: LiveTV not successfully started
2009-08-16 03:13:41.427 TV: Deleting TV Chain in destructor
2009-08-16 03:13:41.433 DPMS Reactivated.
2009-08-16 03:17:18.505 Received a remote 'Clear Cache' request
2009-08-16 03:18:20.742 Received a remote 'Clear Cache' request
2009-08-16 03:18:41.892 TV: Attempting to change from None to WatchingLiveTV
2009-08-16 03:18:41.892 Using protocol version 40
2009-08-16 03:18:43.595 DPMS Deactivated 
2009-08-16 03:19:23.498 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-16 03:19:23.498 TV Error: LiveTV not successfully started
2009-08-16 03:19:23.532 TV: Deleting TV Chain in destructor
2009-08-16 03:19:23.537 DPMS Reactivated.
2009-08-16 03:19:55.671 Received a remote 'Clear Cache' request
2009-08-16 03:20:18.893 Received a remote 'Clear Cache' request
2009-08-16 03:20:37.855 Received a remote 'Clear Cache' request
2009-08-16 03:22:08.867 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2009-08-16 03:22:12.615 Received a remote 'Clear Cache' request
2009-08-16 03:22:19.800 Received a remote 'Clear Cache' request
2009-08-16 03:22:34.912 Received a remote 'Clear Cache' request
2009-08-16 03:22:46.496 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2009-08-16 03:22:52.851 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2009-08-16 03:22:59.067 SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2009-08-16 03:23:05.744 Received a remote 'Clear Cache' request
2009-08-16 03:23:14.617 Received a remote 'Clear Cache' request
2009-08-16 03:23:29.843 Received a remote 'Clear Cache' request
2009-08-16 03:23:34.814 TV: Attempting to change from None to WatchingLiveTV
2009-08-16 03:23:34.814 Using protocol version 40
2009-08-16 03:23:36.016 DPMS Deactivated 
2009-08-16 03:24:15.940 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-16 03:24:15.941 TV Error: LiveTV not successfully started
2009-08-16 03:24:15.955 TV: Deleting TV Chain in destructor
2009-08-16 03:24:15.956 DPMS Reactivated.
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
2009-08-16 03:30:31.369 TV: Attempting to change from None to WatchingLiveTV
2009-08-16 03:30:31.369 Using protocol version 40
2009-08-16 03:30:32.571 DPMS Deactivated 
2009-08-16 03:31:12.495 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-16 03:31:12.495 TV Error: LiveTV not successfully started
2009-08-16 03:31:12.508 TV: Deleting TV Chain in destructor
2009-08-16 03:31:12.515 DPMS Reactivated.
No LSB modules are available.
tail: error reading `/proc/driver/nvidia/cards': Is a directory
tail: error reading `/proc/driver/nvidia/warnings': Is a directory
WARNING: you should run this program as super-user.
2009-08-16 03:39:45.207 TV: Attempting to change from None to WatchingLiveTV
2009-08-16 03:39:45.208 Using protocol version 40
2009-08-16 03:39:46.409 DPMS Deactivated 
2009-08-16 03:40:26.339 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-16 03:40:26.340 TV Error: LiveTV not successfully started
2009-08-16 03:40:26.391 TV: Deleting TV Chain in destructor
2009-08-16 03:40:26.392 DPMS Reactivated.
Starting mythfrontend.real..
2009-08-16 11:46:35.642 New DB connection, total: 2
2009-08-16 11:46:35.642 Connected to database 'mythconverg' at host: localhost
2009-08-16 11:46:35.643 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2009-08-16 11:46:35.643 Enabled verbose msgs:  important general
2009-08-16 11:46:35.706 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-16 11:46:37.016 No theme dir: /home/mythbuntu/.mythtv/themes/Mythbuntu-8.04
2009-08-16 11:46:37.017 Primary screen 0.
2009-08-16 11:46:37.017 Using screen 0, 1360x768 at 0,0
2009-08-16 11:46:37.018 No theme dir: /home/mythbuntu/.mythtv/themes/Mythbuntu-8.04
2009-08-16 11:46:37.018 Switching to square mode (Mythbuntu-8.04)
2009-08-16 11:46:37.043 Using the Qt painter
2009-08-16 11:46:37.044 lirc init success using configuration file: /home/mythbuntu/.mythtv/lircrc
2009-08-16 11:46:37.044 JoystickMenuClient Error: Joystick disabled - Failed to read /home/mythbuntu/.mythtv/joystickmenurc
2009-08-16 11:46:37.600 Specified base font 'medium' does not exist for font clock
2009-08-16 11:46:37.600 Specified base font 'medium' does not exist for font small
2009-08-16 11:46:37.600 Specified base font 'medium' does not exist for font medium
2009-08-16 11:46:37.600 Specified base font 'medium' does not exist for font large
2009-08-16 11:46:37.601 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-08-16 11:46:37.673 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-16 11:46:37.706 Registering Internal as a media playback plugin.
2009-08-16 11:46:37.827 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-16 11:46:38.071 Failed to run 'cdrecord --scanbus'
2009-08-16 11:46:38.073 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-16 11:46:38.074 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-16 11:46:38.088 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.3:5060 NAT address 192.168.0.3
SIP: Cannot register; proxy, username or password not set
2009-08-16 11:46:38.290 No theme dir: /home/mythbuntu/.mythtv/themes/Mythbuntu-8.04
2009-08-16 11:46:54.385 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-16 11:46:54.386 Using protocol version 40
2009-08-16 11:46:54.403 TV: Attempting to change from None to WatchingLiveTV
2009-08-16 11:46:54.403 Using protocol version 40
2009-08-16 11:46:55.737 DPMS Deactivated 
2009-08-16 11:47:35.729 TV Error: StartRecorder() -- timed out waiting for recorder to start
2009-08-16 11:47:35.729 TV Error: LiveTV not successfully started
2009-08-16 11:47:35.768 TV: Deleting TV Chain in destructor
2009-08-16 11:47:35.769 DPMS Reactivated.

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Aug 16 11:46:28 mythbuntu-desktop NetworkManager: <info>  Trying to start the supplicant... 
Aug 16 11:46:28 mythbuntu-desktop NetworkManager: <info>  Trying to start the system settings daemon... 
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: Found user 'avahi' (UID 110) and group 'avahi' (GID 118).
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: Successfully dropped root privileges.
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: avahi-daemon 0.6.23 starting up.
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings:    SCPlugin-Ifupdown: init!
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_24_8c_b8_ea_23, iface: eth0): not well known
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings:    SCPlugin-Ifupdown: (161175296) ... get_connections.
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings:    SCPlugin-Ifupdown: (161175296) ... get_connections (managed=false): return empty list.
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: Successfully called chroot().
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: Successfully dropped remaining capabilities.
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: No service file found in /etc/avahi/services.
Aug 16 11:46:28 mythbuntu-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: Network interface enumeration completed.
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 16 11:46:28 mythbuntu-desktop avahi-daemon[3414]: Server startup complete. Host name is mythbuntu-desktop.local. Local service cookie is 3128600508.
Aug 16 11:46:29 mythbuntu-desktop acpid: client connected from 3367[0:0] 
Aug 16 11:46:29 mythbuntu-desktop /usr/sbin/cron[3555]: (CRON) INFO (pidfile fd = 3)
Aug 16 11:46:29 mythbuntu-desktop /usr/sbin/cron[3556]: (CRON) STARTUP (fork ok)
Aug 16 11:46:29 mythbuntu-desktop /usr/sbin/cron[3556]: (CRON) INFO (Running @reboot jobs)
Aug 16 11:46:30 mythbuntu-desktop console-kit-daemon[3129]: WARNING: Couldn't read /proc/3128/environ: Failed to open file '/proc/3128/environ': No such file or directory 
Aug 16 11:46:32 mythbuntu-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Aug 16 11:46:32 mythbuntu-desktop NetworkManager: <info>  (eth0): bringing up device. 
Aug 16 11:46:32 mythbuntu-desktop NetworkManager: <info>  (eth0): preparing device. 
Aug 16 11:46:32 mythbuntu-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Aug 16 11:46:32 mythbuntu-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Aug 16 11:46:32 mythbuntu-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Aug 16 11:46:32 mythbuntu-desktop kernel: [   29.157079] forcedeth 0000:00:0f.0: irq 2299 for MSI/MSI-X
Aug 16 11:46:32 mythbuntu-desktop nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_24_8c_b8_ea_23
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  dhclient started with pid 3861 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Aug 16 11:46:33 mythbuntu-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 16 11:46:33 mythbuntu-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 16 11:46:33 mythbuntu-desktop dhclient: All rights reserved.
Aug 16 11:46:33 mythbuntu-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 16 11:46:33 mythbuntu-desktop dhclient: 
Aug 16 11:46:33 mythbuntu-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Aug 16 11:46:33 mythbuntu-desktop dhclient: Listening on LPF/eth0/00:24:8c:b8:ea:23
Aug 16 11:46:33 mythbuntu-desktop dhclient: Sending on   LPF/eth0/00:24:8c:b8:ea:23
Aug 16 11:46:33 mythbuntu-desktop dhclient: Sending on   Socket/fallback
Aug 16 11:46:33 mythbuntu-desktop avahi-daemon[3414]: Registering new address record for fe80::224:8cff:feb8:ea23 on eth0.*.
Aug 16 11:46:36 mythbuntu-desktop dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 255.255.255.255 port 67
Aug 16 11:46:36 mythbuntu-desktop dhclient: DHCPNAK from 192.168.0.1
Aug 16 11:46:36 mythbuntu-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> expire 
Aug 16 11:46:36 mythbuntu-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Aug 16 11:46:36 mythbuntu-desktop NetworkManager: <info>  DHCP: device eth0 state changed expire -> preinit 
Aug 16 11:46:37 mythbuntu-desktop lircd-0.8.4a[1615]: accepted new client on /dev/lircd
Aug 16 11:46:38 mythbuntu-desktop dhclient: DHCPOFFER of 192.168.0.3 from 192.168.0.1
Aug 16 11:46:38 mythbuntu-desktop dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 255.255.255.255 port 67
Aug 16 11:46:38 mythbuntu-desktop dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>    address 192.168.0.3 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>    gateway 192.168.0.1 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>    nameserver '192.168.0.1' 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Aug 16 11:46:38 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Aug 16 11:46:38 mythbuntu-desktop avahi-daemon[3414]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.3.
Aug 16 11:46:38 mythbuntu-desktop avahi-daemon[3414]: New relevant interface eth0.IPv4 for mDNS.
Aug 16 11:46:38 mythbuntu-desktop avahi-daemon[3414]: Registering new address record for 192.168.0.3 on eth0.IPv4.
Aug 16 11:46:38 mythbuntu-desktop dhclient: bound to 192.168.0.3 -- renewal in 113710 seconds.
Aug 16 11:46:39 mythbuntu-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Aug 16 11:46:39 mythbuntu-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Aug 16 11:46:39 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Aug 16 11:46:39 mythbuntu-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 16 11:46:39 mythbuntu-desktop ntpd[3102]: ntpd exiting on signal 15
Aug 16 11:46:41 mythbuntu-desktop ntpdate[4025]: adjust time server 91.189.94.4 offset -0.077835 sec
Aug 16 11:46:41 mythbuntu-desktop ntpd[4055]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: precision = 1.000 usec
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: Listening on interface #2 lo, ::1#123 Enabled
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: Listening on interface #3 eth0, fe80::224:8cff:feb8:ea23#123 Enabled
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: Listening on interface #5 eth0, 192.168.0.3#123 Enabled
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: kernel time sync status 0040
Aug 16 11:46:41 mythbuntu-desktop ntpd[4056]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Aug 16 11:46:42 mythbuntu-desktop kernel: [   39.404506] eth0: no IPv6 routers present

==> /var/log/Xorg.0.log <==
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1360 x 768
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 9 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"

==> /home/mythbuntu/.xsession-errors <==
16/08/2009 11:46:32 passing arg to libvncserver: -rfbauth
16/08/2009 11:46:32 passing arg to libvncserver: /home/mythbuntu/.vnc/passwd
16/08/2009 11:46:32 passing arg to libvncserver: -rfbport
16/08/2009 11:46:32 passing arg to libvncserver: 5900
16/08/2009 11:46:32 x11vnc version: 0.9.3 lastmod: 2007-09-30
16/08/2009 11:46:32 Using X display :0
16/08/2009 11:46:32 
16/08/2009 11:46:32 ------------------ USEFUL INFORMATION ------------------
16/08/2009 11:46:32 X DAMAGE available on display, using it for polling hints.
16/08/2009 11:46:32   To disable this behavior use: '-noxdamage'
16/08/2009 11:46:32 
16/08/2009 11:46:32 XFIXES available on display, resetting cursor mode
16/08/2009 11:46:32   to: '-cursor most'.
16/08/2009 11:46:32   to disable this behavior use: '-cursor arrow'
16/08/2009 11:46:32   or '-noxfixes'.
16/08/2009 11:46:32 using XFIXES for cursor drawing.
16/08/2009 11:46:32 GrabServer control via XTEST.
16/08/2009 11:46:32 
16/08/2009 11:46:32 Scroll Detection: -scrollcopyrect mode is in effect to
16/08/2009 11:46:32   use RECORD extension to try to detect scrolling windows
16/08/2009 11:46:32   (induced by either user keystroke or mouse input).
16/08/2009 11:46:32   If this yields undesired behavior (poor response, painting
16/08/2009 11:46:32   errors, etc) it may be disabled via: '-noscr'
16/08/2009 11:46:32   Also see the -help entry for tuning parameters.
16/08/2009 11:46:32   You can press 3 Alt_L's (Left "Alt" key) in a row to 
16/08/2009 11:46:32   repaint the screen, also see the -fixscreen option for
16/08/2009 11:46:32   periodic repaints.
16/08/2009 11:46:32 
16/08/2009 11:46:32 XKEYBOARD: number of keysyms per keycode 6 is greater
16/08/2009 11:46:32   than 4 and 290 keysyms are mapped above 4.
16/08/2009 11:46:32   Automatically switching to -xkb mode.
16/08/2009 11:46:32   If this makes the key mapping worse you can
16/08/2009 11:46:32   disable it with the "-noxkb" option.
16/08/2009 11:46:32   Also, remember "-remap DEAD" for accenting characters.
16/08/2009 11:46:32 X FBPM extension not supported.
16/08/2009 11:46:32 X display is capable of DPMS.
16/08/2009 11:46:32 --------------------------------------------------------
16/08/2009 11:46:32 
16/08/2009 11:46:32 Default visual ID: 0x21
16/08/2009 11:46:32 Read initial data from X display into framebuffer.
16/08/2009 11:46:32 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/5440
16/08/2009 11:46:32 
16/08/2009 11:46:32 X display :0.0 is 32bpp depth=24 true color
16/08/2009 11:46:32 
16/08/2009 11:46:32 Listening for VNC connections on TCP port 5900
16/08/2009 11:46:32 
16/08/2009 11:46:32 Xinerama is present and active (e.g. multi-head).
16/08/2009 11:46:32 Xinerama: enabling -xwarppointer mode to try to correct
16/08/2009 11:46:32 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
16/08/2009 11:46:32 Xinerama: Use -noxwarppointer to force XTEST.
16/08/2009 11:46:32 fb read rate: 430 MB/sec
16/08/2009 11:46:32 screen setup finished.
16/08/2009 11:46:32 

The VNC desktop is:      mythbuntu-desktop:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: [http://www.karlrunge.com/x11vnc/#faq-client-caching](http://www.karlrunge.com/x11vnc/#faq-client-caching)

/usr/bin/startxfce4: X server already running on display :0
/etc/xdg/xfce4/xinitrc: 59: source: not found
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)
xfdesktop[3875]: starting up

(xfce4-panel:3876): xfce4-panel-WARNING **: xfce4-panel is not running
Please note: additional command line arguments will not be passed
  to mythfrontend when using --service
Please set them in /etc/mythtv/session-settings instead

** (update-notifier:3910): WARNING **: already running?

2009-08-16 11:46:35.503 Using runtime prefix = /usr
2009-08-16 11:46:35.505 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-16 11:46:35.506 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2009-08-16 11:46:35.543 XScreenSaver support enabled
2009-08-16 11:46:35.543 DPMS is active.
2009-08-16 11:46:35.543 Empty LocalHostName.
2009-08-16 11:46:35.543 Using localhost value of mythbuntu-desktop
2009-08-16 11:46:35.547 New DB connection, total: 1
2009-08-16 11:46:35.572 Connected to database 'mythconverg' at host: localhost
2009-08-16 11:46:35.573 Closing DB connection named 'DBManager0'
2009-08-16 11:46:35.574 Primary screen 0.
2009-08-16 11:46:35.574 Connected to database 'mythconverg' at host: localhost
2009-08-16 11:46:35.574 Using screen 0, 1360x768 at 0,0
** (nm-applet:3903): DEBUG: applet_common_device_state_changed
** (nm-applet:3903): DEBUG: applet_common_device_state_changed
** (nm-applet:3903): DEBUG: foo_client_state_changed_cb
** (update-notifier:3879): DEBUG: /usr/lib/update-notifier/apt-check returned 3 (security: 0)
** (update-notifier:3879): DEBUG: crashreport_check


==> lsb_release -a <==
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  2.3G  8.2G  22% /
tmpfs                 942M     0  942M   0% /lib/init/rw
varrun                942M  332K  942M   1% /var/run
varlock               942M     0  942M   0% /var/lock
udev                  942M  168K  942M   1% /dev
tmpfs                 942M     0  942M   0% /dev/shm
lrm                   942M  2.2M  940M   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda6             584G  166M  584G   1% /var/lib

==> uname -a <==
Linux mythbuntu-desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 SATA controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7050/nForce 610i (rev a2)
01:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

==> lsusb <==
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 0403:f850 Future Technology Devices International, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegistryDwords: ""

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
GCC version:  gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) 

==> /proc/driver/nvidia/warnings <==
Model: 		 GeForce 7050 / NVIDIA nForce 610i
IRQ:   		 23
Video BIOS: 	 05.73.32.12.00
Card Type: 	 PCI
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 00.10.0

==> lshw <==
computer
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1883MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: [REMOVED]
          size: 2800MHz
          capacity: 2800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:5 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:6 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.5
             bus info: pci@0000:00:01.5
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:7 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:8 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP73 LPC Bridge
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: MCP73 SMBus
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: latency=0
        *-memory:9 UNCLAIMED
             description: RAM memory
             product: MCP73 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: MCP73 Memory Controller
             vendor: nVidia Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: GeForce 7100/nForce 630i
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
        *-usb:1
             description: USB Controller
             product: MCP73 [nForce 630i] USB 2.0 Controller (EHCI)
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-ide
             description: IDE interface
             product: MCP73 IDE
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
        *-multimedia
             description: Audio device
             product: MCP73 High Definition Audio
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-multimedia
                description: Multimedia video controller
                product: iTVC16 (CX23416) MPEG-2 Encoder
                vendor: Internext Compression Inc
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ivtv latency=64 maxlatency=8 mingnt=128 module=ivtv
        *-pci:1
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-storage
             description: SATA controller
             product: GeForce 7100/nForce 630i
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
        *-network
             description: Ethernet interface
             product: MCP73 Ethernet
             vendor: nVidia Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: eth0
             version: a2
             serial: [REMOVED]
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=[REMOVED] latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
        *-display
             description: VGA compatible controller
             product: GeForce 7050/nForce 610i
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a2
             width: 64 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Any help would be greatly appreciated

---

