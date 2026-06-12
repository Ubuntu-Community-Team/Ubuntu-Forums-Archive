---
title: "XPS 13 randomly fails to suspend"
date: 2019-11-25
forum: Hardware
---

### Post by myoan on 2019-11-25
Hello all,

My Dell XPS 13 running 19.10 Mate fails to suspsend 50% of the time with such log (dmesg):

```
[514345.017589] PM: suspend entry (deep)
[514345.038112] Filesystems sync: 0.020 seconds
[514345.038745] Freezing user space processes ... (elapsed 0.002 seconds) done.
[514345.041307] OOM killer disabled.
[514345.041308] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[514345.042636] printk: Suspending console(s) (use no_console_suspend to debug)
[514345.042993] wlp58s0: deauthenticating from 2c:79:d7:3f:3c:e4 by local choice (Reason: 3=DEAUTH_LEAVING)
[514345.330713] PM: Some devices failed to suspend, or early wake event detected
[514345.518712] usb 1-3: reset full-speed USB device number 2 using xhci_hcd
[514345.529775] ath10k_pci 0000:3a:00.0: UART prints enabled
[514345.556742] nvme nvme0: Shutdown timeout set to 10 seconds
[514345.557266] nvme nvme0: 4/0/0 default/read/poll queues
[514345.570774] nvme nvme0: ctrl returned bogus length: 16 for NVME_NIDT_EUI64
[514345.598546] ath10k_pci 0000:3a:00.0: unsupported HTC service id: 1536
[514346.247604] acpi LNXPOWER:13: Turning OFF
[514346.247900] mei_hdcp mei::b638ab7e-94e2-4ea2-a552-d1c54b627f04:01: bound 0000:00:02.0 (ops i915_hdcp_component_ops [i915])
[514346.248043] acpi LNXPOWER:12: Turning OFF
[514346.248104] acpi LNXPOWER:11: Turning OFF
[514346.248158] acpi LNXPOWER:10: Turning OFF
[514346.248211] acpi LNXPOWER:0f: Turning OFF
[514346.248263] acpi LNXPOWER:0e: Turning OFF
[514346.248315] acpi LNXPOWER:0d: Turning OFF
[514346.248368] acpi LNXPOWER:0c: Turning OFF
[514346.248421] acpi LNXPOWER:0b: Turning OFF
[514346.248473] acpi LNXPOWER:0a: Turning OFF
[514346.248527] acpi LNXPOWER:09: Turning OFF
[514346.248579] acpi LNXPOWER:08: Turning OFF
[514346.248631] acpi LNXPOWER:07: Turning OFF
[514346.248684] acpi LNXPOWER:06: Turning OFF
[514346.248736] acpi LNXPOWER:05: Turning OFF
[514346.248788] acpi LNXPOWER:04: Turning OFF
[514346.248841] acpi LNXPOWER:03: Turning OFF
[514346.248893] acpi LNXPOWER:02: Turning OFF
[514346.248945] acpi LNXPOWER:01: Turning OFF
[514346.248997] acpi LNXPOWER:00: Turning OFF
[514346.249030] OOM killer enabled.
[514346.249030] Restarting tasks ... done.
[514346.385820] PM: suspend exit
[514346.385864] PM: suspend entry (s2idle)
[514346.391425] Filesystems sync: 0.005 seconds
[514346.391661] Freezing user space processes ... (elapsed 0.002 seconds) done.
[514346.394277] OOM killer disabled.
[514346.394278] Freezing remaining freezable tasks ... (elapsed 0.036 seconds) done.
[514346.430771] printk: Suspending console(s) (use no_console_suspend to debug)
[514346.992256] ACPI: EC: interrupt blocked
[514358.780576] ACPI: EC: interrupt unblocked
[514359.019561] usb 1-3: reset full-speed USB device number 2 using xhci_hcd
[514359.034304] ath10k_pci 0000:3a:00.0: UART prints enabled
[514359.102944] ath10k_pci 0000:3a:00.0: unsupported HTC service id: 1536
[514368.621486] OOM killer enabled.
[514368.621489] Restarting tasks ... 
[514368.633656] wlp58s0: authenticate with 2c:79:d7:3f:3c:e0
[514368.636841] mei_hdcp mei::b638ab7e-94e2-4ea2-a552-d1c54b627f04:01: bound 0000:00:02.0 (ops i915_hdcp_component_ops [i915])
[514368.640075] done.
[514368.703385] wlp58s0: send auth to 2c:79:d7:3f:3c:e0 (try 1/3)
[514368.711365] wlp58s0: authenticated
[514368.715511] wlp58s0: associate with 2c:79:d7:3f:3c:e0 (try 1/3)
[514368.719350] wlp58s0: RX AssocResp from 2c:79:d7:3f:3c:e0 (capab=0x411 status=0 aid=1)
[514368.742527] PM: suspend exit
```

The only way to finally suspend it is to make it living again by pressing the power button at least 8 seconds, that will eventually reactivate the display with a locked screen. By the way what type of signal is sent after 8 seconds of power buton press?

uname -a is Linux  5.3.0-22-generic #24-Ubuntu SMP Sat Nov 9 17:34:30 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

lshw is here: [https://paste.ubuntu.com/p/WQhq7vtJ95/](https://paste.ubuntu.com/p/WQhq7vtJ95/)

Thank you

---

