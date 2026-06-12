---
title: "Ubuntu 9.10 not recognizing cd/dvd-rom drive."
date: 2010-03-17
forum: Hardware
---

### Post by 47db82 on 2010-03-17
I installed Ubuntu side by side with Windows a few days ago. Ubuntu/Nautilus is not recognizing/mounting my cd/dvd-rw drive. I've talked to some people on #ubuntu irc.chat to no avail. I've put in a music cd (which get a few spins from the drive). The live dvd I used to install Ubuntu, and a few other data cds did nothing in the drive, no spinning or anything. How can I get Ubuntu to recognize my drive?

Here's info from the terminal:
Mar 17 02:24:59 dbook82-laptop kernel: [ 2207.488117] djplay[2775] general protection ip:807c523 sp:bffb6b70 error:0 in djplay[8048000+d4000]
Mar 17 02:27:27 dbook82-laptop kernel: [ 2354.763506] i2c-adapter i2c-2: unable to read EDID block.
Mar 17 02:27:27 dbook82-laptop kernel: [ 2354.763512] i915 0000:00:02.0: HDMI Type A-1: no EDID data
Mar 17 02:27:27 dbook82-laptop kernel: [ 2354.768303] i2c-adapter i2c-2: unable to read EDID block.
Mar 17 02:27:27 dbook82-laptop kernel: [ 2354.768307] i915 0000:00:02.0: HDMI Type A-1: no EDID data
Mar 17 02:33:41 dbook82-laptop pulseaudio[1720]: ratelimit.c: 112 events suppressed
Mar 17 03:42:12 dbook82-laptop pulseaudio[1720]: ratelimit.c: 143 events suppressed
Mar 17 09:53:12 dbook82-laptop kernel: [29100.011164] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Mar 17 12:33:47 dbook82-laptop sudo: pam_sm_authenticate: Called
Mar 17 12:33:47 dbook82-laptop sudo: pam_sm_authenticate: username = [dbook82]

/dev/sr0:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
 HDIO_GET_IDENTITY failed: No message of desired type

/dev/sr0:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
 HDIO_GET_IDENTITY failed: No message of desired type
dbook82@dbook82-laptop:~$ dmesg | egrep -i dvd
[    6.592064] ata5.00: ATAPI: MATSHITADVD-RAM UJ862AS, 1.00, max UDMA/33
[    6.624462] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ862AS  1.00 PQ: 0 ANSI: 5
[    6.639494] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

[    6.639494] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.639593] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.639659] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    9.838902] type=1505 audit(1268790502.074:2): operation="profile_load" pid=412 name=/usr/share/gdm/guest-session/Xsession
[    9.843317] type=1505 audit(1268790502.076:4): operation="profile_load" pid=413 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.843918] type=1505 audit(1268790502.076:5): operation="profile_load" pid=413 name=/usr/lib/connman/scripts/dhclient-script
[    9.898438] type=1505 audit(1268790502.133:6): operation="profile_load" pid=414 name=/usr/bin/evince
[    9.915637] type=1505 audit(1268790502.148:7): operation="profile_load" pid=414 name=/usr/bin/evince-previewer
[    9.925877] type=1505 audit(1268790502.160:8): operation="profile_load" pid=414 name=/usr/bin/evince-thumbnailer
[    9.953990] type=1505 audit(1268790502.188:9): operation="profile_load" pid=416 name=/usr/lib/cups/backend/cups-pdf
[    9.955294] type=1505 audit(1268790502.188:10): operation="profile_load" pid=416 name=/usr/sbin/cupsd
[    9.969792] type=1505 audit(1268790502.204:11): operation="profile_load" pid=417 name=/usr/sbin/mysqld-akonadi
[   16.250877] type=1505 audit(1268804908.484:13): operation="profile_replace" pid=910 name=/usr/share/gdm/guest-session/Xsession
[   16.254494] type=1505 audit(1268804908.488:15): operation="profile_replace" pid=911 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   16.255105] type=1505 audit(1268804908.488:16): operation="profile_replace" pid=911 name=/usr/lib/connman/scripts/dhclient-script
[   16.262135] type=1505 audit(1268804908.496:17): operation="profile_replace" pid=912 name=/usr/bin/evince
[   16.280141] type=1505 audit(1268804908.516:18): operation="profile_replace" pid=912 name=/usr/bin/evince-previewer
[   16.290887] type=1505 audit(1268804908.524:19): operation="profile_replace" pid=912 name=/usr/bin/evince-thumbnailer
[   16.305791] type=1505 audit(1268804908.540:20): operation="profile_replace" pid=914 name=/usr/lib/cups/backend/cups-pdf
[   16.307095] type=1505 audit(1268804908.540:21): operation="profile_replace" pid=914 name=/usr/sbin/cupsd
[   16.311315] type=1505 audit(1268804908.544:22): operation="profile_replace" pid=915 name=/usr/sbin/mysqld-akonadi
[  240.564201]  [<c03c60e3>] sr_test_unit_ready+0x63/0xd0
[  240.564207]  [<c03c7071>] sr_media_change+0x61/0x160
[  240.564228]  [<c03c6341>] sr_block_media_changed+0x11/0x20
[  240.564274]  [<c03c64a8>] sr_block_open+0x58/0xa0
dbook82@dbook82-laptop:~$ /dev/sr0:
bash: /dev/sr0:: No such file or directory
dbook82@dbook82-laptop:~$  HDIO_DRIVE_CMD(identify) failed: Invalid exchange
bash: syntax error near unexpected token `identify'
dbook82@dbook82-laptop:~$  HDIO_GET_IDENTITY failed: No message of desired type
HDIO_GET_IDENTITY: command not found

And here is a screenshot from Nautilus:

---

### Post by 47db82 on 2010-03-17
UPDATE:

Running nautilus under sudo brings up a cdrom0 but also a mount error message. See attached image:

---

### Post by desnaike on 2010-03-17
I work on friends and relatives comp's and usually end up with their old comps 3-5 yrs old I use them for parts cd roms mostly I use them to rip audio cd's rather than use my comps burners on 10's of audio cd's at a time for the past 2 days an LG 32x and samsung cd master were giving me fits I tried everything as u seem to be doing nothing worked. Then I found a thread that said not all cd roms are supported as in printers,video cards, etc. I tried each cd rom as a single and it was the LG from an IBM box that was the problem the samsung was working great. Once I pulled it from the mix no problems. hope this helps.

---

