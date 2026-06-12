---
title: "Venus Fast2 Modem is Not Working"
date: 2011-10-19
forum: Hardware
---

### Post by mardangga on 2011-10-19
Hello everyone.....
I've problem with my Venus Fast2 modem in Kubuntu 11.10. When I try to view my modem using "lsusb" in terminal, it's stuck as storage device. I've try to use commands 
"sudo usb_modeswitch -c /etc/usb_modeswitch.d/venus_fast2"
where for the contents of the venus_fast2 file is like this:
> 
# Venus Fast2 (white)

DefaultVendor=0x05c6
DefaultProduct=0×1000

TargetVendor=0x19f5
TargetProduct=0×9909

CheckSuccess=20

MessageContent=”55534243105c838a000000000000061e000000010000000000000000000000&#8243;
NeedResponse=1

The output that I got after running the above command is something like this:
> 
Looking for target devices …
No devices in target mode or class found
Looking for default devices …
Found devices in default mode, class or configuration (1)
Accessing device 004 on bus 006 …
Getting the current device configuration …
Error getting the current configuration (error -110). Assuming configuration 1.
Using endpoints 0×09 (out) and 0×88 (in)
Inquiring device details; driver will be detached …
Looking for active driver …
No driver found. Either detached before or never attached

Can anyone help me to fix my problem??
Thanks in advance and forgive me for my poor English.

---

### Post by mardangga on 2011-10-22
Please help me to fix these problem. I can't get it to work. I don't know how to make it work.

---

