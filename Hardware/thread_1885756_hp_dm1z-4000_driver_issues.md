---
title: "hp dm1z-4000 driver issues"
date: 2011-11-23
forum: Hardware
---

### Post by jerrycrabb on 2011-11-23
Havnt seen any driver related posts for the dmz1-4000 yet. Looking to see if anyone else has experienced or has resolution for the issues I'm running into.

After fresh 11.10 install, there are 3 drivers populated in the "additional drivers" dialog box. A broadcom sta driver (automatically activated), and two drivers for the on-board graphics. One of the drivers notes "post release updates" and fails to install. The other driver installs the latest catalyst version which seems to work but leaves an AMD unsupported watermark in the corner of the screen.

The wireless works at first but periodically fails (opprates as if wireless card were disabled). Also, if the wireless card is disabled by either keyboard shortkey (f12) or via menu, it cannot be re-enabled without system restart.

---

### Post by mrcoder0101 on 2012-03-16
I'm having the exact same issues as you. The updated AMD driver would never install. I searched this issue and someone on another forum suggested to install the packages directly using apt-get. It seemed to work but I wasn't very comfortable with it. Sorry I didn't record the package names or the forum post; otherwise I would have shared them.
The wireless is the biggest annoyance. It never works consistently. I tried downloading the drivers from broadcom directly and compiling them, and still not much improvements. I tried them on other distros besides Ubuntu and they weren't any better.
As for turning the wireless on/off; you can try installing a package called "rfkill", then with the command "rfkill unblock all" you can have everything turned on. This works best if you login to windows first, download the HP wireless manager and make sure everything is enabled in windows first. There seems to be a hardware switch on those cards and only the HP wireless manager is able to properly enable/disable it (the state persists even when you reboot into another OS).

I hope broadcom fixes the wireless drivers soon. Its the biggest annoyance for this laptop and linux.

---

