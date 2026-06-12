---
title: "Battery is working, but not charging."
date: 2013-12-25
forum: Hardware
---

### Post by mistermagio on 2013-12-25
Hi, 

I've recently bought an Asus UX301LA, and after a bit of trouble with UEFI, I managed to install Ubuntu 13.10 on it, getting rid of Windows 8 in the process.

Everything worked fine out of the box, except for the battery.

I don't know if it was charging when I was running Windows, as it was plugged most of the time at that point. I don't know if it ever charged while it was on Ubuntu either, all I know is that it doesn't charge anymore, and hasn't done so for the past 4 days. It doesn't charge when I'm running Ubuntu, it doesn't charge when the laptop is turned off, and it doesn't charge when I'm in the BIOS.

It isn't discharging when plugged in either, I've only lost 2% of charge in those 4 days, part of those caused by numerous tries to get the battery to charge by plugging/unplugging. The Laptop is working perfectly fine unplugged, by the way, so the battery is detected, and somewhat working.
So I'm stuck at around 60% capacity as it is now.

When I used upower to get info on the battery, while plugged in, I got the following as a result:

```
native-path:          BAT0  vendor:               ASUSTeK
  model:                UX301-4
  power supply:         yes
  updated:              mer 25 déc 2013 14:50:26 CET (3 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    energy:              28,76 Wh
    energy-empty:        0 Wh
    energy-full:         47,53 Wh
    energy-full-design:  50,616 Wh
    energy-rate:         6,87 W
    voltage:             11,1 V
    time to full:        2,7 hours
    percentage:          60%
    capacity:            93,9031%
    technology:          lithium-ion



```

So the battery status according to upower is "charging", even though it isn't charging at all.

As for what upower has to tell me about the AC, here it is:

```
  native-path:          AC0  power supply:         yes
  updated:              mer 25 déc 2013 14:29:51 CET (1798 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    online:             yes

```

ACPI, on the other hand gave me the following:

```
Battery 0: Unknown, 60%


```

So contrary to upower, ACPI seems to know something isn't exactly working properly, but it's still not telling me what.

I am aware that it might be a circuitry issue, in which case I'd have no choice but to send it back to Asus, and quite frankly, this forum is not far from being my last hope to avoid doing so. 

I hope you guys will be able to help me.

Cordially, 

Lepaffe Philippe.

---

### Post by mistermagio on 2013-12-25
Up.

I know self bumping my thread after only a few hours is a bit obnoxious, but as this issue is really urgent, I'll do it anyway.

---

### Post by fissledizzle on 2013-12-26
As mentionned in an earlier threat of mine I encounter the same problen on my Lenovo IdeaPad Yoga 11s @ Ubuntu 13.10 (but also observed with 12.04): The battery would not charge beyond 59% (the Power Statistics Deice History of upower also stops tracking any charge data when 59% is reached). The problem might thus not be device specific (I'll try to finde out what our machines have in common).

With Win8 charging went without problem to 100%.

---

### Post by mistermagio on 2013-12-26
Do you mean that if you're under 59%, it charges? Because mine doesn't do that, or if it does I haven't reached that max charge yet, and am just slowly decreasing towards it.

Currently sitting at 59%, down 1% from yesterday.

I'd gladly try it out with Windows, unfortunately I got rid of it entirely, and have not been able to boot on a Windows USB, it keeps ****ing up for some reason. I'm not really trying hard either, as I strongly believe that if Ubuntu was at fault, it would charge perfectly when the computer is turned off. I did try with another distrib liveUSB, too.

Unless someone around here has an idea, my options are narrowed to finding a torx screwdriver and look at it from the inside, and if that fails, calling out to dear old Asus, which clearly isn't the most convenient of solutions.

So I really hope someone has an idea I could try out.

---

### Post by mistermagio on 2013-12-27
So, latest devellopment to my battery doing whatever it pleases, it has started charging again, for reasons entirely unknown to me.

I'm still running Ubuntu 13.10, haven't updated anything.

Only thing I did is boot on a Windows 8.1 install USB, didn't install anything, waited 7 minutes looking at it, just to see if it charged, then rebooted on Ubuntu to see if it had charged, and no, it was still sitting at 59% like it was before. At that point I was on the verge of going mad.

But then it started charging at a steady rate. Now sitting at 69%, up 10% compared to 10 minutes ago, and still going up.

Had to pinch myself to see if I was actually dreaming, because I have litterally no idea what happened right now.

Checked in the terminal to see what ACPI had to say about it, and indeed it says it's working:

```
Battery 0: Charging, 71%, 00:33:36 until charged
```

So yeah, I don't know if I should mark this as solved, as nothing was actually solved, magic just happened, but I'll definitely be keeping that Windows USB around in case I need magic to happen again. 

There, 73% now, as I finish typing this message.

---

### Post by aceat64 on 2014-01-02
I also have a ux301la that will not charge. I contacted Asus Support and they suggested I get a replacement via Amazon (I had just ordered it). I was running a dual boot system and the issue persisted when booted into Windows 8, so I do not believe this is strictly a software issue.

My replacement laptop is having the same issue, but I don't have a Windows 8 partition to test with this time.

When plugged in the status is "Unknown". I got down to 1% battery life but was finally able to charge the system when it was turned off. I'm unsure if this is due to it being completely out of power or if there was some series of steps that allowed it to charge. It charged to 100% while turned off, but now that I have it on and running it refuses to charge. It is currently at 83% and falling. I'm going to wait until about 50% and then try charging while turned off.

---

### Post by aceat64 on 2014-01-02
I have discovered a workaround.

1. Unplug the laptop
2. Hold power button until the laptop powers down
3. Plug in the power cord, the connector should stay amber. If it flashes amber/green it's not charging.

I left the cord plugged in and booted into Ubuntu, /sys/class/power_supply/BAT0/status now shows "Charging". I have restarted the laptop and the battery appears to be charging without issue now. There may be some kind of trigger, perhaps when the laptop is suspended. I'll have to test some more.

---

### Post by aceat64 on 2014-01-03
In case anyone with a ux301la is still following this thread, after forcing the laptop to power off the issue has not recurred. So this appears to be a semi-permanent fix.

---

### Post by mistermagio on 2014-01-18
Your workaround definitely sounds better than mine !

I'll try that out if that issue comes up again. I also noticed that in my case, the times when it started blinking amber/green, and in consequence stopped charging, are after a boot with the fans at full speed, this seems to be what's starting the issue. 

And here I thought computers were supposed to act logically...

---

### Post by unixpcguy on 2014-01-18
Well your BIOS was geared for Windows 8. It sounds to me like an Ubuntu glitch. It always will behave differently when switch to a non Windows environment. I discovered Windows logic is slightly different than Ubuntu logic.

---

### Post by mistermagio on 2014-01-19
> **unixpcguy said:**
> Well your BIOS was geared for Windows 8. It sounds to me like an Ubuntu glitch. It always will behave differently when switch to a non Windows environment. I discovered Windows logic is slightly different than Ubuntu logic.

The only thing that I don't understand is that it doesn't charge when it's turned off completely, or in the BIOS. And it does sometimes work properly while running Ubuntu. It doesn't make much sense to me...

---

### Post by pantale on 2014-01-31
I have exactly the same issue as you. Sometimes, when booting, fan goes full speed and problem occurs : unable to charge when plugged.
I have to unplug power AC, press power button until full power off (10 s). The plug the power cord again and reboot... Gone !!!

---

### Post by kifer on 2014-02-14
> **aceat64 said:**
> In case anyone with a ux301la is still following this thread, after forcing the laptop to power off the issue has not recurred. So this appears to be a semi-permanent fix.

This is not a permanent solution in my case. This problem seems to have something to do with suspension while on battery power.  To make it charge again, I have to press and hold the power button: a regular shutdown doesn't help. This restores the charging action, but the issue comes back from time to time.

---

### Post by joe71 on 2014-02-15
I've had my UX301LA since early December and running 13.10 about as long.  Never had this problem before and just ran into it today.  Thanks to this thread I was able to recover it.

My symptoms were that I left the laptop on with low charge (Ubuntu had already warned me) and came back to a dead laptop.  No big deal - plugged it in and got the amber/green flashing.  Uh oh.

Since my battery was completely dead I was unable to "unplug AC and shutdown with the power button" because it would die immediately when I removed AC.  Luckily booting into 13.10 and then just holding down the power (while still on AC) to forcibly shut it down worked for me.  Hoping this helps someone else out.

Also, unsure if it's related - but in the off chance that it is - I am running with the following extra kernel options - found these while I was trying to get my brightness keys working (which the acpi_osi setting does) but the rest of them I just grabbed:
acpi_osi= add_efi_memmap i915.i915_enable_rc6=1 pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1

---

### Post by Foalyfr on 2014-02-25
Hi everyone,

I just wanted to say thanks for the tip provided by aceat64, because it seems to work (at least for now, but I guess I will just have to do it again if it happens again), and I was feeling really bad about this problem.

In case this is of importance for someone to understand what causes this issue, I am running an UX301LA-DE022H with Mint 16 (it's not Ubuntu, but I guess it's quite close). During the first two weeks, the blinking and the "crash then powering up with fans at full speed" things happened a few times but every time a reboot and an unplug/plug back fixed it. Then it became permanent and the battery refused to charge (acpi said it was charging, but it was stuck at 46% for 3 days). I called asus, they told me to send it back for repair, and they changed the motherboard. I got it back yesterday working fine, but it has started to do it again 1 hour ago.
So, to sum up :
- also happening with Mint
- asus didn't seem to be aware of this problem since they assumed the motherboard was faulty (they reformated the disk with a Win8 though, but I guess that's classic procedure)
- sending it back for repair doesn't change anything

---

### Post by Thomas_Raleigh on 2014-02-26
I just wanted to throw in that my UX301LA-DH71T (purchased early Feb 2014) has had the same issue on both Arch and a bootable USB running Mint (I think Mint 14, Debian Edition). When it's not charging, acpi reports the battery state as unknown. The issue went away temporarily (machine charged to full, acpi reported state properly) after the machine crashed, and had to be powered down by holding the power button - the issue came back, likely after closing the lid. The first time the issue occurred, the power adapter flashed green and orange, though at the moment, it's stable at green, but not charging (xfce notifications show it as fully charged, but acpi reports the state as unknown). I've also occasionally had the issue with the fan running at full power on boot.

Perhaps unrelated, but I've also occasionally had issues with the wi-fi connecting and disconnecting. Other than that, everything's worked well.

I've contacted ASUS, and they've asked me to send the machine back for repair, but I'm a bit hesitant, since I can't afford to go without it for too long, and, judging from comments on here, it doesn't look like it will resolve the issue.

Edit: It's charging again, without having done a reboot. I'm absolutely confounded, but at least the issue is intermittent.

---

### Post by pantale on 2014-03-07
Here is an extract of the syslog when battery problem occurs. From this, seems to be an ACPI related problem while not finding the battery.

Mar  6 21:25:14 pantale-UX301 kernel: [    0.630565] ACPI Exception: AE_AML_BUFFER_LIMIT, Index (0x0000000CD) is beyond end of object (length 0x20) (20130517/exoparg2-420)
Mar  6 21:25:14 pantale-UX301 kernel: [    0.630571] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BIF9] (Node ffff8802134bbcd0), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
Mar  6 21:25:14 pantale-UX301 kernel: [    0.630576] ACPI Error: Method parse/execution failed [\_SB_.PCI0.BAT0._BIF] (Node ffff8802134bb9d8), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
Mar  6 21:25:14 pantale-UX301 kernel: [    0.630580] ACPI Error: Method parse/execution failed [\_SB_.PCI0.BAT0._BIX] (Node ffff8802134bba78), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
Mar  6 21:25:14 pantale-UX301 kernel: [    0.630584] ACPI Exception: AE_AML_BUFFER_LIMIT, Evaluating _BIX (20130517/battery-444)

On the other hand, here after is the same part of the syslog file when everything is OK:
Mar  6 21:26:21 pantale-UX301 kernel: [    0.608040] ACPI: Battery Slot [BAT0] (battery present)


Olivier

---

### Post by Erik_Pearson on 2014-03-10
Registered to throw this in here. I would like to add my UX301L to this mix. Had it about 4 days now. Charged to full right out of the box, Installed Linux Mint 16 on it, and it refused to recharge after that. Booting it up, then hard shutting down (holding power button) seemed to work. 

I too would get the green/amber flashing light on the power cord plugged in or not. 

I'm about 90% sure its a "microsoft hates linux" problem with UEFI crap not getting along with Linux. Think of UEFI as a mini-os stuck between the hardware firmware and the OS. [COLOR=#000000][FONT=sans-serif]Support for GPT in [/FONT][/COLOR][Linux]("http://en.wikipedia.org/wiki/Linux")[COLOR=#000000][FONT=sans-serif] is enabled by turning on the option [/FONT][/COLOR]CONFIG_EFI_PARTITION[COLOR=#000000][FONT=sans-serif] (EFI GUID Partition Support) during kernel configuration.[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]This option allows Linux to recognize and use GPT disks [/FONT][/COLOR]*after the system firmware passes control over the system to Linux.  *If this pass of control doesn't happen, its quite possible that UEFI will not correctly (or at all) pass correct hardware info or control to the OS. 

I know this deals primarily with disk boot sizes, but if you read up on how UEFI works, its a Microsoft baby, and seems to support FAT file systems. 

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Foalyfr on 2014-03-25
I don't know if it's the same for you, but for me for the past few weeks the problem had become about the constant crashes which were more rare before (on the average I could run it for about 30 minutes before it crashed). Even the low-level sysrq keys didn't work (yes, I enabled them), and I read that the only possibilities for this were a kernel panic or a hardware failure, like overheating. I tried to make it crash with tty1 displayed to see the potential kernel panic, without success.
After that, I tried with many different ACPI settings, and with acpi=off as a kernel parameter it didn't seem to crash, although it crashed with the other settings. Either I was "lucky" with acpi=off, or acpi is actually the cause of the issue. The acpi diagnostic tool (can't remember its name) detected many critical errors with the firmware, but it was the same on a friend's another asus laptop which was working fine, so I don't really know.
Since Mint is based on Ubuntu I thought it was caused by the Ubuntu code somehow, so I tried the Linux Mint Debian Edition, but... I couldn't even reach the installer on my usb live before it crashed, so I guess the problem goes back up to every debian-based distribution.
Finally, feeling quite depressed about having an expensive sport car with its engine stalling every few miles, I decided to try something completely different and spent a few hours to give Arch a shot. And... **it works**! I have been using it for a week now, I spent quite some time installing everything but I now have a system perfectly stable and even faster than before. I even managed to install Cinnamon so it really looks like my previous Mint.

So, if you are bored with the problems with this laptop and don't mind getting your hands dirty, give Arch a shot, it's a good training and the wiki is really well written.

[Sorry for the language mistakes, I'm very tired, but I hope my experience still helps someone]

---

### Post by freeman2 on 2014-04-14
I just wanted to add my story here. Same stuff: ux301la, ubuntu, usually (always?) fails after ubuntu booted with fan at max speed, or when trouble occurred relatively with suspend or hibernate. 
Workaround with hard sutdown works also.
I had the battery replaced once and the motherboard with cpu and ram changed by the warranty service (which is otherwise good).
I can't remember having this issue while using windows 8 but cant be certain about this.
Once it came out of suspend or hibernation by itself while I had it in its slip cover and in my backpack. I noticed my back was unusually hot an the laptop was blazing hot when I pulled it out, but still on.
Anyway, I hope a fix will be issued soon cause it is otherwise a real joy of a laptop with ubuntu.

---

### Post by aeyeaws on 2014-04-14
lol this is a battery problem, you need to discharge completely and then charge the battery. thers a bunch of tricks to try to get capacity back just google restoring a laptop battery. charge discharge put in freezer lol blabla. nicads and lithium ion batterys only last 3 years then they loose capacity, its the big problem with electric cars, you need new batteries after 4 years for 26,000 dollars.

---

### Post by kifer on 2014-05-08
Upgrade the BIOS to version 206 and everything will be fine. This upgrade also solves some other problems, like fan racing.

---

### Post by solvemon on 2014-05-11
I had a similar problem with my HP ProBook 5330m with Ubuntu 14.04 that started just today. I was using the laptop unplugged for a while, until it had 4% battery left. I then plugged in the cord, but it took a while before I noticed it hadnt charged. I tried turning it off to see if it helped, but after starting it an hour later it still hadnt charged past 4%. I also noticed that the charge/power led right next to my connector was flashing amber.

**My solution:** I followed the instructions here: [http://h30434.www3.hp.com/t5/Notebook-Hardware/charging-light-blinking-problem-with-hp-probook-4530s-edited/m-p/1404957#M69267](http://h30434.www3.hp.com/t5/Notebook-Hardware/charging-light-blinking-problem-with-hp-probook-4530s-edited/m-p/1404957#M69267)[INDENT]
[/INDENT]
> [COLOR=#000000][FONT=HPRegular]1-turn off the notebook[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]2-remove the battery[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]3-remove the charging adapter[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]4-Now press and hold the power button for 40 seconds(it will discharge the capacitors)[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]5-now insert the charging adapter only(dont insert the battery)[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]6-now press the power button[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]7-let the windows load and then shutdown it[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]8-now insert the battery and press the power button[/FONT][/COLOR][COLOR=#000000][FONT=HPRegular]
[/FONT][/COLOR]

[COLOR=#000000][FONT=HPRegular]and my laptop is now charging again! Since I only did this about half an hour ago I cant speak for the long-term results, but for now it seems good at least.[/FONT][/COLOR]

---

### Post by mistermagio on 2014-06-09
I saw that there was a new version of the BIOS, wondered if it helped...

Is the process entirely safe though? Or should I make backups?

I'd take whatever risk willingly if I still encountered the problem often, but it's been more than a month since I had any issue with my Zenbook...

---

### Post by Rainer_Piqual on 2014-06-28
Do a back up first.

---

### Post by a_m on 2014-07-01
Hi, I just wanted to tell that I am having the same issues with my brand new UX301LA: after noticing, this morning, that the fan was racing full speed (something I had never noticed before - this zenbook is just a couple of weeks old), I noticed also that the charger was blinking green/orange and the battery was not charging at all. 
I was pretty scared because, like mistermagio, I got rid of Windows (I am running Ubuntu 14.04) and I believe that having entirely removed Windows I have lost the warranty (I am not sure about that, but I hope not to have to find it out!). However, after reading this thread I forced a shutdown holding down the power button for 10s or so and now the battery is charging again. Thank you guys!

---

### Post by tehownt on 2014-09-13
> **pantale said:**
> Here is an extract of the syslog when battery problem occurs. From this, seems to be an ACPI related problem while not finding the battery.

Mar  6 21:25:14 pantale-UX301 kernel: [    0.630565] ACPI Exception: AE_AML_BUFFER_LIMIT, Index (0x0000000CD) is beyond end of object (length 0x20) (20130517/exoparg2-420)
Mar  6 21:25:14 pantale-UX301 kernel: [    0.630571] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BIF9] (Node ffff8802134bbcd0), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
Mar  6 21:25:14 pantale-UX301 kernel: [    0.630576] ACPI Error: Method parse/execution failed [\_SB_.PCI0.BAT0._BIF] (Node ffff8802134bb9d8), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
Mar  6 21:25:14 pantale-UX301 kernel: [    0.630580] ACPI Error: Method parse/execution failed [\_SB_.PCI0.BAT0._BIX] (Node ffff8802134bba78), AE_AML_BUFFER_LIMIT (20130517/psparse-536)
Mar  6 21:25:14 pantale-UX301 kernel: [    0.630584] ACPI Exception: AE_AML_BUFFER_LIMIT, Evaluating _BIX (20130517/battery-444)

On the other hand, here after is the same part of the syslog file when everything is OK:
Mar  6 21:26:21 pantale-UX301 kernel: [    0.608040] ACPI: Battery Slot [BAT0] (battery present)


I have the exact same issue and the same message in syslogs. Bugs need to be opened I gues...

---

### Post by Manwel on 2014-12-13
Just wanted to add to the discussion although I am not a Ubuntu user. I've had my Asus Zenbook UX301LA for 5 months now and never ran into any problems with Windows 8.1. When I received it I made sure I upgraded with all the latest drivers, firmwares and bios (v.209) so I wasn't running later on with a known issue.
And two weeks ago I came across the same issue being discussed in this thread...
Suddenly, while I was working on battery, the laptop suddenly shut down without warning and screen went black. I waited a few seconds and powered it up again, but only to see the same thing happening a few minutes later. I then plugged it with the charger and powered it up again.
Windows was now reporting that there was "no battery detected" and then "unknown remaining" and again "0% available, plugged in, charging"...
So I'm not sure what is going on, I was thinking to send it back for repair to Asus but after reading this discussion it doesn't seem that it's going to solve anything. I added this reply to the discussion just to let know all the UX301 owners that this battery issue doesn't seem to be Ubuntu related but more a hardware issue potentially affecting all operating systems.

Not sure Asus is aware of that issue...

---

### Post by cbplummerguy on 2014-12-13
I have a similar problem, and so far have been unable to find an answering post....  I have a Dell Inspiron 15-3537 laptop for which I'm now on the THIRD battery since upgrading to Ubuntu 14.04 LTS.  The battery works, but simply discharges... never charges.  The laptop isn't all that old, so it was strange when the first battery died, seemingly prematurely.  The second battery would not charge... so I presumed it was bad and ordered a new one from another vendor.  SAME PROBLEM!  I've seen some posts with something about editing the GRUB file; however, the info on how to do that is beyond this noob... couldn't tell whether the instructions contained the full syntax for a new-line, or if I was supposed to edit some other line... and of course, there was a warning in the GRUB file... "DO NOT EDIT THIS FILE"...

Battery Statistics say the battery is "charging"; however, the rate is 0.0W.  The Voltage is 11.2 V, the max and designed capacity is: 48.8 Wh, and the current energy is: 32.9 Wh. 


Everything ran very well under UBUNTO 12.04 LTS...

---

### Post by hadimm on 2015-01-11
Any news on this issue ? I just bought an Asus Zenbook UX310LA DE0002H and I am now stuck at 95% of battery. It does not charge when it's plugged (however it does not seems to discharge neither).

Some info about my system:

> $ cat  /sys/class/power_supply/BAT0/status
Discharging

$ cat /etc/lsb-release 
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=17.1
DISTRIB_CODENAME=rebecca
DISTRIB_DESCRIPTION="Linux Mint 17.1 Rebecca"

$ uname -a
Linux boromir 3.16.0-28-generic #38-Ubuntu SMP Sat Dec 13 16:13:28 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ sudo dmidecode -s bios-version && sudo dmidecode -s bios-release-date
UX301LAA.209
05/08/2014


Note that the trick to unplugged -> hard shutdown -> plug -> reboot does not work for me...

Any help would be really appreciated !!!

Thanks

---

### Post by Bozoo on 2015-09-14
I just installed Ubuntu 15.04 on a UX301LA and the battery does not charge ( I get stuck at 98 % and the LED remains green on the charger ... what now? )

---

### Post by guilherme17 on 2016-05-18
[HR][/HR]Well, I have a Asus S400CA and mine suddenly starts with this problem last night (dont know what just happened).
 I have ubuntu 15.10 installed alongside windows 10 and the problem happens in both systems, when i plug the ac adapter the icon of battery starts blinking and saying ''battery plugged in not charging''. i've tried pushing and held the power button for more than 1 minute then released it (my finger hurted tho) then plugged the ac adapter after more than 1 minute but didnt powered up the laptop. Well... I saw that when the ac adapter is plugged with energy in the laptop but letting it turned off, the orange led in the case lights up and charges the battery until 100% (when the laptop is powered off only), but when i power on the laptop.. the orange led starts blinking again, sometimes the light disappears or quickly lights up when i spin on the adapter wire then lights off again.

---

### Post by scunacc on 2016-06-19
I'm having the same problem too. I just installed 16.04 on an Eee PC 701 to bring it back into usable service. It's doing great as a portable little machine for coding on. I have Xfce on it, PostgreSQL, etc. and still have a bunch of room free.

However, I have noticed a couple of things. 

1.) The original battery is reporting its level strangely. It will say this with upower:


eeepc $ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               ASUS
  model:                701
  power supply:         yes
  updated:              Sun 19 Jun 2016 09:43:23 AM EDT (15 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               discharging
    warning-level:       low
    energy:              4.368 Wh
    energy-empty:        0 Wh
    energy-full:         43.68 Wh
    energy-full-design:  43.68 Wh
    energy-rate:         0 W
    voltage:             7.134 V
    percentage:          10%
    capacity:            100%
    technology:          lithium-ion
    icon-name:          'battery-low-symbolic'

and carry on working for two hours even though it's saying only 5% in the battery monitor. 

I bought a new higher capacity battery, 6600 (which *reports* 4400 in acpi ?!?!?), because I thought maybe the battery was on its way out, and the *real* issue I face happens to both.

2.) The ***_real_*** issue is, if I close the lid to suspend it, which it does just fine, then when I plug the power in - either suspended or woken up - it does not charge properly. The orange charging LED does not come on. It just flashes.

I've gone the capacitor discharge route several times now, and that fixed it *most* of the time, but yesterday did not. I just left it plugged in, and *eventually* the charging light came on. This morning it's fully charged, but, on the other occasions when that's happened it would not charge and I had to do the unplug, hold the power, reboot, power off, reinsert battery route before it would again.

It does seem to be something to do with suspending it.

Also, I've noticed that when just plugging in the power, when it's *not* working, I get a faint "tick tick tick tick" noise from the MB. (This unit has a 4GB SSD, so not a hard disk issue), and it's not the fan - that's working properly. It's not near the charging circuit, but seems to be almost dead center of the MB (I listened without the memory in too) so I don't think a leaky cap, and I don't want to disassemble this to do any further poking around. It's a messy and fiddly disassembly. 

Any other thoughts? Solutions?

(I also have a new PSU on the way as well, JIC there's an issue with that, but it does seem to be suspend related.)

---

### Post by scunacc on 2016-06-30
Replying to my comment above :-) Looks like it was the PSU in my case. Picked up a replacement PSU from Amazon and immediately I plugged it in I got a solid orange power LED and things seem to be charging nicely.

Kind regards

Derek.

---

