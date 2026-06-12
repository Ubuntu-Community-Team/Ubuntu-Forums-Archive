---
title: "My Ubuntu doesn't recognise Bluetooth hardware"
date: 2008-11-05
forum: Hardware
---

### Post by rine238 on 2008-11-05
Hi!

I have laptop Acer Extensa 5210, and installed Ubuntu 8.10. Now everything works except Bluetooth. I tried to search and it solve by google, but no information to find. My Ubuntu doesn't see at all my Bluetooth hardware, so I can't enable it. Maybe somebody knows what to do?

Thanks for any help!
):P

Maybe this means something:
oliver@AcerUbuntu:~$ dmesg | grep "Bluetooth"
[   27.612223] Bluetooth: Core ver 2.13
[   27.614462] Bluetooth: HCI device and connection manager initialized
[   27.614465] Bluetooth: HCI socket layer initialized
[   27.629654] Bluetooth: L2CAP ver 2.11
[   27.629662] Bluetooth: L2CAP socket layer initialized
[   27.638776] Bluetooth: SCO (Voice Link) ver 0.6
[   27.638784] Bluetooth: SCO socket layer initialized
[   27.658922] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.658930] Bluetooth: BNEP filters: protocol multicast
[   27.759742] Bluetooth: RFCOMM socket layer initialized
[   27.761130] Bluetooth: RFCOMM TTY layer initialized
[   27.761138] Bluetooth: RFCOMM ver 1.10
oliver@AcerUbuntu:~$ sudo modprobe acerhk
[sudo] password for oliver: 
oliver@AcerUbuntu:~$ lsmod | grep "acerhk"
acerhk                 33588  0

---

### Post by Handssolow on 2008-11-05
Does it help removing avahi-daemon and avahi-autoipd and see after a cold reboot if your blutooth works. If it makes no difference you can put them back. My Acer Aspire One finds my bluetooth mouse after a cold reboot less so after a warm reboot without these two avahi packages.

---

### Post by Ghilteras on 2008-11-08
i have exaclty the same problem

there are no modules of omnibook to use on my 2.6.27-7 intrepid kernel, same thing for toshset cause "required kernel toshiba support not enabled."

so my bluetooth adapter cannot be switched on in ubuntu, the only way to make it visible is to boot into vista (where i can easily switch it on) and then reboot in ubuntu

this workaround works as long as i dont shutdown, after that i have to repeat the workaround (boot vista, reboot ubuntu)

anyone managed to solve this?

---

### Post by rine238 on 2008-11-09
> **Handssolow said:**
> Does it help removing avahi-daemon and avahi-autoipd and see after a cold reboot if your blutooth works. If it makes no difference you can put them back. My Acer Aspire One finds my bluetooth mouse after a cold reboot less so after a warm reboot without these two avahi packages.

Don't know...I've tried almost everything I've found on internet, removing and installing a lot of programs and packages...and nothing.

---

### Post by rine238 on 2008-11-09
I've tried to make working my USB camera too. I have found an possible solution, but I need a help. I've found this:

[I][SIZE="1"]To solve this:

Open pac207.h (gspcav1-20070508/pixart)
Goto line 137
change:

if (id[0] != 0x27 || id[1] != 0x00)
return -ENODEV;

to:

if (id[0] != 0x27 || id[1] != 0x08)
return -ENODEV;

and rerun "sudo ./gspca_build" to rebuild the driver.

Your camera should now work when plugged in.

This solution was found at: [http://lists.zerezo.com/spca50x-devs/msg01290.html](http://lists.zerezo.com/spca50x-devs/msg01290.html)[/SIZE][/I]


How can I open that pac207.h (gspcav1-20070508/pixart) file???


It is in this threat: [http://ubuntuforums.org/archive/index.php/t-595924.html](http://ubuntuforums.org/archive/index.php/t-595924.html)

---

### Post by arm-c on 2009-02-02
Try my program that will make use of the acerhk program, which it depends on.  It basically enables you to activate and deactivate the bluetooth radio using a gui.

[http://acerhkgui.sourceforge.net](http://acerhkgui.sourceforge.net)

Acerhk is included in ubuntu 8.10 and 8.04 (possibly earlier).

---

### Post by arm-c on 2009-06-21
Re: AcerHK GUI -- GUI for users of the 'acerhk' driver to control wireless/bluetooth
Version 0.5 of the AcerHK GUI is now released and available for download on SourceForge!

My main thread here that I post updates is located at the following URL:
[http://ubuntuforums.org/showthread.php?t=1059704](http://ubuntuforums.org/showthread.php?t=1059704)

I am open to suggestions on what additional functionality I should work into my development plan. I'm not a programmer by trade and this is my first real program... which I happen to be writing as I am learning!

---

### Post by arm-c on 2009-06-23
Version 0.6 was just released.  Big enhancement for "new" users.  See post in message 7 (above)

---

