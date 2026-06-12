---
title: "High CPU temperatures - why?"
date: 2014-12-21
forum: Hardware
---

### Post by stee2 on 2014-12-21
I just installed 14.04 on a Acer Aspire 4755g - i5 2430m, Nvidia GT540m, 4GB RAM

Without running any programs or doing anything at all, the fan is running on mid-speed and the core temperature of the cpu is around 60°.
I tried installing Nvidia drivers - nothing. I deactivated the nv graphics card in the BIOS and the temperatures dropped by a few degrees, core temp is now about 50°. 
This is not really a solution though. Also, the fan should be running much lower and the temperature should be lower at the same time - that's how it's like under Windows.

Any ideas anyone? I'm really not sure where to start the search.

---

### Post by stee2 on 2014-12-21
Here's a powertop readout
```
Zusammenfassung: 436,7 Wakeups/Sekunde,  4,9 GPU-Vorgänge/Sekunde, 0,0 VFS-Vorgänge/Sek. und 7,2% CPU-Auslastung

                Auslastung       Ereignisse/Sek.    Kategorie       Beschreibung
              2,2 ms/s     149,8        Interrupt      PS/2-Touchpad/Tastatur/Maus
            100,0%                      Device         Audiocodec hwC0D3:Intel
            100,0%                      Device         Audiocodec hwC0D0:Realtek
             17,9 ms/s      69,5        Process        gnome-terminal
              1,1 ms/s      40,1        Interrupt      [47] i915
             13,2 ms/s      31,3        Process        /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswi
              8,6 ms/s      29,4        Process        compiz
            261,6 µs/s      33,3        kWork          od_dbs_timer
            608,5 µs/s      14,7        Process        syndaemon -i 1.0 -t -K -R
              3,7 ms/s      14,7        Process        /usr/lib/firefox/firefox
            487,0 µs/s      15,7        Timer          hrtimer_wakeup
              3,4 ms/s      11,7        Process        /usr/bin/ibus-daemon --daemonize --xim
            266,3 µs/s      11,7        Process        [rcu_sched]
             12,5 ms/s       2,0        Process        powertop
              1,4 ms/s       4,9        Process        /usr/lib/ibus/ibus-ui-gtk3
            454,1 µs/s       3,9        Timer          tick_sched_timer
              6,9 µs/s       2,9        kWork          gen6_force_wake_work
             14,2 µs/s       2,0        kWork          intel_unpin_work_fn
              2,8 ms/s      0,00        kWork          rfkill_poll
             87,9 µs/s       1,0        Process        /usr/lib/accountsservice/accounts-daemon
             75,2 µs/s       1,0        Process        /usr/lib/x86_64-linux-gnu/zeitgeist-fts
              4,1 µs/s       1,0        kWork          flush_to_ldisc
              0,0 µs/s       1,0        kWork          disk_events_workfn
            633,2 µs/s      0,00        Process        /usr/lib/ibus/ibus-engine-simple
            431,1 µs/s      0,00        Timer          delayed_work_timer_fn
            281,9 µs/s      0,00        Process        [kworker/1:1]
            233,0 µs/s      0,00        Interrupt      [1] timer(softirq)
            226,2 µs/s      0,00        Process        [rcuos/0]
            219,3 µs/s      0,00        Process        [kworker/u16:0]
            185,4 µs/s      0,00        Interrupt      [7] sched(softirq)
            149,9 µs/s      0,00        Process        [rcuos/2]
            148,3 µs/s      0,00        Timer          tg3_timer
            134,9 µs/s      0,00        Process        [kworker/0:1]
            126,3 µs/s      0,00        Process        [kworker/2:1]


```

---

### Post by tgalati4 on 2014-12-22
Open a terminal:

```
sudo apt-get install htop
htop
```

What processes are taking up your CPU cycles?  Temperature is directly related to CPU use.  Powertop will help the CPU get into deep-sleep mode, but not if there are processes that are actively running.  It's possible that your CPU fan is not being controlled correctly under linux.  Check your BIOS settings for any fan settings.

---

### Post by stee2 on 2014-12-22
Thank you.
Today, I have very different results. I do not know why, but now the core temperature is much lower.

The temperature is at about 40-44° while idling. At the same time the GPU temp is about 36°.

The fan control does seem to work. It's running lower now that the temperature is constantly below 50°. On the other hand, it did not speed up even when reaching temperatures above 90° while doing some benchmarks yesterday.

I have now installed htop, thank you very much for the advice. However, the CPU load is very low. Htop itself is taking up 1.3-2.0% and sits at the top all of the time. 

I guess I can live with those 40something and the fan running on low again, it is weird though.

---

### Post by waterlubber on 2014-12-26
I've had issues with overheating. Look in your fan's exhaust port. If it's dusty, than you don't have any software issues at all. If you can, try to open the case and access the fan. Dust off the dust. If you can't access it, you can try to attach a vacuum and suck out the dust. 

Best to do it now, I had to repair a damaged laptop because my dad let it overheat. Cooked the hard drive, and broke a lot of other things.

---

### Post by pqwoerituytrueiwoq on 2014-12-26
be careful with vacuums they can make the fan spin too fast (combine with paper clip)
are you using nvidia's driver? you probably should for the same of energy efficiency
also possible the unity desktop is putting more of a load on the GPU than windows does

the reason the gpu ups the cpu temp is cause in laptops they use the same heat sync for both chips

---

