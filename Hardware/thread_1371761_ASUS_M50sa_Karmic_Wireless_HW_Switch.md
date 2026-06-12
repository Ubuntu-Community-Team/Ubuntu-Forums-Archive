---
title: "ASUS M50sa Karmic Wireless HW Switch"
date: 2010-01-03
forum: Hardware
---

### Post by brans041 on 2010-01-03
I have been playing around with the operation of the wireless switches on the laptop. There are two of them FN+F2 on the keyboard, and the physical switch on the front of the laptop. I have been playing around with the /etc/acpi/ and /etc/acpi/event scripts and have found that deleting the scripts do not stop the function of the wireless switches. 

Long story short where are the files that I would change to change the function of the wireless switches. Ultimately I would like to have FN+F2 turn on and off the wireless only (currently it does the wireless and bluetooth) and I would like the switch to turn off both the wireless and bluetooth (currently it does something different, not helpful, incorrect).

They give two ACPI signals so I thought that it would be in the ACPI events, those scripts didn't change the operation. I deleted them so I could try to find what makes the change. Couldn't find it.

Here are the ACPI Signals if you need to know.

FN+F2
5d, 7e off
5d, 7d on

switch
5d, 7e off
5e, 7d on

Ultimately I would like to build some code that would send the info the libnotify. I can do that if I know where to change stuff. 

I am comfortable changing driver files and can read code. I am not worried about losing the install. Just need help.

System Information:
Ubuntu 9.10_86_64
Asus M50sa

Wireless Card lspci info
07:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Device 1100
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at fe9fe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number fb-52-6e-ff-ff-3b-1f-00
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

Thanks in Advance,

EGB

---

### Post by brans041 on 2010-01-03
Oh, almost forgot. The Wireless LED is not turning on and off either. I tried changing the value in /sys/devices/platform/asus_laptop/wlan but it didn't do anything. Help me with this too.

---

### Post by jeast on 2010-04-02
Have you tried the workaround by Donatas Glodenis posted on Launchpad:

> As for me, my notebook Asus A8F running Kubuntu 9.10 is also affected. I also noticed that, besides the need to correct the end of file **/usr/share/acpi-support/state-funcs** , the **/etc/acpi/events** scripts have wrong acpi event in my case, so I had to create a new file there and put this in it a corrected keycode **0000005d** instead of the 0000005e or 0000005f:

```
cat /etc/acpi/events/asus-wireless
```
[INDENT]event=hotkey (ATKD|HOTK) 0000005d[/INDENT]
[INDENT]action=/etc/acpi/asus-wireless.sh[/INDENT]

and Filippo Carletti:

> Kernel 2.6.31 introduced a small change in asus-laptop.c:
**#define ASUS_HOTK_FILE KBUILD_MODNAME**
instead of
#define ASUS_HOTK_FILE "asus-laptop"

So, now, all asus-laptop specific settings live in
**/sys/*/asus_laptop**
instead of
/sys/*/asus-laptop

I have Asus N51vf and it worked for me, hope it will change your situation too.

Link to the original thread: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451108]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451108")

---

