---
title: "Ubuntu does not take control of my computer"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by linuxpenguin1 on 2009-09-22
Hi Ubuntu Forums,

I already created a new thread relating to my problem but now I have discovered that the problem of my case is much bigger than I had originally expected therefore please do not hate:( on me. 

So, I small recap of my situation: I have just recently installed Ubuntu Linux 9.04 over my Windows partition (so Ubuntu is my main OS now). The installation procedure went smoothly up until the end where it asked me to restart to conclude the process. I clicked on the "Restart Now" button and the computer screen went black. I waited for 30 seconds to 1 minute but the screen was persistently black. I then decided to turn off my computer from the power button as I was unable to do anything else. This problem further persisted when I had to restart my computer when the update process completed. Same old story happened. 

NOW, though, I discovered that when I put Ubuntu to sleep, restart or shutdown the actual OS goes to sleep, shutdown etc. but the actual computer hardware is still turned on and working. I can actually hear the hard drive spinning. This problem only stops when I turn my computer off from the power outlet. 

So, my question goes to you forum how can I resolve this cumbersome problem of not being able to actually turn off the computer hardware.

My tremendous gratitude to anyone that can help me on this problem:popcorn:

---

### Post by dstew on 2009-09-22
What kind of computer is it? Does the Ubuntu OS work OK otherwise? That is, is it only a shutdown problem?

---

### Post by linuxpenguin1 on 2009-09-22
> **dstew said:**
> What kind of computer is it? Does the Ubuntu OS work OK otherwise? That is, is it only a shutdown problem?

Thank you for taking the time to read my message. 

It is a Lenovo, about 4-5 years old, otherwise Ubuntu works flawlessly. Everything is operating perfect but when I am about to sleep or shutdown my computer Ubuntu sleeps or shutdowns normally but the actual computer is still on. I can hear the hard drive spinning and the light on the desktop is switched on indicating that the hardware is in operation.

I don't know what to do:(

Please aid me further in order to solve this cumbersome problem:confused:

---

### Post by Lieter on 2009-09-22
When booting, go into the BIOS(press delete to enter setup) and check the acpi settings, or even better, load the bios defaults and check every setting regarding hardware. It's a longshot, but my bet is has to do with ubuntu not being able to shutdown all hardware(incedentelly, check /var/log/dmesg and /var/log/syslog for all logs regarding the shutdown).

---

### Post by dstew on 2009-09-22
There is a bug report for this problem with a certain type of Lenovo:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234954](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234954)

There is no indication in the bug report of a fix or work-around.

---

### Post by linuxpenguin1 on 2009-09-22
> **Lieter said:**
> When booting, go into the BIOS(press delete to enter setup) and check the acpi settings, or even better, load the bios defaults and check every setting regarding hardware. It's a longshot, but my bet is has to do with ubuntu not being able to shutdown all hardware(incedentelly, check /var/log/dmesg and /var/log/syslog for all logs regarding the shutdown).

Thank you for taking the time to respond to my question. I checked the BIOS of my computer as instructed but I am unfamiliar with what to do. I managed, though, to discover this information regarding the "acpi" settings:

ACPI BIOS IRQ: [IRQ9]
ACPI STANDBY MODE: [S3]
HARD DISK TIMEOUT: [ENABLED]

I hope the following information will shed some light to my situation. By the way, I now have installed on my computer Windows Vista. I know, not the best option by far but this is what I had laying around. Even so, I still would like to install Ubuntu Linux.:P

Thank you for your patience and cooperation:popcorn:

---

