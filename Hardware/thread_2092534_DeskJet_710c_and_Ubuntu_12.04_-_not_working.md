---
title: "DeskJet 710c and Ubuntu 12.04 - not working"
date: 2012-12-08
forum: Hardware
---

### Post by mac1234mac on 2012-12-08
Hello,

I've got problem [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/smile.gif[/IMG]. Here is output of 'sudo lsusb':

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13fe:1f23 Kingston Technology Company Inc. 
Bus 002 Device 002: ID 13d3:5111 IMC Networks Integrated Webcam
[B]Bus 003 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
[/B] 

Bold font is usb-parallel adapter. So it is discovered in the system.

In the configuration panel of the printer, URI is as follows:

usb://Unknown/Printer

And the printer screams that:

Idle - Unable to send data to printer.

When I try to print some document, it's processed for a moment and then it is suspended.

System shows that the printer is OK (green tick).

I'd like to add that there is no /dev/usb/lp0. When I try to print it  vanishes. I have to unplug usb and connect it again and /dev/usb/lp0  appears again.

Could You, please, tell me what's going on?.

Thank You for Answer,

Mac.

---

### Post by kurt18947 on 2012-12-08
I am a very long ways from an expert but here are my thoughts.  They're worth what you're paying for them :).


[LIST]
[*]The fact that a device shows up on a 'lsusb' list doesn't mean it's 100% functional.
[*]Do you have HPLIP & HPLIP-gui installed?  They usually simplify installing and administering HP printers.
[/LIST]

---

