---
title: "Freecom DVB-T USB problem"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by Zars on 2007-11-03
Hello there :)

I have just bought a Freecom DVB-T USB TV tuner, and have been trying to get it to work on Gutsy. The output of 'lsusb' is:

```
 Bus 005 Device 003: ID 14aa:0226 AVerMedia (again) or C&E 
```

I have managed to download the correct firmware for the device, and so now, when plugged in, the USB LED is on. The end of the output of dmesg is:

```
[  718.720000] usb 5-3: configuration #1 chosen from 1 choice
[  718.720000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[  718.720000] dvb-usb: will use the device's hardware PID filter (table count: 15).
[  718.720000] DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom)).
[  718.720000] DVB: registering frontend 0 (WideView USB DVB-T)...
[  718.720000] input: IR-receiver inside an USB DVB receiver as /class/input/input9
[  718.720000] dvb-usb: schedule remote query interval to 300 msecs.
[  718.720000] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[  718.720000] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Freecom)' in warm state.
[  718.720000] dvb-usb: will use the device's hardware PID filter (table count: 15).
[  718.720000] DVB: registering new adapter (WideView WT-220U PenType Receiver (Typhoon/Freecom)).
[  718.720000] DVB: registering frontend 1 (WideView USB DVB-T)...
[  718.720000] input: IR-receiver inside an USB DVB receiver as /class/input/input10
[  718.720000] dvb-usb: schedule remote query interval to 300 msecs.
[  718.720000] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) successfully initialized and connected.
[  721.024000] dvb-usb: recv bulk message failed: -110
```

The problem comes when I try to use 'scan' to make the channels.conf file. I have tries many different initial config files, but all to no avail. I live in Wareham, Dorset, South England. I have tried the uk-Reigate and uk-Rowridge files from [http://www.linuxtv.org/hg/dvb-apps/file/bd51e3321c05/util/scan/dvb-t/]("http://www.linuxtv.org/hg/dvb-apps/file/bd51e3321c05/util/scan/dvb-t/").

Could someone please help me generate my channels.conf file. I know enough about Ubuntu to get by, some simple instructions where possible!

Thanks very much :D. Zars.

---

### Post by madsmaddad on 2007-12-20
from Wimborne, dorset. I did have my freecom DVB-T working under Feisty, but cannot get it working again under Gutsy. I did an upgrade from feisty to Gutsy, and have followed the instructions (again and again!) from 
[http://www.ubuntuforums.org/showthread.php?t=183297](http://www.ubuntuforums.org/showthread.php?t=183297) 

I now have the situation where Kaffeine starts up on login, but without the DVB icon. 

dmesg gives: 

] eth1: no IPv6 routers present
[  131.581952] usb 4-5: new high speed USB device using ehci_hcd and address 3
[  131.714326] usb 4-5: configuration #1 chosen from 1 choice
[  131.863817] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free
com)' in cold state, will try to load a firmware
[  131.870422] dvb-usb: downloading firmware from file 'dvb-usb-wt220u-fc03.fw'
[  131.949930] usbcore: registered new interface driver dvb_usb_dtt200u
[  133.308691] usb 4-5: USB disconnect, address 3
[  133.308766] dvb-usb: generic DVB-USB module successfully deinitialized and di
sconnected.
[  134.431345] usb 4-5: new high speed USB device using ehci_hcd and address 4
[  134.568284] usb 4-5: configuration #1 chosen from 1 choice
[  134.568430] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free
com)' in warm state.
[  134.568508] dvb-usb: will use the device's hardware PID filter (table count:
15).
[  134.568793] DVB: registering new adapter (WideView WT-220U PenType Receiver (
Typhoon/Freecom)).
[  134.568938] DVB: registering frontend 0 (WideView USB DVB-T)...
[  134.569325] input: IR-receiver inside an USB DVB receiver as /class/input/inp
ut6
[  134.569361] dvb-usb: schedule remote query interval to 300 msecs.
[  134.569367] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) succ
essfully initialized and connected.
[  134.569541] dvb-usb: found a 'WideView WT-220U PenType Receiver (Typhoon/Free
com)' in warm state.
[  134.569631] dvb-usb: will use the device's hardware PID filter (table count:
15).
[  134.569912] DVB: registering new adapter (WideView WT-220U PenType Receiver (
Typhoon/Freecom)).
[  134.570009] DVB: registering frontend 1 (WideView USB DVB-T)...
[  134.570317] input: IR-receiver inside an USB DVB receiver as /class/input/inp
ut7
[  134.570349] dvb-usb: schedule remote query interval to 300 msecs.
[  134.570354] dvb-usb: WideView WT-220U PenType Receiver (Typhoon/Freecom) succ
essfully initialized and connected.
[  134.681448] usbcore: registered new interface driver hiddev
[  134.682147] usbcore: registered new interface driver usbhid
[  134.682350] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-c
ore.c: v2.6:USB HID core driver
[  134.703907] usbcore: registered new interface driver xpad
[  134.704315] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/x
pad.c: driver for Xbox controllers v0.1.6
[  136.865222] dvb-usb: recv bulk message failed: -110
[  144.337816] BUG: unable to handle kernel NULL pointer dereference at virtual
address 00000020
[  144.337824]  printing eip:
[  144.337827] ded5be77
[  144.337828] *pde = 00000000
[  144.337833] Oops: 0000 [#1]
[  144.337834] SMP
[  144.337839] Modules linked in: xpad usbhid hid dvb_usb_dtt200u dvb_usb dvb_co
re i2c_core rfcomm l2cap bluetooth ppdev speedstep_lib cpufreq_powersave cpufreq
_userspace cpufreq_conservative cpufreq_stats cpufreq_ondemand freq_table sbs vi
deo container button dock ac battery nls_iso8859_1 nls_cp437 vfat fat ipv6 af_pa
cket lp snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm s
nd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq zd1
211rw parport_pc parport ieee80211softmac ieee80211 ieee80211_crypt snd_timer pc
spkr psmouse snd_seq_device serio_raw snd soundcore sis_agp snd_page_alloc agpga
rt shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod sata_sis flo
ppy sis900 mii ehci_hcd ohci_hcd pata_sis ata_generic libata scsi_mod usbcore th
ermal processor fan fuse apparmor commoncap
[  144.337923] CPU:    1
[  144.337924] EIP:    0060:[<ded5be77>]    Not tainted VLI
[  144.337925] EFLAGS: 00010282   (2.6.22-14-generic #1)
[  144.337935] EIP is at dvb_usb_fe_wakeup+0x17/0x40 [dvb_usb]
[  144.337938] eax: 00000000   ebx: cd7b302c   ecx: ffffffff   edx: 00000001
[  144.337941] esi: cd7b302c   edi: cd7b3800   ebp: cd7b39b0   esp: cd18bf80
[  144.337944] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
[  144.337947] Process kdvb-fe-0 (pid: 5575, ti=cd18a000 task=c7d6e530 task.ti=c                          d18a000)
[  144.337950] Stack: cd7b302c cd7b302c ded7a5cd 00000021 00000e32 c7d6e640 ffff                          fffc ded7bb06
[  144.337958]        00000003 cc74fe68 d5c63700 ffff4d2e ffffffff cd18bfd0 0000                          00ff 00000000
[  144.337966]        00000000 fffffffc cd7b302c ded7baa0 00000000 c013bb12 c013                          bad0 00000000
[  144.337974] Call Trace:
[  144.337983]  [<ded7a5cd>] dvb_frontend_init+0x1d/0x60 [dvb_core]
[  144.338009]  [<ded7bb06>] dvb_frontend_thread+0x66/0x300 [dvb_core]
[  144.338049]  [<ded7baa0>] dvb_frontend_thread+0x0/0x300 [dvb_core]
[  144.338061]  [<c013bb12>] kthread+0x42/0x70
[  144.338071]  [<c013bad0>] kthread+0x0/0x70
[  144.338081]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  144.338102]  =======================
[  144.338104] Code: 31 d2 5b e9 cc f4 ff ff 8d b6 00 00 00 00 8d bf 00 00 00 00                           83 ec 08 ba 01 00 00 00 89 74 24 04 89 c6 89 1c 24 8b 80 dc 01 00 00 <8b> 58 20                           8b 03 e8 9f f4 ff ff 8b 93 20 03 00 00 85 d2 74 04 89
[  144.338147] EIP: [<ded5be77>] dvb_usb_fe_wakeup+0x17/0x40 [dvb_usb] SS:ESP 00                          68:cd18bf80
peterm@peterm-Kdesktop:~$      

So I can see that it has failed. 

Hope that someone else out there has the knowledge to put all this together and help us both.

---

### Post by madsmaddad on 2007-12-30
I have got it working.   I found it necessary to Uninstall Kaffeine (using adept), reboot and reinstall kaffeine, before following all the instructions in [http://www.ubuntuforums.org/showthread.php?t=183297](http://www.ubuntuforums.org/showthread.php?t=183297) 

to rebuild the drivers. The V4L stuff has been upgraded since this note was posted, so the prompts on the 'make' are a lot more complex. I have kept my answers to the script so if anyone wants it let me know and I will post it. 


Peter M.

---

