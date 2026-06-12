---
title: "Can't set ntfs to read only"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by jynyl on 2007-12-10
This is a laptop running Kubuntu 7.10 with Vista on sda1.
In System Settings, I unchecked the Writeable box, and noted that /etc/fstab now had the "ro" option.
LABEL=C-DRIVE /media/win_c ntfs defaults,umask=007,uid=0,gid=46,auto,ro,nouser 0 1

But in Konqueror or in Konsole, permissions on the ntfs partition are still writeable, permissions 770.  I've tried rebooting a couple of times, but the symptoms persist.

I don't need to write to ntfs, and Vista has complained about some filesystem problems, so I want to be sure Kubuntu isn't upsetting Vista.

TIA

Peter

---

### Post by jynyl on 2007-12-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/175338](https://bugs.launchpad.net/ubuntu/+bug/175338) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				ok - manually editing /etc/fstab to umask=227 appears to make the Vista partition mount as read only.
This isn't obvious from the system settings gui, so it looks like a bug?

---

