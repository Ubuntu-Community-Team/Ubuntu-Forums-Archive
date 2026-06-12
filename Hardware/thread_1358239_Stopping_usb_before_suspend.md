---
title: "Stopping usb before suspend"
date: 2009-12-18
forum: Hardware
---

### Post by Moshanator on 2009-12-18
Running Ubuntu 9.10 kernel 2.6.31-16 on an Asus P5GPL-X.
Suspend has never worked out of the box on this machine, the reason being USB drivers (ehci-hcd, ohci-hcd, uhci-hcd). When pressing the Sleep button, the machine suspends, but immediately resumes, waits a little and throws me to the unlock screen.
When booting with the "nousb" option, both Suspend and Hilbernate work gloriously.
Question: How to stop the USB drivers before suspending and resume them after waking up? I knew it was possible on 8.10 Intrepid, using```
modprobe -r uhci-hcd ehci-hcd ohci-hcd
```but now those modules don't exist anymore.

---

### Post by Moshanator on 2009-12-19
bump

---

### Post by Moshanator on 2009-12-20
Here's what more desperate googling revealed:
The USB drivers (uhci_hcd, ehci_hcd and ohci_hcd) can be found at /sys/bus/pci/drivers . They can be disabled by going to the according folder,```
$ cd /sys/bus/pci/drivers/uhci_hcd
```finding out all the long IDs/addresses/long number things,```
$ ls
0000:00:1d.0  0000:00:1d.1  0000:00:1d.2  0000:00:1d.3  bind  module  new_id  remove_id  uevent  unbind

```disabling (unbinding) them one by one,```
$ echo -n 0000:00:1d.0 > unbind
$ echo -n 0000:00:1d.1 > unbind
$ echo -n 0000:00:1d.2 > unbind
$ echo -n 0000:00:1d.3 > unbind
```and repeating the same for ehci_hcd and uhci_hcd. After doing that, suspend/resume/hibernate worked perfectly for me. After resuming, the USB drivers can be restarted using the same process, but using "bind" instead of "unbind". I'll do some research and see if the process could be automated. Feel free to leave suggestions.

---

### Post by Moshanator on 2009-12-21
This issue was also discussed [here]("http://ubuntuforums.org/showthread.php?t=1168204").
Here's a script that will automatically unbind USB on suspending/hibernating and bind USB on wakeup.
Remove the .txt extension, make it executable and place it into /etc/pm/sleep.d .

---

