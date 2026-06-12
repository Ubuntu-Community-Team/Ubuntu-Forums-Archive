---
title: "Nvidia fails to load after sleep"
date: 2020-05-03
forum: Hardware
---

### Post by gsync on 2020-05-03
Hello,

I've being trying to configure my laptop for the past couple of days but with no final success.
The laptop is Lenovo Legion Y740 with RTX 2070 Max-Q Design.

After installation of Ubuntu 18.04 the brightness control is not working - which is pretty terrible on 500nit display.
That's a common problem with all machines that has external GPU.

I installed the Nvidia drivers 435 (did a test with 440, no diff), but again the brightness control isn't working.
To make it work I had to change in the BIOS from "Switchable Graphics" to "Discrete Graphics".

But that let to another problem,
after sleep/hibernate Nvidia cannot start and all I'm getting is a black screen,
which can be resolved only with reboot.

Of course when "Switchable Graphics" is enabled the black screen is no longer a problem.

If anyone have encounter this problem, please share the details for resolving this?

---

### Post by CelticWarrior on 2020-05-03
Ubuntu 18.04 is older than the hardware.
Ubuntu 20.04 is a better fit.
The driver should be 440 and no need to add the graphics drivers PPA if using Ubuntu 20.04.

Then also the usual stuff: Update UEFI, update other firmwares if applicable.

PS - The NVidia is "discrete", not external. "Discrete graphics" in UEFI ("BIOS") enables the Nvidia graphics permanently. With the other option you should be able to switch between graphics via Nvidia X Server Settings (and a reboot). Generally there's no point in using the dGPU Nvidia unless gaming or running demanding software; for web browsing and multimedia use the iGPU as it does the same and saves (a lot of) energy.

---

### Post by gsync on 2020-05-03
Thanks a lot for the suggestion.

I just did new installation of 20.04, then installed the 440 driver.
BIOS is set to Switchable Graphics and to Legacy Mode.

But the brightness control isn't working again.
Anything I'm missing ?

---

### Post by CelticWarrior on 2020-05-03
Legacy mode is not recommended. It may not do anything different but I may be the root cause.
Any UEFI computer - yours has UEFI, not BIOS - should be installed in UEFI mode.

Brightness controls may not work in both graphics. It should work with the dGPU (Nvidia) with proprietary drivers. Drivers for the iGPU (Intel??) should already be installed but it may need additional boot parameters.

---

### Post by gsync on 2020-05-03
The only driver I installed was for NVidia, 440 as suggested.

I have no idea why but the function buttons cannot change the brightness, and I just did a test with this - [http://ubuntuhandbook.org/index.php/2017/05/install-brightness-controller-utility-in-ubuntu-16-04-higher/](http://ubuntuhandbook.org/index.php/2017/05/install-brightness-controller-utility-in-ubuntu-16-04-higher/)

and it's working. Using this tool I can finally manage the brightness level on the laptop.

The new problem is that I cannot use my external monitor over thunderbolt 3.

I checked the Thunderbolt settings in Ubuntu, and it's not showing any device.

---

### Post by gsync on 2020-05-03
Ok, the problem with the Thunderbolt 3 was due to 440 not being tested properly.

I've reverted to 435 and it's all working now.

The only question is, why external tool can change build-in display brightness, but the OS cannot ...

---

