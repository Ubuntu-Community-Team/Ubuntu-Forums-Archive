---
title: "FSC Amilo V3205 potential hdd problem and solution"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by pbvascon on 2007-10-24
This is just a tip for owners of this laptop model that might increase the lifetime of the harddrive under ubuntu.

I bought a Fujitsu Siemens Amilo Pro V3205 to run Linux and installed Ubuntu 7.10 (gusty) on it last weekend. My model has a 120Gb SATA drive which I think is made by Seagate (identified as ST9120822AS).

I came across some posts discussing potential damage to hdds done by improper kernel behaviour  where the power is cut off before issueing the drive to spindown. This causes an "emergency park" that mechanically stresses the drive more than a correct shutdown. You can check the total number of emergency parks done by the drive using the smartctl tool:

smartctl --attributes --device=ata /dev/sda

The output on my machine is:

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   109   098   006    Pre-fail  Always       -       21485472
  3 Spin_Up_Time            0x0003   100   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       244
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       683758
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       16
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       125
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   053   042   045    Old_age   Always   In_the_past 206950039599
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       74
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1701
.. etc.

Power-Off_Retrat_Count is the number of emergency parks (74) which is quite high for a new machine. I did some tests and concluded that *every* shutdown or reboot was increasing this counter by one (a lot of reboots experimenting with suspend/resume)! 

I could also hear a faint whining sound as the power was cut from the drive still spining, which is not a good sign.

This bug was should not happen on the gusty kernel, and it turns out that
the factory BIOS settings are to blame. Setting the ATA mode from "Enhanced" to "Compatible" solved the problem, i.e. I no longer get the increasing count or the whining sound.
  
Hope this tip is useful to other people

Pedro

---

### Post by igel on 2007-11-05
I believe it is a normal behaveour on latops. I see the same on 3 different IBM machines and one HP. I.e. - restart is always hard in laptops.

---

