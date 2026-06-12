---
title: "USB devices"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by mindstorm15 on 2007-10-13
I'm an Ununtu n00b, and i just installed it on my laptop (Voodoo ENVY N-522) .  I was able to get my audio and graphics working just fine.  However, i can't see any usb devices, ranging from flash drives, external hd's, or even mice and keyboards.  theres not any power going to my USB ports, and I was wondering if i need a USB driver or somemat.  thanks for the help, i need it.

---

### Post by jnorthr on 2007-10-13
do you have windows on this machine and does it recognise the USb devices ?
can you post the results of
lshw
so we can see your hardware ? also look at dmesg just after you insert a USB device as it may offer clues as to what's goin' on :KS

---

### Post by mindstorm15 on 2007-10-13
lshw returns the word "USB", and the following is the relevent info from dmesg

[ 2089.068000] usb 5-1: new high speed USB device using ehci_hcd and address 3
[ 2089.200000] usb 5-1: configuration #1 chosen from 1 choice
[ 2089.380000] usbcore: registered new interface driver libusual
[ 2089.388000] Initializing USB Mass Storage driver...
[ 2089.388000] scsi4 : SCSI emulation for USB Mass Storage devices
[ 2089.388000] usbcore: registered new interface driver usb-storage
[ 2089.388000] USB Mass Storage support registered.
[ 2089.388000] usb-storage: device found at 3
[ 2089.388000] usb-storage: waiting for device to settle before scanning
[ 2094.388000] usb-storage: device scan complete
[ 2094.388000] scsi 4:0:0:0: Direct-Access     PNY      USB 2.0 FD       PMAP PQ: 0 ANSI: 0 CCS
[ 2094.520000] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2094.520000] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2095.336000] hub 5-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 2095.448000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[ 2095.560000] ehci_hcd 0000:00:1d.7: port 1 reset error -110
[ 2095.560000] hub 5-0:1.0: hub_port_status failed (err = -32)
[ 2096.376000] hub 5-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 2096.488000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[ 2097.384000] usb 5-1: device descriptor read/8, error -71
[ 2097.504000] usb 5-1: device descriptor read/8, error -71
[ 2097.720000] usb 5-1: reset high speed USB device using ehci_hcd and address 3
[ 2098.128000] usb 5-1: device not accepting address 3, error -71
[ 2098.128000] usb 5-1: USB disconnect, address 3
[ 2098.128000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[ 2098.128000]  printing eip:
[ 2098.128000] c0258315
[ 2098.128000] *pde = 00000000
[ 2098.128000] Oops: 0000 [#1]
[ 2098.128000] SMP 
[ 2098.128000] Modules linked in: usb_storage libusual ipv6 binfmt_misc rfcomm l2cap bluetooth ppdev speedstep_centrino cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_userspace dev_acpi pcc_acpi tc1100_wmi sony_acpi ac asus_acpi sbs button container dock backlight i2c_ec battery video sbp2 parport_pc lp parport af_packet fuse zc0301 joydev irtty_sir sir_dev gspca snd_hda_intel snd_hda_codec pcmcia irda snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss videodev v4l2_common v4l1_compat snd_seq_midi snd_rawmidi snd_seq_midi_event crc_ccitt serio_raw psmouse ipw2200 snd_seq snd_timer snd_seq_device ieee80211 ieee80211_crypt sky2 snd soundcore yenta_socket rsrc_nonstatic pcmcia_core nvidia(P) intel_agp agpgart snd_page_alloc i2c_core iTCO_wdt iTCO_vendor_support shpchp pci_hotplug evdev tsdev ext3 jbd mbcache sg sr_mod cdrom sd_mod ahci ata_piix ata_generic libata scsi_mod ehci_hcd ohci1394 ieee1394 generic uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[ 2098.128000] CPU:    0
[ 2098.128000] EIP:    0060:[<c0258315>]    Tainted: P      VLI
[ 2098.128000] EFLAGS: 00010202   (2.6.20-15-generic #2)
[ 2098.128000] EIP is at make_class_name+0x35/0xa0
[ 2098.128000] eax: 00000000   ebx: ffffffff   ecx: ffffffff   edx: 0000000b
[ 2098.128000] esi: f8964c91   edi: 00000000   ebp: 00000000   esp: c1bdde50
[ 2098.128000] ds: 007b   es: 007b   ss: 0068
[ 2098.128000] Process khubd (pid: 1962, ti=c1bdc000 task=dfcc1a90 task.ti=c1bdc000)
[ 2098.128000] Stack: e331aa04 f8976ec0 e331a9fc e331aa04 f8976e40 c0258591 00000000 f8976ec8 
[ 2098.128000]        e331a9fc e1390800 00000246 ffffffed c0258618 e331a800 f895ea50 e331a800 
[ 2098.128000]        e1390800 f895c12b e1390830 e1390800 f8956825 e1390af4 e13dfe18 f8fb1f60 
[ 2098.128000] Call Trace:
[ 2098.128000]  [<c0258591>] class_device_del+0xa1/0x120
[ 2098.128000]  [<c0258618>] class_device_unregister+0x8/0x10
[ 2098.128000]  [<f895ea50>] __scsi_remove_device+0x30/0x80 [scsi_mod]
[ 2098.128000]  [<f895c12b>] scsi_forget_host+0x4b/0x60 [scsi_mod]
[ 2098.128000]  [<f8956825>] scsi_remove_host+0x55/0xe0 [scsi_mod]
[ 2098.128000]  [<f8fa3cae>] storage_disconnect+0xe/0x20 [usb_storage]
[ 2098.128000]  [<f8893d20>] usb_unbind_interface+0x50/0xa0 [usbcore]
[ 2098.128000]  [<c02578a8>] __device_release_driver+0x68/0xa0
[ 2098.128000]  [<c0257dd3>] device_release_driver+0x23/0x40
[ 2098.128000]  [<c025721c>] bus_remove_device+0x5c/0x90
[ 2098.128000]  [<c0255672>] device_del+0x152/0x1b0
[ 2098.128000]  [<f88911ee>] usb_disable_device+0x7e/0xe0 [usbcore]
[ 2098.128000]  [<f888d597>] usb_disconnect+0x97/0x130 [usbcore]
[ 2098.128000]  [<f888e2ff>] hub_thread+0x26f/0xc20 [usbcore]
[ 2098.128000]  [<c013adf0>] autoremove_wake_function+0x0/0x50
[ 2098.128000]  [<f888e090>] hub_thread+0x0/0xc20 [usbcore]
[ 2098.128000]  [<c013ac3a>] kthread+0xba/0xf0
[ 2098.128000]  [<c013ab80>] kthread+0x0/0xf0
[ 2098.128000]  [<c01044c7>] kernel_thread_helper+0x7/0x10
[ 2098.128000]  =======================
[ 2098.128000] Code: ff ff 89 6c 24 10 31 ed 89 d9 89 74 24 08 89 c6 89 7c 24 0c 89 c7 89 e8 89 14 24 f2 ae f7 d1 49 8b 04 24 89 ca 89 d9 8b 38 89 e8 <f2> ae f7 d1 49 8d 44 0a 02 ba d0 00 00 00 e8 38 ae f1 ff ba f4 
[ 2098.128000] EIP: [<c0258315>] make_class_name+0x35/0xa0 SS:ESP 0068:c1bdde50
[ 2098.128000]  <5>sdb : READ CAPACITY failed.
[ 2098.136000] sdb : status=0, message=00, host=1, driver=00 
[ 2098.136000] sdb : sense not available. 
[ 2098.136000] sdb: Write Protect is off
[ 2098.136000] sdb: Mode Sense: 00 00 00 00
[ 2098.136000] sdb: assuming drive cache: write through
[ 2098.136000] sd 4:0:0:0: Attached scsi removable disk sdb
[ 2098.136000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2098.156000] sdb : READ CAPACITY failed.
[ 2098.156000] sdb : status=0, message=00, host=1, driver=00 
[ 2098.156000] sdb : sense not available. 
[ 2098.156000] sdb: Write Protect is off
[ 2098.156000] sdb: Mode Sense: 00 00 00 00
[ 2098.156000] sdb: assuming drive cache: write through
[ 2098.160000] sdb : READ CAPACITY failed.
[ 2098.160000] sdb : status=0, message=00, host=1, driver=00 
[ 2098.160000] sdb : sense not available. 
[ 2098.160000] sdb: Write Protect is off
[ 2098.160000] sdb: Mode Sense: 00 00 00 00
[ 2098.160000] sdb: assuming drive cache: write through
[ 2098.172000] sdb : READ CAPACITY failed.
[ 2098.172000] sdb : status=0, message=00, host=1, driver=00 
[ 2098.172000] sdb : sense not available. 
[ 2098.172000] sdb: Write Protect is off
[ 2098.172000] sdb: Mode Sense: 00 00 00 00
[ 2098.172000] sdb: assuming drive cache: write through
[ 2098.184000] sdb : READ CAPACITY failed.
[ 2098.184000] sdb : status=0, message=00, host=1, driver=00 
[ 2098.184000] sdb : sense not available. 
[ 2098.188000] sdb: Write Protect is off
[ 2098.188000] sdb: Mode Sense: 00 00 00 00
[ 2098.188000] sdb: assuming drive cache: write through
[ 4977.756000] ADDRCONF(NETDEV_UP): eth1: link is not ready

thx

---

### Post by mindstorm15 on 2007-10-13
oh, and the drive definitely works fine, on xp and vista (eww)

---

### Post by treesnogger on 2007-10-13
I'm experiencing the same problem on an HP Pavilion dv1000.

---

### Post by jonathanmotes on 2007-10-14
> I'm experiencing the same problem on an HP Pavilion dv1000.The bootup parameters described [here]("http://ubuntuforums.org/showthread.php?t=512059") should fix the USB problem for HP users and might for others too.

---

