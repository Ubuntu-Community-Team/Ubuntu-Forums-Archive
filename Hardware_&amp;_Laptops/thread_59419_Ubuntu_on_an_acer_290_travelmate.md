---
title: "Ubuntu on an acer 290 travelmate"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by John.Michael.Kane on 2005-08-23
Great os.. a few issues i cant seem to get I-net working or wireless. also im looking to find out if you can install this os on a drive, with no windows os at all meaning ubuntu is the main os. i think once i figure our how to get the net and other functions working. windows will go to waist side. if you need more info to offer me some help please post thanks..

---

### Post by s_p_a_r_k_y on 2005-08-23
You must have downloaded the "liveCD" which is meant to be used to run Linux from the CD. You want the install cd. Indeed though you may want to resolve the network and wireless problems before you get rid of the beast. Why don't you post the ouput of some of these commands

```

lspci
ifconfig
lsmod
dmesg

```
so we can see what devices you have and what kernel modules you may need.

---

### Post by John.Michael.Kane on 2005-08-24
These are two i downloaded and burned.. i will reinstall, and try to get the list you asked for.. 

2.8G  Install/live DVD for Intel x86 computers
Install CD for Intel x86 computers

---

### Post by John.Michael.Kane on 2005-08-24
Since this is my frist time with this i have idea how to get this list. still have no net access.. and at a total loss as to what to do. kinda of fed up with the os im using. dont really care for the other linux distos. guess i will have to go with out net access and figure this out..  so far ubuntu do not work right out of the box 

as for what is in my laptop 
Realtek RTL8139 Family PCI Fast Ethernet NIC
1394 Net Adapter via ochi 1394 host controller
Intel(R) PRO/Wireless LAN 2100 3B Mini PCI Adapter
Pcmcia ENE CB1410 card bus controller
Agere Systems AC'97modem
SMSC IrCC (Infrared Communications Controller)
RealTek AC'97audio
Intel Extream Graphics 

if these listed items are needed for anyone to helpme please explain how to get them thanks
lspci
ifconfig
lsmod
dmesg

---

### Post by s_p_a_r_k_y on 2005-08-24
do you see any devices in System->Administration->Networking?

---

### Post by John.Michael.Kane on 2005-08-24
If i run it i will not be able to post a responce so im not running the os. if i can run the live version and still tell you what you need  know i will do it that way ..

---

### Post by macgyver2 on 2005-08-24
I came over after I saw your other thread about the perceived lack of help for older systems...so let's see what's going on here..
[QUOTE=SD-Plissken]Realtek RTL8139 Family PCI Fast Ethernet NIC[/QUOTE]
Okay, I have the same thing in my notebook.  That's a good start. :)
[QUOTE=SD-Plissken]Intel(R) PRO/Wireless LAN 2100 3B Mini PCI Adapter[/QUOTE]
Now as for this...first, AFAIK wireless in Linux, in general, is still pretty shaky. Specifically, what you have still isn't very well supported. I tried getting the same thing working in my girlfriend's Dell-something under Mandrake. I wound up having to use ndiswrapper (that's a program that allows the actual windows drivers to run under Linux) but she experienced intermittent connections and several system lock-ups. So basically, I don't know where else to go with this where I haven't been (and failed) before. If I find something I can let you know. In fact, I'm going to see her this weekend and I think I'll bring a Hoary CD and play around with it on her computer more.

But back to the wired network card...mine worked out-of-box. So the problem might be with Ubuntu seeing the card (which was were s_p_a_r_k_y is going with those commands he suggested). So if you could give us the output of those commands it would help. I think the first two you should do are [font=Courier New]ifconfig[/font] and [font=Courier New]lsmod[/font]. You don't even need to post everything from the latter. The driver that your ethernet card uses is called 8139too, so if you type
```
lsmod | grep 8139too
```
and it returns one or more lines then the system is seeing the card and loading the right module. If nothing is output then post the output of the other two commands ([font=Courier New]dmesg[/font] and lspci) that [font=Courier New]s_p_a_r_k_y[/font] said.

---

### Post by John.Michael.Kane on 2005-08-24
Can this be done using the livecd.. and thanks

---

### Post by macgyver2 on 2005-08-24
[QUOTE=SD-Plissken]Can this be done using the livecd.. and thanks[/QUOTE]
Yes...and no problem.

---

### Post by macgyver2 on 2005-08-24
SD-Plissken, it's almost time for me to go to bed, but I'm watching this thread and I'll come back to it tomorrow so we can work on this some more (if the problem isn't already solved by then!).

---

### Post by John.Michael.Kane on 2005-08-24
@s_p_a_r_k_y and macgyver2 


i think this is what you asked for.. also theres no sound.. 

8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
8139cp: pci dev 0000:01:01.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
ACPI: PCI interrupt 0000:01:01.0[A] -> GSI 10 (level, low) -> IRQ 10
eth0: RealTek RTL8139 at 0xc000, 00:02:3f:bb:59:cf, IRQ 10
eth0:  Identified 8139 chip type 'RTL-8101'
ieee80211_crypt: registered algorithm 'NULL'
ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.0.2
ipw2100: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
ACPI: PCI interrupt 0000:01:02.0[A] -> GSI 10 (level, low) -> IRQ 10
ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
inserting floppy driver for 2.6.10-5-386
floppy0: no floppy controllers found
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
NET: Registered protocol family 17
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
inserting floppy driver for 2.6.10-5-386
floppy0: no floppy controllers found
cloop: Initializing cloop v2.01
cloop: loaded (max 8 devices)
loop: loaded (max 8 devices)
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
cloop: losetup_file: 32753 blocks, 65536 bytes/block, largest block is 65562 bytes.
EXT2-fs warning: maximal mount count reached, running e2fsck is recommended
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
apm: BIOS not found.
Linux agpgart interface v0.100 (c) Dave Jones
eth0: no IPv6 routers present
lp0: using parport0 (interrupt-driven).


ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:02.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
0000:01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
ubuntu@ubuntu:~$


8139too                24320  0
8139cp                 19200  0
mii                     4736  2 8139too,8139cp


Hope this is what youwas asking for.

---

### Post by John.Michael.Kane on 2005-08-25
@s_p_a_r_k_y and macgyver2 hope thats the info you need to help me...

---

### Post by macgyver2 on 2005-08-25
Well, Ubuntu sees both network cards...loads the modules.  That's good.
[QUOTE=s_p_a_r_k_y]do you see any devices in System->Administration->Networking?[/QUOTE]
Do that...look there, and if you see an Ethernet connection check if it's active.  If not, try activating it.

Also, I may have been wrong about the wireless.  [This person]("http://www.botmanfamily.net/%7Eaurelien/articles/ubuntu_linux_on_Acer_TM290.htm#_Toc97568085") apparently didn't have to do anything to get the wireless working on a Travelmate 290.  So while you're in the Networking window, see if there's an entry for Wireless connection, too.  And for your wireless, do you use WEP, WPA, or no encryption?

---

### Post by John.Michael.Kane on 2005-08-25
I will have to find out how to enable these-->WEP, WPA

as for activating Ethernet connection i will see if this can be done . what if it will activate?? thanks

---

### Post by macgyver2 on 2005-08-25
[QUOTE=SD-Plissken]I will have to find out how to enable these-->WEP, WPA[/QUOTE]
So I guess that means your wireless network is currently unencrypted?
[QUOTE=SD-Plissken]as for activating Ethernet connection i will see if this can be done . what if it will activate?? thanks[/QUOTE]
If you can activate it then you should have a working network connection.  As for why it wouldn't be activated when you boot...it would have to be a network issue, not something with the computer itself.  Something's unplugged, network's not working or set up for dhcp or...

---

### Post by John.Michael.Kane on 2005-08-25
Eth1-->Wireless can be activated.
Eth0-->Wired networking can be activated 

Since my Internet is ppoe based i would have set up some way to enter pass and user name. it would seem theres now way to set that.. i might be missing something again....
 
as for wireless network is currently unencrypted i have never used it frist time i turn it on.. i'm sure theres guides for setting that up..

---

### Post by macgyver2 on 2005-08-25
[QUOTE=SD-Plissken]Eth1-->Wireless can be activated.
Eth0-->Wired networking can be activated 

Since my Internet is ppoe based i would have set up some way to enter pass and user name. it would seem theres now way to set that.. i might be missing something again....[/QUOTE]
I see!  My fault for prolonging the problem here...I didn't consider that you might be using pppoe.  I think
```
sudo pppoeconf
```
 will allow you to set up your account info.  I've never used it though so I don't know the details.

Edit:  I looked at a few other threads (searched for 'pppoe').  The above command is what should let you set up your account info.

---

### Post by s_p_a_r_k_y on 2005-08-25
I have never dealed with ppoe, always been a cable modem user. I suggest either reading up on setting up ppoe or getting a wireless router. Thus you can use wireless around the house/appt and have it always connected via the router. Sorry I can't help more. I do suggest the router, its like 60 bucks and you get wireless : ) mmmm wireless

---

### Post by John.Michael.Kane on 2005-08-25
ok  thanks

---

### Post by John.Michael.Kane on 2005-08-25
@s_p_a_r_k_y and macgyver2  I'm posting this from ubuntu live cd install. Thanks guys for the great help ... i know have more to learn. one more question does the os have a firewall program . i  have heard of some people who use linux with out any firewall program.. again thanks

---

### Post by s_p_a_r_k_y on 2005-08-25
yea it has IP tables, although being a newbie I don't think you will like dealing with it directly. There are many front ends which make using iptables fun. Although I don't use a firewall on my laptop, I do have a iptables configured on my servers to drop ping requests and block unnecessary ports (to be invisible) unless you knock on the right doors (http,ssh,ftp)

I'm not familiar with the front ends but here is a quick search

apt-cache search iptables
iptables - Linux kernel 2.4+ iptables administration tools
iptables-dev - development files for iptable's libipq and libiptc
shorewall - Shoreline Firewall (Shorewall)
acidlab - Analysis Console for Intrusion Databases
arptables - ARP table administration
ebtables - Ethernet bridge frame table administration
ferm - maintain and setup complicated firewall rules
fiaif - An easy to use, yet complex firewall
filtergen - packet filter generator for various firewall systems
fireflier-client-gtk - Interactive firewall rule creation tool - GTK client
fireflier-client-kde - Interactive firewall rule creation tool - QT client
fireflier-client-qt - Interactive firewall rule creation tool - QT client
fireflier-server - Interactive firewall rule creation tool - server
firehol - An easy to use but powerful iptables stateful firewall
fwanalog - firewall log-file report generator (using analog)
fwlogwatch - Firewall log analyzer
gnome-lokkit - basic interactive firewall configuration tool (GNOME interface)
guarddog - firewall configuration utility for KDE
guidedog - NAT/masquerading/port-forwarding configuration tool for KDE
ipac-ng - IP Accounting for iptables( kernel >=2.4)
ipmenu - A cursel iptables/iproute2 GUI
iptstate - Top-like state for netfilter/iptables
kernel-patch-ttl - TTL matching and setting
knetfilter - A GUI for configuring the 2.4 kernel IP Tables
lg-issue103 - Issue 103 of the Linux Gazette.
libiptables-ipv4-ipqueue-perl - Perl extension for libipq
lokkit - basic interactive firewall configuration tool (console interface)
netscript-2.4 - Linux 2.4.x (and 2.6.x) router/firewall network configuration system
netstat-nat - A tool that display NAT connections
p3scan - transparent POP3-proxy with virus- and spam-scanning
psad - The Port Scan Attack Detector
reaim - Enable AIM and MSN file transfer on Linux iptables based NAT
shorewall-doc - Shoreline Firewall (Shorewall) documentation
uif - Advanced iptables-firewall script
ulogd - The Netfilter Userspace Logging Daemon
webmin-firewall - iptables control module for webmin

so you can give a few of those a try

---

### Post by macgyver2 on 2005-08-25
[QUOTE=SD-Plissken]@s_p_a_r_k_y and macgyver2 I'm posting this from ubuntu live cd install. Thanks guys for the great help ... i know have more to learn. one more question does the os have a firewall program . i have heard of some people who use linux with out any firewall program.. again thanks[/QUOTE]
There are several. Shorewall is one, and firestarter. There are more I don't know about, I'm sure. One thing to do would be to open Synaptic (under System -> Administration) and use the search function to search for 'firewall'. Make sure you set the search field for 'Description and Name'.

Edit:  Whoops, didn't see s_p_a_r_k_y's reply when I wrote mine. :)

---

### Post by John.Michael.Kane on 2005-08-25
I will look into them. theres also a program called firestarter i see ubuntu comes with..
well i will have to do a format and do a hard intall. thanks again @s_p_a_r_k_y and macgyver2 hopefully i will not have any other issues...

---

### Post by John.Michael.Kane on 2005-08-25
Anonther question is it possable to have the ppoe set up to ask for the user name a pass for every session or is automatic remembered and all you have to do is just click  on the browser or mail program you want to use with out having to enter that info.. right now i'm reading some unoffical ubuntu guide.. dont know if you have read this..

---

### Post by macgyver2 on 2005-08-25
[QUOTE=SD-Plissken]Anonther question is it possable to have the ppoe set up to ask for the user name a pass for every session or is automatic remembered and all you have to do is just click on the browser or mail program you want to use with out having to enter that info.. right now i'm reading some unoffical ubuntu guide.. dont know if you have read this..[/QUOTE]
My *guess*--just a guess--is that there is a way to have it remembered permanently.  I know it's like that with normal PPP.  *However*, on a LiveCD, of course, everything you do is forgotten once you shutdown/reboot...so everytime you boot the LiveCD you're going to have to reconfigure pppoe.

---

### Post by John.Michael.Kane on 2005-08-25
Is there way to have it ask for the user name and pass all the time. after you do a hard install..

---

### Post by para on 2005-09-20
Hi 
I'm new in linux world,FYI.  And have looks like same problem on my TM 290.

All is working fine except modem "Agere",and for now looks like there is no support for that thing, or maybe .....

Now I will try with PCMCI modem card from 3com ..

If you manage to connect via Agere pls post the msg

just started with linux

---

### Post by ngakalden on 2008-05-14
My wife is traveling to Asia where she is going to need a Dial-up Connection. Her TM290 works well w/ Ubuntu however I can't get the modem driver installed. The only available download I found was for XP. Any advice in getting her computer setup would be appreciated.

-J

---

