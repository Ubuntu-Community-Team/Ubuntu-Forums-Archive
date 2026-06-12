---
title: "bluetooth dongle usb wake capable"
date: 2011-04-04
forum: Hardware
---

### Post by gettons on 2011-04-04
All,

I have already posted this onto xbmc forum, but since this can be just an hardware advice request, I post this to the ubuntu forum as well.
Do you basically have any usb bluetooth dongle usb wake capable to suggest ?
I don't know if this is because of MY dongle or not though.


```


Hi all,

I have just installed maverick minimal ( i386 ) + XBMC 10.1 + PS3 BD REMOTE using an usb dongle DLINK DBT-120 rev B4

All is working fine, and I am so glad to have switched to xbmc from my ugly LG. :-)
I am using a ZOTAC HD-ND22 mini pc and I have already enabled S3 ACPI in the bios.

I can shutdown, reboot, hibernate and suspend the machine.
Suspend does work fine, and I can wake the machine up using the WIRED usb keyboard.
I have followed the wiki guide to enable it and it was really really easy to do so.

The problem is now with the usb dongle + remote which looks like not capable of waking the pc up.

Done this bit:

echo "USB0" > /proc/acpi/wakeup
against all the usb interfaces and no problem I could see them enabled catting the above file afterwards.

But strangely enough, when I run the command

echo enabled > /sys/bus/usb/devices/2-4/power/wakeup

agains my device ( the usb dongle ) I get

echo: write error: Invalid argument

while if I do that against my wired usb keyboard it does work nicely.


Does that mean that my usb dongle is not capable of waking up the pc?
Can you suggest me any bluetooth usb dongle working on linux and capable of waking up a pc via usb?
Do you have an idea how to fix this? I know IR remotes + receiver work nicely but I would really like to use this device since I have already got this one.



```



Thanks in advance.



Tommaso

---

