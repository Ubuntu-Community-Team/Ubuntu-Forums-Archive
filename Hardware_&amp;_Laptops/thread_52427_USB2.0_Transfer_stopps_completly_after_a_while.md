---
title: "USB2.0: Transfer stopps completly after a while"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by Donalbain on 2005-07-27
Hi!

I have a big issue with Hoary and USB2.0: 

When I connect my USB2.0 card reader, everything looks ok (usb-storage), but when I transfer a big amount of data, the transfer freezes after about 150 MB.

And the same happens with my external USB-harddrive: about 150Megs get transferred with USB-2.0-speed and then it stops completely until after a reboot.

With the internal USB-1.1 interface, everything is fine, but who wants to use an external hd with USB1.1?

USB2.0 is unusable that way.

I use a USB-2.0 pci card, my board only supports USB1.1.

dmesg says something like this:
----
 device sda1, logical block 346755
Buffer I/O error on device sda1, logical block 346756
Buffer I/O error on device sda1, logical block 346757
...
scsi2 (0:0): rejecting I/O to offline device
...
Buffer I/O error on device sda1, logical block 346795
Buffer I/O error on device sda1, logical block 346796
...
Buffer I/O error on device sda1, logical block 347370
scsi2 (0:0): rejecting I/O to device being removed
...
Buffer I/O error on device sda1, logical block 347314
scsi2 (0:0): rejecting I/O to device being removed
FAT: unable to read inode block for updating (i_pos 3513560)
...
Buffer I/O error on device sda1, logical block 219597
lost page write due to I/O error on sda1
scsi2 (0:0): rejecting I/O to dead device
FAT: Directory bread(block 219595) failed
...
scsi2 (0:0): rejecting I/O to dead device
FAT: Directory bread(block 219626) failed
hub 5-0:1.0: connect-debounce failed, port 1 disabled
Unable to handle kernel paging request at virtual address 054001a6
 printing eip:
e0ca2285
*pde = 00000000
Oops: 0000 [#1]
PREEMPT
Modules linked in: nls_cp437 vfat fat isofs nls_utf8 udf aes_i586 dm_crypt loop appletalk ax25 ipx vmnet parport_pc vmmon proc_intf cpufreq_powersave cpufreq_userspace cpufreq_ondemand freq_table nfsd exportfs lockd sunrpc video battery container button pcc_acpi sony_acpi ac ipv6 snd_bt87x tuner tvaudio bttv video_buf firmware_class i2c_algo_bit v4l2_common btcx_risc videodev sd_mod usblp tmscsim ehci_hcd uhci_hcd pci_hotplug snd_intel8x0 tsdev snd_ac97_codec snd_pcm snd_timer snd soundcore usbhid snd_page_alloc usb_storage ohci_hcd usbcore i2c_amd756 i2c_core nvidia_agp agpgart evdev md dm_mod capability commoncap rt2500 fglrx sg scsi_mod psmouse mousedev lp parport ide_cd cdrom reiserfs ext2 ext3 jbd mbcache ide_generic ide_disk amd74xx ide_core unix thermal processor fan fbcon font bitblit vesafb cfbcopyarea cfbimgblt cfbfillrect
CPU:    0
EIP:    0060:[<e0ca2285>]    Tainted: P      VLI
EFLAGS: 00010246   (2.6.10-5-k7)
EIP is at bus_reset+0x4f/0xd1 [usb_storage]
eax: 05400012   ebx: dd2a1400   ecx: dd9e9318   edx: cf8f8000
esi: fffffffb   edi: dd9e9300   ebp: cf8f9fb4   esp: cf8f9f0c
ds: 007b   es: 007b   ss: 0068
Process scsi_eh_2 (pid: 511, threadinfo=cf8f8000 task=d21a7600)
Stack: 00000003 00000001 cf8f8000 00000286 dd9e9300 e0ac2028 dd9e9300 00000246
       dd9e9300 00000000 00000000 cf8f9fb4 e0ac221f dd9e9300 c666c000 00000000
       cf8f8000 dd9e9300 c666c000 cf8f9fac cf8f9fb4 cf8f9fb4 e0ac2791 c666c000
Call Trace:
 [<e0ac2028>] scsi_try_bus_reset+0x57/0xea [scsi_mod]
 [<e0ac221f>] scsi_eh_bus_reset+0x7a/0x153 [scsi_mod]
 [<e0ac2791>] scsi_eh_ready_devs+0x63/0x93 [scsi_mod]
 [<e0ac2977>] scsi_unjam_host+0xce/0x202 [scsi_mod]
 [<c0114bad>] default_wake_function+0x0/0x12
 [<e0ac2b78>] scsi_error_handler+0xcd/0x169 [scsi_mod]
 [<e0ac2aab>] scsi_error_handler+0x0/0x169 [scsi_mod]
 [<c010127d>] kernel_thread_helper+0x5/0xb
Code: 21 e0 83 68 14 01 8b 40 08 a8 08 0f 85 92 00 00 00 ff 0b 0f 88 c2 03 00 00 be fb ff ff ff 8b 43 1c a9 00 00 20 00 75 14 8b 43 10 <8b> 80 94 01 00 00 80 78 04 01 74 33 be f0 ff ff ff ff 03 0f 8e
 <6>usb 3-1: new full speed USB device using uhci_hcd and address 2
---------------------------------------
I'm not sure if all messages appeared before I became too impatient and removed the cardreader. 

Does anyone know of these problems? Is it a hardware problem? Other devices like my printer work great with the USB-Adapter
Or is it Linux?

Donalbain

---

### Post by Donalbain on 2005-08-01
Reply to my own post for the archive:

It seems to be an Ubuntu-problem. Knoppix and SuSE 9.3 work perfectly. Also in SuSE the rt2500 is much more relyable. So I switched back to SuSE, but I will definitly check the next release of Ubuntu, too.

So long
Donalbain.

---

