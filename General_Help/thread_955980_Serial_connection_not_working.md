---
title: "Serial connection not working?"
date: 2008-10-22
forum: General Help
---

### Post by airandfingers on 2008-10-22
Hi, I've been trying to get my serial connection to work. I have a box here that can be accessed via serial port, and I have connected a USB-to-Serial converter to my laptop, which is running Ubuntu 8.04. This box sends information over the serial connection when it is rebooted, and I should be able to see it with minicom. However, despite using minicom correctly (according to a colleague of mine), I see no information when I reboot the box. It appears to be working properly, so I believe that the problem is with the serial converter, or the serial connection itself.

Running dmesg gives:

user@computer:~/ch341_drv$ dmesg | grep tty
[    8.211431] console [tty0] enabled
[   23.574369] usb 3-1: pl2303 converter now attached to ttyUSB0
[   28.758687] audit(1224620533.981:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5175 profile="/usr/sbin/cupsd" namespace="default"
[96474.834163] tty_ioctl: exports duplicate symbol tty_termios_copy_hw (owned by kernel)

Any help is greatly appreciated.

Cheers,
Aaron

---

### Post by Mister.Vash on 2008-10-22
Are you a member of the group dialout?  Check and make sure you are, also just double check the permissions on /dev/ttyUSB0   This is what mine looks like
crw-rw---- 1 root dialout 188, 0 2008-10-20 09:51 /dev/ttyUSB0


Also, have you followed the steps in the client setup here?
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

---

### Post by airandfingers on 2008-10-23
Vash: Thanks a lot for the quick response. To check if I was in the dialout group, I did:
groups [user name]
[user name] adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin

Also, to check permissions:
ls -l /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 0 2008-10-23 16:47 ttyUSB0

If I'm not mistaken, these are the correct settings.. I also followed that link you gave, and followed the steps. The only change I had to make in minicom was to clear the "Init string" in "modem and dialing". I also tried "sudo minicom," making the recommended changes and trying to run it, but still no luck.

As a random side note, should the password for su and sudo be the same? When I try "su" and put in my password, I get an Authentication failure. However, when I try "sudo [command]", using the same password, it works fine. I was under the impression that sudo is the same as su, but for one command.. Thanks in advance for clearing this issue up for me.

Thanks again, hope to hear back from you soon!

-Aaron

---

### Post by airandfingers on 2008-10-23
Also, Just wanted to add that I already went into the Synaptic Package Manager and "completely removed" the brltty packages: brltty, brltty-flite, brltty-x11, libbrl-api0.5, and libbrlapi-dev.. One or two of those wasn't installed, but I removed the others. This was per other forum suggestions, but it made no difference I could see.

Thanks,
Aaron

---

### Post by airandfingers on 2008-10-31
Meh, turns out I don't really need to use my serial port for this project, but thanks for your help.
I'll be back if I need to use serial connections on Ubuntu at a later date.

---

