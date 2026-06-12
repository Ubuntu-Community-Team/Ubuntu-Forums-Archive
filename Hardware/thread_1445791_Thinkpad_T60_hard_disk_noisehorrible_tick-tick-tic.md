---
title: "Thinkpad T60 hard disk noise:horrible tick-tick-tick sound"
date: 2010-04-03
forum: Hardware
---

### Post by perdubug on 2010-04-03
I am getting sick of this constant tick-tick-tick sound from the laptop. The following is my system env and what I did for this tick sound.
1. OS
      Ubuntu 9.10(2.6.31-20-generic)

2. Hard Disk:
      Model Family:     Fujitsu MHV series
      Device Model:     FUJITSU MHV2100BH PL      
      Firmware Version: 0084002A
      User Capacity:    100,030,242,816 bytes
      Device is:        In smartctl database [for details use: -P show]
      ATA Version is:   7
      ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
      SMART support is: Available - device has SMART capability.
      SMART support is: Enabled

3. Load_Cycle_Count
      I haven't that famous 'Load_Cycle_Count increased very fast' issue. I mean,this number in my T60 is fine after apply a solution I got from [http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046).

      193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       42639

4. BIOS
      I disabled some settings that may relate to this tick noise in BIOS,like turn off CPU power saving in in BIOS.

5. Other change I did:
   In /etc/default/grub,I put max_cstate as option for kernel - **GRUB_CMDLINE_LINUX="processor.max_cstate=2 acpi_osi="Linux""**

Any ideas?

---

### Post by perdubug on 2010-04-03
An interesting thing - I powered off my T60 and disconnected AC charger. Then powered on again, the tick noise disappeared. I connected AC charger again, still no tick noise. I powered on with AC charger connected,the tick noise back again!?

---

