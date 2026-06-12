---
title: "How can I get my external monitor fn keys to produce hotkey events?"
date: 2009-03-21
forum: Hardware
---

### Post by Mr. Picklesworth on 2009-03-21
The Nvidia driver can change display modes on the fly, but we so far do not have the ability for monitor hotplugging, which means if my big monitor gets unplugged from my laptop, it continues to blindly output to that thing.

A workaround to this is hitting the keys on my laptop to change between external / built in monitors. (Fn + F8, for example). The driver does support this with Twinview enabled (it is), if its very extensive documentation is to be trusted... which I think it is.

Turns out those keys do nothing for me :(
My laptop is an Asus F8Sv. Most other hotkeys work for what they claim, but in this case it does absolutely nothing.
Is there a way to check whether these hotkeys are generating events? (Or if it's just the nvidia driver being funny). Further, can I somehow force this into being? For example, map something else to do the same thing?
(Heh, maybe if the problem is deeper I'll send a kernel person a free mouse if he / she fixes it :P)

---

### Post by Neilguy on 2009-03-26
Bump!!!

I too am having the same issue since I upgraded to Jaunty alpha from Intrepid on a HP Laptop. Somebody help please.

BTW: I'm running Kubuntu jaunty

---

### Post by Mr. Picklesworth on 2009-04-10
Not a fix, but here's what I found to file a detailed bug report:
[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

---

### Post by WakkiTabakki on 2009-05-11
Another bump...

I just discovered the disper utility ([http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)) for toggling an external monitor using nVidia-card. On my Thinkpad T61 it works like a charm!

When I press Fn-F7 (Thinkpad monitor-switch-button) the screen goes blank for a second but nothing happens. Clearly the button is bound to do something...
--->> How can I find out to what command the button is bound?

I added a file to /etc/acpi/events/ with this contents
```
event=ibm/hotkey HKEY 00000080 00001007
action=/etc/acpi/thinkpad-monitor-switch.sh

```
And ofcourse added the script /etc/acpi/thinkpad-monitor-switch.sh containing:
```

#!/bin/sh
disper -e

```

- I have restarted the acpid and also rebooted after the acpi fiddling....
- I've tried the script from command-line and it works.
- I've run acpi-listen to verify the "event-code" for Fn-F7 to be ibm/hotkey HKEY 00000080 00001007
- I've added a zentiy-dialog to the script and verified that the script does NOT get run when I press the Fn-F7 button

The question is, thus how do I:
1. Check to what action the hotkey is currently bound
2. Change the hotkey to what I want it to do (why does the acpi stuff above not work)


Cheers all
/N

---

### Post by dejayl on 2009-05-21
I have the exact same problem.  My laptop is an Asus F8SN, so I think it might have something to do with the Asus F8S laptops.  I ran xev and Fn + F8 (the monitor switching shortcut) doesn't do a thing.  I hope this helps.

---

### Post by Mr. Picklesworth on 2009-05-21
Oh, by the way I did eventually file that bug report:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349289](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/349289)

---

