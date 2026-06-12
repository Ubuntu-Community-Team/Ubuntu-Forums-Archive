---
title: "dmesg getting flooded"
date: 2021-11-26
forum: Hardware
---

### Post by tagsense on 2021-11-26
Greetings, 
i am running Ubuntu 20.04.3 on a Dell latitude machine with 5.4.0-90 kernel and gnome desktop environment. 
one of the things I have noticed is that the machine freezes up every 1.5 - 2.0 days. I have run complete hardware tests. as per those tests, there are no issues.  when I run dmesg -wH, I see it is getting flooded with the following messages. as you can see from the timestamps, these messages are extremely frequent. What do these messages mean and how to stop them? Kindly let me know. Thank you!

```
[  +0.000083] [drm:gen9_set_dc_state [i915]] Setting DC state from 00 to 02
[  +0.025070] [drm:intel_power_well_enable [i915]] enabling DC off
[  +0.000098] [drm:gen9_set_dc_state [i915]] Setting DC state from 02 to 00
[  +0.003005] [drm:intel_power_well_disable [i915]] disabling DC off
[  +0.000109] [drm:skl_enable_dc6 [i915]] Enabling DC6
[  +0.000099] [drm:gen9_set_dc_state [i915]] Setting DC state from 00 to 02
[  +0.002936] [drm:intel_power_well_enable [i915]] enabling DC off
[  +0.000104] [drm:gen9_set_dc_state [i915]] Setting DC state from 02 to 00
[  +0.000473] [drm:drm_mode_addfb2 [drm]] [FB:87]
[  +0.000801] [drm:intel_power_well_disable [i915]] disabling DC off
[  +0.000101] [drm:skl_enable_dc6 [i915]] Enabling DC6
[  +0.000092] [drm:gen9_set_dc_state [i915]] Setting DC state from 00 to 02
[  +0.024612] [drm:intel_power_well_enable [i915]] enabling DC off
[  +0.000100] [drm:gen9_set_dc_state [i915]] Setting DC state from 02 to 00
[  +0.003012] [drm:intel_power_well_disable [i915]] disabling DC off
[  +0.000129] [drm:skl_enable_dc6 [i915]] Enabling DC6
[  +0.000092] [drm:gen9_set_dc_state [i915]] Setting DC state from 00 to 02
[  +0.001088] [drm:intel_power_well_enable [i915]] enabling DC off
[  +0.000099] [drm:gen9_set_dc_state [i915]] Setting DC state from 02 to 00
[  +0.001933] [drm:intel_power_well_disable [i915]] disabling DC off
[  +0.000098] [drm:skl_enable_dc6 [i915]] Enabling DC6
[  +0.000091] [drm:gen9_set_dc_state [i915]] Setting DC state from 00 to 02
[  +0.000315] [drm:intel_power_well_enable [i915]] enabling DC off
[  +0.000104] [drm:gen9_set_dc_state [i915]] Setting DC state from 02 to 00
[  +0.000306] [drm:drm_mode_addfb2 [drm]] [FB:113]
[  +0.000709] [drm:intel_power_well_disable [i915]] disabling DC off
[  +0.000119] [drm:skl_enable_dc6 [i915]] Enabling DC6
[  +0.000116] [drm:gen9_set_dc_state [i915]] Setting DC state from 00 to 02
[  +0.015644] [drm:intel_power_well_enable [i915]] enabling DC off
[  +0.000105] [drm:gen9_set_dc_state [i915]] Setting DC state from 02 to 00
[  +0.000736] [drm:drm_mode_addfb2 [drm]] [FB:87]
[  +0.000784] [drm:intel_power_well_disable [i915]] disabling DC off
[  +0.000104] [drm:skl_enable_dc6 [i915]] Enabling DC6
[  +0.000094] [drm:gen9_set_dc_state [i915]] Setting DC state from 00 to 02
```

---

### Post by yancek on 2021-11-26
The link below has a response to a similar question so you might take a look at it to see if it helps.  It appears to be related to the intel GPU.  Also, have you done online searches by just putting one or more of the error messages in your browser search engine?  

 [https://askubuntu.com/questions/1226433/drmgen9-set-dc-state-i915-setting-dc-state-from-02-to-00-spams-my-dmesg](https://askubuntu.com/questions/1226433/drmgen9-set-dc-state-i915-setting-dc-state-from-02-to-00-spams-my-dmesg)

---

### Post by tagsense on 2021-11-26
> **yancek said:**
> The link below has a response to a similar question so you might take a look at it to see if it helps.  It appears to be related to the intel GPU.  Also, have you done online searches by just putting one or more of the error messages in your browser search engine?  

 [https://askubuntu.com/questions/1226433/drmgen9-set-dc-state-i915-setting-dc-state-from-02-to-00-spams-my-dmesg](https://askubuntu.com/questions/1226433/drmgen9-set-dc-state-i915-setting-dc-state-from-02-to-00-spams-my-dmesg)


Yes, I had searched the internet and followed the procedure described in [https://lynxbee.com/how-to-enable-drm-driver-debug-logging-in-linux/](https://lynxbee.com/how-to-enable-drm-driver-debug-logging-in-linux/). However, this fix does not work across reboots since /sys/module/drm/parameters/debug seems to get overwritten.

---

