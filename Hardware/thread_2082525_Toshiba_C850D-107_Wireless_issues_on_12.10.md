---
title: "Toshiba C850D-107 Wireless issues on 12.10"
date: 2012-11-09
forum: Hardware
---

### Post by Oskarm on 2012-11-09
Hello.

Ever since I installed Ubuntu, my laptop seems to freak out, whenever I want to connect to a Wireless network.
This problem occurred in both 12.04 and 12.10.

Sometimes, when it tries to connect to a Wifi, it will freeze completely and does not unfreeze not hibernate, when I close it down. The only thing I can do is restart it.

Other times, when it actually manages to connect to a network, it will be after a long time.

If it freezes and I have to restart it... god help me... it takes about 14 times to start and restart, because it freezes immediately on log-in screen as it tries to connect to wireless. It actually took me 1hour 10 minutes just now to successfully restart it from the last time it froze.

The driver gives an error, when trying to install one found on this forum. I'll give the chipset name in a moment.
Also, ubuntu updates never occur, when connected to wireless. Just a strange fact I encountered.

```
oscar@oscar-SATELLITE-C850D-107:~$ lspci | grep Network

06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
oscar@oscar-SATELLITE-C850D-107:~$
```

It has absolutely no problems, when I use an ethernet cable by the way.
I'm wondering, what can I do to make wireless useful... at the moment its just an annoyance.

---

