---
title: "Sund Card or Network problems - desktip"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by SailorFrank on 2007-05-05
Hi experts
New to linux using Ubunto to give a Me Athlon desktop new lease of life. Love the GUI and the apps but...

Have 5PCI slots Ensoniq 5880, Network card Netvin NV5000sC.
in Unbuntu both card have worked though never together (fine in Windows so not hardware fault).  First Ubuntu install had sound and no network, reinstall swapped this when I first took out the sound card.  Position in slots seems to make a difference and to whether a card is recognised. Sound device appears clearly under "System/Hardware" menu

Have tried some of the fixes in the forum.  Appears the right sound card module is available.
Currently sound icon is there, red circle thought it clicking give message "No volume control GStreamer plugins and/or devices found"

Have gone through the great guide at:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+card+guide+fixing](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+card+guide+fixing)

aplay -l
aplay: device_list:222: no soundcards found...

but is listed in lspci (attached) and drive is supported ens1371 (and sound  did work )
tried "sudo modprobe snd-ens1371" but no fix and inserting module into file  /etc/modules

 and dmesg output attached

What do I do next ? Is it an IRQ problem ?

Thanks in anticipation !

---

