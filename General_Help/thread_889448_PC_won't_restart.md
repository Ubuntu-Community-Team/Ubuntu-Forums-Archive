---
title: "PC won't restart"
date: 2008-08-14
forum: General Help
---

### Post by BiscuitTin on 2008-08-14
Can anyone tell me why my PC running Ubuntu won't restart? I can sometimes d an init 6 and it works, but if you do a restart from the menu, it drops out of the GUI and just hangs.

The last message is:

[   400.154814] Restarting system.

It never gets past that point. While not serious, its a major pain when trying to restart the system remotely, and inevitably means going to the machine and pressing the restart button each time.

---

### Post by tangibleorange on 2008-08-14
> **BiscuitTin said:**
> Can anyone tell me why my PC running Ubuntu won't restart? I can sometimes d an init 6 and it works, but if you do a restart from the menu, it drops out of the GUI and just hangs.

The last message is:

[   400.154814] Restarting system.

It never gets past that point. While not serious, its a major pain when trying to restart the system remotely, and inevitably means going to the machine and pressing the restart button each time.

what happens if instead of clicking restart in the menu you type this command:
```
sudo shutdown -r now
```

---

### Post by BiscuitTin on 2008-08-14
The GUI shuts down and a screen of text appears briefly. I am able to just catch a glimpse the last message which contains ]something like 'libnhal failed'.

The Ubuntu splash screen then comes up and the system freezes.

---

### Post by tangibleorange on 2008-08-14
OK. When you first boot up, you either see a list of operating systems or you need to press ESC to see the list. Either way, once you are highlighted over the Ubuntu menu entry, press 'e'. then scroll down to the line that begins with kernel and press 'e' again. at the end of the line that's displayed, type:
```
acpi=off noapic nolapic
```
it should now look like this:
```
/boot/vmlinuz-2.6.24-19-generic root=UUID=084b3ba0-8dc7-4de3-b7cc-745db14ec083 ro quiet splash acpi=off noapic nolapic
```
then press enter, and then 'b' to boot. If it now hangs, don't worry, simply turn it off and reboot, it will be back to normal. If it does boot however, try shutting down and see what happens.

---

### Post by BiscuitTin on 2008-08-29
Thanks tangible orange. I tried this but I couldn't get the settings to stay there. Everytime I closed the menu window the line reverted back to its previous state. I eventually booted into the system and edited /boot/grub/menu.lst instead.

Anyway, this seemed to make no difference. It still hung when shutting down as previously.

---

