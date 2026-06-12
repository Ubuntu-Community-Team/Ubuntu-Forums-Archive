---
title: "Weird problem with ethernet card"
date: 2012-01-02
forum: Hardware
---

### Post by khaos1 on 2012-01-02
Hi guys I'm using ubuntu 10.10 maverick in my netbook acer aspire one d255. I'm facing a weird problem with my ethernet interface (eth0). *Sometimes* when I boot in ubuntu the eth0 interface is not listed in: ifconfig but it's listed in lspci.

Here is the logs:
My lspci for the ethernet:

> 01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)

My ifconfig:
> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:8e:d5:50  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe8e:d550/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50500413 (50.5 MB)  TX bytes:3459850 (3.4 MB)


And when I type ifconfig eth0 up:
> eth0: ERROR while getting interface flags: No such device

My lsmod: [http://pastebin.com/41eQi1W8](http://pastebin.com/41eQi1W8)
My sudo lshw -C network: [http://pastebin.com/GKvXJcva](http://pastebin.com/GKvXJcva)

The weird thing is that some times the eth0 is listed and works ok. I must note that I have triple boot: Ubuntu/Win7/Debian Testing

Thanks in advance

---

### Post by khaos1 on 2012-01-02
I have updated the post with all the output
Any help is appreciated :)

---

### Post by drdos2006 on 2012-01-02
Check out this link. It may be that you need to "bond" the two network NICs.

[http://ubuntuforums.org/showthread.php?p=11320085#post11320085](http://ubuntuforums.org/showthread.php?p=11320085#post11320085)

regards

---

### Post by khaos1 on 2012-01-03
Thanks for your reply but I dont understand why to bond two network interfaces because in my case the ethernet is not shown! :S

---

### Post by librechick on 2012-01-03
It sounds like a defective nic. Can you confirm the nic works from a live CD or secondary OS?

---

### Post by khaos1 on 2012-01-03
> **librechick said:**
> It sounds like a defective nic. Can you confirm the nic works from a live CD or secondary OS?

Hmm thanks for your answer. As I wrote in my 1st post I have triple boot (Ubuntu/Debian testing/win7). The same problem I face in Debian Testing. I have not faced the same problem in Windows 7 but I use them rarely. I think that If there is no driver issue the problem is harware error :S

Sometimes it works sometimes it doens't recognised. Is this a hardware fault?
I'm trying to find a way to check if the driver is ok but I don't know

I mean that sometimes is appeared in ifconfig list and sometimes not.

---

### Post by librechick on 2012-01-08
> **khaos1 said:**
> Hmm thanks for your answer. As I wrote in my 1st post I have triple boot (Ubuntu/Debian testing/win7). The same problem I face in Debian Testing. I have not faced the same problem in Windows 7 but I use them rarely. I think that If there is no driver issue the problem is harware error :S

Sometimes it works sometimes it doens't recognised. Is this a hardware fault?
I'm trying to find a way to check if the driver is ok but I don't know

I mean that sometimes is appeared in ifconfig list and sometimes not.

It sounds like a hardware problem to me, Flaky. 

[http://www.thinkpenguin.com/](http://www.thinkpenguin.com/) has a USB ethernet. could try that.

---

