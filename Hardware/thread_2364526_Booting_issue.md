---
title: "Booting issue"
date: 2017-06-24
forum: Hardware
---

### Post by tophertk on 2017-06-24
Running Windows 7 on 1 HDD{Purely for work reasons...converted Linux user :P), Ubuntu 17.04 on a 2nd HDD in dual boot config.

Machine is about 3 years old only thing upgraded is graphics card about 6-7 months ago.

So as of the last 2 or 3 days, I have this really strange problem when I turn on my PC, it will boot for about 2 or 3 seconds then turn off briefly before booting back on.  After it boots back on, it boots directly to the bios. It also states that there are 4 keyboards and 2 mice detected...I only have 1 keyboard and 1 mouse plugged in? 

I have cleaned the inside and checked for any possible connectors that could be causing an electrical short and nothing seems apparent. Also when it boots the heatsink fan, case fans and GPU fans all kick in. When it boots after the second time the system runs fine, I can work and use the machine normally no drops in power or anything else etc...

Temperatures also seem fine for all components such nothing anywhere near dangerous levels of heat. Voltages seem fine too, 5 & 12v rails giving an expected output.

Ubuntu has been running fine for the past 2 weeks or so since I installed it, really enjoying using it, far better platform for a software developer, but this issue is annoying me now and concerning in case it is indeed damaging any of the hardware.

Any help is greatly appreciated :)

---

### Post by Autodave on 2017-06-24
Are you saying that 2 or 3 seconds after you press the button to turn the machine on, this is when it turns off and restarts? If so, that does not sound like a Ubuntu or Windows problem. That is just too soon for either operating system to have any effect on the boot sequence.

I am assuming that both the mouse and keyboard are wired and not wireless? If wireless, try unplugging both USB receivers and see what happens on boot.

You say you checked the voltages: did you do that before or after the system had booted? Try to monitor them while first booting.

Last idea for now until I hear back: even if the mouse and keyboard are wired, try booting with both disconnected.

---

### Post by tophertk on 2017-06-24
Yes you are correct that is when it turns off and restarts, both peripherals are wired, I have tried to boot with them both plugged in and unplugged as well. When I boot with both disconnected, the bios appears with a no keyboard detected message

I had checked the voltages after it had booted, as I had no way to check before.

---

### Post by tophertk on 2017-06-24
Update - I updated the bios to the latest version and the issue seems to have stopped, I will report back if it persists.

---

### Post by Autodave on 2017-06-24
Good deal. It is definitely not an OS issue. Please remember to mark the thread closed.

---

### Post by tophertk on 2017-06-24
Sadly I have to mark is as un-solved again, the bios update seemed to work, but after a few restarts its doing the same thing...

---

### Post by tophertk on 2017-06-24
Any ideas on this, is it ok to continue or could it potentially damage the hardware?

---

### Post by efflandt on 2017-06-25
What graphics card and power supply do you have? Maybe the PSU is marginal for the full load during initial boot. Some PSU's can be overrated (may not supply enough current at certain voltages).

My HP PC from 2004 would not even boot to BIOS splash after a mild AGP (before PCIe) graphics card upgrade (shut off in 3 seconds). Its OEM 250W PSU could not even handle 130 watts (measured AC input with "Kill A Watt" meter after upgrading to better 330W PSU that worked).

But Dell PSU's seem to be more conservatively rated. I recently put my old GTX 550 Ti in a discarded PC from work that was so old that its 3.2 GHz Pentium CPU single core with hyperthreading is 32-bit only and cannot even do SpeedStep. Using (2) PATA drive power connectors into a 6-pin adapter to power the graphics card, its 305W OEM PSU easily handled 240 watts (measured AC input). Although the graphics card is not up to its normal performance in PCIe 1.0 slot, I have to throttle streaming videos to 480p to eliminate dropped frames.

But it is difficult to tell whether the PSU is shutting automatically itself down due to sensing excessive power draw or maybe a bad solder joint or component that does not always make good contact until it heats up a little.

---

### Post by johndough2 on 2017-06-26
Hi

PSU points are well made in the above post.

Initial inrush / surge PSU is not happy, shuts off.  
Then with the load taken off and a residual charge in the capacitiors it will restart cleanly.

Possible a capacitor has popped on the MoBo and it's loss is being felt.
[http://www.instructables.com/id/How-to-reapair-capacitors-on-computer-motherboards/](http://www.instructables.com/id/How-to-reapair-capacitors-on-computer-motherboards/)
[https://en.wikipedia.org/wiki/Capacitor_plague](https://en.wikipedia.org/wiki/Capacitor_plague)

Personally I would not try and replace a capacitor as I am a Clumsy Charlie, I only posted the links to show the possibilities and perhaps you could see such an effect on the MoBo.

---

### Post by CatKiller on 2017-06-26
My motherboard has an automatic overclock ability. That always causes a double boot, since it tests things on the first boot, and then boots again with what it's discovered.

Have you enabled anything like that?

I also agree with the other posters that it isn't caused by the OS at all.

---

### Post by ajlongstreet on 2017-06-26
Sounds like it could also be an issue with the USB Initialization. 

Fast-boot can cause issues with that at times.

---

### Post by tophertk on 2017-07-04
I think it could be the CMOS battery on the motherboard, because when it resets into the bios Fast Boot is set to enabled instead of disabled and Secure boot is on Windows UEFI instead of Other OS.

When I change it back to the correct settings, it boots fine for a few boots then the same issue. So does it seem likely that it could be the CMOS battery causing the issue?

---

### Post by CatKiller on 2017-07-04
Could be. They normally last longer than a few years, but a new battery is incredibly cheap, so it wouldn't hurt to check.

---

### Post by tophertk on 2017-07-04
> **efflandt said:**
> What graphics card and power supply do you have? Maybe the PSU is marginal for the full load during initial boot. Some PSU's can be overrated (may not supply enough current at certain voltages).

My HP PC from 2004 would not even boot to BIOS splash after a mild AGP (before PCIe) graphics card upgrade (shut off in 3 seconds). Its OEM 250W PSU could not even handle 130 watts (measured AC input with "Kill A Watt" meter after upgrading to better 330W PSU that worked).

But Dell PSU's seem to be more conservatively rated. I recently put my old GTX 550 Ti in a discarded PC from work that was so old that its 3.2 GHz Pentium CPU single core with hyperthreading is 32-bit only and cannot even do SpeedStep. Using (2) PATA drive power connectors into a 6-pin adapter to power the graphics card, its 305W OEM PSU easily handled 240 watts (measured AC input). Although the graphics card is not up to its normal performance in PCIe 1.0 slot, I have to throttle streaming videos to 480p to eliminate dropped frames.

But it is difficult to tell whether the PSU is shutting automatically itself down due to sensing excessive power draw or maybe a bad solder joint or component that does not always make good contact until it heats up a little.

Palit GTX1060 6GB
Corsair RM750 Gold Modular PSU

---

