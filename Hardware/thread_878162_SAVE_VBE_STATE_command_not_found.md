---
title: "SAVE_VBE_STATE: command not found"
date: 2008-08-02
forum: Hardware
---

### Post by DocFox on 2008-08-02
Hi

I have a Dell Latitude D630, with an nVidia Quadro NVS 135M card. I used EnvyNG to install the 173.14.09 driver. Latest 2.6.24-19-generic kernel.

The suspend to RAM is driving me absolutely nuts. It suspends fine but on wake up *usually* crashes requiring a hard-reset. The screen gets stuck at the flashing cursor top left.

I think i must have read every article in the forums/google.

in the acpid log i get the following pretty reliably appearing after a failed resume:

> [Sun Jul 27 16:18:05 2008] received event "button/lid LID 00000080 00000001"
[Sun Jul 27 16:18:05 2008] notifying client 5509[107:116]
[Sun Jul 27 16:18:05 2008] notifying client 5657[0:0]
[Sun Jul 27 16:18:05 2008] notifying client 5657[0:0]
[Sun Jul 27 16:18:05 2008] executing action "/etc/acpi/lid.sh"
[Sun Jul 27 16:18:05 2008] BEGIN HANDLER MESSAGES
/etc/default/acpi-support: line 23: SAVE_VBE_STATE: command not found
[Sun Jul 27 16:18:05 2008] END HANDLER MESSAGES
[Sun Jul 27 16:18:05 2008] action exited with status 0
[Sun Jul 27 16:18:05 2008] completed event "button/lid LID 00000080 00000001"
[Sun Jul 27 16:18:05 2008] received event "ac_adapter AC 00000080 00000000"
[Sun Jul 27 16:18:05 2008] notifying client 5509[107:116]
[Sun Jul 27 16:18:05 2008] notifying client 5657[0:0]
[Sun Jul 27 16:18:05 2008] notifying client 5657[0:0]
[Sun Jul 27 16:18:05 2008] executing action "/etc/acpi/power.sh"
[Sun Jul 27 16:18:05 2008] BEGIN HANDLER MESSAGES
/etc/default/acpi-support: line 23: SAVE_VBE_STATE: command not found
[Sun Jul 27 16:18:05 2008] END HANDLER MESSAGES
[Sun Jul 27 16:18:05 2008] action exited with status 0

I dont really understand this error, esp since i set SAVE_VBE_STATE=false in the acpi-support ...

I'm attaching the relevant configuration files to this post in the hope that someone out there can give the right pointers. Hey - this might even be a red herring but it's the only lead i can find after trying everything else.

thanks in advance to anyone with a clue

---

