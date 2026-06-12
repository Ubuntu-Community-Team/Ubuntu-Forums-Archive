---
title: "Help recovering after bad bad video driver install"
date: 2010-03-19
forum: Hardware
---

### Post by billdodd on 2010-03-19
Howdy,

I have Ubuntu 9.10 installed on a Lenovo W500 laptop. Today I decided to
install the proprietary ATI/AMD graphics driver that was shown as available
in the "Hardware drivers" Administration menu. I clicked "Activate" and it
installed and told me I needed to reboot.

But on reboot the display was blank (splash screen did appear, but then
went blank). Rebooted again and hit escape at "Grub loading", but can't get
the grub menu in order to boot single user (screen is garbled and
unreadable).

I'm downloading a Live CD now to boot from, but could use some advice
on how to recover after this mishap. Will I be able to uninstall the
graphics driver package from the hard drive after booting from the CD?

Any pointers/advice greatly appreciated!

Bill

---

### Post by 2hot6ft2 on 2010-03-19
> **billdodd said:**
> Howdy,

I have Ubuntu 9.10 installed on a Lenovo W500 laptop. Today I decided to
install the proprietary ATI/AMD graphics driver that was shown as available
in the "Hardware drivers" Administration menu. I clicked "Activate" and it
installed and told me I needed to reboot.
Hi, sorry to hear that you're having problems. Welcome to the forum and to Ubuntu.
> **billdodd said:**
> But on reboot the display was blank (splash screen did appear, but then
went blank). Rebooted again and hit escape at "Grub loading", but can't get
the grub menu in order to boot single user (screen is garbled and
unreadable).
9.10 uses grub2 so esc doesn't get you to the grub menu anymore, now you press the Shift key to get to it.
> **billdodd said:**
> I'm downloading a Live CD now to boot from, but could use some advice
on how to recover after this mishap. Will I be able to uninstall the
graphics driver package from the hard drive after booting from the CD?

Any pointers/advice greatly appreciated!
If you can get to the grub screen and choose recovery mode, once all the text scrolls by you should be presented with some options. I would suggest trying the Fix X Server option first and once that finishes then choose the Boot Normally option. I think those options are still there.
Someone correct me if they're not.

---

### Post by billdodd on 2010-03-20
Thanks 2hot6ft2 - using the Shift key I was able to get to the Grub
menu and boot into recovery mode.

Unfortunately there was no "Fix X Server" option. The options are
"Resume normal boot", "Try to make free space",
"Repair broken packages", "Update grub boot loader" and drop
to root shell, with and without networking.

I ran "Repair broken packages", but there was nothing really broken to
repair, so that didn't help any. I've dropped into a root shell with
networking and am doing further research. If anybody has any more
suggestions, please let me know.

Thanks,
Bill

---

### Post by jrssystemsnet on 2010-03-20
> **billdodd said:**
> Thanks 2hot6ft2 - using the Shift key I was able to get to the Grub
menu and boot into recovery mode.

Unfortunately there was no "Fix X Server" option. The options are
"Resume normal boot", "Try to make free space",
"Repair broken packages", "Update grub boot loader" and drop
to root shell, with and without networking.

I ran "Repair broken packages", but there was nothing really broken to
repair, so that didn't help any. I've dropped into a root shell with
networking and am doing further research. If anybody has any more
suggestions, please let me know.

Thanks,
BillGet to a root shell with networking, make sure your networking is actually getting you to the internet, and ```
sudo apt-get remove xorg-driver-fglrx
``` should get you squared away.

If that doesn't do it, you'll have to edit your xorg.conf file.  Oh frabjous joy. :)

---

### Post by billdodd on 2010-03-20
It was indeed frabjous joy. :)

I removed the fglrx driver and rebooted, but still
did not have working X windows. Checked xorg.conf
and changed the driver from "fglrx" to "radeon".
Rebooted. Still broken.

Looked at the /var/log/Xorg.N.log files and 'lspci'
output. There were 2 video devices seen, the built-in
Intel and the ATI. But the built-in Intel was the
"primary" and this seemed to prevent the X server from
being able to read the ATI rom. Some Xorg.N.log output:

```

...
(--) PCI:*(0:0:2:0) 8086:2a42:17aa:2115 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xfc000000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
(--) PCI: (0:1:0:0) 1002:9591:17aa:2126 ATI Technologies Inc Mobility Radeon HD 3650 rev 0, Mem @ 0xc0000000/268435456, 0xbfff0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
...
(II) RADEON(0): initializing int10
(EE) RADEON(0): Cannot read V_BIOS (3) Input/output error
...
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
...

```

Went into the BIOS and changed a display setting from
"Switchable" to "Discreet" (ATI), so that the ATI device
would be the primary (only) device.

After this, I was finally able to get X running
successfully.

---

