---
title: "Bluetooth  Does Not Find  Devices - Sony TZ31"
date: 2008-09-24
forum: Hardware
---

### Post by stuson on 2008-09-24
Hi All,  looking for a little  help  with  getting Bluetooth  up and working.

I have installed  the  bluez  utilities and  gnome-bluetooth

hcitoo dev  shows

Devices:
	hci0	00:1E:3D:E8:F3:D9

hcitool scan fails  to get any results

When  I  restart  it  the  syslog  output is shown  below,   it  shows that a  config file  main.conf  is missing,  I  have no  idea  what should be  in it.  IT is definately missing  from the  filesystem shown.  There are some other config files and I have tried basic stuff like  copying the hcid.conf to main.conf  but that  failed to parse.

Can  anyone  suggest why  the main.conf is missing  or how to  generate it please.

TIA.

Output  of demsg  for bluetooth  stuff 
==============================================
[   17.983582] Bluetooth: Core ver 2.13
[   17.984987] Bluetooth: HCI device and connection manager initialized
[   17.984996] Bluetooth: HCI socket layer initialized
[   18.337183] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   33.590880] Modules linked in: sonypi(+) ppdev acpi_cpufreq cpufreq_stats cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_ondemand freq_table pci_slot sbs container wmi sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport snd_hda_intel joydev snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy serio_raw arc4 ecb crypto_blkcipher psmouse uvcvideo snd_seq_oss compat_ioctl32 iwlagn btusb pcmcia iwlcore snd_seq_midi videodev sr_mod cdrom snd_rawmidi bluetooth v4l1_compat rfkill snd_seq_midi_event led_class snd_seq mac80211 yenta_socket rsrc_nonstatic pcmcia_core cfg80211 iTCO_wdt snd_timer snd_seq_device battery ac iTCO_vendor_support sony_laptop snd video output soundcore button snd_page_alloc shpchp pci_hotplug intel_agp agpgart evdev ext3 jbd mbcache usb_storage sg sd_mod crc_t10dif pata_acpi ata_piix libusual ata_generic libata scsi_mod ohci1394 ieee1394 uhci_hcd ehci_hcd usbcore sky2 dock thermal processor fan fbcon tileblit font bitblit softcursor uvesafb cn fuse
[   41.291533] Bluetooth: L2CAP ver 2.11
[   41.291548] Bluetooth: L2CAP socket layer initialized
[   41.406948] Bluetooth: RFCOMM socket layer initialized
[   41.408515] Bluetooth: RFCOMM TTY layer initialized
[   41.408531] Bluetooth: RFCOMM ver 1.10

Syslog output  during bluetooth restart
==============================================================

Sep 24 16:42:20 stewart-laptop hcid[9238]: Bluetooth HCI daemon
Sep 24 16:42:20 stewart-laptop hcid[9238]: Parsing /etc/bluetooth/main.conf failed: No such file or directory
Sep 24 16:42:20 stewart-laptop hcid[9238]: Unable to get on D-Bus

---

### Post by stuson on 2008-09-29
Bump!!

---

