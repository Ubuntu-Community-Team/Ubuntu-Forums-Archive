---
title: "Driver support when building up from command-line"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by raptir on 2009-10-26
I love the ease of Ubuntu, but I'm installing to an Asus Eee PC with very limited disk space. I read about installing just a command-line system and then building up a graphical system by choosing packages manually. I've done this when installing both Debian and Arch Linux, but I wanted to make sure that driver support would still be there with a command line install. Could I just install the command-line and have WiFi/Video drivers installed, then install Xfce along with its network manager and get WiFi access, or would there be more to it than that? Also, for once I have a command-line system, is there a way to log into a WPA protected network from the command-line for while I install a GUI? Thanks.

---

### Post by raptir on 2009-10-27
Anyone have any idea? Wireless is really the only thing I haven't dealt with on my own with Linux.

---

### Post by MisfitI38 on 2009-10-27
> **raptir said:**
> I love the ease of Ubuntu, but I'm installing to an Asus Eee PC with very limited disk space. I read about installing just a command-line system and then building up a graphical system by choosing packages manually. I've done this when installing both Debian and Arch Linux, but I wanted to make sure that driver support would still be there with a command line install. 
Of course, yes. Drivers are in the kernel, or exist as loadable modules, in the distros you mention.
> 
Could I just install the command-line and have WiFi/Video drivers installed, then install Xfce along with its network manager and get WiFi access, or would there be more to it than that? 
You mentioned that you have installed Arch. If you followed the installation guide(s), you performed a similar procedure.
> 
Also, for once I have a command-line system, is there a way to log into a WPA protected network from the command-line for while I install a GUI? Thanks.
With wpa_supplicant, and/or netcfg on Arch, yes.

---

### Post by raptir on 2009-10-27
Sorry, I should have mentioned, I've only installed Arch on a desktop and a laptop so old it didn't have a wireless card. I've only dealt with wired network connections with Arch, which worked out of the box.

---

### Post by MisfitI38 on 2009-10-27
> **raptir said:**
> Sorry, I should have mentioned, I've only installed Arch on a desktop and a laptop so old it didn't have a wireless card. I've only dealt with wired network connections with Arch, which worked out of the box.

It will be fine. If you are using Arch, just follow the Beginners' Guide and the Wireless article and you should be good. There are also a few EEE resources in the wiki which are quite exhaustive.

I am sure you could cut Ubuntu down to size and make that work as well, with a minimal install.

---

