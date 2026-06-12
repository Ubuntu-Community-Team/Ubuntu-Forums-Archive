---
title: "Programs stop working after USB pen drive connected"
date: 2008-11-01
forum: General Help
---

### Post by Mark224 on 2008-11-01
Hi,

I have a really bizarre problem with Hardy.  Every time I connect a pen drive to the computer this seems to stop most new programs working.  I can access the pen drive fine but things like networking stops and gnome-terminal, and most other programs from the menus no longer launch.

If I disconnect the pen drive then the system does not recover.

When I try to start a new program I get a message at the bottom saying "<application> starting" and the rotating cursor, but no new window appears.

If I try commands like ifconfig, iwconfig in a terminal then they hang and I can't break out of them with Ctrl+C.

I've tried lsusb, /var/log/messages and dmesg and I can't see any errors reported.

I also cannot shut down cleanly since the GUI does not appear and typing "sudo shutdown ..." or "sudo reboot" does not do anything.  Again these hang forever.

The only way I can recover from this is to Do "Ctrl+Alt+Del" which seems to reboot immediately.

---

### Post by OldDirtyTurtle on 2008-11-01
Interesting.  My wife has recently confessed that she "can't get anything to work on Ubuntu".  I've had nothing but success jumping from my piece-of-crap work computer with XP, another work computer with Vista, and our home computer.

I did some observation and noticed that it had to do with her using a USB drive between her work laptop and our home computer with Hardy.  It locks Hardy up, just as you describe.  After a rebooting with Ctrl-Alt-Del or a forced shut down, I can open her files from the drive.

FWIW...  I have no issues with either of my SanDisk 4gig USB drives.  One is old, one is brand new.

It turns out that her SanDisk 1gig does OK.  Her trouble drive is a generic freebie.

---

### Post by Mark224 on 2008-11-02
This is a more subtle problem that I first thought.  I believe it to be an interaction between USB devices.

I have a USB wireless network adaptor which works fine on its own.  However if I plug in another USB device then it stops working and programs hang.

Unplugging an USB device does not help.

If I start up the computer with more than one USB device connected then the computer does not recognize the network adaptor but I can plug and unplug other USB devices with no problems.

It works fine under Windows.  I defintely think this is a bug.

---

### Post by Mark224 on 2008-11-03
BTW: The network adaptor is a Linksys WUSB54G v2.1

---

### Post by Mark224 on 2008-11-05
I have installed all the recommended updates to Hardy which includes a new version of the kernel (-21) but the USB problem is still there.

Can anyone tell me what information would be useful to help diagnoze this problem?

---

### Post by Mark224 on 2008-11-08
Bump

---

### Post by Mark224 on 2008-11-13
Bump

---

### Post by Mark224 on 2008-11-16
I have just encountered the same problem without plugging or unplugging USB devices so maybe this is a red herring.  I booted the computer before I had switched on the wirless access point.  After powering up the computer could not access the network.  I tried to stop the network by unloading the ndiswrapper module:
```

sudo modprobe -r ndiswrapper

```
This command hung forever and I could not Ctrl+C out of it.  The GUI had partially hung in exactly the same way a before.  This time I got error messages on the console:
```

unregister_netdevice: waiting for wlan0 to become free: Usage count = 7

```
This message comes up every few seconds for ever.  I had to use the "Raising Elephants" trick to get out.  After reboot all is working ok again.

---

### Post by Mark224 on 2008-12-02
Bump

---

### Post by Mark224 on 2009-01-16
Bump

---

### Post by Mark224 on 2009-08-13
Bump

---

