---
title: "Error PCIE Bus...."
date: 2018-09-07
forum: Hardware
---

### Post by thierrylsomon on 2018-09-07
Hello. I have recently encountered a problem while trying to install another distro from live CD. I have also noticed it happened when switching sessions (CTRL-ALT-F1) in my current Kubuntu distro.

My issue is the following: I keep getting an error message spammed in the console (when booting in live CD I get it each time the installer displays a terminal):

```
pcieport 0000:00:1c.5 PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e5(Transmitter ID)
device [8086:9d15] error status/mask=000030000/000020000
[12] Replay TImer Timeout
```

I have already seen this issue on similar posts, but the solutions given  to them (adding the option "pci=nomsi" or "pci=noaer") in the GRUB kernel  options didn't work out for me. I couldn't find any more help so I'm no  requesting yours.

Thanks in advance!

---

