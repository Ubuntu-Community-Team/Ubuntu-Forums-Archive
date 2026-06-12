---
title: "Razer Blade Stealth Screen Glitch Issues"
date: 2016-12-01
forum: Hardware
---

### Post by doomsday.wombats on 2016-12-01
I recently purchased a [Razer Blade Stealth]("http://www.razerzone.com/gaming-systems/razer-blade-stealth") with Intel HD 620 Graphics. I'm having a glitching issue with Ubuntu. When this occurs everything is locked up and I have to force a restart.

I get this glitch occasionally when I logout of my account or suspend. I get this glitch consistently if I open specific fullscreen applications (such as VMware Workstation).

There is a proprietary driver in use (says microprocessor, but I'm guessing this is the integrated graphics). I get this glitch when I use this driver and when I do not.

I'm not quite sure where to start looking for information on this error. Nothing shows up in dmesg. There are no crash logs in /var/log/crash.

Has anyone seen this before? Know of a fix? Hints on where to start looking for information?

> $ lshw -c video
   *-display                      description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:275 memory:db000000-dbffffff memory:90000000-9fffffff ioport:f000(size=64)


[ATTACH=CONFIG]272489[/ATTACH]

Update:
I don't want to jinx this...but I want to say this is fixed.

I ran across a post from some guy saying Fedora 25 worked without any issues. I installed Fedora 25 and sure enough it worked without a problem. Fedora 25 runs kernel 4.8 and uses the i915 driver. I reinstalled Ubuntu 16.04 and started trying kernels around 4.8. I found that 4.9+ uses the i915 driver and seems to work without any problems...so far...

Update 2:
See post below!

---

### Post by doomsday.wombats on 2016-12-04
Turns out this isn't as "fixed" as I thought it was. Updating the kernel to 4.9 seemed to make it work reliably for a while...but it's back to crashing. I got some interesting screens of a partially glitched out kernel panic though (attached).

It's interesting that the error that has a file and line number (/build/linux-j9zxaP/linux-4.4.0/mm/slub.c:3627) is for kernel 4.4 when I have kernel 4.9 installed...could this be the issue?

I investigated further into Fedora 25. After a little experimentation I was able to get it to fail in the exact same way (makes me feel slightly better about my goto OS Ubuntu).

Update:
I can reliably reproduce this bug by hitting caps lock (terrible glitchy sound+video). I installed Windows 10 again to see if this is a hardware issue...everything seems to work under Windows 10.

---

### Post by richjames11 on 2017-01-16
Hi,

Did you ever get to the bottom of this? I'm running Fedora 25 but Ubuntu did the exact same and I think I've run all the same diagnostic steps as you. Caps lock seems to trigger it every time and sometimes unplugging/plugging in peripherals like my USB-C hub. Looks like I'm running kernel 4.8 but I've not tried upgrading it to 4.9.

---

### Post by jcopeland on 2017-02-20
I also ran into this issue and determined it to be related to Caps Lock. For some reason pressing Caps Lock will kernel panic the computer. My solution was to disable the key.

---

### Post by tgibson1380 on 2017-03-15
I'm seeing this on my kaby lake stealth as well.
Same glitchy a/v.


Problem persists on kernels 4.9.14, 4.10.1, 4.10.2, and 4.10.3, as well as 4.11.0-rc2.


Num lock also does it, not just caps lock.

-----------------------------

Actually, I just realized before hitting post that 4.9.15 is out as well, and it seems to be better.
Oddly, the first time I booted into it I hit the caps lock key a few times and it crashed, but with a delay of about 5-10s.
Then, on the second boot, I logged in, then hit the key several times, and it hasn't crashed yet.

---

