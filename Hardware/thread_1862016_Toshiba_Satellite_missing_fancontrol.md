---
title: "Toshiba Satellite: missing fancontrol"
date: 2011-10-16
forum: Hardware
---

### Post by geronimo66 on 2011-10-16
Hello,

I got a Toshiba Satellite C660 (sold without OS). CPU is Intel P6200, dual core.
With 11.04 it works mostly; critical functions of hardware-support are regulary acpi/powermanagement.
CPU-clocking control seems to be OK; Suspend / hibernating also works, as dimming of the display.

One issue remains: the control of the annoying fan.

There are two sensors detected, managed by coretemp, which are giving the temperature.

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +32.0°C  (high = +80.0°C, crit = +90.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 2:      +43.0°C  (high = +80.0°C, crit = +90.0°C) 

No sensor for fancontrol.

After about 15 seconds the laptop is running at 933 MHz the temperature of core 2 reaches 47 degrees (celsius) and the fan is switching on.
With my last Toshiba Satellite I could use the omnibook module, set the upper limit to 60 degrees and had a mostly calm working. 
The omnibook module is no more functional (crashing with modprobe).
Now the fan is running about 60%, when the laptop is idle.

I now tried several options, that didn't work, v.a. the acpi_osi kernel command.

How to get fancontrol working again?

thanx for helping
geronimo


PS: the only remaining option of fixing this issue, I find in reach, might be the downgrading of the kernel: the omnibook module, that had provided the fancontrol, was repotedly functional until kernel-version 2.6.31.x
Someone here to tell, how to do such a downgrading / how to find this old kernel-package and if there are problems to use it with natty?

---

### Post by ezramorris on 2011-10-16
Have you tried compiling the module yourself?

```
sudo apt-get install build-essential git linux-headers-$(uname -r)
git clone git://omnibook.git.sourceforge.net/gitroot/omnibook/omnibook
cd omnibook/
make
sudo make install
sudo make load
```

You can then use modprobe to install/remove it. You may need to add it to /etc/modules to get it to load at boot.

I don't have a Satellite, so can't test it, but it builds and installs OK for me.

Hope this helps,
Ezra.

---

### Post by geronimo66 on 2011-10-16
Hi again,

thanx for replying.
I followed the advice and successfully compiled and loaded the module.
But then I found (in the /proc/omnibook location) not the submodules I need for controlling the fan, which I knew from previous use; just "dmi" and "version".

Maybe thus the only remaining option is downgrading the kernel to 2.6.31.*.

PS: I read one post of the developers list of omnibook, that they no more feel required to support the fan with ubuntu, since the system supports it genuinly.
But until now didn't find such support.

---

