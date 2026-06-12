---
title: "[SOLVED] boot stops at this message. What's happening?"
date: 2008-09-03
forum: General Help
---

### Post by AlanInVancouverBC on 2008-09-03
After trying to reduce boot time by stopping 3 processes, I can't complete the boot sequence. It stops at this:

NetworkManager: <WARN> nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -ihosts'): could not spawn process. (Failed to execute child process "usr/sbin/nscd" (No such file or directory)

then a few lines later...

NetworkManager: <debug> [1220484243.224892] nm_hal_device_added(): Newdevice added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_1511_MY29PD405DWB_if0_printer_MY29PD405DWB').

If I then hit Enter, I get:

Ubuntu 8.04.1 telus tty1
telus login:


From what I can make out, I don't know what process is being spawned; I haven't changed or added anything related to a usb device (that I am aware of); and there is nothing I am aware of related to my printer.


Any help would be appreciated. I'm able to do this due to a dual boot with XP.

Thanks in advance.

---

### Post by AlanInVancouverBC on 2008-09-06
I just decided to uninstall and reinstall Ubuntu. It's easy and fast. 
Just one thought: Make it more clear about what services will do, if stopped. I got a message that the service I would stop may cause permanent loss of personal information. I think it should be more clear that it might cause Ubuntu not to boot at all!

---

### Post by cariboo on 2008-09-06
You can run in a terminal:

```
man service
```

This will bring up the man page for the particular service. You can also use this for any program you don't underrstand. Remember Linux does not hold your hand the way windows does. You are responsible for what happens to your computer.

Jim

---

