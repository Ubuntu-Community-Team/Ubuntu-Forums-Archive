---
title: "Why not dynamic power management?"
date: 2010-07-19
forum: Hardware
---

### Post by x-shaney-x on 2010-07-19
Although in ubuntu power management is *kind of* dynamic (reduces brightness and such when unplugged) I have noticed while trying out some other distros that many of them (Mandriva and openSUSE come to mind) that they also alter cpu scaling dynamically.

What I mean is, when running on AC, cpu scaling is set to performance but when running on battery it automatically switches to powersave (or on-demand depending on the distro) and then more aggressive powersaving states as the battery reaches critical levels.

I have noticed on Mandriva especially I get way more battery life than on ubuntu (up to an hour more depending what I'm doing).

It seems ubuntu uses the on-demand state whether or not on battery.
If I'm plugged in and not worrying about battery I want the best performance and there is certainly a difference between on-demand and performance, especially with desktop effects turned on as such.

I tried disabling on-demand on startup but that left it running on performance when on battery as well.

---

### Post by IcarusR on 2010-07-19
I believe laptop-mode-tools does this, but is disabled due to causing some systems to hang.
Can enable by changing the following line to =true in /etc/default/acpi-support ENABLE_LAPTOP_MODE=false

For config see man laptop-mode.conf

---

### Post by x-shaney-x on 2010-07-19
Hmm, I noticed this line in /etc/default/acpi-support
```
# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf.
```

So I'm slightly confused.
Mandriva has "laptop-mode" as a startup service.
There is no laptop-mode package in ubuntu, is laptop-mode-tools the same thing or is laptop-mode built in and needs the tools package to configure it?

Anyhoo, information regarding laptop-mode-tools suggests it is only to spin down hard drives more often and for longer.
According to some information I read on the Arch wiki it does much more than that.
Does anyone know the full feature-set of laptop mode tools?

---

### Post by x-shaney-x on 2010-07-20
So I went ahead and tried laptop-mode-tools

It doesn't seem to do what I was asking.
The scaling governor is still set to on-demand whether or not it is running on battery.
If I disable on-demand it just runs in performance mode whether or not on battery.

Yes I could use the panel applet to change the scaling governor manually but I think this should be automatic.

I have a fairly powerful laptop and I don't want it to be throttled when it is plugged in, I want it using that power.
But at the same time the OS should surely be smart enough to change states depending.

Mandriva is certainly smart enough (shame it's so stupid with too many other things).

---

