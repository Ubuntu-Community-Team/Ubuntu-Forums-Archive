---
title: "General battery question - decreased capacity?"
date: 2011-09-27
forum: Hardware
---

### Post by SkyeFerret on 2011-09-27
Acer Aspire 4520
Ubuntu 11.04
Upgraded from Windows Vista

My laptop lasts 1m30s after unplugging from AC power. It then throws itself into a seizure and shuts down.

It says my battery is down to 30% capacity and that it may be old or broken, too.

Just wondering, before I spend any money on a new battery, is this any kind of known glitch with switching out Vista for Ubuntu? I'm fairly sure there were no battery problems prior, but I'm not absolutely sure.

Thanks!

---

### Post by SkyeFerret on 2011-09-30
[[If double posts aren't allowed here, merge this with my other post. I'm not sure if they are or not.]]

Here's what Ubuntu's battery monitor has to say about all this.

---

### Post by viperdvman on 2011-09-30
I too have less battery time in Ubuntu 11.04 (running Ubuntu Classic desktop) than I do in Windows 7, and I run an Asus Eee PC netbook with an AMD V105 processor and ATI Radeon 4250/4270 HD. But then again, I usually have my AC adapter with me, so battery life means little unless I'm on a bus/plane/train with no AC access.

But how do we get more battery life out of our laptops/netbooks running Ubuntu? And how does resource-heavy Windows 7 use less power?

---

### Post by SkyeFerret on 2011-09-30
> **viperdvman said:**
> I too have less battery time in Ubuntu 11.04 (running Ubuntu Classic desktop) than I do in Windows 7, and I run an Asus Eee PC netbook with an AMD V105 processor and ATI Radeon 4250/4270 HD. But then again, I usually have my AC adapter with me, so battery life means little unless I'm on a bus/plane/train with no AC access.

But how do we get more battery life out of our laptops/netbooks running Ubuntu? And how does resource-heavy Windows 7 use less power?

Exactly what I'm wondering. I just want to know before I go spend money on a new battery to find that it's not a battery problem.

I'm using Unity, by the way, so I don't think it's a UI issue.

---

### Post by rogue1987 on 2011-09-30
I had the same issue, went from about 2 hours to less than an hour and a 1/2. the laptop is a 17" HP Pavilion. My suspicion is the video driver as I had issues when converting this to Ubuntu. It won't run Unity, even though it has plenty of resources to do it.

---

### Post by SkyeFerret on 2011-10-03
> **rogue1987 said:**
> I had the same issue, went from about 2 hours to less than an hour and a 1/2. the laptop is a 17" HP Pavilion. My suspicion is the video driver as I had issues when converting this to Ubuntu. It won't run Unity, even though it has plenty of resources to do it.

My video card works fine and runs Unity. The only problem I had was with the Broadcom card.

Should I just buy a new battery (I can get it at a discount) or...?

---

### Post by diasf on 2011-10-03
What he meant is that VGAs usually use a lot of power, and the drivers for linux not always control that power as they do on windows. Same for the rest of hardware, mostly.

AFAIK, yes, linux in general uses a bit more power than windows atm, but that can be minimized by properly configuring the system. The "out of the box works" concept was greatly improved on linux recently, but some stuff still need some under the hood tweaks.

---

### Post by SkyeFerret on 2011-10-04
> **diasf said:**
> The "out of the box works" concept was greatly improved on linux recently, but some stuff still need some under the hood tweaks.

What tweaks can you suggest?

EDIT: Found this, the one comment here helps a lot: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/516023](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/516023)

```
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
```

---

### Post by tgalati4 on 2011-10-04
Recompiling your kernel to support undervolting and using phctool (for Intel chips only) to set the voltage schedule.  Turning on dynamic clock for your graphics card--card specific--throttles the graphics card during low use.  This is typically done in an xorg.conf setting.

---

### Post by SkyeFerret on 2011-10-04
> **tgalati4 said:**
> Recompiling your kernel to support undervolting and using phctool (for Intel chips only) to set the voltage schedule.  Turning on dynamic clock for your graphics card--card specific--throttles the graphics card during low use.  This is typically done in an xorg.conf setting.

I... have no idea how to do pretty much anything with the kernel yet. Still an Ubuntu newbie, and I'd rather not tinker with that until I'm ready. I don't want to break anything. :P
I've found a fix that keeps my laptop from shutting itself off after about a minute, but the battery still drains faster than I'd like. I'll see if I can turn on dynamic clock; I'm not using anything overly graphics intensive on this thing, so that might help out. I'll let you know. Thanks! <3

EDIT: Friend pointed out CompizConfig, tinkering with that and turning off effects and such, looks like it's helping things a little. Still looking for how to enable dynamic clocks on nVidia GeForce 7000m. I know it's through xorg.config but I don't know what to tell it to do. D:

---

### Post by SkyeFerret on 2011-10-10
> **tgalati4 said:**
> Turning on dynamic clock for your graphics card--card specific--throttles the graphics card during low use.  This is typically done in an xorg.conf setting.

nVIdia X server settings for me, I suppose - says I have adaptive clocking enabled, but it's locked on the maximum setting.

Using the default nVidia generated xorg.conf file. What do you suggest I add to my file to allow me to enable the drop-down menu to change the clocking styles that I know should be there?

My CPU is also on OnDemand right now. I can swap it to PowerSave and see what that does, but right now my focus is on fixing the nVidia thing.

(Again, sorry for double-post; merge with my other post if you want.)

---

### Post by arkanabar on 2011-10-11
Battery life extension is something near and dear to my heart.  Here's what I've done to extend mine:

first, I started with lubuntu 11.04 -- lxde is significantly less demanding than unity.  If you miss gnome 2, it might also be more comfortable.

second, I enabled active state power management in Grub.  Open a terminal.
```

sudo cp /etc/default/grub /etc/default/grub.bak0
sudo nano /etc/default/grub
```and add "pcie_aspm=force" to the line GRUB_CMDLINE_LINUX
then run "sudo update-grub"
This may cause glitches.  That's why I suggested you create a backup first.

Second, I installed the xfce4-power-manager package.  I haven't figured out how to get it to run at startup yet; I have to alt-f2 and run it there.

Third, I installed Jupiter 0.0.50 from webupd8.org -- I use it to disable bluetooth (manually, alas!  I'm looking around for something to do it at boot up besides hal, which is deprecated in natty).

Finally, I downloaded and installed granola.  I know it's captive software, but it helps.  I may kill it to see if jupiter makes it superfluous.

---

### Post by SkyeFerret on 2011-10-22
Okay, here's what I've gotten so far:

Installed Jupiter, -huge- help
Installed compizconfig, tinkered with some of the window effects
Using the GNOME UI in 11.04 instead of Unity (it'd make sense to me that the Unity UI uses more power to render)

So far, those have all helped a lot. :) The battery still only lasts about 10 - 30m depending on what I'm doing, but it's progress from only lasting 1m30s.

I found something interesting, though - My nVidia X Server Settings shows I have three power levels available (0, 1, 2 under powermizer, I think?), but it's locked on power level 2 (max power), with no drop-down menu to change them and the other two power levels greyed out. Anything I can do there?

---

