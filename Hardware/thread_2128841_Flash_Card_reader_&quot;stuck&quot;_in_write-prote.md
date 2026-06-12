---
title: "Flash Card reader &quot;stuck&quot; in write-protect mode."
date: 2013-03-24
forum: Hardware
---

### Post by jason0x21 on 2013-03-24
I'm running 12.04.2, and I've got an Alcor Micro Corp. Flash Card Reader/Writer (usb ID 058f:6362).  Occasionally, I'll have a flash card fail, or get messed up, and the card will go "read only".  The problem is that the **reader** seems to go read-only, because all subsequent cards plugged into the reader are now marked read-only as well.  All cards will come up with the same drive name (ie. /dev/sdg), so when one card messes up it ruins it for everyone after, until I reboot and start over again.

Things I've tried...
[LIST=1]
[*]Mounting, unmounting, remounting, all while trying to specify "read-write"
[*]Locking and unlocking a "good" flash card while mounting it in each state (always shows up read-only).
[*]Using "sudo hdparm -r0 /deb/sdg" to change the read-only attribute on the drive (it always shows up as read-write, but that never seems to change things).
[*]Rebooting (this works, but I hate having to do that).
[/LIST]

The cards themselves are fine (except for the one that caused the reader to get stuck, obviously), moving the card to a different reader on the same computer works. Any clues on how to get a card reader stuck in write-protect mode unstuck?

---

