---
title: "External USB Disks Fail to Mount"
date: 2012-07-06
forum: Hardware
---

### Post by ienne on 2012-07-06
Hello!

I have recently upgraded a Zotac H55-ITX WiFi from 10.04 LTS to 12.04 LTS by reinstalling everything afresh. The original system worked perfectly fine.

I use five external WD USB drives, all of the Elements series and between 1.5TB and 2.5TB size.

I am having all sorts of problems with the USB/auto-mount process: sometimes they work, sometimes they don't, sometimes I can read the content, sometimes I cannot but I can read the directories, sometimes rebooting helps seeing more of them, sometimes it makes no difference. It is a bit crazy, as there appear to be no determinism at all.

I have run "sudo lspci | grep USB" and get

00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.1 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.2 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.1 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.2 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)

If I disconnect one of the disks (per chance working) and reconnect it, here is what I read in syslog (and the disk does not mount):

Jul  6 11:44:04 NASvideo kernel: [ 2206.043665] usb 1-2: USB disconnect, device number 2
Jul  6 11:44:04 NASvideo ntfs-3g[2752]: Unmounting /dev/sdb1 (backup)
Jul  6 11:44:16 NASvideo kernel: [ 2217.987787] usb 1-1: new high-speed USB device number 13 using ehci_hcd
Jul  6 11:44:21 NASvideo kernel: [ 2223.125654] usb 1-1: unable to read config index 0 descriptor/start: -110
Jul  6 11:44:21 NASvideo kernel: [ 2223.125660] usb 1-1: chopping to 0 config(s)
Jul  6 11:44:31 NASvideo kernel: [ 2233.122126] usb 1-1: string descriptor 0 read error: -110
Jul  6 11:44:31 NASvideo kernel: [ 2233.122356] usb 1-1: no configuration chosen from 0 choices
Jul  6 11:44:31 NASvideo mtp-probe: checking bus 1, device 13: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1"
Jul  6 11:44:31 NASvideo mtp-probe: bus: 1, device: 13 was not an MTP device

After some other disconnect/connect attempts I also read

Jul  6 11:49:48 NASvideo kernel: [ 2549.686303] hub 1-4:1.0: hub_port_status failed (err = -110)
Jul  6 11:49:53 NASvideo kernel: [ 2554.732440] hub 1-4:1.0: hub_port_status failed (err = -110)
Jul  6 11:49:58 NASvideo kernel: [ 2559.778502] hub 1-4:1.0: hub_port_status failed (err = -110)
Jul  6 11:50:03 NASvideo kernel: [ 2564.824623] hub 1-4:1.0: hub_port_status failed (err = -110)
Jul  6 11:50:08 NASvideo kernel: [ 2569.870765] hub 1-4:1.0: hub_port_status failed (err = -110)

The syslog seems full of error messages about the USB; here are some more

I know nothing of these issues. Can anyone help? For the moment I think I will revert to the 10.04 LTS installation which worked like a charm.

Thanks,

p.

---

