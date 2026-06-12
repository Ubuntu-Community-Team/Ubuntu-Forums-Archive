---
title: "NVIDIA GTX 285M underclocked, can't overclock."
date: 2012-12-27
forum: Hardware
---

### Post by MisteR2 on 2012-12-27
Hello everyone, wanted to see if anyone else here has come across this while trying to do some gaming under Ubuntu.

I've got the aforementioned card in my laptop and I'm finding that I'm unable to get upto proper frequency speed while gaming. No matter what's done (trying to OC the clock to the proper frequency, playing the game itself) the system or driver will not allow the graphics processor to get up. I've run it under Windows and by default, the machine sounds like a harrier trying to take off when under load.

I don't get that under Ubuntu. :) 

So, I've checked over the net and the best I've found is threads started, and some mentioning lines in xorg.conf.d that should be put in, but that has not worked. 

Symptoms of the problem:

The card has four levels in the PowerMizer menu. Out of 0 to 3, it only goes to 1, which is a 275 mhz graphics clock, 301 mhz memory clock and 550 processor clock.

No issues when running Unity, but the only reason I've noticed this is because I wanted to start playing games on this laptop.

Checked on my desktop running 12.10 with twin 9800 GTX+, but there's only two performance levels showing on that nvidia panel.

One thing I'd like to check into is to see what the card thinks it's default frequencies should be. I have yet to find a way to do so.

If anyone has any information or tips on this they would be greatly appreciated!

---

### Post by MisteR2 on 2012-12-28
Looks like some of this might be DSDT related. Already pulled a copy of mine and decompiled it. 

A couple of places where I'll be picking up soon:

[http://www.nvnews.net/vbulletin/showthread.php?p=2478085](http://www.nvnews.net/vbulletin/showthread.php?p=2478085)

[http://en.community.dell.com/support-forums/software-os/f/3525/t/19481239.aspx](http://en.community.dell.com/support-forums/software-os/f/3525/t/19481239.aspx)

---

### Post by MisteR2 on 2012-12-30
Found some info in the dmesg related to this driver:

[   32.223105] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  313.09  Tue Dec  4 21:22:17 PST 2012
[   32.503217] cfg80211: Calling CRDA to update world regulatory domain
[   32.506067] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   32.506077] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   32.506080] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   32.506085] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   32.506092] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \RPGB 2 (20120320/utaddress-251)
[   32.506098] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   32.506107] ACPI Warning: 0x0000000000001180-0x00000000000011ff SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   32.506113] ACPI Warning: 0x0000000000001180-0x00000000000011ff SystemIO conflicts with Region \RPGP 2 (20120320/utaddress-251)
[   32.506120] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

So...
-I'm using 313.09 which appears to be ahead of official. I was having the same issue with 310, so I'm not sure if that's having an effect here

-it looks like the nvidia driver is having issues with ACPI. Now I'm a little unsure if this is something with the DSDT. :D

I'll keep digging. If anyone else who's having this issue sees this in their dmesg, let me know.

EDIT:

Turned on MSI for the nvidia driver, messages still appear. They may not be related. Still going.

---

### Post by MisteR2 on 2012-12-30
Finally taking a break from this. So far going down the DSDT path hasn't given any insight on why this is breaking. I found the two video cards listed in the DSDT which helps, but I'm having trouble tracking down just where the signal is sent saying what power level it should be at.

On that note, after digging into the ACPI docs availalble on the net, I'm really unsure if this is controlled in ACPI. Most of the stuff that I had read indicated there were four power states that were generally dealt with... I think D0 to D3 and the two in between generally weren't used. 

After putting that aside, I tried banging on the driver to see if that would do anything to get this to go past 275mhz on the core frequency. After trying to set up MSI (successful) and trying to force maximum performance on the driver (successful only to performance level 2 out of 4), my brain is a bit baked. :)

I've checked to see what the maximum frequency is for the card according to what nvidia-settings sees, and it's seeing what it should be which is 600 core, 1020 memory, 1500-something for processor clock. But it just won't touch it. Dunno why yet.

---

