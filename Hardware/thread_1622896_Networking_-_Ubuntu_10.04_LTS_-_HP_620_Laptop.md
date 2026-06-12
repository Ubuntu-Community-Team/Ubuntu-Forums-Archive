---
title: "Networking - Ubuntu 10.04 LTS - HP 620 Laptop"
date: 2010-11-16
forum: Hardware
---

### Post by jwoodward on 2010-11-16
My network drops out every now and again.
I have tried rebooting network-manager and this does not resolve the problem I have to do a full reboot.

Below are the results from ip link and as you can see 'state UNKNOWN'.

*******@*****:~$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 1c:c1:de:9b:52:2e brd ff:ff:ff:ff:ff:ff
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DORMANT qlen 1000
    link/ether 70:f1:a1:a4:15:98 brd ff:ff:ff:ff:ff:ff
4: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
5: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether 0e:08:d1:66:c4:53 brd ff:ff:ff:ff:ff:ff


The other problem I am facing is if I boot the laptop with an external monitor attached everything loads massive resolution and I cannot change it unless I boot with the laptop screen and apply the external one once booted.

Any ideas? Thanks.

---

### Post by jwoodward on 2010-11-16
Another problem with this version on my laptop, there is no sound! Alsamixer reports the INTEL HDMI and the volumes are up but nothing.

Card: HDA Intel                                                                                                                              
Chip: Intel G45 DEVCTG 
 Item: Master [dB gain: 0.00, 0.00]

jwoodward@jwoodward-lt:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by jwoodward on 2010-11-16
Done some more tests and I have found that it is working from the headphone output playing through external speakers but does not come out the laptops default built in output so I assume that output of the sound driver is not being linked properly.

---

### Post by bixejo on 2010-12-18
> **jwoodward said:**
> Done some more tests and I have found that it is working from the headphone output playing through external speakers but does not come out the laptops default built in output so I assume that output of the sound driver is not being linked properly.
Hi, jwoodward. Did you find a solution for this? I've just bought the same laptop and gettign the same issue. I'm planning to give it back to the shop in I do not solve this in the 10 days left to do so.

Thanks for your help.

Regards,

---

### Post by gdonwallace on 2011-01-19
Thought I would add my name to the list. My wireless is also doing this, but it just started today.

I am gong to reboot the wireless and router after the office clears out and see if that helps, but anything else that anyone might try to fix would also be helpful.

---

