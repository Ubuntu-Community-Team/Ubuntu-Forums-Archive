---
title: "HELP - computer just got bricked"
date: 2015-05-13
forum: Hardware
---

### Post by fr33z0n3r on 2015-05-13
_**How my issue occurred:**_
1. I was working on my (fairly new) desktop computer when the gui locked up.  I was on Hangouts and it continued to pass audio.  
2. I was forced to press REISUB to get it to respond.
3.  Upon that restart, I was unable to decrypt my LVM!
4.  So I powered off and back on.
5.  Computer lights come on but no sounds at all. Now it will not boot to the UEFI BIOS even.  I get no audible codes, and have no LED for codes.
6.  I can boot into the BIOS Maintenance mode via jumper.  And from there I can choose my Ubuntu install to boot from - I got to the initial Ubuntu boot menu and powered off to be safe.

_**Computer:**_
  I have a newer Intel motherboard, DH77EB.
  I recently rebuilt Ubuntu with 14.10 x64 1 month ago and chose to use UEFI boot.  (I used 14.04LTS for over a year without issue)
Have Secure Boot enabled.
I have an encrypted LVM
I had RAID mode enabled in the BIOS - my previous OS config used RAID for some additional HDDs which are now removed.  (forget to switch back to AHCI)

Was there any recent update for Ubuntu related to boot problems like this? I thought I saw a recent update maybe about addressing Intel issues?    I've heard of UEFI leading to bricked devices.

Anyone have any ideas?  

I have to look into doing a BIOS reset right now, but this came out of the blue.  I have to suspect that UEFI is part of the issue.

There was no odd physical behavior going on  - ever with this device.  And I never pushed it very hard (CPU/GPU/memory/SSD).

_**UPDATE**_ - Fixed by resetting the UEFI BIOS to defaults from inside Intel BIOS Maintenance Mode.

---

### Post by fr33z0n3r on 2015-05-13
I just managed to get into my UEFI BIOS via the maintenance mode.  And the speakers works, and USB mouse and keyboard work fine. Obviously the CPU works fine (I think BIOS access proves that), as does memory.  

Any ideas?

---

### Post by Vladlenin5000 on 2015-05-14
Your motherboard has
```
[Intel[SUP]®[/SUP] H77 Express Chipset]("http://www.intel.com/content/www/us/en/chipsets/mainstream-chipsets/chipset-h77.html") with [COLOR=#ff0000]Intel[SUP]®[/SUP] Rapid Storage Technology[/COLOR]
```
Disable the [COLOR=#ff0000]red[/COLOR] feature and try again.

---

### Post by fr33z0n3r on 2015-05-14
Thanks for the idea Vladlenin5000!  So, I could find no way to disable that feature specifically.  I tried changing it from RAID (which I think IS RST) to AHCI but_ it still failed to boot_.  Can you explain your reasoning why you think it is the cause?  I'd be interested in sources.

So I was essentially forced to reset the BIOS to defaults.  And that worked.  Thank the maker!  I was concerned that resetting the UEFI bios would cause Ubuntu boot issues, but it did not.  (I have an encrypted LVM and the 2nd sign of trouble was upon the REISUB reboot, I was unable to decrypt my LVM!!!!)

Updating my first post above in case anyone knows more about a cause.  (you might be right about RST causing an issue ultimately)

There is a BIOS update available and I may be installing that if I can figure out how.

---

