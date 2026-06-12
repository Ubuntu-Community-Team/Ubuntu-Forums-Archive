---
title: "acpid not responding to resume"
date: 2008-09-24
forum: Hardware
---

### Post by phileh on 2008-09-24
Hi folks, I'm having a problem with acpid not responding to resume events. I'm running:

Ubuntu 8.04.1
kernel image 2.6.24-19
acpid 1.0.4-5

When suspending the system (it's a Dell XPS 1330), all network interfaces go down (which is expected), but when resuming, they don't come up again.

Digging in /etc/acpi I see /etc/acpi/resume.d/62-ifup.sh which should bring up any interface taken down on resume. If I add a diagnostic line like:

touch /tmp/acpid_is_responding

to the script, it's not executed. Moving further up the chain to 
/etc/acpi/resume.sh yields the same result: the script does not seem to get executed.

I have a feeling that acpid does not receive any ACPI events at all from the kernel but I have no idea what's wrong. The acpid manpage says that the daemon is listening on /proc/acpi/event and that's available.

Also note that there is no problem with ACPI hardware-wise. I can suspend and resume the system just fine. It's just that I need some kind of ACPI event handler which restores the network interfaces.

Anyone seen this before?

---

### Post by mechatronicat on 2008-09-29
Hello

I have this kind of problem too, i found out that the scripts in /etc/acpi/resume.d/ and /etc/acpi/suspend.d/ are not executed! Only /etc/acpi/start.d/ works.

Medion akoya mini, ubuntu 8.04.1

Does anyone have an idea?

Thanks

---

### Post by szczav on 2008-10-01
I've got same problem. I found this [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/205005]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/205005") and works for me.

---

