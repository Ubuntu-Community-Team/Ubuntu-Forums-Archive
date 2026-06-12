---
title: "WARNING! power/level is deprecated; use power/control instead"
date: 2014-08-15
forum: Hardware
---

### Post by edcompsci on 2014-08-15
I have had intermittent (and right now have this happening) problems with hibernation on my lubuntu Trusty desktop machine. It seems to happen after dist-upgrades.  So what it does is it will hibernate with a pm-hibernate or hibernate or hibernate-disk command just fine, but when I turn the computer back on, it starts loading but then hangs.  I think I have waited a significant amount of time for it to come all the way back from hibernation but maybe I should try waiting a more extraneous amount of time, which I will have to try, but it wasn't taking so long before.  It may also have something to do with running VMs?  I think most lately it has started doing this since I created and was using some VMs using virt-manager.  I have tried even loading a new kernel to no ado.

So to try to get some system info about this I:

installed all of the packages I think I could by listing from apt-cache
```

sudo apt-cache pkgnames | grep acpi
kacpimon
libacpi-dev
acpitool
acpi
wmacpi
acpitool-dbg
libfwtsacpica1
yacpi
acpid
acpi-support
claws-mail-acpi-notifier
acpitail
acpidump
acpica-tools
libacpi0


```

then installing anything with acpi in the name

then found something by running 
```

acpi --show-empty

No support for device type: power_supply

```


and

```

dmesg | grep -i power
[    0.000000] ACPI: SSDT 00000000cffba6f0 000672 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    1.796813] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.796817] ACPI: Power Button [PWRB]
[    1.796842] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.796844] ACPI: Power Button [PWRF]
[  217.749924] WARNING! power/level is deprecated; use power/control instead
edward@SelfMade-Desktop:~$ 


```


also
```

sudo dmidecode -t 39
# dmidecode 2.12
SMBIOS 2.6 present.


```

Last time hibernate worked, I was having trouble with pm-hibernate, so then installed tuxonice and the hibernate command and it worked for a while, so even though it says device not supported, this power supply was handling hibernate just fine for a while.

I have 4G of memory and my swap part.e is 8.79G.  Could it be my swap part. is too large?

after most recent dist-upgrade I noticed this:
cryptsetup: WARNING: found more than one resume device candidate:
                     e9714b1b-2f18-4273-b8b6-f346da8cd5e5
                     023ea1e3-9ff0-4637-a12f-4a851085d16a
however only one of these devices appears in fstab, so I don't know why the computer sees both of these.

---

