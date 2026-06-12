---
title: "ati"
date: 2013-07-08
forum: Hardware
---

### Post by albaniaguard on 2013-07-08
hi
i have ubuntu 12.04 install in a acer 5810t laptop with 4gb ram and ati mobility radeon hd 4330 grafik card but i can find the driver. can you help...

---

### Post by QIII on 2013-07-08
Hello!

Is that 12.04, 12.04.1 or 12.04.2?

---

### Post by albaniaguard on 2013-07-08
12.04 lts i have just 1 week wou i have install

---

### Post by Bashing-om on 2013-07-08
albaniaguard; Hi ! Welcome to the forum.
In respect to an ATI graphics card.. what kernel version you have as a base for the operating system is relevant to what can be done.
As of about 5 days ago there has been an option developed for the ATI 2 to 4 serries cards.
See see what kernel version you are presently using, do in terminal (ctl+alt+t) ->
```
uname -r
```
And to see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

The background info - old-:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


and now the good news:
This repository provides AMD Catalyst Lagacy 13.1 (fglrx 8.97.100.7) drivers for Radeon HD 2xxx - 4xxx:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
In respect to the kernels' 3.5 series and above.
Now, I have not taken an opportunity to investigate Tomasz Makarewicz's methods to know what is actually happening to make his patch work or what results. I am aware that 3 people have applied it with solid results. - Your mileage may vary !

[INDENT][INDENT]good things happen
[/INDENT][/INDENT]

---

### Post by QIII on 2013-07-08
I recommend VERY strongly against that course of action.

This PPA is nothing new.  Such approaches have been available for months.

When you downgrade the X Server and the kernel, you effectively break your install. I have been saying for months that it is impossible to say what changes in the future may cause dependency issues or cause problems with updates.

And exactly as I predicted, I have already had to sort this out for a few people on the forums.

You may do as you wish, of course, but this is not a recommended process.

Using 12.04.1 with the proprietary driver or 12.04.2 and later with the open source Radeon driver is a much safer approach.

---

### Post by albaniaguard on 2013-07-08
3.5.0-36-generic
 AND

lspci -nnk | grep -iA3 vga
  *-display               
       përshkrimi: VGA compatible controller
       produkti: RV710 [Mobility Radeon HD 4300 Series]
       shitësi: Hynix Semiconductor (Hyundai Electronics)
       id fizike: 0
       info e bus: pci@0000:01:00.0
       versioni: 00
       gjerësia: 32 bits
       ora: 33MHz
       aftësitë: pm pciexpress msi vga_controller bus_master cap_list rom
       konfigurimi: driver=radeon latency=0
       resurset: irq:47 memorje:c0000000-cfffffff ioport:4000(size=256) memorje:e4400000-e440ffff memorje:e4420000-e443ffff
  *-display
       përshkrimi: Display controller
       produkti: Mobile 4 Series Chipset Integrated Graphics Controller
       shitësi: Intel Corporation
       id fizike: 2
       info e bus: pci@0000:00:02.0
       versioni: 07
       gjerësia: 64 bits
       ora: 33MHz
       aftësitë: msi pm bus_master cap_list rom
       konfigurimi: driver=i915 latency=0
       resurset: irq:44 memorje:e0000000-e03fffff memorje:d0000000-dfffffff ioport:5110(size=8)
ervis@ervis-Aspire-5810T:~$ sudo lshw -C display
  *-display               
       përshkrimi: VGA compatible controller
       produkti: RV710 [Mobility Radeon HD 4300 Series]
       shitësi: Hynix Semiconductor (Hyundai Electronics)
       id fizike: 0
       info e bus: pci@0000:01:00.0
       versioni: 00
       gjerësia: 32 bits
       ora: 33MHz
       aftësitë: pm pciexpress msi vga_controller bus_master cap_list rom
       konfigurimi: driver=radeon latency=0
       resurset: irq:47 memorje:c0000000-cfffffff ioport:4000(size=256) memorje:e4400000-e440ffff memorje:e4420000-e443ffff
  *-display
       përshkrimi: Display controller
       produkti: Mobile 4 Series Chipset Integrated Graphics Controller
       shitësi: Intel Corporation
       id fizike: 2
       info e bus: pci@0000:00:02.0
       versioni: 07
       gjerësia: 64 bits
       ora: 33MHz
       aftësitë: msi pm bus_master cap_list rom
       konfigurimi: driver=i915 latency=0
       resurset: irq:44 memorje:e0000000-e03fffff memorje:d0000000-dfffffff ioport:5110(size=8)
ervis@ervis-Aspire-5810T:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Acer Incorporated [ALI] Device [1025:023f]
	Kernel driver in use: i915
	Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4300 Series] [1002:9552]
	Subsystem: Acer Incorporated [ALI] Device [1025:023f]
	Kernel driver in use: radeon
	Kernel modules: fglrx, radeon

WHAT I NEAD TO DO NOW

---

### Post by Mark Phelps on 2013-07-08
> and now the good news:
This repository provides AMD Catalyst Lagacy 13.1 (fglrx 8.97.100.7) drivers for Radeon HD 2xxx - 4xxx:

That is NOT "good news".  If you actually read through the linked material, you will see that downgrading your X-server is part of the changes that must be made.

I agree with QIII in advising AGAINST using this kind of "hack" to get older drivers working.

---

### Post by Bashing-om on 2013-07-08
albaniaguard; & QIII ---

We are going to follow QIII's most knowledgeable advise,, and dis-regard my erroneous thoughts .. I now stand corrected ...;

From your output it appears that you have hybrid graphics, Intel/AMD:
This thread in it's discussion will enlighten you and guide your decisions. 
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

And by all means, post back to this thread with any additional questions and concerns.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by albaniaguard on 2013-07-09
my laptop is broken,i install again the ubuntu :(

---

### Post by Yellow Pasque on 2013-07-09
If you want to use the proprietary AMD/ATI driver, install Ubuntu 12.04.1: [http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

---

### Post by albaniaguard on 2013-07-11
i have now 12.04.2

---

