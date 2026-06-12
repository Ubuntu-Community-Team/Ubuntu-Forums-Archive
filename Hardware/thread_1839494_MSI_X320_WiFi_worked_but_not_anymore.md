---
title: "MSI X320 WiFi worked but not anymore"
date: 2011-09-05
forum: Hardware
---

### Post by Knilch on 2011-09-05
Hello there!

After investing countless hours in trying to get any Linux to work on my MSI X320 I am currently running Ubuntu 10.04 Netbook Edition and managed to get everything running, even graphics.

One problem persists, however: Friday I installed the WiFi wit__[]("http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090")h [this HOWTO]("http://ubuntuforums.org/showthread.php?t=1600498") and everything worked fine through the weekend. I could even connect to my Apple MacBook Pro over my router, browse through images and all in acceptable speed.

However after shutting down the MSI Saturday and rebooting it today WiFi stopped working correctly. First it didn't connect at all so I tried to recompile and reinstall the driver with no success. Then I found [another]("http://planetared.com/2011/02/ralink-rt3090-en-ubuntu-10-10/") way of doing it but didn't change anything. Only after I REMOVED the blacklisted driver described in the first link the MSI actually connects to my network but is awfully slow and therefore not usable at all.

Now I ask for someone to help me as I don't know how to solve that problem. This is the controller I have:

02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

Funnily after the last reboot Ubuntu forgot the WiFi card again so iwconfig now tells me this:

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.437 GHz  Access Point: E0:46:9A:03:01:CE   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:0 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Another one:

lspci | grep Network
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

I blacklisted something last time system was on so I removed it now and will reboot again, maybe iwconfig tells something different.

---

### Post by Knilch on 2011-09-05
Yeah, that worked (well, somehow) again. Removed everything from blacklist and now it connects to my WiFi, is extremely slow and iwconfig tells me this:

lo        no wireless extensions.

ra0       Ralink STA  ESSID:"FaGe"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: E0:46:9A:03:01:CE   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level:-61 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

Help? Please!

---

### Post by Knilch on 2011-09-07
Well, I know that is something not normally wanted but I really would like a hint in my case. Anyone?

---

