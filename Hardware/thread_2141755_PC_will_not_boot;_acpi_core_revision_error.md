---
title: "PC will not boot; acpi core revision error"
date: 2013-05-03
forum: Hardware
---

### Post by kjetilon on 2013-05-03
Hi!
I am having trouble booting my PC.

**Hardware: **
[LIST]
[*][COLOR=#000000][FONT=Arial]In-Win BQ660 Mini-ITX[/FONT][/COLOR]
[*][SIZE=2]MSI FM2-A75IA-E53, Socket-FM2
[/SIZE]
[*][SIZE=2]Kingston DDR3 HyperX blu 1600MHz 8GB
[/SIZE]
[*][SIZE=2]AMD A-Series A10-5800K
[/SIZE]
[*][SIZE=2]Kingston HyperX 3K SSD 120GB 2.5"[/SIZE]
[/LIST]
[SIZE=2]
**Problem: **
[/SIZE]Ubuntu (or any other OS) will not boot. The error message acpi core revision is displayed.

**What I have tried (and did not work):**
[LIST]
[*]Booting with acpi=off, nolapic and noapic (if this is applied another message than acpi core revision is displayed)
[*]Disabling acpi from BIOS.
[*]Changing hard drive (with Windows installed), black screen
[*]Booting from a live USB key (no CD room), either Ubuntu, Mint or Windows Vista.
[*]Booting hard drive on another computer. Works fine, so it is not the hard drive.
[*]Upgrading BIOS with never or older version
[*]Resetting CMOS on the motherboard
[/LIST]

I bought and build the computer one week ago. There is nothing wrong with the hardware. The computer worked just fine, except there was no sound over HDMI, so I tried various upgrades. The computer crashed some days ago after I installed something, and the acpi core revision error appeared. After resetting CMOS on the motherboard this was solved. However, sound did still not work, so I continued do try various things. One of the last things I did was uninstall PulseAudio and add "option snd-hda-intel model=3stack" (or 6stack) to alsa-base.conf in modprob. My current theory is that there is an incompatible command that is not deleted or reset when flashing BIOS or resetting CMOS.

Thank you for your help. I am no computer (or Linux) expert so please be kind.

---

### Post by matt_symes on 2013-05-03
Hi

Can you take a photo of the error message as it's displayed and post it here.

It's not an error i have ever come across so i'll be interested in seeing it.

When in the boot sequence are you seeing this error ?

Have you checked to see if there are any BIOS updates for the motherboard ? 

Don't install them yet, just check.

EDIT:

> Booting with acpi=off, nolapic and noapic (if this is applied another message than acpi core revision is displayed)

Please also take a photo of this error message and upload it here.

Kind regards

---

### Post by kjetilon on 2013-05-04
Pictures of the errors are displayed below.
[ATTACH=CONFIG]242160[/ATTACH][ATTACH=CONFIG]242161[/ATTACH][ATTACH=CONFIG]242162[/ATTACH][ATTACH=CONFIG]242163[/ATTACH]

I have already installed a newer version of BIOS and nothing changed. I have read many similar threads about this and in many of them the problem has been solved by adding acpi=off. 

When I turned on the computer today it booted into recovery mode, and after that into Ubuntu. I was able to remove "option snd-hda-intel model=stack3" from alsa-base.conf and update grub. When I rebooted the errors as before appears.

---

### Post by matt_symes on 2013-05-04
Hi

Can you disable ACPI in the BIOS as well as pass the boot line option *acpi=off*. I.E do both at the same time ?

Also try disabling any VT options in the BIOS.

Kind regards

---

