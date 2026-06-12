---
title: "Digitus DN-3023: Gigabit Ethernet USB 3.0 adapter"
date: 2012-11-30
forum: Hardware
---

### Post by dpjg on 2012-11-30
Does anybody know, whether this device is supported under linux/ubuntu? I could not find an answer via google, etc.

[/0/"]Manufacturer product website]("http://www.digitus.info/en/products/network/gigabit-ethernet-network/network-interface-cards/gigabit-ethernet-usb-30-adapter-dn-3023/#!prettyPhoto[set)

---

### Post by dpjg on 2012-12-01
I decided to just buy the device. It does not seem to work out of the box. This is the output of lsusb: [http://pastebin.com/weWZJ6ZG](http://pastebin.com/weWZJ6ZG)

It seems to be a re-branded version of this device: ASIX AX88179. An Android/Linux drives seems to be available too. I will try that out later:

[http://www.asix.com.tw/products.php?op=pItemdetail&PItemID=131;71;112](http://www.asix.com.tw/products.php?op=pItemdetail&PItemID=131;71;112)

---

### Post by dpjg on 2012-12-01
Final step: driver from hardware manufacturer compiles and works unter 12.10:

[http://www.asix.com.tw/FrootAttach/driver/AX88179_178A_LINUX_DRIVER_v1.2.0_SOURCE.tar.bz2](http://www.asix.com.tw/FrootAttach/driver/AX88179_178A_LINUX_DRIVER_v1.2.0_SOURCE.tar.bz2)

---

### Post by abraxxa on 2013-01-11
If others are also searching for infos how to build the driver:
sudo su
apt-get install linux-headers-generic
change Makefile to: KDIR    = /usr/src/linux-headers-$(CURRENT)
make
make install

The driver is automatically loaded when the usb adapter is pluged in.

---

### Post by dpjg on 2013-01-11
Strange, the driver compiled for me even without changing the makefile. You are right, that kernel headers have to be installed.

---

### Post by B@rt_d@_M@n on 2013-01-17
Could anybody help me how to install this driver onto a Synology DS209 NAS?

---

### Post by dpjg on 2013-02-12
The driver has been updated to v1.3.0: [http://www.asix.com.tw/FrootAttach/driver/AX88179_178A_LINUX_DRIVER_v1.3.0_SOURCE.tar.bz2](http://www.asix.com.tw/FrootAttach/driver/AX88179_178A_LINUX_DRIVER_v1.3.0_SOURCE.tar.bz2).

---

### Post by dpjg on 2013-02-12
> **B@rt_d@_M@n said:**
> Could anybody help me how to install this driver onto a Synology DS209 NAS?

Sorry for my ignorance, but could you answer the following questions first:

[LIST]
[*]Does the Synology DS209 NAS run linux?
[*]If yes, which "distribution" if any?
[*]Do you have root access?
[/LIST]

---

### Post by dpjg on 2013-02-12
> **B@rt_d@_M@n said:**
> Could anybody help me how to install this driver onto a Synology DS209 NAS?

Sorry for second guessing, but why do you want to use an ethernet usb adapter on a device with a built gigabit ethernet?

---

### Post by B@rt_d@_M@n on 2013-02-13
> **dpjg said:**
> Sorry for second guessing, but why do you want to use an ethernet usb adapter on a device with a built gigabit ethernet?

Because I need a second Ethernet connection for the IPTV streams. 
I would like to run DVBLOGIC IPTV server on my NAS.

---

### Post by dpjg on 2013-02-14
> **B@rt_d@_M@n said:**
> Because I need a second Ethernet connection for the IPTV streams. 
I would like to run DVBLOGIC IPTV server on my NAS.

Ok. Could you try to describe the OS running on the NAS in a bit more detail (ie. answer my other questions from above)?

---

### Post by longint on 2013-03-16
The ASIX drivers are runnign fine using Ubuntu 13.04. Compared to a USB 2.0 dongle I get reasonable more network performance out if (17+  MB/s instead of less about 11MB/s on my cheap home network).

Isn't there any package/repository including this driver to make sure it gets automagically updated or recompiled in case of kernel updates?

---

### Post by dpjg on 2013-03-16
[FONT=arial black][FONT=arial][/FONT][/FONT]@longint: I thought about packaging the driver and using dkms in the past, but could not find time to do it. It looks like that the driver is on its way to hit mainland. So the problem will go away with the next but one ubuntu release.

---

### Post by federmejo87 on 2013-04-04
Hi,

First of all thank for the advice :D

So, i have a DN-3023 because now i'm working in the university bunker without  WLAN :-(
Under Windows work very well, under ubuntu work but with a lot of disconnection. Have you some idea about? 

Driver: AX88179_178A_LINUX_DRIVER_v1.4.0_SOURCE but i tried also v1.3

Perhaps it is useful to see the logs present in the link below. The first one it's about 10 minut log, the second one it's a two day filtred by disconnetion.

[http://pastebin.com/grEmLTkW](http://pastebin.com/grEmLTkW)
[http://pastebin.com/C2Ue3C3c](http://pastebin.com/C2Ue3C3c)

Thank you. :D

---

### Post by dpjg on 2013-04-04
> **federmejo87 said:**
> Under Windows work very well, under ubuntu work but with a lot of disconnection. Have you some idea about? 

Driver: AX88179_178A_LINUX_DRIVER_v1.4.0_SOURCE but i tried also v1.3

Perhaps it is useful to see the logs present in the link below. The first one it's about 10 minut log, the second one it's a two day filtred by disconnetion.

[http://pastebin.com/grEmLTkW](http://pastebin.com/grEmLTkW)
[http://pastebin.com/C2Ue3C3c](http://pastebin.com/C2Ue3C3c)

Beyond the obvious (the usb device disconnects) I cannot see what the reason for this behavior could be (the logs don't say it). Maybe it is best to get in contact with the developer(s) of the driver and check what goes wrong: Freddy Xin (freddy AT asix DOT com DOT tw). Furthermore, it would be great if you could try to reproduce the problem on a usb2 plug and/or another laptop.

In case anyone in the future reads this, the driver [has been merged]("http://marc.info/?l=linux-kernel&m=136229306208003&w=2") into the mainline kernel. If you are running 3.9 (still not released at the time of writing) or later, the driver is included out of the box.

---

### Post by federmejo87 on 2013-04-04
> **dpjg said:**
> Beyond the obvious (the usb device disconnects) I cannot see what the reason for this behavior could be (the logs don't say it). Maybe it is best to get in contact with the developer(s) of the driver and check what goes wrong: Freddy Xin (freddy AT asix DOT com DOT tw). Furthermore, it would be great if you could try to reproduce the problem on a usb2 plug and/or another laptop.

In case anyone in the future reads this, the driver [has been merged]("http://marc.info/?l=linux-kernel&m=136229306208003&w=2") into the mainline kernel. If you are running 3.9 (still not released at the time of writing) or later, the driver is included out of the box.

I'm texting rigth now to Freddy Xin.

My notebook have not USB2 :-( and on my desktops (home and work) i have only windows, i don't know if it's the same try with a live distro.

P.s.: I have tried to analize the time between disconnections without results. So it's not time-dependent.

[ATTACH=CONFIG]240954[/ATTACH]

---

### Post by dpjg on 2013-04-04
> **federmejo87 said:**
> I'm texting rigth now to Freddy Xin.

...

P.s.: I have tried to analize the time between disconnections without results. So it's not time-dependent.

Would be great if you could keep us informed! Disconnect time analysis: good job! :D

---

### Post by federmejo87 on 2013-04-04
Thank you, i work every day with Wolfram Mathematica, now we also know how to make coffee with Mathematica!!! :D

I will keep you in touch.

---

### Post by czikus on 2013-04-04
Hi,

Could someone please share the driver source package somewhere? The ASIX website is down and I cannot download the driver using the official link. 

Thanks a lot!
Andrzej

---

### Post by dpjg on 2013-04-05
The ASIX Website is up again. Alternatively I uploaded the driver [over here]("http://www.file-upload.net/download-7427842/AX88179_178A_LINUX_DRIVER_v1.4.0_SOURCE.tar.bz2.html").

---

### Post by dpjg on 2013-04-27
I just confirmed that driver version 1.4.0 works flawlessly under 13.04.

---

### Post by CyberAngel on 2013-06-26
I see many people reporting success with this device under Linux but unfortunately this is not the case for me on Ubuntu 12.10 and 13.04 on a Dell XPS 13 Developer Edition. I compile the driver (v1.4.0) without any problems (make, make install), I load it using modprobe and I see it as eth2. I can even see some RX/TX traffic but it cannot acquire an IP address so it is unusable.

dmesg output:
```
    [ 1338.583575] ASIX USB Ethernet Adapter:v1.4.0 10:01:27 Jun 26 2013
    [ 1338.583575]          http://www.asix.com.tw
    [ 1338.583599] ax88179_178a 4-2:1.0 (unregistered net_device): mtu 1500
    [ 1338.584080] ax88179_178a 4-2:1.0 eth0: register 'ax88179_178a' at usb-0000:00:14.0-2, ASIX AX88179 USB 3.0 Gigibit Ethernet, 00:24:9b:06:6a:85
    [ 1338.585110] usbcore: registered new interface driver ax88179_178a
    [ 1338.932157] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
    [ 1338.933382] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
    [ 1341.887977] ax88179_178a 4-2:1.0 eth2: ax88179_178a - Link status is: 1
    [ 1341.889595] ax88179_178a 4-2:1.0 eth2: Write medium type: 0x013f
    [ 1341.890699] IPv6: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
    [ 1341.891748] ax88179_178a 4-2:1.0 eth2: link up, 1000Mbps, full-duplex, lpa 0xC1E1
```

ifconfig output:
```

    eth2      Link encap:Ethernet  HWaddr 00:24:9b:06:6a:85  
              inet6 addr: fe80::224:9bff:fe06:6a85/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:76623 errors:1 dropped:22802 overruns:0 frame:1
              TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:2601276 (2.6 MB)  TX bytes:109741 (109.7 KB)
```

A different USB 2.0 Gigabit ethernet adapter and the WiFi are both working fine, so networking shouldn't be a problem on my laptop. 

Is there something I miss for this specific chipset?
Any suggestion on how to debug this further?

---

### Post by dpjg on 2013-06-26
@CyberAngel: Stupid question, but maybe it is a good idea to rule out a hardware problem first: does the device work on another laptop and/or under Windows? If this is the case, I would suggest to contact the developer of the driver (Freddy Xin, contact details are mentioned above) directly.

---

### Post by CyberAngel on 2013-06-26
> **dpjg said:**
> @CyberAngel: Stupid question, but maybe it is a good idea to rule out a hardware problem first: does the device work on another laptop and/or under Windows? If this is the case, I would suggest to contact the developer of the driver (Freddy Xin, contact details are mentioned above) directly.

I haven't tried this specific Digitus device, but I have tried an STLab USB 3.0 Docking Station (which provides 3 USB 3.0 ports + 1 Gigabit Ethernet port based on this chipset) and a Startech USB 3.0 Gigabit Ethernet Adapter. Both of them behave the same. I am going to try it now on different hardware with Ubuntu 12.04 (USB 2.0 Ports on the motherboard though) and see if it works.

---

### Post by dpjg on 2013-06-26
Well, it could be that this specific Digitus device is broken. My intention was to rule this out (as it seems to work "for everybody else").

---

### Post by CyberAngel on 2013-06-26
It looks like it's working on different hardware that I tried it. It must be something with Dell XPS 13 then.

---

### Post by webworka on 2013-07-10
> **CyberAngel said:**
> 
[...]
Is there something I miss for this specific chipset?
Any suggestion on how to debug this further?


I had the very same problem on a Dell XPS 13. The Solution was to upgrade to Kernel 3.10 as described here: [http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/](http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/)

---

### Post by CyberAngel on 2013-07-10
> **webworka said:**
> I had the very same problem on a Dell XPS 13. The Solution was to upgrade to Kernel 3.10 as described here: [http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/](http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/)

So it is something with the Dell XPS 13..

Thanks for replying on this! I will try to upgrade to the latest kernel tomorrow and report if it fixes the problem.

---

### Post by CyberAngel on 2013-07-16
I tested with 3.9 and 3.10.1 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) but still no luck :/

Same weird behavior. Recognised, dmesg shows link is up at 1000Mbps, the packet counter of ifconfig increases and then the error counter increases as well :(

---

### Post by johnsto on 2013-08-07
> **CyberAngel said:**
> I tested with 3.9 and 3.10.1 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) but still no luck :/

Same weird behavior. Recognised, dmesg shows link is up at 1000Mbps, the packet counter of ifconfig increases and then the error counter increases as well :(

Exact same problem here as well on my office network. Connects perfectly fine on a Win7 (non XPS13) box, but no luck on 13.04 with 3.10 kernel.

It does get as far as establishing a 1Gbps connection, obtaining the correct IP, gateway and DNS servers via DHCP (exactly same as on Win7), but after that, it can't ping any of them nor resolve any addresses.

That said, it works perfectly fine on my home network, also via DHCP (but at 100mbps as that's the limit of my router) - but haven't found any kernel option to force 100mbps in case that's related to this issue.

---

### Post by johnsto on 2013-08-07
Hah, and just like that I guessed correctly!

After forcing 100mbps mode, it now connects perfectly fine. Try running this command to force 100mbps on the current connection (be sure to choose the correct eth interface):

```
sudo ethtool -s eth1 speed 100 duplex full antoneg off
```

No need to connect/reconnect - it should start working immediately.

You can switch back to 1Gbps with:

```
sudo ethtool -s eth1 speed **1000** duplex full antoneg off
```

...which in my case returned it back to it's original non-functional state.

---

### Post by pmgast on 2013-08-18
Hi johnsto,

I also own a Dell XPS13 developer edition and I am interested in bying a usb3 to ethernet converter. I have seen that the driver version 1.5 is out and would like to know if the speed problem is maybe fixed with the new release. It would be nice if you could test it and tell me about it.
Many thanks in advance! :-)

---

### Post by johnsto on 2013-08-18
> **pmgast said:**
> I also own a Dell XPS13 developer edition and I am interested in bying a usb3 to ethernet converter. I have seen that the driver version 1.5 is out and would like to know if the speed problem is maybe fixed with the new release. It would be nice if you could test it and tell me about it.

I tried 1.5, but exact same issue as 1.4 - the adapter only worked when restricted to 100mbps.

---

### Post by pmgast on 2013-08-18
Thanks for the info.
Are there any alternatives not based on the ASIX AX88179 chip that you know of? It is quite useless bying a usb3 device if you can only use it at 100mbps speed...

---

### Post by johnsto on 2013-08-18
> **pmgast said:**
> Thanks for the info.
Are there any alternatives not based on the ASIX AX88179 chip that you know of? It is quite useless bying a usb3 device if you can only use it at 100mbps speed...

I'm not sure. 

Since this is a driver or firmware issue, I'm hoping by the time I have a Gigabit network at home, the issue will be fixed!

---

### Post by CyberAngel on 2013-08-19
I can confirm that forcing it to work at 100Mbps does the trick. Not the best solution for a Gigabit card, but better than no connectivity at all.

---

### Post by johnsto on 2013-08-20
There's a suggestion on [this GitHub issue]("https://github.com/FreddyXin/ax88179_178a/issues/1") that 1Gbps negotation might work if you have kernel 3.10. I've yet to test this myself though.

---

### Post by CyberAngel on 2013-08-20
> **johnsto said:**
> There's a suggestion on [this GitHub issue]("https://github.com/FreddyXin/ax88179_178a/issues/1") that 1Gbps negotation might work if you have kernel 3.10. I've yet to test this myself though.

I tried once sometime ago but it didn't work. I might try once more now with driver version 1.5.0.

---

### Post by johnsto on 2013-08-22
> **CyberAngel said:**
> I tried once sometime ago but it didn't work. I might try once more now with driver version 1.5.0.

Tried with 1.5.0 and kernel 3.10.7 - no luck either.

---

### Post by pauloppenheim on 2013-09-09
Filed a new bug on the AX88179 driver github page: [https://github.com/FreddyXin/ax88179_178a/issues/5](https://github.com/FreddyXin/ax88179_178a/issues/5)

As it's github, you can star / watch for updates.

---

### Post by pauloppenheim on 2013-11-14
There is now a patch on that github issue that resolves the issue for me.

---

### Post by CyberAngel on 2013-11-14
For me it works as well now with the latest driver.

---

