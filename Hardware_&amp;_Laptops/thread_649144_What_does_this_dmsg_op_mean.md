---
title: "What does this dmsg o/p mean?"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by Scott S. on 2007-12-24
I'm a hardware guy who can usually work around almost anything but I've never dealt with linux devices before. Could someone please explain what this dmsg output means? Where is "descriptor/start" located? In the device or somewhere in the OS?

The device in question is an MP3 player that connected fine to a Suse box and a Windoze box... but refuses to even show up on Ubuntu. Since it doesn't show, I can't mount it or use it.

Thanks,

Scott

[27839.890572] usb 4-1: new high speed USB device using ehci_hcd and address 10
[27845.021787] usb 4-1: unable to read config index 0 descriptor/start
[27845.021800] usb 4-1: chopping to 0 config(s)
[29347.671632] usb 4-1: no configuration chosen from 0 choices
[29347.671717] usb 4-1: USB disconnect, address 10

---

### Post by nick_h on 2007-12-24
There is a thread, [here](http://ubuntuforums.org/showthread.php?t=524935), that suggests removing the ehci_hcd module.

Type:
```
sudo rmmod ehci_hcd
```
and then plugging in your device again.

---

### Post by Scott S. on 2007-12-24
BINGO.

I checked Konqueror under removable devices without success. Checking fdisk -l, the device was not listed. Then I removed the module and tried Konqueror again, still nothing. Closed Konqueror and I tried a dmsg, and got command not found. I meant to do sudo Konqueror again but accidentally hit enter at the wrong time and re-removed the module, which said it didn't exist. I then checked fdisk -l again and the device showed up as /dev/sda

Re-tried sudo Konqueror and it was right there waiting for me, under removable devices.

Thanks Nick, this has been three days of frustration and was solved with one line:

sudo rmmod ehci_hcd

If you need to do this, check for the device MORE THAN ONCE with:

sudo fdisk -l     (that's an L as in List)

Scott

---

