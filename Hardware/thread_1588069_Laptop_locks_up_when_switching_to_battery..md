---
title: "Laptop locks up when switching to battery."
date: 2010-10-04
forum: Hardware
---

### Post by lupusnoctu on 2010-10-04
I'm running Ubuntu 10.10 64-bit on an Asus G72GX. For the most part, it's working pretty well, with a few exceptions and one major issue where the whole system locks up if I unplug it while it's running. Plugging it back in does not unlock it (no surprise there).  If I start the system while it's on battery, it works just fine. It does NOT lock up when I plug it back in if I started it on battery. I suspect it would be a problem with the ACPI, but I've no idea where to begin troubleshooting it.

Any help or ideas would be appreciated.

---

### Post by lupusnoctu on 2010-10-09
After some frustration with Wine on 64-bit, I decided to downgrade to 32-bit. I'm still having this issue. Any help would be very much appreciated. An immobile laptop is an oxymoron and a massive problem for me.

---

### Post by coffeecat on 2010-10-09
> **lupusnoctu said:**
> I suspect it would be a problem with the ACPI, but I've no idea where to begin troubleshooting it.

I agree that's likely.

You can disable acpi in the grub boot options, although I've never been comfortable with disabling acpi entirely. See here for a list of other options you can try:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It's disappointing that that page still only gives instructions to include these options in legacy grub and only gives a link to...

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

...without explaining what to do. I think you would need to edit /etc/default/grub and add whatever options you want to GRUB_CMDLINE_LINUX. Then run 'sudo update-grub'.

---

### Post by lupusnoctu on 2010-10-12
Thank you for the response. That sounds about right. I can't believe I didn't think to try that. Of course, at the time I was more thinking along the lines of logs and debugging. As I'm typing this, I'm pulling in a new generic kernel from the repos, so we'll see if the issue is fixed next time I reboot. If not, then I'll try this. Would I be better off going with acpi=ht or is that obsolete now with true multi-core processors? If memory serves, HyperThreading was only used in the previous generation of single-core CPUs that were trying to act like dual-core CPUs before we started to get real, multi-core processors, but I want to make sure the HT technology isn't needed or beneficial for a multi-core CPU before I turn off ACPI all-together.

Also, I've only been using linux for a few years now, and ACPI has always worked for me in the past. I know it's generally "safe" to turn off ACPI, but I  find myself wondering what would then be handling the power system? Only answer this one if you feel up to it. IF it really bothers me, I could just research it. lol

---

### Post by coffeecat on 2010-10-12
Tbh, I don't know much about acpi, but...

> **lupusnoctu said:**
> Would I be better off going with acpi=ht or is that obsolete now with true multi-core processors? If memory serves, HyperThreading was only used in the previous generation of single-core CPUs that were trying to act like dual-core CPUs before we started to get real, multi-core processors, but I want to make sure the HT technology isn't needed or beneficial for a multi-core CPU before I turn off ACPI all-together.

I came across a thread a few weeks ago where the OP had found that System Monitor was showing an absurd number of processors - something like 12 iirc. Apparently all with their own colour in the Resources tab. From what I remember of the subsequent discussion, it was concluded that the OP's multi-core processor did support hyperthreading and that's why System Monitor was showing so many CPUs. It must have looked impressive! :)

---

### Post by lupusnoctu on 2010-10-23
Well, it's been a while, and I have tried turning off acpi. Without it, the laptop refuses to boot. I have also seen a kernel update or two come down the pipe, and still having problems. This is driving me nuts. I have checked in the bios for anything weird. Nothing. This shouldn't be happening, yet it is. Anyone have any ideas left on what's causing this or how to fix it? I'm tired of using my laptop as a freaking desktop. If I wanted to buy a desktop, I would have upgraded/fixed my current freaking one.

---

### Post by ckennow on 2010-12-20
> **lupusnoctu said:**
> Well, it's been a while, and I have tried turning off acpi. Without it, the laptop refuses to boot. I have also seen a kernel update or two come down the pipe, and still having problems. This is driving me nuts. I have checked in the bios for anything weird. Nothing. This shouldn't be happening, yet it is. Anyone have any ideas left on what's causing this or how to fix it? I'm tired of using my laptop as a freaking desktop. If I wanted to buy a desktop, I would have upgraded/fixed my current freaking one.

I've tested my Asus G72GX on the last 3 releases. Unfortunately the only solution I could come up with was to shut down the laptop before unplugging and shut it down before plugging it back it. that kept it from freezing.

I don't know if this happens to you as well but when I unplug it and it refuses to boot after freezing...I run the Battery calibration and voila! boots back up without having to do a reinstall. I hope that tidbit of info helps. 

The only thing keeping me from using Ubuntu on all my computers (instead of W7 on them all) is this issue and the multitouch touchpad problems. Besides that it's pretty solid.

---

### Post by spantch101 on 2011-01-03
i have an asus k50-di x2 and i am having the exact same issue. i am currently looking for a resolve.... any ideas or did you just revert to windows like me.. sad really... i have been using ubuntu since 6.10..... i am not liking the whole windows 7 thing... any help would be greatly appreciated

---

### Post by tig33r on 2011-01-11
Try this [http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/)
For me new kernel solved lock problem on battery.

---

