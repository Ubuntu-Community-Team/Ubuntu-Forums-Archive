---
title: "Latest 2.6.27-11 updates breaks wireless and automounting"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Ingenium on 2009-01-30
I installed the update to 2.6.27-11 that came out last night (this is the third one in 3 days) and when I login jockey-gtk and jockey-backend crash. As a result, my wireless won't work, automounting of drives doesn't work, and if I don't have an ethernet cable plugged in when booting, that won't work either. It seems to be able to connect to wireless, but unable to get a DHCP address and fails. The same occurs if an ethernet cable is not plugged in before jockey crashes; it can't get a DHCP lease and fails.

Previous releases of 2.6.27-11 worked fine. I tried booting 2.6.27-9, but the problem somehow still persists. No other updates or changes were made other than the kernel, restricted modules, backports, headers, and other associated packages. Manually running jockey-gtk results in a crash immediately.

---

### Post by schwal on 2009-01-31
I have the same issue. reinstalled and updated with the same result. i have an acer aspire one.

---

### Post by schwal on 2009-01-31
actualy, i have the other wired bug described in this forum.

---

### Post by Ingenium on 2009-01-31
> **schwal said:**
> actualy, i have the other wired bug described in this forum.

I figured out that the wired bug can be fixed by disabling network manager and manually sending out a DHCP request:
```
sudo dhclient eth0
```
If network manager is still managing networking, it will immediately try to take over and you lose networking again.

No solution yet for the other bugs caused by this.

---

### Post by Ingenium on 2009-01-31
In the meantime, I just manually configured wpa_supplicant. Annoying, but at least it works. Once configured, just run wpa_supplicant followed by dhclient. Before you do this though, you need to right click on the network manager icon and disable networking. 

Jockey must be required for network manager to function. I bet installing wicd might also "fix" the issue, but I feel it's too drastic of a solution for something which will hopefully be short term...though this is assuming it's fixed in an update within the next couple days, which should at least be released because I've read about a lot of other bugs caused by the same update. Just have to hope our bug one of the ones fixed :p

---

### Post by Ingenium on 2009-02-16
Problem was fixed following directions here: [http://ubuntuforums.org/showthread.php?t=779992](http://ubuntuforums.org/showthread.php?t=779992)

It was a dbus problem, at least for me.

---

