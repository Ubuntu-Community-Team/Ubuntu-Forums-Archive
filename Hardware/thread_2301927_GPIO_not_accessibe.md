---
title: "GPIO not accessibe"
date: 2015-11-06
forum: Hardware
---

### Post by Vinayaka_Negalur on 2015-11-06
Hi there,

I have the hardware to which the signal pulse for generator is connected. My hardware expert tells me that the connections are established correctly at hardware level.
My requirement is to read the pulse value regularly from the GPIO to which the pin is connected.

I have following issues with this.
1. Me and the HW expert do not know which GPIO pin to read.
2. We do not know if the basic GPIO configuration is already done by BSP.
3. Do we need a hardware driver to read the pin value and update in GPIO if BSP is not doing it?
4. How do I know which all GPIOs are already configured?

the below command just shows few GPIOs as available, GPIO2 is listed after it was exported.
```
bash-4.3# pwd
/sys/class/gpio
bash-4.3# echo 2 > export
bash-4.3# cat  /sys/kernel/debug/gpio  
GPIOs 0-255, platform/6000d000.gpio, tegra-gpio:
 gpio-2   (sysfs               ) in  lo    
 gpio-65  (max16989            ) out lo    
 gpio-88  (en-vdd-sdcard1      ) out hi    
 gpio-89  (en-vdd-sdcard3      ) out lo    
 gpio-188 (temp_alert          ) in  lo    
 gpio-200 (extcon:extcon@1     ) in  lo    
 gpio-225 (hdmi2.0_hpd         ) in  lo    

GPIOs 1016-1023, platform/max77620-gpio.0, max77620-gpio, can sleep:
 gpio-1016 (extcon:extcon@1     ) in  lo 

```

---

### Post by Vinayaka_Negalur on 2015-11-09
Hello, anyone??

---

