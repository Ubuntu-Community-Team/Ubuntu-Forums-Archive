---
title: "How to deal with kernel pancis like Unable to handle kernel paging request ..."
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by anders5737 on 2005-10-01
Hello, 
I've been running Ubuntu for a few months at things have been fine with the kernel. Recently however I have been getting a number of kernel panics with the message "Unable to handle kernel paging request at virtual address ..."
See an example below (taken from dmesg). 
The pattern I have seen is that they are all happening from either RealPlayer (realplay.bin) or Firefox (firefox-bin). Looking at the stack trace it is always the 
[pg0+948974920/1070015488] snd_pcm_oss_open+0xdb/0x289 [snd_pcm_oss]
in the top. I guess the top row is where the 'bug' is, right?
I googled up this [http://lists.debian.org/debian-kernel/2004/09/msg00445.html](http://lists.debian.org/debian-kernel/2004/09/msg00445.html) which leads to Debian bug [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271871](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271871) but I doesn't get much out of those debian pages... Is the bug fixed or not? Doesn't look so...
Now I am not sure this is 'my' bug but how can I have a bug like that fixed? Should I report my issue as a Ubuntu bug? 
Or are there other approaches... 
It seems that it is related to sound support perhaps I can reconfigure somehow to dodge this?
I also have a general question about kernel panics (KP). I see many other people reporting KPs here in the forums but they get no reply. Is it so obvious on how to deal with KPs or are peole just asking impossible questions? It would be good to have a process on howto isolate the most significant features of a KP, like the top row of the stack trace (its significance is more a guess from my side). I try to find a FAQ or  Howto but nothing here at Ubuntu Forum anyway... A [http://www.faqs.org/docs/Linux-HOWTO/Linux-Crash-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Linux-Crash-HOWTO.html) but for Ubuntu/Debian would be nice?
Thanks,
Anders
Sep 23 21:57:29 localhost kernel:  <1>Unable to handle kernel paging request at virtual address 8dd59e78
Sep 23 21:57:29 localhost kernel: f8c160e0
Sep 23 21:57:29 localhost kernel: PREEMPT
Sep 23 21:57:29 localhost kernel: Modules linked in: nls_cp437 isofs udf rfcomm l2cap powernow_k8 proc_intf freq_table cpufreq_userspace cpufreq_ondemand cpufreq_powersave video sony_acpi pcc_acpi button battery container ac ipv6 hci_usb bluetooth joydev wacom tsdev snd_via82xx snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc gameport snd_mpu401_uart af_packet snd_rawmidi snd_seq_device snd soundcore usbhid ehci_hcd uhci_hcd ohci1394 r8169 shpchp pci_hotplug amd64_agp floppy pcspkr rtc md dm_mod capability commoncap it87 eeprom lm90 i2c_sensor i2c_isa i2c_viapro i2c_core nvidia agpgart sbp2 ieee1394 evdev psmouse mousedev parport_pc lp parport ide_generic ide_disk ide_cd via82cxxx ext3 jbd sr_mod cdrom sd_mod usb_storage usbcore ide_core sata_via libata scsi_mod unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
Sep 23 21:57:29 localhost kernel: CPU:    0
Sep 23 21:57:29 localhost kernel: EIP:    0060:[pg0+948478176/1070015488]    Tainted: P      VLI
Sep 23 21:57:29 localhost kernel: EFLAGS: 00210246   (2.6.10-5-386)
Sep 23 21:57:29 localhost kernel: EIP is at snd_task_name+0x8/0x38 [snd]
Sep 23 21:57:29 localhost kernel: eax: c6eac000   ebx: c6eadeb4   ecx: e979fa20   edx: 00000000
Sep 23 21:57:29 localhost kernel: esi: f8bf0320   edi: fffffff2   ebp: f4e86600   esp: c6eade6c
Sep 23 21:57:29 localhost kernel: ds: 007b   es: 007b   ss: 0068
Sep 23 21:57:29 localhost kernel: Process realplay.bin (pid: 28497, threadinfo=c6eac000 task=e979fa20)
Sep 23 21:57:29 localhost kernel: Stack: c6eadeb4 f8bf0320 f8c8f548 e979fa20 c6eadeb4 00000020 00000000 00000000
Sep 23 21:57:29 localhost kernel:        00000003 c6eadf5c c6eadf5c dfff4280 c6eadef4 c6eac000 c6eac000 00000001
Sep 23 21:57:29 localhost kernel:        00000002 f4ab551c c0122159 f11fae80 0000001d 000021b0 f5d1d210 c0151bf9
Sep 23 21:57:29 localhost kernel: Call Trace:
Sep 23 21:57:29 localhost kernel:  [pg0+948974920/1070015488] snd_pcm_oss_open+0xdb/0x289 [snd_pcm_oss]
Sep 23 21:57:29 localhost kernel:  [in_group_p+51/92] in_group_p+0x33/0x5c
Sep 23 21:57:29 localhost kernel:  [generic_permission+163/278] generic_permission+0xa3/0x116
Sep 23 21:57:29 localhost kernel:  [pg0+948315591/1070015488] soundcore_open+0x189/0x27e [soundcore]
Sep 23 21:57:29 localhost kernel:  [chrdev_open+328/364] chrdev_open+0x148/0x16c
Sep 23 21:57:29 localhost kernel:  [dentry_open+240/473] dentry_open+0xf0/0x1d9
Sep 23 21:57:29 localhost kernel:  [filp_open+65/73] filp_open+0x41/0x49
Sep 23 21:57:29 localhost kernel:  [get_unused_fd+40/189] get_unused_fd+0x28/0xbd
Sep 23 21:57:29 localhost kernel:  [sys_open+50/141] sys_open+0x32/0x8d
Sep 23 21:57:29 localhost kernel:  [sysenter_past_esp+82/117] sysenter_past_esp+0x52/0x75
Sep 23 21:57:29 localhost kernel: Code: c0 5b c3 8d 81 d8 01 00 00 e8 b9 01 65 45 e9 1a fb ff ff 8d 82 d8 01 00 00 e8 cd 01 65 45 e9 24 fb ff
ff 56 31 d2 53 8b 08 24 14 <8b> 74 04 0c 8b 5c 24 10 83 f9 01 76 18 0a b6 84 16 ae 01 00 00

---

