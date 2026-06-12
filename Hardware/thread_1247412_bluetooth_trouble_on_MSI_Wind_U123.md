---
title: "bluetooth trouble on MSI Wind U123"
date: 2009-08-22
forum: Hardware
---

### Post by jms1989 on 2009-08-22
As stated in the title I have a MSI Wind U123 and am experiencing some bluetooth trouble. First, once I have my bluetooth mouse paired, it randomly resets the connection. At first, I thought it was having something to do with a piece of software from the ubuntu netbook remix software set but I keep getting connection drops every 30 seconds but it takes at least 15 to come back online and another 5 or 10 to reconnect. Then I just have only 5 seconds to use it and it resets again.

Here is some output of from the kernel...

```

Aug 22 20:10:51 mini-me kernel: [18253.712145] usb 5-1: USB disconnect, address 31
Aug 22 20:10:51 mini-me kernel: [18253.712257] btusb_intr_complete: hci0 urb ede3c880 failed to resubmit (19)
Aug 22 20:10:51 mini-me kernel: [18253.712280] btusb_bulk_complete: hci0 urb ede3c100 failed to resubmit (19)
Aug 22 20:10:51 mini-me kernel: [18253.713273] btusb_bulk_complete: hci0 urb ede3ca80 failed to resubmit (19)
Aug 22 20:10:51 mini-me kernel: [18253.715447] btusb_send_frame: hci0 urb d58cbf00 submission failed
Aug 22 20:10:52 mini-me kernel: [18254.696166] usb 5-1: new full speed USB device using uhci_hcd and address 32
Aug 22 20:10:52 mini-me kernel: [18254.906535] usb 5-1: configuration #1 chosen from 1 choice
Aug 22 20:11:08 mini-me kernel: [18270.549397] input: Bluetooth Mouse as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/bluetooth/hci0/hci0:39/input43
Aug 22 20:11:08 mini-me kernel: [18270.564358] generic-bluetooth 0005:0A12:1005.0022: input,hidraw33: BLUETOOTH HID v0.21 Mouse [Bluetooth Mouse] on 00:24:21:8F:A8:4C

```

Perhaps you guys can make some since of it?

---

