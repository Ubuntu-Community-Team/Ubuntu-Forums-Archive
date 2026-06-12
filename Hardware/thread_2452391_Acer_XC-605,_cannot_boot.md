---
title: "Acer XC-605, cannot boot"
date: 2020-10-21
forum: Hardware
---

### Post by mathias-x on 2020-10-21
I have read several threads on this issue, but nothing helps me

BG: I 'inherited' an older XC605 with Win8 installed. I replaced the harddisk (as there may be a need to go back to the Win install, which I btw don't have a login to) when I return the server some day...

I can boot ubuntu-20 live/install disk and install ubuntu (server) on the (new) HD just fine

However when it comes to boot the server, I only get this

a) a beep

A few flickering cursor lines and then

Reboot and Select proper Boot Device
or Insert Boot Media in selected device and press a key



Details

System BIOS P11-A1

Authentication:
  System Boot State           Setup (greyed out)
  Secure Boot Mode State   Disabled (greyed out)
 Secure Boot                     [DISABLED]

Security
 Supervisor Password         Not installed (greyed out)
 User Password                  Not installed (greyed out)  

Boot
 Launch CSM                     [Always]
 Launch PXE OPROM          [Legacy]  (greyed out)
 Launch Storage OPROM    [Legacy]  (greyed out)
 Launch Video OPROM       [Legacy]  (greyed out)

Boot Priority order            
   1st Boot Device             [ubuntu]
   1ns Boot Device             [P1: HL-DT-ST-DVDRAM...]]
   3rd Boot Device             [Removable Devide]]
   4th Boot Device             [LAN]

...

Boot Menu                       [Enabled]
D2D Recovery                  [Enabled]
Quiet Boot                       [Enabled]


Without access to Windows (and no Windows install media) how
can I get past this?

The Ubuntu install disk (even though its name has live in the filename) that I burned does not seem to offer any live mode either

---

