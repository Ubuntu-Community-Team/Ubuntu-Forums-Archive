---
title: "suspend occasionally fails, Dapper"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by arthur_kalm on 2007-01-31
Hi everyone,

I've been using Dapper for a while now and this has been bothering me for a long time. Suspend works on Dapper, but occasionally it fails. When suspend works, the power light slowly blinks. However, when suspend fails, the screen goes black (as it should), but the power button stays lit. The keyboard and mouse don't work and I never come back to my desktop. I have to turn off the laptop using the power button.

Frustrated, I tried to look for the culprit. I looked at /var/log/messages /var/log/acpid and dmesg. However, I can't see anything strange between the interval right before I turn the computer off (when suspend fails) and when I turn it back on. I thought that this might happen only when I'm connected to a wireless network, but it doesn't seem to be the case because it failed while I was connected via Ethernet (and anyways, the acpi scripts bring down all network interfaces before suspending).

If anyone has any ideas of where I can look to find the problem or have any solutions I would really appreciate it! Thank you!

Note: by suspend I mean suspend-to-RAM not hibernate (suspend-to-disk).

Also, I'm using a Dell Inspiron 6400 which has the an X1400 (proprietary drivers) and uses the Dell 1390 Wireless (ndiswrapper). I'm also running XGL with Beryl.

P.S. I haven't switched to Edgy because the last time I tried to install it, suspend and hibernate did not work. If anyone has suspend and hibernate working on Edgy with a similar hardware configuration, please tell me how you did it. Thanks!

---

### Post by arthur_kalm on 2007-02-06
Well, on one of the suspends that failed I catch a certain message "resume error -113". I greped for this in /var/log and sure enough I found a few of these message, no doubt coinciding with the different times that resume failed. Does anyone know what 
syslog:Feb  2 00:00:43 localhost kernel: [17214434.048000] usbhid 4-1:1.1: resume error -113 means?

Thank you for your help.

P.S. I added ndiswrapper to the module section of /etc/default/acpi_support, and it *seemed* to work, however, I did have it fail a couple of times.

P.S.S. I'm getting the hunch that the suspend fails when I have a lot of applications open. So several instances of OO.o, Firefox, Kile, Kopete, etc all open before I suspend. Is it possible that suspend fails then? I doubt I'm swapping though, since I have 1 GB of RAM (I'll check next time).

---

### Post by ltmon on 2007-02-06
usbhid is "USB human interface device", or in simpler terms usually a usb keyboard or mouse.

Does the failure occur at a time that you have a mouse plugged in? Maybe try adding "usbhid" to the modules section alongside ndiswrapper and see if that fixes it up?

---

### Post by arthur_kalm on 2007-02-20
I tried this, but it still fails on occasion :(

---

### Post by notanatheist on 2008-02-07
I know this is a year later but why post dupes?

I'm investigating this myself with 7.10. I'm wondering if Firefox might be causing the suspend issue. My Dell pretty much crapped out and I got a new Acer 6292. Power management was working out of the box with a clean install. Resume time seems reasonable but after leaving FF on then putting it to sleep it went through all the motions and this morning when I popped the lid and tapped the keyboard it took a few whole minutes to actually resume and I got the "suspend failed" message. I followed that by closing FF, closing the lid and allowing the machine to suspend. After a few minutes I woke it up and it was back in less than 30 seconds as expected. I'll repeat these tests in the next few days with a combo of FF2, FF3, and no FF to see if there is any consistency.

---

