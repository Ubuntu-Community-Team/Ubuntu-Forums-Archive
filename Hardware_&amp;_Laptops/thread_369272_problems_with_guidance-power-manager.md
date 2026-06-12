---
title: "problems with guidance-power-manager"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by taiko on 2007-02-24
I'm trying to set my laptop's lid close action (i.e. I want the laptop to suspend on lid close but when left-click on the Power-Manager icon in my menubar all the options are disabled.  When I start guidance-power-manager manually using konsole I get the following errors but the application appears to start (i.e. it's icon appears in the menubar and I can use it to suspend the laptop).  Starting manually as root still does not activate the power settings options.

```
taiko@taiko-laptop:/usr/bin$ sudo guidance-power-manager
taiko@taiko-laptop:/usr/bin$ X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
No battery found.
No AC adapter found - assume that we are on batteries.
No AC adapter found - assume that we are on batteries.
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
power-manager: ERROR: Communication problem with power-manager, it probably crashed.

```

Any help would be appreciated!

---

