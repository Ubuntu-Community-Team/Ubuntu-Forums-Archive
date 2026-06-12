---
title: "USB problem"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by wcgoh on 2007-11-02
Hi,

Currently running Ubuntu 7.10. Experiencing problem with the ATEN KVM, suspecting it is because it has to do with the way ubuntu handling the usb hub in the kvm. Here is the usb and the debug.
```

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 003: ID 04f2:0111 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0557:7000 ATEN International Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
```

```
[  840.562691] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  841.134091] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  842.352818] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  842.924214] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  844.087997] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  844.659405] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  845.718293] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  846.349624] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  847.436503] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  848.043865] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  849.154692] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  849.738092] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  850.784993] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  851.432305] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  852.535151] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  853.126520] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  854.820731] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  855.380142] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  856.514943] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  857.394018] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  858.209163] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  859.903372] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  861.229970] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  861.801367] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  863.211879] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  863.783284] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  864.906105] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  865.477509] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  867.087803] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  867.659199] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  869.349417] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  869.948777] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  871.043624] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  872.202405] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  872.773811] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  873.984528] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  874.555930] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4
[  875.886527] usb 2-1.1: reset low speed USB device using ohci_hcd and address 3
[  876.458934] usb 2-1.2: reset low speed USB device using ohci_hcd and address 4

```

as you can see there is a lot of reset. Can the reset be stop?
Due tttto the reset ai am ping like this.

---

