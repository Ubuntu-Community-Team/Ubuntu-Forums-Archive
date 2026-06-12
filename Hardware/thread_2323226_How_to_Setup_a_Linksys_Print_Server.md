---
title: "How to: Setup a Linksys Print Server"
date: 2016-05-03
forum: Hardware
---

### Post by 777funk on 2016-05-03
[B]First of all... DISCLAIMER: there are no guarantees this will work for you. There is no warranty. I am not responsible for crashes, vulnerabilities, etc. etc. This is my experience and something that worked for me. I'm not recommending this as a solution to anyone else. Also if anyone does find something here that is an issue or vulnerability, please do note it for myself and others to take notice of. 
[/B]
This took me a good part of the day AND Linksys tech support wasn't much help. That said, I figured I'd post a simple how to just in case it helps someone else.

Objective: 
Samba reliability has been so-so on my install. I NEED to be able to print and can't depend on reaching the sometimes unreachable Win7 computer on our network which hosts our printers. I decided to use a LinkSys EPSX3 (triple parallel port host) Print Server to host my old faithful HP LaserJet 6P laser printer (should work with almost any printer connected to the LinkSys Print Server) over my home network. This is great because now we don't have to have the host computer powered on in order to print over the network. Basically, this is an Ethernet in and 3x parallel ports out. These also come in Ethernet to USB versions. It's a network host for your old non network equipped printers. This is a great solution to bring old (late 90's in my case) equipment up to date. 

Background:
Chatted with LinkSys tech support who didn't help much. They couldn't inform on how to find to the LinkSys device's IP address nor a way to set it. They did refer me to a program to set the IP which did work but was clunky and with limitations (ONLY in Win XP... Win 7 didn't work and of course they don't want to even mention Linux). After some back and forth, the tech said this unit was non functional. I figured it was possible that it was but didn't bank on his credibility.

Solution:
**Step 1** - Get an IP address assigned to this Linksys Print server. This was initially done on an old XP laptop using the LinkSys Bi-Admin utility. I won't go into the steps other than that you need the Linksys Bi-Admin program in Win XP. It should recognize the device when connected to ethernet and allow you to name the IP address. I used a far simpler method and found a USEFUL NEW TOOL (Arp Scan) in the mean time! 
here goes:
download Arp-Scan which is a utility to find all IP's within a LAN. This will basically show every computer or device you have connected locally on the LAN side of your router. What a great tool! Here's how I obtained this:
```

    sudo apt-get install arp-scan


```

Next run the program
```

sudo arp-scan -l

```

This should show the IP and** more importantly _MAC address_ (we'll need this shortly)** of every device on your network. Identify the device you believe to be the LinkSys Print Server. In my case it was:

```

192.168.x.xxx    xx:xx:xx:xx:xx:xx    SERCOMM CORPORATION

e.g.
<IP>   <MAC>   <PRODUCT IDENTIFICATION>

```

It wasn't obvious that (SERCOMM) was the LinkSys but I knew by identifying the other devices of which I knew the IP or the identification. With the MAC address handy now we can assign an IP address to the device. NOTE: I also reset the device first by unplugging all cables, holding RESET, then plugging the power in and waiting 10 seconds with RESET held. Next here's how to assign the devices new IP:


THIS is a NEAT Tool!! I found this through Axis Corporation. It lets you assign an IP to a device for which you know the MAC address.
```

      
sudo arp -s 192.168.x.xxx xx:xx:xx:xx:xx:xx temp


```
but of course fill in the IP you want to asign and the mac address of the device. E.g.
```

     
sudo arp -s 192.168.1.102     00:b0:05:g8:22:14 temp

 

```

Now we finally have an IP for this device that we can reach via a browser. Simply type in your new IP into a browser and hit enter. This will bring you to the LinkSys print servers control panel. 

**Step 2: **Install the newly setup print server's printer(s) in Ubuntu:
   [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[IMG]https://help.ubuntu.com/community/NetworkPrintingWithUbuntu?action=AttachFile&do=get&target=findNetworkPrinterScreenshot.png[/IMG]

It was as easy as this graphic makes it (1, 2, 3). 1. Find Network Printer 2. Type in the Print Server's IP 3. Click on "Find".

Then go through the usual driver choices for your printer and keep clicking Forward until your done. 


THE END... since this is after all a Linux forum. 




But a quick appendix for Windows users on the same network. This part is just pasted from my own notes to myself and not edited but should get you an idea:

   
Adding the printer in Windows XP:
 1. Add a Printers
 2. Local Printer attached to this computer
 UNCHECK Automatically detect
 Next
 3. Select Creat a new port
 Standard TCP/IP Port
 enter the IP into IP Address
 Port Name automatically fills
 Next and Do Not Share This Printer




 


 Adding the printer in Windows 7:
 1. Start > Ctrl Panel > Programs and Features
 2. Turn Windows features on or off
 Check LPD Print Service
 Check LPR Port Monitor
 Click OK.
 3. Start > Ctrl Panel > Devices and Printers > Add a Printer > Local Printers
 4. Create a new port > Standard TCP/IP Port
 5. IP address (possibly prompted for it twice)

---

