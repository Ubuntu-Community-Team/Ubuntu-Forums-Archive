---
title: "Zombie USB keyboard dies, comes back to life"
date: 2010-07-30
forum: Hardware
---

### Post by poubelle on 2010-07-30
Hi all,

I recently picked up a new USB keyboard to replace my old PS2 one. I've noticed, though, a couple of weird things about its behaviour that necessitate keeping both keyboards plugged in:

- It doesn't work until I've booted fully. Since I bypass a login, this means the keyboard doesn't work until *after* I've entered my password in the "unlock keyring" dialog.

- It seems to randomly disconnect itself and stops working. It equally randomly starts working again.

I was wondering if anyone could have a look at a snip of my log file and let me know what exactly is happening here. This is where it most recently disconnected and reconnected.

```
Jul 30 03:36:13 jubuntu kernel: [38028.490095] usb 2-10: USB disconnect, address 7
Jul 30 07:57:29 jubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="730" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 30 09:27:23 jubuntu kernel: [59098.290053] usb 2-10: new low speed USB device using ohci_hcd and address 8
Jul 30 09:27:23 jubuntu kernel: [59098.522200] usb 2-10: configuration #1 chosen from 1 choice
Jul 30 09:27:23 jubuntu kernel: [59098.532942] input: USB USB Keykoard as /devices/pci0000:00/0000:00:02.0/usb2/2-10/2-10:1.0/input/input12
Jul 30 09:27:23 jubuntu kernel: [59098.533323] generic-usb 0003:1C4F:0002.0008: input,hidraw1: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:02.0-10/input0
Jul 30 09:27:33 jubuntu kernel: [59108.531064] generic-usb 0003:1C4F:0002.0009: timeout initializing reports
Jul 30 09:27:33 jubuntu kernel: [59108.531377] input: USB USB Keykoard as /devices/pci0000:00/0000:00:02.0/usb2/2-10/2-10:1.1/input/input13
Jul 30 09:27:33 jubuntu kernel: [59108.531616] generic-usb 0003:1C4F:0002.0009: input,hidraw2: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:02.0-10/input1
Jul 30 09:29:24 jubuntu kernel: [59219.260064] usb 2-10: USB disconnect, address 8
```

This is being typed on the old keyboard, as the new one is currently ignoring me.

Let me know if I need to add more details. Thanks!

---

### Post by sydbat on 2010-07-30
> **poubelle said:**
> Hi all,

I recently picked up a new USB keyboard to replace my old PS2 one. I've noticed, though, a couple of weird things about its behaviour that necessitate keeping both keyboards plugged in:

- It doesn't work until I've booted fully. Since I bypass a login, this means the keyboard doesn't work until *after* I've entered my password in the "unlock keyring" dialog.

- It seems to randomly disconnect itself and stops working. It equally randomly starts working again.

I was wondering if anyone could have a look at a snip of my log file and let me know what exactly is happening here. This is where it most recently disconnected and reconnected.

```
Jul 30 03:36:13 jubuntu kernel: [38028.490095] usb 2-10: USB disconnect, address 7
Jul 30 07:57:29 jubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="730" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 30 09:27:23 jubuntu kernel: [59098.290053] usb 2-10: new low speed USB device using ohci_hcd and address 8
Jul 30 09:27:23 jubuntu kernel: [59098.522200] usb 2-10: configuration #1 chosen from 1 choice
Jul 30 09:27:23 jubuntu kernel: [59098.532942] input: USB USB Keykoard as /devices/pci0000:00/0000:00:02.0/usb2/2-10/2-10:1.0/input/input12
Jul 30 09:27:23 jubuntu kernel: [59098.533323] generic-usb 0003:1C4F:0002.0008: input,hidraw1: USB HID v1.10 Keyboard [USB USB Keykoard] on usb-0000:00:02.0-10/input0
Jul 30 09:27:33 jubuntu kernel: [59108.531064] generic-usb 0003:1C4F:0002.0009: timeout initializing reports
Jul 30 09:27:33 jubuntu kernel: [59108.531377] input: USB USB Keykoard as /devices/pci0000:00/0000:00:02.0/usb2/2-10/2-10:1.1/input/input13
Jul 30 09:27:33 jubuntu kernel: [59108.531616] generic-usb 0003:1C4F:0002.0009: input,hidraw2: USB HID v1.10 Device [USB USB Keykoard] on usb-0000:00:02.0-10/input1
Jul 30 09:29:24 jubuntu kernel: [59219.260064] usb 2-10: USB disconnect, address 8
```

This is being typed on the old keyboard, as the new one is currently ignoring me.

Let me know if I need to add more details. Thanks!Above and beyond the fact that this signals the Zombie Apocalypse, I think that there is a problem with the USB keyboard...some defect of manufacturing. I suggest taking it back and have the store replace it. If the problem persists with the replacement, then we can look into other reasons why it is not working properly.

Oh, can you tell us what the make/model of the keyboard is? I just got a Logitech MK300 wireless myself, and it mostly seems to work fine (there are a couple of buttons not working). I have found that Logitech does not provide Linux "drivers", but there are many other manufacturers who do provide drivers/specs, so there might be a solution in System > Preferences > Keyboard.

---

### Post by poubelle on 2010-07-30
Thanks for replying. The keyboard is a no-name made-in-China-type thing, so this might not mean much, but IIRC it's reported as "Sigma" brand when I ran lsusb. (I can't run it now because it's currently not working...) 

In terms of keyboard layouts, I was using Generic > Winbook Model XP5, which seemed to be correctly mapped. I couldn't find anything else that had 78 keys. (The keyboard has 78 + 10 "multimedia keys".)

---

### Post by sydbat on 2010-07-30
> **poubelle said:**
> Thanks for replying. The keyboard is a no-name made-in-China-type thing, so this might not mean much, but IIRC it's reported as "Sigma" brand when I ran lsusb. (I can't run it now because it's currently not working...) 

In terms of keyboard layouts, I was using Generic > Winbook Model XP5, which seemed to be correctly mapped. I couldn't find anything else that had 78 keys. (The keyboard has 78 + 10 "multimedia keys".)I'd bring it back to the store and get a new one. 

Or, try other keyboard configs (when it is recognized/working again) and see if that stabilizes it.

But I think it really is something faulty with the keyboard.

---

