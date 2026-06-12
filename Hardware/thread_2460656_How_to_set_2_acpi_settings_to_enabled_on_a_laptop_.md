---
title: "How to set 2 acpi settings to enabled on a laptop via bash script at boot"
date: 2021-04-15
forum: Hardware
---

### Post by ahbart on 2021-04-15
I'm on Ubuntu 20.10. It runs on a laptop.
It is running very well, but I still have a small issue with power management. When I close the lid, the laptop suspends. But when I open it, it does not wake up. 
I do know that I can set LID0 and XHC1 with an echo to /proc/acpi/wakeup. When you echo these, then it is switched. So possibly I switch it off while I want it to have enabled. 
Therefor I've found a script on askubuntu, that works well with 1 device, but not with 2. But the script was made for more then one device.

This is the original script:
```
#!/bin/bash

declare -a devices=("EHC1 EHC2 XHCI") # <-- Add your entries here
for device in "${devices[@]}"; do
    if grep -qw ^$device.*enabled /proc/acpi/wakeup; then
        sudo sh -c "echo $device > /proc/acpi/wakeup"
    fi
done
``` made, or reposted by a user: Hrishikesh Kadam on: [AskUbuntu]("https://askubuntu.com/questions/1146264/apply-the-proc-acpi-wakeup-settings-permanently/1331422#1331422").

In: "cat /proc/acpi/wakeup" these are the XHC1 and LID0 items:
```
XHC1      S3    *disabled   pci:0000:00:14.0 
LID0      S4    *disabled  platform:PNP0C0D:00
```

I changed the script that I've found like this:
```
#!/bin/bash
declare -a devices=("XHC1 LID0")
for device in "${devices[@]}"; do
    if grep -qw ^$device.*disabled /proc/acpi/wakeup; then
        sudo sh -c "echo $device > /proc/acpi/wakeup"
    fi
done
```
Which does not look wrong to me. 

But than I get this error: ```
grep: LID0.*disabled: File or folder does not exist
```
(I translated from dutch) 
When I change the code like this: 
```
declare -a devices=("XHC1")
```
 so by removing 1 device, then the code works. 

Finally I want to set the script as ExecStart in systemd.
Why does this not work anymore? What changed in the way this is working? And how do I fix this script for Ubuntu 20.10? Please advise.
Anyone?

---

### Post by coffeecat on 2021-04-15
[Duplicate thread]("https://ubuntuforums.org/showthread.php?t=2460602"). Closed.

---

