---
title: "Startup problems after downloading updates"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by Steve1961 on 2005-09-09
I've just downloaded a couple of updates after being notified that they were available, one of which was a new kernel image.  Everything seemed to go well and I continued working.  However, when I rebooted an hour or so later, gnome appeared to start as normal and the two panels appeared with all the icons on them, but no wallpaper, just a plain brown background, and no desktop icons.  Everything seemed to work OK, but I tried rebooting and the screen froze and I had to alt-ctrl-backspace and reboot manually.  I tried again but got the same result two or three times, but finally one reboot seemed to go normally.

Unfortunately this now seems to be happening most of the time, and I have to reboot the system at least twice before the desktop comes up properly.  Putting a cd in the drive before rebooting makes no difference.  A real downer because I'd just got the system working great.

Any ideas?

Update: dmesg seems to show a problem with the dvd drive (hda).  Lots of messages like:

hda: command error: status=0x51 { DriveReady SeekComplete Error }
hda: command error: error=0x54
ide: failed opcode was 100

I haven't enabled DMA because when I tried once I got an error message saying action not permitted.  As the drive seems to work OK without this I left it as it was.

I don't know if changing the order of modules in the /etc/modules will make any difference.  That seems to work sometimes for people getting the can't initialize hal problem, although I don't get this message.  Anyway, the modules are listed in the following order:

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
rtc
sbp2
sr_mod
nvidia

---

