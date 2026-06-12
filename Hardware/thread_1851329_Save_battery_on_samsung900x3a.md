---
title: "Save battery on samsung900x3a"
date: 2011-09-28
forum: Hardware
---

### Post by Pille456 on 2011-09-28
Hi!

I'm using my samsung 900x3a for about 4 month with linux and it worked better and better, waiting for a few updates. Currently everything works great, except of wifi, which still seems a bit slow to me and the battery power lifetime.
According to some test, I've read about this notebook, it should run around 5 1/2 h wile just surfing with wifi and doing "normal" stiff. But I only get close to 3 1/2 h.
I ran some test with powertop and found this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830) which I could fix with the given idea in the thread.
Maybe you know what I can fix / update to have a better battery lifetime. This is my powertop output, while typing this and running thunderbird in background:

```
The battery reports a discharge rate of 11.7 W
The estimated remaining time is 88 minutes

Summary: 774.7 wakeups/second,  0.0 GPU ops/second and 0.0 VFS ops/sec

Power est.    Usage       Events/s    Category       Description
  6.20 W     26.9%                      Device         Display backlight
  3.35 W      0.0 pkts/s                Device         Network interface: p8p1 (r8169)
  2.77 W     98.0 pkts/s                Device         Network interface: eth1 (wl)
  651 mW      2.2 ms/s     141.3        Timer          hrtimer_wakeup
  609 mW      2.1 ms/s     132.4        Interrupt      PS/2 Touchpad / Keyboard / Mouse
  459 mW    105.6 ms/s      99.8        Process        /usr/lib64/firefox-6/firefox
  432 mW     19.5 ms/s      93.8        Process        /usr/lib64/firefox-6/xulrunner/plugin-container /usr/lib64/mozilla/plugins/libflashplayer.so -g
  431 mW     16.9 ms/s      93.5        Process        /usr/bin/Xorg :0 -background none -verbose -auth /var/run/gdm/auth-for-gdm-XVmMfx/database -nol
  291 mW      2.4 ms/s      63.1        Interrupt      [41] i915
  253 mW     16.7 ms/s      54.9        Process        /usr/bin/gnome-shell
  195 mW      3.5 ms/s      42.4        Timer          tick_sched_timer
 71.5 mW      0.8 ms/s      15.5        Interrupt      [6] tasklet(softirq)
 42.7 mW      5.1 ms/s       9.3        Process        /usr/lib64/thunderbird-6.0/thunderbird-bin
 34.9 mW    376.7 us/s       7.6        Interrupt      [7] sched(softirq)
 24.6 mW     30.8 us/s       5.3        kWork          console_callback
 8.50 mW      0.9 ms/s       1.8        Process        gnome-terminal
 8.27 mW     25.7 us/s       1.8        Process        [ksoftirqd/0]
 4.60 mW     54.2 us/s       1.0        Process        /usr/sbin/lldpad -d
 4.60 mW     28.9 us/s       1.0        Process        [ksoftirqd/1]
 3.91 mW    174.1 us/s       0.8        Interrupt      [9] RCU(softirq)
 3.45 mW     14.1 us/s       0.7        Timer          watchdog_timer_fn
 3.22 mW     37.3 us/s       0.7        Interrupt      [9] acpi
 2.99 mW     14.9 us/s       0.6        kWork          i915_gem_retire_work_handler
 2.99 mW     11.7 us/s       0.6        Process        [ksoftirqd/3]
 2.99 mW      3.8 us/s       0.6        kWork          sync_cmos_clock
 2.76 mW    379.8 us/s       0.6        Process        gnome-power-manager
 2.76 mW    157.2 us/s       0.6        Process        /usr/libexec/upowerd


```First, the ~12W power consumption is fairly to high. Every test I've read about this notebook tells me something around 8W in IDLE mode and a maximum of 33W with maximum power. Currently the notebook (nearly) isnt doing anything, so I would like to hit 8W as close as possible.

The strange parts I see in this output are:
 3.35 W      0.0 pkts/s                Device         Network interface: p8p1 (r8169)
2.77 W     98.0 pkts/s                Device         Network interface: eth1 (wl)

I'm using w-lan,so I can understand the second output, but why do I have two network outputs here and why are the using ~6W for simple 54mb-wifi?

and sometimes I also have an output like this:
1.03 W    100.0%                      Device         Audio codec hwC0D3: *
where * can be Intel or Realtek or both
which I totally cannot understand.

Just for clarity: I'm using currently fedora 15(kernel 2.6.40.4-5 which is the same as kernel 3.0.0.4-5) instead of ubuntu, because I wanted to try gnome 3 and the 3.* kernels, which I couldnt get to work with ubuntu. Therefore powertop is in version 1.98 (which has a totally different look). I already tried the powertop tunables and they really seem to do their job. Activated them, the notebook needs around 1W less, which is really nice. But the tunables arnt activated per default on startup. Is there a way to do so?

Thank you for reading this little wall of text. Hope you have an idea how to tune this notebook a bit more :-)

Greetings
Pille

---

### Post by diasf on 2011-09-28
just a bit of info
Keep in mind that newer kernels (well, not that new, 2.6 and up, if i'm not mistaken) have a "bug" that makes them consume around 30% more than before (and similarly wrt to other OSs).

---

### Post by Pille456 on 2011-09-28
Hi!

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/818830]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/818830") shows this bug and I fixed it  with the "i915.i915_enable_rc6=1 parameter"

---

### Post by diasf on 2011-09-28
wrong bug afaik. The one I knew of is way older than 3.0 kernel. And affected amds as well.

---

