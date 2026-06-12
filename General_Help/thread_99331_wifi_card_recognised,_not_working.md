---
title: "wifi card recognised, not working"
date: 2005-12-05
forum: General Help
---

### Post by sean12345 on 2005-12-05
Hi all,
  I recently installed breezy on a thinkpad t22.  I have everything working except for my wireless network card which is a belkin f5d6020.

I ran ndiswrapper and got breezy to recognise the card.  I can even see the card with the networking program under system>>administration>>networking.  I selected my network, entered my wep key, and said use DHCP for an ip address.  The network icon in the upper right hand corner of the screen says I have full signal.

YET  it _will not connect to the internet or ping my router_.  I know i must be missing some thing small...

here is the output for ifconfig if you want it

eth0      Link encap:Ethernet  HWaddr 00:01:03:84:FA:E5
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe84:fae5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2631 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:5158538 (4.9 MiB)  TX bytes:277824 (271.3 KiB)
          Interrupt:11 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:880521 (859.8 KiB)  TX bytes:880521 (859.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:30:BD:4C:F9:0A
          inet6 addr: fe80::230:bdff:fe4c:f90a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:10400000-10400024

Thanks for any help

---

### Post by aclaunch on 2005-12-05
Sounds like the route is not set up. Did you enter the IP of your gateway in the networking dialog box? If yes and it's still not working, try "sudo route add default gw XXX.XXX.XXX.XX (your gateway address)".

Good Luck
Alan

---

### Post by newuser111 on 2005-12-05
try installing the restricted modules package matching your kernel version with synaptic, it has wifi support

also does your ISP require you register your MAC address?  If you are using a router, the router settings may let you spoof a mac address

---

### Post by sean12345 on 2005-12-05
ok..  

I just looked at synaptic, and I have the restricted modules installed.  Im downloadinng the 686 kernal and its restricted modules at the moment to see if  that offers any improvement.

I tried adding the route but got this error
becca@Beccascomp:~$ sudo route add default gw 192.168.1.1
Password:
SIOCADDRT: File exists

How do I install a kernal above 2.6.12?  kernal 2.6.14 is supposed to work better on a T22 thinkpad becuase it doesnt need acpi=off  passed at boot time.  And its might solve my wireless issues

---

### Post by newuser111 on 2005-12-05
[QUOTE=sean12345]ok..  

I just looked at synaptic, and I have the restricted modules installed.  Im downloadinng the 686 kernal and its restricted modules at the moment to see if  that offers any improvement.

I tried adding the route but got this error
becca@Beccascomp:~$ sudo route add default gw 192.168.1.1
Password:
SIOCADDRT: File exists

How do I install a kernal above 2.6.12?  kernal 2.6.14 is supposed to work better on a T22 thinkpad becuase it doesnt need acpi=off  passed at boot time.  And its might solve my wireless issues[/QUOTE]

2.6.14 installation guide
[http://ubuntuforums.org/showthread.php?t=84174&highlight](http://ubuntuforums.org/showthread.php?t=84174&highlight)

---

### Post by weirdo on 2005-12-05
Did you check if the card is the default ? When you go in the network settings at the bottom there is a drop down menu and you should set it to wlan0

Nic

---

### Post by aaronc222 on 2005-12-05
[QUOTE=sean12345]How do I install a kernal above 2.6.12?  kernal 2.6.14 is supposed to work better on a T22 thinkpad becuase it doesnt need acpi=off  passed at boot time.  And its might solve my wireless issues[/QUOTE]

Wierd, I need acpi=off and pnpbios=off to run 2.6.14.2 on my Toshiba 4025(older than dirt) laptop.

---

### Post by sean12345 on 2005-12-05
I made the card the default and I also tried deactivating eth0 so that only wlan0 was active.  It didnt help.  Another thing I have noticed is that the green led on my card never blinks or turns on.

As for the kernal 2.6.14, I read that here

[http://thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized](http://thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized)

Your toshiba wasnt listed as fixed so it would still need the acpi=off command

I synaptic'd the 686 kernal for 2.6.12 this morning, but it didnt do anything
I will get the 2.6.14 kernal when I get home tonight and report back.

Thanks

---

### Post by shimshun on 2005-12-06
I am having the same sort of issue with a wg311v2 card and a netgear fw114 router; recognised card but not working at all (except that the light at the back does come on but never blinks)
I know the router works becuase another machine runing windows sees it both as a wirless on channell 11 and as an ethernet router too
But it simply cannot get an ip address. Have you got a WEP key set or is the router running in opne mode?
What is the 'iwconfig' output?
Also what is the 'iwlist scan' output?

---

### Post by sean12345 on 2005-12-06
Hi all,

Ok.  I compiled and installed the new kernal 2.6.14 last night.  It didn't help my wifi problem.

My router is a linksys wrt54g and it is spoofing the mac address of my windows computer.

I know my router is working, becuase my windows wifi box picks it up fine via dhcp and my ubuntu box works over ethernet via dhcp as well.

I have the router wifi broadcasting in mixed B/G mode, and I have the correct wep key.

I installed gtkwifi as well to see if it might work getting my connection up.  It didnt, but it did give me an error message that might help figure things out.
It says "DHCP failed"  I tried connecting to my network, and two of my neighbors open networks--for testing purpuses only--, same error.  SOO I tried setting up a static ip for my computer
-went into router, created static ip 192.168.1.102

-on the networking panel 
static IP    192.168.1.101,
subnet       255.255.255.0,
gateway    192.168.1.1

It didnt work! - I don't think this is a  problem that can be solved by just setting up a static ip, so im going to try messing with ndiswrapper and combinations of the realtek and belkin drivers when I get home tonight.  I will also post the iwconfig and iwlist 

Thanks for all your help

p.s.  since I have the card recognised, this is more of a netwoking problem now -I think- so if you think i should create a new thread under networking let me know.

---

### Post by stevea1210 on 2005-12-06
I noticed that you don't have an address from DHCP.  It wasn't asked what security you have setup on the router.  Do you:

have wep or wpa
mac filtering
ssid broadcast off

Misconfiguring the first two will prevent you from getting an address from dhcp, but still could show you connected to the network.  I have only seen problems with not broadcsting ssid on certain bridges/game adapters.

Please post /etc/network/interfaces.

---

### Post by sean12345 on 2005-12-06
Hi all,

Ok first stevea1210
-I have WEP
-Mac filtering is OFF
-SSID broadcast - enabled

here is the contents of /ect/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Wireless Network 3
wireless-key s:4b6e8e5d1189c583e0ae0dec26

Now for shimshun
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Auto  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Power Management:off
          Link Quality:100/100  Signal level:-69 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:42:A6:E3
                    ESSID:"Wireless Network 3"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-50 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0F:3D:5C:38:DE
                    ESSID:"295digs"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-49 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:09:5B:71:64:68
                    ESSID:"burnham"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-57 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:0D:72:BC:F7:F9
                    ESSID:"LookAtThe45PrettyColors!"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-50 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.

Im at a loss for what to do to get the wireless to obtain an ip address! my ethernet works fine im writing this at home!

---

### Post by paradoxium on 2005-12-06
I can only connect to my router while user shared wep keys.  I didn't notice if you said whether you're using shared wep or open.  If you're using Open, try changing to shared.

---

### Post by ahave2005 on 2005-12-06
I have no idea if this will work, but i've noticed that your LED isn't on.
Have a look at: [http://www.ubuntuforums.org/showthread.php?p=550172#post550172](http://www.ubuntuforums.org/showthread.php?p=550172#post550172)
From: *I found the cardnumber with: * where lstinds is different from your windows driver.
and to: *(at this point the lights came on)*

/ahave

---

### Post by sean12345 on 2005-12-06
Hi all, I finially got it working!

1st, I went to belkin and got their most recent drivers, problem is that they are in a windows exe self installer.  SO I installed it on my windows box (they are usefull sometimes), found the drivers and put them on my ubuntu box.

2nd, I switched my wep key from asci to hexadecimal - yup I had the wrong type of key selected!!!!!  For some reason ubuntu froze when it was enabling wlan0 after that but I restarted (via the power button) and enabled it and wala, no wires!

Now i just need to figure out how to get linux to boot without syncing to ubuntu.org for the time, when there isnt a network to do this with it stalls the boot process by a few minutes.



Thanks for all the help!

---

### Post by stevea1210 on 2005-12-07
/etc/default/ntpdate is the file where that is configured.
```
sudo gedit /etc/default/ntpdate
```

When the file opens, put a # in front of ntp.ubuntulinux.org (think that is the name, posting from work on xp), and any other server listed in there.
Save the file, and when you rebot it shouldn't sync with any server.


Another alternitive is if you hit CTRL -c while it is hanging, it will move on to the next step, so you don't have to wait forever for it to fail

---

### Post by sean12345 on 2005-12-07
I stopped it from trying to sync the time.  Thanks for everyones help

---

### Post by The Chef on 2005-12-08
Might try deactivating _and_ disabling the ethernet interface using Network Settings app.  Then just to show it you really mean business 'down' the interface with **sudo ifconfig eth0 down**, so it does not appear on an a ifconfig listing.  The wlan0 wireless interface may then pick up a DHCP address etc which it does not appear to be doing now.  If not, next try configuring wlan0 using the "Properties" button in the Network Settings app (change at least one setting - like retyping the ESSID or something, otherwise the app doesn't seem to query the interface at all).  wlan0 might find religion then.

This sort of strategy has worked for me before.  Good luck!

---

### Post by theidealist on 2005-12-14
Okay, I'm dying here.  I've got a similar problem as you, sean - and I think I'm more of a newbie too, so here goes, maybe someone can help me:

First off, I've got a HP Compaq nx9600 laptop running Ubuntu Breezy with a pain-in-the-@$$ broadcom wireless NIC card.

When I use my laptop at work (Broadcasted SSID with Shared WEP key) it works terrific, no problems.  I lease an IP, my DNS works that lovely miracle of turning [www.google.com](www.google.com) into numbers, and, best of all, when I set wlan0 to be the default gateway, it ACTUALLY DOES IT.

The problem happens when I try to connect at home.  At home, I've got an insecure wireless network with no WEP.  The only thing I do is I don't broadcast the SSID.  When I bring my laptop home, I use the Network configuration applet to "switch profiles".  My work profile works correctly, and my Home profile seems to work correctly (no errors given), but I've noticed that, for some reason the little box in the Network configuration applet will NOT keep my selection of wlan0 as the default gateway.  I can select it, but if I hit "OK" and then open the Network Configuration applet again, it has "eth0" as the default gateway, or if I've disabled eth0, it's got nothing.

Retreating to the command line, I do a ifconfig with all adapters "up".  Everything looks okay.  In my windows mind, I'll do a up/down and "restart" the wlan0 adapter, right?  Right.

sudo -s
ifdown wlan0
<no errors>
ifup wlan0
<leases IP, but then emits a STOICADDRT error that says the network is unreachable>
ifconfig
<wlan0 has a legitimate ip>

At this point I have a legitimate IP address from my wireless router.  When I ping other boxes on my network they respond, and I can see the little blue light signaling wireless network activity.  I can see with netstat -nr that all the traffic is being sent through wlan0.  I can see in /etc/resolv.conf that the nameserver is correct and I can ping that nameserver.  I disable all firewall and anything else that might hinder me that I can think of, but I can't do any dns for the life of me.  [www.google.com](www.google.com) will forever mean nothing to it.

Has anyone had this problem?
Successfully leases an IP address and then, aftewards, after verification that the DHCP exchange was successful, is completely incapable of doing a simple nslookup request?

I also can't access things directly by their ip either, which is strange.  Say for example I want to access my gateway/router at 192.168.2.1 via http (it has a web-interface) - it refuses the connection!

Any help would be most appreciated - should I issue a bug report on the "failure to save default gateway selection" error in the Network Configuration Applet?

Thanks,

-Patrick

---

