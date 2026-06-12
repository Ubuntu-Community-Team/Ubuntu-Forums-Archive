---
title: "Elantech Touchpad not detected"
date: 2023-04-02
forum: Hardware
---

### Post by asearle on 2023-04-02
Hallo Everyone,

I have two "Terra" laptops (a 1460p and 1450ii) both with Elantech touchpads which originally worked when, in the BIOS, legacy-mode was selected.

Now legacy-mode is no longer available (only UEFI) and the touchpads are visible neither with "cat /proc/bus/input/devices" nor "xinput list".

I have trawled through the internet trying all kinds of suggestions (changing GRUB_CMDLINE_LINUX in GRUB and installing/deinstalling various xserver-xorg components) but nothing has helped.

My suspicion is that it is a BIOS-level problem (UEFI?) so I am hoping that someone out there can help me(?)

Any ideas?  Any suggestions on how I can diagnose/fix this problem?  ... it is driving my crazy having to lug a mouse around with me!!!!

Many, many thanks,
Alan (in Cologne)

PS: I have tried with other distros including a usb-live-stick of Manjaro Linux, which is supposed to have good hardware-recognition, but got the same result.

PS #2: I checked the BIOS and see that the laptop has an Insyde H2O 52.10 BIOS.  I have looked around in the menus (a lot) but cannot see an option to activate/deactivate the touchpad.

---

### Post by devmarxx on 2023-11-08
I got the touchpad running on my Terra 1460p on Debian 12 by changing the ACPI settings in the BIOS from 5.1 to 6.1. 

After doing so the trackpad ran out of the box.

Hope this is of some help.

Regards

devmarxx

---

### Post by devmarxx on 2023-11-08
Sorry, I have to correct myself ...

After the third reboot it stopped working. Confusing ...

At least I know now that it did work. I will have to dig deeper.

marxx

---

### Post by devmarxx on 2023-11-09
OK, I now can reproduce the start of the touchpad on my Terra 1460p with Debian 12.

I downloaded Hiren's BootCD PE and made me a bootable USB Stick with Hiren's Windows 10 on it.

1. Boot the laptop from the Hiren's BootCD PE USB stick.
2. Wait till completely up and running.
3. The touchpad is working (sure, it is a Windows that we are running on now).
4. Reboot directly into Linux via "Start" -> "Shut down" -> "Restart".

- The touchpad works fine now under Linux
- Even after a reboot from Linux to Linux
- It won't survive hibernation
- It won't survive shutdown and a new boot.

So not for daily usage, but we now can compare log files from the states "working" and "not working".

Regards

devmarxx

---

### Post by devmarxx on 2023-11-10
Solved :-)

I found this thread [https://bugzilla.kernel.org/show_bug.cgi?id=81331](https://bugzilla.kernel.org/show_bug.cgi?id=81331) describing the exact problem. And they have the solution there.

So I ran 'sudo -H gedit /etc/default/grub' and added i8042.kbdreset=1 to the line GRUB_CMDLINE_LINUX.

This is how it looks:

GRUB_CMDLINE_LINUX="i8042.kbdreset=1"

Then I saved the file and ran

sudo update-grub

After a shutdown and restart the touchpad is still running :-)

Regards

devmarxx

---

