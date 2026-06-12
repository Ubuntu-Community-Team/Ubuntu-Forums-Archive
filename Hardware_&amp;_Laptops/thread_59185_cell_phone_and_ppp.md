---
title: "cell phone and ppp"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by zukakog on 2005-08-23
I'm trying to use my cell phone as a modem for my laptop.

[-X Don't yell at me yet!  I didn't put this in the laptop section because I'll be using it on my main box too.

I'm having a hard time figuring out what /dev/tty**** my phone is.  I'm connecting it via a usb cable.  Hotplug detects my USB flash drive just fine, but I can't tell if it's doing anything with my phone.  The phone says that it's entering data mode, but I don't get any kind of visual clues on my screen.

**Is there any way to figure out where my phone is being mounted?**

---

### Post by jasmuz on 2005-08-23
Open a terminal, type tail -f /var/log/messages

Plug the cellphone in....read what it loads and paste here

---

### Post by zukakog on 2005-08-23
[QUOTE=jasmuz]Open a terminal, type tail -f /var/log/messages

Plug the cellphone in....read what it loads and paste here[/QUOTE]

Thanks tons, jasmuz!

Here's what I got when I plugged in the phone
```
Aug 23 06:35:55 localhost kernel: usb 1-2: new full speed USB device using uhci_hcd and address 2
Aug 23 06:35:56 localhost kernel: uhci_hcd 0000:00:1d.0: Unlink after no-IRQ?  Different ACPI or APIC settings may help.
Aug 23 06:35:56 localhost kernel: usb 1-2: khubd timed out on ep0in
Aug 23 06:36:01 localhost kernel: usb 1-2: khubd timed out on ep0out
Aug 23 06:36:07 localhost kernel: usb 1-2: khubd timed out on ep0out
Aug 23 06:36:07 localhost kernel: usb 1-2: new full speed USB device using uhci_hcd and address 3
Aug 23 06:36:08 localhost kernel: usb 1-2: khubd timed out on ep0in
Aug 23 06:36:13 localhost kernel: usb 1-2: khubd timed out on ep0out
Aug 23 06:36:19 localhost kernel: usb 1-2: khubd timed out on ep0out
```

Any ideas?

---

### Post by jasmuz on 2005-08-23
None whatsoever...hope anyone can ditch in, because your cellphone isnt recognized.

---

### Post by zukakog on 2005-08-23
[QUOTE=jasmuz]None whatsoever...hope anyone can ditch in, because your cellphone isnt recognized.[/QUOTE]

Great.  ](*,)

I did get it to dial on my Fedora 4 box at work.  Didn't connect, just dialed.  Doesn't help me much with my laptop though . . .

Maybe with Breazy it'll work.

BTW, I have a Toshiba 4050 (same as the Audiovox 9950) and I'm using Sprint.  It's one of the only phones that can still dial #777 (#PPP).  Sprint has told most manufacturers that they won't continue to offer their phones if they don't disable it in the firmware.  They'd much rather sell you a US$300 connection card and then charge US$40/month for a 40MB plan!

I'm still open for ideas.  I've got the Window$ drivers if anyone can tell me how to port them.

Thanks for the help, jasmuz.

---

