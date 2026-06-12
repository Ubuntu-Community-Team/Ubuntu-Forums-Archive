---
title: "USB Mouse no longer functions if removed and then re-inserted"
date: 2019-02-03
forum: Hardware
---

### Post by n2te on 2019-02-03
I'm running Ubuntu 18.04 on my Latitude E6400 notebook where Linux has served me very well. However if I happen to unplug my USB mouse in the middle of an already up and running session, let's say to move the computer to another desk or area, and then I _RE-INSERT_ the USB mouse back into the USB port, the OS no longer re-activates functionality of the mouse.  Subsequently, I must use the notebook's mouse pad to reboot in order to get back usage of the mouse.  Invoking the lsusb command the system immediately sees the mouse again once it's re-inserted.

[COLOR=#0000ff]~$ lsusb
Bus 006 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0[/COLOR]

Is there a system setting of some sort to re-activate functionality of the mouse again once it is re-inserted? Even though the lsusb cmd sees the device, a system reboot is the only thing that will get it to function again. 

On my other two machines that run OSX and Win7 I can remove and re-insert USB devices without any issue. Why does this happen on my Linux notebook? Is this standard behaviour for Linux? Any way around it? (FYI, I did do a Google search for answers but found nothing.) Suggestions? Thanks. Eddie (my apologies if I don't use the correct terminology here to describe my issue as I'm not a veteran Linux user.)

---

### Post by Autodave on 2019-02-04
Since no one has jumped in yet, let me give you something to try.  Power up the machine *without* having the mouse plugged in.  See what happens then when you connect and disconnect it several times.

---

### Post by #&amp;thj^% on 2019-02-04
Try reloading the mouse driver with:
```

sudo rmmod usbhid
sudo modprobe usbhid
```

when the mouse is plugged in and not working.

---

### Post by n2te on 2019-02-05
Engaging the usb connector in and out as you suggested does make it work. I booted with no mouse connected then inserted the mouse and it immediately functioned. However when I reinserted it to try this suggestion it seemed like it took a while (30 secs) to respond and re-activate. Then after re-inserting numerous times the re-engagement delay became shorter. Not sure what that means. I guess it takes the system some time to cycle thru it's re-connect sequence to check the usb mouse connection. I will try some other sequences of re-insertion to see what happens. Thanks.

---

