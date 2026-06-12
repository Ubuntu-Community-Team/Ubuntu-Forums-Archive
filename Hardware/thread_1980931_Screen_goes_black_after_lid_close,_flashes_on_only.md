---
title: "Screen goes black after lid close, flashes on only when moving mouse."
date: 2012-05-16
forum: Hardware
---

### Post by iceparrot on 2012-05-16
I have installed 12.04 from a USB stick and applied all updates through update manager.   The system is a Acer Aspire D250 (with an Intel Graphics card, no restricted driver needed)

The issue is that if I close the lid (no matter what the lid action is set to) the screen turns off, and then only shows a short "flicker" if I move the mouse.  I can get to the terminal normally with Ctrl-Alt-F1, and the screen works fine there.  

Workarounds Tried:
Restart X server with LCtrl-PrSrc-K -  it does not resolve the issue, get brought to login screen where screen still only flashes when I move the mouse

Suspend and resume system - no change in behavior

Reboot system:  This (as expected) does work, but isn't much of a workaround!

Suspend before closing lid - This also works of course.


Happy to try any workarounds or ideas to fix the issue, just need some suggestions!

---

### Post by 2F4U on 2012-05-16
Did you change the settings in the Power Management application?

---

### Post by iceparrot on 2012-05-16
Yes, I tried changing them to both suspend and no action, neither has any effect.   The system also does not suspend when the lid closes (but it may be a separate issue.)

---

### Post by agustjin on 2012-07-09
I'm having the same problem here with my D250. The netbook won't suspend whatever I choose in lid-close action which is another matter. But after reopenning the lid the screen remains black and flashes only when I move the mouse. Could anyone help? Pls?:confused:

---

### Post by Smelost on 2012-08-06
The same thing with Acer Aspire One D150.
Tried with lightdm restart, but nothing changed, it is still dark and flickers on mouse move. Linuxmint is Ubuntu based and the problem still persits. The only exceptions by now are Fedora & Debian.
Finaly I think that the problem is with the Intel Mobile Express video "drivers".

---

### Post by Smelost on 2012-08-06
Again.
Tried on Dell Inspiron 1525 which uses Mobile Intel 965 Express Graphics and the result after closing the lid and "Do Nothing" option set is when opened again it freezes with only mouse cursor moving...

---

### Post by Smelost on 2012-08-07
Guys, just found an admissible solution which is nice for me.

Watching over the processes I've found a lid.sh running on lid opening and I removed the file and did a reboot then closed the lid again and it started working like "Do Nothing" option.

Will dig around to examine the script and see what goes wrong, but deleting it is an acceptable walkthrough by now.

Location: /etc/acpi/lid.sh

---

### Post by mthomure on 2012-08-23
I see the same problem on an Acer Aspire One KAV10/D150. Interestingly, the lid state seems to be misreported on my system:

> cat /proc/acpi/button/lid/LID0/state
state:      closed

which, of course, it's not. Thus, it seems as though lid.sh runs on a "panel open" event, but mistakenly configures the display for a "panel close" event.

The following *might* be relevant:
[https://wiki.ubuntu.com/X/Quirks#Intel_No_Display_After_Lid_Close_Quirks:_i915.2BAC8-intel_lvds.c](https://wiki.ubuntu.com/X/Quirks#Intel_No_Display_After_Lid_Close_Quirks:_i915.2BAC8-intel_lvds.c)

Does anybody know how to fix the reported lid state?

Also, this problem seems identical to [http://ubuntuforums.org/showthread.php?t=1542323](http://ubuntuforums.org/showthread.php?t=1542323), though the fix may not be applicable anymore.

Thanks!

---

### Post by Jackalux on 2013-03-27
Also bugging me with exact same symptoms as OP.  Did you get anywhere with the following look at lid.sh?
Possibly this same issue that means I can't close lid when watching a film on an ext monitor (with LidClose=DoNothing)
I'd appreciate some non-native Unix instructions on how to resolve.  Cheers!

> **Smelost said:**
> Guys, just found an admissible solution which is nice for me.

Watching over the processes I've found a lid.sh running on lid opening and I removed the file and did a reboot then closed the lid again and it started working like "Do Nothing" option.

Will dig around to examine the script and see what goes wrong, but deleting it is an acceptable walkthrough by now.

Location: /etc/acpi/lid.sh

---

