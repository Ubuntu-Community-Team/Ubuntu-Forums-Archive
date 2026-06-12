---
title: "AsRock H310m-HDV Hard Crashing broken video output"
date: 2019-12-20
forum: Hardware
---

### Post by seanmuth on 2019-12-20
Hi y'all, been having hard crash issues on my rig. Recently re-did my OS install, and originally went with Mint Cinnamon 18, but was having the hard crash with broken video output issue. Figured I'd come back to ubuntu 19.04, still having the issue.
I've upgraded to 19.10, and also upgraded my BIOS from v3 to v4.10, with no change.

After some internet searching, I've added this to my grub command: 

[PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.alpha_support=1 intel_idle.max_cstate=1"[/PHP]

Which seems to have somewhat lessened the frequency of the crashes down to about 2-3x/day of normal use.

I've followed the instructions in [this thread]("https://ubuntuforums.org/showthread.php?t=2308445") but now I'm stumped.

[Dump of lshw gist is here]("https://gist.github.com/seanmuth/f6d5073fc95942c6390904ae2dd67f78")

---

### Post by oldfred on 2019-12-21
Is it just video or something else.

Are  you able to shutdown with REISUB? So you do not corrupt system?
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Are you able to get to terminal and see what is running with top or htop (not installed by default)?
Can you run system monitor in separate Windows and see what it says?

---

### Post by seanmuth on 2019-12-29
> **oldfred said:**
> Is it just video or something else.

Are  you able to shutdown with REISUB? So you do not corrupt system?
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Are you able to get to terminal and see what is running with top or htop (not installed by default)?
Can you run system monitor in separate Windows and see what it says?

I know I should be not hard rebooting, I'll keep that in mind. I have been able to use TTY (Ctrl + Alt + F1) and type sudo reboot and have the system reboot, however i cannot see the terminal to do anything useful.
I've looked thru syslog and dmesg at the time of the crash, but haven't found anything out of the ordinary.

I think this issue has a lot to do with the i915 drivers for the onboard video.

---

### Post by oldfred on 2019-12-29
I thought this was only for newer systems with older kernel.
        i915.alpha_support=1
With Linux 4.13~4.14, you need to set i915.alpha_support=1 to enable this "alpha" quality driver support for Coffee Lake. 
    
[https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)

---

### Post by seanmuth on 2019-12-30
> **oldfred said:**
> I thought this was only for newer systems with older kernel.
        i915.alpha_support=1
With Linux 4.13~4.14, you need to set i915.alpha_support=1 to enable this "alpha" quality driver support for Coffee Lake. 
    
[https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)

I'm on 5.3.0-24-generic kernel. Setting that i915 alpha flag seems to have helped somewhat, but my issue still exists

dmesg for i915 returns this. That error doesn't seem too crazy, just complaining about a queue underrun?

```
sean@muth-plex ~ &#955; dmesg | grep i915
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.3.0-24-generic root=UUID=1bda1eff-6313-400d-9f7e-98cd590a49d3 ro quiet splash i915.alpha_support=1 intel_idle.max_cstate=1 vt.handoff=7
[    0.060435] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.3.0-24-generic root=UUID=1bda1eff-6313-400d-9f7e-98cd590a49d3 ro quiet splash i915.alpha_support=1 intel_idle.max_cstate=1 vt.handoff=7
[    5.760634] i915 0000:00:02.0: vgaarb: deactivate vga console
[    5.762046] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    5.767139] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[    5.775843] [drm] Initialized i915 1.6.0 20190619 for 0000:00:02.0 on minor 0
[    5.847800] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    5.847804] fbcon: i915drmfb (fb0) is primary device
[    5.847882] i915 0000:00:02.0: fb0: i915drmfb frame buffer device
[  248.529120] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun

```

---

### Post by oldfred on 2019-12-30
Google search finds that error, but much older kernels & systems.
some used this boot parameter.
i915.enable_rc6=0

---

### Post by seanmuth on 2019-12-31
> **oldfred said:**
> Google search finds that error, but much older kernels & systems.
some used this boot parameter.
i915.enable_rc6=0
well rather than attempting to fix the i915 issue, which seems to still be extant for some users on 5.x kernels, I snagged a cheap 2Gb MSI AMD R7 240, and am currently running that. 

```
dmesg | grep i915 
```

no longer shows any output, and I've removed all my special boot params, so we'll see if this issue really is localized to the intel i915 drivers or not! :fingers-crossed:

---

