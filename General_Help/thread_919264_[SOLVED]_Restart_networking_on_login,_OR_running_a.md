---
title: "[SOLVED] Restart networking on login, OR running a script as root without password"
date: 2008-09-13
forum: General Help
---

### Post by mb_webguy on 2008-09-13
I'm posting this here instead of the Networking forum because I have a non-networking-specific solution that I know would work if I could just figure out exactly how to implement it.

So here's the problem... Every time I reboot and login, I have to restart networking using "sudo /etc/init.d/networking restart" before I can connect to anything.  I don't know exactly why networking isn't starting correctly, but restarting it is an easy enough fix.  (If it matters, I'm using ndiswrapper to use my wireless card, and I have a manual wireless network configuration for a static IP.)

If someone can give me a solution that eliminates the need to restart networking on every reboot, that would be great.  But I'd be happy if I simply didn't have to manually enter the command every time.  I could put it in a script to run on login, but it requires root privileges so I'd still be prompted for my password.  I might as well be typing in the command.

So.... how can I run a script at login with root privileges without having to enter my password?

---

### Post by caljohnsmith on 2008-09-13
Have you by chance looked through your dmesg output after booting to see if there are any errors that might give a clue why you would have to restart networking every time you login? It would of course be great to find the root of your problem, but if you want a workaround in the meantime, you could put that networking restart command in your /etc/rc.local file. All commands in that file are run as root on start up, but they are run after the symlinks in /etc/rcS.d are run at start up; that's important in your case because rcS.d is where networking is started. So try adding
```
/etc/init.d/networking restart
```
at the bottom of rc.local, but before the "exit 0", and let me know if that works for you.

---

### Post by mb_webguy on 2008-09-13
Yes, I'd checked dmesg.  The only lines I noticed specifically mentioning wireless were:```
[   28.406632] wlan0: ethernet device 00:1c:26:ac:e8:9a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[   28.406707] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
...
[   28.349381] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

And thanks, putting the line in rc.local works perfectly.  I had thought of that, but wasn't sure about the order of execution.  With the line restarting networking in rc.local, dmesg shows the following:```
[   28.406632] wlan0: ethernet device 00:1c:26:ac:e8:9a using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[   28.406707] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
...
[   47.321935] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.646506] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.786687] wlan0: no IPv6 routers present

```

While my underlying networking problem still exists, this workaround seems to work just fine, so I'm marking the thread solved.  Thanks!

---

### Post by caljohnsmith on 2008-09-13
Glad it worked. :)

---

