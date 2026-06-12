---
title: "ACPI Battery Status not working"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by veraction on 2005-12-28
Recently got a Toshiba Satellite L25-S119 and loaded Ubuntu 5.10 on it. (Worked fine except couldn't start x host, so need to change drivers from "ati" to "vesa" in /etc/X11/xorg.conf)

Gnome battery status thing always says that A/C power is connected and battery life is 0% even when it is not. Note that when I booted this up initially (and windows was on it), that the battery status things were working.

And:

```

$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         2250 mAh
last full capacity:      2240 mAh
battery technology:      rechargeable
design voltage:          14400 mV
design capacity warning: 300 mAh
design capacity low:     132 mAh
capacity granularity 1:  32 mAh
capacity granularity 2:  32 mAh
model number:            PA3450U-1BRS
serial number:           ---
battery type:            LION
OEM info:                TOSHIBA

 

[COLOR="Red"]$ cat /proc/acpi/battery/BAT1/state 
present:                 yes
ERROR: Unable to read battery status[/COLOR]

```

I've been googling this for a while. Seems like it should be a fairly common problem, though I have seen any clear cut guides. Seems that the only way to fix it would require recompiling the kernel :cry: 

Also, I have some buttons for skipping tracks of music and pausing (near the power button), and they aren't working. I was wondering if anyone knew how to go about adding functionality to these.

---

### Post by Quirky on 2005-12-28
There are a couple of toshiba-specific kernel modules - are they already loaded? You can check with:

lsmod | grep toshiba

They are toshiba and toshiba_acpi. More info here [http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver) not sure what the plain "toshiba" module does though.

---

### Post by veraction on 2005-12-28
Can't figure this part of the guide out:

```

Configure the kernel - For a 2.6 series kernel, you'll find the driver located at:

    Power management options / ACPI Support / Toshiba Laptop Extras 

```

Where are those options?

Only been googling for 15 min thus far about trying to find these. but will check more later

[edit] Found this command on that site, but it doesn't work -- so I guess that thing is of no use to me

```

$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.12-10-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

```

---

### Post by Luzbel on 2005-12-29
Ubuntu is not to blame, dude. I'm almost sure that it is due to a corrupt DSDT. Most are compiled with Microsoft, so it's not a surprising thing that it isn't very standard. You can fix it, you may want to have a look to this guide:

[http://forums.gentoo.org/viewtopic-t-122145.html](http://forums.gentoo.org/viewtopic-t-122145.html)

BTW, is it Phoenix BIOS based? It would explain the "No such device" thing, since some laptops are not trully made by Toshiba, but bought to others fabricants.

---

### Post by lifeempowered.com on 2006-02-05
I'm having a similar issue.  I have an Averatec 3300 and the low battery warning comes on about every 5 minutes or so.  It always warns that the battery is at 5%.  I can stop this problem by simply turning off low battery notification, but I'd like to be notified since I can't suspend yet.  Any ideas?

---

### Post by nwcowboysfan on 2006-02-05
i am running the same toshiba l25-s119, the problem with the battery is a DSDT problem. i found [https://wiki.ubuntu.com/ACPIBattery?highlight=%28battery%29](https://wiki.ubuntu.com/ACPIBattery?highlight=%28battery%29) to be the most useful guide. this will allow acpi to show the state of your battery, but for me it never changes. now it just says that it is always plugged in with 25 hours of life, etc. regardless if it is running on ac or battery.

if anyone figures this out i would love to hear about it!

---

### Post by bigbird_594 on 2006-05-03
"Gnome battery status thing always says that A/C power is connected and battery life is 0% even when it is not. Note that when I booted this up initially (and windows was on it), that the battery status things were working."

I had the same problem.  I have a Toshiba Satellite M35X-S149 but I thought it might be the BIOS too.  I tried DSDT solution, unloading acpi_sbs, and a number of other suggestions on these forums.  In the end, this has worked for me:


I went to the Toshiba website (This is the URL for my model of laptop only) 

[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp?moid=835422&ct=DL&BV_SessionID=@@@@0291165162.1146698638@@@@&BV_EngineID=ccceaddhjedemjlcgfkceghdgngdgmn.0]("http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp?moid=835422&ct=DL&BV_SessionID=@@@@0291165162.1146698638@@@@&BV_EngineID=ccceaddhjedemjlcgfkceghdgngdgmn.0")

and downloaded the appropriate BIOS update (careful to select Intel not ATI display adapter in my case).  I upgraded my BIOS and it now seems to be working. :D (I'm surprised it was that easy)

Everything else worked out of the box and I'm delighted with Ubuntu - wifi, suspend, hibernate - all perfect :) I'm sure this battery thing is just a hardware oddity - I've never had the battery monitor work on any distribution

Still have a few power management issues to sort out - but over all delighted.

---

