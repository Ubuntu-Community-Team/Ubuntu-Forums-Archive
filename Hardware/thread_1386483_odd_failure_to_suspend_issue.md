---
title: "odd failure to suspend issue"
date: 2010-01-20
forum: Hardware
---

### Post by maestrobwh1 on 2010-01-20
Was using live with persistence so "restoring" was simple... booted into non persistent mode and deleted all directories (and hidden .wh file) from casper-rw partition except for /home and and saved /etc/apt and /etc/rc.local /etc/modules.  Rebooted into persistent mode and reinstalled optional applications.  Suspend works again.

*original post*

I can only suspend my computer using this command:
```
sudo /etc/acpi/sleep.sh sleep
```

Gnome power manager and the logout request to suspend results in the screen dimming and then the desktop comes right back.

If I run this script (found googling what command gnome uses to suspend)
```

#!/bin/bash
dbus-send \
--session \
--dest=org.freedesktop.PowerManagement \
--type=method_call \
--print-reply \
--reply-timeout=2000 \
/org/freedesktop/PowerManagement \
org.freedesktop.PowerManagement.Suspend
exit 0

```
Also causes a failure to suspend with this response:
[INDENT]Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/INDENT]

I am assuming I am having a permissions issue or something?

---

