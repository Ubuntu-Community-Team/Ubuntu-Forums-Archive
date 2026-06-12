---
title: "Problems with Acer Aspire 5515 w/ 8.10 &amp; 2.6.27-11-generic"
date: 2009-04-06
forum: Hardware
---

### Post by mr72 on 2009-04-06
OK, so I have done some searching and tried a million things but still nothing works. Looking for maybe some more specific direction rather than the shotgun approach of trying everything with my fingers crossed.

Problem #1 is it will not resume correctly either from hibernate or from suspend. I tried the i8042.reset solution in the /boot/grub/menu.lst and it does not fix the problem.

When coming back from hibernate, it just gets a black, blank screen after the ubuntu logo splash and thermometer and appears to be frozen.

When resuming from suspend, it will not detect the mouse (touchpad) or keyboard. So I get the login/resume dialog and cannot input to get it to resume.

Problem #2 has to do with the USB. I have a SonyEricsson w350 phone with a memory stick micro flash drive and it will not mount. When I connect it with USB, then it tries to install the phone as a mobile broadband adapter but does not mount the file system. This phone mounts fine on a different computer running Windows XP. I can, however, mount other USB flash devices with no problems including thumb drives and digital cameras (also Sony with memory stick). 

Problem #3 is on bootup, "..MP-BIOS bug: 8254 timer not connected to IO-APIC". Dunno if this is related to the other problems. Still researching that one.

Anyone have a suggestion for either of these problems? Thanks in advance.

---

### Post by mr72 on 2009-04-09
bump and more info ...

I tried the i8042.reset kernel option and it didn't help with my suspend/thaw problem.

I also tried "nohz=off hpet=disable noapic" kernel options and that gets rid of the MP-BIOS bug error, but does not change anything else.

The symptom on hibernate with the above kernel options is that it tries to wake up, but when I get the login screen it freezes before I can type any input (mouse cursor frozen, blinking input box cursor stops blinking). Looks like the box hangs. When I suspend and try to resume, then it just boots like it was shut down when I resume.

Here is the output of lspci:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

I think some of my other problems may be related to the USB device. I have also had a problem with saving files to a USB flash drive wherein the files are corrupt very frequently. I suspect this might be somehow related to my problem with accessign my phone from USB.

Any help is appreciated. This laptop is nearly useless to me for its intended purpose until I can get suspend and resume to work.

---

### Post by mr72 on 2009-04-10
Nobody knows how to help me with this? If I can't get suspend/resume to work, I am going to have to go back to Vista unfortunately.

---

### Post by mr72 on 2009-04-13
OK folks, I figure maybe someone else is going to post or search for this on this forum and get the same amount of help I did (zero), so I might as well post my solution.

Disabling the ATI proprietary graphics card driver for the Radeon Xpress 1200 card fixes the suspend/resume problem. I cannot tell any degradation or change in video performance.

As to the phone problem, if I plug it in and put it in "File Transfer" mode, and then reboot the computer while the phone is rebooting to file transfer mode, then the "PHONE CARD" memory stick mounts as expected. Unfortunately it won't mount while the machine is actually up and running. When I plug in the phone and select "File Transfer", I get the following in dmesg:

[  338.172039] usb 1-1: new full speed USB device using ohci_hcd and address 2
[  338.384880] usb 1-1: configuration #2 chosen from 1 choice
[  339.088224] cdc_acm 1-1:2.1: ttyACM0: USB ACM device
[  339.091651] usbcore: registered new interface driver cdc_acm
[  339.092372] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[  339.094599] BUG: unable to handle kernel NULL pointer dereference at 00000003
[  339.094607] IP: [<f8cf15bc>] :cdc_wdm:wdm_probe+0x13c/0x3c0
[  339.094615] *pde = 00000000 
[  339.094619] Oops: 0000 [#1] SMP 
[  339.094624] Modules linked in: cdc_wdm(+) cdc_acm ipv6 af_packet radeon drm binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev powernow_k8 cpufreq_powersave cpufreq_userspace cpufreq_conservative cpufreq_stats cpufreq_ondemand freq_table container pci_slot sbs sbshc iptable_filter ip_tables x_tables parport_pc lp parport joydev evdev video output battery arc4 ecb crypto_blkcipher ac snd_hda_intel serio_raw psmouse snd_pcm_oss snd_mixer_oss snd_pcm ath5k lbm_cw_mac80211 snd_seq_dummy lbm_cw_cfg80211 led_class snd_seq_oss wmi snd_seq_midi snd_rawmidi button snd_seq_midi_event snd_seq pcspkr snd_timer snd_seq_device k8temp snd soundcore i2c_piix4 snd_page_alloc i2c_core ati_agp shpchp pci_hotplug agpgart ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg pata_acpi ata_generic pata_atiixp ehci_hcd r8169 ohci_hcd ahci mii usbcore libata scsi_mod dock thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  339.094696] 
[  339.094700] Pid: 7649, comm: modprobe Not tainted (2.6.27-11-generic #1)
[  339.094703] EIP: 0060:[<f8cf15bc>] EFLAGS: 00010246 CPU: 0
[  339.094709] EIP is at wdm_probe+0x13c/0x3c0 [cdc_wdm]
[  339.094712] EAX: 00000000 EBX: 00000800 ECX: f8cf5480 EDX: f43a8000
[  339.094715] ESI: 00000000 EDI: f6a51f00 EBP: f4055de8 ESP: f4055dac
[  339.094718]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[  339.094722] Process modprobe (pid: 7649, ti=f4054000 task=f4014b60 task.ti=f4054000)
[  339.094724] Stack: c020129b c02009d8 f4055dcc c0200a85 f4055dc8 f43a8000 00000000 f4055de0 
[  339.094732]        fffffff4 0800ab24 f32ca85c f8cf3234 f43a8000 00000000 f43a801c f4055e14 
[  339.094739]        f8930597 f43a8094 f4055e00 c0201927 f8cf3200 f32ca800 f8cf32a0 f43a801c 
[  339.094746] Call Trace:
[  339.094749]  [<c020129b>] ? sysfs_addrm_finish+0x3b/0xf0
[  339.094758]  [<c02009d8>] ? sysfs_add_one+0x18/0x50
[  339.094763]  [<c0200a85>] ? sysfs_addrm_start+0x75/0xa0
[  339.094771]  [<f8930597>] ? usb_probe_interface+0xa7/0x140 [usbcore]
[  339.094792]  [<c0201927>] ? sysfs_create_link+0x17/0x20
[  339.094803]  [<c02c4c7e>] ? really_probe+0xee/0x190
[  339.094812]  [<f892f959>] ? usb_match_id+0x49/0x60 [usbcore]
[  339.094833]  [<c02c4d63>] ? driver_probe_device+0x43/0x60
[  339.094838]  [<c02c4df9>] ? __driver_attach+0x79/0x80
[  339.094845]  [<c02c44c3>] ? bus_for_each_dev+0x53/0x80
[  339.094852]  [<c02c4a9e>] ? driver_attach+0x1e/0x20
[  339.094856]  [<c02c4d80>] ? __driver_attach+0x0/0x80
[  339.094861]  [<c02c3e5f>] ? bus_add_driver+0x1cf/0x250
[  339.094870]  [<c02c4fce>] ? driver_register+0x6e/0x150
[  339.094880]  [<f893086c>] ? usb_register_driver+0x7c/0xf0 [usbcore]
[  339.094896]  [<c012a2be>] ? resched_task+0x1e/0x70
[  339.094905]  [<f88fa000>] ? wdm_init+0x0/0x1e [cdc_wdm]
[  339.094910]  [<f88fa01c>] ? wdm_init+0x1c/0x1e [cdc_wdm]
[  339.094915]  [<c0101120>] ? _stext+0x30/0x160
[  339.094919]  [<c012b58e>] ? try_to_wake_up+0xde/0x290
[  339.094926]  [<c014c734>] ? __blocking_notifier_call_chain+0x14/0x70
[  339.094935]  [<c015c378>] ? sys_init_module+0x88/0x1b0
[  339.094942]  [<c0103f7b>] ? sysenter_do_call+0x12/0x2f
[  339.094947]  =======================
[  339.094949] Code: 00 00 00 c7 87 9c 00 00 00 50 1b cf f8 66 89 47 38 8d 87 94 00 00 00 89 87 94 00 00 00 89 87 98 00 00 00 8b 02 8b 40 0c 89 45 dc <0f> b6 40 03 83 e0 03 83 f8 03 74 38 c7 45 e4 ea ff ff ff 89 f8 
[  339.094982] EIP: [<f8cf15bc>] wdm_probe+0x13c/0x3c0 [cdc_wdm] SS:ESP 0068:f4055dac
[  339.094990] ---[ end trace 768e00831eb5f6e3 ]---
[  358.240001] usb 1-1: USB disconnect, address 2

So this doesn't look good.

---

### Post by dpena on 2009-04-17
I have similar errors when I connect a Sonyericsson Mobile Phone (W380i) using the USB data cable, disabling all the USB devices, and freezing 'lsusb' commands in a terminal.

I think there is something wrong with the modules:
/lib/modules/2.6.27-14-generic/kernel/drivers/usb/class/cdc-wdm.ko
/lib/modules/2.6.27-14-generic/kernel/drivers/usb/class/cdc-acm.ko

I have renamed them to 'cdc-wdm.ko.NO' and 'cdc-acm.ko.NO' and rebooted. Now I can use the phone as a USB storage.

---

### Post by ringoshu on 2009-05-09
Wow finally I 'm closer to getting it to work -___-; Thanks a lot :) It now mounts everytime, only problem is that it stops working shortly afterwards :( I small photo of like 120kb may copy but after that other file transfers stall and I can't browse the folders. Oh well...  should consider getting a card reader. I'm tired of all this kernel problems regarding the phone through usb AND bluetooth as well -sighs-

---

