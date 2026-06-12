---
title: "Bluetooth adapter - none found! Where has it gone?"
date: 2020-04-29
forum: Hardware
---

### Post by makem2 on 2020-04-29
```

makem@XPS-13-9300:~$ blueman-manager
blueman-manager version 2.1.2 starting
blueman-manager 23.17.51 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 23.17.51 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting
makem@XPS-13-9300:~$ 

```

It  was there and working less than an hour ago.

This is a new dual boot install and I updated windows drivers using DELL updater. One of the drivers was bluetooth. Has windows now kidnapped my adapter? It was working fine in both OS :(

---

### Post by jeremy31 on 2020-04-29
You might need to shut down the laptop completely and do a cold boot into Ubuntu

---

### Post by makem2 on 2020-04-29
> **jeremy31 said:**
> You might need to shut down the laptop completely and do a cold boot into Ubuntu

Thank you.

That was the answer. A reboot from windows back into ubuntu was insufficient.

Now fix my fingerprint reader so quickly ;)

---

### Post by eduweb on 2021-02-14
Hi all,

Im getting the same error message when trying to run blueman-manager.
About restarting the system/machine, yes, it works, but I'm trying to find a way it stop happening to I dont have to restart the computer everytime.
After compter sleeps they come back with bluetooth not working and I have to reboot. It's annoying.

I appreciate any help.

---

