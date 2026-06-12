---
title: "Packet loss within local network - flood ping"
date: 2009-02-25
forum: Hardware
---

### Post by seattle vic on 2009-02-25
My DSL upload speed starting having problems, and after several calls to my ISP, I came across an article that recommended a flood ping.  First I did that to the ISP and several outside web sites (a moderate 100 rapid pings), and dropped over 80% of the packets.  Then I did it within my local network (ie, to a desktop at 192.168.x.xxx with the same result.  Then I eliminated my wireless laptop that I'd been running from and did it just from one desktop to another.  Same result

Then I just pinged the router, with the same result.  Then I replaced the router with an older (non-wireless) router.  Same result:

======================================================

vic@vic-desktop:~$ sudo ping -c 100 -f 192.168.2.101
PING 192.168.2.101 (192.168.2.101) 56(84) bytes of data.
.....................................................................................
--- 192.168.2.101 ping statistics ---
100 packets transmitted, 15 received, 85% packet loss, time 1018ms
rtt min/avg/max/mdev = 0.131/0.187/0.257/0.036 ms, ipg/ewma 10.291/0.199 ms
vic@vic-desktop:~$

========================================================
This looks fishy, and I'm wondering if it's even a fair test?  I would "assume" that within the network, there should be no dropped packets at all, or at least down in the 1% level at worst.  It also drops less % packets if I send less (ie, 10 pings drops 5 packets, or 50%.  AND, no matter how many I send, it drops the exact same number every time (ie, 100 packets, 15 received, 85% loss, same every time)

My routers are both Linksys brands, the wireless a wrt54gl.  I even replaced the 12 volt adaptor to make sure it wasn't the power level to the router.

The one thing I've done differently lately is installed "the dish network", which has UHF remotes, and transmits via "HomePlug" technology over the power lines.  I don't have the homeplug adaptor hooked into the router now, and aren't even running wireless, so those should not be a factor.

Thanks in advance...

---

### Post by seattle vic on 2009-02-26
Well, the problem corrected itself, in that I "believe" that the DSL company (Qwest) tweaked some settings, and my upload speed has improved and I'm able to upload files to my company without errors.

HOWEVER, I still have the phenomenon of getting a lot of dropped packets within my home network when I do a flood ping:

% sudo ping -c 500 -f 192.168.1.1

I'd appreciate it if somebody would try this to see if there's something about this test within a local network that would cause dropped packets.  My system seems to be back to normal with these dropped packets, and it doesn't make sense.

Thanks.

---

