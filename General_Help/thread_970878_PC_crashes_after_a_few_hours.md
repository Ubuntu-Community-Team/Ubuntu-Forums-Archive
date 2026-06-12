---
title: "PC crashes after a few hours"
date: 2008-11-04
forum: General Help
---

### Post by poldie on 2008-11-04
My 32bit 8.10 installation seems to be working fine, but if I leave it logged on and running in the morning when I go to work, when I come back it's hung.  The screen is black, although the monitor hasn't lost sync. It's an lcd monitor, so when it's turned on, even with a black display it's slightly blueish.  If another user is logged on and using the pc they'll be fine, but when I switch users back to me, it takes me to the black screen and from there I can do nothing.  Control alt backspace does nothing.  Control alt delete makes a beep but nothing happens.  All I can do is press the reset button on my pc and reboot.

Where do I start diagnosing this?  The system log? I'm not sure what to look for.

---

### Post by cmnorton on 2008-11-05
What is running, when you walk away? I had an old Acer laptop that would hang, if I left a browser (firefox) running.

You can also look in the logs (/var/log), and see if there is anything interesting there.

Edit:
-----------------

Posting some information about your hardware is also a good idea. Especially, important would be graphics information (chip), and what you have configured, like compiz.

---

### Post by poldie on 2008-11-06
> **cmnorton said:**
> What is running, when you walk away? I had an old Acer laptop that would hang, if I left a browser (firefox) running.

You can also look in the logs (/var/log), and see if there is anything interesting there.

Edit:
-----------------

Posting some information about your hardware is also a good idea. Especially, important would be graphics information (chip), and what you have configured, like compiz.

It crashed again today, so it's fairly repeatable. That's from 8am to 6pm.  I had no software running.  Another session was being used (this isn't always the case) but that would have been just firefox, perhaps running YouTube videos for a while). I switched back (from that low permissions user) to my (admin) account and again - nothing. I did control alt delete because that brings up a message saying i'll be logged out in 60 seconds, but around 60 seconds later (I didn't time it - just got in from work and was faffing about) the pc rebooted.

I have compiz enabled on the session which hangs.  I googled and perhaps you want this info:

$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

(It's an on-motherboard graphics card)




Here's /var/log/syslog (up until the time I did ctrl-alt-delete) - hope it's not too much info!

Nov  6 08:27:05 UbuntuDesktop syslogd 1.5.0#2ubuntu6: restart.
Nov  6 08:27:05 UbuntuDesktop anacron[9379]: Job `cron.daily' terminated
Nov  6 08:27:05 UbuntuDesktop anacron[9379]: Normal exit (1 job run)
Nov  6 08:54:02 UbuntuDesktop -- MARK --
Nov  6 09:14:02 UbuntuDesktop -- MARK --
Nov  6 09:17:01 UbuntuDesktop /USR/SBIN/CRON[9802]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 09:34:02 UbuntuDesktop -- MARK --
Nov  6 09:54:02 UbuntuDesktop -- MARK --
Nov  6 10:14:02 UbuntuDesktop -- MARK --
Nov  6 10:17:01 UbuntuDesktop /USR/SBIN/CRON[9836]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 10:34:02 UbuntuDesktop -- MARK --
Nov  6 10:54:02 UbuntuDesktop -- MARK --
Nov  6 11:14:02 UbuntuDesktop -- MARK --
Nov  6 11:17:01 UbuntuDesktop /USR/SBIN/CRON[9870]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 11:34:02 UbuntuDesktop -- MARK --
Nov  6 11:54:02 UbuntuDesktop -- MARK --
Nov  6 12:14:02 UbuntuDesktop -- MARK --
Nov  6 12:17:01 UbuntuDesktop /USR/SBIN/CRON[9904]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 12:34:02 UbuntuDesktop -- MARK --
Nov  6 12:54:02 UbuntuDesktop -- MARK --
Nov  6 13:14:02 UbuntuDesktop -- MARK --
Nov  6 13:17:01 UbuntuDesktop /USR/SBIN/CRON[9938]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 13:34:02 UbuntuDesktop -- MARK --
Nov  6 13:54:02 UbuntuDesktop -- MARK --
Nov  6 14:14:02 UbuntuDesktop -- MARK --
Nov  6 14:17:01 UbuntuDesktop /USR/SBIN/CRON[9972]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 14:34:02 UbuntuDesktop -- MARK --
Nov  6 14:54:02 UbuntuDesktop -- MARK --
Nov  6 15:14:02 UbuntuDesktop -- MARK --
Nov  6 15:17:01 UbuntuDesktop /USR/SBIN/CRON[10006]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 15:34:02 UbuntuDesktop -- MARK --
Nov  6 15:54:02 UbuntuDesktop -- MARK --
Nov  6 15:57:42 UbuntuDesktop acpid: client connected from 10038[0:0] 
Nov  6 15:57:43 UbuntuDesktop kernel: [68634.347302] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
Nov  6 15:57:44 UbuntuDesktop gdmgreeter[10061]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Nov  6 15:57:53 UbuntuDesktop pulseaudio[10170]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  6 15:57:53 UbuntuDesktop pulseaudio[10172]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  6 15:57:53 UbuntuDesktop pulseaudio[10172]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  6 15:57:54 UbuntuDesktop x-session-manager[10080]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Nov  6 15:57:55 UbuntuDesktop pulseaudio[10172]: module-x11-xsmp.c: X11 session manager not running.
Nov  6 15:57:55 UbuntuDesktop pulseaudio[10172]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov  6 15:58:59 UbuntuDesktop kernel: [68710.012377] ppdev0: registered pardevice
Nov  6 15:58:59 UbuntuDesktop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  6 15:58:59 UbuntuDesktop kernel: [68710.060163] ppdev0: unregistered pardevice
Nov  6 15:58:59 UbuntuDesktop kernel: [68710.079780] ppdev0: registered pardevice
Nov  6 15:58:59 UbuntuDesktop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  6 15:58:59 UbuntuDesktop kernel: [68710.124202] ppdev0: unregistered pardevice
Nov  6 15:58:59 UbuntuDesktop kernel: [68710.134278] ppdev0: registered pardevice
Nov  6 15:58:59 UbuntuDesktop kernel: [68710.180015] ppdev0: unregistered pardevice
Nov  6 15:58:59 UbuntuDesktop kernel: [68710.657008] type=1503 audit(1225987139.764:16): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/10398/net/" pid=10398 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522118] type=1503 audit(1225987140.628:17): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/10402/net/" pid=10402 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522152] type=1503 audit(1225987140.628:18): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=10402 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522160] type=1503 audit(1225987140.628:19): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=10402 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522167] type=1503 audit(1225987140.628:20): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=10402 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522174] type=1503 audit(1225987140.628:21): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=10402 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522193] type=1503 audit(1225987140.628:22): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=10402 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522200] type=1503 audit(1225987140.628:23): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=10402 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522208] type=1503 audit(1225987140.628:24): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=10402 profile="/usr/sbin/cupsd"
Nov  6 15:59:00 UbuntuDesktop kernel: [68711.522215] type=1503 audit(1225987140.628:25): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=10402 profile="/usr/sbin/cupsd"
Nov  6 16:14:02 UbuntuDesktop -- MARK --
Nov  6 16:17:01 UbuntuDesktop /USR/SBIN/CRON[10466]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 16:34:02 UbuntuDesktop -- MARK --
Nov  6 16:54:02 UbuntuDesktop -- MARK --
Nov  6 17:14:02 UbuntuDesktop -- MARK --
Nov  6 17:17:01 UbuntuDesktop /USR/SBIN/CRON[10635]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 17:34:02 UbuntuDesktop -- MARK --
Nov  6 17:35:56 UbuntuDesktop dhclient: DHCPREQUEST of 192.168.1.64 on eth0 to 192.168.1.254 port 67
Nov  6 17:35:56 UbuntuDesktop dhclient: DHCPACK of 192.168.1.64 from 192.168.1.254
Nov  6 17:35:56 UbuntuDesktop dhclient: bound to 192.168.1.64 -- renewal in 36558 seconds.
Nov  6 17:53:52 UbuntuDesktop acpid: client connected from 5247[0:0] 
Nov  6 17:54:00 UbuntuDesktop init: tty4 main process (4673) killed by TERM signal
Nov  6 17:54:00 UbuntuDesktop init: tty5 main process (4674) killed by TERM signal
Nov  6 17:54:00 UbuntuDesktop init: tty2 main process (4681) killed by TERM signal
Nov  6 17:54:00 UbuntuDesktop init: tty3 main process (4682) killed by TERM signal
Nov  6 17:54:00 UbuntuDesktop init: tty6 main process (4683) killed by TERM signal
Nov  6 17:54:00 UbuntuDesktop init: tty1 main process (5611) killed by TERM signal


So did something happen around 15:57?  Perhaps it's when my wife started another session - how would I check?  Could it be related?

Thanks for the help so far!

---

### Post by cmnorton on 2008-11-26
I would post this either as a question or bug up in launchpad. Other than looking in /var/log/syslog and /var/log/messages and the output of dmesg after you reboot, I don't offhand have any other ideas.

You might have a graphics driver conflict.

Does this happen if you don't use compiz? I don't so do not know how difficult it is to disable it.

---

