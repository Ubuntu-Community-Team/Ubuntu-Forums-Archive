---
title: "How to know if someone is stealing my wireless connection ?"
date: 2008-07-24
forum: General Help
---

### Post by deformation on 2008-07-24
Hello 

I am getting suspicious, my Internet becoming very slow sometimes, i feel someone is stealing my connection, i change the WEP key frequently, the connection goes normal for 1 or two days after that it returns to be slow. I am afraid that some sniffing/ wep key cracking is involved, can someone advice me how to detect such activity?

I am on an xubuntu 8.04 system. using enocre router, 802.11g.


Thanks in advance

---

### Post by Potatoj316 on 2008-07-24
You could use WPA, its harder to crack.  I dont know about your router but mine lets you see who is connected to it.  All I have to do is login to the router, [http://192.168.1.1](http://192.168.1.1) and enter my name/password (probably admin-password) and check to see who is connected.

---

### Post by DGortze380 on 2008-07-24
If you have a decent router you should be able to log in and look at the logs to view your DHCP leases and the MAC addressed associated with them.

---

### Post by Potatoj316 on 2008-07-24
I cant believe I forgot about this, MAC address filtering.  Allow only your own MAC address, and those of the computers who should be accessing your network.  You could also turn of SSID broadcast and change the SSID to some obscure name (these last 2 wont stop someone who is already cracking your WEP though)

---

### Post by WRDN on 2008-07-24
On most routers, you can view the attached devices. For example, I have to look under "Attached Devices" on my Netgear DG834G wireless router. It is also [usually] possible to limit the IP ranges that can connect to the router, so you can set a rule to only allow certain computers to connect, while rejecting others.

---

### Post by timcredible on 2008-07-24
well, does the data transfer light flash when you're not connected?  that's probably the easiest way to know if someone else is using your connection.  if they are, and you don't want them to, mac filtering is the next easiest thing to try.

---

### Post by Kevbert on 2008-07-24
If you're user name and password are admin and password you should change these for security reasons as anyone who can see your router can change any of the settings.  Also you should be able to restrict who uses the router by restricting MAC codes.  This isn't 100% secure but is a start.  To do this you should only see one MAC address displayed in the connected PCs list (which will be your PC).  If you change the wireless card or require other PCs to connect to the router you'll need to add their MAC codes.  The MAC code will look something like 00:11:22:33:40:59 and this it what you need to put in this list.  Then set the restriction to ON (normally a tick box) and then you'll stop any casual use by others of your wireless connection.
Other reasons for speed reductions are number of users on the website that you're looking at especially at peak times, traffic on the phone connection (to which the router is connected, regardless of whether it's copper wire or cable) and interference of the wireless by other networks in close proximity or other devices using the 2.4GHz band (such as cordless phones and microwave ovens).

---

### Post by estyles on 2008-07-24
If someone is cracking your WEP, MAC filtering isn't going to stop them - though it might slow them down.  From what I gather, it's a lot easier to sniff a MAC Address, which is broadcast by the wireless card, than it is to crack WEP, although supposedly WEP is easy to crack as well.  Unless your router is really old, it should support WPA, and if it doesn't, there might be a firmware upgrade that you can download.  I know I was able to dl a firmware upgrade for my older Linksys router that enables WPA.

---

### Post by Taxman415a on 2008-07-24
Same here. When you go in to change the WEP key, try looking through all the options the configuration tool gives you. You should be able to see one for all the MAC addresses or IP addresses that have connected to the router and/or have active connections. Then compare that to your MAC address and you should be able to tell who shouldn't be there. 

Then either use MAC address filtering (not perfect since they can clone your MAC address, but it's a start) or upgrade to WPA if you can.

The other thing you can do is install something like airsnort (use apt-get or whatever to install it) and capture packets. But then you'd really have to learn about how to analyze them to know what packets represented someone on your network that shouldn't be. That's not a bad thing to be able to do, but beyond what most want to learn. Since it captures all packets in the air whether they are on your network or not, I suppose it could also be considered illegal in your country, I don't know the laws.

---

### Post by sp0nge on 2008-07-24
I prefer wireshark to keep an eye on the network traffic..

---

### Post by deformation on 2008-07-25
Thanks for all the replies, I agree with what all of you advised, from what i get, the best thing is to make a WPA password, i can see the option in the router settings at 192.168.1.1, but when i do chose it and put a password, ubuntu cant connect to the Internet, i assume the problem that my wireless card cant read WPA? i am on an 3 years old acer travelmate with a 2200BG(802.11 b/g WLAN). if thats not the scenario, can someone advice me how to make a WPA encrypted WIFI correctly?

Thanks to all of you, your replies are much appreciated.

---

### Post by jimv on 2008-07-25
> **deformation said:**
> Thanks for all the replies, I agree with what all of you advised, from what i get, the best thing is to make a WPA password, i can see the option in the router settings at 192.168.1.1, but when i do chose it and put a password, ubuntu cant connect to the Internet, i assume the problem that my wireless card cant read WPA? i am on an 3 years old acer travelmate with a 2200BG(802.11 b/g WLAN). if thats not the scenario, can someone advice me how to make a WPA encrypted WIFI correctly?

Thanks to all of you, your replies are much appreciated.

Make sure that you have WPA Supplicant installed.  Here's the terminal command to install it:

sudo apt-get install wpasupplicant

---

### Post by Taxman415a on 2008-07-25
Can you give us the output of lspci on the command line?
Or better yet, can you look for the product manual for your laptop or wireless card to see if it supports WPA?

---

### Post by Krupski on 2008-07-25
> **deformation said:**
> Hello 

I am getting suspicious, my Internet becoming very slow sometimes, i feel someone is stealing my connection, i change the WEP key frequently, the connection goes normal for 1 or two days after that it returns to be slow. I am afraid that some sniffing/ wep key cracking is involved, can someone advice me how to detect such activity?

I am on an xubuntu 8.04 system. using encore router, 802.11g.


Thanks in advance

Setup an access restriction which only allows your MAC ADDRESS (and any other legit users in your home - their MAC addressee too) to connect to the router.

Still use WEP or WPA or whatever you like, but ALSO add MAC address authorization.

Since no two network devices have the same MAC address (unless they're spoofed), you will lock out everyone but those you want to allow.

-- Roger

---

### Post by deformation on 2008-07-25
> **Taxman415a said:**
> Can you give us the output of lspci on the command line?
Or better yet, can you look for the product manual for your laptop or wireless card to see if it supports WPA?

Dont have the manual, but i got the lspci output :

> deformation@deformation-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)


Thanks in advance.

---

### Post by kerry_s on 2008-07-25
if someones on your line it shouldn't effect the speed. my guess it's your isp, there either throttling you during peak hours or you simply have slow dns look up.
routers can support multiple connections at once, i have 8 on mine.

first try the dns, hop over to open dns->
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

also, the # of wireless around you can affect your signal, i don't know how detailed ubuntu's wireless detection is, but you want to make sure your on a different channel then everyone else, for instance around me, there using 4, 6, and 11, so i'm using 8.

start from the basics and work your way down, to try and locate the problem spot.
also, if you can disable the name broadcasting, just input it manually.

---

### Post by deformation on 2008-07-25
> **kerry_s said:**
> if someones on your line it shouldn't effect the speed. my guess it's your isp, there either throttling you during peak hours or you simply have slow dns look up.
routers can support multiple connections at once, i have 8 on mine.

first try the dns, hop over to open dns->
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

also, the # of wireless around you can affect your signal, i don't know how detailed ubuntu's wireless detection is, but you want to make sure your on a different channel then everyone else, for instance around me, there using 4, 6, and 11, so i'm using 8.

start from the basics and work your way down, to try and locate the problem spot.

Hello,

I am already running open DNS here, so its not a DNS problem, about the channel, i am on 6 , i don't know how many of my neighbors using 6 , but i can see that my eth1 signal is always 96% and above, does that rule out the channel traffic thing or its not related?

About the ISP throttling my connection, i dont think thats the issue, because i get slow connection on non peak hours, (by slow i mean like 1 or 0,5 KB/s, and i am on a 1mb dsl line) plus,

my connection is like the following, dsl lan modem connected to a wireless router connected to a single laptop. i think the problem is ubuntu settings related, because connections is fine under windows on the same laptop.

I am really getting out of hope here:confused:

---

### Post by kerry_s on 2008-07-25
> **deformation said:**
> Hello,

I am already running open DNS here, so its not a DNS problem, about the channel, i am on 6 , i don't know how many of my neighbors using 6 , but i can see that my eth1 signal is always 96% and above, does that rule out the channel traffic thing or its not related?

About the ISP throttling my connection, i dont think thats the issue, because i get slow connection on non peak hours, (by slow i mean like 1 or 0,5 KB/s, and i am on a 1mb dsl line) plus,

my connection is like the following, dsl lan modem connected to a wireless router connected to a single laptop. i think the problem is ubuntu settings related, because connections is fine under windows on the same laptop.

I am really getting out of hope here:confused:

in that case i'm pretty sure your right, it's a ubuntu problem. :(

about the channel i would still change it different from every one else 4, 6, and 11 are common default numbers, so changing it will give you less interference, a cleaner connection.

---

### Post by Taxman415a on 2008-07-25
Ok from that command output I see it's an Intel 2200BG wireless, and a google search on that points to this link to get the specs:[http://support.intel.com/support/wireless/wlan/pro2200bg/](http://support.intel.com/support/wireless/wlan/pro2200bg/)
The tech specs links to a pdf that says it does WPA. 
As for getting it working, I didn't find any good up to date links. [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo) is old and mentions you should just be able to use the network manager to get WPA set up. Unfortunately I don't have a laptop handy to test with to show you how.

Your best bet may be to start a new post asking how to set up WPA. If you use a good subject, people will help you.

---

