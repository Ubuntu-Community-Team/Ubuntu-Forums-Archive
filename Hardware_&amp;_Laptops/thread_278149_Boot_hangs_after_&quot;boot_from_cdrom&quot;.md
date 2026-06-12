---
title: "Boot hangs after &quot;boot from cdrom&quot;"
date: 2006-10-15
forum: Hardware &amp; Laptops
---

### Post by Jerrac on 2006-10-15
I am confused. I installed a second disk to put windows on. Windows wasn't liking me, so I tried to reinstall it. It went and said that it was going to wipe both of my disks. I had told it to wipe the second disk. So I exited and tried to reboot. It will not boot up anymore. Once it reaches the "Boot from cd-rom" line, it just sits there. Did windows wipe my mbr?

I have tried several combinations of my hard disk cables, nothing worked. Right now I just have my linux disk hooked up.

I also have been trying to boot to my dapper cd so I can try to repair things. It just boots to a blank screen with a cursor blinking. Even in the safe graphics mode.

Help.

---

### Post by Jerrac on 2006-10-15
Ok, I was just playing around with knoppix on my system. When I try to "sudo mount -t /dev/hdc1 /mnt/hdc1" it says:
> mount: wrong fs type, bad option, bad superblock on /dev/hdc1, missing codepage or other error
In some cases useful info is found in syslog - try dmesg | tail or so

That gives > VFS: Can't find ext3 filesystem on dev hdc1.

So, apparently windows destroyed my filesystem. Is there anyway to restore it?

---

