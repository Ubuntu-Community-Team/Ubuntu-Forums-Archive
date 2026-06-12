---
title: "Screen Brightness on a Radeon HD 5430 with Kubuntu 13.10"
date: 2013-10-24
forum: Hardware
---

### Post by Monsuco on 2013-10-24
I see a few people are having this issue, oddly mostly with Intel cards.

I have a Radeon HD 5430 card in mine and I use fglrx. I've seen more than my fair share of issues with AMD's buggy drivers. This time around my screen brightness settings only *kinda* work. Usually, if I hit the function keys, it pretty much just ignores me. Instead, I have to adjust the slider on the battery meter and THEN hit the function key and it'll adjust. It also sometimes doesn't adjust when I plug/unplug.

Anyways, I don't want to hijack someone else's thread but I'll be posting the same output that was used in [this thread]("http://ubuntuforums.org/showthread.php?t=2183154").

Here's lspci's vga line
```

monsuco@EarthBound:~$ lspci -k | grep -iA3 VGA
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470]
        Subsystem: Dell Device 0457
        Kernel driver in use: fglrx_pci
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]

```

here's my proc/cmdline

```

monsuco@EarthBound:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=59e82249-d1d1-4593-9284-d7a0acd0779f ro quiet splash vt.handoff=7

```
And here's my backlight interfaces
```

monsuco@EarthBound:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
0
15

```

And here's my [pastebin]("http://paste.ubuntu.com/6293388/")

This is probably as simple as blacklisting a single driver but I'm not an expert at these sorts of things.

I also still get occasional crashes (a bunch of random blocks on the screen, some of which blink). The brightness issues are new to 13.10 but I used to have it periodically crash for no reason and it still does that. I assume that's just fglrx being fickle but if there's something I need to do about that let me know. Who knows what happens when the new fglrx drivers or when Kubuntu switches to Wayland. Maybe that'll help, maybe that'll break a bunch of stuff.

---

### Post by Toz on 2013-10-24
Haven't had much luck with fixing brightness issues with fglrx drivers lately. Unfortunately, I don't have an ATI video card myself to do any real troubleshooting. I did come across [this thread]("http://askubuntu.com/questions/310812/last-couple-of-fglrx-drivers-on-ubuntu-12-04-have-backlight-support-broken") over at AskUbuntu that seems to confirm what I'm noticing. Of interest is the last post in that thread:
> It appears that the latest beta released on Sept. 30th, 2013 (version 13.10) has finally fixed the problem for me. See [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) for more info.

The driver still fails to update brightness once the system is suspended and then resumed. Has anyone had any luck with this?

Perhaps some hope?

---

### Post by Monsuco on 2013-10-28
How peculiar. Why didn't this show up in Kubuntu 13.04 then? Why did this pop up all of a sudden?

So you're saying that the beta drivers might very well solve it for me? Does anyone know just how "beta" are they? I mean, what AMD calls their "stable" drivers are usually anything but. I'm instinctively weary of anything AMD considers "unstable". Has anyone out there tried them?

---

