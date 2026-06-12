---
title: "Samsung NP535U4C-A01 (Nvidia video) Ubuntu 12.10 does not wake up form suspend"
date: 2012-12-20
forum: Hardware
---

### Post by lopcaf on 2012-12-20
Hi all, 

when I try to wake-up a laptop from suspension I just get a black screen (apparently the monitor is off), unfortunately, the scripts described in

[http://ubuntuforums.org/showthread.php?t=1978290](http://ubuntuforums.org/showthread.php?t=1978290)

do not work for me in a  Samsung Series 5 NP535U4C-A01 (with Nvidia video card) running Ubuntu  12.10 (linux kernel 3.5.0-19-generic). I am using the following driver

X.Org X Server -- AMD/ATI display driver wrapper from xserver-org-video-ati

As mentioned before, when I try to wake up the laptop from suspend mode,  the monitor is just black.  Interestingly, if I use the driver of Nvidia, I can resume from suspend  mode with no problem. Unluckily, the Nvidia driver has some issues, such  as bright management, that's why I would prefer to use the X.Org  driver.

The output of my suspend log (pm-suspend.log) is attached. 

Does anyone have any idea/solution?

Thanks!

---

### Post by lopcaf on 2013-01-01
Bump

---

### Post by Toz on 2013-01-01
> Unluckily, the Nvidia driver has some issues, such as bright management,
Was brightness management the only issue? If so, you have a few options:

[LIST=1]
[*]enablebrightnesscontrol:
With the proprietry nvidia drivers installed, add:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the "Device" section of your /etc/X11/xorg.conf file and restart X
.
[*]Linux on my Samsung PPA: ([https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/~voria/+archive/ppa"))
.
[*]nvidiabl: ([https://github.com/guillaumezin/nvidiabl]("https://github.com/guillaumezin/nvidiabl") and Downloads here: [https://github.com/guillaumezin/nvidiabl/downloads]("https://github.com/guillaumezin/nvidiabl/downloads"))
[/LIST]

---

### Post by lopcaf on 2013-01-11
> **Toz said:**
> Was brightness management the only issue? If so, you have a few options: ...



Thansk for your reply and sorry for the huge delay. 

I tried to use the Nvidia driver, but after installing it and restarting Ubuntu,  the monitor stopped working. I had to reinstall Ubuntu :( 

Sorry I have no log files, but I lost them during the reinstallation. 

Any further ideas?

Best wishes

---

### Post by Toz on 2013-01-11
>  Samsung Series 5 NP535U4C-A01 (with Nvidia video card)

and

> X.Org X Server -- AMD/ATI display driver wrapper from xserver-org-video-ati

I'm confused. Which video card do you have? Open  a terminal window, run this command and post back the results:
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by lopcaf on 2013-01-11
> **Toz said:**
> I'm confused. Which video card do you have? Open  a terminal window, run this command and post back the results:
```
sudo lspci -vnn | grep -A12 VGA
```


Hi

thanks for the quick reply. 

here is the output of the command

```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:990a] (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device [144d:c660]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=256]
    Memory at feb00000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon
    Kernel modules: radeon
```Cheers!

---

### Post by Toz on 2013-01-11
Okay, so you actually have an ATI card (of some sort), not an nvidia card.

Do you have additional drivers available to install (open the Software Centre, goto Edit->Software sources and look at the Additional Drivers tab) for the video card?

---

### Post by lopcaf on 2013-01-11
> **Toz said:**
> Okay, so you actually have an ATI card (of some sort), not an nvidia card.

Do you have additional drivers available to install (open the Software Centre, goto Edit->Software sources and look at the Additional Drivers tab) for the video card?

Hi, 

as it turns out there are two options of additional drivers:

"Using Video drivers for the AMD graphics accelerators from fglrx (proprietary)"
"Using Video drivers for the AMD graphics accelerators from fglrx-updates (proprietary)"

However I recall seeing this very page (Additional drivers) in my previous installation of Ubuntu and I'm sure it had an Nvidia. (The box of the laptop also says that includes a Nvidia card.)

Cheers!

---

### Post by Toz on 2013-01-11
What does the following command return:
```
sudo lshw -class video
```

---

### Post by lopcaf on 2013-01-12
> **Toz said:**
> What does the following command return:
```
sudo lshw -class video
```


Hi,

this is the output.

  ```
*-display               
       description: VGA compatible controller
       product: Advanced Micro Devices [AMD] nee ATI
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:45 memory:c0000000-cfffffff ioport:f000(size=256) memory:feb00000-feb3ffff
```

---

### Post by Toz on 2013-01-12
Does enabling the **"Using Video drivers for the AMD graphics accelerators from fglrx (proprietary)"** drivers help?

---

### Post by topazhn on 2013-01-25
Hello,

Got here from this thread:
[http://ubuntuforums.org/showthread.php?t=1978290&highlight=lenovo&page=5]("http://ubuntuforums.org/showthread.php?t=1978290&highlight=lenovo&page=5")

My interest stemmed from a recent problem; my T400, running Ubuntu 12.10 would not suspend.

I approached the problem from a different angle. Examining the system log I noted that something called TPM was returning error code 28. Googling revealed that 1. TPM = Trusted Platform Module and 2. This chip, if interupted during a self test, hangs. Getting it back on track is problematic and I didn't persue this path.

It seemed unlikely that a GNU/Linux would use this feature. This Wikipedia link: [http://en.wikipedia.org/wiki/Trusted_Platform_Module]("http://en.wikipedia.org/wiki/Trusted_Platform_Module") is the basis for my reasoning.

I made the "security chip" invisible in the BIOS. Problem solved. And no, I've had no problems coming back from suspend.

Perhaps this chip is your nemesis.

---

### Post by lopcaf on 2013-02-04
> **Toz said:**
> Does enabling the **"Using Video drivers for the AMD graphics accelerators from fglrx (proprietary)"** drivers help?


Hi, sorry for the huge delay. I was in the middle of a project and could not afford to loose the data. 

As suggested, I used the proprietary drivers: "Video driver for the AMD graphics accelerator" and the suspension works. 

However there are some issues with such a driver. 

1) When using two monitors, the only option supported is to clone to output
2) The bright managment does not work
3) The sound coming from the HDMI is not working (well neither does it with the Ubuntu driver)

Sorry again for the delay. 

Cheer!

---

### Post by imcgeoch on 2013-07-12
> **Toz said:**
> Does enabling the **"Using Video drivers for the AMD graphics accelerators from fglrx (proprietary)"** drivers help?

Thank you! I was having this problem with suspend on an ASUS K55N and this solved it.

---

