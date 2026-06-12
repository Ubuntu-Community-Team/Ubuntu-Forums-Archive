---
title: "HP Officejet G85 won't run on Gutsy"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by D-KICK on 2007-11-21
this printer was running fine on feisty.

config:
AMD X2 5200+
Asrock ALiveNF5-eSATA2+

in /var/log/syslog I found following messages:

[COLOR="red"]Nov 21 21:02:59 Petix2 OfficeJet_G85?serial=SGG11E21GZVL: INFO: open print channel failed; will retry in 30 seconds...
Nov 21 21:03:37 Petix2 OfficeJet_G85?serial=SGG11E21GZVL: INFO: open print channel failed; will retry in 30 seconds...
[/COLOR]

I already updated hplip to the newest version available.
hp-info outputs:

[COLOR="red"]
peter@Petix2:~$ hp-info

HP Linux Imaging and Printing System (ver. 2.7.10)
Device Information Utility ver. 3.4

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/OfficeJet_G85?serial=SGG11E21GZVL

hp:/usb/OfficeJet_G85?serial=SGG11E21GZVL

error: Device busy: hp:/usb/OfficeJet_G85?serial=SGG11E21GZVL
error: Error opening device (Device not found). Exiting.[/COLOR]

directly after plugin off and on the usb cable of the printer hp-info looks like this:

[COLOR="green"]peter@Petix2:~$ hp-info

HP Linux Imaging and Printing System (ver. 2.7.10)
Device Information Utility ver. 3.4

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/OfficeJet_G85?serial=SGG11E21GZVL

hp:/usb/OfficeJet_G85?serial=SGG11E21GZVL

Device Parameters (dynamic data):
  Parameter                     Value(s)
  ----------------------------  ----------------------------------------------------------
  agent1-ack                    False
  agent1-desc                   Black cartridge
  agent1-dvc                    0
  agent1-health                 0
  agent1-health-desc            Good/OK
  agent1-hp-ink                 False
  agent1-id                     0
  agent1-kind                   3
  agent1-known                  False
  agent1-level                  0
  agent1-level-trigger          0
  agent1-sku                    45 (51645A)
  agent1-type                   1
  agent1-virgin                 False
  agent2-ack                    False
  agent2-desc                   Tri-color cartridge
  agent2-dvc                    0
  agent2-health                 0
  agent2-health-desc            Good/OK
  agent2-hp-ink                 False
  agent2-id                     0
  agent2-kind                   3
  agent2-known                  False
  agent2-level                  0
  agent2-level-trigger          0
  agent2-sku                    78 (C6578DN/C6578AN)
  agent2-type                   2
  agent2-virgin                 False
  back-end                      hp
  cups-printer                  OfficeJet_G85,OfficeJet_G85_2
  cups-uri                      hp:/usb/OfficeJet_G85?serial=SGG11E21GZVL
  dev-file
  device-state                  1
  device-uri                    hp:/usb/OfficeJet_G85?serial=SGG11E21GZVL
  deviceid                      MFG:Hewlett-Packard;MDL:OfficeJet
                                G85;CMD:MLC,PCL,PML,SCL;CLASS:PRINTER;DESCRIPTION:Hewlett-
                                Packard OfficeJet G
                                Series;1284.3M:f7f,f7f;1284.4DL:4d,4e,1;SERN:SGG11E21GZVL;
                                VSTATUS:$HB0$NC0,ff,DN,IDLE,CUT,K3,C3,SM,NR,KP000,CP000;Ai
                                O:0;DW-PCL;
  duplexer                      0
  error-state                   0
  host
  in-tray1                      0
  in-tray2                      0
  is-hp                         True
  media-path                    1
  panel                         0
  panel-line1
  panel-line2
  photo-tray                    0
  port                          1
  r                             0
  revision                      255
  rg                            000
  rr                            000000
  rs                            000000000
  scan-uri                      hpaio:/usb/OfficeJet_G85?serial=SGG11E21GZVL
  serial                        SGG11E21GZVL
  status-code                   1000
  status-desc                   The printer is idle.
  supply-lid                    0
  top-lid                       1

Model Parameters (static data):
  Parameter                     Value(s)
  ----------------------------  ----------------------------------------------------------
  align-type                    1
  clean-type                    1
  color-cal-type                0
  copy-type                     0
  embedded-server-type          1
  fax-type                      0
  fw-download                   0
  icon                          OfficeJet_G85.png
  io-mfp-mode                   6
  io-mode                       6
  io-support                    6
  linefeed-cal-type             0
  model                         OfficeJet_G85
  model-ui                      HP Officejet g85
  model1                        Officejet G85
  panel-check-type              1
  pcard-type                    0
  plugin                        0
  plugin-library
  pq-diag-type                  0
  r-type                        0
  r0-agent1-kind                3
  r0-agent1-sku                 45 (51645A)
  r0-agent1-type                1
  r0-agent2-kind                3
  r0-agent2-sku                 78 (C6578DN/C6578AN)
  r0-agent2-type                2
  scan-style                    1
  scan-type                     1
  status-battery-check          0
  status-dynamic-counters       0
  status-type                   1
  support-released              1
  support-type                  2
  support-ver                   0.9.5
  tech-class                    DJ9xx
  tech-type                     2
  usb-pid                       0211
  usb-vid                       03f0

Status History (most recent first):
  Date/Time             Code   Status Description                        User      Job ID
  --------------------  -----  ----------------------------------------  --------  --------
  11/21/07 21:14:41     1000   The printer is idle.                      peter
  11/21/07 21:09:24     5021   Device is busy.                           peter
[/COLOR]

Does anybody has an idea what is going wrong?

Thanks for helping.

peter

---

### Post by Spuggie on 2008-06-06
Hi,

  Did you get anywhere with this?  I'm having problems with my OfficeJet G85 on Gutsy too.  If the PC has been on for a while, printing either won't happen at all (although it appears in the print queue), or it prints a few lines at a time then has a massive delay before saying there's an unknown error.  This repeats until the document is eventually printed.

  Alternatively, if I reboot, then anything that is in the queue gets printed perfectly as soon as the services are loaded.  Equally, printing within the first few minutes of logging in has never been a problem either.

  I've tried restarting the CUPS daemon, but that makes no difference.  Is there another service that needs restarting too?

---

### Post by doubtintom on 2008-06-20
Agh! I've got the same problem with a G55 (little brother to G85). Through some hours of hair tearing, giving up, and then offhandedly noticing a "coincidence" I discovered that in my case, at least, VirtualBox had the USB to my G55 as an attached device. That made the CUPS daemon believe the device was "busy". All I had to do was to uncheck the checkmark in VirtualBox's device tray, and as they say, voila! I'm ccanning again from Xane in my host Linux OS!

Of course there may be other sources to that response from the printer driver, but if you're not capturing the printer device in VirtualBox or some other VM, perhaps there is some other device or program that has a grip on your USB device.

I hope this helps someone!

keep da faith
Doubtin Tom

---

