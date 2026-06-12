---
title: "SMW2835W V3 can't get it running!!!HELP!"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by greatshape on 2005-04-05
hi,
I got an SMC 2835W wireless card v3 (partnr. 99-012084-338 ) in my laptop running kubuntu.
I can't get the card to work. I installed ndiswrapper, and it says the card is loaded, but the lights on the card stay dead. I did not forget modprobe ndiswrapper.

Here is some output:

root@Kubuntu:/home/yves # ndiswrapper -l
Installed ndis drivers:
smc2835w        driver present, hardware present
root@Kubuntu:/home/yves # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

root@Kubuntu:/home/yves # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:9D:C9:78:AB
          inet addr:192.168.2.155  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fec9:78ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:677737 (661.8 KiB)  TX bytes:215174 (210.1 KiB)
          Interrupt:11 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@Kubuntu:/home/yves #                        

Any idea's?
regards steve

---

### Post by nocturn on 2005-04-05
Hmm, at first glance, I think you need to specify the ESSID of the wireless router.
Try scanning for it.

---

### Post by tumpy on 2005-04-05
I am running kubuntu live cd, i have the smc 2532w-b card i didnt had to do any adjustment of wlan0  nor the ndis, it work right out of the box,i just open up the webbrowser and i am online, i also test  simple mepis and had to do settings but ubuntu work without my intervention..

---

### Post by greatshape on 2005-04-06
[QUOTE=tumpy]I am running kubuntu live cd, i have the smc 2532w-b card i didnt had to do any adjustment of wlan0  nor the ndis, it work right out of the box,i just open up the webbrowser and i am online, i also test  simple mepis and had to do settings but ubuntu work without my intervention..[/QUOTE]

The SMC2835w V3 is another card, there's even a difference in the chipset in V2 to v3 i thought

---

### Post by greatshape on 2005-04-06
[QUOTE=nocturn]Hmm, at first glance, I think you need to specify the ESSID of the wireless router.
Try scanning for it.[/QUOTE]

I tried this already, even set it manually, not a solution  :cry: 
The NOT READY!!! is bothering me, it refers to the driver not doing what it should do i guess...

---

### Post by greatshape on 2005-04-09
ok solved. the problem was the prism54 module which was also loaded everytime and seemed to conflict with the ndiswrapper driver. Unloading the prism54 module solved the problem. The card was in the laptop when i installed Kubuntu, so the prism54 module was autom. configured during install.

Regards, steve

---

