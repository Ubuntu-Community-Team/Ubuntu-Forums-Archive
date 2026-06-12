---
title: "How to enable auto suspend / hibernation on critical battery level"
date: 2008-06-28
forum: Hardware
---

### Post by hihihi on 2008-06-28
Your laptop went off on low battery without hibernating.

solution:

laptop-mode tools:
those come with your ubuntu installation, are not started by default but are very very handy for laptop users.

-preconditions:
--your hibernation-script is working well and your laptop awakes from hibernation nicely.
--gnome-power-manager is working, like gives out warnings on battery low.


1.) first of all make sure "laptop-mode" is enabled on battery (not default)

$ sudo gedit /etc/default/acpi-support

set line &#8220;ENABLE_LAPTOP_MODE&#8221; to &#8220;true&#8221;

save;
from now on this will work automatically after next reboot:
 once you're on battery, laptop mode is activated.

to activate on the fly, without having to reboot:

$ sudo laptop_mode start

now laptop_mode is enabled.



2.) now you need to edit laptop-mode-tools:

$ sudo gedit /etc/laptop-mode/laptop-mode.conf

set the
"Disable all data loss sensitive features"-option when the battery level to 1%:

MINIMUM_BATTERY_CHARGE_PERCENT=1

to enable auto-hibernation (hibernate on battery critical-low):

ENABLE_AUTO_HIBERNATION=1

HIBERNATE_COMMAND=/etc/acpi/hibernate.sh (this is my working hibernation script, point it to the script that works for you)

AUTO_HIBERNATION_BATTERY_CHARGE_PERCENT=3 (this value has to be higher than the "MINIMUM_BATTERY_CHARGE_PERCENT"-value and has to give your battery enough time to hibernate)


when you're ready, save.

To be very sure, reboot, open terminal and type:
$ sudo laptop_mode

if on AC it tells you:
 "Laptop mode enabled, not active."

on BATTery it should tell you:
"Laptop mode enabled, active."

this is correct.

-you should read more about laptop-mode, it is a powerful tool
$ man laptop_mode
$ man laptop-mode.conf

but you should really know what you are doing once you start to configure it to your needs. There are some nice threads that can be found on several linux forums. 

I hope this helps anybody searching for the answer.
It works on my laptop very well.

cheers

---

### Post by otaviofcs on 2008-07-04
Thanks for the post. I'll try it now. But, it has a warning:

[B]off by default as it causes odd
# hangs on some machines[/B]

---

### Post by sergiom99 on 2008-07-04
If I applied the ugly fix for the hdd Load_Cycle_Count issue, would it still work with laptop-mode enabled?
I dont want my drive parking heads every other second.

Thanks for the tuto.

---

### Post by otaviofcs on 2008-07-04
hy. I tried to run laptop_mode in a, almost new, core2duo Toshiba Satellite with Ubuntu 8.04. Here's my lspci:

> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


I just don't work. Nothing happens (except for a few bug in the first reboot). Thank's anyway.

---

### Post by hihihi on 2008-07-04
> **sergiom99 said:**
> If I applied the ugly fix for the hdd Load_Cycle_Count issue, would it still work with laptop-mode enabled?
I dont want my drive parking heads every other second.

Thanks for the tuto.



hello sergiom99,

first of all, my laptop (sony fz31m) doesn't seem to be affected by this hdd-killer-problem. So wasn't my old laptop (jewel 2600).

On AC-power the disk never spins down. There is are no clicks really, all OK.

smartctl confirms that:
Load_Cycle_Count didn't really change in the last 90min.
I got an evarage of 35 Load_Cycle_Counts per hour.

The same case when on BATT-power:
if I don't enable laptop_mode, the disk stays on forever,
but then the battery-life-time is very short. 
After 1h something the battery is empty.

Enabling laptop_mode, battery-life-time increases remarkably to around 2h 30min, doing normal stuff, like browsing, writing / reading documents, e-mails, editing fotos, etc... which is good.
It spins down the HDD after a certain amount of time, which can be set in laptop-mode.conf
Spinning down the disk is very good for laptop-users who are on battery.
Laptop-disks are built for this and can take more Load_Cycle_Counts than desktop-disks: 
[http://samwel.tk/laptop_mode/faq](http://samwel.tk/laptop_mode/faq)

Some drives override the idle timeout setting (hdparm -S) when you also set an aggressive power management level (hdparm -B). Set
CONTROL_HD_POWERMGMT=0 (supported from version 1.07) to stop laptop mode tools from fiddling with the HD power management setting.[/QUOTE]

By default, laptop_mode is not active when on AC-power and so my laptop's disk never spins down once connected to the power-supply-plug, -> O.K.

Note that under Windows, your laptop will behave similar once you pull off the power-plug; when it switches over to battery, the disk will spin down and up once in a while, unlike on AC-power.

So, to be honest, I have been following that thread out of curiosity, did check if I was affected, but as I am clearly not affected, I do not know and dare not to tell you, what might happen if you already applied that ugly-fix (which one?) and afterwards you do enable laptop_mode.
If you want to know, you might try it out (at your own risk :))
Afterwards, on AC-power, you do the checks with smartctl.
If then your Load_Cycle_Counts are like after your ugly-fix, that's fine, if not, you could try this ([http://samwel.tk/laptop_mode/faq):](http://samwel.tk/laptop_mode/faq):)
> *Some drives override the idle timeout setting (hdparm -S) when you also set an aggressive power management level (hdparm -B).* 
Set CONTROL_HD_POWERMGMT=0 (supported from version 1.07) to stop laptop mode tools from fiddling with the HD power management setting.

OR

you can always disable laptop_mode like this:
$ sudo gedit /etc/default/acpi-support

set line &#8220;ENABLE_LAPTOP_MODE&#8221; to &#8220;false&#8221;

If you feel like testing:
could you please post the results?
but please keep in mind that this is outside of my experience and to consult more on this, you might want to check the web first!

Some people stated, that by just enabling laptop_mode and configuring the HDD-behavior under AC/BATT in laptop-mode.conf was enough to solve the HDD-killer-problem and did not require the use of that "ugly-fix".
What works for one, does not always work for others.

I hope this helps ~
cheers

---

### Post by hihihi on 2008-07-04
to your first post:

> off by default as it causes odd
# hangs on some machines

check out this ([http://samwel.tk/laptop_mode/packages/ubuntu):](http://samwel.tk/laptop_mode/packages/ubuntu):)

> Ubuntu has a laptop-mode-tools package, which is installed by default on laptops. However, laptop mode is disabled by default in Ubuntu Edgy (6.10), because some people have been experiencing hangups with it on certain laptops (mostly Thinkpads). Until now, nobody has any clue what is happening here. To reenable laptop mode, edit /etc/default/acpi-support and set ENABLE_LAPTOP_MODE=true.


to your second post:

> ...I tried to run laptop_mode in a, almost new, core2duo Toshiba Satellite with Ubuntu 8.04. Here's my lspci:{...}
I just don't work. Nothing happens (except for a few bug in the first reboot). Thank's anyway.

what exactly did / didn't happen?
and what are the bugs in the first reboot like?

---

### Post by sergiom99 on 2008-07-05
thanks for your answer dude. 
I'll keep reading and searching and maybe do the test.

---

