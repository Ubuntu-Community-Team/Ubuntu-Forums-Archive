---
title: "Determining event for special laptop buttons"
date: 2009-08-24
forum: Hardware
---

### Post by parameter on 2009-08-24
I have a HP 6910p laptop that has some special buttons at the top of the keyboard. Two of them do nothing in Ubuntu so I'd like to assign an action to them. I tried using xev but the buttons do not trigger an event. From googling I have determined that these buttons might trigger an ACPI event. I tried stopping acpid and reading from /proc/acpi/events but didn't get any output for these buttons.

Does anyone have any ideas of something else I can try?

---

### Post by parameter on 2009-08-25
I googled some more and determined that I can read the keys with the "sudo input-events 4" and "sudo input-events 11" commands. Can someone tell me what I can do with this information? Is there a program that I can configure to use this?

```
# sudo input-events 11
/dev/input/event11
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HP WMI hotkeys"
   phys    : "wmi/input0"
   bits ev : EV_SYN EV_KEY EV_SW

waiting for events
14:24:59.128496: EV_KEY KEY_INFO (0x166) pressed
14:24:59.128503: EV_SYN code=0 value=0
14:24:59.128506: EV_KEY KEY_INFO (0x166) released
14:24:59.128509: EV_SYN code=0 value=0

# sudo input-events 4
/dev/input/event4
   bustype : BUS_I8042
   vendor  : 0x1
   product : 0x1
   version : 43841
   name    : "AT Translated Set 2 keyboard"
   phys    : "isa0060/serio0/input0"
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

waiting for events
14:24:23.835501: EV_MSC code=4 value=136
14:24:23.835520: EV_KEY KEY_PRESENTATION (0x1a9) pressed
14:24:23.835526: EV_SYN code=0 value=0
14:24:23.842493: EV_MSC code=4 value=136
14:24:23.842506: EV_KEY KEY_PRESENTATION (0x1a9) released
14:24:23.842510: EV_SYN code=0 value=0

```

---

### Post by parameter on 2009-08-26
Bump

---

### Post by parameter on 2009-09-12
bump

---

### Post by parameter on 2009-10-25
bump

---

### Post by parameter on 2009-10-26
Come on. Someone has to have experience with this. Any Ubuntu developers reading this forum? [-o<

---

### Post by parameter on 2009-10-28
bump

---

### Post by parameter on 2009-11-09
bump

---

### Post by Anonymousable on 2009-11-09
I'm not sure... Maybe they're read as keyboard events.

Try using System>Preferences>Keyboard Shortcuts.

Then find an unbound action, select it and press one of the buttons. If it shows a value, lucky you. If not, unlucky (i.e. Sorry, I can't help). :P ;)

---

### Post by parameter on 2009-11-21
> **Anonymousable said:**
> I'm not sure... Maybe they're read as keyboard events.

Try using System>Preferences>Keyboard Shortcuts.

Then find an unbound action, select it and press one of the buttons. If it shows a value, lucky you. If not, unlucky (i.e. Sorry, I can't help). :P ;)

That doesn't work. The only way to read them that I could find is what I described in post #2. It seems I need to configure HAL but I need help doing that. I've read the HAL documentation but I don't really understand it.

---

