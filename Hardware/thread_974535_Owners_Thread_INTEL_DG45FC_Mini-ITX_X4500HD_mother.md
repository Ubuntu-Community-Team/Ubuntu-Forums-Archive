---
title: "Owners Thread: INTEL DG45FC Mini-ITX X4500HD motherbord"
date: 2008-11-07
forum: Hardware
---

### Post by ghat on 2008-11-07
hi

got this motherboard to upgrade my sysB, until the nvidia mcp7a boards become plenty..

Installed Intrepid and most things seem to work well.
Installed XBMC/Atlantis (compiled from source) and currently struggling with the wiimote to work.

Found this nice keyboard...

[http://www.madcatz.com/Default.asp?Page=352&CategoryImg=PS3_Controllers](http://www.madcatz.com/Default.asp?Page=352&CategoryImg=PS3_Controllers)

[IMG]http://www.madcatz.com/Images2/products/enlarge/8829.gif[/IMG]

works like a charm
```

Nov  6 17:17:13 htpc kernel: [14590.756618] usb 3-2: new low speed USB device using uhci_hcd and address 4
Nov  6 17:17:13 htpc kernel: [14590.931213] usb 3-2: configuration #1 chosen from 1 choice
Nov  6 17:17:13 htpc kernel: [14590.948457] input: Device USB Device as /devices/pci0000:00/0000:00:1a.2/usb3/3-2/3-2:1.0/input/input6
Nov  6 17:17:13 htpc kernel: [14591.012788] input,hidraw2: USB HID v1.10 Keyboard [Device USB Device] on usb-0000:00:1a.2-2

```

but missing some keys...

---

### Post by ghat on 2008-11-07
hi

Does anyone know where I can buy a spare IO shield for this motherboard. I guess most G45 motherboards have the same type of IO shields..

G
> 
I found the site where I can buy the IO sheld...

[https://www.industryeducation.com/-I_O_Shield___E30164-P6313.aspx ](https://www.industryeducation.com/-I_O_Shield___E30164-P6313.aspx )
You can confirm the part number from here
[http://www.intel.com/support/motherboards/desktop/sb/cs-009031.htm](http://www.intel.com/support/motherboards/desktop/sb/cs-009031.htm)
enjoy


---

### Post by ghat on 2008-11-10
hi again...


Wiimote works...

HDMI output works from PC->Denon2808->SharpSE94U

Digital Audio... does not still work....
Any comments any one ? I have connected the optical out to the Denon's optical In, and have assigned the input but it does not detect any signal. 

Is the audio sent over the HDMI?Analog?optical in intrepid ?


G

---

### Post by ghat on 2008-11-12
ha

its only me on this thread.... no users of ubuntu for this board I guess. 

I have another problem, when the machine is idle, the fan  keeps revving... like a car trying to start... Its very embarrassing for my family.. 

I was looking into the acpi control for the CPU fan and there is no support... 

root@htpc:~# cat /proc/acpi/processor/CPU1/
info        limit       power       throttling  
root@htpc:~# cat /proc/acpi/processor/CPU1/info 
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no
root@htpc:~# cat /proc/acpi/processor/CPU1/limit 
<not supported>
root@htpc:~# cat /proc/acpi/processor/CPU1/throttling 
<not supported>
root@htpc:~# acpi -v
acpi 1.1

Copyright (C) 2001 Grahame Bowland.
              2008 Michael Meskes.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
root@htpc:~# acpi -a
root@htpc:~# acpi -t
root@htpc:~# 

Any hints on getting this working...

G

---

### Post by kingmoffa on 2008-11-19
Hi, 

I also have this motherboard. Im running mythbunutu 8.10 from a usb disk on it and most things seem to have been detected and work ok. 

I cannot seem to get audio over the hdmi. Can you please tell me how you got this working?

I've tried alsamixer and unmuting the different sections. 

I can also confirm my cpu doesn't seem to have processor throttling either.

---

### Post by notanatheist on 2008-12-10
Don't worry, you're not the only one with this board. I've had mine since the moment they were available. I bugged the Intel rep very regularly about them for months. Which leads to your question. Any Authorized Intel Reseller should be able to get you a spare I/O plate. Should be under $10.

Audio over HDMI not working here yet either. I've tried everything I can under alsamixer with no results. Interesting thing is when you look at "lspci" you'll see a "Conexant Systems Video and Audio Decoder". I'm thinking that may be for the HDMI audio but "asoundconf list" doesn't give any options other than the Intel HDA. 

Also, I'm using the Gyration kebyboard and remote which I can strongly NOT recommend at this point. I've actually got a secondary USB keyboard plugged in due to the troubles I've had with this set. The responsiveness is pure suck. The remote capabilities are barely okay. The only worthwhile feature is the remote can handle up to 4 devices via IR and RF. 

That's just my $0.02 on the matter. I'll be testing more components soon (MS Bluetooth Media Center set and Soundgraph iMedion remote) and will post in one of the two threads I've been in about this board. Look for that in the next week or two.

---

### Post by jollyr0ger on 2008-12-23
hi to all! I'm oem and I'm selling a media center based on this board. The machine works, but I've the problem that there's not soud over hdmi. I don't know where to look, if you have some suggestion please give them to me too.

another thing, some our customer said to us that the fan is noisy. I think that is noisy like a normal pc. what's your opinion about it?

---

### Post by comcute on 2009-02-06
I am using it with mythbuntu. Everything works pretty OK, including sound over HDMI. It has this infamous video tearing problem and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275351](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275351).

---

### Post by ghat on 2009-03-19
hi guys

I am back with the fan cycle/spinup problem.. 
actually it never went away, only I went away to vista..

I wanted to try Boxee, so updated to jaunty as the kernel and driver have audio over hdmi in it (I guess)
and the problem is too audible... 

I tried to get into the Intel MEBx and disable to fan control but this seems to disable the POST and bios completely... what a pain... 
I have to recover by removing the jumper... 

HUH... never will I ever recommend a intel g45 chipset to anyone..

Ghat
:(

PS: I am using this case...
[http://www.silentpcreview.com/apex-mi008](http://www.silentpcreview.com/apex-mi008)

and using the BIOS...
IDG4510H.86A.0089.2009.0109.1533

which is the latest...

---

### Post by ghat on 2009-03-19
hi fellas...

I am trying to do the following now...

1. get lm-sensors to work properly on this board. 
```
root@htpc:/var/log# sensors
lm85-i2c-0-2e
Adapter: SMBus I801 adapter at f000
in0:         +0.00 V  (min =  +0.00 V, max =  +3.32 V)   
Vcore:       +0.00 V  (min =  +0.00 V, max =  +2.99 V)   
+3.3V:       +0.00 V  (min =  +0.00 V, max =  +4.38 V)   
+5V:         +0.00 V  (min =  +0.00 V, max =  +6.64 V)   
+12V:        +0.00 V  (min =  +0.00 V, max = +15.94 V)   
fan1:          0 RPM  (min =    0 RPM)  ALARM
fan2:          0 RPM  (min =    0 RPM)  ALARM
fan3:          0 RPM  (min =    0 RPM)  ALARM
fan4:          0 RPM  (min =    0 RPM)  ALARM
temp1:        +0.0°C  (low  = -127.0°C, high = +127.0°C)  
M/B Temp:     +0.0°C  (low  = -127.0°C, high = +127.0°C)  
temp3:        +0.0°C  (low  = -127.0°C, high = +127.0°C)  
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +38.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38.0°C  (high = +76.0°C, crit = +100.0°C)  

root@htpc:/var/log# 
```

Does not work at the moment... even with 
sensors version 3.1.0 with libsensors version 3.1.0

2. Is there a way to tell GPU temperature on this board ?

Any comments appreciated.... 
Ghat

---

### Post by ghat on 2009-03-21
hi

One more reason [SIZE=5]**not**[/SIZE] to buy this board...

[https://bugs.freedesktop.org/show_bug.cgi?id=14611](https://bugs.freedesktop.org/show_bug.cgi?id=14611)

Ghat

---

### Post by comcute on 2009-04-22
Video tearing problem should be fixed now. [http://lists.freedesktop.org/archives/intel-gfx/2009-February/001516.html](http://lists.freedesktop.org/archives/intel-gfx/2009-February/001516.html)
I haven't tested this yet.

It works (no more tearing), I tested with xf86-video-intel-2.7.0

---

### Post by klato on 2009-04-24
You should check out the thread for this motherboard over at the avsforums...they have a huge thread going on:

[http://www.avsforum.com/avs-vb/showthread.php?t=1050640](http://www.avsforum.com/avs-vb/showthread.php?t=1050640)

---

### Post by ghat on 2009-06-10
One more problem with the motherboard...

note: in the code below "htpc" has the dg45fc motherboard

I have configured a static IP address on htpc which is 172.16.59.14 however I see that it also takes one of the dhcp addresses from my router... (.75)

```

desktop:~> ping 172.16.59.75
PING 172.16.59.75 (172.16.59.75) 56(84) bytes of data.
64 bytes from 172.16.59.75: icmp_seq=1 ttl=255 time=4.67 ms
64 bytes from 172.16.59.75: icmp_seq=2 ttl=255 time=1.10 ms
64 bytes from 172.16.59.75: icmp_seq=3 ttl=255 time=1.12 ms
^C
--- 172.16.59.75 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.101/2.302/4.678/1.680 ms
desktop:~> arp -a
gateway (172.16.59.1) at 00:23:69:41:ce:34 [ether] on eth0
htpc (172.16.59.14) at 00:1c:c0:70:f2:88 [ether] on eth0
? (172.16.59.75) at 00:1c:c0:70:f2:88 [ether] on eth0
desktop:~> ping 172.16.59.14
PING 172.16.59.14 (172.16.59.14) 56(84) bytes of data.
64 bytes from 172.16.59.14: icmp_seq=1 ttl=64 time=0.180 ms
64 bytes from 172.16.59.14: icmp_seq=2 ttl=64 time=0.421 ms
^C
--- 172.16.59.14 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.180/0.300/0.421/0.121 ms
desktop:~> arp -a
gateway (172.16.59.1) at 00:23:69:41:ce:34 [ether] on eth0
htpc (172.16.59.14) at 00:1c:c0:70:f2:88 [ether] on eth0
? (172.16.59.75) at 00:1c:c0:70:f2:88 [ether] on eth0
desktop:~> 

```Note here that one mac address is associated with 2 IP addresses...


This is my /etc/network/interfaces file... 
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 172.16.59.14
        netmask 255.255.255.0
        network 172.16.59.0
        broadcast 172.16.59.255
        gateway 172.16.59.1

```any hints on why this may be happening ?

also...
```

root@htpc:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:70:f2:88  
          inet addr:172.16.59.14  Bcast:172.16.59.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe70:f288/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66239730 (66.2 MB)  TX bytes:1734602 (1.7 MB)
          Memory:d0500000-d0520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2772653 (2.7 MB)  TX bytes:2772653 (2.7 MB)

pan0      Link encap:Ethernet  HWaddr 32:b2:5a:9d:48:59  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
and
```

root@htpc:~# ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:1c:c0:70:f2:88 brd ff:ff:ff:ff:ff:ff
    inet 172.16.59.14/24 brd 172.16.59.255 scope global eth0
    inet6 fe80::21c:c0ff:fe70:f288/64 scope link 
       valid_lft forever preferred_lft forever
3: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether 32:b2:5a:9d:48:59 brd ff:ff:ff:ff:ff:ff

```Ghat

---

### Post by notanatheist on 2009-06-21
> **comcute said:**
> I am using it with mythbuntu. Everything works pretty OK, including sound over HDMI. It has this infamous video tearing problem and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275351](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275351).

Wait! What?! You said your audio over HDMI is working? How!?! Please share.

---

### Post by comcute on 2009-07-08
IIRC HDMI support was added in alsa v1.0.18a, also you need later intel drivers (2.6.0/2.7.0). Then try with command aplay -l and aplay -L. If you see HDMI output, it is working.

> **notanatheist said:**
> Wait! What?! You said your audio over HDMI is working? How!?! Please share.

---

### Post by ghat on 2010-08-04
hi

anyone flashed with the recent bios update ?

G

---

