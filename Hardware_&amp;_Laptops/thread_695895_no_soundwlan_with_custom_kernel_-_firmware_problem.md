---
title: "no sound/wlan with custom kernel - firmware problem"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by Meister Krause on 2008-02-13
Hi Folks,

I'm having trouble compiling/using my custom kernel (not a surprise to me though).
I want to compile a custom kernel to use my 4GB RAM under a 32bit system (enabling PAE-extended memory support).

I did that following the countless ubuntu-kernel howtos. So far everything is fine, 4GB of memory are working. :)

Sound and wireless are not working though. Taking a look at the output from ```
lsmod
``` I see that the appropriate moduls are not loaded.

These are for example for the wireless:

iwl4965
iwlwifi_mac80211
cfg80211

which are loaded when using the generic kernel.

OK, I know that these are proprietary drivers. For the generic kernel the **modules** can be found under /lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi.
Under /lib/modules/2.6.22-custom-kernel there is no ubuntu directory.

So how can I tell ubuntu to use the proprietary drivers when compiling the kernel.
If that is not possible, how can I load the module into the kernel when the new kernel is already running (modprobe just does not find iwl4965 when running the new kernel)?

_**or**_

I know ubuntu does handle the firmware in a different way than debian itself does.

The firmware-file for the wireless card itself can be found under /lib/firmware/2.6.22-14-generic/iwlwifi-4965-1.ucode.
Setting up a symlink for the new kernel in /lib/firmware pointing to the firmware file for the old kernel /lib/firmware/2.6.22-14-generic does not do, does it?

The same for the sound, are the modules

snd_***_*** are missing.


I hope somebody can explain a little, I'd really like to understand.
Thanks in advance...

---

### Post by Ayuthia on 2008-02-13
I am not for sure about which driver you are looking for, but the kernel does have some drivers that will need to be configured.  One way to view the list is to go to the kernel source directory and as root (sudo) do a make menuconfig.  This should bring up a menu where you should be able to configure what you want to add to the kernel.

---

### Post by Meister Krause on 2008-02-13
Thanks, but the driver I'm looking for can not be found within the configuration options of the kernel.
Since I did "make oldconfig" they would be loaded if they would be a kernel option.
This driver (for the intel 4965AGN wireless card) needs special firmware.
The firmware is "existent" but how to help the kernel to make use of it??

---

### Post by Ayuthia on 2008-02-13
Have you checked this site out:
[http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi)

I am not for sure if it will help or not, but it does have some information on how to get their experimental driver up and running.  It looks similar to what you are doing.

---

### Post by Meister Krause on 2008-02-14
Well Ayuthia, you are right, that probably is what I should be looking for.
I'm pretty sure that would work, but than I would have to search through the web to find the proper drivers for my soundcard and for the bluetooth and so on...

I just thought there has to be way to make use of the firmware and the modules which the old kernel is using. I mean the generic kernel works, it uses all those modules, why isn't there a way to tell the new kernel to do the same??????

I also tried something else: the latest Hardy-Kernel which is 2.6.24..... has the modules for the wireless-card I'm using already built in. So I downloaded the sources and compiled the new kernel. The necessary modules are loaded now, but the wireless is still not working.

The main question, which so far no linux geek around me could  answer is:
How to tell the new kernel to make use of the proprietary modules which the generic ubuntu kernel uses.

Thanks for your ideas anyways

---

### Post by Meister Krause on 2008-02-15
back again,

I might be on it:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I guess it's about the restricted modules.

I just switched to hardy and now I compile a new kernel...see if it works

---

### Post by Meister Krause on 2008-02-16
OK, weird:

I compiled  a kernel with the latest ubuntu linux-source and got 2.6.24.2-custom.
PAE (support for 64GB RAM) works, the sound surprisingly works as well.
As the driver iwl4965 for my wlan device can be found within the kernel now I thought this is gonna work for sure - it does not.   ](*,)

Whatever, sound is more important to me.

close this thread?

---

