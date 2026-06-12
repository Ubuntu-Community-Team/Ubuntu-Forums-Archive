---
title: "toshiba mx40 detect monitors blank screen no panels or windows"
date: 2009-12-16
forum: Hardware
---

### Post by wayneox on 2009-12-16
ok, i have been using ubuntu a while now... no real problems,,,, a cpl of reinstalls due to my own cock ups etc, but still cool.. any how, bought a new tv the other day, so come to connect my laptop to it,. worked great...  but i had two blank lines on the left n right due to it being widescreen and only getting a 4:3 image, so edited display today, set it to 16:9 onto my tele, clicked apply and bang. tele and laptop lcd is black, all i see is my cursor,,, 
do not even see background.

all windows panels etc close. move to ttyl1 and service gdm stop, disconnect tele and startx brilliant... lcd back to normal.. connect tele. go to display, detect monitor, and bang back to black... [without applying] and now cannot even move to ttyl1 via ctrl alt n f1, have to hard reset using power button.

i tried looking at /etc/X11/xorg.conf but doesnt exist...
so by applying alternative settings the first time where did this save, i can deal with lines... at least could connect to my new tele... but now i cant...

alternatively. does anyone know what i need to put into xorg.conf so it'll work correctly... i would prefer mirrored screen at 16:9 if needed since ill be using it on tele a lot now

cheers guys.

---

### Post by wayneox on 2009-12-17
anyone?... any hints?  for addition, if TV is NOT connected the Detect monitors button doesnt do anything...
tele is on vga connection to vga on tv...

not sure if this from syslog will help but ill put it anyhow...

```

Dec 17 00:08:36 wayne-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="795" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Dec 17 00:08:50 wayne-laptop anacron[1838]: Job `cron.daily' terminated
Dec 17 00:08:50 wayne-laptop anacron[1838]: Job `cron.weekly' started
Dec 17 00:08:50 wayne-laptop anacron[2383]: Updated timestamp for job `cron.weekly' to 2009-12-17
Dec 17 00:09:37 wayne-laptop init: gdm main process (811) killed by KILL signal
Dec 17 00:09:40 wayne-laptop NetworkManager: <info>  (eth1): device state change: 8 -> 3 (reason 38)
Dec 17 00:09:40 wayne-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 38).
Dec 17 00:09:41 wayne-laptop NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 1601
Dec 17 00:09:42 wayne-laptop NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess#012
Dec 17 00:09:42 wayne-laptop avahi-daemon[809]: Withdrawing address record for 192.168.1.3 on eth1.
Dec 17 00:09:42 wayne-laptop avahi-daemon[809]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.3.
Dec 17 00:09:42 wayne-laptop avahi-daemon[809]: Interface eth1.IPv4 no longer relevant for mDNS.
Dec 17 00:09:43 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 17 00:09:43 wayne-laptop wpa_supplicant[903]: Associated with 00:00:00:00:00:00
Dec 17 00:09:43 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 17 00:09:43 wayne-laptop wpa_supplicant[903]: WPA: No SSID info found (msg 1 of 4).
Dec 17 00:09:47 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:09:49 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:09:53 wayne-laptop wpa_supplicant[903]: Authentication with 00:00:00:00:00:00 timed out.
Dec 17 00:09:53 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:09:57 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:02 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:06 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:11 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:15 wayne-laptop anacron[1838]: Job `cron.weekly' terminated
Dec 17 00:10:15 wayne-laptop anacron[1838]: Normal exit (2 jobs run)
Dec 17 00:10:15 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:20 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:24 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:28 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:33 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:37 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:41 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:45 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:50 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:54 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:10:58 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:03 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:07 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:09 wayne-laptop acpid: client 989[0:0] has disconnected
Dec 17 00:11:09 wayne-laptop acpid: client connected from 2562[0:0]
Dec 17 00:11:10 wayne-laptop kernel: [ 4006.409983] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:10 wayne-laptop kernel: [ 4006.515035] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:10 wayne-laptop kernel: [ 4006.717323] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:10 wayne-laptop kernel: [ 4006.857692] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:10 wayne-laptop kernel: [ 4007.002454] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:10 wayne-laptop kernel: [ 4007.107389] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:10 wayne-laptop kernel: [ 4007.334773] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:11 wayne-laptop kernel: [ 4007.475050] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:11 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:14 wayne-laptop kernel: [ 4011.221817] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:14 wayne-laptop kernel: [ 4011.327370] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:15 wayne-laptop kernel: [ 4011.542997] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:15 wayne-laptop kernel: [ 4011.684971] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:15 wayne-laptop kernel: [ 4011.835283] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:15 wayne-laptop kernel: [ 4011.947625] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:15 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:15 wayne-laptop kernel: [ 4012.160035] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:15 wayne-laptop kernel: [ 4012.303446] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:16 wayne-laptop kernel: [ 4012.465557] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:16 wayne-laptop kernel: [ 4012.573004] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:16 wayne-laptop kernel: [ 4012.780433] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:16 wayne-laptop kernel: [ 4012.921679] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:19 wayne-laptop kernel: [ 4015.942786] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:19 wayne-laptop kernel: [ 4016.047911] [drm] DAC-6: set mode 640x480 0
Dec 17 00:11:19 wayne-laptop kernel: [ 4016.250589] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:19 wayne-laptop kernel: [ 4016.390856] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:11:20 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:24 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:28 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:33 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:37 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:42 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:46 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:49 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:53 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:11:57 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:02 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:06 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:10 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:14 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:19 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:23 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:27 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:32 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:36 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:40 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:44 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:49 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:53 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:12:57 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:02 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:06 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:10 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:14 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:19 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:23 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:27 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:32 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:36 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:40 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:44 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:49 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:53 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:13:57 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:02 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:06 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:10 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:15 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:19 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:23 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:27 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:32 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:36 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:40 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:44 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:49 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:53 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:14:57 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:02 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:06 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:10 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:14 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:19 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:23 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:25 wayne-laptop acpid: client 2562[0:0] has disconnected
Dec 17 00:15:25 wayne-laptop acpid: client connected from 2562[0:0]
Dec 17 00:15:27 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:32 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:36 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:40 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:45 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:49 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:53 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:15:58 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:02 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:06 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:10 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:14 wayne-laptop kernel: [ 4310.521866] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:14 wayne-laptop kernel: [ 4310.627229] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:14 wayne-laptop kernel: [ 4310.830736] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:14 wayne-laptop kernel: [ 4310.971027] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:15 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:17 wayne-laptop kernel: [ 4314.224016] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:17 wayne-laptop kernel: [ 4314.329411] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:18 wayne-laptop kernel: [ 4314.532024] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:18 wayne-laptop kernel: [ 4314.672326] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:19 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:23 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:24 wayne-laptop kernel: [ 4320.646626] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:24 wayne-laptop kernel: [ 4320.751882] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:24 wayne-laptop kernel: [ 4320.954518] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:24 wayne-laptop kernel: [ 4321.094934] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:27 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:29 wayne-laptop kernel: [ 4325.770375] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:29 wayne-laptop kernel: [ 4325.875625] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:29 wayne-laptop kernel: [ 4326.082074] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:29 wayne-laptop kernel: [ 4326.222400] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:31 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:35 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:36 wayne-laptop kernel: [ 4332.662080] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:36 wayne-laptop kernel: [ 4332.767338] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:36 wayne-laptop kernel: [ 4332.969992] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:36 wayne-laptop kernel: [ 4333.110759] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:36 wayne-laptop kernel: [ 4333.260863] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:36 wayne-laptop kernel: [ 4333.366009] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:37 wayne-laptop kernel: [ 4333.568773] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:37 wayne-laptop kernel: [ 4333.709228] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:40 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:45 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:47 wayne-laptop kernel: [ 4343.625089] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:47 wayne-laptop kernel: [ 4343.730329] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:47 wayne-laptop kernel: [ 4343.932969] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:47 wayne-laptop kernel: [ 4344.073299] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:47 wayne-laptop kernel: [ 4344.222240] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:47 wayne-laptop kernel: [ 4344.327378] [drm] DAC-6: set mode 640x480 0
Dec 17 00:16:48 wayne-laptop kernel: [ 4344.529976] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:48 wayne-laptop kernel: [ 4344.670225] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:16:48 wayne-laptop kernel: [ 4345.190330] [drm] LVDS-8: set mode  18
Dec 17 00:16:49 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:53 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:16:58 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:01 wayne-laptop kernel: [ 4357.538588] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:01 wayne-laptop kernel: [ 4357.644360] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:01 wayne-laptop kernel: [ 4357.847447] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:01 wayne-laptop kernel: [ 4357.988129] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:02 wayne-laptop kernel: [ 4358.504420] [drm] LVDS-8: set mode  1c
Dec 17 00:17:02 wayne-laptop CRON[2878]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 17 00:17:02 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:06 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:07 wayne-laptop kernel: [ 4363.577327] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:07 wayne-laptop kernel: [ 4363.682553] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:07 wayne-laptop kernel: [ 4363.885212] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:07 wayne-laptop kernel: [ 4364.025527] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:07 wayne-laptop kernel: [ 4364.174676] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:07 wayne-laptop kernel: [ 4364.279820] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:08 wayne-laptop kernel: [ 4364.482421] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:08 wayne-laptop kernel: [ 4364.622707] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:10 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:14 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:18 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:20 wayne-laptop kernel: [ 4376.990602] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:20 wayne-laptop kernel: [ 4377.095863] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:20 wayne-laptop kernel: [ 4377.298467] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:20 wayne-laptop kernel: [ 4377.438723] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:21 wayne-laptop kernel: [ 4377.589656] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:21 wayne-laptop kernel: [ 4377.695318] [drm] DAC-6: set mode 640x480 0
Dec 17 00:17:21 wayne-laptop kernel: [ 4377.898317] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:21 wayne-laptop kernel: [ 4378.038888] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:22 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:26 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:30 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:35 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:39 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:43 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:48 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:49 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:52 wayne-laptop kernel: [ 4409.008026] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:52 wayne-laptop kernel: [ 4409.148482] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:17:52 wayne-laptop kernel: [ 4409.399441] [drm] DAC-6: set mode  1d
Dec 17 00:17:53 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:17:57 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:01 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:05 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:10 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:14 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:18 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:23 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:27 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:31 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:18:35 wayne-laptop wpa_supplicant[903]: CTRL-EVENT-SCAN-RESULTS 







HARD RESET HERE.......





Dec 17 00:32:16 wayne-laptop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 17 00:32:16 wayne-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="771" x-info="http://www.rsyslog.com"] (re)start
Dec 17 00:32:16 wayne-laptop rsyslogd: rsyslogd's groupid changed to 102
Dec 17 00:32:16 wayne-laptop rsyslogd: rsyslogd's userid changed to 101
Dec 17 00:32:16 wayne-laptop init: ureadahead-other main process (758) terminated with status 4
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 17 00:32:16 wayne-laptop rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: Successfully dropped root privileges.
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: avahi-daemon 0.6.25 starting up.
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: Successfully called chroot().
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: Successfully dropped remaining capabilities.
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  starting...
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] KERNEL supported cpus:
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   Intel GenuineIntel
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   AMD AuthenticAMD
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   NSC Geode by NSC
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   Cyrix CyrixInstead
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   Centaur CentaurHauls
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   UMC UMC UMC UMC
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6ea000 (ACPI data)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 000000001f6ea000 - 000000001f700000 (ACPI NVS)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] DMI present.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] last_pfn = 0x1f6e0 max_arch_pfn = 0x100000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] MTRR default type: uncachable
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   00000-9FFFF write-back
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   C0000-CFFFF write-protect
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   D0000-E3FFF uncachable
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   E4000-FFFFF write-protect
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   0 base 000000000 mask FE0000000 write-back
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   1 base 01F700000 mask FFFF00000 uncachable
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   2 base 01F800000 mask FFF800000 uncachable
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   3 disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   4 disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   5 disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   6 disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   7 disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] PAT not supported by CPU.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] modified physical RAM map:
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 0000000000100000 - 000000001f6e0000 (usable)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 000000001f6e0000 - 000000001f6ea000 (ACPI data)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 000000001f6ea000 - 000000001f700000 (ACPI NVS)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 000000001f700000 - 0000000020000000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0006000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000001f6e0000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  0000400000 - 001f400000 page 2M
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]  001f400000 - 001f6e0000 page 4k
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] kernel direct mapping tables up to 1f6e0000 @ 7000-c000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] RAMDISK: 1721d000 - 17967293
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: RSDP 000f6b70 00014 (v00 TOSCPL)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: RSDT 1f6e33f6 00048 (v01 TOSCPL   RSDT   06040000  LTP 00000000)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: APIC 1f6e9e88 00068 (v01 INTEL  ALVISO   06040000 LOHR 0000005F)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: FACP 1f6e9ef0 00074 (v01 TOSCPL ALVISO   06040000 LOHR 00000032)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: DSDT 1f6e495f 05529 (v01 TOSCPL ALVISO   06040000 MSFT 0100000E)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: FACS 1f6fafc0 00040
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: BOOT 1f6e9fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: MCFG 1f6e9f9c 0003C (v01 INTEL  ALVISO   06040000 LOHR 0000005F)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: SSDT 1f6e430c 0064F (v01 SataRe  SataPri 00001000 INTL 20030224)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: SSDT 1f6e3c7a 00692 (v01 SataRe  SataSec 00001000 INTL 20030224)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: SSDT 1f6e3835 00235 (v01  PmRef  Cpu0Ist 00003000 INTL 20030224)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: SSDT 1f6e3657 001DE (v01  PmRef  Cpu0Cst 00003001 INTL 20030224)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: SSDT 1f6e343e 00219 (v01  PmRef    CpuPm 00003000 INTL 20030224)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] 0MB HIGHMEM available.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] 502MB LOWMEM available.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   mapped low ram: 0 - 1f6e0000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   low ram: 0 - 1f6e0000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   node 0 low ram: 00000000 - 1f6e0000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000bedc
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f6e0000]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #4 [001721d000 - 0017967293]          RAMDISK ==> [001721d000 - 0017967293]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #6 [00008a9000 - 00008ac0f0]              BRK ==> [00008a9000 - 00008ac0f0]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000]
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Zone PFN ranges:
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x0001f6e0
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   HighMem  0x0001f6e0 -> 0x0001f6e0
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Movable zone start PFN for each node
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] early_node_map[3] active PFN ranges
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0001f6e0
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] On node 0 totalpages: 128635
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1000000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   Normal zone: 974 pages used for memmap
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]   Normal zone: 123666 pages, LIFO batch:31
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Using APIC driver default
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] nr_irqs_gsi: 24
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] PERCPU: Embedded 14 pages at c13f2000, static data 35612 bytes
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127629
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=45b43022-847d-4189-9140-627184115e7d ro quiet splash
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Initializing CPU#0
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] allocated 2574720 bytes of page_cgroup
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Memory: 491668k/514944k available (4566k kernel code, 22424k reserved, 2142k data, 540k init, 0k highmem)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] virtual kernel memory layout:
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]     vmalloc : 0xdfee0000 - 0xff7fe000   ( 505 MB)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Dec 17 00:32:16 wayne-laptop kernel: [    0.000000] Detected 1595.888 MHz processor.
Dec 17 00:32:16 wayne-laptop kernel: [    0.001843] Console: colour VGA+ 80x25
Dec 17 00:32:16 wayne-laptop kernel: [    0.001848] console [tty0] enabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.001914] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.77 BogoMIPS (lpj=6383552)
Dec 17 00:32:16 wayne-laptop kernel: [    0.001943] Security Framework initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.001967] AppArmor: AppArmor initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.001978] Mount-cache hash table entries: 512
Dec 17 00:32:16 wayne-laptop kernel: [    0.002142] Initializing cgroup subsys ns
Dec 17 00:32:16 wayne-laptop kernel: [    0.002148] Initializing cgroup subsys cpuacct
Dec 17 00:32:16 wayne-laptop kernel: [    0.002153] Initializing cgroup subsys memory
Dec 17 00:32:16 wayne-laptop kernel: [    0.002162] Initializing cgroup subsys freezer
Dec 17 00:32:16 wayne-laptop kernel: [    0.002165] Initializing cgroup subsys net_cls
Dec 17 00:32:16 wayne-laptop kernel: [    0.002186] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 17 00:32:16 wayne-laptop kernel: [    0.002189] CPU: L2 cache: 2048K
Dec 17 00:32:16 wayne-laptop kernel: [    0.002194] mce: CPU supports 5 MCE banks
Dec 17 00:32:16 wayne-laptop kernel: [    0.002205] CPU0: Thermal monitoring enabled (TM1)
Dec 17 00:32:16 wayne-laptop kernel: [    0.002215] Performance Counters: p6 PMU driver.
Dec 17 00:32:16 wayne-laptop kernel: [    0.002235] ... version:                 0
Dec 17 00:32:16 wayne-laptop kernel: [    0.002237] ... bit width:               32
Dec 17 00:32:16 wayne-laptop kernel: [    0.002239] ... generic counters:        2
Dec 17 00:32:16 wayne-laptop kernel: [    0.002242] ... value mask:              00000000ffffffff
Dec 17 00:32:16 wayne-laptop kernel: [    0.002244] ... max period:              000000007fffffff
Dec 17 00:32:16 wayne-laptop kernel: [    0.002247] ... fixed-purpose counters:  0
Dec 17 00:32:16 wayne-laptop kernel: [    0.002249] ... counter mask:            0000000000000003
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: No service file found in /etc/avahi/services.
Dec 17 00:32:16 wayne-laptop kernel: [    0.002253] Checking 'hlt' instruction... OK.
Dec 17 00:32:16 wayne-laptop kernel: [    0.016946] SMP alternatives: switching to UP code
Dec 17 00:32:16 wayne-laptop kernel: [    0.024004] ACPI: Core revision 20090521
Dec 17 00:32:16 wayne-laptop kernel: [    0.036439] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 17 00:32:16 wayne-laptop kernel: [    0.079223] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] Brought up 1 CPUs
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] Total of 1 processors activated (3191.77 BogoMIPS).
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] CPU0 attaching NULL sched-domain.
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] Booting paravirtualized kernel on bare hardware
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] regulator: core version 0.5
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] Time:  0:31:44  Date: 12/17/09
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] NET: Registered protocol family 16
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] EISA bus registered
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] ACPI: bus type pci registered
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] PCI: MCFG area at e0000000 reserved in E820
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] PCI: Using MMCONFIG for extended config space
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] PCI: Using configuration type 1 for base access
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] bio: create slab <bio-0> at 0
Dec 17 00:32:16 wayne-laptop kernel: [    0.080001] ACPI: EC: Look up EC in DSDT
Dec 17 00:32:16 wayne-laptop kernel: [    0.082033] ACPI: Interpreter enabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.082040] ACPI: (supports S0 S3 S4 S5)
Dec 17 00:32:16 wayne-laptop kernel: [    0.082065] ACPI: Using IOAPIC for interrupt routing
Dec 17 00:32:16 wayne-laptop kernel: [    0.082833] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
Dec 17 00:32:16 wayne-laptop kernel: [    0.124653] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
Dec 17 00:32:16 wayne-laptop kernel: [    0.124656] ACPI: EC: driver started in poll mode
Dec 17 00:32:16 wayne-laptop kernel: [    0.125061] ACPI: No dock devices found.
Dec 17 00:32:16 wayne-laptop kernel: [    0.125692] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 17 00:32:16 wayne-laptop kernel: [    0.125781] pci 0000:00:02.0: reg 10 32bit mmio: [0xb0080000-0xb00fffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.125787] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
Dec 17 00:32:16 wayne-laptop kernel: [    0.125793] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.125798] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0000000-0xb003ffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.125832] pci 0000:00:02.1: reg 10 32bit mmio: [0x000000-0x07ffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.125944] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126007] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126071] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126134] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126205] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb0040000-0xb00403ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126268] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Dec 17 00:32:16 wayne-laptop kernel: [    0.126274] pci 0000:00:1d.7: PME# disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.126380] pci 0000:00:1e.2: reg 10 io port: [0x1c00-0x1cff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126388] pci 0000:00:1e.2: reg 14 io port: [0x18c0-0x18ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126397] pci 0000:00:1e.2: reg 18 32bit mmio: [0xb0040800-0xb00409ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126406] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xb0040400-0xb00404ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126446] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
Dec 17 00:32:16 wayne-laptop kernel: [    0.126451] pci 0000:00:1e.2: PME# disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.126490] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126499] pci 0000:00:1e.3: reg 14 io port: [0x2000-0x207f]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126548] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
Dec 17 00:32:16 wayne-laptop kernel: [    0.126554] pci 0000:00:1e.3: PME# disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.126644] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
Dec 17 00:32:16 wayne-laptop kernel: [    0.126652] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Dec 17 00:32:16 wayne-laptop kernel: [    0.126657] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Dec 17 00:32:16 wayne-laptop kernel: [    0.126704] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126713] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  Trying to start the modem-manager...
Dec 17 00:32:16 wayne-laptop kernel: [    0.126722] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126730] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126739] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126774] pci 0000:00:1f.2: PME# supported from D3hot
Dec 17 00:32:16 wayne-laptop kernel: [    0.126779] pci 0000:00:1f.2: PME# disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.126842] pci 0000:00:1f.3: reg 20 io port: [0x20a0-0x20bf]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126924] pci 0000:06:01.0: reg 10 io port: [0x3000-0x30ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126934] pci 0000:06:01.0: reg 14 32bit mmio: [0xb0106000-0xb01060ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.126996] pci 0000:06:01.0: supports D1 D2
Dec 17 00:32:16 wayne-laptop kernel: [    0.126999] pci 0000:06:01.0: PME# supported from D1 D2 D3hot D3cold
Dec 17 00:32:16 wayne-laptop kernel: [    0.127005] pci 0000:06:01.0: PME# disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.127054] pci 0000:06:02.0: reg 10 32bit mmio: [0xb0107000-0xb0107fff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.127124] pci 0000:06:02.0: PME# supported from D0 D3hot D3cold
Dec 17 00:32:16 wayne-laptop kernel: [    0.127130] pci 0000:06:02.0: PME# disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.127181] pci 0000:06:04.0: reg 10 32bit mmio: [0xb0108000-0xb0108fff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.127209] pci 0000:06:04.0: supports D1 D2
Dec 17 00:32:16 wayne-laptop kernel: [    0.127212] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 17 00:32:16 wayne-laptop kernel: [    0.127218] pci 0000:06:04.0: PME# disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.127271] pci 0000:06:04.2: reg 10 32bit mmio: [0xb0106800-0xb0106fff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.127282] pci 0000:06:04.2: reg 14 32bit mmio: [0xb0100000-0xb0103fff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.127348] pci 0000:06:04.2: supports D1 D2
Dec 17 00:32:16 wayne-laptop kernel: [    0.127351] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
Dec 17 00:32:16 wayne-laptop kernel: [    0.127357] pci 0000:06:04.2: PME# disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.127406] pci 0000:06:04.3: reg 10 32bit mmio: [0xb0104000-0xb0105fff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.127475] pci 0000:06:04.3: supports D1 D2
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: init!
Dec 17 00:32:16 wayne-laptop kernel: [    0.127477] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
Dec 17 00:32:16 wayne-laptop kernel: [    0.127483] pci 0000:06:04.3: PME# disabled
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Dec 17 00:32:16 wayne-laptop kernel: [    0.127532] pci 0000:06:04.4: reg 10 32bit mmio: [0xb0109400-0xb01094ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.127542] pci 0000:06:04.4: reg 14 32bit mmio: [0xb0109000-0xb01090ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.127553] pci 0000:06:04.4: reg 18 32bit mmio: [0xb0106400-0xb01064ff]
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Dec 17 00:32:16 wayne-laptop kernel: [    0.127608] pci 0000:06:04.4: supports D1 D2
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth0, iface: eth0)
Dec 17 00:32:16 wayne-laptop kernel: [    0.127611] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
Dec 17 00:32:16 wayne-laptop kernel: [    0.127617] pci 0000:06:04.4: PME# disabled
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 17 00:32:16 wayne-laptop kernel: [    0.127679] pci 0000:00:1e.0: transparent bridge
Dec 17 00:32:16 wayne-laptop kernel: [    0.127685] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:02.0/net/eth1, iface: eth1)
Dec 17 00:32:16 wayne-laptop kernel: [    0.127691] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:06:02.0/net/eth1, iface: eth1): no ifupdown configuration found.
Dec 17 00:32:16 wayne-laptop kernel: [    0.127729] pci_bus 0000:00: on NUMA node 0
Dec 17 00:32:16 wayne-laptop kernel: [    0.127736] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 17 00:32:16 wayne-laptop kernel: [    0.127944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Dec 17 00:32:16 wayne-laptop kernel: [    0.133335] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 17 00:32:16 wayne-laptop kernel: [    0.133454] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: end _init.
Dec 17 00:32:16 wayne-laptop kernel: [    0.133567] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Dec 17 00:32:16 wayne-laptop kernel: [    0.133683] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Dec 17 00:32:16 wayne-laptop NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 17 00:32:16 wayne-laptop kernel: [    0.133800] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Dec 17 00:32:16 wayne-laptop kernel: [    0.133921] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Dec 17 00:32:16 wayne-laptop NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 17 00:32:16 wayne-laptop kernel: [    0.134041] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Dec 17 00:32:16 wayne-laptop kernel: [    0.134158] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Dec 17 00:32:16 wayne-laptop kernel: [    0.134365] SCSI subsystem initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.134413] libata version 3.00 loaded.
Dec 17 00:32:16 wayne-laptop kernel: [    0.134496] usbcore: registered new interface driver usbfs
Dec 17 00:32:16 wayne-laptop kernel: [    0.134520] usbcore: registered new interface driver hub
Dec 17 00:32:16 wayne-laptop kernel: [    0.134550] usbcore: registered new device driver usb
Dec 17 00:32:16 wayne-laptop kernel: [    0.134698] ACPI: WMI: Mapper loaded
Dec 17 00:32:16 wayne-laptop kernel: [    0.134700] PCI: Using ACPI for IRQ routing
Dec 17 00:32:16 wayne-laptop kernel: [    0.134883] Bluetooth: Core ver 2.15
Dec 17 00:32:16 wayne-laptop kernel: [    0.134913] NET: Registered protocol family 31
Dec 17 00:32:16 wayne-laptop kernel: [    0.134915] Bluetooth: HCI device and connection manager initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.134918] Bluetooth: HCI socket layer initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.134921] NetLabel: Initializing
Dec 17 00:32:16 wayne-laptop kernel: [    0.134923] NetLabel:  domain hash size = 128
Dec 17 00:32:16 wayne-laptop kernel: [    0.134925] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 17 00:32:16 wayne-laptop kernel: [    0.134941] NetLabel:  unlabeled traffic allowed by default
Dec 17 00:32:16 wayne-laptop kernel: [    0.135113] hpet clockevent registered
Dec 17 00:32:16 wayne-laptop kernel: [    0.135117] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Dec 17 00:32:16 wayne-laptop kernel: [    0.135125] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 17 00:32:16 wayne-laptop kernel: [    0.135131] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Dec 17 00:32:16 wayne-laptop kernel: [    0.142112] pnp: PnP ACPI init
Dec 17 00:32:16 wayne-laptop kernel: [    0.142136] ACPI: bus type pnp registered
Dec 17 00:32:16 wayne-laptop kernel: [    0.164150] pnp: PnP ACPI: found 9 devices
Dec 17 00:32:16 wayne-laptop kernel: [    0.164153] ACPI: ACPI bus type pnp unregistered
Dec 17 00:32:16 wayne-laptop kernel: [    0.164157] PnPBIOS: Disabled by ACPI PNP
Dec 17 00:32:16 wayne-laptop kernel: [    0.164170] system 00:01: ioport range 0xfe00-0xfe7f has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164174] system 00:01: ioport range 0xfe80-0xfeff has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164178] system 00:01: ioport range 0xff00-0xff7f has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164183] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164187] system 00:01: iomem range 0xf0000000-0xf0003fff has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164191] system 00:01: iomem range 0xf0004000-0xf0004fff has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164194] system 00:01: iomem range 0xf0005000-0xf0005fff has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164198] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164202] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164210] system 00:05: ioport range 0x800-0x80f has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164214] system 00:05: ioport range 0x1000-0x107f has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164218] system 00:05: ioport range 0x1180-0x11bf has been reserved
Dec 17 00:32:16 wayne-laptop kernel: [    0.164222] system 00:05: ioport range 0x1640-0x164f has been reserved
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Option
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin MotoC
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Gobi
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Option High-Speed
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Sierra
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Generic
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Nokia
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Huawei
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Novatel
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin Ericsson MBM
Dec 17 00:32:16 wayne-laptop modem-manager: Loaded plugin ZTE
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: (153697008) ... get_connections.
Dec 17 00:32:16 wayne-laptop NetworkManager:    SCPlugin-Ifupdown: (153697008) ... get_connections (managed=false): return empty list.
Dec 17 00:32:16 wayne-laptop kernel: [    0.198930] AppArmor: AppArmor Filesystem Enabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.198971] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
Dec 17 00:32:16 wayne-laptop kernel: [    0.198975] pci 0000:06:04.0:   IO window: 0x003400-0x0034ff
Dec 17 00:32:16 wayne-laptop kernel: [    0.198981] pci 0000:06:04.0:   IO window: 0x003800-0x0038ff
Dec 17 00:32:16 wayne-laptop kernel: [    0.198988] pci 0000:06:04.0:   PREFETCH window: 0x20000000-0x23ffffff
Dec 17 00:32:16 wayne-laptop kernel: [    0.198998] pci 0000:06:04.0:   MEM window: 0x28000000-0x2bffffff
Dec 17 00:32:16 wayne-laptop kernel: [    0.199005] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
Dec 17 00:32:16 wayne-laptop kernel: [    0.199009] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
Dec 17 00:32:16 wayne-laptop kernel: [    0.199016] pci 0000:00:1e.0:   MEM window: 0xb0100000-0xb01fffff
Dec 17 00:32:16 wayne-laptop kernel: [    0.199022] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
Dec 17 00:32:16 wayne-laptop kernel: [    0.199039] pci 0000:00:1e.0: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [    0.199051]   alloc irq_desc for 16 on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.199054]   alloc kstat_irqs on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.199061] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 17 00:32:16 wayne-laptop kernel: [    0.199069] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199073] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199077] pci_bus 0000:06: resource 0 io:  [0x3000-0x3fff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199080] pci_bus 0000:06: resource 1 mem: [0xb0100000-0xb01fffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199084] pci_bus 0000:06: resource 2 pref mem [0x20000000-0x23ffffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199087] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199091] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199094] pci_bus 0000:07: resource 0 io:  [0x3400-0x34ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199098] pci_bus 0000:07: resource 1 io:  [0x3800-0x38ff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199101] pci_bus 0000:07: resource 2 pref mem [0x20000000-0x23ffffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199105] pci_bus 0000:07: resource 3 mem: [0x28000000-0x2bffffff]
Dec 17 00:32:16 wayne-laptop kernel: [    0.199146] NET: Registered protocol family 2
Dec 17 00:32:16 wayne-laptop kernel: [    0.199259] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Dec 17 00:32:16 wayne-laptop kernel: [    0.199572] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Dec 17 00:32:16 wayne-laptop kernel: [    0.199693] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Dec 17 00:32:16 wayne-laptop kernel: [    0.199816] TCP: Hash tables configured (established 16384 bind 16384)
Dec 17 00:32:16 wayne-laptop kernel: [    0.199820] TCP reno registered
Dec 17 00:32:16 wayne-laptop kernel: [    0.199907] NET: Registered protocol family 1
Dec 17 00:32:16 wayne-laptop kernel: [    0.199984] Trying to unpack rootfs image as initramfs...
Dec 17 00:32:16 wayne-laptop kernel: [    0.461298] Freeing initrd memory: 7464k freed
Dec 17 00:32:16 wayne-laptop kernel: [    0.468422] Simple Boot Flag at 0x36 set to 0x1
Dec 17 00:32:16 wayne-laptop kernel: [    0.468540] cpufreq-nforce2: No nForce2 chipset.
Dec 17 00:32:16 wayne-laptop kernel: [    0.468581] Scanning for low memory corruption every 60 seconds
Dec 17 00:32:16 wayne-laptop kernel: [    0.468748] audit: initializing netlink socket (disabled)
Dec 17 00:32:16 wayne-laptop kernel: [    0.468773] type=2000 audit(1261009904.468:1): initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.479822] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec 17 00:32:16 wayne-laptop kernel: [    0.481637] VFS: Disk quotas dquot_6.5.2
Dec 17 00:32:16 wayne-laptop kernel: [    0.481712] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 17 00:32:16 wayne-laptop kernel: [    0.482402] fuse init (API version 7.12)
Dec 17 00:32:16 wayne-laptop kernel: [    0.482507] msgmni has been set to 975
Dec 17 00:32:16 wayne-laptop kernel: [    0.482756] alg: No test for stdrng (krng)
Dec 17 00:32:16 wayne-laptop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth0): carrier is OFF
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: '8139too')
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth0): now managed
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth0): bringing up device.
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth0): preparing device.
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Dec 17 00:32:16 wayne-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/net/eth0
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): driver supports SSID scans (scan_capa 0x21).
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'ipw2200')
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): now managed
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): device state change: 1 -> 2 (reason 2)
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): bringing up device.
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): preparing device.
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): deactivating device (reason: 2).
Dec 17 00:32:16 wayne-laptop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Dec 17 00:32:16 wayne-laptop kernel: [    0.482771] io scheduler noop registered
Dec 17 00:32:16 wayne-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 17 00:32:16 wayne-laptop kernel: [    0.482773] io scheduler anticipatory registered
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  modem-manager is now available
Dec 17 00:32:16 wayne-laptop kernel: [    0.482776] io scheduler deadline registered
Dec 17 00:32:16 wayne-laptop kernel: [    0.482831] io scheduler cfq registered (default)
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  Trying to start the supplicant...
Dec 17 00:32:16 wayne-laptop kernel: [    0.482848] pci 0000:00:02.0: Boot video device
Dec 17 00:32:16 wayne-laptop kernel: [    0.483058] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 17 00:32:16 wayne-laptop kernel: [    0.483090] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 17 00:32:16 wayne-laptop kernel: [    0.483314] ACPI: AC Adapter [ACAD] (on-line)
Dec 17 00:32:16 wayne-laptop kernel: [    0.483420] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Dec 17 00:32:16 wayne-laptop kernel: [    0.483428] ACPI: Power Button [PWRF]
Dec 17 00:32:16 wayne-laptop kernel: [    0.483492] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
Dec 17 00:32:16 wayne-laptop kernel: [    0.483535] ACPI: Lid Switch [LID0]
Dec 17 00:32:16 wayne-laptop kernel: [    0.483586] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
Dec 17 00:32:16 wayne-laptop kernel: [    0.483590] ACPI: Power Button [PWRB]
Dec 17 00:32:16 wayne-laptop kernel: [    0.484035] Marking TSC unstable due to TSC halts in idle
Dec 17 00:32:16 wayne-laptop kernel: [    0.484084] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Dec 17 00:32:16 wayne-laptop kernel: [    0.484114] processor LNXCPU:00: registered as cooling_device0
Dec 17 00:32:16 wayne-laptop kernel: [    0.488096] Switched to high resolution mode on CPU 0
Dec 17 00:32:16 wayne-laptop kernel: [    0.504237] isapnp: Scanning for PnP cards...
Dec 17 00:32:16 wayne-laptop kernel: [    0.597552] ACPI: Battery Slot [BAT1] (battery present)
Dec 17 00:32:16 wayne-laptop kernel: [    0.858784] isapnp: No Plug & Play device found
Dec 17 00:32:16 wayne-laptop kernel: [    0.860092] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.860491]   alloc irq_desc for 20 on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.860495]   alloc kstat_irqs on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.860504] serial 0000:00:1e.3: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Dec 17 00:32:16 wayne-laptop kernel: [    0.860512] serial 0000:00:1e.3: PCI INT B disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.861626] brd: module loaded
Dec 17 00:32:16 wayne-laptop kernel: [    0.862175] loop: module loaded
Dec 17 00:32:16 wayne-laptop kernel: [    0.862257] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Dec 17 00:32:16 wayne-laptop kernel: [    0.862343] ahci 0000:00:1f.2: version 3.0
Dec 17 00:32:16 wayne-laptop kernel: [    0.862354]   alloc irq_desc for 19 on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.862356]   alloc kstat_irqs on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.862361] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 17 00:32:16 wayne-laptop kernel: [    0.862379] ahci 0000:00:1f.2: PCI INT B disabled
Dec 17 00:32:16 wayne-laptop kernel: [    0.862384] ahci: probe of 0000:00:1f.2 failed with error -22
Dec 17 00:32:16 wayne-laptop kernel: [    0.862435] ata_piix 0000:00:1f.2: version 2.13
Dec 17 00:32:16 wayne-laptop kernel: [    0.862443] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 17 00:32:16 wayne-laptop kernel: [    0.862449] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Dec 17 00:32:16 wayne-laptop kernel: [    0.862503] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [    0.862597] scsi0 : ata_piix
Dec 17 00:32:16 wayne-laptop kernel: [    0.862686] scsi1 : ata_piix
Dec 17 00:32:16 wayne-laptop kernel: [    0.863846] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
Dec 17 00:32:16 wayne-laptop kernel: [    0.863850] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
Dec 17 00:32:16 wayne-laptop kernel: [    0.864890] Fixed MDIO Bus: probed
Dec 17 00:32:16 wayne-laptop kernel: [    0.864937] PPP generic driver version 2.4.2
Dec 17 00:32:16 wayne-laptop kernel: [    0.865034] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 17 00:32:16 wayne-laptop kernel: [    0.865053]   alloc irq_desc for 23 on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.865056]   alloc kstat_irqs on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.865061] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 17 00:32:16 wayne-laptop kernel: [    0.865076] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [    0.865082] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 17 00:32:16 wayne-laptop kernel: [    0.865148] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Dec 17 00:32:16 wayne-laptop kernel: [    0.869068] ehci_hcd 0000:00:1d.7: debug port 1
Dec 17 00:32:16 wayne-laptop kernel: [    0.869076] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Dec 17 00:32:16 wayne-laptop kernel: [    0.869334] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0040000
Dec 17 00:32:16 wayne-laptop kernel: [    0.884020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec 17 00:32:16 wayne-laptop kernel: [    0.884109] usb usb1: configuration #1 chosen from 1 choice
Dec 17 00:32:16 wayne-laptop kernel: [    0.884150] hub 1-0:1.0: USB hub found
Dec 17 00:32:16 wayne-laptop kernel: [    0.884159] hub 1-0:1.0: 8 ports detected
Dec 17 00:32:16 wayne-laptop kernel: [    0.884239] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 17 00:32:16 wayne-laptop kernel: [    0.884261] uhci_hcd: USB Universal Host Controller Interface driver
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): supplicant manager state:  down -> idle
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): device state change: 2 -> 3 (reason 0)
Dec 17 00:32:16 wayne-laptop kernel: [    0.884289] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 17 00:32:16 wayne-laptop kernel: [    0.884297] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [    0.884301] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 17 00:32:16 wayne-laptop kernel: [    0.884334] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec 17 00:32:16 wayne-laptop kernel: [    0.884361] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
Dec 17 00:32:16 wayne-laptop kernel: [    0.884456] usb usb2: configuration #1 chosen from 1 choice
Dec 17 00:32:16 wayne-laptop kernel: [    0.884495] hub 2-0:1.0: USB hub found
Dec 17 00:32:16 wayne-laptop kernel: [    0.884503] hub 2-0:1.0: 2 ports detected
Dec 17 00:32:16 wayne-laptop kernel: [    0.884558] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 17 00:32:16 wayne-laptop kernel: [    0.884565] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [    0.884570] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 17 00:32:16 wayne-laptop kernel: [    0.884606] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Dec 17 00:32:16 wayne-laptop kernel: [    0.884640] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
Dec 17 00:32:16 wayne-laptop kernel: [    0.884735] usb usb3: configuration #1 chosen from 1 choice
Dec 17 00:32:16 wayne-laptop kernel: [    0.884766] hub 3-0:1.0: USB hub found
Dec 17 00:32:16 wayne-laptop kernel: [    0.884775] hub 3-0:1.0: 2 ports detected
Dec 17 00:32:16 wayne-laptop kernel: [    0.884826]   alloc irq_desc for 18 on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.884829]   alloc kstat_irqs on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    0.884834] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 17 00:32:16 wayne-laptop kernel: [    0.884841] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [    0.884845] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 17 00:32:16 wayne-laptop kernel: [    0.884877] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Dec 17 00:32:16 wayne-laptop kernel: [    0.884912] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
Dec 17 00:32:16 wayne-laptop kernel: [    0.885009] usb usb4: configuration #1 chosen from 1 choice
Dec 17 00:32:16 wayne-laptop kernel: [    0.885040] hub 4-0:1.0: USB hub found
Dec 17 00:32:16 wayne-laptop kernel: [    0.885048] hub 4-0:1.0: 2 ports detected
Dec 17 00:32:16 wayne-laptop kernel: [    0.885102] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Dec 17 00:32:16 wayne-laptop kernel: [    0.885109] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [    0.885113] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Dec 17 00:32:16 wayne-laptop kernel: [    0.885147] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Dec 17 00:32:16 wayne-laptop kernel: [    0.885184] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
Dec 17 00:32:16 wayne-laptop kernel: [    0.885275] usb usb5: configuration #1 chosen from 1 choice
Dec 17 00:32:16 wayne-laptop kernel: [    0.885305] hub 5-0:1.0: USB hub found
Dec 17 00:32:16 wayne-laptop kernel: [    0.885312] hub 5-0:1.0: 2 ports detected
Dec 17 00:32:16 wayne-laptop kernel: [    0.885426] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 17 00:32:16 wayne-laptop kernel: [    0.885728] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 17 00:32:16 wayne-laptop kernel: [    0.885803] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 17 00:32:16 wayne-laptop kernel: [    0.885809] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 17 00:32:16 wayne-laptop kernel: [    0.885813] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 17 00:32:16 wayne-laptop kernel: [    0.885816] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 17 00:32:16 wayne-laptop kernel: [    0.885820] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 17 00:32:16 wayne-laptop kernel: [    0.885878] mice: PS/2 mouse device common for all mice
Dec 17 00:32:16 wayne-laptop kernel: [    0.886011] rtc_cmos 00:06: RTC can wake from S4
Dec 17 00:32:16 wayne-laptop NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready
Dec 17 00:32:16 wayne-laptop wpa_supplicant[879]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:32:16 wayne-laptop kernel: [    0.886048] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Dec 17 00:32:16 wayne-laptop kernel: [    0.886081] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Dec 17 00:32:16 wayne-laptop kernel: [    0.886202] device-mapper: uevent: version 1.0.3
Dec 17 00:32:16 wayne-laptop kernel: [    0.886294] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec 17 00:32:16 wayne-laptop kernel: [    0.886380] device-mapper: multipath: version 1.1.0 loaded
Dec 17 00:32:16 wayne-laptop kernel: [    0.886384] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 17 00:32:16 wayne-laptop kernel: [    0.886520] EISA: Probing bus 0 at eisa.0
Dec 17 00:32:16 wayne-laptop kernel: [    0.886527] Cannot allocate resource for EISA slot 1
Dec 17 00:32:16 wayne-laptop kernel: [    0.886530] Cannot allocate resource for EISA slot 2
Dec 17 00:32:16 wayne-laptop kernel: [    0.886533] Cannot allocate resource for EISA slot 3
Dec 17 00:32:16 wayne-laptop kernel: [    0.886554] EISA: Detected 0 cards.
Dec 17 00:32:16 wayne-laptop kernel: [    0.886659] cpuidle: using governor ladder
Dec 17 00:32:16 wayne-laptop kernel: [    0.886757] cpuidle: using governor menu
Dec 17 00:32:16 wayne-laptop kernel: [    0.887328] TCP cubic registered
Dec 17 00:32:16 wayne-laptop kernel: [    0.887515] NET: Registered protocol family 10
Dec 17 00:32:16 wayne-laptop kernel: [    0.888040] lo: Disabled Privacy Extensions
Dec 17 00:32:16 wayne-laptop kernel: [    0.888400] NET: Registered protocol family 17
Dec 17 00:32:16 wayne-laptop kernel: [    0.888419] Bluetooth: L2CAP ver 2.13
Dec 17 00:32:16 wayne-laptop kernel: [    0.888421] Bluetooth: L2CAP socket layer initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.888425] Bluetooth: SCO (Voice Link) ver 0.6
Dec 17 00:32:16 wayne-laptop kernel: [    0.888427] Bluetooth: SCO socket layer initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.888469] Bluetooth: RFCOMM TTY layer initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.888472] Bluetooth: RFCOMM socket layer initialized
Dec 17 00:32:16 wayne-laptop kernel: [    0.888475] Bluetooth: RFCOMM ver 1.11
Dec 17 00:32:16 wayne-laptop kernel: [    0.888769] Using IPI No-Shortcut mode
Dec 17 00:32:16 wayne-laptop kernel: [    0.888846] PM: Resume from disk failed.
Dec 17 00:32:16 wayne-laptop kernel: [    0.888861] registered taskstats version 1
Dec 17 00:32:16 wayne-laptop kernel: [    0.889002]   Magic number: 5:787:506
Dec 17 00:32:16 wayne-laptop kernel: [    0.889084] rtc_cmos 00:06: setting system clock to 2009-12-17 00:31:45 UTC (1261009905)
Dec 17 00:32:16 wayne-laptop kernel: [    0.889088] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 17 00:32:16 wayne-laptop kernel: [    0.889090] EDD information not available.
Dec 17 00:32:16 wayne-laptop kernel: [    0.890724] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Dec 17 00:32:16 wayne-laptop kernel: [    1.032647] ata1.00: ATA-6: HTS541060G9AT00, MB3WA5EJ, max UDMA/100
Dec 17 00:32:16 wayne-laptop kernel: [    1.032652] ata1.00: 117210240 sectors, multi 16: LBA48 
Dec 17 00:32:16 wayne-laptop kernel: [    1.032668] ata1.00: applying bridge limits
Dec 17 00:32:16 wayne-laptop kernel: [    1.048605] ata1.00: configured for UDMA/100
Dec 17 00:32:16 wayne-laptop kernel: [    1.048765] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3W PQ: 0 ANSI: 5
Dec 17 00:32:16 wayne-laptop kernel: [    1.048912] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 17 00:32:16 wayne-laptop kernel: [    1.048958] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
Dec 17 00:32:16 wayne-laptop kernel: [    1.049016] sd 0:0:0:0: [sda] Write Protect is off
Dec 17 00:32:16 wayne-laptop kernel: [    1.049019] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 17 00:32:16 wayne-laptop kernel: [    1.049049] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 17 00:32:16 wayne-laptop kernel: [    1.049200]  sda:
Dec 17 00:32:16 wayne-laptop kernel: [    1.056394] ata2.00: ATAPI: SlimtypeDVD A  DS8A1P, CX17, max UDMA/33
Dec 17 00:32:16 wayne-laptop kernel: [    1.073691]  sda1 sda2 < sda5
Dec 17 00:32:16 wayne-laptop kernel: [    1.096304] ata2.00: configured for UDMA/33
Dec 17 00:32:16 wayne-laptop kernel: [    1.100093] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A1P    CX17 PQ: 0 ANSI: 5
Dec 17 00:32:16 wayne-laptop kernel: [    1.101835]  sda6sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 17 00:32:16 wayne-laptop kernel: [    1.110564] Uniform CD-ROM driver Revision: 3.20
Dec 17 00:32:16 wayne-laptop kernel: [    1.110651] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec 17 00:32:16 wayne-laptop kernel: [    1.110697] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec 17 00:32:16 wayne-laptop kernel: [    1.122333]  sda7 >
Dec 17 00:32:16 wayne-laptop kernel: [    1.122672] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 17 00:32:16 wayne-laptop kernel: [    1.122690] Freeing unused kernel memory: 540k freed
Dec 17 00:32:16 wayne-laptop kernel: [    1.123059] Write protecting the kernel text: 4568k
Dec 17 00:32:16 wayne-laptop kernel: [    1.123104] Write protecting the kernel read-only data: 1836k
Dec 17 00:32:16 wayne-laptop kernel: [    1.330510] Linux agpgart interface v0.103
Dec 17 00:32:16 wayne-laptop kernel: [    1.334870] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
Dec 17 00:32:16 wayne-laptop kernel: [    1.335666] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Dec 17 00:32:16 wayne-laptop kernel: [    1.409154] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Dec 17 00:32:16 wayne-laptop kernel: [    1.442453] ohci1394 0000:06:04.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 17 00:32:16 wayne-laptop kernel: [    1.447430] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Dec 17 00:32:16 wayne-laptop kernel: [    1.474424] [drm] Initialized drm 1.1.0 20060810
Dec 17 00:32:16 wayne-laptop kernel: [    1.492448] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 17 00:32:16 wayne-laptop kernel: [    1.492459] i915 0000:00:02.0: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [    1.496493] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b0106800-b0106fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec 17 00:32:16 wayne-laptop kernel: [    1.497407] 8139cp 0000:06:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
Dec 17 00:32:16 wayne-laptop kernel: [    1.501351] 8139too Fast Ethernet driver 0.9.28
Dec 17 00:32:16 wayne-laptop kernel: [    1.501405]   alloc irq_desc for 21 on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    1.501408]   alloc kstat_irqs on node -1
Dec 17 00:32:16 wayne-laptop kernel: [    1.501415] 8139too 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Dec 17 00:32:16 wayne-laptop kernel: [    1.502698] eth0: RealTek RTL8139 at 0x3000, 00:0f:b0:68:14:3e, IRQ 21
Dec 17 00:32:16 wayne-laptop kernel: [    1.901745] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:16 wayne-laptop kernel: [    2.132851] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:16 wayne-laptop kernel: [    2.261919] [drm] fb0: inteldrmfb frame buffer device
Dec 17 00:32:16 wayne-laptop kernel: [    2.261937] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: Network interface enumeration completed.
Dec 17 00:32:16 wayne-laptop kernel: [    2.325512] render error detected, EIR: 0x00000010
Dec 17 00:32:16 wayne-laptop kernel: [    2.325515] page table error
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: Registering new address record for fe80::212:f0ff:fe11:2603 on eth1.*.
Dec 17 00:32:16 wayne-laptop kernel: [    2.325517]   PGTBL_ER: 0x00000100
Dec 17 00:32:16 wayne-laptop kernel: [    2.325521] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
Dec 17 00:32:16 wayne-laptop kernel: [    2.325529] render error detected, EIR: 0x00000010
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: Server startup complete. Host name is wayne-laptop.local. Local service cookie is 136018315.
Dec 17 00:32:16 wayne-laptop kernel: [    2.325531] page table error
Dec 17 00:32:16 wayne-laptop avahi-daemon[789]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 17 00:32:16 wayne-laptop kernel: [    2.325533]   PGTBL_ER: 0x00000100
Dec 17 00:32:16 wayne-laptop kernel: [    2.334232] [drm] LVDS-8: set mode 1280x800 17
Dec 17 00:32:16 wayne-laptop kernel: [    2.360200] Console: switching to colour frame buffer device 160x50
Dec 17 00:32:16 wayne-laptop kernel: [    3.054325] irq 18: nobody cared (try booting with the "irqpoll" option)
Dec 17 00:32:16 wayne-laptop kernel: [    3.054332] Pid: 335, comm: fstype Not tainted 2.6.31-16-generic #53-Ubuntu
Dec 17 00:32:16 wayne-laptop kernel: [    3.054336] Call Trace:
Dec 17 00:32:16 wayne-laptop kernel: [    3.054347]  [<c056ea7c>] ? printk+0x18/0x1c
Dec 17 00:32:16 wayne-laptop kernel: [    3.054355]  [<c0190ee7>] __report_bad_irq+0x27/0x90
Dec 17 00:32:16 wayne-laptop kernel: [    3.054360]  [<c018f8fc>] ? handle_IRQ_event+0x4c/0x140
Dec 17 00:32:16 wayne-laptop kernel: [    3.054365]  [<c01910a0>] note_interrupt+0x150/0x190
Dec 17 00:32:16 wayne-laptop kernel: [    3.054370]  [<c01e77ff>] ? rw_verify_area+0x5f/0xe0
Dec 17 00:32:16 wayne-laptop kernel: [    3.054374]  [<c01915fc>] handle_fasteoi_irq+0xac/0xd0
Dec 17 00:32:16 wayne-laptop kernel: [    3.054380]  [<c0105a38>] handle_irq+0x18/0x30
Dec 17 00:32:16 wayne-laptop kernel: [    3.054384]  [<c0104f07>] do_IRQ+0x47/0xc0
Dec 17 00:32:16 wayne-laptop kernel: [    3.054388]  [<c01e836d>] ? sys_read+0x3d/0x70
Dec 17 00:32:16 wayne-laptop kernel: [    3.054392]  [<c01039b0>] common_interrupt+0x30/0x40
Dec 17 00:32:16 wayne-laptop kernel: [    3.054395] handlers:
Dec 17 00:32:16 wayne-laptop kernel: [    3.054396] [<c040f6f0>] (usb_hcd_irq+0x0/0x70)
Dec 17 00:32:16 wayne-laptop kernel: [    3.054403] Disabling IRQ #18
Dec 17 00:32:16 wayne-laptop kernel: [    3.214121] PM: Starting manual resume from disk
Dec 17 00:32:16 wayne-laptop kernel: [    3.214125] PM: Resume from partition 8:7
Dec 17 00:32:16 wayne-laptop kernel: [    3.214128] PM: Checking hibernation image.
Dec 17 00:32:16 wayne-laptop kernel: [    3.214318] PM: Resume from disk failed.
Dec 17 00:32:16 wayne-laptop kernel: [    3.235864] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
Dec 17 00:32:16 wayne-laptop kernel: [    3.235869] EXT4-fs (sda6): write access will be enabled during recovery
Dec 17 00:32:16 wayne-laptop kernel: [    3.248090] EXT4-fs (sda6): barriers enabled
Dec 17 00:32:16 wayne-laptop kernel: [    9.632026] Clocksource tsc unstable (delta = -78995156 ns)
Dec 17 00:32:16 wayne-laptop kernel: [    9.872092] kjournald2 starting: pid 355, dev sda6:8, commit interval 5 seconds
Dec 17 00:32:16 wayne-laptop kernel: [    9.872115] EXT4-fs (sda6): delayed allocation enabled
Dec 17 00:32:16 wayne-laptop kernel: [    9.872120] EXT4-fs: file extents enabled
Dec 17 00:32:16 wayne-laptop kernel: [    9.872774] EXT4-fs: mballoc enabled
Dec 17 00:32:16 wayne-laptop kernel: [    9.872793] EXT4-fs (sda6): orphan cleanup on readonly fs
Dec 17 00:32:16 wayne-laptop kernel: [    9.872802] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 65861
Dec 17 00:32:16 wayne-laptop kernel: [    9.872881] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 65860
Dec 17 00:32:16 wayne-laptop kernel: [    9.872898] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 65859
Dec 17 00:32:16 wayne-laptop kernel: [    9.872915] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 65858
Dec 17 00:32:16 wayne-laptop kernel: [    9.872931] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 5018
Dec 17 00:32:16 wayne-laptop kernel: [    9.872940] EXT4-fs (sda6): 5 orphan inodes deleted
Dec 17 00:32:16 wayne-laptop kernel: [    9.872944] EXT4-fs (sda6): recovery complete
Dec 17 00:32:16 wayne-laptop kernel: [   10.016494] EXT4-fs (sda6): mounted filesystem with ordered data mode
Dec 17 00:32:16 wayne-laptop kernel: [   10.668051] type=1505 audit(1261009915.278:2): operation="profile_load" pid=378 name=/usr/share/gdm/guest-session/Xsession
Dec 17 00:32:16 wayne-laptop kernel: [   10.670703] type=1505 audit(1261009915.278:3): operation="profile_load" pid=379 name=/sbin/dhclient3
Dec 17 00:32:16 wayne-laptop kernel: [   10.671493] type=1505 audit(1261009915.278:4): operation="profile_load" pid=379 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 17 00:32:16 wayne-laptop kernel: [   10.671922] type=1505 audit(1261009915.278:5): operation="profile_load" pid=379 name=/usr/lib/connman/scripts/dhclient-script
Dec 17 00:32:16 wayne-laptop kernel: [   10.734106] type=1505 audit(1261009915.343:6): operation="profile_load" pid=380 name=/usr/bin/evince
Dec 17 00:32:16 wayne-laptop kernel: [   10.747011] type=1505 audit(1261009915.354:7): operation="profile_load" pid=380 name=/usr/bin/evince-previewer
Dec 17 00:32:16 wayne-laptop kernel: [   10.754635] type=1505 audit(1261009915.362:8): operation="profile_load" pid=380 name=/usr/bin/evince-thumbnailer
Dec 17 00:32:16 wayne-laptop kernel: [   10.789962] type=1505 audit(1261009915.398:9): operation="profile_load" pid=382 name=/usr/lib/cups/backend/cups-pdf
Dec 17 00:32:16 wayne-laptop kernel: [   10.790896] type=1505 audit(1261009915.398:10): operation="profile_load" pid=382 name=/usr/sbin/cupsd
Dec 17 00:32:16 wayne-laptop kernel: [   10.807843] type=1505 audit(1261009915.414:11): operation="profile_load" pid=383 name=/usr/sbin/tcpdump
Dec 17 00:32:16 wayne-laptop kernel: [   29.211620] udev: starting version 147
Dec 17 00:32:16 wayne-laptop kernel: [   29.245606] Adding 489940k swap on /dev/sda7.  Priority:-1 extents:1 across:489940k 
Dec 17 00:32:16 wayne-laptop kernel: [   29.281854] lp: driver loaded but no devices found
Dec 17 00:32:16 wayne-laptop kernel: [   29.411862] sdhci: Secure Digital Host Controller Interface driver
Dec 17 00:32:16 wayne-laptop kernel: [   29.411867] sdhci: Copyright(c) Pierre Ossman
Dec 17 00:32:16 wayne-laptop kernel: [   29.418779] intel_rng: FWH not detected
Dec 17 00:32:16 wayne-laptop kernel: [   29.468213] sdhci-pci 0000:06:04.4: SDHCI controller found [104c:8034] (rev 0)
Dec 17 00:32:16 wayne-laptop kernel: [   29.468238] sdhci-pci 0000:06:04.4: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec 17 00:32:16 wayne-laptop kernel: [   29.468319] Registered led device: mmc0::
Dec 17 00:32:16 wayne-laptop kernel: [   29.468364] mmc0: SDHCI controller on PCI [0000:06:04.4] using PIO
Dec 17 00:32:16 wayne-laptop kernel: [   29.468404] Registered led device: mmc1::
Dec 17 00:32:16 wayne-laptop kernel: [   29.468439] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
Dec 17 00:32:16 wayne-laptop kernel: [   29.468477] Registered led device: mmc2::
Dec 17 00:32:16 wayne-laptop kernel: [   29.468504] mmc2: SDHCI controller on PCI [0000:06:04.4] using PIO
Dec 17 00:32:16 wayne-laptop kernel: [   29.563772] yenta_cardbus 0000:06:04.0: CardBus bridge found [1179:ff00]
Dec 17 00:32:16 wayne-laptop kernel: [   29.563796] yenta_cardbus 0000:06:04.0: Enabling burst memory read transactions
Dec 17 00:32:16 wayne-laptop kernel: [   29.563802] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
Dec 17 00:32:16 wayne-laptop kernel: [   29.563805] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
Dec 17 00:32:16 wayne-laptop kernel: [   29.563813] yenta_cardbus 0000:06:04.0: TI: mfunc 0x10aa1b22, devctl 0x66
Dec 17 00:32:16 wayne-laptop kernel: [   29.565537] lib80211: common routines for IEEE802.11 drivers
Dec 17 00:32:16 wayne-laptop kernel: [   29.565540] lib80211_crypt: registered algorithm 'NULL'
Dec 17 00:32:16 wayne-laptop kernel: [   29.609022] ieee80211: 802.11 data/management/control stack, git-1.1.13
Dec 17 00:32:16 wayne-laptop kernel: [   29.609027] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Dec 17 00:32:16 wayne-laptop kernel: [   29.633354] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Dec 17 00:32:16 wayne-laptop kernel: [   29.633358] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 17 00:32:16 wayne-laptop kernel: [   29.747815] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 17 00:32:16 wayne-laptop kernel: [   29.801893] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x04f8, PCI irq 16
Dec 17 00:32:16 wayne-laptop kernel: [   29.801900] yenta_cardbus 0000:06:04.0: Socket status: 30000006
Dec 17 00:32:16 wayne-laptop kernel: [   29.801905] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
Dec 17 00:32:16 wayne-laptop kernel: [   29.801917] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
Dec 17 00:32:16 wayne-laptop kernel: [   29.801922] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
Dec 17 00:32:16 wayne-laptop kernel: [   29.802183] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
Dec 17 00:32:16 wayne-laptop kernel: [   29.802187] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
Dec 17 00:32:16 wayne-laptop kernel: [   29.804580]   alloc irq_desc for 22 on node -1
Dec 17 00:32:16 wayne-laptop kernel: [   29.804584]   alloc kstat_irqs on node -1
Dec 17 00:32:16 wayne-laptop kernel: [   29.804595] ipw2200 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 17 00:32:16 wayne-laptop kernel: [   29.817060] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 17 00:32:16 wayne-laptop kernel: [   29.817138] ipw2200 0000:06:02.0: firmware: requesting ipw2200-bss.fw
Dec 17 00:32:16 wayne-laptop kernel: [   29.839579]   alloc irq_desc for 17 on node -1
Dec 17 00:32:16 wayne-laptop kernel: [   29.839584]   alloc kstat_irqs on node -1
Dec 17 00:32:16 wayne-laptop kernel: [   29.839594] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 17 00:32:16 wayne-laptop kernel: [   29.839646] Intel ICH 0000:00:1e.2: setting latency timer to 64
Dec 17 00:32:16 wayne-laptop kernel: [   30.036456] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 17 00:32:16 wayne-laptop kernel: [   30.037614] tifm_7xx1 0000:06:04.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 17 00:32:16 wayne-laptop kernel: [   30.111974] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Dec 17 00:32:16 wayne-laptop kernel: [   30.113542] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Dec 17 00:32:16 wayne-laptop kernel: [   30.114187] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Dec 17 00:32:16 wayne-laptop kernel: [   30.114716] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Dec 17 00:32:16 wayne-laptop kernel: [   30.115431] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Dec 17 00:32:16 wayne-laptop kernel: [   30.143772] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input5
Dec 17 00:32:16 wayne-laptop kernel: [   30.160470] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input6
Dec 17 00:32:16 wayne-laptop kernel: [   30.664052] intel8x0_measure_ac97_clock: measured 55347 usecs (2667 samples)
Dec 17 00:32:16 wayne-laptop kernel: [   30.664058] intel8x0: clocking to 48000
Dec 17 00:32:16 wayne-laptop kernel: [   31.369534] EXT4-fs (sda6): internal journal on sda6:8
Dec 17 00:32:16 wayne-laptop kernel: [   31.589605] eth0: link down
Dec 17 00:32:16 wayne-laptop kernel: [   31.589701] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 17 00:32:16 wayne-laptop kernel: [   31.681471] type=1505 audit(1261009936.290:12): operation="profile_replace" pid=898 name=/usr/share/gdm/guest-session/Xsession
Dec 17 00:32:16 wayne-laptop kernel: [   31.683193] type=1505 audit(1261009936.290:13): operation="profile_replace" pid=899 name=/sbin/dhclient3
Dec 17 00:32:16 wayne-laptop kernel: [   31.683985] type=1505 audit(1261009936.290:14): operation="profile_replace" pid=899 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 17 00:32:16 wayne-laptop kernel: [   31.684440] type=1505 audit(1261009936.294:15): operation="profile_replace" pid=899 name=/usr/lib/connman/scripts/dhclient-script
Dec 17 00:32:16 wayne-laptop kernel: [   31.689099] type=1505 audit(1261009936.298:16): operation="profile_replace" pid=900 name=/usr/bin/evince
Dec 17 00:32:16 wayne-laptop kernel: [   31.741152] type=1505 audit(1261009936.350:17): operation="profile_replace" pid=900 name=/usr/bin/evince-previewer
Dec 17 00:32:16 wayne-laptop kernel: [   31.770396] type=1505 audit(1261009936.378:18): operation="profile_replace" pid=900 name=/usr/bin/evince-thumbnailer
Dec 17 00:32:16 wayne-laptop init: ureadahead-other main process (914) terminated with status 4
Dec 17 00:32:16 wayne-laptop kernel: [   31.817012] type=1505 audit(1261009936.426:19): operation="profile_replace" pid=929 name=/usr/lib/cups/backend/cups-pdf
Dec 17 00:32:16 wayne-laptop kernel: [   31.817950] type=1505 audit(1261009936.426:20): operation="profile_replace" pid=929 name=/usr/sbin/cupsd
Dec 17 00:32:16 wayne-laptop kernel: [   31.820449] type=1505 audit(1261009936.430:21): operation="profile_replace" pid=930 name=/usr/sbin/tcpdump
Dec 17 00:32:16 wayne-laptop wpa_supplicant[879]: CTRL-EVENT-SCAN-RESULTS 
Dec 17 00:32:16 wayne-laptop ntfs-3g[946]: Version 2009.4.4 external FUSE 27
Dec 17 00:32:16 wayne-laptop ntfs-3g[946]: Mounted /dev/sda1 (Read-Write, label "", NTFS 3.1)
Dec 17 00:32:16 wayne-laptop ntfs-3g[946]: Cmdline options: rw,nls=utf8,umask=007,gid=46
Dec 17 00:32:16 wayne-laptop ntfs-3g[946]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sda1,blkdev,blksize=4096
Dec 17 00:32:16 wayne-laptop gdm-binary[793]: WARNING: Unable to find users: no seat-id found
Dec 17 00:32:16 wayne-laptop init: apport pre-start process (993) terminated with status 1
Dec 17 00:32:16 wayne-laptop cron[996]: (CRON) INFO (pidfile fd = 3)
Dec 17 00:32:16 wayne-laptop init: apport post-stop process (1005) terminated with status 1
Dec 17 00:32:16 wayne-laptop anacron[1016]: Anacron 2.3 started on 2009-12-17
Dec 17 00:32:16 wayne-laptop cron[1027]: (CRON) STARTUP (fork ok)
Dec 17 00:32:16 wayne-laptop cron[1027]: (CRON) INFO (Running @reboot jobs)
Dec 17 00:32:16 wayne-laptop anacron[1016]: Will run job `cron.daily' in 5 min.
Dec 17 00:32:16 wayne-laptop anacron[1016]: Jobs will be executed sequentially
Dec 17 00:32:16 wayne-laptop acpid: client connected from 968[0:0]
Dec 17 00:32:16 wayne-laptop acpid: client connected from 1069[107:114]
Dec 17 00:32:17 wayne-laptop kernel: [   32.439360] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:17 wayne-laptop kernel: [   32.450850] ppdev: user-space parallel port driver
Dec 17 00:32:17 wayne-laptop kernel: [   32.568340] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:17 wayne-laptop kernel: [   32.771509] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:17 wayne-laptop kernel: [   32.913674] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2
Dec 17 00:32:17 wayne-laptop udev-configure-printer: Failed to get parent
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
Dec 17 00:32:17 wayne-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2
Dec 17 00:32:17 wayne-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.3/usb5
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1
Dec 17 00:32:17 wayne-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
Dec 17 00:32:17 wayne-laptop kernel: [   33.114935] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:17 wayne-laptop kernel: [   33.243131] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:18 wayne-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 17 00:32:18 wayne-laptop udev-configure-printer: Failed to get parent
Dec 17 00:32:18 wayne-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb3
Dec 17 00:32:18 wayne-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 17 00:32:18 wayne-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 17 00:32:18 wayne-laptop udev-configure-printer: Failed to get parent
Dec 17 00:32:18 wayne-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb4
Dec 17 00:32:18 wayne-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 17 00:32:18 wayne-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 17 00:32:18 wayne-laptop udev-configure-printer: Failed to get parent
Dec 17 00:32:18 wayne-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.3/usb5
Dec 17 00:32:18 wayne-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Dec 17 00:32:18 wayne-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 17 00:32:18 wayne-laptop udev-configure-printer: Failed to get parent
Dec 17 00:32:18 wayne-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1
Dec 17 00:32:18 wayne-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Dec 17 00:32:18 wayne-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec 17 00:32:18 wayne-laptop kernel: [   33.536578] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:18 wayne-laptop kernel: [   33.683548] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:18 wayne-laptop console-kit-daemon[808]: WARNING: Couldn't read /proc/798/environ: Failed to open file '/proc/798/environ': No such file or directory
Dec 17 00:32:20 wayne-laptop kernel: [   35.532855] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:20 wayne-laptop kernel: [   35.644160] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:20 wayne-laptop kernel: [   35.860715] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:20 wayne-laptop kernel: [   36.001678] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:20 wayne-laptop kernel: [   36.237238] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:21 wayne-laptop kernel: [   36.360394] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:21 wayne-laptop kernel: [   36.568826] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:21 wayne-laptop kernel: [   36.709532] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:21 wayne-laptop kernel: [   36.872596] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:21 wayne-laptop kernel: [   37.011522] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:21 wayne-laptop kernel: [   37.216396] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:21 wayne-laptop kernel: [   37.357311] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:23 wayne-laptop kernel: [   38.775986] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:23 wayne-laptop kernel: [   38.897913] [drm] DAC-6: set mode 640x480 0
Dec 17 00:32:23 wayne-laptop kernel: [   39.100992] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:23 wayne-laptop kernel: [   39.241873] [drm] TV-14: set mode NTSC 480i 0
Dec 17 00:32:24 wayne-laptop pulseaudio[1330]: ratelimit.c: 6 events suppressed
Dec 17 00:32:26 wayne-laptop kernel: [   42.100018] eth1: no IPv6 routers present

```

---

