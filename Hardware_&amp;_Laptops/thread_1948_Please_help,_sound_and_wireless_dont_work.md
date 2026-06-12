---
title: "Please help, sound and wireless dont work"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by brschmid on 2004-10-24
i have messed with linux in the past, but i usually gave up because i got frustrated, i like this one and i really want to make this work. but i am still quite n00bish.

-Wireless card is an Intel 2100. I think Ubuntu is recognizing it though because i can see that the correct DNS servers are entered and i didn't enter them. 
but it won't activate and when i try, it just immediately disables itself. 

i tried to rebuild the driver (which i have never done before) according to these instructions, but all i get is errors. [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/)

- Sound is SigmaTel C-Major. i have no idea what to do for this either, since it doesn't work. 

any help is greatly appreciated, thanks :)

---

### Post by sfw5000 on 2004-10-24
Hi,

What do you get  when you do iwconfig? Should look something like this:

sam@ernie / $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"YOUR ESSID NAME"
          Mode:Managed  Frequency:2.437GHz  Access Point: 00:0F:3D:06:FD:91
          Bit Rate:24Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=23/94  Signal level=-72 dBm  Noise level=-95 dBm
          Rx invalid nwid:584061  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:3   Missed beacon:3

sit0      no wireless extensions.
--
You might need to manually enter the ESSID and IP address -- post the results of iwconfig to start.

---

### Post by brschmid on 2004-10-24
results of iwconfig


> 
lo          no wireless extensions
eth1      no wireless extension
sit0       no wireless extensions.


also when booting up, i get 3 FATAL errors while inserting these 3 things, "pciehp" "shcphp" "hw_random"
i don't know what that means either

---

### Post by sfw5000 on 2004-10-24
OK,

So your card is not active right now, but hopefully it can still be detected. Have you tried adding the card in the GUI wizard? Computer --> System Config --> Networking. Click the ADD+ button and it will walk you through the set-up process. If you are lucky, it will detect your card automatically in this process, and then activate it. 

Can you also post the result of ifconfig -- this should at least show if your card is being detected. You might also try lspci to see if your card shows up in there.

> 
(from lspci)
0000:01:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)


> 
sam@ernie /etc/apt $ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0D:88:C9:D7:F3
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fec9:d7f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47490 errors:15170 dropped:0 overruns:0 frame:15170
          TX packets:26422 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:25654864 (24.4 MiB)  TX bytes:4818291 (4.5 MiB)
          Interrupt:201 Memory:deb72000-deb82000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:696915 errors:0 dropped:0 overruns:0 frame:0
          TX packets:696915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:52890281 (50.4 MiB)  TX bytes:52890281 (50.4 MiB)



---

### Post by brschmid on 2004-10-24
[QUOTE=sfw5000]OK,

So your card is not active right now, but hopefully it can still be detected. Have you tried adding the card in the GUI wizard? Computer --> System Config --> Networking. Click the ADD+ button and it will walk you through the set-up process. If you are lucky, it will detect your card automatically in this process, and then activate it. 

Can you also post the result of ifconfig -- this should at least show if your card is being detected. You might also try lspci to see if your card shows up in there.[/QUOTE]
 results from ifconfig:
> eth1      Link encap:Ethernet  HWaddr 00:0F:1F:9E:8D:7B
          inet addr:192.168.1.4  Bcast:192.168.1.7  Mask:255.255.255.248
          inet6 addr: fe80::20f:1fff:fe9e:8d7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4029 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2391671 (2.2 MiB)  TX bytes:592604 (578.7 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5045741 (4.8 MiB)  TX bytes:5045741 (4.8 MiB)


lspci :
> 
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB (ICH4) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB (ICH4) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB (ICH4) USB UHCI #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB (ICH4) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BAM/CAM PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB (ICH4) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB (ICH4) AC'97 Modem Controller (rev 01)
0000:01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
0000:01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
0000:01:03.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
0000:01:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 81)


i can't add it thru the GUI method, i already tried that, it doesn't detect it.

---

### Post by sfw5000 on 2004-10-25
OK... is eth1 the wireless card (have you disabled eth0, which would be the wired card?)

I assume you were following these directions: [http://ipw2100.sourceforge.net/INSTALL](http://ipw2100.sourceforge.net/INSTALL)

Did you set up the firmware? I haven't taken a close look at the Ubuntu kernel config yet, so it might be possible that you need to enable some options in there -- but hopefully not.

Have you tried ```
% modprobe ipw2100
% ifup eth1
```. What happens when you do that? You mentioned in your inital post that you got some errors, what are those errors?

---

### Post by brschmid on 2004-10-25
[QUOTE=sfw5000]OK... is eth1 the wireless card (have you disabled eth0, which would be the wired card?)

I assume you were following these directions: [http://ipw2100.sourceforge.net/INSTALL](http://ipw2100.sourceforge.net/INSTALL)

Did you set up the firmware? I haven't taken a close look at the Ubuntu kernel config yet, so it might be possible that you need to enable some options in there -- but hopefully not.

Have you tried ```
% modprobe ipw2100
% ifup eth1
```. What happens when you do that? You mentioned in your inital post that you got some errors, what are those errors?[/QUOTE]
 eth1 is my wired card, because i selected wireless as primary when i set up Ubuntu. I have deleted eth0 from the GUI networking screen. 

Yes i was following sf's instructions, i will post the errors in a few hours, i have to go to class now. 

modprobe ipw2100 didn't do anything last time i tried it,  i will try ifup when i get home as well. 

errors? i will start over again, but i got unpacking errors, then when i tried to make the driver i got errors. the Linux kernal isn't under usr/src like the instructions call for and i don't know where it is :(

---

### Post by ronin69hof on 2004-10-25
try adding:

acpi=noirq

to your kernel line in: /boot/grub/menu.lst

then reboot.  worked for me for sound and wireless.

---

### Post by sfw5000 on 2004-10-25
I'm also guessing that when you tried to compile the driver it didn't work because your lacking gcc and other compile tools. Not having this card, though, I'm not exactly sure what  might be going on -- hope what worked for ronin69hof works for you, and of course post back.

---

### Post by brschmid on 2004-10-25
[QUOTE=ronin69hof]try adding:

acpi=noirq

to your kernel line in: /boot/grub/menu.lst

then reboot.  worked for me for sound and wireless.[/QUOTE]
 i will try that ad report back

---

### Post by brschmid on 2004-10-25
i have sound now and wireless

what did adding that line do exactly?

---

