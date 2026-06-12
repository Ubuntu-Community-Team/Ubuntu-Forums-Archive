---
title: "drm i915 hangcheck..."
date: 2011-09-07
forum: Hardware
---

### Post by oblador on 2011-09-07
Hi friends,

I'm running Ubuntu 11.04, Unity (3d, default), whole system updated. 

Once in a while the screen turns to black, the keyboard stops responding, everything freezes. 

I checked my /var/log/syslog and I got this:


```
Sep  7 09:35:19 lagreca-pc kernel: [33576.136027] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Sep  7 09:35:19 lagreca-pc kernel: [33576.137713] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 14562095 at 14562071, next 14562097)
Sep  7 09:35:21 lagreca-pc kernel: [33577.916432] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Sep  7 09:35:21 lagreca-pc kernel: [33577.916691] [drm:init_ring_common] *ERROR* render ring initialization failed ctl 00000000 head 00000000 tail 00000000 start 00000000
Sep  7 09:35:21 lagreca-pc kernel: [33578.329238] [drm:i915_do_wait_request] *ERROR* something (likely vbetool) disabled interrupts, re-enabling
Sep  7 09:35:27 lagreca-pc kernel: [33584.336039] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Sep  7 09:35:27 lagreca-pc kernel: [33584.336844] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 14562196 at 14562071, next 14562275)
Sep  7 09:35:29 lagreca-pc kernel: [33585.916023] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Sep  7 09:37:04 lagreca-pc kernel: [33680.643592] SysRq : Keyboard mode set to system default
Sep  7 09:37:04 lagreca-pc kernel: Kernel logging (proc) stopped.
Sep  7 09:37:04 lagreca-pc rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="828" x-info="http://www.rsyslog.com"] exiting on signal 15.

```


My video is Intel GM 965, what can I do in order to use Unity 3d without getting this kind of problem?

Thank you.

---

### Post by tojha on 2011-09-14
Hey,

I am also getting the same kind of problem. Whenever i have locked my screen for around 30 minutes it is kind of restarted. I have checked the dmesg also, where i found like -


> [91000.020509] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[91000.020518] render error detected, EIR: 0x00000000
[91000.020541] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 11168507 at 11168506)
[91000.320011] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[91000.320020] render error detected, EIR: 0x00000000
[91000.320035] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 11168510 at 11168506)

---

