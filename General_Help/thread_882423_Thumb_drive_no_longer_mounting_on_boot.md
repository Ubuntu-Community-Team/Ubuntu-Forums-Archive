---
title: "Thumb drive no longer mounting on boot"
date: 2008-08-06
forum: General Help
---

### Post by grindedrick on 2008-08-06
I have been loading a thumb drive into my usb and booting Ubuntu for sometime now without having to mount anything manually.

Just now, I'm getting these 2 windows popping up:

> 
mount: wrong fs type, bad option, bad superbolck on /dev/sdc1, missing codepage or helper program, or other error in some cases useful info is found in syslog -try dmesg|tail of so

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I've tried rebooting just to get the same errors.
I have mounted through the command line but I keep getting a file I/O error when I try to save anything to the drive. I have also tried the thumb drive on my Windows machine and it works fine? What on earth happened on my Linux machine.

The only thing I have done today is add a new default user for educational purposes so I could get the feel of the environment. I have deleted the user but I'm still getting the same errors. Does anybody have any ideas?

Thanks in advance.

---

### Post by grindedrick on 2008-08-07
I guess I could have specified the file I/O problems is from a simple 3rd party txt file writing application that was working. 

It looks like the reason is a security issue.

Also the tail on the dmesg was something along the lines of this:

FAT 'flush' not expected, missing value.
Something like that.

Thanks in advance????
:confused:

---

