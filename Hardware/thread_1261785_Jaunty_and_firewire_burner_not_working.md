---
title: "Jaunty and firewire burner not working"
date: 2009-09-09
forum: Hardware
---

### Post by iadegesso on 2009-09-09
Hi,

I moved recently from Hardy to Jaunty, and now I cannot complete a dvd burning process successfully...

I've a Plextor PX-716 connected via firewire external box... in Hardy, dvd burning process work fine only using NeroLinux... with other burning programs process fails: lead-in was written, but when starts burn data track, the burning process does not proceed and I must kill program and restart the box to get drive accessible.

Now, with Jaunty, also NeroLinux does not work fine and do the same things described above...

Searching with Google, I realized that this is due to integration of [FONT=Courier New]scsi generic[/FONT] support into Jaunty new 2.6.28 kernel. In Hardy  [FONT=Courier New]scsi generic[/FONT] support was enabled loading [FONT=Courier New]sg[/FONT] module, and NeroLinux added it automatically to [FONT=Courier New]/etc/modules[/FONT]; now this no longer the case... and NeroLinux does not work exactly like the other programs...

Can you help me please? (sorry for my bad english)

Iade

---

### Post by iadegesso on 2009-09-11
Hi,
I've solved that problem by adding my user to [FONT=Courier New]disk[/FONT] group to grant myself full access to all [FONT=Courier New]sg*[/FONT] devices.

Is also necessary to create a [FONT=Courier New]firewire.conf[/FONT] file into [FONT=Courier New]/etc/modprobe.d[/FONT] with the following content:

[FONT=Courier New]options sbp2 serialize_io=N[/FONT]

---

