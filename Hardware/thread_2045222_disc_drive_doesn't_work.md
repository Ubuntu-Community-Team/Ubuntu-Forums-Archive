---
title: "disc drive doesn't work"
date: 2012-08-20
forum: Hardware
---

### Post by spencerownside on 2012-08-20
Hi all - I've had a long-standing problem with the disc drive on my acer aspire timeline X laptop. The disc drive doesn't work - at all. No response no matter what and it has been this way through the ubuntu 12 system upgrades. When I hit the eject button on the laptop there is no response from the laptop and if i use the "alt + E" key shortcut, nothing happens there either. 
I had kind of hoped that one of the updates would have a patch or something but nothing has worked and I would like to use my drive. 
While I'm not new to ubuntu, I'm not an expert with terminal code so don't hate me too much if i ask some stupid questions. 
Who has some ideas on my first couple steps please?

---

### Post by spjackson on 2012-08-29
If you press the eject button the second you turn the laptop on, before it gets chance to start the operating system and it does not eject, then it must be a hardware fault. Does it eject if you put a pin in the emergency eject hole?

---

### Post by spencerownside on 2012-08-29
I did use a pin and the drive did eject. I then did the reboot and eject button on startup and it did open. When I got the laptop, it was brand new and came with windows loaded on it. The drive did work then but when I switched from windows to ubuntu that is when the drive stopped working. 
I do have the drive open now - what should I do next please?

---

### Post by dandnsmith on 2012-08-31
When you power-up the laptop with the drive open, it should then close and check the drive for a CD during boot - does it?
BTW hold old is the laptop now? - the drive could have died at as little as a year old (from my personal experience)

---

### Post by spjackson on 2012-08-31
Do you have a bootable CD (preferably Linux)? If so, I suggest changing the BIOS settings to boot from CD. If this works, then the problem is definitely to do with your Ubuntu installation. If it fails to boot from the CD, then that suggests a more fundamental problem - i.e. BIOS or hardware.

If it turns out to be a Ubuntu problem then we need some more information to help sort it out.

[LIST]
[*]Which Ubuntu version are you using?
[*]Is that 32-bit or 64-bit?
[*]What make and model is your laptop?
[*]How old is it?
[*]Do you know anything about the optical drive? (DVD reader/writer? CD reader/writer? make, model, etc.)
[/LIST]
Is the device recognised at boot time? On my laptop, I get:
```

dmesg | fgrep -i cd
 
Snipped some irrelevant stuff
[    2.066702] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7710H  A833 PQ: 0 ANSI: 5
[    2.069483] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.069492] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.069715] sr 4:0:0:0: Attached scsi CD-ROM sr0

```Do you get anything similar?

[Here is a thread]("http://ubuntuforums.org/showthread.php?t=1900565") that wasn't solved, but it does have some hints about what to look at.

---

