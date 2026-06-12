---
title: "Inspiron 8600 triggers the lid button event all by itself!?!"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by André on 2006-01-12
Hi everybody,

i have a nice Inspiron 8600 and i am pretty satisfied with it. Suspending to disk and RAM seems to work out of the box, BUT:

Often when i suspend to RAM and leave my system on my office table without touching it, it hust turns itself on again. I can see the last events of acpid with ```
sudo less /var/log/acpid
``` and it gives me:

> [Sun Jan  8 19:12:00 2006] starting up
[Sun Jan  8 19:12:00 2006] 47 rules loaded
[Sun Jan  8 19:12:03 2006] client connected from 6920[111:111]
[Sun Jan  8 19:12:03 2006] 1 client rule loaded
[Sun Jan  8 20:28:26 2006] received event "button/lid LID 00000080 00000001"
[Sun Jan  8 20:28:26 2006] notifying client 6920[111:111]
[Sun Jan  8 20:28:26 2006] executing action "/etc/acpi/lid.sh"
[Sun Jan  8 20:28:26 2006] BEGIN HANDLER MESSAGES
xscreensaver-command: throttled.

xscreensaver-command: activating and locking.

[Sun Jan  8 20:28:28 2006] END HANDLER MESSAGES
[Sun Jan  8 20:28:28 2006] action exited with status 1
[Sun Jan  8 20:28:28 2006] completed event "button/lid LID 00000080 00000001"
[Sun Jan  8 20:36:29 2006] received event "button/lid LID 00000080 00000002"
[Sun Jan  8 20:36:29 2006] notifying client 6920[111:111]
[Sun Jan  8 20:36:29 2006] executing action "/etc/acpi/lid.sh"
[Sun Jan  8 20:36:29 2006] BEGIN HANDLER MESSAGES
xscreensaver-command: unthrottled.

xscreensaver-command: deactivating.

That is really strange. The lid was closed after Suspending to RAM via the function button + Esc and i did not touch it again.

Any ideas? That really gets disturbing because it happens like 3 out of 4 times :-(

Greetings and thanks for any help
André

---

### Post by André on 2006-01-12
Wait a moment. The timestamp says that the event happens 4 days ago...

Am i looking into the wrong file??

Greetings
André

---

### Post by André on 2006-01-14
Hi everybody,

it really was the lid. I turned of the wakeup event for the lid and everything is fine :-)

Greetings
André

---

### Post by jude01 on 2007-10-20
> **André said:**
> I turned of the wakeup event for the lid and everything is fine :-)


hi
can you tell me how you did this? I want my laptop to resume from suspend on keypress only, not by opening the lid

thanks

---

