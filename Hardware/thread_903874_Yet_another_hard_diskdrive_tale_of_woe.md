---
title: "Yet another hard diskdrive tale of woe"
date: 2008-08-28
forum: Hardware
---

### Post by superbiskit on 2008-08-28
[I see other "HDD not recognized" posts, but this part of my problem involves the BIOS -- and that I don't see]

Mainboard: MSI K7N2-Delta, nVidia chipset, AthlonXP1800
BIOS: Phoenix AwardBIOS W6750MS V5.1 041803 18:12:13
IDE0 Master

If I boot cold, after the machine sat overnight, I boot to a blank screen.  If I go back and get into BIOS-SETUP, the disk is described as
"WDC WD1600".  It just will not boot that way!
By the way, there is a scary sequence of click-pause-click-pause noises during the POST early-boot time period.

After needlessly re-installing Ubuntu a few times, I stumbled upon a trick.
If I _momentarily_ power-down/power-up, there are fewer click-pause events and the BIOS-SETUP now shows
"MDT MD11600JB-006VA0".  And now, when I exit Setup, it boots into GRUB and everything is cool for the day.

It is possible to re-boot.  I don't need to do all the power-button tricks.  And there isn't any click-pause.

Two obvious possibilities: the disk -- which is new to me, but not brand spanking new from the factory -- is on its way out.  That won't make me very happy, but the solution is only money.

Or, the BIOS is too old (2003?) to know what to do with the disk.  I could probably get a BIOS update from Phoenix, but all of their tools are Windoze-only and I don't play that game. 

OpenBIOS looks interesting, but it isn't obvious that it's a complete solution or that it works for the ia32 architecture.  That's apart from the question of turning my 'puter into a doorstop.

---

### Post by kspncr on 2008-08-28
I don't like the sound of that clicking. That is not a good sound. I can only wager a guess here, but I think your hard drive might be dying. I hope I'm wrong.

---

### Post by superbiskit on 2008-08-28
> **kspncr said:**
> I don't like the sound of that clicking. That is not a good sound. I can only wager a guess here, but I think your hard drive might be dying. I hope I'm wrong.

Sad to say, I suspect you are right.  That might also explain why the disk cannot decide what ID-string to send to the BIOS during startup.

For anyone interested, I'm appending the outputs of various reporting tools.

---

### Post by superbiskit on 2008-08-28
fdisk, lshw, lspci, hwinfo outputs attached.

---

