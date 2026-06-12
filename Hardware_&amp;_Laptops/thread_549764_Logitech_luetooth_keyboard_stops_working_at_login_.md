---
title: "Logitech luetooth keyboard stops working at login screen"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by P00T1E on 2007-09-13
I installed Ubuntu Studio last week and I the Logitech Cordless MX Duo for Bluetooth, I am only using the keyboard at the moment cause the mouse is crap.
Anyways so here's what happens:
Turn on the computer and keyboard is working fine, Ubuntu Studio splash screen comes up and keyboard is still working fine. At this point my monitor loses sync for a sec as the resolution changes and keyboard stops responding. The bluetooth hub actually seems to "lock up" have to unplug it and plug it back in, and reconnect the keyboard to it.
I have tried editing a bluetooth config file to enable bluetooth at startup but it made no difference. Any Ideas?

---

### Post by kylemallory on 2007-09-20
I am having this exact same problem.  I'm not so sure that its the USB hub/controller that is crashing though, as much as the HID module.  I've had this problem since upgrading to Feisty, (Dapper and Edgy worked fine).  In my own research, it looks like GDM reinitializes all HID devices, and for whatever reason, either the driver, or the hardware itself doesn't like this idea.

Based on the contents of /var/log/messages:

kernel: [  160.568742] usb 1-2.1.4: new full speed USB device using ehci_hcd and address 10
kernel: [  160.662396] usb 1-2.1.4: configuration #1 chosen from 1 choice
kernel: [  160.662573] hub 1-2.1.4:1.0: USB hub found
kernel: [  160.662678] hub 1-2.1.4:1.0: 3 ports detected
kernel: [  160.964536] usb 1-2.1.4.2: new full speed USB device using ehci_hcd and address 11
kernel: [  161.063064] usb 1-2.1.4.2: configuration #1 chosen from 1 choice
kernel: [  161.264396] usb 1-2.1.4.3: new full speed USB device using ehci_hcd and address 12
kernel: [  161.367190] usb 1-2.1.4.3: configuration #1 chosen from 1 choice
kernel: [  161.391424] usbcore: registered new interface driver hiddev
kernel: [  161.394395] input: Logitech Logitech BT Mini-Receiver as /class/input/input7
kernel: [  161.394604] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.7-2.1.4.2
kernel: [  161.400703] input: Logitech Logitech BT Mini-Receiver as /class/input/input8
kernel: [  161.400962] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.7-2.1.4.3
kernel: [  161.401120] usbcore: registered new interface driver usbhid
kernel: [  161.401228] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
kernel: [  162.484513] NET: Registered protocol family 10
kernel: [  162.484591] lo: Disabled Privacy Extensions
kernel: [  162.484666] ADDRCONF(NETDEV_UP): eth1: link is not ready
kernel: [  164.506843] Bluetooth: L2CAP ver 2.8
kernel: [  164.506848] Bluetooth: L2CAP socket layer initialized
[COLOR="Red"]kernel: [  164.691540] BUG: at drivers/hid/hid-core.c:780 implement()
kernel: [  164.691544]
kernel: [  164.691545] Call Trace:
kernel: [  164.691569]  [_end+139523507/2130485360] :hid:hid_output_report+0x1a3/0x210
kernel: [  164.691580]  [_end+139564456/2130485360] :usbhid:hid_submit_ctrl+0x78/0x240
kernel: [  164.691588]  [_end+139565321/2130485360] :usbhid:usbhid_submit_report+0x199/0x200
kernel: [  164.691596]  [_end+139574289/2130485360] :usbhid:hiddev_ioctl+0x441/0xb00
kernel: [  164.691601]  [chrdev_open+394/480] chrdev_open+0x18a/0x1e0
kernel: [  164.691606]  [open_namei+680/1664] open_namei+0x2a8/0x680
kernel: [  164.691610]  [chrdev_open+0/480] chrdev_open+0x0/0x1e0
kernel: [  164.691613]  [__dentry_open+292/496] __dentry_open+0x124/0x1f0
kernel: [  164.691625]  [do_ioctl+105/160] do_ioctl+0x69/0xa0
kernel: [  164.691629]  [vfs_ioctl+674/736] vfs_ioctl+0x2a2/0x2e0
kernel: [  164.691636]  [sys_ioctl+108/176] sys_ioctl+0x6c/0xb0
kernel: [  164.691643]  [system_call+126/131] system_call+0x7e/0x83[/COLOR]


This BUG: at drivers/hid/hid-core.c:780 implement() calls repeatedly until I remove the Bluetooth dongle and reinsert it.  then its fine.

kernel: [  164.742632] Bluetooth: RFCOMM socket layer initialized
kernel: [  164.742645] Bluetooth: RFCOMM TTY layer initialized
kernel: [  164.742647] Bluetooth: RFCOMM ver 1.8
kernel: [  164.898755] usb 1-2.1.4.1: new full speed USB device using ehci_hcd and address 13
kernel: [  164.995954] usb 1-2.1.4.1: configuration #1 chosen from 1 choice
kernel: [  173.145149] usb 1-2.1.4: USB disconnect, address 10
kernel: [  173.145157] usb 1-2.1.4.1: USB disconnect, address 13
kernel: [  173.419223] usb 1-2.1.4.2: USB disconnect, address 11
kernel: [  173.419655] usb 1-2.1.4.3: USB disconnect, address 12
kernel: [  173.426163] hald-addon-keyb[5563] general protection rip:2abfc2ca221b rsp:7fffe84efca0 error:0
kernel: [  173.426552] hald-addon-keyb[5542] general protection rip:2b0fcbc4221b rsp:7fffdf551d10 error:0
kernel: [  188.199885] usb 1-2.1.4: new full speed USB device using ehci_hcd and address 14
kernel: [  188.293718] usb 1-2.1.4: configuration #1 chosen from 1 choice
kernel: [  188.293854] hub 1-2.1.4:1.0: USB hub found
kernel: [  188.294065] hub 1-2.1.4:1.0: 3 ports detected
kernel: [  188.595717] usb 1-2.1.4.2: new full speed USB device using ehci_hcd and address 15
kernel: [  188.695053] usb 1-2.1.4.2: configuration #1 chosen from 1 choice
kernel: [  188.698992] input: Logitech Logitech BT Mini-Receiver as /class/input/input9
kernel: [  188.699077] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.7-2.1.4.2
kernel: [  188.899525] usb 1-2.1.4.3: new full speed USB device using ehci_hcd and address 16
kernel: [  188.999633] usb 1-2.1.4.3: configuration #1 chosen from 1 choice
kernel: [  189.006989] input: Logitech Logitech BT Mini-Receiver as /class/input/input10
kernel: [  189.007202] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.7-2.1.4.3
gconfd (kmallory-6185): starting (version 2.18.0.1), pid 6185 user 'kmallory'


Given that the stack trace identifies that its a BUG I've written it off as a known issue.  Googling "drivers/hid/hid-core.c:780" turns up this Ubuntu bug.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99118](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99118)

---

