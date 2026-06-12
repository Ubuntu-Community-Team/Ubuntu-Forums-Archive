---
title: "Feisty user has working ACPI events; how to edit Edgy user to match?"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by Fyda on 2007-07-09
Hello,

I'm using an ASUS U5F laptop with Intel HDA (High Definition Audio) sound.

I'm having an issue with ACPI events and the GNOME panel volume applet. When using my old user account, *fyda* (created under Edgy, surviving an upgrade to Feisty), the laptop buttons for **Vol Up**, **Vol Down** and **Vol Mute** don't trigger the volume OSD. They also don't effect any change in the volume state. But, on a new user, *guest* (created *after* upgrading to Feisty), they do.

I did a *tail -f /var/log/acpid >> acpid_log_$(whoami).txt* for each user. Then, I pressed the buttons in this order: **Vol Down**, **Vol Up**, **Mute** (toggle on), **Mute** (toggle off). The results (after removing lines not pertaining to these specific events) showed that both users were triggering the same .sh scripts under */etc/acpi*. This is puzzling because they work for user *guest* but not for user *fyda*.

**acpid_log_fyda.txt**:
```
[Mon Jul  9 16:04:50 2007] client connected from 4868[0:0]
[Mon Jul  9 16:04:50 2007] 1 client rule loaded
[Mon Jul  9 16:05:00 2007] received event "hotkey ATKD 00000031 0000006e"
[Mon Jul  9 16:05:00 2007] notifying client 4714[106:110]
[Mon Jul  9 16:05:00 2007] notifying client 7411[0:0]
[Mon Jul  9 16:05:00 2007] client has disconnected
[Mon Jul  9 16:05:00 2007] notifying client 4868[0:0]
[Mon Jul  9 16:05:00 2007] executing action "/etc/acpi/voldownbtn.sh"
[Mon Jul  9 16:05:00 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:01 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:01 2007] action exited with status 0
[Mon Jul  9 16:05:01 2007] executing action "/etc/acpi/voldownbtn.sh"
[Mon Jul  9 16:05:01 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:01 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:01 2007] action exited with status 0
[Mon Jul  9 16:05:01 2007] completed event "hotkey ATKD 00000031 0000006e"
[Mon Jul  9 16:05:01 2007] received event "hotkey ATKD 00000030 0000003c"
[Mon Jul  9 16:05:01 2007] notifying client 4714[106:110]
[Mon Jul  9 16:05:01 2007] notifying client 4868[0:0]
[Mon Jul  9 16:05:01 2007] executing action "/etc/acpi/volupbtn.sh"
[Mon Jul  9 16:05:01 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:01 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:01 2007] action exited with status 0
[Mon Jul  9 16:05:01 2007] executing action "/etc/acpi/volupbtn.sh"
[Mon Jul  9 16:05:01 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:01 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:01 2007] action exited with status 0
[Mon Jul  9 16:05:01 2007] completed event "hotkey ATKD 00000030 0000003c"
[Mon Jul  9 16:05:02 2007] received event "hotkey ATKD 00000032 00000009"
[Mon Jul  9 16:05:02 2007] notifying client 4714[106:110]
[Mon Jul  9 16:05:02 2007] notifying client 4868[0:0]
[Mon Jul  9 16:05:02 2007] executing action "/etc/acpi/mutebtn.sh "
[Mon Jul  9 16:05:02 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:02 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:02 2007] action exited with status 0
[Mon Jul  9 16:05:02 2007] completed event "hotkey ATKD 00000032 00000009"
[Mon Jul  9 16:05:02 2007] received event "hotkey ATKD 00000032 0000000a"
[Mon Jul  9 16:05:02 2007] notifying client 4714[106:110]
[Mon Jul  9 16:05:02 2007] notifying client 4868[0:0]
[Mon Jul  9 16:05:02 2007] executing action "/etc/acpi/mutebtn.sh "
[Mon Jul  9 16:05:02 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:02 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:02 2007] action exited with status 0
[Mon Jul  9 16:05:02 2007] completed event "hotkey ATKD 00000032 0000000a"
```

**acpid_log_guest.txt:**
```
[Mon Jul  9 16:05:13 2007] client connected from 7411[0:0]
[Mon Jul  9 16:05:13 2007] 1 client rule loaded
[Mon Jul  9 16:05:15 2007] received event "hotkey ATKD 00000031 0000006f"
[Mon Jul  9 16:05:15 2007] notifying client 4714[106:110]
[Mon Jul  9 16:05:15 2007] notifying client 4868[0:0]
[Mon Jul  9 16:05:15 2007] client has disconnected
[Mon Jul  9 16:05:15 2007] notifying client 7411[0:0]
[Mon Jul  9 16:05:15 2007] executing action "/etc/acpi/voldownbtn.sh"
[Mon Jul  9 16:05:15 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:15 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:15 2007] action exited with status 0
[Mon Jul  9 16:05:15 2007] executing action "/etc/acpi/voldownbtn.sh"
[Mon Jul  9 16:05:15 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:15 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:15 2007] action exited with status 0
[Mon Jul  9 16:05:15 2007] completed event "hotkey ATKD 00000031 0000006f"
[Mon Jul  9 16:05:16 2007] received event "hotkey ATKD 00000030 0000003d"
[Mon Jul  9 16:05:16 2007] notifying client 4714[106:110]
[Mon Jul  9 16:05:16 2007] notifying client 7411[0:0]
[Mon Jul  9 16:05:16 2007] executing action "/etc/acpi/volupbtn.sh"
[Mon Jul  9 16:05:16 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:16 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:16 2007] action exited with status 0
[Mon Jul  9 16:05:16 2007] executing action "/etc/acpi/volupbtn.sh"
[Mon Jul  9 16:05:16 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:16 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:16 2007] action exited with status 0
[Mon Jul  9 16:05:16 2007] completed event "hotkey ATKD 00000030 0000003d"
[Mon Jul  9 16:05:16 2007] received event "hotkey ATKD 00000032 0000000b"
[Mon Jul  9 16:05:16 2007] notifying client 4714[106:110]
[Mon Jul  9 16:05:16 2007] notifying client 7411[0:0]
[Mon Jul  9 16:05:16 2007] executing action "/etc/acpi/mutebtn.sh "
[Mon Jul  9 16:05:16 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:16 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:16 2007] action exited with status 0
[Mon Jul  9 16:05:16 2007] completed event "hotkey ATKD 00000032 0000000b"
[Mon Jul  9 16:05:16 2007] received event "hotkey ATKD 00000032 0000000c"
[Mon Jul  9 16:05:16 2007] notifying client 4714[106:110]
[Mon Jul  9 16:05:16 2007] notifying client 7411[0:0]
[Mon Jul  9 16:05:16 2007] executing action "/etc/acpi/mutebtn.sh "
[Mon Jul  9 16:05:16 2007] BEGIN HANDLER MESSAGES
[Mon Jul  9 16:05:16 2007] END HANDLER MESSAGES
[Mon Jul  9 16:05:16 2007] action exited with status 0
[Mon Jul  9 16:05:16 2007] completed event "hotkey ATKD 00000032 0000000c"
```

I have searched for this on Google, and found some people who edited their system files, but I don't think that would be the issue, since both users are, again, using the same files. I haven't found any acpi(d)-related files in the home directories, either, but I may not be looking in the right place. I have also found that some users had similar behaviour due to lacking root privs (which are required to put the laptop to sleep), but I don't know whether that affects the volume controls, nor do I know how to make the scripts execute as root.

I have checked the user groups and ensured that there are no groups which contain *guest* but not *fyda*.

I have tried a *dpkg-reconfigure* for the *acpi*, *acpi-support*, and *acpid* packages, but this has had no effect.

**Question:** What is the difference between the old user and the new user, with regards to correctly functioning ACPI keys? Is there a specific package I need to *dpkg-reconfigure* to get the correct settings? Are there flags or settings I need to edit? How do I enable correct ACPI events for the old user *without creating a new user*? If it is a problem with root privs, how do I make the volume scripts execute as root?

Thanks for your time.

---

