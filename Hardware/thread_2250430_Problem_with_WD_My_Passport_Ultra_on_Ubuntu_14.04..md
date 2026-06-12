---
title: "Problem with WD My Passport Ultra on Ubuntu 14.04..."
date: 2014-10-28
forum: Hardware
---

### Post by andrew.t.sullivan on 2014-10-28
Hello

I have a rather strange problem with a 1TB WD My Passport Ultra on Ubuntu 14.04.

[INDENT]If I boot my laptop into Ubuntu then plug in the drive to the USB3 port, the drive is not recognised.

If I disconnect the drive, reboot into W 8.1 then plug in the drive, all is fine.

If I leave the drive connected then reboot into Ubuntu, the drive shows up in Dolphin.  I can "Safely remove" the drive, unplug it then plug it in again, I can still see the drive.

If I switch off the laptop I have to go through the whole process again...
[/INDENT]

Anyone got any idea what's going on?

TIA

Andrew

---

### Post by vanadium on 2014-10-29
What do you mean with the last point: switch off while in Windows or switch of while in Ubuntu. If the former, then it could be that the drive is be properly closed, such that it is not anymore automounted by Ubuntu. That is because Windows does not completely shutdown in order to be able to boot faster ("hybrid shutdown").

---

### Post by andrew.t.sullivan on 2014-10-29
Thanks for your reply.  I tried a few more things, as follows:

[INDENT]Connected WD drive in W8.1 - no problems.

Shut down laptop (not Restart) leaving drive connected.

Restart laptop, Ubuntu won't boot, drive just beeps.

Disconnect drive, restart computer (needs a long power-buttonpress); Ubuntu starts OK.  Connect drive, doesn't appear in Dolphin.

Disconnect drive, restart laptop in W8.1, connect drive, all OK.

Restart laptop (as opposed to Shutdown/Start), leaving drive connected; Ubuntu loads, drive appears in Dolphin.  Can Safely remove/reconnect drive at will.
[/INDENT]
 
I really don't know what is going on here - it seems that powering down the laotop causes the drive not to be recognised by Ubuntu?  Would zapping the WD drive and reformatting to clean NTFS just give me a usable drive?  I'm not particularly bothered about the WD software/security etc.  I guess I could do this GParted?

Thanks again

Andrew

---

### Post by steeldriver on 2014-10-29
Don't the Passport drives use hardware-based encryption? perhaps the drive is getting unlocked when you boot into Windows and is then staying unlocked for as long as the device remains powered up?

---

### Post by andrew.t.sullivan on 2014-10-29
Except that when I've pursuaded Ubuntu to recognise it, I can "Safely remove" then reconnect it as often as I like, which involves powering down the drive...

---

### Post by andrew.t.sullivan on 2014-11-03
This is getting ever more bizarre...

I just tried to connect the WD Passport drive to my desktop machine, which is running Linux Mint 17 (32bit) - works fine!

If it helps, the laptop on which the Passport drive won't work is a Lenovo G505s.

Thanks again.

---

### Post by andrew.t.sullivan on 2014-11-03
Further bit of information...

When the WD drive is plugged in to the laptop, it doesn't appear in Dolphin, but if I run lsusb one of the replies is[INDENT]
Bus 001 Device 005: ID 1058:0820 Western Digital Technologies, Inc.
[/INDENT]
 
Which seems to indicate that the laptop is seeing the drive, just not allowing the contents to be seen.

---

### Post by andrew.t.sullivan on 2014-11-04
Might have sorted this...

My desktop PC only has usb2 ports while the laptop has both usb2 and usb3.  I had been using a usb3 port on the laptop, so I plugged the WD drive into a usb2 port - works fine.  No idea why, but I&#8217;ll be posting the question here!

---

