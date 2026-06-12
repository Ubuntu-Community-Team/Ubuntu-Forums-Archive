---
title: "bluetooth help"
date: 2008-11-17
forum: Hardware
---

### Post by Lee_Machine on 2008-11-17
I posted this in the System76 section but I'd thought id see if anyone in this section might have an answer.





So I started a thread about this issue and I had thought that I had fixed it but I guess not.

[http://ubuntuforums.org/showthread.php?t=982688](http://ubuntuforums.org/showthread.php?t=982688)

The symptoms are this:

I cannot connect or see any bluetooth devices. When I go to the bluetooth menu in Preferences all I can see is the General Information, not the hardware information, or where it would be called by my computer name1 by default and you can set options like what devices to trust and if to always connect.

I am thinking that this is an issue where it is not talking to the hardare correctly, as it has worked before at random times.

It still says in the Device Manager under USB bluetooth "Inusfficiant power to operate USB device"

Not sure what this is about.

In the daemon.log for bluetoothd it says "unable to get on D-Bus"
along with "Failed to find Bluetooth netlink family"

The system is panp4n Ubuntu 8.10 64bit

Thanks in Advance,

Update:

I found this with my exact hardware information per Device Manager:

[https://bugs.launchpad.net/ubuntu/+bug/289836](https://bugs.launchpad.net/ubuntu/+bug/289836)

No known workarounds.
Last edited by Lee_Machine; 51 Minutes Ago at 09:35 PM..

---

