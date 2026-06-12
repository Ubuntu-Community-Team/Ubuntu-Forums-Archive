---
title: "Help - blank screen after login"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by voxe on 2006-01-17
I just installed 5.10 on an IBM T20 (12GB, 256MB, netgear wifi card) using a single CD installer I downloaded from ubuntulinux. I can login but I only see a brown background and the mouse pointer. I can move the mouse pointer, but can't see or do anything else. Help!

Other details, though I'm not sure its relevant: I used Ctrl+Alt+F1 and can open a shell, but i can't seem to ping another machine on my home wifi network (I used the IP Address). BTW, DHCP auto-config failed, and I had to manually configure the IP address. Since I'm on a cable modem, I looked at the IP of my gateway (X.X.X.1) and a working computer (X.X.X.2) and used the same IP with the last field incremented by 4 (X.X.X.6).

---

### Post by gosh on 2006-01-17
From the shell you could try to reconfigure xorg:
sudo dkpg-reconfigure xserver-xorg

or if that doesn't work reinstall the desktop:
sudo apt-get install ubuntu-desktop
About your network connection, is your driver properly installed?
What does iwconfig says?
This link has a number of troubleshooting suggestions: [https://wiki.ubuntu.com/WiFiTroubleshooting?highlight=%28wifi%29](https://wiki.ubuntu.com/WiFiTroubleshooting?highlight=%28wifi%29)

---

### Post by psYchotic on 2006-01-19
I had a similar problem, and it seems that letting ubuntu handle the wireless all by itself makes it hang for sometimes as long as 5 minutes. Anyway, what I did was : I waited long enough for the desktop to load (be patient, it should load), and then went to System --> Administration --> Networking, selected my wireless connection and then clicked on Properties, to finally uncheck "Enable this connection". There's one downside to all this : you have to configure your network everytime you reboot. But that's quite easily done with a script, mine looks like this : ```
sudo iwconfig wlan0 essid <my essid> enc s:<my ascii WEP key>
sudo dhclient wlan0
```
You could also use gksudo, or maybe someone knows how to make a script run in single user mode upon login.

---

### Post by voxe on 2006-02-12
Alas - I tried the above suggestions (to the best of my understanding), with no luck. I reinstalled ubuntu without the wireless card plugged in, but with a live ethernet cable plugged in. Now the desktop does eventually come up (after around 20 minutes).  But it takes a minute for any UI operation (click on a menu, button) to complete or to launch any app (CPU utilization is fairly low, something  else is going on). 

Ubuntu failed to detect my built-in ethernet controller while scanning for hardware during installation. System->Administration->Networking only has a modem connection listed. 

Wireless card shows up as "eth0" when I type iwconfig. However, using the "sudo" commands above to configure the essid and passwd, the DHCP command is fails. My wireless router does not show association with this computer.

I'm running out of options, short of trying another distribution (like Red Hat). 
Any suggestions on which distribution/version to use for my IBM T20 laptop?

Thanks a lot for all your suggestions.

---

