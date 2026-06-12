---
title: "SSD failure when accessing certain files"
date: 2012-05-03
forum: Hardware
---

### Post by tommycli on 2012-05-03
I have two partitions on my SSD:
/home at /dev/sda1
/     at /dev/sda2

Both are formatted ext4.

When I access certain files in /home, usually in heavily trafficked directories. (Theres one in .thunderbird, one in .purple), it causes a bunch of dmesg errors that look like:

exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen

This occurs on both Ubuntu and Mint, and occurs while I put the drive in IDE mode in the BIOS too.

When this error occurs, I can no longer access anything on the drive, including both /dev/sda1 and /dev/sda2. The computer can reboot normally but the problem recurs when I try to access that file again.

I feel that the fact that this occurs in IDE mode also means it's not a kernel issue. The fact that it occurs for a specific file means it's probably not a SATA controller issue...

Could it be a filesystem problem? I kind of doubt it because the error causes both /dev/sda1 and /dev/sda2 to become inaccessible.

I also checked for bad blocks and there were none.

Any thoughts?

---

### Post by mips on 2012-05-04
Try and disable SMART and power management for the device and see if it still happens.

Seems to be a common bug,
[https://bugzilla.redhat.com/show_bug.cgi?id=549981](https://bugzilla.redhat.com/show_bug.cgi?id=549981)
[https://www.google.co.za/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=exception+Emask+0x0+SAct+0x0+SErr+0x0+action+0x6+frozen](https://www.google.co.za/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=exception+Emask+0x0+SAct+0x0+SErr+0x0+action+0x6+frozen)

---

