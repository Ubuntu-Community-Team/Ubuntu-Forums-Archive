---
title: "suspend/hibernate freezes Lenovo E480  22.04 5.15.0"
date: 2022-12-19
forum: Hardware
---

### Post by rs-aleev on 2022-12-19
I know that this issue is very old and many time was solved, but nothing works persistent for me. 

Configuration: 

```
[FONT=monospace][COLOR=#000000]/sys/power/state       [/COLOR]
freeze mem disk
[/FONT]
```

pm-utils package is installed 

and re-enabled policykit

```

[FONT=monospace][COLOR=#000000][[/COLOR][COLOR=#000000]Re-enable hibernate by default in upower[/COLOR][COLOR=#000000]][/COLOR]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes

[Enable hibernate to be run via cron]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
ResultAny=yes
[COLOR=#5454FF]~               [/COLOR]
[/FONT]
```

I can't debug what causes freezes since I have to hard reboot everytime. Any of these commands causes black screend and FN keys and power LED are still on.
Tried uswsusp and hibernate packages. Same result.


UPDATE: pm-utils suspend works fine, and I can turn on sleep mode in lightdm, but after KDE 5 starts any ACPI event: LID, PowerButton or sleep mode in KMenu freezes notebook.

---

