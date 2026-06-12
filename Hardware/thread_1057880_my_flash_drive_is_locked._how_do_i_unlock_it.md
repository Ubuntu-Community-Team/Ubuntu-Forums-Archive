---
title: "my flash drive is locked. how do i unlock it?"
date: 2009-02-02
forum: Hardware
---

### Post by Meow27 on 2009-02-02
ok ive been playing around with my Kingston DT mini slim 4gb flash drive until it became protect by something. the drive is locked to writes and deletions (in some cases i cant copy certain files out of it.) i cant delete/format the card either in gparted (within gnome)


anyone know any good solution to this kind of problems? i dont see any manual locking switch :/

---

### Post by ajmctaggart on 2009-02-02
Can you unmount the drive with a right click?
Then reinsert into usb...

run the command "mount" from terminal, should tell you what the usb drive is called, say /dev/sdx or something like that...

Then mount it with

again right click to unmount and this time mount it from the terminal with 

sudo mount /dev/sdx

see if that gives you access to reformat in gParted now...

more info on usb drive commands and reformatting,etc...
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

This thread is about pen drive linux, but the mount, unmount, and reformatting from the terminal still apply...

Good Luck!

---

### Post by Meow27 on 2009-02-02
thanks! i think it worked :3

---

