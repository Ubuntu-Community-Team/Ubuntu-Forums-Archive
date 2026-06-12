---
title: "demsg logs has i2c-GXT7863:00: Fetching the HID descriptor"
date: 2022-03-20
forum: Hardware
---

### Post by zzqayy on 2022-03-20
logs 

```

[FONT=monospace][COLOR=#000000][    1.337331] [/COLOR][COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: Fetching the HID descriptor [/COLOR]
[    1.337335] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=20 00 [/COLOR]
[    1.338201] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: HID Descriptor: 1e 00 00 01 99 02 02 00 03 00 20 00 04 00 00 00 05 00 06 00 c6 27 e0 01 05 01 00 00 00 00 [/COLOR]
[    1.338334] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: entering i2c_hid_parse [/COLOR]
[    1.338336] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_hwreset [/COLOR]
[    1.338338] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_set_power [/COLOR]
[    1.338339] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 00 08 [/COLOR]
[    1.409876] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: resetting... [/COLOR]
[    1.409878] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 00 01 [/COLOR]
[    1.410114] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: waiting... [/COLOR]
[    6.481983] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: finished. [/COLOR]
[    6.481991] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: failed to reset device. [/COLOR]
[    6.481999] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_set_power [/COLOR]
[    6.482003] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 01 08 [/COLOR]
[    7.506026] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_hwreset [/COLOR]
[    7.506036] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_set_power [/COLOR]
[    7.506040] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 00 08 [/COLOR]
[    7.573974] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: resetting... [/COLOR]
[    7.573982] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 00 01 [/COLOR]
[    7.575137] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: waiting... [/COLOR]
[   12.625974] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: finished. [/COLOR]
[   12.625982] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: failed to reset device. [/COLOR]
[   12.625989] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_set_power [/COLOR]
[   12.625993] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 01 08 [/COLOR]
[   13.649977] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_hwreset [/COLOR]
[   13.649985] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_set_power [/COLOR]
[   13.649989] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 00 08 [/COLOR]
[   13.717978] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: resetting... [/COLOR]
[   13.717985] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 00 01 [/COLOR]
[   13.718455] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: waiting... [/COLOR]
[   18.769972] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: finished. [/COLOR]
[   18.769973] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: failed to reset device. [/COLOR]
[   18.769975] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_set_power [/COLOR]
[   18.769975] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 01 08 [/COLOR]
[   19.793951] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_hwreset [/COLOR]
[   19.793952] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_set_power [/COLOR]
[   19.793953] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 00 08 [/COLOR]
[   19.861960] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: resetting... [/COLOR]
[   19.861962] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 00 01 [/COLOR]
[   19.862180] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: waiting... [/COLOR]
[   24.913955] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: finished. [/COLOR]
[   24.913957] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: failed to reset device. [/COLOR]
[   24.913958] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: i2c_hid_set_power [/COLOR]
[   24.913959] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: __i2c_hid_command: cmd=05 00 01 08 [/COLOR]
[   25.937957] [COLOR=#ff5454]**i2c_hid_acpi i2c-GXT7863:00**[/COLOR][COLOR=#000000]: can't add hid device: -61[/COLOR]
[/FONT]

```

---

### Post by zzqayy on 2022-03-20
How should I handle it?

---

### Post by Yellow Pasque on 2022-03-21
From googling, I'm guessing this is your touchpad? So does your touchpad work properly? What laptop model is this?

---

### Post by zzqayy on 2022-04-13
from googling,the solution is add kernel params i8042.noaux,thanks

---

### Post by Yellow Pasque on 2022-04-14
> **zzqayy said:**
> from googling,the solution is add kernel params i8042.noaux,thanks

Nice. I'm still curious if this had any practical effect on your system or whether it was just spamming your logs? Either way, please mark the thread SOLVED ('Thread Tools' menu above the first post). Bonus points if you link to the site or bug report that solved it for you.

---

### Post by zzqayy on 2022-05-13
[COLOR=#000000][FONT=Roboto]I thought it had been solved before, but now this problem still occurs, it will cause the system to freeze, and it will be accompanied by cpu errors[/FONT][/COLOR]

---

### Post by zzqayy on 2022-05-14
[Xiaomi Mi Notebook Pro 15.6 Ryzen edition touchpad sometimes doesn't work - General system - EndeavourOS]("https://forum.endeavouros.com/t/xiaomi-mi-notebook-pro-15-6-ryzen-edition-touchpad-sometimes-doesnt-work/22132/57") this is the link.

---

