---
title: "Bluetooth broke down after recent upgrades"
date: 2021-07-19
forum: Hardware
---

### Post by fondfire on 2021-07-19
After recent package upgrades on Friday, July 16th, the Bluetooth device on my motherboard quit working. (Apt's history log here: [http://paste.ubuntu.com/p/zKFyYkNBXn/plain/]("http://paste.ubuntu.com/p/zKFyYkNBXn/plain/")) I've attempted to downgrade and adjust the packages since the install, but none of those attempts have restored the device to functioning (though I did not exactly exactly reverse Friday's upgrade either).

The bluetooth device is an Intel Wireless-AC 3168NGW device that handles both WiFi and Bluetooth with a shared antenna installed on a Gigabyte X570 AORUS ELITE WIFI motherboard. Here's the output of [FONT=Courier New]lspci[/FONT], [FONT=Courier New]lsusb[/FONT], and [FONT=Courier New]dmesg[/FONT] commands: [http://paste.ubuntu.com/p/2Sy9FnvkGk/plain/]("http://paste.ubuntu.com/p/2Sy9FnvkGk/plain/"). Also, some [FONT=Courier New]dmesg[/FONT] output captured more recently after bootup (before most of the relevant data is consumed by the ever-cycling Bluetooth crashout): [http://paste.ubuntu.com/p/pC3ttfsRfJ/plain/]("http://paste.ubuntu.com/p/pC3ttfsRfJ/plain/").

I'm pretty stumped about how to actually fix this and being unable to use the Bluetooth keyboard and mouse are major pains right now. Can anybody help?

Thanks!

--fondfire

---

### Post by fondfire on 2021-07-19
Posted to AskUbuntu: [https://askubuntu.com/questions/1352936/how-do-i-fix-my-bluetooth-device-in-xubuntu-20-04]("https://askubuntu.com/questions/1352936/how-do-i-fix-my-bluetooth-device-in-xubuntu-20-04")

Things seem more lively over there... I guess this was kinda where we asked the questions decade before last... But I've been running Ubuntu so steady for so long, I just didn't feel the need! :)

---

### Post by fondfire on 2021-07-20
Wow, I have forgotten some basic troubleshooting, obviously!

So, the fix turned out to be really easy. After shutting down the computer, I actually unplugged it from the wall for a while... and 60 seconds later, I plugged it back in. Apparently, the motherboard just wasn't really powering down with the computer plugged in, so the Intel Wireless-AC 3168NGW wasn't really powering off and resetting itself.

At least it's a super-easy fix! Hope it helps one of you... though I'll feel kinda stupid for a while...

---

### Post by clauder2 on 2021-09-12
Same thing happened to me with a AC8265. Normal power down did not worked until I followed the instruction above and removed the power cable.

Arguably, there is a bug in the driver since at boot time, it should not depend on the state of the HW to initialize properly. That is device driver developer 101.

---

### Post by tahitiwibble on 2021-09-14
> **fondfire said:**
> Wow, I have forgotten some basic troubleshooting, obviously!

So, the fix turned out to be really easy. After shutting down the computer, I actually unplugged it from the wall for a while... and 60 seconds later, I plugged it back in. Apparently, the motherboard just wasn't really powering down with the computer plugged in, so the Intel Wireless-AC 3168NGW wasn't really powering off and resetting itself.

At least it's a super-easy fix! Hope it helps one of you... though I'll feel kinda stupid for a while...

Oh my friend it sure as heck got my problem solved. Can't believe that I spent hours going through articles about broken Bluetooth and trying to correct the issue and then ........ unplugged the friggin PC and got rid of any residual power in the power brick and BINGO. Thanks for that, cheers.

---

