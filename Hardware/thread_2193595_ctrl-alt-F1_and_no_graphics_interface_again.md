---
title: "ctrl-alt-F1 and no graphics interface again"
date: 2013-12-13
forum: Hardware
---

### Post by etielsolrac on 2013-12-13
Hi

Apparently, everything is working well as long as I don't change to a terminal  (eg. ctrl-Alt-F1), in text mode. If I do that, I won't be able to start lightdm again (ctrl-alt-F8 or other combinations won't do any better ), even after rebooting. I had to reinstall ubuntu to solve the problem:

(Ubuntu 13.10 installed on a usb hard drive)

Laptop Toshiba Qosmio - F750   (GeForce GT 540M, NVidia compatible)
+ monitor Samsung VGA
+ another keyboard on a usb port
+ wireless mouse

There are ACPI errors reported, so I would like to know if I must install any ACPI driver or if there is another solution.


Thank you

---

### Post by varunendra on 2013-12-15
It might help if you post the exact error messages that look suspicious to you.

Have you tried various boot options? Especially nomodeset and/or acpi related ones :
[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

And by the way, it is 'Ctrl-Alt-**[COLOR="#FF0000"]F7[/COLOR]**', not **F8**, to return to gui from the virtual tty.

---

### Post by etielsolrac on 2013-12-16
errors:

[   11.060939] [drm] GMBUS [i915 gmbus panel] timed out, falling back to bit banging on pin 3
[   11.085596] [drm] Wrong MCH_SSKPD value: 0x16040307
[   11.085598] [drm] This can cause pipe underruns and display issues.
[   11.085599] [drm] Please upgrade your BIOS to fix this.
[   11.115415] fbcon: inteldrmfb (fb0) is primary device
[   11.404057] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   11.404095] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
[   11.404122] ACPI Warning: \_SB_.PCI0.PEGP.VGA_._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   11.404142] ACPI Warning: \_SB_.PCI0.PEGP.VGA_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
[   11.435204] Linux video capture interface: v2.00
[   11.461397] Console: switching to colour frame buffer device 160x48
[   11.464408] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   11.464409] i915 0000:00:02.0: registered panic notifier
[   11.464450] nouveau 0000:01:00.0: enabling device (0004 -> 0007)
[   11.464568] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20130517/video-126

It seems that the problem is caused by changes of resolution when passing to text mode... I don't see why the trouble remains after booting.
I didn't dare to change any parameters...
 As to ctrl-alt-..., I've tried them all.

---

### Post by varunendra on 2013-12-17
The first link I posted lists the commonly used parameters. The second one tells in detail how to add them temporarily (just for one session).

And have you checked Toshiba's website to see if an updated BIOS is available for your model?

---

### Post by etielsolrac on 2013-12-17
> **varunendra said:**
> The first link I posted lists the commonly used parameters. The second one tells in detail how to add them temporarily (just for one session).

And have you checked Toshiba's website to see if an updated BIOS is available for your model?

I'll try to change some of those parameters.
I have checked Toshiba's website and there is no update available.

Thank you for your help

---

