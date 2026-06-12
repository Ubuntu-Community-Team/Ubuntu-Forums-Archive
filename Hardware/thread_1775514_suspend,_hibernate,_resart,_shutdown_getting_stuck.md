---
title: "suspend, hibernate, resart, shutdown getting stuck"
date: 2011-06-04
forum: Hardware
---

### Post by ameseisch on 2011-06-04
My hardware is an ideapad s205. Ubuntu 11.04 up and going, but trying to work through some issues. wifi, card reader, mic, etc. 

Probably the biggest pain at the moment is that shutdown, restart, hibernate, and suspend don't work. It gets stuck. The fan just runs full blast, and the only way to get out of it is to hard shut down by holding the power button.

On shutdown sometimes text is displayed on screen and it says something like 'trying to interrupt ...' 

I am not sure where to start in trying to solve this issue.

---

### Post by ameseisch on 2011-06-04
looking around I stumbled upon some log files in /var/log/

pm-suspend.log has this bit in it... does that give anyone any hints?

```

Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

```

---

### Post by matt_symes on 2011-06-04
Hi

Open a terminal and type

```
sudo lshw -C network
```Enter your password. It will not be echoed to the screen. This is normal.

Post back the results here. It will tell us what drivers your network cards are using.

It might be a case of unloading them before suspending.

Kind regards

---

### Post by ameseisch on 2011-06-04
```

PCI (sysfs)  


  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:59:7a:bc
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:1000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:65:d0:c7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0100000-f010ffff

```

---

### Post by matt_symes on 2011-06-04
Hi

Try this. Open a terminal and type

```
sudo modprobe -r ath9k
```

Enter your password. It will not be echoed to the screen. This is normal.

You will lose internet connectivity as you have unloaded the driver.

Try to suspend the PC.

Wake up from suspend and type

```
sudo modprobe ath9k
```

to reload the driver and get internet connectivity. Did that suspend and resume successfully ?

Kind regards

---

### Post by ameseisch on 2011-06-04
No luck. the "sudo modprobe -r ath9k" seemed to work. connection was lost and 

```
rfkill list all
``` 

returned nothing, but suspend still got stuck.

---

### Post by matt_symes on 2011-06-04
Hi

Can you post the /var/log/pm-suspend.log file again after that last attempt and can you also post the tail of /var/log/syslog ( the part containing information about that last suspend attempt).

That may give more clues as to what is happening.

Kind regards

---

### Post by ameseisch on 2011-06-04
here is the pm-suspend.log:
```

Initial commandline parameters: 
Sat Jun  4 21:19:28 CDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux ideapad 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  0 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
arc4                   12529  0 
binfmt_misc            17565  1 
snd_hda_codec_conexant    57511  1 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
fglrx                2739144  131 
psmouse                73535  0 
snd_seq_midi           13324  0 
serio_raw              13166  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
ideapad_laptop         13494  0 
vfat                   21708  1 
videodev               82052  1 uvcvideo
fat                    61374  1 vfat
snd                    67382  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17078  1 videodev
sparse_keymap          13898  1 ideapad_laptop
video                  19438  0 
k10temp                13119  0 
sp5100_tco             13744  0 
i2c_piix4              13303  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  3 
libahci                26642  1 ahci
r8169                  48022  0 
             total       used       free     shared    buffers     cached
Mem:       3646764     947888    2698876          0      42304     340420
-/+ buffers/cache:     565164    3081600
Swap:      3777160          0    3777160

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Jun  4 21:19:32 CDT 2011: performing suspend

```

looks like the same kinda thing.

here is syslog relevant parts:

```

Jun  4 21:19:16 ideapad kernel: [ 2037.626633] wlan0: deauthenticating from c0:3f:0e:9f:28:1c by local choice (reason=3)
Jun  4 21:19:16 ideapad kernel: [ 2037.689106] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun  4 21:19:16 ideapad kernel: [ 2037.689124] cfg80211: Restoring regulatory settings
Jun  4 21:19:16 ideapad kernel: [ 2037.689141] cfg80211: Calling CRDA to update world regulatory domain
Jun  4 21:19:16 ideapad kernel: [ 2037.702722] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jun  4 21:19:16 ideapad kernel: [ 2037.702743] cfg80211: World regulatory domain updated:
Jun  4 21:19:16 ideapad kernel: [ 2037.702749] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  4 21:19:16 ideapad kernel: [ 2037.702760] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 21:19:16 ideapad kernel: [ 2037.702769] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  4 21:19:16 ideapad kernel: [ 2037.702779] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  4 21:19:16 ideapad kernel: [ 2037.702787] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 21:19:16 ideapad kernel: [ 2037.702796] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  4 21:19:16 ideapad avahi-daemon[663]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun  4 21:19:16 ideapad avahi-daemon[663]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::6aa3:c4ff:fe65:d0c7.
Jun  4 21:19:16 ideapad avahi-daemon[663]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun  4 21:19:16 ideapad avahi-daemon[663]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.8.
Jun  4 21:19:16 ideapad dhclient: receive_packet failed on wlan0: Network is down
Jun  4 21:19:16 ideapad NetworkManager[668]: <info> (wlan0): now unmanaged
Jun  4 21:19:16 ideapad NetworkManager[668]: <info> (wlan0): device state change: 8 -> 1 (reason 36)
Jun  4 21:19:16 ideapad NetworkManager[668]: <info> (wlan0): deactivating device (reason: 36).
Jun  4 21:19:16 ideapad avahi-daemon[663]: Withdrawing address record for fe80::6aa3:c4ff:fe65:d0c7 on wlan0.
Jun  4 21:19:16 ideapad avahi-daemon[663]: Withdrawing address record for 192.168.1.8 on wlan0.
Jun  4 21:19:16 ideapad avahi-daemon[663]: Withdrawing workstation service for wlan0.
Jun  4 21:19:16 ideapad kernel: [ 2037.881216] ath9k 0000:03:00.0: PCI INT A disabled
Jun  4 21:19:16 ideapad kernel: [ 2037.881313] ath9k: Driver unloaded
Jun  4 21:19:16 ideapad wpa_supplicant[850]: Failed to initialize the driver after interface was added.
Jun  4 21:19:16 ideapad wpa_supplicant[850]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  4 21:19:16 ideapad NetworkManager[668]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2082
Jun  4 21:19:16 ideapad NetworkManager[668]: <info> (wlan0): cleaning up...
Jun  4 21:19:16 ideapad NetworkManager[668]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  4 21:19:16 ideapad NetworkManager[668]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:15.2/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  4 21:19:16 ideapad NetworkManager[668]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:15.2/0000:03:00.0/ieee80211/phy0/rfkill2 disappeared
Jun  4 21:19:16 ideapad nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist#012
Jun  4 21:19:16 ideapad wpa_supplicant[850]: Could not read interface wlan0 flags: No such device
Jun  4 21:19:27 ideapad NetworkManager[668]: <info> sleep requested (sleeping: no  enabled: yes)
Jun  4 21:19:27 ideapad NetworkManager[668]: <info> sleeping or disabling...
Jun  4 21:19:27 ideapad NetworkManager[668]: <info> (eth0): now unmanaged
Jun  4 21:19:27 ideapad NetworkManager[668]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Jun  4 21:19:27 ideapad NetworkManager[668]: <info> (eth0): cleaning up...
Jun  4 21:19:27 ideapad NetworkManager[668]: <info> (eth0): taking down device.
Jun  4 21:19:28 ideapad anacron[2514]: Anacron 2.3 started on 2011-06-04
Jun  4 21:19:28 ideapad anacron[2514]: Normal exit (0 jobs run)
Jun  4 21:19:29 ideapad kernel: [ 2050.310242] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
Jun  4 21:20:45 ideapad kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun  4 21:20:45 ideapad rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="616" x-info="http://www.rsyslog.com"] (re)start
Jun  4 21:20:45 ideapad rsyslogd: rsyslogd's groupid changed to 103
Jun  4 21:20:45 ideapad rsyslogd: rsyslogd's userid changed to 101
Jun  4 21:20:45 ideapad rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]


```

---

### Post by matt_symes on 2011-06-06
Hi

I think your suspend, shutdown, hibernate and restart issue may be due to a wifi problem.

Try this.

```
sudo service network-manager stop
```

Try to suspend and resume. Do you still get the problem ?

Kind regards

---

### Post by ameseisch on 2011-06-06
No luck. Suspend still got stuck.

I wonder if there is any chance it could be related to other issues I am having. The internal mic doesn't seem to be working, the wireless hardware switch needs to be dealt with after each startup with a series of commands that I made into a little script on my desktop, and the USB ports don't seem to be able to mount things like cameras nor does the card reader read cards. USB mouse does work though, seems like a mounting issues maybe...  

Here is what I use to get the wireless active in case it has any relevance:
```

sudo rfkill unblock wifi
sudo rfkill unblock all
sudo modprobe -r acer_wmi

```

---

### Post by matt_symes on 2011-06-07
Hi

> **ameseisch said:**
> No luck. Suspend still got stuck.

I wonder if there is any chance it could be related to other issues I am having. The internal mic doesn't seem to be working, the wireless hardware switch needs to be dealt with after each startup with a series of commands that I made into a little script on my desktop, and the USB ports don't seem to be able to mount things like cameras nor does the card reader read cards. USB mouse does work though, seems like a mounting issues maybe...  

Here is what I use to get the wireless active in case it has any relevance:
```

sudo rfkill unblock wifi
sudo rfkill unblock all
sudo modprobe -r acer_wmi

```

You have some problems there then :(

The first thing i would suggest is blacklisting the acer_wmi module using the blacklist.conf file and not your own script. That way it will not be loaded at startup and you will not have to unload it each time with your script.

```
sudo nano /etc/modprobe.d/blacklist.conf
```add

```
blacklist acer_wmi
```to the bottom of the file. Crtl + o to save and ctrl + x to exit.

Upon reboot the module should not be loaded.

Is there any reason you used that script and not blacklisting ? Did you try this method originally ?

If you still need the 2 rfkill commands, put them in /etc/rc.local before the exit 0 command. That should automate that for you.

I think an idea might be to see the /var/log/syslog file when you suspend without unloading modules (ath9k) or stopping network manager. 

It would be good to see them with no interference as it were.

Kind regards

---

### Post by ameseisch on 2011-06-07
Yes, I tried the blacklist approach, but that approach has a problem. at startup the wifi hardware switch is still seen as turned to the off position, and the rfkill unblock won't work to unblock it at that point for some reason, meaning no wireless whatsoever. Thus resorted to little script that I run at each startup.

I will post some fresh syslog content this evening.

Thanks for your persistence in helping.

---

### Post by ameseisch on 2011-06-08
here is a recent chunk from syslog file

```

0fa3bb0c1
Jun  8 01:01:21 ideapad AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/41f6052316594b83b3e60120fa3bb0c1
Jun  8 01:01:22 ideapad AptDaemon.Worker: INFO: Updating cache
Jun  8 01:01:25 ideapad AptDaemon.Trans: INFO: Cancelling transaction /org/debian/apt/transaction/41f6052316594b83b3e60120fa3bb0c1
Jun  8 01:01:25 ideapad AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/41f6052316594b83b3e60120fa3bb0c1
Jun  8 01:06:44 ideapad AptDaemon: INFO: Quitting due to inactivity
Jun  8 01:06:44 ideapad AptDaemon: INFO: Shutdown was requested
Jun  8 01:09:41 ideapad kernel: [ 2503.120886] keyboard: can't emulate rawmode for keycode 240
Jun  8 01:09:41 ideapad kernel: [ 2503.120908] keyboard: can't emulate rawmode for keycode 240
Jun  8 01:09:42 ideapad kernel: [ 2504.420625] keyboard: can't emulate rawmode for keycode 240
Jun  8 01:09:42 ideapad kernel: [ 2504.420646] keyboard: can't emulate rawmode for keycode 240
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> sleep requested (sleeping: no  enabled: yes)
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> sleeping or disabling...
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (eth0): now unmanaged
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (eth0): device state change: 2 -> 1 (reason 37)
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (eth0): cleaning up...
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (eth0): taking down device.
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (wlan0): now unmanaged
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (wlan0): device state change: 8 -> 1 (reason 37)
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (wlan0): deactivating device (reason: 37).
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1625
Jun  8 01:10:49 ideapad kernel: [ 2571.704265] wlan0: deauthenticating from c0:3f:0e:9f:28:1c by local choice (reason=3)
Jun  8 01:10:49 ideapad wpa_supplicant[910]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun  8 01:10:49 ideapad kernel: [ 2571.811534] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun  8 01:10:49 ideapad kernel: [ 2571.811554] cfg80211: Restoring regulatory settings
Jun  8 01:10:49 ideapad kernel: [ 2571.811572] cfg80211: Calling CRDA to update world regulatory domain
Jun  8 01:10:49 ideapad avahi-daemon[812]: Withdrawing address record for 192.168.1.8 on wlan0.
Jun  8 01:10:49 ideapad avahi-daemon[812]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.8.
Jun  8 01:10:49 ideapad kernel: [ 2571.825622] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jun  8 01:10:49 ideapad kernel: [ 2571.825643] cfg80211: World regulatory domain updated:
Jun  8 01:10:49 ideapad kernel: [ 2571.825649] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  8 01:10:49 ideapad kernel: [ 2571.825660] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  8 01:10:49 ideapad kernel: [ 2571.825670] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  8 01:10:49 ideapad kernel: [ 2571.825679] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  8 01:10:49 ideapad kernel: [ 2571.825687] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  8 01:10:49 ideapad kernel: [ 2571.825696] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  8 01:10:49 ideapad avahi-daemon[812]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (wlan0): cleaning up...
Jun  8 01:10:49 ideapad NetworkManager[841]: <info> (wlan0): taking down device.
Jun  8 01:10:50 ideapad avahi-daemon[812]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun  8 01:10:50 ideapad avahi-daemon[812]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::6aa3:c4ff:fe65:d0c7.
Jun  8 01:10:50 ideapad avahi-daemon[812]: Withdrawing address record for fe80::6aa3:c4ff:fe65:d0c7 on wlan0.
Jun  8 01:10:50 ideapad anacron[2321]: Anacron 2.3 started on 2011-06-08
Jun  8 01:10:50 ideapad anacron[2321]: Will run job `cron.daily' in 5 min.
Jun  8 01:10:50 ideapad anacron[2321]: Will run job `cron.weekly' in 10 min.
Jun  8 01:10:50 ideapad anacron[2321]: Jobs will be executed sequentially
Jun  8 01:10:51 ideapad kernel: [ 2573.356284] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
Jun  8 01:10:53 ideapad init: anacron main process (2321) killed by TERM signal
Jun  8 01:12:06 ideapad kernel: imklog 4.6.4, log source = /proc/kmsg started.
Jun  8 01:12:06 ideapad rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="522" x-info="http://www.rsyslog.com"] (re)start
Jun  8 01:12:06 ideapad rsyslogd: rsyslogd's groupid changed to 103
Jun  8 01:12:06 ideapad rsyslogd: rsyslogd's userid changed to 101
Jun  8 01:12:06 ideapad rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jun  8 01:12:06 ideapad kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  8 01:12:06 ideapad kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  8 01:12:06 ideapad kernel: [    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
Jun  8 01:12:06 ideapad kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=b0d06dab-fc69-4576-858a-5dcbe94096db ro quiet splash vt.handoff=7

```

suspend requested at 01:10:49

---

### Post by matt_symes on 2011-06-08
Hi

Hmm. Maybe it's not Network manager after all. There is not much in the logs to help either.

Lets try to by pass some of the ACPI code.

Open a terminal and type...

```
sudo bash -c "echo shutdown > /sys/power/disk"
sudo bash -c "echo mem > /sys/power/state"
```

Does it suspend. You may need to hit the power key to waken it.

Kind regards

---

### Post by ameseisch on 2011-06-11
No luck. 

It still got stuck, though it seems to at least not be working so hard that time. The fans didn't kick into high gear.

---

### Post by matt_symes on 2011-06-12
Hi

Lets disable all ACPI functionality to eliminate it.

Boot the PC. When you get to the grub menu highlight the kernel you wish to change and hit e to edit the command line.

Add this to the end of the line that has quit splash on it.

```
acpi=off
```

It will end up looking something like (but not exactly the same as)

```
linux   /boot/vmlinuz-2.6.32-28-generic root=UUID=dffbd026-c151-45c6-9c94-c6625200f01b ro single acpi=off
```

Press ctrl and x to continue booting. When it has booted up try to suspend. 

This is a bit of a blunt hammer approach but it will hep us eliminate ACPI.

Kind regards

---

### Post by ameseisch on 2011-06-22
got sick kids last week, and quit messing around trying to get this thing to work. gonna try this last suggested thing with the grub and ACPI, but actually not sure how to get to the GRUB menu... it normally skips right past that.

---

### Post by lobstar on 2011-07-24
Hi

How did this go? It seems like the same problem i have. Suspend / hibernate not working, pm-suspend log says the same



```
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

```

Any Ideas?

---

### Post by currydude on 2011-07-24
> **lobstar said:**
> Hi

How did this go? It seems like the same problem i have. Suspend / hibernate not working, pm-suspend log says the same



```
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

```

Any Ideas?

+1 I get the same problem

---

### Post by SliceOf314 on 2011-11-15
+1 I get the same error messages and have same problem on 11.10 on lenovo x220.

---

### Post by northd_tech on 2011-11-15
So does everyone else with these Suspend troubles also have an NVIDIA graphics adapter (like me, with AMD 2-core 64bit Ubuntu Lucid Lynx 10.04.3 LTS and the new(est?) NVIDIA 285.05.09 graphics driver module(s)? )

These terminal commands might help some of us make sense out of the problem:

```
cat /var/log/pm-suspend.log | grep Nov
tail -n 100 /var/log/pm-suspend.log
locate acpi.ko
lsmod | grep acpi
dmesg | egrep 'wake|acpi|uspend|bernat|ower|esume|ailed'
 acpitool -e

egrep 'wake|acpi|uspend|bernat|ower|esume|ailed' /var/log/syslog

```This makes me think mine is probably working NOW (with that newer NVIDIA 285.05.09 driver module):

```
cat /var/log/pm-suspend.log  | grep wake

```> Fri Nov 11 06:09:14 MST 2011: Awake.
Sat Nov 12 07:33:10 MST 2011: Awake.
Sat Nov 12 09:47:44 MST 2011: Awake.
Sun Nov 13 06:01:10 MST 2011: Awake.
For NVIDIA graphics, these 2 might help isolate the problem(s):
```

modinfo nvidia
modinfo nvidia-current

```> **modinfo nvidia-current**
filename:       /lib/modules/2.6.32-35-generic/updates/dkms/nvidia-current.ko
alias:          char-major-195-*
supported:      external
license:        NVIDIA
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       2.6.32-35-generic SMP mod_unload modversions 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_NvAGP:int
Also, System > Administration > NVIDIA X Server Settings reports this for the first 'tab' "X Server Information" >  "NVIDIA Driver Version: 285.05.09"

That might tell some of you more about the nature of the Suspend problems in Ubuntu 10.xx (and apparently 11.xx too).

I'm really not sure why I don't see a [COLOR=DarkGreen]**"Tue Nov 15" "Awake"**[/COLOR] line at the bottom of the log for this morning though:
> 
$ **cat /var/log/pm-suspend.log | grep Nov**
[....]
Fri Nov 11 06:09:14 MST 2011: Running hooks for resume
Fri Nov 11 06:09:17 MST 2011: Finished.
Sat Nov 12 06:48:20 MST 2011: Running hooks for suspend.
Sat Nov 12 06:48:24 MST 2011: [COLOR=Red]performing suspend[/COLOR]
Sat Nov 12 07:33:10 MST 2011: [COLOR=DarkGreen]**Awake.**[/COLOR]
Sat Nov 12 07:33:10 MST 2011: Running hooks for resume
Sat Nov 12 07:33:11 MST 2011: Finished.
Sat Nov 12 09:47:25 MST 2011: Running hooks for suspend.
Sat Nov 12 09:47:29 MST 2011: [COLOR=Red]performing suspend[/COLOR]
Sat Nov 12 09:47:44 MST 2011: [COLOR=DarkGreen]**Awake.**[/COLOR]
Sat Nov 12 09:47:44 MST 2011: Running hooks for resume
Sat Nov 12 09:47:45 MST 2011: Finished.
Sun Nov 13 03:53:46 MST 2011: Running hooks for suspend.
Sun Nov 13 03:53:52 MST 2011: [COLOR=Red]performing suspend[/COLOR]
Sun Nov 13 06:01:10 MST 2011: [COLOR=DarkGreen]**Awake.**[/COLOR]
Sun Nov 13 06:01:10 MST 2011: Running hooks for resume
Sun Nov 13 06:01:13 MST 2011: Finished.
Tue Nov 15 05:19:32 MST 2011: Running hooks for suspend.
[COLOR=Red]**Tue Nov 15 05:19:40 MST 2011: performing suspend**[/COLOR]
I really don't remember what/how I did to/with my HP laptop first this morning though...
:confused:

Edit:  This command might also tell us something:

```
tail -n 100 /var/log/pm-powersave.log
```

---

### Post by teeedubb on 2012-01-07
> **ameseisch said:**
> My hardware is an ideapad s205. Ubuntu 11.04 up and going, but trying to work through some issues. wifi, card reader, mic, etc. 

Probably the biggest pain at the moment is that shutdown, restart, hibernate, and suspend don't work. It gets stuck. The fan just runs full blast, and the only way to get out of it is to hard shut down by holding the power button.

On shutdown sometimes text is displayed on screen and it says something like 'trying to interrupt ...' 

I am not sure where to start in trying to solve this issue.

I started having the exact same issues after adding powertop suggestions  to my /etc/rc.local file. Removing these fixed suspend resuming to a  blank screen...

---

### Post by bobik314 on 2012-03-09
This is hard problem even now. I have debian with kernel 3.2 and after last dist-upgrade suspend broke down.

---

### Post by lalawawa on 2012-03-11
I installed 11.04 yesterday.

For a long time I've been unable to get my Ubuntu Linux to sleep and wake up.

Just to see if they'd fixed the problem, I selected "suspend".  The screen went blank, and the power light on the computer stayed on.  When I waved the mouse around and clicked on it, the computer would not wake up.

I powered the computer down, turned it back on.  I get the pre-OS "Compaq" display, then the monitor goes blank again.  It won't wake up.  Even if I hit F11 (labeled "System Recovery") duing the Compaq prompt, it won't do it.  It just always goes back to a blank screen no matter what I do.  I'm typing this from another computer.  I think the only way I'm going to get access to my Linux box is to reinstall 11.04 from the DVD again and lose all the work I've done over this weekend.

---

### Post by lalawawa on 2012-03-11
I just booted with the Linux 11.04 DVD.  It booted off the DVD, I brought it up in "rescue" mode.  Don't know how to fix it.  I thought maybe just booting it would fix the permanent suspend problem, but when I tried rebooting without the DVD, it just went back to sleep again.

I guess I'm going to be up late tonight, reinstalling Linux.

---

### Post by lalawawa on 2012-03-11
One of the options the DVD gave me the option "upgrade from 11.04 to 11.04".  I thought a trivial upgrade might do nothing but clear the "suspended" state and solve my problem.  I tried it and it hung.

So I'm wiping the disk and reinstalling.

---

### Post by mgb on 2012-03-12
I found this thread doing some research on rsyslogd.  My 10.10 LTS system crashed yesterday and the last message in the  /var/log/syslog is:

Mar 11 07:40:06 mgb-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="937" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

There are other messages after google'ing this message that indicate that this is a problem, including messages from the forum for [www.rsyslog.com](www.rsyslog.com).

The current version for this software is 5.8.8.   Not sure why this happens or why a remote system is HUP'ing something on my system.  Don't particularly like that.  Is there a way to update this software?

Regards,

mgb

---

### Post by tanoloco on 2012-05-14
> **teeedubb said:**
> I started having the exact same issues after adding powertop suggestions  to my /etc/rc.local file. Removing these fixed suspend resuming to a  blank screen...

What must I do exactly to try this?

---

### Post by bobik314 on 2012-05-16
I managed to get suspend/resume working. More info [http://forums.debian.net/viewtopic.php?f=6&t=77011](http://forums.debian.net/viewtopic.php?f=6&t=77011)

---

### Post by moteprime on 2012-05-24
@ameseisch

I also have an Ideapad and struggled alot, (with other) to get WiFi working. We have a long thread about getting the rt3090 in Ideapad s205 to work with 11.10 here. [http://ubuntuforums.org/showthread.php?t=1849602](http://ubuntuforums.org/showthread.php?t=1849602)
The was two solutions that worked for me, the one i posted in post #20, and the one in post #71 
I have had both of then working in 12.04 but for some unknown reason the easy one in #20 did not work after i upgraded til 12.04 for good. I get the bughttps://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582
So now i use the solutin #20, it works fine.

And I to suffer from the lock ups when suspending, and are looking for a solution. (without downgrading the kernel).

---

### Post by DriverDevel on 2012-12-29
Generic suspend/resume breakage debugging instructions:

First, try removing many/all modules (rmmod) prior to suspending
(the rmmod commands should ideally be done in a small shell script to gain nice automization via an editable list of candidate modules from test to test).
If you then suddenly manage to keep the machine working post resume then you know which are the candidate modules that the one that broke it is a part of.
Then reduce the set of removed modules after each fresh boot until it starts failing again and thereby you finally nailed down which module broke it.
Then file a kernel.org bug report about this module.

If even removing all loadable modules did not help...

Then you ought to read the kernel's linux/Documentation/power/basic-pm-debugging.txt file (and possibly other files in this source directory) on how to do debugging of partial power management suspend steps, until this hopefully manages to sufficiently pinpoint the issue.
In this case, do a kernel.org bug report as well.

---

### Post by os2 on 2013-01-04
I am having the exact same issue with Suspend/Hibernate not working properly on an HP 6910p. Some of the deviced go off, others stay on (some lights are still lit), and the fan starts spinning at full throttle. Only way to recover is via hard boot.

I've had the exact same issue on both Ubuntu 12.x and OpenSuse 12.x.

In the /var/log/pm-suspend.log this is only Fail checkmark:

/usr/lib/pm-utils/sleep.d/50rcnetwork suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.



This blog seems to suggest a solution by changing ACPI settings in version 7. Don't know how relevant it is to version 12.

[http://jkyamog.blogspot.be/2007/12/linux-install-on-hp-6910p-using-ubuntu.html](http://jkyamog.blogspot.be/2007/12/linux-install-on-hp-6910p-using-ubuntu.html)

---

### Post by mikaelpersson on 2013-01-05
There is a bug report about this on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1007924](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1007924)

It seems that an update to the network manager's scripting interface has caused the current sleep/wake commands to be broken. There is a patch and/or instructions to do the fix manually in the sleep command.

I've been having the same issue with resuming from sleep since 12.04. However, I do not have a wireless card on my desktop computer, so this must not be the root cause. And the fix in the bug report did solve the network manager problem that shows up in the suspend logs. However, the overall problem with the resume persists. That is, resuming from sleep or hibernate results in the screen remaining asleep (i.e., the LED remains in "sleep" mode for the screen), and the computer simply winds up with a full-speed running fan and nothing else happens, until I press down the power-button to force a shutdown.

My computer was always set to automatically hibernate after about 1 hour without being used, and I never had any problems until an upgrade to 12.04. Now, I always put it to sleep (to RAM) instead, but about 1 time out of 2, I get the problem described above (and throughout this thread).

Cheers,
Mikael

---

### Post by johnbasinger84 on 2013-06-22
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: ec:a8:6b:79:9c:e3
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.035.00-NAPI duplex=full ip=192.168.1.8 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

---

