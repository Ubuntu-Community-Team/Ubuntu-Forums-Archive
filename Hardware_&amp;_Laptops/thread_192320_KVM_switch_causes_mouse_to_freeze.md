---
title: "KVM switch causes mouse to freeze"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by 18nikko on 2006-06-08
Hi,
I have an IOGEAR 2-port usb KVM switch and a microsoft trackball explorer 1.0 usb mouse. Whenever I switch to my laptop and then switch back to my destop the mouse freezes. From the posts I have read, it seems when switching back the mouse is not restarted. Has anyone fixed this problem? I am running Ubuntu 6.06. I have a similar setup at work running fedora 5 and I have had no problems.

Here is my xorg.conf 

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mouse1"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

from what I have read this could use some tweaking anyway.

Thanks in advance for any help.

Nicholas

---

### Post by woodythdog on 2006-06-12
Any luck fixing this?   I am having the same trouble :-(

---

