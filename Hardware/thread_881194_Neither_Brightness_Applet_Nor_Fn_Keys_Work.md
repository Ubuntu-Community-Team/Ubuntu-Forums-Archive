---
title: "Neither Brightness Applet Nor Fn Keys Work"
date: 2008-08-05
forum: Hardware
---

### Post by kaoskorruption on 2008-08-05
Neither my brightness applet nor my Fn keys work to adjust the brightness. The applet just says "cannot get laptop panel brightness."

This is a Gateway T-6836.

Any ideas?

---

### Post by ibuclaw on 2008-08-05
does the following file exist?
```
 test -f /sys/devices/virtual/backlight/acpi_video0/brightness && echo YES || echo NO
```
If is does, try this:
```
echo 5 | sudo tee /sys/devices/virtual/backlight/acpi_video0/brightness
```
And see if the screen brightness changes

Regards
Iain

---

### Post by kaoskorruption on 2008-08-05
And what if it doesn't?

---

### Post by ibuclaw on 2008-08-05
It may appear that it isn't a supported feature with your motheboard.

Can you run this:
```
sudo lshw | head -n 30
```
And just paste the output of it on the forums so I can get a good idea of what motherboard/bios you are running with.

Regards
Iain

---

### Post by cherok on 2008-08-05
I've got the same problem. 

I ran this code ```
 test -f /sys/devices/virtual/backlight/acpi_video0/brightness && echo YES || echo NO
```

... received a "NO" so I ran the the next one that you provided.

```
 description: Notebook
    product: HP Pavilion dv2000 (GM040UA#ABL)
    vendor: Hewlett-Packard
    version: F.34
    serial: 2CE7300NJP
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=E1062260-3BA4-11DC-B489-9520D860C330
  *-core
       description: Motherboard
       product: 30B5
       vendor: Wistron
       physical id: 0
       version: 62.57
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.34 (06/02/2007)
          size: 96KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.1

```

Thanks, any help would be great.  I'm on a DV 2000 HP Pavilion, more specifically a DV2404ca

---

### Post by kaoskorruption on 2008-08-05
```
phantom                   
    description: Portable Computer
    product: T-6836
    vendor: Gateway
    version: 89.24
    serial: N1B86 T10 34697
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=portable cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=54726974-6F6E-2D2D-2D2D-0003254C3E47
  *-core
       description: Motherboard
       vendor: Gateway
       physical id: 0
       version: Rev1.89.24
       serial: V86JM0040709KF401X
     *-firmware
          description: BIOS
          vendor: Gateway
          physical id: 0
          version: 89.24 (05/22/2008)
          size: 105KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13

```

There's mine.

---

### Post by solariz on 2008-08-09
Same problem here on my Samsung X65, grmpf I need the laptop next week outside the office so I have now to install windows to use it ;(
It is so damn dark without brightness regulation as ssoon as there is any aylight I cant see anything on the display. I tried everything related to this topic in this forum but nothing solved the problem :(



```
 sudo lshw | head -n 30
PCI (sysfs)  
solariz-laptop            
    description: Notebook
    product: SX65S
    vendor: SAMSUNG ELECTRONICS CO., LTD.
    version: 05AF
    serial: 928Z93BP900023
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=A0742550-DB1D-B211-8000-D66D6926514D
  *-core
       description: Motherboard
       product: SX65S
       vendor: SAMSUNG ELECTRONICS CO., LTD.
       physical id: 0
       serial: 123490EN400015
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 06AF (12/04/2007)
          size: 111KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.10
          slot: U2E1

```

One thing I noticed is that if i Press Fn UP/DOWN this only works during boot or if I manually shutdown GDM. So as soon as GDM is active I cant regulate the brigtness anymore.
Currently to regulate I have to /etc/init.d/gdm stop  <regulate using Fn Keys> start gdm


grmpf

---

### Post by DerSkw on 2008-09-10
I have exactly the same problem with my Samsung x65!
But I think it is a problem of the NVidia driver because brightness control works with "nv" !

---

### Post by J-Morris on 2008-09-11
I am having the exact same problem as everyone else here. I am running an HP lap top just like the cool cat above. I would like to see a solution.

---

### Post by Leviathan2k on 2008-10-24
Similar problem for me. Running fresh-installed Ubuntu 8.10rc1 on a Samsung R700. Everything worked fine with the Live CD and also with the installed version, until I installed nvidia drivers. Since then, I cannot activate my second monitor and I cannot change the brightness. The problem is definitely nvidia drivers for me, but it looks very same - the brightness applet says "Cannot get laptop panel brightness". Another thing that stopped working is the Gnome display resolution manager (I had two separate displays set up there before installing drivers, it worked perfectly, but stopped doing that after), but this is a bit offtopic.

By the way, the command from the second post here returned YES, the second command however did nothing to the brightness - it just returned 5.

I tried following the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=836762&highlight=nvidia+brightness&page=2") and added following to */etc/init.d/gdm*:> 
echo -n 100 > /proc/acpi/video/NVID/LCD/brightness
That worked (sort of), now I get full brightness at startup, but it still cannot be changed on running system. Even sudo'ing that command at runtime returns *Permission denied*, so I'm not sure how that could be used to help anything.

---

### Post by Ecologger on 2008-11-13
Are there any updates on this issue?

---

### Post by rekado on 2008-12-02
I'm having similar issues. In my thread I described all methods I tried. Could be that one of these works for you. None worked for me, though...

[http://ubuntuforums.org/showthread.php?t=922401](http://ubuntuforums.org/showthread.php?t=922401)


EDIT: I found a fix for my issue. Booting with the kernel option *acpi_osi=* made it work. Apparently the default string is the cause for this problem.

---

### Post by rekado on 2008-12-08
> **Leviathan2k said:**
> ...

I tried following the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=836762&highlight=nvidia+brightness&page=2") and added following to */etc/init.d/gdm*:
That worked (sort of), now I get full brightness at startup, but it still cannot be changed on running system. Even sudo'ing that command at runtime returns *Permission denied*, so I'm not sure how that could be used to help anything.


The sudo command cannot pipe the standard output to a file. Try to use "tee" (Wikipedia: [http://en.wikipedia.org/wiki/Tee_(command](http://en.wikipedia.org/wiki/Tee_(command))) in the following way:


echo *value* | sudo tee *file*

---

### Post by PC_load_letter on 2009-07-04
> **Leviathan2k said:**
> ...

By the way, the command from the second post here returned YES, the second command however did nothing to the brightness - it just returned 5.

...

Exactly what I have on my Dell Vostro 1400 after a clean install of Jaunty 32bit. I can change the brightness from fn key + up or down. I can change it from the brightness applet as well but once the brightness is changed from it's initial value the brightness applet fails to give a reading and gives "cannot get laptop panel brightness" message.

This is a minor but a very disappointing regression since this worked flawlessly on the same laptop w/ Hardy amd64.
In my case it seems that it is a problem with the brightness applet. 

Any ideas?

---

### Post by PC_load_letter on 2009-07-04
And here is the output from the lshw command:

```
$ sudo lshw | head -n 30
darwin                    
    description: Portable Computer
    product: Vostro 1400
    vendor: Dell Inc.
    serial: xxxxxx
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-4400-1054-8042-B8C04F304731
  *-core
       description: Motherboard
       product: 0TT361
       vendor: Dell Inc.
       physical id: 0
       serial: .8DTB0G1.CN7878383Q00BF.
       slot: &#65533;&#65533;@
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A09 (07/10/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.7.6
```

---

### Post by Saghaulor on 2011-01-19
> **Leviathan2k said:**
> Similar problem for me. Running fresh-installed Ubuntu 8.10rc1 on a Samsung R700. Everything worked fine with the Live CD and also with the installed version, until I installed nvidia drivers. Since then, I cannot activate my second monitor and I cannot change the brightness. The problem is definitely nvidia drivers for me, but it looks very same - the brightness applet says "Cannot get laptop panel brightness". Another thing that stopped working is the Gnome display resolution manager (I had two separate displays set up there before installing drivers, it worked perfectly, but stopped doing that after), but this is a bit offtopic.

By the way, the command from the second post here returned YES, the second command however did nothing to the brightness - it just returned 5.

I tried following the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=836762&highlight=nvidia+brightness&page=2") and added following to */etc/init.d/gdm*:
That worked (sort of), now I get full brightness at startup, but it still cannot be changed on running system. Even sudo'ing that command at runtime returns *Permission denied*, so I'm not sure how that could be used to help anything.

Sudo'ing fails because you need to ```
sudo su
``` Then enter the code.

I chown'd my brightness file, so that now I only have to enter the command to modify the brightness. Now I'm just trying to figure out how to get the brightness applet to modify the values.

---

### Post by Saghaulor on 2011-01-19
> **Leviathan2k said:**
> Similar problem for me. Running fresh-installed Ubuntu 8.10rc1 on a Samsung R700. Everything worked fine with the Live CD and also with the installed version, until I installed nvidia drivers. Since then, I cannot activate my second monitor and I cannot change the brightness. The problem is definitely nvidia drivers for me, but it looks very same - the brightness applet says "Cannot get laptop panel brightness". Another thing that stopped working is the Gnome display resolution manager (I had two separate displays set up there before installing drivers, it worked perfectly, but stopped doing that after), but this is a bit offtopic.

By the way, the command from the second post here returned YES, the second command however did nothing to the brightness - it just returned 5.

I tried following the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=836762&highlight=nvidia+brightness&page=2") and added following to */etc/init.d/gdm*:
That worked (sort of), now I get full brightness at startup, but it still cannot be changed on running system. Even sudo'ing that command at runtime returns *Permission denied*, so I'm not sure how that could be used to help anything.

Sudo'ing fails because you need to ```
sudo su
``` Then enter the code.

I chown'd my brightness file, so that now I only have to enter the command to modify the brightness. It's an ugly hack that removes one extra step.

Now I'm just trying to figure out how to get the brightness applet to modify the values.

---

### Post by Saghaulor on 2011-02-21
> **Saghaulor said:**
> Sudo'ing fails because you need to ```
sudo su
``` Then enter the code.

I chown'd my brightness file, so that now I only have to enter the command to modify the brightness. It's an ugly hack that removes one extra step.

Now I'm just trying to figure out how to get the brightness applet to modify the values.

Okay, the chown'in only worked until reboot.Apparently something is fixing the permissions at reboot. Apparmor maybe?

---

### Post by fmdex2011 on 2011-02-21
Take a look at this link:

[https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)

I have a Gateway NV59 that had the same problem and used this fix to cure it

Now the Fn keys work and the power management app works

Hope this helps :)

---

