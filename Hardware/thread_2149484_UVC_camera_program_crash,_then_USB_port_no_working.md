---
title: "UVC camera program crash, then USB port no working anymore"
date: 2013-05-28
forum: Hardware
---

### Post by lance7 on 2013-05-28
Hi,

I have one program to run UVC camera
After a segfault,  my usb port are all no response.

Ubuntu 12.04, 3.5.0-30-generic, 64bit, usb 3.0 port -> usb 3.0 hub with one usb 2.0 camera and one NIC

Here is dmesg:

[  131.838543] full[2366]: segfault at 7f2d47f81000 ip 00007f2d4643e59b sp 00007fff26aad838 error 7 in libc-2.15.so[7f2d463b2000+1b5000]
[  131.952214] xhci_hcd 0000:00:14.0: Signal while waiting for configure endpoint command
[  131.952256] usb 3-2.2: Not enough bandwidth for altsetting 0
[  131.952258] xhci_hcd 0000:00:14.0: WARN Set TR Deq Ptr cmd with unknown completion code of 24.
[  135.203505] usb 3-2.2: USB disconnect, device number 3
[  136.954710] xhci_hcd 0000:00:14.0: xHCI host not responding to stop endpoint command.
[  136.954721] xhci_hcd 0000:00:14.0: Assuming host is dying, halting host.
[  136.954875] xhci_hcd 0000:00:14.0: HC died; cleaning up
[  136.957124] xhci_hcd 0000:00:14.0: Slot 3 endpoint 2 not removed from BW list!
[  136.957155] xhci_hcd 0000:00:14.0: Slot 3 endpoint 6 not removed from BW list!
[  136.957221] hub 3-2:1.0: hub_port_status failed (err = -19)
[  136.957241] hub 3-2:1.0: connect-debounce failed, port 2 disabled
[  136.957278] usb 3-2: USB disconnect, device number 2
[  136.957292] usb 3-2.4: USB disconnect, device number 4
[  136.957569] asix 3-2.4:1.0: eth0: unregister 'asix' usb-0000:00:14.0-2.4, ASIX AX88772 USB 2.0 Ethernet
[  138.258113] xhci_hcd 0000:00:14.0: Slot 4 endpoint 2 not removed from BW list!
[  138.258984] xhci_hcd 0000:00:14.0: Slot 2 endpoint 2 not removed from BW list!
[  138.259010] usb 4-2: USB disconnect, device number 2
[  138.259072] usb 4-2: Failed to set U1 timeout to 0x0,error code -19
[  138.259080] usb 4-2: Set SEL for device-initiated U1 failed.
[  138.259085] usb 4-2: Set SEL for device-initiated U2 failed.
[  138.259122] usb 4-2: Failed to set U1 timeout to 0x0,error code -19
[  138.259127] usb 4-2: Set SEL for device-initiated U1 failed.
[  138.259132] usb 4-2: Set SEL for device-initiated U2 failed.

---

### Post by mischr on 2013-10-02
Hello,

i have same Problem on 
Linux Aspire-V3-771 3.8.0-31-generic #46~precise1-Ubuntu SMP Wed Sep 11 18:21:16 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

can anyone help please?

---

