---
title: "Broken USB port"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by zPenguin on 2005-12-14
Hello, I've been using ubuntu for about 11month now and I'm very happy with it. But I had a problem installing Ubuntu in the beginning. Continuously there were error messages from the kernel. So I tried another distro and 2 weeks later I tried Ubuntu with succes. No error messages at all. Then several months later the error messages were back. I have disconnected the whole USB thing on the motherboard (Card reader + 3 USB ports and 1 Firewire). So I lost alot of USB ports.

I have tried to plug it in with succes after a couple of months and it was always working (even the cardreader). I booted into windows and *bang* the problem was there again. I dont wanna blaim Windows but sometimes after a cold boot it works again.

I googled around and found out that there was a blacklist of hotplug, and maybe I can put the bad USB-port in that file. But I dont know how to start. I have asked on the IRC channel and they said that I could cut the wires of the bad USB-port, but that is a drastic solution.

The bad port is the cardreader itself but it doesnt get recognized. If I can disable the USB port with a blacklist (for hotplug) or somebody has another solution for it, tell me so.

Error messages:
[I]localhost kernel [4295785.398000] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
localhost kernel [4295799.121000] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
....[/I]
Every 15 seconds in the logs and the active terminal.

---

