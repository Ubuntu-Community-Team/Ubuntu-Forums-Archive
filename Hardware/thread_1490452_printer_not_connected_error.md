---
title: "printer not connected error"
date: 2010-05-22
forum: Hardware
---

### Post by chubbtech on 2010-05-22
Hi, I'm having issues printing PRF files on my HP laserjet P1006.  I'm still with Hardy Heron and never had that prob before.  I tried updating adobe reader and couldn't get the .bin file to execute.  Then I realised I first got that issue trying to print remotely from my laptop.  So I updated HPLIP and now nothing prints at all... still get that "printer may not be connected" message.
here's an output suggested on hplip help page
 tail -f /var/log/messages
May 22 09:29:57 pcfrancois kernel: [  352.134873] usb 7-6: USB disconnect, address 5
May 22 09:30:03 pcfrancois kernel: [  358.220806] usb 7-6: new high speed USB device using ehci_hcd and address 6
May 22 09:30:03 pcfrancois kernel: [  358.373050] usb 7-6: configuration #1 chosen from 1 choice
May 22 09:30:03 pcfrancois logger: loading hp_laserjet_p1006 firmware 007 006
May 22 09:30:03 pcfrancois kernel: [  358.376072] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3E17
May 22 09:30:07 pcfrancois kernel: [  361.733804] usblp0: removed
May 22 09:30:44 pcfrancois kernel: [  398.806617] audit(1274535044.369:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=13332 profile="/usr/sbin/cupsd" namespace="default"
May 22 09:30:44 pcfrancois foo2xqx-wrapper: foo2xqx-wrapper -r1200x600 -p1 -s7 -m1 -d1 -n1
May 22 09:30:48 pcfrancois foo2xqx-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
May 22 09:30:48 pcfrancois foo2xqx-wrapper: foo2xqx -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7  -u 177x84 -l 177x84       
May 22 09:44:52 pcfrancois -- MARK --
May 22 09:45:21 pcfrancois kernel: [ 1274.380198] audit(1274535921.105:5): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=29339 profile="/usr/sbin/cupsd" namespace="default"
May 22 09:45:21 pcfrancois foo2xqx-wrapper: foo2xqx-wrapper -r1200x600 -p1 -s7 -m1 -d1 -n1
May 22 09:45:25 pcfrancois foo2xqx-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
May 22 09:45:25 pcfrancois foo2xqx-wrapper: foo2xqx -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7  -u 177x84 -l 177x84       

looks like permission issue but don't know where to fix it

thx for the help

---

### Post by arrange on 2010-05-22
Try temporarily disabling the *apparmor* profile for *cups*
```
sudo aa-complain cupsd
```and test the printer again.

---

### Post by chubbtech on 2010-05-22
tried complain mode - no change

---

### Post by chubbtech on 2010-05-22
uninstalled former hplip version then reinstalled new version 3.10.5 and still no printing on either HP LJ P1006 or HP DJ F4400.  scanning works though.

here's what's on my CUPs page

**/usr/lib/cups/backend/hp failed**

---

### Post by chubbtech on 2010-05-22
:guitar:
Finally reverted to hplip included in synaptic, reinstalled both printers and got printing back.
Tried printing pdfs with ghostview and evince worked perfectly, tried Adobe again no printing...until I looked up printing options were set to landscape...for whatever reason landscape printing doesn't work.  Landscape option will print in evince and ghostview but will output in portrait.  Guess that solves the problem but the bug remains:confused:

---

### Post by thanasis57 on 2010-07-07
Also had the same problem with a USB HP-LaserJet-1300 printer on a WinXP/Ubuntu 10.04 dual-boot system. Although it worked under Windows, under Ubuntu it showed up as "not connected" after every update.

After the last one I tried removing-reinstalling hplip and hplip-gui, and also deleting-reinstalling the printer through System-Administation-Printing. No go!

My solution:
-opened Firefox and accessed CUPS through [http://localhost:631](http://localhost:631)
-In "Administration" (root privileges) I chose "Add Printer" and selected the HP-LaserJet-1300 _**NOT**_ using HPLIP.

Worked right away! Doing the same and choosing the HPLIP printer resulted to a printer that did not work.

My diagnosis? (for whatever it's worth):
The problem is with HPLIP

---

