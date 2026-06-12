---
title: "Bluetooth adapter not working on ubuntu 9.10"
date: 2009-12-23
forum: Hardware
---

### Post by bst_28 on 2009-12-23
Hi,
    My USB bluetooth dongle(BCM92035DGROM) works on ubuntu 9.04,but it is not working in 9.10.
The syslog says this :- 

Dec 24 10:06:43 bst-desktop kernel: [ 1642.620021] usb 4-1: new full speed USB device using uhci_hcd and address 3
Dec 24 10:06:53 bst-desktop kernel: [ 1652.841796] usb 4-1: configuration #1 chosen from 1 choice
Dec 24 10:06:53 bst-desktop bluetoothd[2108]: HCI dev 0 registered
Dec 24 10:06:53 bst-desktop bluetoothd[2108]: HCI dev 0 up
Dec 24 10:06:53 bst-desktop bluetoothd[2108]: Starting security manager 0
Dec 24 10:06:53 bst-desktop bluetoothd[2108]: Parsing /etc/bluetooth/serial.conf failed: No such file or directory
Dec 24 10:06:53 bst-desktop bluetoothd[2108]: Adapter /org/bluez/2107/hci0 has been enabled
Dec 24 10:07:11 bst-desktop kernel: [ 1670.781625] hci_cmd_task: hci0 command tx timeout

and running hcitool scan on terminal outputs this:-

bst@bst-desktop:~$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out

My phone(nokia 6300) detects computer but it doesn't show it as PC(It hints that bluetooth stack is not working properly) and if I try to pair computer from phone, ubuntu doesn't detect any coming request.Is there any workaround for this problem or I should stick with ubuntu 9.04.For internet connectivity I need bluetooth connection.

---

### Post by drpjkurian on 2009-12-23
Hi
I also have this problem. Well this issue has been notified as a bug in launchpad.

Dr Kurian

---

### Post by bst_28 on 2009-12-23
Can you please give me launchpad link.

---

### Post by drpjkurian on 2009-12-23
Hi
Please checkout these URL [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/436694](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/436694)
[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/441800](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/441800)

Hope this might help you. Let me know if it works

Dr Kurian

---

### Post by Lowspirit on 2009-12-23
I have the same issue, dongle is found and all but it can't detect any of my bluetooth devices, everytime it does a search that timeout line is added to my dmesg.

Sadly neither of those bugs seem applicable for my problem, there are other huuuge bugs about the timeout tx problem but none that have any answers.

---

### Post by bst_28 on 2009-12-27
> **Lowspirit said:**
> I have the same issue, dongle is found and all but it can't detect any of my bluetooth devices, everytime it does a search that timeout line is added to my dmesg.

Sadly neither of those bugs seem applicable for my problem, there are other huuuge bugs about the timeout tx problem but none that have any answers.
I have filed bug on launchpad, but nobody is not responded till now.You can also share technical details about your problem there.Link is mentioned below.
[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/499716](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/499716)
I switched back to ubuntu 9.04,thanks to this because internet is must if you are using ubuntu.

---

### Post by muckblit on 2010-01-03
I went through that this week when dist-upgrading in lucid. I had blueman working and then something broke. I was already in lucid though, when blueman was working the first time.

Just now I got blueman to recognize the adapter which /var/log/daemon.log
had said that bluetoothd had set up an HID for but blueman did not have permission or session id.

I found this fix via google, in the arch forum:
________________________________________________________________________

First, add yourself(or some user) to groups uucp and messagebus. Then,

ck-launch-session blueman-manager &
________________________________________________________________________

blueman then recognizes the adapter because it has a session or blueman's own daemonic seat/session id for hal, and user belongs to groups that have permissions on the HID. Before that you could see that blueman was not being recognized if you ran blueman in a term and looked at error codes.

Obviously blueman could add the groups in the package install, but as far as calling blueman from ck-launch-session, I wonder if blueman script would be polite if it ran ck-launch session within its script or had a
recursion of itself to do that? Or what? Why did it stop working?

---

