---
title: "Insyde H20 BIOS and Toshiba modules"
date: 2009-11-02
forum: Hardware
---

### Post by szarywilq on 2009-11-02
Hi,

I have linux since Intrepid Ibex release. So I'm far from pro.
My laptop is TOSHIBA SATELLITE A300-1eh.

From 8.10, through 9.04, to 9.10 all the time I still have same problems.

- Bluetooth do not work (adapter starts only after suspend)
- Suspend do not work (after 1st suspend log is full of errors, after second suspend laptop freezes)

> ACPI: Transitioning device [FAN] to D3
ACPI: Unable to turn cooling device [ffff88013fa3aec0] 'off'

- FN do not work at all
- Some minor problems with Battery/AC power sources (system do not switch them when I plug/unplug power cable)

I have found few workaraounds like for errors after suspend, there is line to add in kernel that fix this, (acpi.power_nocheck=1) but still - second suspend = freeze.

I searched everywhere. And after all these months and releases I am pretty sure all of this is because I can't modprobe toshiba_acpi module.

> mateusz@mateusz-laptop:~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.31-14-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device

and because of this

> mateusz@mateusz-laptop:~$ toshset
required kernel toshiba support not enabled.

I can't run toshset.

When I figured that out. I was wondering why I cannot modprobe toshiba_acpi.

So far, I found that this is because few Toshiba notebooks, just like mine, have BIOS made not by Toshiba but by Phoenix or Insyde. For Phoenix, some say that Omnibook module works just fine with it. But not with Insyde h20 BIOS. 

So is there any hope that linux will ever work well on this strange Insyde h20 bios? Have anybody know how to fix it?

---

### Post by SonicsDemon on 2009-11-26
i have no idea. Have the same computer with the same issue.

---

### Post by turvyc on 2009-12-14
*Bump*

I have a Toshiba Satellite L300 ... same issues.

---

### Post by robin314 on 2009-12-16
Same problem here. I would be very interested in seeing the response... 

My fan is the main problem, though it is much worse than most others: mine wont turn _on_ :(

---

### Post by Victory444 on 2010-01-12
> **robin314 said:**
> Same problem here. I would be very interested in seeing the response... 

My fan is the main problem, though it is much worse than most others: mine wont turn _on_ :(

I have a Toshiba L505-S5971 with an Insyde H20 BIOS. Specify **acpi_osi="Linux"** in grub to the kernel and the fan should work with acpi.

My processor is an Intel Core 2 Duo, and /proc/acpi/thermal_zone/THRM/trip_points read 70C, and the critical level of the cpu is 85C. When I specify acpi_osi="Linux" the fan turns on at 50C and off at 40C.

NOTE: depending on what version of grub you have, you may need to escape the quotes with \, such as **acpi_osi=\"Linux\"**.

---

### Post by Nuzair on 2010-01-13
I'm also facing the same problem. I use Toshiba Satellite A100 which is the older version. I get trouble in detecting the bluetooth adapter. Before this, I used Ubuntu 9.04. The bluetooth adapter can be used for a short time only. I find out that the kernel is not supported the toshset application. That why toshiba hardware cannot be used. This is some solution that I find out. However, it's not working on my laptop. Mybe it's working on you.

Open a terminal window
```
cd /etc/init.d
sudo nano tosh-bluetooth
``` Now paste the following script:
 ```
#! /bin/bash

# script to start/stop Toshiba Bluetooth adapter
# requires toshset

case "$1" in
 start)
 /usr/bin/toshset -bluetooth on
 ;;
 stop)
 /usr/bin/toshset -bluetooth off
 ;;
 *)
 echo "Usage: /etc/init.d/tosh-bluetooth {start|stop}" >&2
 exit 1
 ;;

esac

exit 0

``` In Nano, type Ctrl-O to save the script. Ctrl-X to exit Nano.
 Make the script executable:
 ```
sudo chmod 755 tosh-bluetooth
``` Add it to the startup scripts:
 ```
sudo update-rc.d tosh-bluetooth defaults
```

---

### Post by Marc1973 on 2010-01-17
Hmm.  I tried the scripts.  Looked cool (It seemed like things were happening).  Unfortunately, when I tried connecting my phone with the bluetooth, I had the same response (I.E. none).

Thanks for the advice.  The answer is out there.  I am eager to see a solution to this.

---

### Post by SonicsDemon on 2010-01-24
That script was so close. ](*,) So. Close. Yeah, its a no go here. Dang.

---

### Post by Dave Gravox on 2010-10-25
I have an Insyde H20 BIOS on a Toshiba Satellite Pro L510 (PSLGXA-002002). I had major trouble installing Ubuntu and I have no suspend, battery support, hibernate or Fn keys. Only one core seems to be working. Bluetooth does seem to work though.

---

### Post by Dave Gravox on 2010-11-03
*BUMP*

Has anyone got any ideas on getting the Insyde H20 BIOS to work properly?

---

### Post by dkstoney on 2010-11-18
I think the reality of this problem lies with Insyde H2O BIOS.Is it possible to FLASH another, more acceptable, normal, and Earth-friendly BIOS, while banishing the demon BIOS to the furthest reaches of HELL?

---

### Post by moomoo5000 on 2010-11-28
Funny thing, I talked with a very nice man at the Apple store (of all places!) and he said I may be able to call Toshiba support and get a "general BIOS [upgrade/update/something like that] that would be more Linux friendly."

[http://forums.toshiba.com/t5/Satellite-Laptops-all-other/Why-doesn-t-Toshiba-support-Linux/m-p/148974#M11191]("http://forums.toshiba.com/t5/Satellite-Laptops-all-other/Why-doesn-t-Toshiba-support-Linux/m-p/148974#M11191")

The admin on that page said "A bios update won't help, you will have to wait for someone to repackage the kernal to support your hardware."

I'm going to try calling support, but I really don't know who to believe here. Is the devil BIOS really that important to my laptop's performance? This whole position is frustrating... Hope someone comes up with a general solution soon.

---

### Post by rocdoc on 2011-01-30
Function keys and fan control problems on the Toshiba Satellite L300 (and possibly other similar models with the old InsydeH2O BIOS) are solved by upgrading the BIOS to the latest version (2.2). I wrote up the method here:
[https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300)

---

### Post by szarywilq on 2011-03-16
Not for me, unfortunately.

I have Satellite A300 (PSAG4E). Latest BIOS for that model I have found is still 1.80.

---

### Post by corestorm on 2011-03-16
nice post

---

### Post by www.rzr.online.fr on 2011-10-12
Similar issue here on lenovo g470 

BIOS: InsydeH20 3.5 40CN22WW(V1.09)


The fan is always on ... should I wait for a bios update too ?

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

