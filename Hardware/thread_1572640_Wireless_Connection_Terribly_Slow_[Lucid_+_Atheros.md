---
title: "Wireless Connection Terribly Slow [Lucid + Atheros AR9285]"
date: 2010-09-11
forum: Hardware
---

### Post by noran on 2010-09-11
Hello,

I have a Sony laptop, with an Atheros AR9285 wireless card. Wireless works out of the box on Ubuntu Lucid, but it's *extremely* slow. I don't really know my way around Linux yet. Should I install the proprietary drivers instead of using the default ones? If so then how can I do that? My laptop is a Sony VPC-CW2S1E/W. Proprietary drivers don't appear in the Restricted Drivers list.

Thanks :p

Noran

---

### Post by Xaifas on 2010-10-17
> **noran said:**
> Hello,

I have a Sony laptop, with an Atheros AR9285 wireless card. Wireless works out of the box on Ubuntu Lucid, but it's *extremely* slow. I don't really know my way around Linux yet. Should I install the proprietary drivers instead of using the default ones? If so then how can I do that? My laptop is a Sony VPC-CW2S1E/W. Proprietary drivers don't appear in the Restricted Drivers list.

Thanks :p

Noran

I have the exact same problem.

Disabled IPv6, no firewall, dns is fine yet its slow.

Runs smooth on windows but barely crawling on 10.4 ubuntu

---

### Post by dimoftheyard on 2010-10-17
I know, Xaifas, that you said you disabled IPv6, but I recommand you to recheck that. I had a problem with slow internet for a long time, and did not succeed in effectively turning off IPv6, as blacklisting the kernel moduls did not work. A good way to test this is wget -4 (on the console). If that downloads at a reasonable speed it's IPv6's fault. Another way is to turn off IPv6 in firefox (enter about:config and set network.dns.disableIPv6 to true).

If one of these work for the respective program you should turn off IPv6 by passing the kernel option ipv6.disable=1.

I hope that helps a little.

---

### Post by noran on 2010-11-13
> **dimoftheyard said:**
> I know, Xaifas, that you said you disabled IPv6, but I recommand you to recheck that. I had a problem with slow internet for a long time, and did not succeed in effectively turning off IPv6, as blacklisting the kernel moduls did not work. A good way to test this is wget -4 (on the console). If that downloads at a reasonable speed it's IPv6's fault. Another way is to turn off IPv6 in firefox (enter about:config and set network.dns.disableIPv6 to true).

If one of these work for the respective program you should turn off IPv6 by passing the kernel option ipv6.disable=1.

I hope that helps a little.

Thanks for your reply.

I tested wget -4, with the same result. Download speed is in bytes per second, and I have a broadband connection. It actually stopped completely after downloading 3% of a (very small) file.

I'm inclined to think it's a generic driver problem, but I have no idea how to solve it. :(

---

### Post by Istvan70 on 2010-11-13
I agree, I have the same card running in Maverick and am having speed issues as well. Testing speed with speedtest.net I am getting around 6 Mbps down and around 26 Mbps up (I am on 100M fiber :P). My wife who is on a Mac on the same wireless access point is getting around 50 up and down. I tried disabling IP 6 but it made no difference.

I also tried the wget -4 but saw no difference in performance. I am on the AMD64 build. The card worked immediately after the initial build, but the speed (at least down stream) is appalling.

---

### Post by Istvan70 on 2010-11-13
I tried the fix here

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/535222](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/535222)

It doubled my Download speed to 14Mbps but totally killed my upload speed (From 26 to 3).

On reboot it reverted to my previous driver so it was easy enough to backout of. You may want to try it and see if you get better results.

---

### Post by Istvan70 on 2010-11-13
I tried a number of things. I first tried to 
apt-get update 
apt-get upgrade
apt-get install ubuntu-restricted-extras

Nothing changed, I then tried the backport modules

sudo apt-get install linux-backports-modules-wireless-maverick-generic

That didn't help and I think it was worse by a little bit.

Finally I tried the bleeding edge compat drivers.

[http://wireless.kernel.org/en/users/Download/#Where_to_download_bleeding_edge](http://wireless.kernel.org/en/users/Download/#Where_to_download_bleeding_edge)

I went through the process there and it has helped a lot! I am now getting about 20Mbps down and 43Mbps up.

I can't speak for stability right now, but I can at least accept this performance for now.

---

### Post by Istvan70 on 2010-11-15
Just a quick follow-up. The compat drivers have been working flawlessly. I also checked out Google Chrome as a browser which is much faster (I can now often pull down 40Mpbs compared to 20Mbps on Firefox) so for me the issue is resolved. I hope this can help anyone else who is having these problems.

---

### Post by seventeener on 2011-01-04
Upgrading the ath5k module with the compat-wireless has doubled my wireless speed. But it's still as low as 3 Mbps. I run Ubuntu 9.10 on Samsung NC10.

---

