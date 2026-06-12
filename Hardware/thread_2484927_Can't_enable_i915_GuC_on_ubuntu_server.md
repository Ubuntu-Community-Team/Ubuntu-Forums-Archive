---
title: "Can't enable i915 GuC on ubuntu server"
date: 2023-03-14
forum: Hardware
---

### Post by wang.he on 2023-03-14
After some searching I found that there are two ways to enable i915 GuC but neither of them works:

[B]The first way:
[/B]create a file _/etc/modprobe.d/i915.conf_ and add ```
options i915 enable_fbc=1 enable_guc=3
```, then _sudo update-initramfs -k all -u_.

After rebooting the system, I run _systool -m i915 -av_ and the parameters are updated: ```
[COLOR=#000000][FONT=Menlo]enable_fbc[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]= "1"
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]enable_guc= "3"[/FONT][/COLOR]
```[COLOR=#000000][FONT=Menlo] but firmware path is none: [/FONT][/COLOR]```
guc_firmware_path   = "(null)" 
huc_firmware_path   = "(null)"
``` and _dmesg | grep -iE "huc|guc|dmc"_ returns:

```
[    2.679661] i915 0000:00:02.0: GuC initialization failed -110

```

[B]The second way:
[/B]Modify the _/etc/default/grub_ file and add the red text to the GRUB_CMDLINE ```
GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]quiet splash i915.enable_guc=3 i915.enable_fbc=1[/COLOR]"
```

then[FONT=arial] _[COLOR=#24292F]update-grub[/COLOR]_[/FONT]
Both of the ways above works the same for me. The system info is below. It would be appreciated if anyone can help.

Intel N5105

[COLOR=#000000][FONT=Menlo]**Linux version 5.15.0-67-generic (buildd@lcy02-amd64-116) (gcc (Ubuntu 11.3.0-1ubuntu1~22.04) 11.3.0**[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Menlo]modinfo i915 | grep guc[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/skl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/bxt_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/kbl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/glk_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/kbl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/kbl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/cml_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/icl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/ehl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/ehl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/tgl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/tgl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/tgl_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.0.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]firmware:       i915/adlp_[COLOR=#AC1F16]**guc**[/COLOR]_62.0.3.bin[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]parm:           enable_[COLOR=#AC1F16]**guc**[/COLOR]:Enable GuC load for GuC submission and/or HuC load. Required functionality can be selected using bitmask values. (-1=auto [default], 0=disable, 1=GuC submission, 2=HuC load) (int)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]parm:           [COLOR=#AC1F16]**guc**[/COLOR]_log_level:GuC firmware logging level. Requires GuC to be loaded. (-1=auto [default], 0=disable, 1..4=enable with verbosity min..max) (int)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]parm:           [COLOR=#AC1F16]**guc**[/COLOR]_firmware_path:GuC firmware path to use instead of the default one (charp)[/FONT][/COLOR]
```

---

