---
title: "kernel crash when trying to sync palm tx pda"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by benyau on 2006-12-10
Pressed the sync button on the Palm usb cable first and then the sync button in JPilot.

/var/log/message recorded:

Dec 10 20:47:43 desktop kernel: [17230832.640000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Dec 10 20:47:43 desktop kernel: [17230832.648000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Dec 10 20:47:43 desktop kernel: [17230832.648000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Dec 10 20:47:43 desktop kernel: [17230832.648000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Dec 10 20:47:43 desktop kernel: [17230832.652000] visor 2-3:1.0: Handspring Visor / Palm OS converter detected
Dec 10 20:47:43 desktop kernel: [17230832.652000] usb 2-3: Handspring Visor / Palm OS converter now attached to ttyUSB0
Dec 10 20:47:43 desktop kernel: [17230832.652000] usb 2-3: Handspring Visor / Palm OS converter now attached to ttyUSB1
Dec 10 20:47:43 desktop kernel: [17230832.652000] usbcore: registered new driver visor
Dec 10 20:47:43 desktop kernel: [17230832.652000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Dec 10 20:48:26 desktop kernel: [17230875.592000] usb 2-3: USB disconnect, address 6
Dec 10 20:48:26 desktop kernel: [17230875.592000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Dec 10 20:48:26 desktop kernel: [17230875.592000] c022450d
Dec 10 20:48:26 desktop kernel: [17230875.592000] Modules linked in: visor usbserial usblp vmnet vmmon binfmt_misc cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery asus_acpi ac ipt_TCPMSS xt_tcpmss xt_tcpudp iptable_filter ip_tables x_tables pppoe pppox ipv6 af_packet ppp_generic slhc sbp2 lp tsdev serio_raw analog snd_mpu401 snd_mpu401_uart snd_rawmidi snd_seq_device gameport bt878 floppy parport_pc parport evdev nvidia pcspkr snd_intel8x0 snd_ac97_codec snd_ac97_bus psmouse tuner bttv snd_pcm_oss snd_mixer_oss snd_pcm snd_timer video_buf ir_common 3c59x compat_ioctl32 i2c_algo_bit v4l2_common btcx_risc snd soundcore i2c_nforce2 mii tveeprom videodev snd_page_alloc nvidia_agp agpgart i2c_core shpchp pci_hotplug forcedeth ext3 jbd ohci1394 ieee1394 ide_generic ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan fbcon ti
Dec 10 20:48:26 desktop kernel: eblit font bitblit softcursor vesafb capability commoncap
Dec 10 20:48:26 desktop kernel: [17230875.592000] EIP:    0060:[check_tty_count+77/176]    Tainted: P      VLI
Dec 10 20:48:26 desktop kernel: [17230875.592000] EFLAGS: 00210246   (2.6.17-10-generic #2) 

Once this occurred, all USB devices stopped working.

The computer has a fresh install of Edgy and is up-to-date.  It is unlikely a hardware problem as all worked well when the computer had Dapper.

I had no luck with gnome-pilot on Edgy either.  Having gone through many threads here, at the end I removed gnome-pilot and gnome-pilot-conduits.

Appreciate any advice.



ASUS A7N8X (nVidia nForce2), AMD Athlon XP, 512Mb

---

### Post by wyatt8609 on 2006-12-13
I have the same problem....
I'm new to Unix OS...But like Ubuntu so much I deleated windows altogether!

Would like to get my palm TX workin tho,,,I just bought it about 2 months ago and wont to use it....

Let me know what you find out....Thanks!

---

### Post by benyau on 2006-12-14
no probs, I will keep you updated here.  

I have read through all threads related to "palm sync" and tried all stated "solutions".  If you have the time, it may be worth for you to try them as well.  It may work for you.  

FYI.  my last attempt at a solution was to build a custom kernel per Unbuntu wiki instructions.   I aborted the attempt at the end.  I do miss the relative ease of compiling a custom kernel under Redhat/Fedora Core.  

Anyway, I still think it is a kernel issue.  I will try to build the visor kernel module next.   If I cannot find a solution by next year, I will move back to Fedora Core.  I cannot live without my palm.

have fun.

---

### Post by benyau on 2006-12-14
I managed to crash again with the following output:

Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] usb 2-3: USB disconnect, address 84
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] ------------[ cut here ]------------
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] kernel BUG at kernel/workqueue.c:110!
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] invalid opcode: 0000 [#1]
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] SMP 
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] Modules linked in: visor usbserial vmnet vmmon binfmt_misc cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi sbs pcc_acpi i2c_ec hotkey dev_acpi container button battery asus_acpi ac ipt_TCPMSS xt_tcpmss xt_tcpudp iptable_filter ip_tables x_tables pppoe pppox ipv6 af_packet ppp_generic slhc sbp2 lp tsdev 3c59x bt878 tuner bttv nvidia video_buf ir_common compat_ioctl32 i2c_algo_bit v4l2_common btcx_risc mii evdev snd_mpu401 snd_mpu401_uart snd_rawmidi snd_seq_device analog gameport pcspkr serio_raw psmouse tveeprom videodev parport_pc parport floppy snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc forcedeth shpchp pci_hotplug i2c_nforce2 i2c_core nvidia_agp agpgart ext3 jbd ehci_hcd ohci_hcd ohci1394 ieee1394 usbcore ide_generic ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan fbcon tileblit
Dec 14 21:04:54 yau-desktop kernel: font bitblit softcursor vesafb capability commoncap
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] CPU:    0
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] EIP:    0060:[queue_work+104/128]    Tainted: P      VLI
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] EFLAGS: 00010212   (2.6.17-10-generic #2) 
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] EIP is at queue_work+0x68/0x80
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] eax: da8b8150   ebx: 00000000   ecx: dffee540   edx: da8b814c
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] esi: 00000000   edi: cfce9414   ebp: cfce9414   esp: dfb25e9c
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] ds: 007b   es: 007b   ss: 0068
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] Process khubd (pid: 1798, threadinfo=dfb24000 task=dfbc2050)
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] Stack: 00000001 cdf25fa0 e0ea0994 c030455b e08e7a68 cfce9400 cfce9400 e0e73500 
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]        e0e73528 e08e9994 cfce948c cfce9414 c0245e2b cfce9414 cfce9414 e0900880 
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]        c02460ec cfce9414 c0245657 cfce9414 ce582458 00000000 c02446c5 cfce9400 
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] Call Trace:
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]  <e0ea0994> usb_serial_disconnect+0x44/0xb0 [usbserial]  <e08e7a68> usb_disable_interface+0x28/0x40 [usbcore]
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]  <e08e9994> usb_unbind_interface+0x34/0x70 [usbcore]  <c0245e2b> __device_release_driver+0x5b/0xa0
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]  <c02460ec> device_release_driver+0x1c/0x30  <c0245657> bus_remove_device+0x77/0x90
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]  <c02446c5> device_del+0x35/0x70  <e08e7bc6> usb_disable_device+0x86/0xe0 [usbcore]
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]  <e08e3927> usb_disconnect+0x97/0xf0 [usbcore]  <e08e498a> hub_thread+0x27a/0xc80 [usbcore]
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]  <c0136180> autoremove_wake_function+0x0/0x50  <e08e4710> hub_thread+0x0/0xc80 [usbcore]
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000]  <c0101005> kernel_thread_helper+0x5/0x10 
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] Code: 3b 42 04 75 26 8b 01 f7 d0 8b 04 98 bb 01 00 00 00 e8 3d ff ff ff 89 d8 8b 1c 24 8b 74 24 04 83 c4 08 c3 8b 1d d0 e5 46 c0 eb d2 <0f> 0b 6e 00 1d 3a 2f c0 eb d0 8d b4 26 00 00 00 00 8d bc 27 00 
Dec 14 21:04:54 yau-desktop kernel: [17210211.488000] EIP: [queue_work+104/128] queue_work+0x68/0x80 SS:ESP 0068:dfb25e9c

---

### Post by eamann on 2006-12-14
Hi,

I too cannot sync my Zire 72 to Edgy.  More exactly, very rarely and for no apparent reason I do manage to sync but 99 times out of a hundred it does not work.

FYI, see the previous thread on "PalmTX and Dapper" and this link to bug reports:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39518](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39518)

Let's hope a definitive solution will be found!

Best wishes,

Eamann

---

### Post by benyau on 2006-12-15
Concur.

I came across that bug while reading the thread mentioned and got the impression it has been fixed in Edgy.

It is likely a different bug.  It may be similar to this one (ipaq.c, linux-usb-devel related) - [http://lkml.org/lkml/2006/6/2/126](http://lkml.org/lkml/2006/6/2/126)

cheers,
ben

---

### Post by benyau on 2006-12-15
eamman,
 what CPU and chip set your motherboard has?

ben

---

### Post by eamann on 2006-12-16
Ben,

I'm sorry, but I am not very literate in things informatic. My laptop has an Intel Pentium M 1600 MHz processor, but beyond that I cannot say more. If you tell where I can find the information I will gladly do so. I tried System / Administration / Device Manager but did not see any mention of chip sets.

Thank you for your interest!

All the best,

Eamann

---

### Post by benyau on 2006-12-16
With your information, Pentium M..., it seems this bug is not just for AMD chips or supporting chipset (Nvidia NForce2 for mine).  

I found this bug report:  [http://bugzilla.kernel.org/show_bug.cgi?id=7095](http://bugzilla.kernel.org/show_bug.cgi?id=7095)   It seems the stock kernel in Ubuntu Edgy has the same bug.

And I recompiled a new vanilla kernel (2.6.19.1) per Method #2 of [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)  but I have not throughoutly tested with Palm Tx yet.  I will post my attempts here.  

Meanwhile, my exit strategy is OpenSUSE.  I like their opensync effect.  You may want to check it out.

cheers,
Ben

---

### Post by benyau on 2006-12-17
FYI.  This is getting interesting.  

With my new kernel and new nvidia module, Jpilot can sync reliably every time with my sony TJ27 (on ttyUSB0).  Of course, my computer runs noticably faster.  

However, Syncing with Palm Tx still sucks.

---

### Post by eamann on 2006-12-17
> **benyau said:**
>  Meanwhile, my exit strategy is OpenSUSE.  I like their opensync effect.  You may want to check it out.

Ben,

I'm quite new to Linux. Am I right in thinking what you are saying is that you would install the Open SUSE distribution in place of Ubuntu? I have spent a lot (and I mean a lot!) of time sweating to set up Ubuntu to do about 80% of what I used do with Windows. I am reluctant at this stage to undertake such a radical step!

I have stopped using JP until such times that I can be sure to sync with it. Once a week I back up my Palm on Windows.

Good luck with your efforts to find a fix!

Eamann

---

### Post by benyau on 2006-12-18
It is only for my case and I have not decided yet.    If it comes to that, I will keep Ubuntu 6.10 in a dual boot arrangement with OpenSUSE or FC6.  So I can have my Palm Tx functional.  FYI.  I don't have any Windows on my PC.  

Ubuntu is an excellent distribution.  I have been distributing their free CDs at work.  I won't recommend anyone move away from it unless there is an absolute need.  

Ben

---

### Post by benyau on 2007-02-14
There may be problem with the current USB kernel subsystem for my hardware.  

I tried
- kernel 2.6.17 to 2.6.20 under Edgy
- Opensuse 10.2, Fedora Core 6, Dapper and Edgy
- Kpilot, gnome-pilot and Jpilot

My conclusion is Palm Tx is not compatible with Linux.

---

### Post by eamann on 2007-02-15
Hi!

As I said in an earlier post, I have spent hours and hours trying to get my Palm Zire 71 to sync (in my case using J-Pilot). In vain. Frustration.

Then yesterday I read on a site that opening J-Pilot as root could solve the problem. I tried it and it worked! I could not believe my eyes! I thought it was a fluke and tried a second time and a second time it worked!

It has worked again today, though sometimes only after a second or third try.

I hope that this will help some of you solve your problems!


Best wishes,

Eamann O Ruairc
Edit/Delete Message

---

