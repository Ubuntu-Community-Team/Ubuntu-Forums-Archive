---
title: "HP Printer Not Found"
date: 2008-05-24
forum: Hardware
---

### Post by lordfkiller on 2008-05-24
Hi everyone.

My HP photosmart 7760 used to work very well with my old computer and Feisty. But it no more does with my new computer. The printer was found by Administration --> Printing at first, but not working. I deleted it. Now neither Printers tool nor hp-setup find it.

Output of sudo tail -f /var/log/syslog when printer is connected:

May 24 19:08:46 farshid-desktop kernel: [ 6380.772379] usb 3-1: new full speed USB device using uhci_hcd and address 66
May 24 19:08:46 farshid-desktop kernel: [ 6380.892179] usb 3-1: device descriptor read/64, error -71
[Repeated several times]


System info: 
ASUS Commando main board
Intel 2.66 GHz Core 2 Duo processor
OS: Hardy 64-bit

Thanks for any help.

---

### Post by revidnus on 2008-05-24
Just a thought have you tried printconf in the synaptic package manager? It 
"automatically configures USB and parallel printers with CUPS"

---

### Post by lordfkiller on 2008-05-24
When turning the printer off, I noticed that it does not turn off. After unplugging the device and re-plugging it, the problem was solved!

---

### Post by lordfkiller on 2008-06-09
This is happening again and again. My printer crashes and I have to unplug the power cord.
The printer only crashes when I'm using Ubuntu and works well with Windows.
By the way, it seems that it crashes when a print command is sent.

Any help is appreciated.

---

### Post by misio129 on 2009-08-03
hey i had the same problem, my hp printer wasn't being found by either the 'printconf' command or the hp setup utility. turns out that the usb cable was faulty, and now it works great! :) its a good idea to check your cables, as the problem isn't always with the software.

---

