---
title: "Dell WLAN 1395 Wireless Issue"
date: 2008-06-20
forum: Hardware
---

### Post by NosLycn on 2008-06-20
I've got a Dell Inspiron 1521 laptop (AMD X2, ATI GFX, UBUNTU LINUX - SELF-INSTALL). The laptop works beautifully with Ubuntu Gutsy except for one thing. Periodically, the computer will lose its wireless internet connection. This happens a few times a day and is unpredictable. Other times, it is slow. I am using the drivers from the Restricted Drivers manager (bcm43xx-fwcutter) for the Dell 1395 card. The driver shows up in lsmod as bcm43xx:


> bcm43xx 127336 0 
ieee80211softmac 31360 1 bcm43xx
ieee80211 35656 2 bcm43xx,ieee80211softmac

To get the connection operational again, it usually works to wait. Network Manager never changes to show it as disconnected, but during these times, I'm not even able to access my router's configuration.

I used to use ndiswrapper, which was even worse. It died after 5 minutes of connection, the maximum download speed from anything was 10k/sec, and my mother was very cranky with it. Then, I tried Hardy on this laptop and the fwcutter worked. But, it had the same issues. I switched back to Gutsy out of convenience (my other computer is running Gutsy due to a personal life choice--Hardy does weird things to the other computer). When I noticed that fwcutter was working in Gutsy, we stuck with that.

Does anyone know a way to solve this? I attempted to replace it with my Intel 3945abg wireless card, but the laptop wouldn't recognize it. I have until September to find a way of keeping this as steady as possible. Thanks, everyone.

---

### Post by stats on 2008-07-10
the driver is in the repo now
if you dint install  ndiswrapper then skip steps 2,3,4 
1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

### Post by rosegarden78 on 2008-07-17
I have the Dell 1350 WLAN on the Inspiron 1200.  Back in Gutsy, Feisty, ndiswrapper wouldn't work.  I always had to use bcm43xx-fwcutter.  Anyway, back to the question:  Just today, finally, I found TWO reasons why my Internet connection was slow, and cutting me off repeatedly at random.

1) EM interference - I owned a 2.4 GHz cordless phone.  Guess what?  It uses the same microwave frequency as WiFi!  To demonstrate place your handset by the wireless card.  When you press Talk to get a dial tone, you should see your WiFi lights get disrupted.

While the phone is on, your wireless card/router connection will disconnect.  But you should still have Internet via ethernet cable.  When you turn off the handset, the WiFi will automatically connect.  To prove this was not defective house wires, I plugged in an old 900 MHz cordless phone.  The dial tone did not brick my Internet connection.

Long story short: You can't have two radio waves on the same 2.4 GHz.  And if your neighbor uses a 2.4 GHz cordless phone you are SOL.  If all else fails ask your neighbors over for a tea party.

2) Misconfigured router beacon - I have a Linksys so my router config is at 192.168.x.x.  If you enter Wireless - Advanced Wireless Settings you can change these values:

a)  Beacon interval - change from 100ms to 10ms.  This makes a HUGE difference in speed and eliminating dropped signals.  To test the validity of this, change it to 5000 ms and watch what happens in a packet sniffer like Wireshark.  These "beacons" are used to synch your router and wireless card so services like YouTube can work properly.

b) Frame burst - This had no effect until I changed the beacon interval, but set this to Enabled if you want the best possible performance.

c) AP isolation - I turned this on and everything works so I left it.

d) WPA encryption - You wouldn't want a DoS attack by somebody with Aircrack or Wireshark sniffing your traffic or worse.  You can find plenty of tutorials on how to break WEP encryption.

3) Bad wiring - Make sure you have DSL filters on your phone jacks.  Make sure the phone cable is firmly attached to the wall and modem.  Make sure all cables are firmly inserted.

Good luck!  It took me a year to realize the problem was EM interference.  I feel sorry to Verizon for yelling at tech support, and blaming them for faulty wiring.  Final note: We called our ISP and threatened to cancel and they informed us they had found a network problem.  They said they had fixed it, but nothing except removing the culpret cordless phone and changing the beacon interval helped the poor wireless connection.:)

---

