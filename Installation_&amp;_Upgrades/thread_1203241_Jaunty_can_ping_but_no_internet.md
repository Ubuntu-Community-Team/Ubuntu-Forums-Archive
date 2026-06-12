---
title: "Jaunty can ping but no internet"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by taquinas on 2009-07-03
I've been trying on and off to get the internet working on Jaunty since April. I have Heron on a separate hard disk that's how I am posting this thread. I installed Jaunty on a Athlon 64 X2 motherboard before it fried due to chip fan failure. And now I have installed on a brand new AMD AM3 710 chipset motherboard. But still no internet.

I have internet connection with Heron and XP on the same machine. I can ping outside networks. I cannot update Ubuntu or browse with firefox. My dns server is visible in /etc/resolv.conf. 

A possible bug I have noticed was My wireless connection turns on (tick mark re-appears) everytime I reboot machine. Something that stays off in Heron when turned off.

Is the problem with the new network manager? Or is it ipv6?

Thanks for all the help.

---

### Post by Brandon Williams on 2009-07-03
Run tcpdump to determine what's happening when your try to browse. These tcpdump commands might be helpful.

To determine whether or not your machine is attempting to send any ipv6:
```
sudo tcpdump -i any ip6
```

To determine whether or not your machine is attempting ipv6 DNS lookups:
```
sudo tcpdump -v -i any port 53
```

To watch your http connections in order to determine whether or not they appear to be working in both directions:
```
sudo tcpdump -v -i any port 80
```

Post some dumps here if there is anything from the output that you don't understand.

---

