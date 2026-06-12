---
title: "2700X idle issue"
date: 2020-12-08
forum: Hardware
---

### Post by CatKiller on 2020-12-08
I'm running Kubuntu 18.04 on a 2700X, in a Gigabyte X470 Gaming WiFi 7 motherboard. The motherboard is running the F51 bios. There's 16 GB of RAM, running at 3200 MHz. It's got a 1 TB NVMe drive, RTX 2080 Ti, and runs off a 750 W Seasonic Prime Ultra PSU. I'm using the 5.4 lowlatency kernel. Sound is using an external USB DAC, a Scarlett 2i2. It all works great except for one niggling thing. 

The issue is that something's broken in the way it comes out of its low power states at idle. At the point it does so, something stalls and the voltage spikes. I've got my fans using the VRM temperature as a proxy for *all the stuff at the top of my case* and, at idle, they'll briefly spin up every ten seconds or so, as the machine decides that it's idled enough and needs to do a squirt of work. That would be ignoreable (the fans are quiet) except for the stall as it happens, which causes audio to skip. 

It's *not* an issue with the audio: when the machine is under heavy load (folding proteins) the audio is absolutely fine. 

I've tried turning off all the power saving things I can think of to try in the UEFI, and the governor is set to performance, but it still exhibits that symptom.

Switching out to the generic kernel doesn't help. 

It's been going on a while, and I couldn't say if it's always behaved like that or started with a particular kernel or UEFI version. It took a while to track down this far of what was causing the audio to skip. 

I'm hoping that someone has some insight or experience into what I might try to prevent this stall on wakeup.

---

### Post by TheFu on 2020-12-08
Could it be connected to USB?  What happens using the on-board audio?

---

### Post by CatKiller on 2020-12-08
> **TheFu said:**
> Could it be connected to USB?  What happens using the on-board audio?

It's a good thought. I had played around with the USB settings to see if I could make a difference previously (the motherboard is able to overvolt one of the USB ports specifically for DACs, which I'm skeptical about, but they claim it's for stability), without any joy.

Sadly in testing tonight I couldn't get either the external or onboard sound to reliably skip - the intermittent nature of the problem has made it tricky to track down already. It's only when the temperature is *just right* that I get the fan burst for the VRMs waking up. I'll keep testing as I get opportunity. 

Interestingly, ALSA picks very different buffer settings for the two devices: 
period_size: 1200
buffer_size: 4800
for the onboard sound, and 
period_size: 48000
buffer_size: 96000
for the USB DAC. 
PulseAudio complains about underruns for the onboard sound, and scheduling delays for the USB DAC.

I've also spotted that ALSA [has a quirk incoming](https://mailman.alsa-project.org/pipermail/alsa-devel/2020-April/166479.html) around asynchronous playback for this USB DAC in particular, so maybe it will all fix itself then.

I've also noticed that ALSA disables PulseAudio's tsched mode for the onboard sound all on its own (the default is to use tsched), but disabling tsched on the 2i2 hadn't helped previously: ALSA just kept interrupting with no data.

Maybe ALSA is just broken, and the stuttery wake from idle is a symptom rather than a cause. Other than the fan and the audio skipping at the same time, everything works fine, so I don't have many tests to use for troubleshooting.

Further testing: they both skip when the machine is idle.

---

### Post by TheFu on 2020-12-09
I've been seeing USB bus resets for 1 bad device that impacts all the other devices, including the keyboard.  If that 1 bad device isn't connected, all is fine.  Those resets show up clearly in the dmesg logs.

---

### Post by CatKiller on 2020-12-09
No, there's nothing like that. It was one of the things I checked early on when I thought the issue might be that the machine was temporarily too busy rather than that it had dozed off.

I've discovered that I can restrict the availability of sleep states from the Linux side as well as (ineffectually, it seems) from the hardware side, so I'll do some testing with that probably tonight.

---

### Post by CatKiller on 2020-12-09
I set processor.max_cstate=0 as a kernel option, which seemed to disable the sleep states according to /sys/devices/system/cpu/cpuidle/current_driver, but the voltage was still being dropped at idle (I monitor VCore with conky) and the audio was still skipping. Still works fine under load. I'm stumped for more things to try for now.

---

### Post by CatKiller on 2020-12-09
OK, so setting ```
processor.max_cstate=0 idle=poll
``` *does* keep the voltage up, and *does* prevent the audio from skipping. The processor's warm, obviously, but not as much as if I'm folding proteins.

---

### Post by CatKiller on 2020-12-09
Setting nohz=off so that it's not tickless, and uses ladder rather than menu to set sleep states, doesn't stop the audio from skipping.

---

### Post by CatKiller on 2020-12-09
Setting ```
sudo cpupower idle-set -d 2
``` *doesn't* stop the audio from skipping.

Setting ```
sudo cpupower idle-set -d 1
``` *does* stop the audio from skipping. I *think* that's functionally equivalent to setting idle=poll on the kernel line, but means I don't need to reboot and deal with the ghastly redraw speeds on the Grub menu.

---

### Post by CatKiller on 2020-12-11
So, as far as I can tell, due to some combination of lying hardware, ALSA being held together with chewing gum and string, and unrealistic assumptions by Linux and PulseAudio, the sleeping core isn't being woken up in time to actually get its work done when it's needed. However long the scheduling thinks it's going to take to do that, it takes longer.

I've tried playing around with buffers and poking the scheduler tuneables to get the lazy core jabbed awake earlier, but without success. Disabling those idle states seems to be the only thing that works. Which kinda sucks.

---

