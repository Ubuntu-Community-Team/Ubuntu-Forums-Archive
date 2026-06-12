---
title: "ipw3945 kernel BUG at kernel/workqueue.c:323!"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by rhand on 2007-10-06
I'm having some trouble with my wireless connection.

This only happens once in a while and because I have to reboot to get it working again I forgot to report it earlier. I've found a bugreport [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117842](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117842) But it doesn't give any information and is still described as 'new'. This is kinda important for me, because I usually have a few nfs mounted and it's hard to use my file system after this happens.
I hope someone has more information for me... 
Is it usefull to post this information in the bugreport? It doesn't really add anything...

I'm on Feisty Fawn with an Acer Aspire 9412

Linux aldazar 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux
roeland@aldazar:~$ modinfo ipw3945 

filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.0mp
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     9B03103B15A8FE1824967C2
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)


```
Oct  6 11:45:58 aldazar kernel: [43828.416000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Oct  6 11:45:59 aldazar kernel: [43829.144000] ipw3945: Error sending cmd #07 to daemon: time out after 500ms.
Oct  6 11:46:00 aldazar kernel: [43829.644000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
Oct  6 11:46:01 aldazar kernel: [43830.744000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Oct  6 11:46:01 aldazar kernel: [43831.244000] ipw3945: Error sending cmd #08 to daemon: time out after 500ms.
Oct  6 11:46:02 aldazar kernel: [43831.744000] ipw3945: Error sending ADD_STA: time out after 500ms.
Oct  6 11:46:02 aldazar kernel: [43832.244000] ipw3945: Error sending SCAN_ABORT_CMD: time out after 500ms.
Oct  6 11:46:02 aldazar kernel: [43832.244000] ------------[ cut here ]------------
Oct  6 11:46:02 aldazar kernel: [43832.244000] kernel BUG at kernel/workqueue.c:323!
Oct  6 11:46:02 aldazar kernel: [43832.244000] invalid opcode: 0000 [#1]
Oct  6 11:46:02 aldazar kernel: [43832.244000] SMP 
Oct  6 11:46:02 aldazar kernel: [43832.244000] Modules linked in: nfs lockd sunrpc arc4 ecb blkcipher ieee80211_crypt_wep af_packet isofs udf vmnet(PF) vmmon(PF) binfmt_misc rfcomm l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_userspace cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table sony_acpi dev_acpi pcc_acpi tc1100_wmi asus_acpi button sbs i2c_ec backlight dock battery container video ac nls_utf8 ntfs nls_iso8859_1 nls_cp437 vfat fat eeprom i2c_i801 visor usbserial parport_pc lp parport fuse snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss pcmcia joydev gspca snd_pcm nvidia(P) videodev v4l2_common ipw3945 tifm_7xx1 snd_seq_dummy ieee80211 i2c_core snd_seq_oss v4l1_compat yenta_socket rsrc_nonstatic ieee80211_crypt tifm_core snd_seq_midi snd_rawmidi snd_seq_midi_event iTCO_wdt iTCO_vendor_support sdhci mmc_core pcmcia_core psmouse serio_raw snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc shpchp pci_hotplug intel_agp agpgart tsdev evdev ext3 jbd mbcache usbhid hi
Oct  6 11:46:02 aldazar kernel:  sg sr_mod cdrom sd_mod generic ata_generic uhci_hcd ata_piix libata scsi_mod r8169 ehci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Oct  6 11:46:02 aldazar kernel: [43832.244000] CPU:    0
Oct  6 11:46:02 aldazar kernel: [43832.244000] EIP:    0060:[run_workqueue+238/320]    Tainted: PF     VLI
Oct  6 11:46:02 aldazar kernel: [43832.244000] EFLAGS: 00010292   (2.6.20-16-generic #2)
Oct  6 11:46:02 aldazar kernel: [43832.244000] EIP is at run_workqueue+0xee/0x140
Oct  6 11:46:02 aldazar kernel: [43832.244000] eax: 0001156c   ebx: f79e64cc   ecx: 00000246   edx: 00000000
Oct  6 11:46:02 aldazar kernel: [43832.244000] esi: f79e64c0   edi: f79e64c8   ebp: 00000246   esp: f7959f58
Oct  6 11:46:02 aldazar kernel: [43832.244000] ds: 007b   es: 007b   ss: 0068
Oct  6 11:46:02 aldazar kernel: [43832.244000] Process ipw3945/0 (pid: 5311, ti=f7958000 task=dfa67030 task.ti=f7958000)
Oct  6 11:46:02 aldazar kernel: [43832.244000] Stack: 00000000 f79e64d4 f7959f9c 00000246 f79e64cb f79e64e0 00000001 f79e64c0 
Oct  6 11:46:02 aldazar kernel: [43832.244000]        f79e64cc f79e64d4 f7959f9c c0137d97 00000001 00000000 c200c5c0 00010000 
Oct  6 11:46:02 aldazar kernel: [43832.244000]        00000000 00000000 dfa67030 c0120b40 00100100 00200200 ffffffff ffffffff 
Oct  6 11:46:02 aldazar kernel: [43832.244000] Call Trace:
Oct  6 11:46:02 aldazar kernel: [43832.244000]  [worker_thread+327/368] worker_thread+0x147/0x170
Oct  6 11:46:02 aldazar kernel: [43832.244000]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Oct  6 11:46:02 aldazar kernel: [43832.244000]  [worker_thread+0/368] worker_thread+0x0/0x170
Oct  6 11:46:02 aldazar kernel: [43832.244000]  [kthread+186/240] kthread+0xba/0xf0
Oct  6 11:46:02 aldazar kernel: [43832.244000]  [keventd_create_kthread+110/112] keventd_create_kthread+0x6e/0x70
Oct  6 11:46:02 aldazar kernel: [43832.244000]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10
Oct  6 11:46:02 aldazar kernel: [43832.244000]  =======================
Oct  6 11:46:02 aldazar kernel: [43832.244000] Code: 24 00 00 00 00 e8 f3 72 fe ff 8b 44 24 10 3b 46 0c 0f 85 78 ff ff ff 83 6e 34 01 89 ea 83 c4 1c 89 f0 5b 5e 5f 5d e9 a2 76 1b 00 <0f> 0b eb fe 65 a1 08 00 00 00 8b 90 a4 00 00 00 05 94 01 00 00 
Oct  6 11:46:02 aldazar kernel: [43832.244000] EIP: [run_workqueue+238/320] run_workqueue+0xee/0x140 SS:ESP 0068:f7959f58
```

---

