---
title: "upsmon -c fsd"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by bikrus on 2008-01-24
Hello!
I'm noob in Linux and Ubuntu. I need the next procedure (don't ask why) :
- shutdown PC
- "reboot" UPS even if it not OB (on battery)
- PC will start automatically.

I've installed NUT. It works ok, as far as I understand it's functionality. By googling answers for required procedure I've tried
> upsmon -c fsd
and
> upscmd -u admin -p pass apc@localhost shutdown.return;shutdown -h +0
and
> upscmd -u admin -p pass apc@localhost shutdown.return;sleep 5;upscmd -u admin -p pass apc@localhost shutdown.return;shutdown -h +0

No success yet. The PC is shutdowned normally, but UPS stay online. I need to load off + load on UPS after PC shutdown, like reboot both: PC and UPS.
Any help or suggestions?
I have APC Smart-UPS 1000. If more information required, please, tell me. If I need to ask this question in another forum, please point me to it.

By the way. To shutdown PC and shutdown UPS I use
> upscmd -u admin -p pass apc@localhost shutdown.stayoff;sleep 5;upscmd -u admin -p pass apc@localhost shutdown.stayoff;shutdown -h +0

The analogue:
> upsdrvctl shutdown apc;shutdown -h now

doesn't work always, but sometime. Don't understand why.

Thanks.

PS: this is a copy of my message from "Absolute Beginner Talk" forum. Maybe here somebody have any suggestions.

---

### Post by bikrus on 2008-01-24
Resolved.
One of following reasons has solved the problem:
1. Changing UPS device (same model)
2. Applying command:
> /lib/nut/apcsmart -k -x sdtype=0 /dev/ttyS0;shutdown -h +0

---

