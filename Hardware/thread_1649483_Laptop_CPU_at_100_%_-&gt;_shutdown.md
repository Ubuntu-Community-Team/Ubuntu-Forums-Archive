---
title: "Laptop CPU at 100 % -&gt; shutdown"
date: 2010-12-20
forum: Hardware
---

### Post by fa2k on 2010-12-20
Hi, I need to run at 100 % CPU utilisation for extended periods of time*. My laptop shuts down, is there a way to prevent this? I get these messages in syslog:
```
Dec 20 15:06:17 muon kernel: [47234.519895] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:07:02 muon kernel: [47279.428159] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:07:57 muon kernel: [47334.315985] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:08:12 muon kernel: [47349.284177] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:08:37 muon kernel: [47374.234411] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:08:42 muon kernel: [47379.224216] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:08:54 muon kernel: [47390.964625] CPU2: Core temperature above threshold, cpu clock throttled (total events = 2302)
Dec 20 15:08:54 muon kernel: [47390.964629] CPU3: Core temperature above threshold, cpu clock throttled (total events = 2302)
Dec 20 15:08:54 muon kernel: [47390.965660] CPU2: Core temperature/speed normal
Dec 20 15:08:54 muon kernel: [47390.965662] CPU3: Core temperature/speed normal
Dec 20 15:09:06 muon kernel: [47402.744899] Machine check events logged
Dec 20 15:09:22 muon kernel: [47419.141402] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:09:32 muon kernel: [47429.122260] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:09:42 muon kernel: [47439.101870] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:10:47 muon kernel: [47503.968071] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:11:22 muon kernel: [47538.896703] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:12:07 muon kernel: [47583.806186] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:14:07 muon kernel: [47703.560390] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:14:20 muon kernel: [47716.635688] CPU3: Core temperature above threshold, cpu clock throttled (total events = 2612)
Dec 20 15:14:20 muon kernel: [47716.635695] CPU2: Core temperature above threshold, cpu clock throttled (total events = 2612)
Dec 20 15:14:20 muon kernel: [47716.636732] CPU2: Core temperature/speed normal
Dec 20 15:14:20 muon kernel: [47716.636735] CPU3: Core temperature/speed normal
Dec 20 15:14:27 muon kernel: [47723.520730] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:15:32 muon kernel: [47788.388172] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:15:47 muon kernel: [47803.356319] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:16:02 muon kernel: [47818.326989] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:16:12 muon kernel: [47828.306597] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:16:22 muon kernel: [47838.285007] intel ips 0000:00:1f.6: CPU power or thermal limit exceeded
Dec 20 15:16:26 muon kernel: [47842.490234] Critical temperature reached (100 C), shutting down.
Dec 20 15:16:26 muon kernel: [47842.495013] Critical temperature reached (100 C), shutting down.
Dec 20 15:16:27 muon kernel: Kernel logging (proc) stopped.

```

I have a Thinkpad 410i with an intel i5 M430 CPU. It does get hot, but not uncomfortable to work with, I think there may be something wrong with the temperature sensor.



*Because of some badly written teleconferencing software. I also would like to run long computations because this is my desktop replacement.

---

### Post by davidmohammed on 2010-12-20
I would suggest you remove your battery and open the cover hiding your CPU.  Using an air-can - blow the dust off the heatsink etc.

---

### Post by fa2k on 2010-12-20
Thanks, I don't have compressed air at hand, and the computer is only 6 months old, but I'll try it later. Is there a way to make it throttle more aggressively ?

---

### Post by davidmohammed on 2010-12-20
Normally ubuntu is set to "on demand" - if you want to play - suggest you use the powersave/conservation CPU options...

right click the panel and choose "Add to Panel..."

Add "CPU Frequency"

This will add an icon to the panel - click it to display your CPU options.

---

### Post by fa2k on 2010-12-20
Both conservative and powersave seem to have worked fine so far. Thanks for the info!

---

### Post by fa2k on 2011-01-01
Those didn't really work 100 %, I had a shutdown in conservative. I think the best solution is to change the BIOS setting:
Config->Power->Adaptive thermal management := Balanced (not Maximum Performance)

Apparently, max.performance is really max performance -- even at the risk of a sudden shutdown.

BTW: This happened on windows as well. Maybe something is wrong with this laptop

---

