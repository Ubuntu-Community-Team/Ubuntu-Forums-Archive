---
title: "Problem while configuring broadcom wifi with pppoeconf while setting up wireless DSL"
date: 2010-05-28
forum: Hardware
---

### Post by g33kd_pr1nc3 on 2010-05-28
Hello all you linux geeks :) , glad to be part of this open source league FINALLY!!!!
I have no idea why it took me so long to join here, I am very happy to share whatever I know with you amazing ppl :)

But now I have a very serious problem. Here is how it goes. I installed Ubuntu 10.04 on my Dell Studio 1535 laptop. The installation had no problems whatsoever. My laptop has a Broadcom Wifi Adapter, specifically BCM4312, I know ubuntu has wireless disabled by default. So what I did was first plug my ethernet connection from my desktop to my laptop and I updated all my repositories through the internet. I've installed the pppoe driver package as well. Then when i was asked to install restricted drivers, the following drivers were given to me, as a choice of activation:
1. Broadcom B43 wireless driver
2. Broadcom STA wireless driver
I chose option one and the driver installed successfully, then i reboot there it was my wifi up and and running fine. I was even able to connect to wireless access points that I've set up successfully. Now I wasn't out of the woods yet, see I wanted to connect my DSL through wireless, so far I've got only till connecting to a wireless access point :P , then I read several ubuntu forum posts which guided me to use 'pppoeconf' to set up DSL over existing ethernet, which I did after my wifi was successfully connected. The access point concentrator that came up while running pppoeconf detected my wlan0 correctly, and i was able to configure my dsl just as easy as it would have been if over a regular wired DSL. Now it told me to run 'pon dsl-provider' to connect, which i did, and the i was able to access the internet successfully with a big smile in my face, but once I rebooted my system, the following took the smile of my face :((((
The network applet didn't show up at the top most right corner as it supposed to ( both wired and wireless)  I never knew why, I tried to run 'pppoeconf' again but it said my wlan0 is not responding to the concentrator, check network config and cables, or another pppoeconf is using the interface, please help me, i have no idea what did i do wrong, i mean before i rebooted , the initial configuration worked fine and i was able to access the internet, when I restarted my laptop, all this happened :(
Please help my guys, and sorry for being so wordy :P

---

### Post by efflandt on 2010-05-28
I am somewhat puzzled how you got PPPoE to work at all over a wireless connection.  Do you have a DSL bridge modem with just a wireless AP (not a router) connected to it?  I could be wrong, but I thought wireless was tcp/ip only, and PPPoE on the outside is something else (my old DSL bridge modem did not even have an IP).

It is possible that something you did manually interfered with network manager, but I seem to remember the network applet disappearing on at least one of my systems in Lucid (I think the default "Auto eth0" disappeared).  But I simply went to System > Preferences > Network Connections and set it up again.  I know that with wireless I have to sometimes do it a couple of times to actually make it stick.  Make sure that you check the box "Available to all users".

Not sure which wireless module is best for your laptop, but when I tried 9.10 on a Dell 1545 with BCM4312 wireless that I had temporarily, I used Broadcom STA instead of B43.  But not sure how well that works in Lucid, because the BCM4311 in my work Inspiron 6400 was too weak to get a signal, so I used an automatically supported Linksys USB54GSC v1 instead.  Note that Broadcom STA and B43 are mutually exclusive, and with STA wireless appears to be eth instead of wlan, but Network Connections can still find it (and **sudo iwlist scan** works).

I do use Broadcom B43 in Lucid on an old Compaq laptop, and it gets a much stronger signal than my Dell 6400.

If all else fails, why not just hang a wireless router on your modem?  Or do you have multiple static public IP's that you are trying to manage from Linux?

---

### Post by g33kd_pr1nc3 on 2010-05-28
> **efflandt said:**
> I am somewhat puzzled how you got PPPoE to work at all over a wireless connection.  Do you have a DSL bridge modem with just a wireless AP (not a router) connected to it?  I could be wrong, but I thought wireless was tcp/ip only, and PPPoE on the outside is something else (my old DSL bridge modem did not even have an IP).

It is possible that something you did manually interfered with network manager, but I seem to remember the network applet disappearing on at least one of my systems in Lucid (I think the default "Auto eth0" disappeared).  But I simply went to System > Preferences > Network Connections and set it up again.  I know that with wireless I have to sometimes do it a couple of times to actually make it stick.  Make sure that you check the box "Available to all users".

Not sure which wireless module is best for your laptop, but when I tried 9.10 on a Dell 1545 with BCM4312 wireless that I had temporarily, I used Broadcom STA instead of B43.  But not sure how well that works in Lucid, because the BCM4311 in my work Inspiron 6400 was too weak to get a signal, so I used an automatically supported Linksys USB54GSC v1 instead.  Note that Broadcom STA and B43 are mutually exclusive, and with STA wireless appears to be eth instead of wlan, but Network Connections can still find it (and **sudo iwlist scan** works).

I do use Broadcom B43 in Lucid on an old Compaq laptop, and it gets a much stronger signal than my Dell 6400.

If all else fails, why not just hang a wireless router on your modem?  Or do you have multiple static public IP's that you are trying to manage from Linux?
well thanks for your reply man :) , but the thing is when i say my network applet is gone, i didn't mean the configurations like auto eth0 or any other wireless network access points for that matter, as you said i can still access it from System-> preferences-> Network Connections. Infact the pre configurations i made for connecting to my wifi access point remains intact. Like if say consider i wanted to connect to an access point named "Mywifi" its not displaying as "Wireless networks available" on the top right corner as it used too. The applet simply vanished, seeing that its the only way to connect to any network if i don't have "auto connect" checked for that connection. Your first question, how i managed to get pppoe over wireless, well i do have a dsl bridge modem with an access point, you were not wrong, see for the wired dsl, there is a pre option for it called DSL, where you enter your username password etc along with the other network configs like ips, gateways, dns servers etc, but for doing it in wireless, what i did was set my network config on the wireless option within the network connections, which made me connect to the access point i've set up, after that i run pppoeconf and it listed out eth0 and wlan0, seeing that wlan0 is already connected to my access point, the concentrator was able to capture my DSL connection in the same manner as it would if i had done this for a wired connection(eth0). Then the usual routine followed, where i enter the username, password, dns config, then pppd initialization followed, then what i did tell before was, my internet worked during the initial config , pon dsl-provider did connect me to the internet , but only until i've restarted. :(
when I got back into my ubuntu after restart, the applet was gone, and i tried to connect by the terminal using ifconfig wlan0, it said wlan0 no such device, and i run pppoeconf again, it said one of my interfaces was not responding or was in use with another pppoe :( . I hope now you get a clear picture of what my problem is , please help me .....

---

### Post by g33kd_pr1nc3 on 2010-05-29
:guitar: hey hey i finally got my wifi to work, thanks for the help :) efflandt, I appreciate it really :D , I found an effective round about to my problem. What I did was started over, by installing Broadcom STA Drivers instead of B43 drivers. It had my wifi adapter up and running, and I did connect to the wireless access point that I've set up earlier. Once the connection was successful, I ran pppoeconf for my wireless adapter, it was able to get the access concentrator up and running, and when it asked me to run pppd at start up i said "No", so that I can do it manually. Then when I reboot the system, as usual the applet was gone, but what I did was, sneak into my terminal, ran **"pppd" **followed by the command **"ifconfig wlan0 up" **and **"iwconfig wlan0 essid on" **and WOALAA!!! my preconfigured settings that I've set up before using network manager for my access point was up and running again :) followed by this command I ran **"sudo pon dsl-provider" **and my internet connection was back in a jiffy. I couldn't get back the network applet though :/ , but I got back my wireless DSL :D with no problems whatsoever :P One more pointer is that after iwconfig you have to give the correct name for your network interface, mine was wlan0 sometimes it could be eth1 or wmaster0 or anything else that your ubuntu could think of  :P

If anybody in india with a BSNL broadband connection, is having the same problems as i did while configuring wireless DSL? follow the above method it did wonders for me :)

---

### Post by Daisy90 on 2010-05-29
[www.zstar.hk]("http://www.zstar.hk")

---

### Post by Daisy90 on 2010-05-29
[www.tigersupermall.com]("http://www.tigersupermall.com")

---

### Post by Daisy90 on 2010-05-29
[www.zstar.hk]("http://www.zstar.hk")
[www.tigersupermall.com]("http://www.tigersupermall.com")

---

