---
title: "Local USB Printer not working"
date: 2006-01-12
forum: Hardware &amp; Laptops
---

### Post by xlancealotx on 2006-01-12
Morning, all as you see from the title I can't print! I have a Dell inspiron 300M and can print fine using an HP JetDirect network printer, but I now want to print to a local hp 880c via USB.

When I connect the printer, I recieve the following:
Jan 11 09:42:25 morpheus kernel: [4297513.936000] usb 1-1: new full speed USB de vice using uhci_hcd and address 11
Jan 11 09:42:25 morpheus kernel: [4297513.941000] drivers/usb/class/usblp.c: usb

I add it to the printers section, which now says ready. I use the reccomended HP drivers. I can then right click, select properties, and print test page. The printer starts, pulls in the paper, writes a few black lines, I then see in color the very top of the orange 'U" of the ubuntu logo, and then the printer stops. The icon changes to paused, I can click resume, which starts the printer again which then pauses again instantly with no new print lines.

Looking through the logs I also saw:
Jan 11 09:42:25 morpheus kernel: [4297513.643000] drivers/usb/class/usblp.c: usb lp0: nonzero read/write bulk status received: -75

Not sure if that is a help or not, I also tried using the other drivers after removing / readding the printer, much worse results.

Thanks much for any help.

Lance

---

