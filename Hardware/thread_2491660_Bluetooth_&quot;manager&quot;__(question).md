---
title: "Bluetooth &quot;manager&quot; ? (question)"
date: 2023-10-16
forum: Hardware
---

### Post by salvarore on 2023-10-16
Is there an option / setup to instruct Ubuntu Bluetooth manager to ALWAYS connect to Bluetooth device which was set to "connected" before reboot ?

Ubuntu Bluetooth  manager ALWAYS displays Bluetooth device(s) , hence it has record of them, but NEVER attempts to actually connect to a device , even when the device HAS power  AND was active / connected  BEFORE reboot.   The "status" shown  by Bluetooth manager is always "Disconnected" , and the actual device name is ALWAYS shown.   ( Manager knows the name , but does not know its  last active state )
Its " I am here " light is active - flashing.

---

### Post by Holger_Gehrke on 2023-10-16
If a device is marked as "Trusted" it will automatically be connected when it becomes visible. You can manually connect to a non-trusted device from it's context menu (right mouse click) in blueman-manager.

Holger

---

