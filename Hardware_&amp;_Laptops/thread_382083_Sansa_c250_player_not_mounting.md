---
title: "Sansa c250 player not mounting"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Keith_Beef on 2007-03-11
I just got a Sansa c250 MP3 player.

This is the third Sansa player I've had. The two others show up as external discs.

This one, though I tried putting the player into MSC mode as well as trying it on Auto mode, doesn't show up.

By this, I mean that a folder representing the filesystem doesn't appear on the desktop, and it doesn't appear in /media as other mplayers have done.

This device has 2GB of memory, and a Micro SD slot (currently empty).

tail /var/log/messages shows me that something happens when I plug it in:

```
Mar 11 17:24:22 localhost kernel: [17180666.364000] scsi6 : SCSI emulation for USB Mass Storage devices
Mar 11 17:24:33 localhost kernel: [17180676.976000] usb 3-1: reset high speed USB device using ehci_hcd and address 14
Mar 11 17:24:38 localhost kernel: [17180682.108000]  6:0:0:0: scsi: Device offlined - not ready after error recovery
Mar 11 17:24:38 localhost kernel: [17180682.108000] usb 3-1: USB disconnect, address 14
Mar 11 17:24:38 localhost kernel: [17180682.220000] usb 3-1: new high speed USB device using ehci_hcd and address 15
Mar 11 17:24:38 localhost kernel: [17180682.356000] scsi7 : SCSI emulation for USB Mass Storage devices
Mar 11 17:24:49 localhost kernel: [17180692.968000] usb 3-1: reset high speed USB device using ehci_hcd and address 15
Mar 11 17:24:54 localhost kernel: [17180698.100000]  7:0:0:0: scsi: Device offlined - not ready after error recovery
Mar 11 17:24:54 localhost kernel: [17180698.100000] usb 3-1: USB disconnect, address 15
Mar 11 17:24:54 localhost kernel: [17180698.212000] usb 3-1: new high speed USB device using ehci_hcd and address 16
Mar 11 17:24:54 localhost kernel: [17180698.348000] scsi8 : SCSI emulation for USB Mass Storage devices
Mar 11 17:25:05 localhost kernel: [17180708.960000] usb 3-1: reset high speed USB device using ehci_hcd and address 16
Mar 11 17:25:05 localhost kernel: [17180708.960000] usb 3-1: reset high speed USB device using ehci_hcd and address 16
Mar 11 17:25:10 localhost kernel: [17180714.092000]  8:0:0:0: scsi: Device offlined - not ready after error recovery
Mar 11 17:25:10 localhost kernel: [17180714.092000] usb 3-1: USB disconnect, address 16
Mar 11 17:25:10 localhost kernel: [17180714.204000] usb 3-1: new high speed USB device using ehci_hcd and address 17
Mar 11 17:25:10 localhost kernel: [17180714.340000] scsi9 : SCSI emulation for USB Mass Storage devices
Mar 11 17:25:21 localhost kernel: [17180724.952000] usb 3-1: reset high speed USB device using ehci_hcd and address 17
Mar 11 17:25:26 localhost kernel: [17180730.084000]  9:0:0:0: scsi: Device offlined - not ready after error recovery
Mar 11 17:25:26 localhost kernel: [17180730.084000] usb 3-1: USB disconnect, address 17
Mar 11 17:25:26 localhost kernel: [17180730.196000] usb 3-1: new high speed USB device using ehci_hcd and address 18
Mar 11 17:25:26 localhost kernel: [17180730.332000] scsi10 : SCSI emulation for USB Mass Storage devices
Mar 11 17:25:37 localhost kernel: [17180740.944000] usb 3-1: reset high speed USB device using ehci_hcd and address 18
Mar 11 17:25:42 localhost kernel: [17180746.076000]  10:0:0:0: scsi: Device offlined - not ready after error recovery
Mar 11 17:25:42 localhost kernel: [17180746.076000] usb 3-1: USB disconnect, address 18
Mar 11 17:25:42 localhost kernel: [17180746.188000] usb 3-1: new high speed USB device using ehci_hcd and address 19
Mar 11 17:25:42 localhost kernel: [17180746.324000] scsi11 : SCSI emulation for USB Mass Storage devices
Mar 11 17:25:53 localhost kernel: [17180756.936000] usb 3-1: reset high speed USB device using ehci_hcd and address 19
Mar 11 17:25:58 localhost kernel: [17180762.068000]  11:0:0:0: scsi: Device offlined - not ready after error recovery
Mar 11 17:25:58 localhost kernel: [17180762.068000] usb 3-1: USB disconnect, address 19
Mar 11 17:25:58 localhost kernel: [17180762.180000] usb 3-1: new high speed USB device using ehci_hcd and address 20
Mar 11 17:25:58 localhost kernel: [17180762.316000] scsi12 : SCSI emulation for USB Mass Storage devices
Mar 11 17:26:09 localhost kernel: [17180772.928000] usb 3-1: reset high speed USB device using ehci_hcd and address 20
Mar 11 17:26:11 localhost gconfd (root-8553): starting (version 2.14.0), pid 8553 user 'root'
Mar 11 17:26:11 localhost gconfd (root-8553): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source
at position 0
Mar 11 17:26:11 localhost gconfd (root-8553): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 11 17:26:11 localhost gconfd (root-8553): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 11 17:26:11 localhost gconfd (root-8553): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source
at position 3
Mar 11 17:26:11 localhost gconfd (root-8553): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 11 17:26:14 localhost kernel: [17180778.060000]  12:0:0:0: scsi: Device offlined - not ready after error recovery
Mar 11 17:26:14 localhost kernel: [17180778.060000] usb 3-1: USB disconnect, address 20
Mar 11 17:26:14 localhost kernel: [17180778.176000] usb 3-1: new high speed USB device using ehci_hcd and address 21
Mar 11 17:26:32 localhost kernel: [17180796.720000] usb 3-1: new high speed USB device using ehci_hcd and address 22
```

But it doesn't look good :(

---

### Post by Powder305 on 2007-03-11
Keith,

I know NOTHING about Ubuntu because I have had it installed on my kids systems for 1 day now. I have used Windoze my entire life. I did plug in my kids c250 (in order to charge it) and a window popped up which allowed me to browse it. The music folder was empty which is strange but I can browse it.

Do you want me to run any commands and give you results? Would that help you compare? Let me know...

Powder

---

### Post by Keith_Beef on 2007-03-17
Curiously, this device now mounts as an external drive when I plug it in in MSC mode.

I don't know why, since I didn't change anything.

I copied three albums' worth of MP3 tracks into the MUSIC directory of the device.

```

sheryl_crow
|-- sheryl_crow
|   |-- 01_maybe_angels.mp3
|   |-- 02_a_change_would_do_you_good.mp3
|   |-- 03_home.mp3
|   |-- 04_sweet_rosalyn.mp3
|   |-- 05_if_it_makes_you_happy.mp3
|   |-- 06_redemption_day.mp3
|   |-- 07_hard_to_make_a_stand.mp3
|   |-- 08_every_day_is_a_winding_road.mp3
|   |-- 09_love_is_a_good_thing.mp3
|   |-- 10_oh_marie.mp3
|   |-- 11_superstar.mp3
|   |-- 12_the_book.mp3
|   `-- 13_ordinary_morning.mp3
|-- the_globe_sessions
|   |-- 01_my_favorite_mistake.mp3
|   |-- 02_there_goes_the_neighborhood.mp3
|   |-- 03_riverwide.mp3
|   |-- 04_it_dont_hurt.mp3
|   |-- 05_maybe_thats_something.mp3
|   |-- 06_am_i_getting_through_part_i__ii.mp3
|   |-- 07_anything_but_down.mp3
|   |-- 08_the_difficult_kind.mp3
|   |-- 09_mississippi.mp3
|   |-- 10_members_only.mp3
|   `-- 11_crash_and_burn.mp3
`-- the_very_best_of_sheryl_crow
    |-- 01_all_i_wanna_do.mp3
    |-- 02_soak_up_the_sun.mp3
    |-- 03_my_favorite_mistake.mp3
    |-- 04_the_first_cut_is_the_deepest.mp3
    |-- 05_everyday_is_a_winding_road.mp3
    |-- 06_leaving_las_vegas.mp3
    |-- 07_strong_enough.mp3
    |-- 08_light_in_your_eyes.mp3
    |-- 09_if_it_makes_you_happy.mp3
    |-- 10_the_difficult_kind.mp3
    |-- 11_picture_kid_rock_featuring_sheryl_crow.mp3
    |-- 12_steve_mcqueen.mp3
    |-- 13_a_change_would_do_you_good.mp3
    |-- 14_home.mp3
    |-- 15_there_goes_the_neighborhood.mp3
    |-- 16_i_shall_believe.mp3
    `-- 17_the_first_cut_is_the_deepest_country_version_bonus_track.mp3

3 directories, 41 files

```

Strangely, the track name is not being interpreted correctly for some files.
Instead of displaying the track name from the ID3 tag, the device shows the filename for these:

```

sheryl_crow
|-- sheryl_crow
|   |-- 03_home.mp3
|   |-- 11_superstar.mp3
|-- the_globe_sessions
|   |-- 03_riverwide.mp3
|   |-- 09_mississippi.mp3
`-- the_very_best_of_sheryl_crow
    |-- 14_home.mp3

```

K.

---

