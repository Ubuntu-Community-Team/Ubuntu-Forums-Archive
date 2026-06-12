---
title: "what ubuntu version should I get for my hardware?"
date: 2017-01-14
forum: Hardware
---

### Post by Leon8200 on 2017-01-14
Hi all just got a new lappy and I read online that I should avoid the newer linux kernels due too bad driver support for my specific hardware, so I thought Id ask here on what version of ubuntu I should get for my **accer aspire 5517**, as I am wanting **non-free** drivers for my machine, thanx in advance.

```
inxi -Fxz
System:    Host: 82130853 Kernel: 3.19.0-32-generic x86_64 (64 bit gcc: 4.8.2)
           Desktop: MATE 1.12.0 (Gtk 3.10.8~8+qiana)
           Distro: Linux Mint 17.3 Rosa
Machine:   Mobo: Acer model: Aspire 5517 v: V1.09
           Bios: Acer v: V1.09 date: 11/30/2009
CPU:       Dual core AMD Athlon 64 X2 TK-55 (-MCP-) cache: 512 KB
           flags: (lm nx sse sse2 sse3 svm) bmips: 7182
           clock speeds: max: 1800 MHz 1: 1800 MHz 2: 1800 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS780M [Mobility Radeon HD 3200]
           bus-ID: 01:05.0
           Display Server: X.Org 1.17.1 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.1hz
           GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A
Audio:     Card Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k3.19.0-32-generic
Network:   Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k bus-ID: 02:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Qualcomm Atheros AR8132 Fast Ethernet
           driver: atl1c v: 1.0.1.1-NAPI port: 2000 bus-ID: 08:00.0
           IF: eth0 state: down mac: <filter>
Drives:    HDD Total Size: 320.1GB (16.9% used)
           ID-1: /dev/sda model: Hitachi_HTS54503 size: 320.1GB
Partition: ID-1: / size: 38G used: 6.5G (19%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 269M used: 47M (19%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 63.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 183 Uptime: 1:28 Memory: 683.7/2753.6MB
           Init: Upstart runlevel: 2 Gcc sys: 4.8.4
           Client: Shell (bash 4.3.111) inxi: 2.2.28 

```

---

### Post by kc1di on 2017-01-14
Your machine is very similar to the one I'm using right now and any of the following should work well
Ubuntu-mate, xubutu, lubuntu  I use Ubuntu-gnome and it works quite well. Unity is a bit slow but does work. 
I'm using version 16:10 but 16:04 LTS would be a good choice also.
I would try the above mentioned DEs on live usb or DVD first remembering that live sessions will be slower than installed and make sure they work
then choose the one you like the best for you style of computing. 
This is my opinion and you'll most likely get several, but only you will know when you find the right combo for you. 
Happy hunting. 
P.S. Mint is a fine Distro also is there a reason you want to change?

---

### Post by Leon8200 on 2017-01-14
> **kc1di said:**
> Your machine is very similar to the one I'm using right now and any of the following should work well
Ubuntu-mate, xubutu, lubuntu  I use Ubuntu-gnome and it works quite well. Unity is a bit slow but does work. 
I'm using version 16:10 but 16:04 LTS would be a good choice also.
I would try the above mentioned DEs on live usb or DVD first remembering that live sessions will be slower than installed and make sure they work
then choose the one you like the best for you style of computing. 
This is my opinion and you'll most likely get several, but only you will know when you find the right combo for you. 
Happy hunting. 
P.S. Mint is a fine Distro also is there a reason you want to change?

well... I read online that the newer linux kernels are using open source drivers instead of non-free drivers, and my current gaming performance with this machine is horrible, I am using mint 17.3, and I think if I switch to an older distro maybe that distro will use non-free drivers so I can get better gaming performance.

I know for sure that my machine has more power than what I need, yet its giving me horrable gaming performance, this can only be due to the fact that I am stuck with open source drivers.

---

### Post by kc1di on 2017-01-14
Your Graphics card is quite old by today's standards.  -- and the opensource driver is a good one for that card. 
don't know that you'll see a great improvement in it with non-free driver.  
but if you want to try you should be able to find one here:
[http://support.amd.com/en-us/download]("http://support.amd.com/en-us/download")
Look for X86_64 legacy driver.

---

### Post by Yellow Pasque on 2017-01-14
You are limited to 12.04.1 if you insist on using fglrx. Official support for 12.04.x is going to end in April.

> GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A

Did you have mesa-utils package installed when you ran the inxi script? If you did, double check that you have 3D working properly because there really should be output describing the mesa version where it says 'N/A'.

---

### Post by Leon8200 on 2017-01-15
I tried the legacy driver and that failed, so I installed 12.04, and it also had bad performance.

Now I installed the fglrx-legacy and I am unable to boot into ubuntu, I get a flashing message saying something like (v runlevel compatibility).

And I cant use the open source driver because it really gives terrable performance, I had another laptop that didnt even have half the cpu or gpu that this pc has and it gave me twice the fps.

So now what?
Do I give up on finding a working nonfree driver?

---

### Post by Leon8200 on 2017-01-15
O sorry I missed that last part,
When I ran the inxi script, I was using mint 17.3 and I did have working 3d but I was geting terrable fps, thats why I am wanting to get a working non-free driver.

---

### Post by Yellow Pasque on 2017-01-15
Can you give an example of what are you trying to do that gets terrible fps?

> thats why I am wanting to get a working non-free driver. 
If you can't tell from my last post, fglrx/Catalyst is a dead end for a GPU this old. Even if you got it working, you would still be running a very old distro that will no longer receive important/security updates in a few months.

---

