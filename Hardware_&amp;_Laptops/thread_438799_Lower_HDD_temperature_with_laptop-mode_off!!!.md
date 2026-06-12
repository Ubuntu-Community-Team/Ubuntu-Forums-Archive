---
title: "Lower HDD temperature with laptop-mode off!!!"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by kilou on 2007-05-10
Hi,

I use an MSI S260 laptop with a Hitachi 7k60 60Gb HDD which runs at 7200rpm. I've enabled laptop-mode when the laptop is on battery power however I never spin down the disk. When on AC laptop mode is off and the HDD temperature increases slowly and rarely go past 40°C. When on battery and laptop mode is on, the HDD temperature can go as high as 47°C. Both these temperature are in non stressfull condition for the disk, just browsing the web for instance. 

The only parameter I can see that would make a difference is the harddrive power management setting. I use the following settings in laptop-mode.conf:

# Should laptop mode tools control the hard drive power management settings?
CONTROL_HD_POWERMGMT=1

# Power management for HD (hdparm -B values)
BATT_HD_POWERMGMT=128
LM_AC_HD_POWERMGMT=255
NOLM_AC_HD_POWERMGMT=255

As you can see I use 128 on battery and no power management (255) on AC. Is it possible that power management of harddrive causes the drive to run at higher temperature??????

---

### Post by jjordan on 2007-05-10
Shot in the dark here:

The discharging battery creates heat warming the interior of the laptop thereby causing the HD temperature to increase.  My laptop runs much warmer, to the touch, on batteries than AC (when the battery is not charging).

-j

---

### Post by kilou on 2007-05-10
Oh OK....but a charging battery while on AC should produce as much heat, if not probably more than a discharging battery no? My battery was charging when seing a lower HDD temp...

---

