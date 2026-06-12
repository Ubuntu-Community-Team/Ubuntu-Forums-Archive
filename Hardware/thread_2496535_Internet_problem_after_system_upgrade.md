---
title: "Internet problem after system upgrade"
date: 2024-04-02
forum: Hardware
---

### Post by fidgety on 2024-04-02
Hello, hoping for a little help.

I had ubuntu running with no issues for around 4 years at a guess.
A few weeks ago I upgraded my motherboard CPU and ram.
Since the upgrade, I had a few issues getting ubuntu to boot from the motherboard boot manager but resolved this on first day.
The problem I'm having is randomly throughout the day, the internet connection symbol in the top left goes dark with a ? printed on top. I'm connected to the router using an ethernet cable. Usually websites stop responding first for a minute or so then this happens.
It's completely random how this happens. Sometimes I can be online for 10 hours with no issue before it occurs and other times like today, it has happened 2 times in 5 hours. When this happens I am forced to restart the system to get the connection back. Only thing I have attempted this far is disabling the wired connection by right clicking the symbol and choosing this option then starting it again. This doesn't work.

After I did the system upgrade I checked on websites how to upgrade system drivers but saw on a few sites it would happen on its own. I'm not sure if something is wrong with driver or not. Ubuntu has installed updates maybe 3 or 4 times in the last few weeks im not sure if any of these are related to drivers.

I have been spending most my time these few weeks on windows which is on a separate ssd and haven't had any issues with connectivity on that OS so I dont believe it to be a hardware fault.

Any advice pointing me in the direction to diagnose this issue would be much appreciated.

Regards

---

### Post by TheFu on 2024-04-03
If Windows was last booted, it could leave the NIC with Windows-specific settings. This can be bad or great, depending on the result.

You didn't provide any details, so nobody can help.
Which release of ubuntu, exactly?
Which DE?
Which NIC?
Have you swapped the cable already?  Have you tried a different switch port?
Does everything work perfectly on the same hardware, when booted into MS-Windows?

Answer all those questions to get the best help.  There are lots of possible ways to provide the data spelled out in these forums. Search for the commands. **system-info** is probably the easiest way. It needs to be installed.  **inxi** is another, but multiple commands with options will be needed.

---

