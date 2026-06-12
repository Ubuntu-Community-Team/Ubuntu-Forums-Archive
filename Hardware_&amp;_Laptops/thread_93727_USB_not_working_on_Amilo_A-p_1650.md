---
title: "USB not working on Amilo A-p 1650"
date: 2005-11-22
forum: Hardware &amp; Laptops
---

### Post by Eproxus on 2005-11-22
Hi,

I'm recently got an FUJITSU Siemens Amilo A-p 1650. It seems that I cannot get USB working. Plugging in either an external USB harddrive, memory stick or even a mouse gives no visible results. Tail /var/log/messages shows nothing when plugging them in or out. The USB stick has this red light on it which should turn green but it does not and the mouse is as dead as unplugged.

dmesg | grep usb results in this output:
```
[4294680.545000] usbcore: registered new driver usbfs
[4294680.545000] usbcore: registered new driver hub
[4298765.367000] usb 3-3: new high speed USB device using ehci_hcd and address 2
[4298765.863000] usb-storage: device found at 2
[4298765.863000] usb-storage: waiting for device to settle before scanning
[4298765.863000] usbcore: registered new driver usb-storage
[4298846.581000] usb 3-3: USB disconnect, address 2
[4298846.581000] usb-storage: device scan complete
[4298846.581000] Modules linked in: usb_storage af_packet radeon drm rfcomm l2ca                                                                           p bluetooth powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_power                                                                           save cpufreq_ondemand cpufreq_conservative pcmcia video tc1100_wmi sony_acpi pcc                                                                           _acpi hotkey dev_acpi i2c_acpi_ec i2c_core button battery container ac pcspkr rt                                                                           c ohci1394 yenta_socket rsrc_nonstatic pcmcia_core ath_pci ath_rate_sample wlan                                                                            ath_hal snd_atiixp snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer sn                                                                           d soundcore snd_page_alloc shpchp pci_hotplug ati_agp agpgart dm_mod joydev tsde                                                                           v evdev sr_mod sbp2 scsi_mod ieee1394 psmouse mousedev parport_pc lp parport md                                                                            ext3 jbd thermal processor fan 8139too 8139cp mii ehci_hcd ohci_hcd usbcore ide_                                                                           cd cdrom ide_disk ide_generic atiixp ide_core unix vesafb capability commoncap v                                                                           ga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font                                                                            bitblit
[4298846.581000]  [<f8d2c27b>] storage_disconnect+0x50/0x6a [usb_storage]
[4298846.581000]  [<f88f009c>] usb_unbind_interface+0x36/0x65 [usbcore]
[4298846.581000]  [<f88f59cb>] usb_disable_device+0x77/0xe9 [usbcore]
[4298846.581000]  [<f88f1b77>] usb_disconnect+0x93/0xec [usbcore]
[4298846.581000]  [<f88f27c6>] hub_port_connect_change+0x57/0x2b2 [usbcore]
[4298846.581000]  [<f88f2c43>] hub_events+0x222/0x2c6 [usbcore]
[4298846.581000]  [<f88f2ce7>] hub_thread+0x0/0xe8 [usbcore]
[4298846.581000]  [<f88f2d03>] hub_thread+0x1c/0xe8 [usbcore]
[4298846.581000]  [<f88f2ce7>] hub_thread+0x0/0xe8 [usbcore]
```

Any suggestions on how to fix this?

Thanks in advance!

---

