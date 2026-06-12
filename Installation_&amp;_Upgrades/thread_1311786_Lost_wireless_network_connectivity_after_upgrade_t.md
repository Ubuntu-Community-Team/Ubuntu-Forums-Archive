---
title: "Lost wireless network connectivity after upgrade to 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by arilds on 2009-11-02
I upgraded fine to 9.10.  No error messages of any sort, but I lost connectivity to my wireless router.

The wireless adapter I am using is Airlink 101, AWLH4030.

When I go in the network tool to add it back in, it will let me do that but the configuration is lost as soon as I authenticate.

Anyone with similar issues, and a possible solution?

The wireless router I have is a Linksys WRT610N, and all other computers and printers connecting to it works still fine.

---

### Post by mcooke1 on 2009-11-02
I had problems with wireless after installing 9.10 and using synaptic installer I removed Network Manager and installed WICD, at the same time, and rebooted and my wireless is now better than it was in 9.04.

---

### Post by arilds on 2009-11-02
WICD won't run at all on my computer, so that does not help.  I am using the 64-bit version of 9.10, and I have tried to debug the issue but all I see is that the wicd process dies.

---

### Post by Unchqua on 2009-11-03
> **arilds said:**
> WICD won't run at all on my computer, so that does not help.  I am using the 64-bit version of 9.10, and I have tried to debug the issue but all I see is that the wicd process dies.
Did you try to do one lever lower and use standard command-line utilities to see if your wireless adapter works at all and can see your router? Your problem may be not with NM or Wicd.
Here's some examples:
[http://en.wikipedia.org/wiki/Wireless_tools_for_Linux#Package_tools](http://en.wikipedia.org/wiki/Wireless_tools_for_Linux#Package_tools)
[http://wirelessdefence.org/Contents/LinuxWirelessCommands.htm](http://wirelessdefence.org/Contents/LinuxWirelessCommands.htm)

---

