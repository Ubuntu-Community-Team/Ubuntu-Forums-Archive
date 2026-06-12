---
title: "Toshiba A100 laptop, Internal CD annoyance"
date: 2008-10-01
forum: Hardware
---

### Post by lisati on 2008-10-01
This is kind-of a follow-up to [http://ubuntuforums.org/showthread.php?t=560829](http://ubuntuforums.org/showthread.php?t=560829) (archived due to lack of activity) and relates to some annoyances on my Toshiba A100 Satellite running Feisty with all the available updates.

This morning I was annoyed by knocking sound coming from within my laptop. Inspection of the system logs revealed several entries similar to the following, popping up whenever I heard the sound:
> 
ct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] ide: failed opcode was: unknown
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: drive not ready for command
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] ide: failed opcode was: unknown
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: drive not ready for command
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] ide: failed opcode was: unknown
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: drive not ready for command
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] ide: failed opcode was: unknown
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: drive not ready for command
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] ide: failed opcode was: unknown
Oct  2 11:52:02 portable-aspie kernel: [10212.660000] hdc: drive not ready for command

There were quite a few of them!

Trying to reboot from the alternate CD using the internal CD/DVD drive didn't work, the system behaved as if there was no media in the drive. And Ubuntu didn't seem to want to mount it either....

So out of curiosity, I boot into Windows to see what it would make of it. After it wakes up from suspend, it could access the drive.... so shut down Windows completely and try rebooting from the CD. It worked, so I run the "Rescue broken system" option of the alternate CD (on the off chance that it could work some magic)

This reboot of Ubuntu hasn't had any of the knocking sounds, no sign so far of the error message in the log, no sign of the phantom audio CD icon on the desktop.

I wouldn't have expected it (I've only ever heard of unclean shutdowns affecting hard disk drives), but shutting down Windows properly seems to have made a difference.......

Comments and questions are welcome.....

EDIT: Hmmmm changed to Xubuntu 8.10, no apparent problems so far relating to this one.......

---

