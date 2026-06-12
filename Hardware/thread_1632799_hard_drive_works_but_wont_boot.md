---
title: "hard drive works but wont boot"
date: 2010-11-28
forum: Hardware
---

### Post by old.purple on 2010-11-28
Toshiba A65-S1068
BIOS v. 1.9 ACPI
OS Ubuntu 10.10

Backstory:

Laptop hard drive died over a year ago. Since it was old and slow anyway, I simply stuck it in a closet. Recently purchased and installed a new hard drive (same make and model the machine came with originally) . 

Problem: Although, the hard drive is working, computer wont boot from hard drive. Works fine from Live CD.

Ubuntu successfully installed on hard drive (ext3/ext4). The drive mounts, reads, writes and all tests indicate it is working properly. Although the BIOS is set to boot from HDD first, it instead behaves as though the hard drive is not installed and attempts to boot from CD... which is odd considering that once up and running from Live CD the hard drive is clearly mounted and working.

No error msg regarding the hard drive is thrown at boot time. Instead, it is simply ignored. On inspection of BIOS settings, it indicates that "HDD=Not Installed". There is no option to alter this information.

Solutions Attempted: 

The BIOS has no option for loading default settings. I have flashed the BIOS with the latest version (also 1.9) in an attempt to have it recognize its hard drive. No effect.

Checked hard drive... has no jumpers.

Questions: 

Is there a way to force the BIOS to recognize the hard drive? (I realize that that is not an Ubuntu question, really).

Is there a way to create a CD that boots a menu that allows me to load the OS from the hard drive? This is just a workaround, but if the BIOS refuses to cooperate, at least this would get it going.

Any help or ideas would be appreciated.

Please note: Although I am computer literate, I do not speak Linux... please phrase any replies as simply and clearly as possible. Thanks.

---

### Post by oldfred on 2010-11-28
Do you have any of these settings?

BIOS should be set for IDE compatibility mode
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 

Usually Ubuntu will not see a drive that BIOS does not see.

Can you boot USB flash drives. That is often easier to use. I have a Toshiba A105 and it boots flash drives.

There is the plop boot manager or you can create a grub2 boot CD. 

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

### Post by old.purple on 2010-11-28
> **oldfred said:**
> Do you have any of these settings?

BIOS should be set for IDE compatibility mode
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 

Usually Ubuntu will not see a drive that BIOS does not see.


Yes... weird problem, huh? I have none of those mode settings.

In BIOS, under Peripheral, I have "Hard Drive = Not Used" This is simply displayed, it does not have any options to change the setting.

Under Boot Priority I have "HDD -> FDD -> CD-ROM" The order of this is changeable

Under Drives I/O I have "Built in HDD = No Drive" This cannot be directly changed.

I am used to BIOS settings such as the ones you discuss... this one has very little that I can change.

> 

Can you boot USB flash drives. That is often easier to use. I have a Toshiba A105 and it boots flash drives.

There is the plop boot manager or you can create a grub2 boot CD. 

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")I have never booted this machine from a USB flash drive, however, I will try that later this week... (all of my sticks are at work!!!) it has a setting called USB - FDD Legacy Emulation, so perhaps that will allow me to boot from a stick... but I would still like to get the BIOS to function correctly!

So... is it possible to boot it on a stick or CD with a boot loader, and from there switch it to the hard drive?

---

### Post by oldfred on 2010-11-28
I only have looked at plop's site and a few users have commented that it worked. I believe it will boot from just about anything.

Grub2 now is just about the same way. I have my Flash drives set up with grub2 and one boots ISO directly (loopmount), the other is a full install and I have added a few extra entries for booting my hard drives from the flash. I was going to follow Herman's info on CD's and do the same just to learn how to do it but have not got round2it.

On my desktop I have many USB boot devices one listed as USB-HDD. But my flash would not boot from any of them. I gave up but then tested on my Toshiba laptop and it booted so I knew I had it set up correctly. Later I had it plugged into my desktop but was selecting a different hard drive and there was my flash (and it worked). It was a hard drive not a USB device.

---

### Post by old.purple on 2010-12-30
Update:

Attempted to boot with Plop... this caused Toshiba to lock up. Removed HD and placed it in a USB enclosure (because I believe that the bus between the HD and the motherboard was damaged when the original hard drive suffered mechanical failure). Again computer hangs. Changed Plop settings to force USB 1.1, and now the screen goes black, as though it is about to switch to (now) external hard drive, but it simply sits there doing nothing.

Since the hard drive is usable (and Puppy Linux is running on it right now), it seems to me that if I could boot from the CD and switch_root to the HD (whether external or internal) I would be able to use Ubuntu. I simply dont have the skill to create the needed script, or create the ISO for the CD.

I will keep trying... Puppy Linux is great, but Ubuntu is super awesome.

---

