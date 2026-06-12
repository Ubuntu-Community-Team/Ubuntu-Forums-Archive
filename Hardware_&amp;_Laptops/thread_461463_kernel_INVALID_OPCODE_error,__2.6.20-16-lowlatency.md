---
title: "kernel /INVALID OPCODE/ error,  2.6.20-16-lowlatency #2 SMP PREEMPT"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by tomjennings on 2007-06-01
Hi,

I had a bad kernel error today, posted below. At the time I was doing apt-get, but I don't think it was that app... simultaneously the wifi driver dropped the link (my wifi Slimserver client stayed up, so it wasn't the AP) and I was unable to bring up the link again, so the driver got upset somehow. It worked fine after reboot.

syslog gunk from that time follows.

Did a clean install on Tuesday (partition up). Ubuntustudio 7.04. More details available.


Begin DISTRACTING NOTE;
> The following packages were automatically installed and are no longer required:
>   libcpufreq0 libpowersave10

Umm, duh, I bungled my power management. I apt-get remove'd powersave. Brain said one thing, fingers another. I reinstalled it after reboot. 
End DISTRACTING NOTE;


cut'n'paste of xterm at time of bug:

```

tomic@qx:~/Pointless-graphics/new-photos/01Jun2007$ sudo apt-get install gxine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcpufreq0 libpowersave10
Use 'apt-get autoremove' to remove them.
Suggested packages:
  realplayer libdvdcss2 libdvdcss gxineplugin
The following NEW packages will be installed:
  gxine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 285kB of archives.
After unpacking 1331kB of additional disk space will be used.
0% [Connecting to us.archive.ubuntu.com]
Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] ------------[ cut here ]------------

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] ------------[ cut here ]------------

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] invalid opcode: 0000 [#1]

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] invalid opcode: 0000 [#1]

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] PREEMPT SMP 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] PREEMPT SMP 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] CPU:    0

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] CPU:    0

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] EIP:    0060:[run_workqueue+238/320]    Not tainted VLI

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] EIP:    0060:[run_workqueue+238/320]    Not tainted VLI

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] eax: 000303bc   ebx: f78fd8d0   ecx: f7aae000   edx: 00000000

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] eax: 000303bc   ebx: f78fd8d0   ecx: f7aae000   edx: 00000000

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] esi: f78fd8c0   edi: f78fd8cc   ebp: 00000213   esp: f7aaff58

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] EIP is at run_workqueue+0xee/0x140

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] EIP is at run_workqueue+0xee/0x140

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] EFLAGS: 00010292   (2.6.20-16-lowlatency #2)

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] EFLAGS: 00010292   (2.6.20-16-lowlatency #2)

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] Stack: 00000000 ffffffff c0122713 00000060 f78fd8cf f78fd8e8 00000001 f78fd8c0 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] esi: f78fd8c0   edi: f78fd8cc   ebp: 00000213   esp: f7aaff58

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [worker_thread+0/368] worker_thread+0x0/0x170

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] Process ipw3945/0 (pid: 3929, ti=f7aae000 task=dff32570 task.ti=f7aae000)

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [kthread+186/240] kthread+0xba/0xf0

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [kthread+186/240] kthread+0xba/0xf0

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [default_wake_function+0/16] default_wake_function+0x0/0x10

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [keventd_create_kthread+110/112] keventd_create_kthread+0x6e/0x70

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [keventd_create_kthread+110/112] keventd_create_kthread+0x6e/0x70

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]        00000000 00000000 dff32570 c0121f70 00100100 00200200 ffffffff ffffffff 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] Code: 24 00 00 00 00 e8 93 6b fe ff 8b 44 24 10 3b 46 10 0f 85 78 ff ff ff 83 6e 40 01 89 ea 83 c4 1c 89 f0 5b 5e 5f 5d e9 32 c5 1b 00 <0f> 0b eb fe 65 a1 08 00 00 00 8b 90 a4 00 00 00 05 94 01 00 00 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] Stack: 00000000 ffffffff c0122713 00000060 f78fd8cf f78fd8e8 00000001 f78fd8c0 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] Process ipw3945/0 (pid: 3929, ti=f7aae000 task=dff32570 task.ti=f7aae000)

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]        00000000 00000000 dff32570 c0121f70 00100100 00200200 ffffffff ffffffff 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] Code: 24 00 00 00 00 e8 93 6b fe ff 8b 44 24 10 3b 46 10 0f 85 78 ff ff ff 83 6e 40 01 89 ea 83 c4 1c 89 f0 5b 5e 5f 5d e9 32 c5 1b 00 <0f> 0b eb fe 65 a1 08 00 00 00 8b 90 a4 00 00 00 05 94 01 00 00 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [sub_preempt_count+19/144] sub_preempt_count+0x13/0x90

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] Call Trace:

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  =======================

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] Call Trace:

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [worker_thread+0/368] worker_thread+0x0/0x170

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [worker_thread+327/368] worker_thread+0x147/0x170

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]        f78fd8d0 f78fd8d8 f7aaff9c c0139667 00000001 00000000 c1fff840 00010000 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [worker_thread+327/368] worker_thread+0x147/0x170

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]        f78fd8d0 f78fd8d8 f7aaff9c c0139667 00000001 00000000 c1fff840 00010000 

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  =======================

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000]  [sub_preempt_count+19/144] sub_preempt_count+0x13/0x90

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] EIP: [run_workqueue+238/320] run_workqueue+0xee/0x140 SS:ESP 0068:f7aaff58

Message from syslogd@qx at Fri Jun  1 13:00:48 2007 ...
qx kernel: [135571.288000] EIP: [run_workqueue+238/320] run_workqueue+0xee/0x140 SS:ESP 0068:f7aaff58
0% [Connecting to us.archive.ubuntu.com]
0% [Connecting to us.archive.ubuntu.com]






```

Log junk:

```

$ sudo egrep "13:00:48" /var/log/*

/var/log/auth.log:Jun  1 15:34:15 qx sudo:    tomic : TTY=pts/0 ; PWD=/home/tomic ; USER=root ; COMMAND=/bin/egrep 13:00:48 /var/log/acpid /var/log/apport.log /var/log/apport.log.1 /var/log/apport.log.2.gz /var/log/apport.log.3.gz /var/log/auth.log /var/log/auth.log.0 /var/log/boot /var/log/btmp /var/log/btmp.1 /var/log/cups /var/log/daemon.log /var/log/daemon.log.0 /var/log/daemon.log.1.gz /var/log/debug /var/log/debug.0 /var/log/dist-upgrade /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dmesg.4.gz /var/log/dpkg.log /var/log/dpkg.log.1 /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/kern.log /var/log/kern.log.0 /var/log/kismet /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/messages.0 /var/log/news /var/log/pycentral.log /var/log/samba /var/log/scrollkeeper.log /var/log/suspend2ram.log /var/log/syslog
/var/log/auth.log:Jun  1 15:34:32 qx sudo:    tomic : TTY=pts/0 ; PWD=/home/tomic ; USER=root ; COMMAND=/bin/egrep 13:00:48 /var/log/acpid /var/log/apport.log /var/log/apport.log.1 /var/log/apport.log.2.gz /var/log/apport.log.3.gz /var/log/auth.log /var/log/auth.log.0 /var/log/boot /var/log/btmp /var/log/btmp.1 /var/log/cups /var/log/daemon.log /var/log/daemon.log.0 /var/log/daemon.log.1.gz /var/log/debug /var/log/debug.0 /var/log/dist-upgrade /var/log/dmesg /var/log/dmesg.0 /var/log/dmesg.1.gz /var/log/dmesg.2.gz /var/log/dmesg.3.gz /var/log/dmesg.4.gz /var/log/dpkg.log /var/log/dpkg.log.1 /var/log/faillog /var/log/fontconfig.log /var/log/fsck /var/log/gdm /var/log/installer /var/log/kern.log /var/log/kern.log.0 /var/log/kismet /var/log/lastlog /var/log/lpr.log /var/log/mail.err /var/log/mail.info /var/log/mail.log /var/log/mail.warn /var/log/messages /var/log/messages.0 /var/log/news /var/log/pycentral.log /var/log/samba /var/log/scrollkeeper.log /var/log/suspend2ram.log /var/log/syslog
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): n to 00:11:50:72:57:d2 completed (reauth) [id=0 id_str=] 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 33 36 2d 34 00 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): wpa_driver_wext_set_operstate: operstate 0->1 (UP) 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): WEXT: Operstate: linkmode=-1, operstate=6 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Cancelling scan request 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING]) 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Wireless event: cmd=0x8b15 len=20 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Wireless event: new AP: 00:00:00:00:00:00 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Setting scan request: 0 sec 100000 usec 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Added BSSID 00:11:50:72:57:d2 into blacklist 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 33 36 2d 34 00 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): State: COMPLETED -> DISCONNECTED 
/var/log/daemon.log:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT) 
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] ------------[ cut here ]------------
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] kernel BUG at kernel/workqueue.c:323!
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] invalid opcode: 0000 [#1]
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] PREEMPT SMP 
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage libusual acpi_cpufreq cpufreq_powersave cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_ondemand ipv6 binfmt_misc freq_table rfcomm l2cap sonypi ppdev dev_acpi tc1100_wmi sony_acpi pcc_acpi ac button dock video battery asus_acpi container backlight sbs i2c_ec i2c_core fuse sbp2 parport_pc lp parport snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device joydev ipw3945 hci_usb iTCO_wdt iTCO_vendor_support snd pcmcia bluetooth ieee80211 ieee80211_crypt soundcore tifm_7xx1 yenta_socket rsrc_nonstatic pcmcia_core psmouse tifm_core snd_page_alloc intel_agp serio_raw agpgart af_packet shpchp pci_hotplug tsdev evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom ata_piix ata_generic libata scsi_mod e100 mii ohci1394 ieee1394 piix generic ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tile
/var/log/kern.log:Jun  1 13:00:48 qx kernel: lit font bitblit softcursor vesafb capability commoncap
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] CPU:    0
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] EIP:    0060:[run_workqueue+238/320]    Not tainted VLI
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] EFLAGS: 00010292   (2.6.20-16-lowlatency #2)
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] EIP is at run_workqueue+0xee/0x140
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] eax: 000303bc   ebx: f78fd8d0   ecx: f7aae000   edx: 00000000
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] esi: f78fd8c0   edi: f78fd8cc   ebp: 00000213   esp: f7aaff58
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] ds: 007b   es: 007b   ss: 0068
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] Process ipw3945/0 (pid: 3929, ti=f7aae000 task=dff32570 task.ti=f7aae000)
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] Stack: 00000000 ffffffff c0122713 00000060 f78fd8cf f78fd8e8 00000001 f78fd8c0 
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]        f78fd8d0 f78fd8d8 f7aaff9c c0139667 00000001 00000000 c1fff840 00010000 
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]        00000000 00000000 dff32570 c0121f70 00100100 00200200 ffffffff ffffffff 
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] Call Trace:
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]  [sub_preempt_count+19/144] sub_preempt_count+0x13/0x90
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]  [worker_thread+327/368] worker_thread+0x147/0x170
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]  [worker_thread+0/368] worker_thread+0x0/0x170
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]  [kthread+186/240] kthread+0xba/0xf0
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]  [keventd_create_kthread+110/112] keventd_create_kthread+0x6e/0x70
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000]  =======================
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] Code: 24 00 00 00 00 e8 93 6b fe ff 8b 44 24 10 3b 46 10 0f 85 78 ff ff ff 83 6e 40 01 89 ea 83 c4 1c 89 f0 5b 5e 5f 5d e9 32 c5 1b 00 <0f> 0b eb fe 65 a1 08 00 00 00 8b 90 a4 00 00 00 05 94 01 00 00 
/var/log/kern.log:Jun  1 13:00:48 qx kernel: [135571.288000] EIP: [run_workqueue+238/320] run_workqueue+0xee/0x140 SS:ESP 0068:f7aaff58
/var/log/messages:Jun  1 13:00:48 qx kernel: [135571.288000] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage libusual acpi_cpufreq cpufreq_powersave cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_ondemand ipv6 binfmt_misc freq_table rfcomm l2cap sonypi ppdev dev_acpi tc1100_wmi sony_acpi pcc_acpi ac button dock video battery asus_acpi container backlight sbs i2c_ec i2c_core fuse sbp2 parport_pc lp parport snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device joydev ipw3945 hci_usb iTCO_wdt iTCO_vendor_support snd pcmcia bluetooth ieee80211 ieee80211_crypt soundcore tifm_7xx1 yenta_socket rsrc_nonstatic pcmcia_core psmouse tifm_core snd_page_alloc intel_agp serio_raw agpgart af_packet shpchp pci_hotplug tsdev evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom ata_piix ata_generic libata scsi_mod e100 mii ohci1394 ieee1394 piix generic ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tile
/var/log/messages:Jun  1 13:00:48 qx kernel: lit font bitblit softcursor vesafb capability commoncap
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] ------------[ cut here ]------------
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] kernel BUG at kernel/workqueue.c:323!
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] invalid opcode: 0000 [#1]
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] PREEMPT SMP 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage libusual acpi_cpufreq cpufreq_powersave cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_ondemand ipv6 binfmt_misc freq_table rfcomm l2cap sonypi ppdev dev_acpi tc1100_wmi sony_acpi pcc_acpi ac button dock video battery asus_acpi container backlight sbs i2c_ec i2c_core fuse sbp2 parport_pc lp parport snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device joydev ipw3945 hci_usb iTCO_wdt iTCO_vendor_support snd pcmcia bluetooth ieee80211 ieee80211_crypt soundcore tifm_7xx1 yenta_socket rsrc_nonstatic pcmcia_core psmouse tifm_core snd_page_alloc intel_agp serio_raw agpgart af_packet shpchp pci_hotplug tsdev evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom ata_piix ata_generic libata scsi_mod e100 mii ohci1394 ieee1394 piix generic ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tile
/var/log/syslog:Jun  1 13:00:48 qx kernel: lit font bitblit softcursor vesafb capability commoncap
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] CPU:    0
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] EIP:    0060:[run_workqueue+238/320]    Not tainted VLI
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] EFLAGS: 00010292   (2.6.20-16-lowlatency #2)
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] EIP is at run_workqueue+0xee/0x140
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] eax: 000303bc   ebx: f78fd8d0   ecx: f7aae000   edx: 00000000
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] esi: f78fd8c0   edi: f78fd8cc   ebp: 00000213   esp: f7aaff58
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] ds: 007b   es: 007b   ss: 0068
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] Process ipw3945/0 (pid: 3929, ti=f7aae000 task=dff32570 task.ti=f7aae000)
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] Stack: 00000000 ffffffff c0122713 00000060 f78fd8cf f78fd8e8 00000001 f78fd8c0 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]        f78fd8d0 f78fd8d8 f7aaff9c c0139667 00000001 00000000 c1fff840 00010000 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]        00000000 00000000 dff32570 c0121f70 00100100 00200200 ffffffff ffffffff 
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): n to 00:11:50:72:57:d2 completed (reauth) [id=0 id_str=] 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] Call Trace:
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 33 36 2d 34 00 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]  [sub_preempt_count+19/144] sub_preempt_count+0x13/0x90
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): wpa_driver_wext_set_operstate: operstate 0->1 (UP) 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]  [worker_thread+327/368] worker_thread+0x147/0x170
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): WEXT: Operstate: linkmode=-1, operstate=6 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Cancelling scan request 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]  [worker_thread+0/368] worker_thread+0x0/0x170
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]  [kthread+186/240] kthread+0xba/0xf0
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]  [keventd_create_kthread+110/112] keventd_create_kthread+0x6e/0x70
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING]) 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Wireless event: cmd=0x8b15 len=20 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000]  =======================
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Wireless event: new AP: 00:00:00:00:00:00 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] Code: 24 00 00 00 00 e8 93 6b fe ff 8b 44 24 10 3b 46 10 0f 85 78 ff ff ff 83 6e 40 01 89 ea 83 c4 1c 89 f0 5b 5e 5f 5d e9 32 c5 1b 00 <0f> 0b eb fe 65 a1 08 00 00 00 8b 90 a4 00 00 00 05 94 01 00 00 
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Setting scan request: 0 sec 100000 usec 
/var/log/syslog:Jun  1 13:00:48 qx kernel: [135571.288000] EIP: [run_workqueue+238/320] run_workqueue+0xee/0x140 SS:ESP 0068:f7aaff58
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): Added BSSID 00:11:50:72:57:d2 into blacklist 
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys 
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 30 33 36 2d 34 00 
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): State: COMPLETED -> DISCONNECTED 
/var/log/syslog:Jun  1 13:00:48 qx NetworkManager: <information>^Iwpa_supplicant(4853): wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT) 
tomic@qx:~$ 


```

---

### Post by tedrampart on 2007-06-03
this **just** happened to me, I don't know how to solve it, but I thought I'd voice up and say there's another with this problem.

I'm not using the lowlatency kernel, just the generic kernel.

---

### Post by tomjennings on 2007-06-03
What was the trigger? What kernel version? (uname -a) etc.... anyone debugging will need all that, and more; save your logs from that time.

---

