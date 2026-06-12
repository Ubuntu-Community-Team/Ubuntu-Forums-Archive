---
title: "acpi problem"
date: 2008-05-29
forum: Hardware
---

### Post by gdzsi on 2008-05-29
On my laptop, I have just installed Kubuntu 8.04. (well, a few days ago).

The problem I have is that nothing happens when I close the lid (Even the screen doesn't turn off).
I discovered that when I pull the ethernet cable out, the screen turns off for a moment, and after that, everything works properly - even if I plug it in again.

I changed the default network manager to WICD, and I use KPowersave instead of kde-guidance-powermanager. I know that KPowersave is not the issue, because the same happens with all power managers (I even tried installing gnome-power-manager).
Also, though I like wicd, it didn't connect the wired network automatically for me, so I wrote "auto eth0 inet dhcp" or something like that into /etc/network/interfaces.

If you can tell me why this issue is, or give a workaround, I would be happy, cause ACPI doesn't work until I plug a cable out, which is a great problem when I don't have ethernet nearby and I want to work on battery.

Thanks
G

---

### Post by hotweiss on 2008-05-29
> **gdzsi said:**
> On my laptop, I have just installed Kubuntu 8.04. (well, a few days ago).

The problem I have is that nothing happens when I close the lid (Even the screen doesn't turn off).
I discovered that when I pull the ethernet cable out, the screen turns off for a moment, and after that, everything works properly - even if I plug it in again.

I changed the default network manager to WICD, and I use KPowersave instead of kde-guidance-powermanager. I know that KPowersave is not the issue, because the same happens with all power managers (I even tried installing gnome-power-manager).
Also, though I like wicd, it didn't connect the wired network automatically for me, so I wrote "auto eth0 inet dhcp" or something like that into /etc/network/interfaces.

If you can tell me why this issue is, or give a workaround, I would be happy, cause ACPI doesn't work until I plug a cable out, which is a great problem when I don't have ethernet nearby and I want to work on battery.

Thanks
G

Did you left-click on the Power Manager icon (battery) in the task bar and set the appropriate action to be performed after closing the lid?

---

### Post by gdzsi on 2008-05-30
> **hotweiss said:**
> Did you left-click on the Power Manager icon (battery) in the task bar and set the appropriate action to be performed after closing the lid?
The action I set is performed only after I pull the cable out.

---

