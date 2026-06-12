---
title: "Wireless help"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by Gooks on 2005-12-24
Hi i dont realy know anything about linux all i need is just to get wireless and to go online and look at my emails.. The driver to my wireless download link is [http://support.gateway.com/support/drivers/getFile.asp?id=19881](http://support.gateway.com/support/drivers/getFile.asp?id=19881).. Can it be ported to linux? I know that this isn't the source code but can somebody try to get this on linux? Much apreachated.

By the way my english is not that good

---

### Post by Lambert on 2005-12-24
A driver for this chipset is being worked on for linux but it won't work in breezy at it needs a kernel 2.6.15 or greater. (there will be a beta version in dapper when it's released)

You need to use an app called ndiswrapper to get your wireless device working. It basically makes the windows drivers work in linux.

See link in my signature for ndiswrapper. And you may want to search in your native language for ndiswrapper instructions. Some of them may tell you to download and compile driver. Not needed as repositories have a version of ndiswrapper that shoule work.

---

### Post by Gooks on 2005-12-24
untouchable@bigbi:~$ sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_1386.deb
dpkg: error processing ndiswrapper-utils_1.1-4ubuntu2_1386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndiswrapper-utils_1.1-4ubuntu2_1386.deb
untouchable@bigbi:~$ sudo_dpkg -i ndisgtk_0.5-1ubuntu1_all.deb
bash: sudo_dpkg: command not found
untouchable@bigbi:~$ sudo dpkg -i ndisgtk_0.5-1ubuntu1_all.deb
dpkg: error processing ndisgtk_0.5-1ubuntu1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndisgtk_0.5-1ubuntu1_all.deb
untouchable@bigbi:~$

---

### Post by Rob2687 on 2005-12-24
Make sure you run the command in the same directory as the files.

---

### Post by Gooks on 2005-12-24
I put that in my home/untouchable dir

edit it works now the forums file name was wrong...


untouchable@bigbi:~/w$ $sudo apt-get install ndisrapper-utils
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
untouchable@bigbi:~/w$


Where can i get my driver at?

---

### Post by Gooks on 2005-12-24
bump

---

### Post by Lambert on 2005-12-24
try running this

```
sudo apt-get clean
```

then

```
sudo apt-get update
```

---

### Post by Gooks on 2005-12-24
Now i need to get my driver but i dont know how. GOD thanks you so much for helping me even tho i dont understand and for stupidity thank you for helping.... back to the questiong wher can i get my driver at?

---

### Post by Lambert on 2005-12-24
There are pages on the wiki about ndiswrapper. One of them is in my signature. It has instructions about finding the correct windows driver to use with ndiswrapper.

---

### Post by Gooks on 2005-12-24
Sorry to ask about my own computer what what is my chipset?

I am running a Gateway 7215GX Notebook
Serial Number: N454B11012472

---

### Post by Gooks on 2005-12-26
bump

---

### Post by Lambert on 2005-12-26
Run these commands and post the output here

lspci -v

then 

lspci -n

---

### Post by Gooks on 2005-12-26
Lol i am sorry for you going through this trouble i am thankful to be a linux user


Here is the output for lspci -v

```
0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Memory at d0400000 (32-bit, prefetchable) [size=4K]
        I/O ports at 8090 [disabled] [size=4]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff
        Secondary status: SERR

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
        Subsystem: ALi Corporation ALI M1533 Aladdin IV ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:08.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
        Subsystem: Rioworks: Unknown device 2036
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 8400 [size=256]
        Memory at d0008000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
        Subsystem: Rioworks: Unknown device 2033
        Flags: medium devsel, IRQ 5
        Memory at d0009000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 8800 [size=256]
        Capabilities: <available only to root>

0000:00:0a.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
        Subsystem: Rioworks: Unknown device 2036
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at ffbfe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 1: fbbfd000-ffbfc000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10 [OHCI])
        Subsystem: Rioworks: Unknown device 2036
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at d000c000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Unknown device 17f9:0002
        Flags: fast devsel, IRQ 10
        Memory at d0004000 (32-bit, non-prefetchable) [size=8K]

0000:00:0d.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Rioworks: Unknown device 2036
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d000a000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0d.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Rioworks: Unknown device 2036
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d000b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:0d.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
        Subsystem: Rioworks: Unknown device 2036
        Flags: bus master, medium devsel, latency 132, IRQ 11
        Memory at d000c800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:0e.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Rioworks: Unknown device 2029
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at d0006000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
        Subsystem: Rioworks: Unknown device 2036
        Flags: bus master, medium devsel, latency 0
        I/O ports at 8080 [size=16]
        Capabilities: <available only to root>

0000:00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: Rioworks: Unknown device 2036
        Flags: medium devsel

0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1 (prog-if 00 [VGA])
        Subsystem: Rioworks: Unknown device 2036
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>
```


and here is for lspci -n
```
untouchable@bigbi:~$ lspci -n
0000:00:00.0 0600: 1002:cab0 (rev 13)
0000:00:01.0 0604: 1002:700f (rev 01)
0000:00:07.0 0601: 10b9:1533
0000:00:08.0 0401: 10b9:5451 (rev 02)
0000:00:09.0 0703: 10b9:5457
0000:00:0a.0 0607: 104c:ac44 (rev 02)
0000:00:0a.1 0c00: 104c:8029
0000:00:0c.0 0280: 14e4:4320 (rev 03)
0000:00:0d.0 0c03: 1033:0035 (rev 43)
0000:00:0d.1 0c03: 1033:0035 (rev 43)
0000:00:0d.2 0c03: 1033:00e0 (rev 04)
0000:00:0e.0 0200: 14e4:4401 (rev 01)
0000:00:10.0 0101: 10b9:5229 (rev c4)
0000:00:11.0 0680: 10b9:710
```

---

### Post by Lambert on 2005-12-26
Ok here's what you do. (from a terminal)

The link to the gateway driver in your first post. Download that to your linux machine. Then move to the directory where you downloaded. (following assumes it was downloaded to a directory called downloads in your home folder)

cd ~/downloads

then run this command (double check I didn't make a typo in the file name)

unzip 9528158.exe (you can just type unzip 95 then hit tab and it should autocomplete for you assuming you have no other files in that folder begininng with 95)

This will put all the files from the .exe file into that drive

then copy these files over to a folder. I assume a file called drivers in your home folder

cp ~/downloads/bcmwl5.inf ~/drivers/
cp ~/downloads/bcmwl5.sys ~/drivers/

then move to the drivers folder

cd ~/drivers


Now walk through the wiki entry on ndiswrapper using the .inf file when you run the command sudo ndiswrapper -i xxxx.inf

if you can't get it working using this then do this

sudo modprobe -r ndiswrapper

sudo ndiswrapper -e bcmwl5.inf
(removes the driver)

go back into your drivers folder and delete the bcmwl5.inf file(do not delete the .sys file though, you need to keep that there.)

rm bcmwl5.inf

and now copy the bcmwl5a.inf file into the driver folder

cp ~/downloads/bcmwl5a.inf ~/drivers/

and go through the ndiswrapper installation instructions again this time using the bcmwl5a.inf driver.

One of these drivers should work. 

Don't worry about asking for more help. I (and others) learn from help as I don't have these situations happen so it's a learning experience for me.

---

### Post by Gooks on 2005-12-26
untouchable@bigbi:~/drivers$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
bcmwl5a invalid driver!

---

### Post by Lambert on 2005-12-26
You didn't try to put both .inf files in the folder and install both at the same time did you?

There should be only one .inf file and one .sys file in the folder. The only reason I mentioned both is some find success with one, some find success with the other.

---

### Post by Gooks on 2005-12-26
untouchable@bigbi:~/drivers$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
untouchable@bigbi:~/drivers$


Thank you so much... Now what?

---

### Post by Lambert on 2005-12-26
sudo modprobe ndiswrapper

go to system>administration>networking

your device should be in the list as wlan0. highlight it, click properties, enter your network information, click ok then try to activate.

if all goes well and it works then use this command so it loads at boot

sudo ndiswrapper -m

---

### Post by Gooks on 2005-12-26
Thank you so much....!!!!!! It works but it doesn't send any packets

---

### Post by Lambert on 2005-12-26
run these commands

iwconfig

iwconfig

for iwconfig what is after Access Point

for ifconfig do you have a section that says inet addr: with an ip address after it? (should be on second line under the wlan0 iface)

---

### Post by Gooks on 2005-12-26
It dont send any packets but i can still surf the web. I think that is ok right now just a bug or glitch.... And after i did the Howto: Firefox thing i cant use firefox no more. Keeps on crashing on me how can i fix that?

---

### Post by Lambert on 2005-12-26
If you're surfing the web in the browser then it's sending packets. Where are you getting it's not sending packets from?

As far as the howto for firefox which one? It's best to post there in the same thread so those who have used that howto or the author can help you. I don't use firefox. Or start a new thread.

---

### Post by Gooks on 2005-12-26
It doesn't show any packet send from the network monitor.. I deactivated eth0

---

### Post by Lambert on 2005-12-26
did you change the interface so it shows wlan0? eth0 is the default.

---

### Post by Gooks on 2005-12-26
No i didn't how would i do that?

---

### Post by Gooks on 2005-12-26
Now i dont think it realy works. I cant even go on the wbes no more it wont even load.

---

### Post by Gooks on 2005-12-27
NO PACKET SENDS!!!! On wireless
```
untouchable@bigbi:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```
```
untouchable@bigbi:~$ ping 192.168.1.109
PING 192.168.1.109 (192.168.1.109) 56(84) bytes of data.
From 192.168.1.110 icmp_seq=2 Destination Host Unreachable
From 192.168.1.110 icmp_seq=3 Destination Host Unreachable
From 192.168.1.110 icmp_seq=4 Destination Host Unreachable
From 192.168.1.110 icmp_seq=6 Destination Host Unreachable
From 192.168.1.110 icmp_seq=7 Destination Host Unreachable
From 192.168.1.110 icmp_seq=8 Destination Host Unreachable
From 192.168.1.110 icmp_seq=10 Destination Host Unreachable
From 192.168.1.110 icmp_seq=11 Destination Host Unreachable
From 192.168.1.110 icmp_seq=12 Destination Host Unreachable
From 192.168.1.110 icmp_seq=14 Destination Host Unreachable
From 192.168.1.110 icmp_seq=15 Destination Host Unreachable
From 192.168.1.110 icmp_seq=16 Destination Host Unreachable

--- 192.168.1.109 ping statistics ---
17 packets transmitted, 0 received, +12 errors, 100% packet loss, time 16001ms
, pipe 3
untouchable@bigbi:~$ ping 192.168.1.109
PING 192.168.1.109 (192.168.1.109) 56(84) bytes of data.
From 192.168.1.110 icmp_seq=2 Destination Host Unreachable
From 192.168.1.110 icmp_seq=3 Destination Host Unreachable
From 192.168.1.110 icmp_seq=4 Destination Host Unreachable
From 192.168.1.110 icmp_seq=6 Destination Host Unreachable
From 192.168.1.110 icmp_seq=7 Destination Host Unreachable
From 192.168.1.110 icmp_seq=8 Destination Host Unreachable

--- 192.168.1.109 ping statistics ---
11 packets transmitted, 0 received, +6 errors, 100% packet loss, time 10000ms
, pipe 3
```

```
wlan0     Link encap:Ethernet  HWaddr 00:90:4B:C0:D0:78
          inet6 addr: fe80::290:4bff:fec0:d078/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:d0004000-d0005fff
```

---

### Post by scflymedic on 2005-12-27
I have an emachines with the same broadcom wireless card and the only driver I was able to get to work was the one on the restore disc under the drivers folder.  I copied that to my linux desktop then used Arnieboy's "Automatix" that has a gui ndiswrapper included and was up and running in no time.  I hope this helps.  Sorry no step by step but the gui version is pretty self-explanatory.

---

### Post by Gooks on 2005-12-27
I am still lost

---

