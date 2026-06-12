---
title: "Ubuntu 22.04, Intermittent monitor problems"
date: 2022-10-20
forum: Hardware
---

### Post by Advait on 2022-10-20
I'm running Ubuntu 22.04 LTS Gnome Wayland an MSI Bravo 15 Ryzen 7 4800H 15.6" 40GB A4DDR-212IN laptop. It's about 2 years old. I just did a software update and reboot and the problem is still there.

In the past week or so the screen has been intermittently acting up. See here 

[https://youtu.be/ehUqmKF0tMM](https://youtu.be/ehUqmKF0tMM) 

to see exactly what's going on. Anyone seen anything like this? Any ideas what's going on and how to fix it? How can I run diagnostic tests on my graphics/screen stack?

Note: I'm referring here to the laptop screen, not an external monitor.

PS: Next time the problem happens, I'll switch to X11 and see what that does.

Update, I plugged in an external HDMI monitor and the problem was not happening on the external monitor. Does this narrow down where the problem is?

---

### Post by TheFu on 2022-10-26
I didn't reply to this because "I'm running Ubuntu 22.04 LTS Gnome".  I don't use any of those. Sorry.

Looked at the video (which I wouldn't normally do, but you've been here some time) .... to me, looks like a failing monitor, bad cable or incorrect refresh rate seeing.  You can check the EDID information that the GPU is getting from the monitor and check of that maps to the technical specs for the monitor.

Does the monitor work correctly with other computers driving it?  This checks if it is the monitor or the computer.  Try different hardware, different OSes, etc.
Does the monitor work correctly when booted from a "Try Ubuntu" flash drive?  This checks if it is the installed OS settings or not.
Does the monitor work correctly under a different/new login account?  Perhaps there are some old Gnome settings that are bad.

If this is about the laptop screen, the cable may have become loose.  Reseat it.  A replacement screen usually isn't THAT expensive ($30-$50) and about a 10 minutes to swap. Sadly, there aren't any smaller parts to be replaced, so swapping the entire screen is the normal troubleshooting step.

Be certain to check the GPU temperatures.  Does it only happen when cold or when really hot?

The normal way to isolate any issue is to simplify and test, changing 1 thing at a time.  Keep going until you figure out the only remaining area that cannot be swapped or tested separately.

---

### Post by Advait on 2022-10-27
Great. Thanks! The problem is with the laptop screen, not an external monitor. I'll get started on checking the items you mentioned. Very helpful for a non-techie like me.

I plugged in an external HDMI monitor and the problem was not happening  on the external monitor. Does this narrow down where the problem is?

The problem is very intermittent. It happens for maybe 5 minutes and then goes away. This happens about twice a day.

---

### Post by TheFu on 2022-10-27
Well, it certainly helps to know that it doesn't happen over HDMI, but if it happened with all connected devices, on all OSes, then I'd lean towards the GPU hardware being the issue.  We can't rule that out, but we know it isn't the entire GPU, if there's only 1 GPU in the system.  

These new-fangled systems often have discrete and internal GPUs.  This happens with Intel CPUs and nvidia GPUs all the time.  There's a program/BIOS setting to disabled the iGPU.  On the Ryzen you have, I don't know.  I've seen 1 used for the laptop screen and another used for all external video connections. Hard to say.  Can you do more research for your exact hardware about that?

---

### Post by Advait on 2022-10-27
> **TheFu said:**
> Well, it certainly helps to know that it doesn't happen over HDMI, but if it happened with all connected devices, on all OSes, then I'd lean towards the GPU hardware being the issue.  We can't rule that out, but we know it isn't the entire GPU, if there's only 1 GPU in the system.  

These new-fangled systems often have discrete and internal GPUs.  This happens with Intel CPUs and nvidia GPUs all the time.  There's a program/BIOS setting to disabled the iGPU.  On the Ryzen you have, I don't know.  I've seen 1 used for the laptop screen and another used for all external video connections. Hard to say.  Can you do more research for your exact hardware about that?

I'll research and get back soonest. Thanks!

---

### Post by Advait on 2022-10-28
On Reddit someone said that it could be a monitor cable issue cuz the problem is not happening on the external HDMI monitor. In my experience, many computer problems arise from faulty wiring/cabling. I'll take my laptop to a repair place so they can check.

Looks like my laptop has only 1 GPU (an AMD Radeon RX 5500M). This GPU has 22 "compute units". I don't know what a "compute unit" is. Maybe each "compute unit" can controller a monitor. I don't know.

---

### Post by TheFu on 2022-10-28
Compute Units are tiny CPUs designed to do 1 task well.  It is the backbone of GPU technology.  22 isn't many.  A mid-level GPU will have over 4600 units. Of course, they are broken down into specialized processors, good for specialized workloads - shading, texture mapping, render output.  This is all beyond me.

Certain workloads seem to be designed specifically for these little compute units, but only if they can be parallelized.  

Today, we get the same compute power in a $400 desktop as we had in a Cray supercomputer in 1990 costing many millions. It is little surprise that GPUs have similarly greater GPUs.

BTW, my first post here says "bad cable", but I wouldn't take it into a shop until I'd removed the other, easy-to-check, things, like the OS settings.

---

### Post by Advait on 2022-10-29
> **TheFu said:**
> Does the monitor work correctly when booted from a "Try Ubuntu" flash drive?  This checks if it is the installed OS settings or not.
Does the monitor work correctly under a different/new login account?  Perhaps there are some old Gnome settings that are bad.

If this is about the laptop screen, the cable may have become loose.

I tried both of those tests and no change. Problem still happening. I'll take it to the shop. Thanks for all your suggestions! :KS Cheers.

---

### Post by Advait on 2022-10-29
> **TheFu said:**
> Compute Units are tiny CPUs designed to do 1 task well.  It is the backbone of GPU technology.  22 isn't many.  A mid-level GPU will have over 4600 units. Of course, they are broken down into specialized processors, good for specialized workloads - shading, texture mapping, render output.

BTW, my first post here says "bad cable", but I wouldn't take it into a shop until I'd removed the other, easy-to-check, things, like the OS settings.

Here's some suggestions I got from someone on the LinuxQuestions forum. They look pretty good to me. What do you think? (Note:  the problem also happens on Xorg.)

Start---------------------
Don't be surprised if the shop finds nothing wrong. That video resembles  corruption I've seen with various GPUs on various distros, often called  tearing. Various combinations of hardware and software have bugs, and  this is one of the types that gets past software developers' own  testing, particularly the driver writers it seems. 

Disabling compositing may make the problem disappear, but it can come with a feature loss cost.

You could try using the modesetting DIX display driver instead of the  amdgpu DDX display driver. Simply uninstall xserver-xorg-video-amdgpu  and reboot. If it helps, you're done if you want to be. If not,  reinstall it or not, but [communicate the issue]("https://gitlab.freedesktop.org/xorg/driver/xf86-video-amdgpu/-/issues/new")  to the developers of the amdgpu DDX driver for possible assistance.  But, don't do this until you have determined whether it happens with  Xorg too.
End----------------------

Could my system get messed up if I uninstall xserver-xorg-video-amdgpu?

Would it be helpful if I tried switching from the IGPU to the AMD GPU and see what that does?

FYI: I'm using prime-select = on demand

---

### Post by TheFu on 2022-10-29
I'm not qualified to have a useful opinion. Sorry.

---

### Post by Advait on 2022-10-29
> **TheFu said:**
> I'm not qualified to have a useful opinion. Sorry.

No prob. Thanks again for your help and guidance on this issue.

---

### Post by Advait on 2022-11-10
Turns out my laptop monitor needed replacing. I got the new one installed and it's now working back to normal.

---

