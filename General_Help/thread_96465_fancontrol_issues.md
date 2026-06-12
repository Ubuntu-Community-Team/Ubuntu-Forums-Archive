---
title: "fancontrol issues"
date: 2005-11-28
forum: General Help
---

### Post by crag277 on 2005-11-28
I was fonally able to get lm_sensors to configure properly and load all the necessary drivers, but I am still having issues with the fancontrol script.  First of all, my chip, the SMSC47xxx reports inverted pwm values, 255 = 0rpm and 0 = max rpm.  Here is my output from 'sensors'.

smsc47m1-isa-0800
Adapter: ISA adapter
fan1:        0 RPM  (min = 5120 RPM, div = 1)
fan2:        0 RPM  (min = 2560 RPM, div = 2)

eeprom-i2c-0-52
Adapter: SMBus I801 adapter at 0500
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

eeprom-i2c-0-50
Adapter: SMBus I801 adapter at 0500
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

So to configure fancontrol, all that should be done is run the pwmconfig script.  However when I do that it detects the fans, but is unable to restart them, probably because of the inverted value issue.  Here is what pwmconfig tells me:

This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following PWM controls:
   9191-0800/pwm1
   9191-0800/pwm2

Found the following fan sensors:
   9191-0800/fan1_input     current speed: 6301 RPM
   9191-0800/fan2_input     current speed: 5522 RPM

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue:

Testing pwm control 9191-0800/pwm1 ...
  9191-0800/fan1_input ... speed was 6301 now 0
    It appears that fan 9191-0800/fan1_input
    is controlled by pwm 9191-0800/pwm1
    Fan 9191-0800/fan1_input has not returned to speed, please investigate!
  9191-0800/fan2_input ... speed was 5522 now 0
    It appears that fan 9191-0800/fan2_input
    is controlled by pwm 9191-0800/pwm1
    Fan 9191-0800/fan2_input has not returned to speed, please investigate!

Testing pwm control 9191-0800/pwm2 ...
  9191-0800/fan1_input ... speed was 6301 now 0
    It appears that fan 9191-0800/fan1_input
    is controlled by pwm 9191-0800/pwm2
    Fan 9191-0800/fan1_input has not returned to speed, please investigate!
  9191-0800/fan2_input ... speed was 5522 now 0
    It appears that fan 9191-0800/fan2_input
    is controlled by pwm 9191-0800/pwm2
    Fan 9191-0800/fan2_input has not returned to speed, please investigate!

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? y
/usr/sbin/pwmconfig: There are no temperature-capable sensor modules installed

Sorry for the long post, but does anyone have any ideas?  Temperature sensors aren't a big deal, I just want to turn the fans down to a rasonable level so my computer doesn't sound like a vacuum cleaner.

---

