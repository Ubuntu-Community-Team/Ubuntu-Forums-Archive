---
title: "Power management : Powertop and TLP"
date: 2014-01-09
forum: Hardware
---

### Post by jozamm on 2014-01-09
Hi all,

I am using TLP to manage my power on my lenovo W530 and managed to reduce my power consumption to an minimum. I am using powertop to monitor my power settings. When running both programs powertop (version 2.5) still shows some 'bad' settings on battery. I have two questions:

1. Does ubuntu have a script that will run one battery power is detected? i can put the solutions to the 'bad' options in this script and have them run once battery power is detected and vice versa once AC power is detected?

2. Running **tlp stat**  says that following functions are default : 

/sys/module/i915/parameters/powersave        =  1 (enabled)/sys/module/i915/parameters/i915_enable_rc6  = -1 (use per-chip default)
/sys/module/i915/parameters/i915_enable_fbc  = -1 (use per-chip default)
/sys/module/i915/parameters/lvds_downclock   =  0 (disabled)
/sys/module/i915/parameters/semaphores       = -1 (use per-chip default)

It seems that these settings can be changed using GRUB. If these settings to save more power are applied via GRUB will they also be active when running on AC power?

Thanks for your help,

Regards,

Joseph

---

### Post by linrunner on 2014-01-09
Hi,

1) Don't do this. 

You may change one of TLP's settings ```
RUNTIME_PM_ALL=1
``` This isn't enabled by default because some hardware exposes shutdown/reboot problems with it.

After that you can safely ignore powertop's remaining "bad"s. They won't improve your battery life. Refer to the [FAQ]("http://linrunner.de/en/tlp/docs/tlp-faq.html#powertop") too.

2) The i915 boot options are always effective for both bat and ac. But anyway: there is no need to change them, because the only one with real impact &#8211; rc6 &#8211; is enabled by default for your hardware.

The real power hog in the W530 is the discrete Nvidia graphics. So you have to disable it or use the proprietary driver and/or bumblebee to adress that.

---

### Post by jozamm on 2014-01-10
Hi,

Thanks a lot for your help,

I am already using bumblee to manage the graphics card

Regards,

Joseph

> **linrunner said:**
> Hi,

1) Don't do this. 

You may change one of TLP's settings ```
RUNTIME_PM_ALL=1
``` This isn't enabled by default because some hardware exposes shutdown/reboot problems with it.

After that you can safely ignore powertop's remaining "bad"s. They won't improve your battery life. Refer to the [FAQ]("http://linrunner.de/en/tlp/docs/tlp-faq.html#powertop") too.

2) The i915 boot options are always effective for both bat and ac. But anyway: there is no need to change them, because the only one with real impact &#8211; rc6 &#8211; is enabled by default for your hardware.

The real power hog in the W530 is the discrete Nvidia graphics. So you have to disable it or use the proprietary driver and/or bumblebee to adress that.

---

