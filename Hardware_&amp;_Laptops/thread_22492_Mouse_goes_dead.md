---
title: "Mouse goes dead"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by MrPsycho on 2005-03-28
Hello

My intellimouse usb explorer goes dead after leaving the computer unattended for about half an hour.  The light is still on but moving the mouse produces no response.  I have a feeling this is some problem with acpi or whatnot, except I did not have this issue a month ago.

Here is my xf86config:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"Auto"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5" 
EndSection

```

Changing the protocol to usb or explorerps/2 or intellimouse makes no difference.

The zaxis is configured to match the buttons for the scroll wheel.  I did have imwheel installed recently but removing it hasn't corrected the problem.

This really is a problem for me as I have to restart my computer to redetect my mouse whenever I leave it unatteneded.  Thanks for your help.

---

### Post by mercurus on 2005-03-28
Is only the mouse locked up or is the kernel locked up?
(ie. when you come back after inactivity, does the keyboard work?)
If possible, use Ctrl-Alt-F1 to access a text terminal, and have a look through the X log file, dmesg, and syslog to see what is causing the problem.

If it happens frequently and the keyboard works, you can use Ctrl-Alt-Backspace to restart X too (rather than the whole machine).

If the lockup is absolute (ie. not JUST the mouse) is sleepd or acpid installed \ running ? Disable them and leave the computer idle and see if the same problem occurs. It is possible that the machine is detecting that it is idle and putting itself to sleep, and getting stuck half-way. Is it a laptop or a desktop machine ? Eitherway, the last few lines of the acpid logfile might help too ...

Cheers
mercurus

---

