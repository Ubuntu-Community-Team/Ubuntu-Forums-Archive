---
title: "MotherBoard without RTC battery - fake-hwclock"
date: 2015-07-07
forum: Hardware
---

### Post by peioazkarate on 2015-07-07
Hi,

I've a Motherboard without RTC battery. 
Every time I power up I need to go into the BIOS and update date and time. 
Otherwise ubuntu don't start and appears the message **"errors were found while checking the disk drive for /”**.
I installed **fake-hwclock** without results.
Any idea?.

---

### Post by tgalati4 on 2015-07-07
Is the battery missing?  Was the motherboard designed without a battery for the real time clock (rtc)?  The disk errors are a separate issue.

Look through the log files for other errors.  Open a terminal.

```
more /var/log/syslog
```

Spacebar to page forward, "q" to quit.

---

### Post by peioazkarate on 2015-07-08
It's an embedded system with the RTC battery powered from a rack. When the board is extracted from the rack RTC power is lost. So the BIOS date is lost.
It's not an disk error. When the Ubuntu's init scripts detect a BIOS date previous to the last date saved on disk, launch a fsck.
fake-hwclock should be a workaround.

From fake-hwclock man:
       [I]Many  embedded  Linux  systems do not have a functional hardware clock.
       Either they simply don't have a hardware clock at all or  they  have  a
       hardware  clock  but  it is not usable (e.g. because Linux doesn't know
       how to use it or because no battery is present).

       This can lead to time moving backwards to  some  default  value  (often
       1970)  when the system is rebooted. Since lots of software assumes that
       time only moves forward this is a bad thing. NTP can (and should  where
       practical)  be  used  to sync with an external timeserver but it is not
       available early in the boot process and may be  unavailable  for  other
       reasons.[/I]

But it doesn't works. 
I suspect the script could be launching fsck before the fake-hwclock script is executed.

Someone knows about Ubuntu's init scripts related to fsck?.

---

### Post by tgalati4 on 2015-07-08
Well, there is *tune2fs* and some switches that may bypass the file system check and to continue on errors.

```
man tune2fs
```

Although Ubuntu can run on embedded systems, it's really not designed to.  Expect some breakage and headaches.

---

### Post by peioazkarate on 2015-07-10
tune2fs doesn't solve the issue.
It seems "init" date check works apart of tune2fs parameters.

---

### Post by tgalati4 on 2015-07-10
If you can't boot with *tune2fs* or a *sysctl* parameter (man sysctl), then you have no recourse except to patch the kernel to work with this hardware.  Such patching is not uncommon for getting linux to work properly on embedded hardware.

And it appears that you can't completely turn off *fsck* for file system errors with *tune2fs*, so you need to determine exactly what is causing the file system errors.  Normally time stamps won't, but anything is possible.  Many linux systems boot just fine with a bad rtc (bad motherboard battery, super slow quartz crystal, or fried rtc), and rely on *ntp* to set the clock during bootup.  It's possible that your embedded boards don't have a real date for the default values (like 01/01/2012) when booting.

---

### Post by sinisa1hr-z on 2015-07-10
why not just powered it,with 3V DC source(most motherboards have one 3V DC battery)..like that motherboard have it while is in rack, or make extra long extension cable so will work outside of rack ,too.. so easy workaround..regardless you still have or have not that rack..so if i understand you good,you have jack on mobo (for RTC supply input)what and from where mobo was connected to rack.. so cheapest solution is plastic battery holder(have for 3V batt,and even for 2 X AA type bat) and wire to jack or socket,or pins.. easy like that! well even power adapter ac to 3v dc can be used..but ac/dc adapter to 3vdc i do not recommend as when main ac power is lost.. really cheap hardware workaround.. some (broken)toys have battery holder and wire...so cost can be 0,and "green"...maybe photo of that socket or pins?

---

