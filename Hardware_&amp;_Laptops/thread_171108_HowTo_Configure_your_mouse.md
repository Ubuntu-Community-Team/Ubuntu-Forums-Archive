---
title: "HowTo: Configure your mouse"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by BomanAJeff on 2006-05-05
Apologies if this was already answered (most likely; I'll bet it's one of the first things folks fix)... I just couldn't find an answer 9 pages into a search:

When I load up Linux (ANY flavor) my mouse cursor flies all over the screen on its own, picking its own commands to press. 

I'm guessing this can be fixed with just one option in the settings, but I haven't figured out which one. Could anyone here help me (or point me to the thread that answered it already)?

---

### Post by BomanAJeff on 2006-05-09
No answers yet - but in the past 10 minutes alone windows have been opening and closing all over, desktop stuff keeps getting rearranged, and I've tried everything I can figure to get it to stop. Can someone please help?

---

### Post by Slavus on 2006-05-09
That sounds like a hardware problem-- try using a different mouse? switching from PS2 to USB, changing ports, fiddle with the hardware

other than that I cant give any answers

---

### Post by aineko on 2006-05-09
[QUOTE=BomanAJeff]
When I load up Linux (ANY flavor) my mouse cursor flies all over the screen on its own, picking its own commands to press. [/QUOTE]

I'm experiencing the same problem.  I don't believe it's hardware-related, as I tried to fix it by using a different mouse.  However, the problem was identical using either of the two PS/2 mice (a 3-button CountorMouse and a 2-button Microsoft Mouse.)  Both mice work fine under Windows XP.  Both mice also worked fine under Ubuntu 5.04 before the latest xorg upgrade.  

I think the problem is the latest X-Windows from xorg under both Ubuntu 5.04 and 5.10.  My Xorg.conf worked fine under 5.04 prior to the xorg upgrade.  Running dpkg-reconfigure xorg-xserver doesn't change my Xorg.conf.

---

### Post by aineko on 2006-05-10
[QUOTE=aineko]I think the problem is the latest X-Windows from xorg under both Ubuntu 5.04 and 5.10.  My Xorg.conf worked fine under 5.04 prior to the xorg upgrade.  Running dpkg-reconfigure xorg-xserver doesn't change my Xorg.conf.[/QUOTE]

Is the xserver-xorg-input-mouse package new?  Could this be causing the problem?

---

### Post by DiGiTY on 2006-05-10
i've been having the same problem ever since i've installed Ubuntu (6.04 then, 6.06 now) on my laptop a couple of months ago. the trackpad, ps/2 and usb mice all gives me the same issues (though the trackpad is far worse and unstable). i've tried a couple of fixes but nothing truly works yet

---

### Post by aineko on 2006-05-10
I fixed the problem ... almost, but it might be a full fix for some people.

I modified /etc/X11/xorg.conf to be as follows:

[INDENT]Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "ImPS/2"
EndSection[/INDENT]

This fixed the problem until I used my KVM switch to switch from Ubuntu to Windows.  When I returned to Ubuntu, mouse behavior was broken again and stayed that way until I rebooted.  After a reboot, it's fine again.  The problem is completely repeatable.

Everything worked fine before the May xorg upgrade.   I suspect something in the change when the mouse driver moved to the xserver-xorg-input-mouse package broke my Belkin Omniview KVM switch.

---

### Post by aineko on 2006-05-10
I fixed the KVM problem using the method from [http://www.ubuntuforums.org/showthread.php?t=28643&highlight=kvm]("http://www.ubuntuforums.org/showthread.php?t=28643&highlight=kvm").

I modified /etc/modules, replacing "psmouse" with

psmouse proto=imps

and rebooted the system.  I've switched between Ubuntu and Windows half a dozen times without any problems, so it looks like everything is okay now.

---

