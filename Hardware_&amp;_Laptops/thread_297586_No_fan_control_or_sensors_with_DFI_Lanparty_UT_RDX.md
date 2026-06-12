---
title: "No fan control or sensors with DFI Lanparty UT RDX200"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by jsteve54302 on 2006-11-11
I have a DFI Lanparty UT RDX200 mobo, and cannot get the fans to spin down, even by manually editing /etc/fancontrol.  This is very annoying because my CPU fan is very loud, and the case and PSU fans keep it below 60 degrees Centigrade (seems default BIOS setting for fan full-on on this mobo, but BIOS doesn't seem to actually change fan speeds) even at very high CPU usage...  The pwmconfig utility mentions something about needing testers for my chipset, but when I cut/paste the link it gives, the website I get doesn't seem to have any info on how to become a tester, just general sensor/fancontrol stuff.  I've even checked the temps by rebooting and looking at the System Health in the BIOS (lm-sensors doesn't work either :( )and they're never over 50-55 CPU, 25-30 on NB/SB chipsets...  This is really getting on my nerves, as the only place I can put my computer is my bedroom, and I leave my computer running at night for SETI BOINC ](*,) ...  No, I'm not willing to stop running BOINC...
Has anyone managed to get the sensors/fancontrol system working on this mobo?  If so, how?
And what info/console output can i post to help?

Sys:  [INDENT]
DFI LandParty UT RDX200
Onboard Sound, LAN
AMD Athlon 64 X2 4800+
4GB Ultra Dual Channel PC3200(400Mhz)
ATI X1900 512MB Crossfire Edition (Primary PCIE:0:0:0)
ATI X1900 512MB Crossfire Ready (Secondary PCIE:1:0:0)
Dual 250GB SATA300 HD, No RAID (xp choked on it)
PSU 650W 19A (each) Dual Rail +12V
[/INDENT]OS (Dual Boot):[INDENT]
Xubuntu 6.10 (Edgy) plus full Gnome Session linux-generic-2.6.17-10 kernel
xp home SP2(for my scanner... gotta replace that :))
[/INDENT]

---

### Post by jsteve54302 on 2006-11-27
OK, it's safe to igore this now :)

1:   It wasn't my CPU fan, it was ATI X1800 CrossFire fan (which never spun _up_ in xp)
2:   It doesn't matter anyway, as i tired of hard-resetting 3-4 times every boot/reboot when the system froze during POST, so i'm getting a new mobo (yes, it's gotta be the mobo, every other component has been swapped out trying to fix it :) )

Anyway, don't bother, it's fixed...

---

