---
title: "dmesg Intel GPU Errors"
date: 2018-05-12
forum: Hardware
---

### Post by kazakore on 2018-05-12
Running Ubuntu Studio 18.04 on my laptop and I've just checked dmesg shortly after booting up and noticed this large chunk of errors relating to the i915 graphics driver. A quick search indicates all Intel integrated chipsets use this i915 driver. My processor is the i7 5500U with the                                                                                                                                                                             Intel® HD Graphics 5500                                         according to Intel's website.

```
[   26.848357] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   28.831781] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   30.879361] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   32.864953] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   36.831136] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   40.863597] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   42.850474] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   44.836653] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   46.886673] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   48.872487] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   50.859542] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   54.894127] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   56.877603] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   58.862515] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   60.847901] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   66.865932] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   68.850392] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   70.898773] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   72.883197] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   74.867017] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   78.901629] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   82.869481] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   84.853692] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   86.900949] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   88.884748] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   90.869094] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   92.852818] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   94.900660] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   96.885409] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[   98.869875] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  100.917084] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  102.901950] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  104.887546] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  106.869692] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  108.853892] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  110.902899] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  112.886095] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  114.869840] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  116.918621] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  118.901713] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  120.886169] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  122.870878] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  124.854504] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  126.901958] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  128.886081] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  130.871621] [drm:i915_gem_idle_work_handler [i915]] *ERROR* Timeout waiting for engines to idle
[  134.775345] [drm] GPU HANG: ecode 8:1:0xfffffffe, reason: Hang on bcs0, action: reset
[  134.775360] i915 0000:00:02.0: Resetting bcs0 after gpu hang
```


Although it finishes stating the GPU has hung I am using it and no instantly obvious errors with the display. Should I worry about this? Is there anything I can do to test if there is a deeper issue?

---

### Post by kazakore on 2018-05-12
This seems to have gone away.

A config change had changed my default audio device away from the onboard analogue chipset and I wonder if the system was polling the HDMI audio, causing it to also try and use it for video, thus generating this output.

But whatever it was it has stopped giving me the error :)

---

