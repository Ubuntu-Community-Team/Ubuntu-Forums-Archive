---
title: "Help needed with atheros AR9285 (Sony Vaio) on Ubuntu."
date: 2010-04-05
forum: Hardware
---

### Post by ultiva on 2010-04-05
Hello everyone.
I'm using Ubuntu for serveral years on three desktops and laptop. Recently I've bought another laptop - Sony Vaio VPC-EB1S1E and here are some problems. Most severe is my problem with WiFi - atheros 9285. Athough card was detected out of the box it's not working as expected, symptoms:

1. File transfers are frequently interrupted, downloading stops and stays in this state for some time (15-30 sec.) then it resumes just to go into another stop in a while. WiFi link IS NOT disassociated during this stops.
2. Web pages loads slow during this stops which is connected with symptom 1.
3. When transfer stops (and waits), I'm capable of starting another download in parallel or ping another host.
4. Additionaly top dowload speed which can be achieved (between stops ofcoz) (ftp over LAN) is about 1.8MB/s (wget), while on Windows 7 I can easily reach 2.9MB/s (filezilla) - the same file over LAN.
5. Also noticed that iwconfig shows on ath9k driver wifi link speed is  frequently dropping from 54 mbit/s to 1 mbit/s and goes up again in a  while.
6. Such symptoms ARE NOT present on Windows 7 (ar9285 driver version 8.0.0) which is also installed on this machine, on this platform everything works perfect.

Here is what I've tried so far:
1. OS: Ubuntu 9.10 32 bit, Ubuntu 10.04 b1 64 bit livecd, Fedora 12 livecd, all the following tests performed on U9.10 32bit (2.6.31-20 generic)
2. Three different APs (linksys WRT54GL + tomato) in two diffrent locations
3. Different settings - WPA2+AES, WPA+TKIP, no encryption, short/long preamble, different power settings etc.
4. Disabled/enabled BT module in laptop
5. Tried ubuntu backports karmic + wireless
6. Installed compat-wireless from source - bleeding edge
7. Replaced network-manager with wicd (and back again)
8. Unloaded, blacklisted ath9k and installed ndiswrapper with Windows XP 7.7.0 atheros 9285 driver (Vista 7.7.0 driver is not starting - device wlan0 is not created)

All of these attempts failed. Described symptoms are still present under Ubuntu and I have no idea what to do next. Plz helpme with this, because it prevents me from working normally on Ubuntu and have to use Win7 all the time.

Regards
Piotr Sikorski

---

### Post by Ernie S. on 2010-04-05
I had the EXACT same symptoms and tried the exact same solutions you did. The thing that finally worked for me was to un-blacklist the ath5k driver in /etc/modprobe.d/blacklist-ath_pci.conf. So far it's working (2 hours without a problem). Hope that helps.

---

### Post by ultiva on 2010-04-06
Thank You very much for your response. My blacklist-ath_pci.conf file looked like this:

```

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

```So, there was not ath5k module blacklisted just ath_pci and I've unblacklisted it. Unfortunately that changed nothing - symptoms still present. It looks like some kind of interference for me, because today morning I've noticed that wifi works somewhat better and can achieve 2.5 MB/s under Ubuntu also "stops" are maybe less frequent. Worst situation is in the evening. Ofcourse I've tried changing WiFi channel. Most interesting is that even if this is some kind of interference it's not affecting wifi under win7, where wifi speed and reliability is superb (must say that I've never seen such fast wifi transfers).

Can You please tell me what is in your file blacklist-ath_pci.conf ?

Regards
Piotr Sikorski

---

### Post by Ernie S. on 2010-04-09
```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
# blacklist ath_pci
```

This is my current blacklist-ath_pci.conf. It seems to be the same. I also uninstalled ndiswrapper and deleted the file that showed up in the modprobe.d folder. I think it was called ndiswrapper.conf. You should recognize it anyway. Sorry it took so long to reply (I'm traveling right now). Also these may be silly questions, but does iwconfig show any power management options turned on? And have you tried bringing wlan0 down and bringing it back up in the terminal? Before mine was working 100% I could turn the wireless card off via the hardware switch, but could not turn it back on. I would have to reboot and hold the switch during startup to get the card back on. When I brought it down in the terminal, the same thing happened. I'm still pretty new to linux so I may have gotten lucky, but there has to be a reason.

---

