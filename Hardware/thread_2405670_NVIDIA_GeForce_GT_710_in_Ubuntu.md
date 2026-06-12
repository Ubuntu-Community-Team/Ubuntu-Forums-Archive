---
title: "NVIDIA GeForce GT 710 in Ubuntu"
date: 2018-11-09
forum: Hardware
---

### Post by sed_faster on 2018-11-09
Hello folks,

I need acquire a GPU to my board: [https://www.asus.com/pt/Motherboards/PRIME-B250-PRO/specifications/](https://www.asus.com/pt/Motherboards/PRIME-B250-PRO/specifications/)
I am thinking use this model: [https://www.asus.com/Graphics-Cards/710-2-SL/](https://www.asus.com/Graphics-Cards/710-2-SL/)

Before spend my money I would know if this model will work in my Lubuntu 18.04 LTS or Ubuntu 18.04 LTS.

Thanks

---

### Post by Autodave on 2018-11-09
You shouldn't have a problem with that card at all.  Once you install the card, you will go to Additionial Drivers and that should find the driver that you need and give you the option to install it.  After installation, reboot and life should be good. :-)

---

### Post by oldfred on 2018-11-09
I am using  a GT720 and  found this:
       Fermi based should use 390.xx not newer
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus](https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus)

If you install incorrect driver it can create issues. And you definitely have to purge & then install correct driver.

       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by $yl9pAR%t on 2018-11-09
My Gigabyte GT710 works both with Ubuntu 18.04 and Ubuntu 18.10.

@oldfred
It is Kepler not Fermi.

---

### Post by Bashing-om on 2018-11-09
sed_faster; Hey - 

I run that Nvidia card = 
> 
Graphics:  Card: NVIDIA GK208 [GeForce GT 710B]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1600x900@59.95hz
           OpenGL: renderer: NV106 version: 4.3 Mesa 18.0.5
sysop@x1804mini:~$ 

I also have the development 19.04 installed with the proprietary 390 version driver with no issues there either.
The Nvidia card runs circles around my ole old ATI card :)

[INDENT]newer can be better
[/INDENT]

---

### Post by sed_faster on 2018-11-09
Thanks guys, I will opt this board and after I will post results.

@Bashing-om
How can I get this output in terminal line?

@oldfredI
I will read about NOMODESET

Thanks

---

### Post by Bashing-om on 2018-11-09
sed_faster; Well -

that output is from
```

inxi -GCS

```

will have to install the tool:
```

sudo apt install inxi

```
if you are running an earlier release of ubuntu.
Well worth the read.
```

man inxi

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by sed_faster on 2018-11-09
Hooo, I love linux :)
```

$ inxi -GCS
System:    Host: user Kernel: 4.15.0-22-generic x86_64 bits: 64 Desktop: LXDE (Openbox 3.6.1)
           Distro: Ubuntu 18.04.1 LTS
CPU:       Quad core Intel Core i5-7500 (-MCP-) cache: 6144 KB
           clock speeds: max: 3800 MHz 1: 981 MHz 2: 2661 MHz 3: 2380 MHz 4: 2877 MHz
Graphics:  Card: Intel HD Graphics 630
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz, 1024x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) version: 4.5 Mesa 18.0.5

```

---

### Post by Bashing-om on 2018-11-09
sed_fasterl Uh Huh 

What release are you running as "kaby Lake" has better support in later releases.

[INDENT][INDENT]'buntu - just keeps getting better
[/INDENT][/INDENT]

---

### Post by sed_faster on 2018-11-09
> **Bashing-om said:**
> sed_fasterl Uh Huh 

What release are you running as "kaby Lake" has better support in later releases.
[INDENT][INDENT]'buntu - just keeps getting better
[/INDENT]
[/INDENT]


I can't understand what do you want say. Should I choose another driver in "Additional Drivers?" Because on the this tab in Software and Updates I receive the message "No additional drivers are available".

Thanks

---

### Post by Bashing-om on 2018-11-09
sed_faster; Hummm,,,, no

There are no other drivers for Intel, as the drivers are in the kernel - Additional drivers can not show what is not -  Hence the better support in later kernels (releases) for newer hardware ( Kaby Lake) .

[INDENT]regrets that I fail to communicate
[/INDENT]

---

### Post by oldfred on 2018-11-09
When I built my Haswell Intel system, I did not plan on using my old nVidia card. But made a mistake on selecting version of motherboard that had HDMI and Displayport out and monitor only had VGA & DMI in.
Back then I also thought that performance of new Intel video and somewhat older nVidia were approximately the same. Since I do not game I did not want to purchase newer high performance video.

[https://www.videocardbenchmark.net/compare/GeForce-GT-710-vs-Intel-HD-630/2910vs3540](https://www.videocardbenchmark.net/compare/GeForce-GT-710-vs-Intel-HD-630/2910vs3540)

---

### Post by sed_faster on 2018-11-10
I finished plug my new Asus Nvdia Geforce GT 710 in my PRIME B250-PRO ([https://www.asus.com/pt/Motherboards/PRIME-B250-PRO/](https://www.asus.com/pt/Motherboards/PRIME-B250-PRO/))
After power on I did this:
```

$ inxi -GCS
System:    Host: user Kernel: 4.15.0-22-generic x86_64 bits: 64 Desktop: LXDE (Openbox 3.6.1)
           Distro: Ubuntu 18.04.1 LTS
CPU:       Quad core Intel Core i5-7500 (-MCP-) cache: 6144 KB
           clock speeds: max: 3800 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz 4: 800 MHz
Graphics:  Card: NVIDIA GK208 [GeForce GT 710B]
           Display Server: x11 (X.Org 1.19.6 ) drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz, 1024x768@60.00hz
           OpenGL: renderer: NV106 version: 4.3 Mesa 18.0.5

```

In additional drivers I have this scenario: [https://snag.gy/8T0Aon.jpg](https://snag.gy/8T0Aon.jpg)
Should I must let it stay like this?

Thanks

---

### Post by oldfred on 2018-11-10
With my system and GT710, I found little difference with open source nouveau driver & nVidia driver. But I do not game.
It is offering the proprietary nVidia 390.xx version which should be correct.

---

### Post by sed_faster on 2018-11-10
I can apply the property driver. Exist any software or command native to benchmark GPU and CPU?
I know I can googled about this software around the internet but I am asking about software to benchmark specific nVidia drivers.
Thanks

---

### Post by oldfred on 2018-11-10
I have not used this, but many post their specific configuration so you can compare yours to their's.

       [http://openbenchmarking.org/](http://openbenchmarking.org/)

---

