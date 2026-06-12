---
title: "i can only enable bluetooth from windows"
date: 2008-10-27
forum: Hardware
---

### Post by nabilgh on 2008-10-27
hi. i have a toshiba satellite laptop and i'm not being able to enable the bluetooth radio form ubuntu. everytime i try i want to enable it i should restart to windows than enable bluetooth from it and then get back to ubuntu. This is the onlay i know to enable bluetooth. I've tried several codes from the command line such as:
gksudo /etc/init.d/bluetooth start
sudo modprobe hci_usb reset=1
but it didn't work. anybody knows how to solve this problem? thanks

---

### Post by porthoslohnes on 2008-10-31
[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/261318](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/261318)

Know this probably isn't helpful.  Went though this headache last night when I loaded Intrepid for the first time to try Ubuntu.  Love it except for this.  Hopefully it will be sorted out sooner rather than later.  :-\

---

