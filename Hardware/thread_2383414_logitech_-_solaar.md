---
title: "logitech - solaar"
date: 2018-01-24
forum: Hardware
---

### Post by jgw on 2018-01-24
I have a logitech mouse that I am trying to get going.  My dongle is a unifying logitech dongle.  when I run solaar I get: Found a Logitech Receiver (/dev/hidraw1), but did not have permission to open it.  I then went to /dev/hidraw1 and changed the group to me and that went away.  All that being said it no longer even recognizes that unifying logiech receiver.  I checked if the system knew the receiver was plugged in and it is.  (Bus 003 Device 014: ID 046d:c534 Logitech, Inc. Unifying Receiver).  I then went back to the hidraw1 file and switched the group permission back to root and got the error again (Found a Logitech Receiver (/dev/hidraw1), but did not have permission to open it.  If you've just installed Solaar, try removing the receiver and plugging it back in.)

I have also swapped the connection from usb3 to usb2 (found that one someplace).

Undere normal circumstances all I have to do is to plugin the receiver, turn on the mouse, and sonarr tells me I am connected.  Now it only recognizes the receiver which I can't open it and, when I can, nothing at all happens.

when I run sudo solaar-cli show  I get: (without the sudo I don't have permission)

Exception AttributeError: "'Receiver' object has no attribute '_devices'" in <object repr() failed> ignored
Traceback (most recent call last):
  File "/usr/bin/solaar-cli", line 42, in <module>
    solaar.cli.main()
  File "/usr/share/solaar/lib/solaar/cli.py", line 431, in main
    args.cmd(receiver, args)
  File "/usr/share/solaar/lib/solaar/cli.py", line 203, in show_devices
    _print_receiver(receiver, args.verbose)
  File "/usr/share/solaar/lib/solaar/cli.py", line 98, in _print_receiver
    paired_count = receiver.count()
AttributeError: 'NoneType' object has no attribute 'coun

thank you................

---

