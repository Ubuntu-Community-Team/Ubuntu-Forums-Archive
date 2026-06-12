---
title: "Network Configuration"
date: 2013-12-02
forum: Hardware
---

### Post by miguel6 on 2013-12-02
If you have any input please help.

I just bought a Acer Aspire E1-572-6870 [http://us.acer.com/ac/en/US/content/model/NX.M8EAA.002](http://us.acer.com/ac/en/US/content/model/NX.M8EAA.002)

I use it for class and connecting to internet is important. I can't get my ethernet port to work. I also can't connect to the schools wireless because I have to pay $$$ for a certificate to connect to the wifi with a operating system that is not Windows or OS X.............

using ifconfig I get this output:

```
mig@mig-Aspire-E1-572:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35975 (35.9 KB)  TX bytes:35975 (35.9 KB)

wlan0     Link encap:Ethernet  HWaddr 24:fd:52:2a:6c:96  
          inet addr:192.168.43.123  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::26fd:52ff:fe2a:6c96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3078606 (3.0 MB)  TX bytes:422813 (422.8 KB)
```

So wlan0 is my ethernet port i'm assuming. It is detected but when I plug in a cat5 cable it won't connect to internet. It won't even recognize it is there. The light will flicker on the port but as of Ubuntu 13.10 is dosen't do anything.

Reading this...[https://help.ubuntu.com/13.04/serverguide/network-configuration.html](https://help.ubuntu.com/13.04/serverguide/network-configuration.html) do I have to configure my ethernet port ?

I was going to try this:

"To configure a default gateway, you can use the route              command in the following manner.  Modify the default gateway address to match              your network requirements." - the link above

```
sudo route add default gw 10.0.0.1 eth0
```

that is the example they gave so i'd have to change it to...

```
sudo route add default gw 192.168.43.123 wlan0
```

i'm not sure if that is correct. any help. Laptop was just purchased so I guess the kernal simply dosen't have drivers yet for this hardware but that dosen't seem right since it does see it in ifconfig.

JUST TO MAKE SURE: WIFI DOES WORK. IT'S JUST ETHERNET.

---

### Post by The Cog on 2013-12-02
wlan0 is your wireless lan. ifconfig doesn't show the ethernet port at all, which is a bit worrying.
You could try "ifconfig -a" which shows all network ports, even the non-configured ones. But let's try to list the hardware and see what's there. Try this command:
```
lspci -v
```
and post the bits about the ethernet controller.

---

### Post by miguel6 on 2013-12-02
thank-you so much for a quick response. I'm literally in class right now on my phones tethered bandwidth which is limited to 1 gb.

Here is the output to that command. I placed the entire output into a pastie link if that helps to view it.

[http://pastie.org/8523422](http://pastie.org/8523422)

> 01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57786 Gigabit Ethernet PCIe (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 0775
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at b0410000 (64-bit, prefetchable) [size=64K]
    Memory at b0420000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at b0430000 [disabled] [size=2K]
    Capabilities: <access denied>

I'm searching for some fix to enabling NetXtreme BCM57786 Gigabit Ethernet PCIe on Ubuntu. I hope i'm going in the right direction.

---

### Post by miguel6 on 2013-12-03
This problem was resolved after I was able to download a GeoTrust certificate and connect to my schools wifi then checked for updates and downloaded 160 MB of downloads lol...after that I restarted and now ethernet works!

---

