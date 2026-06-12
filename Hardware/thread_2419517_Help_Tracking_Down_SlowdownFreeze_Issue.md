---
title: "Help Tracking Down Slowdown/Freeze Issue"
date: 2019-05-23
forum: Hardware
---

### Post by linuxguy2 on 2019-05-23
I built a little rig, but I'm having continual issues with it.

I often start up the computer without issue, but at some point after the computer starts slowing down tremendously while I'm in some operation (whether it be a game or web browsing, or writing a text document) where an action takes many seconds to register and complete until the point that it freezes up completely and I am unable to unfreeze it. I can't even switch to another session (I'm not sure if this has  anything to do with my using a USB, rather than PS/2, keyboard) when it  gets in this state. I end up having to reboot the machine. This has happened to me many times to the point where I can no longer count on this machine for any serious work.

I have decided to dedicate some time to troubleshoot it and try to fix this darned thing. If I cannot fix it in a reasonable amount of time, I've decided to scrap it and sell it for parts, because I don't have infinite amount of time and resources to dedicate to it. It's my first build in several years, so I'm pretty bummed about the issue, but I also have hope that I can fix it with the help of this wonderful board.

Here are the basic specs of my machine:


[LIST]
[*]AMD RYZEN 5 2400G w/Radeon Vega RX 11 Graphics CPU 
[*]GIGABYTE B450 AORUS M Motherboard 
[*]240GB SATA SSD Startup drive 
[*]2TB SSHD Storage Drive 
[*]16GB DDR4 2400 RAM 
[*]Seasonic FOCUS series SSR-650FM 650W Power Supply 
[*]Ubuntu 18.04 (bionic) 
[/LIST]

(I don't have a dedicated graphics card on there yet, but its a planned upgrade if I manage to fix it)

My first thought is that looking at the logs would be a good place to start, but I know there are many logs, so I'm not sure where to find the relevant ones. I also did not find any kind of "log viewer" in the GUI, but I suppose I'd just view them with nano or something similar.

Some more info. The times I have had issues booting it up I've had it tell me things like this:
[IMG]https://cotg.ws/cloud/index.php/s/ZcAA8t8rPTPmHmL/download[/IMG]

Update: I took the time to type it out as well:

[   32.165535] watchdog: BUG: soft lockup - CPU#5 stuck for 22s! [NetworkManager:932]
[   36.059972] watchdog: BUG: soft lockup - CPU#1 stuck for 22s! [migration/1:15]
[   36.059973] watchdog: BUG: soft lockup - CPU#0 stuck for 22s! [migration/0:10]
[   36.063973] watchdog: BUG: soft lockup - CPU#3 stuck for 22s! [migration/3:27]
[   36.063973] watchdog: BUG: soft lockup - CPU#2 stuck for 22s! [migration/2:21]
[   36.067973] watchdog: BUG: soft lockup - CPU#4 stuck for 22s! [migration/4:33]
[   36.071973] watchdog: BUG: soft lockup - CPU#6 stuck for 22s! [migration/6:45]
[   36.075973] watchdog: BUG: soft lockup - CPU#7 stuck for 22s! [migration/7:51]

If anybody can point me to the rights direction for solving this, I would greatly appreciate it.

---

### Post by CatKiller on 2019-05-23
There are a few avenues that occur to me:

A lot of motherboard manufacturers seem to have had trouble with producing a BIOS that's adequate for Ryzen on the first attempt. Updated versions work much better.

Since 18.04 was released before the APUs were, support for them was iffy when they launched, although newer versions of the kernel and mesa worked much better. I don't know if those changes got backported or not.

People with very similar symptoms to the ones you're seeing had inadequate power supplies: there just wasn't enough juice going to their processor. You haven't said which power supply you're using.

---

### Post by linuxguy2 on 2019-05-23
> **CatKiller said:**
> There are a few avenues that occur to me:

A lot of motherboard manufacturers seem to have had trouble with producing a BIOS that's adequate for Ryzen on the first attempt. Updated versions work much better.

Since 18.04 was released before the APUs were, support for them was iffy when they launched, although newer versions of the kernel and mesa worked much better. I don't know if those changes got backported or not.

People with very similar symptoms to the ones you're seeing had inadequate power supplies: there just wasn't enough juice going to their processor. You haven't said which power supply you're using.

Thank you for your reply, CK!

So, you think it might be the:


[LIST=1]
[*]BIOS
[*]System Version
[*]or Power Supply
[/LIST]

In the case of #1, a BIOS update might do the trick, right?
In the case of #2, an update to the latest Ubuntu version (Currently 19.04) would resolve the issue, correct?
And in the case of #3, changing the power supply to a beefier, adequate one would be the cure.

And yes, I did not initially state my power supply. I have edited my original post to include that.
It has a ***Seasonic FOCUS series SSR-650FM 650W*** power supply, so I don't think that's the source of the problem, in my case.
The RYZEN 5 2400G is rated at 65W.

---

### Post by CatKiller on 2019-05-23
> **linuxguy2 said:**
> Thank you for your reply, CK!

So, you think it might be the:


[LIST=1]
[*]BIOS
[*]System Version
[*]or Power Supply
[/LIST]

In the case of #1, a BIOS update might do the trick, right?
In the case of #2, an update to the latest Ubuntu version (Currently 19.04) would resolve the issue, correct?
And in the case of #3, changing the power supply to a beefier, adequate one would be the cure.

And yes, I did not initially state my power supply. I have edited my original post to include that.
It has a ***Seasonic FOCUS series SSR-650FM 650W*** power supply, so I don't think that's the source of the problem, in my case.
The RYZEN 5 2400G is rated at 65W.

More specifically, things to poke at to see if they tease out more information on the issue. I've never seen that message myself, but it seems to indicate that something is fundamentally not working the way it should be.

Seasonic has a good reputation, and 650 W seems to me to be plenty. It could still be the case that the power delivery to the processor is still under strain; if it's automatically overclocking to more than your motherboard is providing, for example. It's *supposed* to stay within safe limits, but initial implementations *were* a bit sketchy.

The hardware enablement stack might be sufficient to get backported support for the new hardware, rather than a full upgrade. I don't use an APU to be familiar with which versions exactly brought in the support, nor which versions are included in HWE. 

Other than that troubling message at boot, some kind of memory leak might also show up as severely degraded performance over time. Might be worth keeping an eye on, as well. I have conky monitoring a bunch of stuff all the time, but other system monitors that will show memory use are available.

Oh, and dmesg is probably a good place to look for messages, at least unless a different specific place makes itself known. It shows messages about interactions between the kernel and the hardware drivers.

---

### Post by linuxguy2 on 2019-05-29
> **CatKiller said:**
> 
Oh, and dmesg is probably a good place to look for messages, at least unless a different specific place makes itself known. It shows messages about interactions between the kernel and the hardware drivers.

Taking a peek at dmesg gave me a tremendous repetition of these two lines:
```
[drm:dm_vblank_get_counter [amdgpu]] *ERROR* dc_stream_state is NULL for crtc '1'!
[71131.079085] [drm:dm_crtc_get_scanoutpos [amdgpu]] *ERROR* dc_stream_state is NULL for crtc '1'!
```

I also get a line mentioning ***[UFW BLOCK]***, but it contains a MAC address, so I probably would want to repost it intact here.

I might be reinstalling the OS soon- I was thinking of replacing the SSD. Do you think I should stick to 18.04 LTS or would going with 19.04 be better for me and potentially resolve this issue?

---

### Post by CatKiller on 2019-05-29
DRM is the Direct Rendering Manager: hardware accelerated drawing to the screen. It seems from that message that it's having trouble working out the timing for VSync. UFW is the firewall and is probably unrelated.

Normally I'd recommend staying with the LTS releases rather than getting on the upgrade treadmill but, in your case, newer versions should get you better hardware support. If you're reinstalling anyway, trying any particular version only takes a half hour or so.

---

### Post by linuxguy2 on 2019-08-14
I believe it was the BIOS. After updating the BIOS, it has been up and stable for over 30 days.

---

