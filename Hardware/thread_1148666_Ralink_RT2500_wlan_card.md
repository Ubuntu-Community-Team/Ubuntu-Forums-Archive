---
title: "Ralink RT2500 wlan card"
date: 2009-05-04
forum: Hardware
---

### Post by SBloke on 2009-05-04
I've decided to try and run ubuntu jaunty on by PB R1801 easynote. So far so good save the wlan card. 

So far it's just not working. My brother - a long term linux veteran among other things - couldn't get it to work either. Does anyone here have a solution other than to plug in an external wlan stick of trash the Ralink card?

---

### Post by ahbart on 2009-05-04
Most Ralink wireless cards work well with linux (nowadays).
What is the output of 'lsusb' in a terminal?

---

### Post by SBloke on 2009-05-04
> **ahbart said:**
> Most Ralink wireless cards work well with linux (nowadays).
What is the output of 'lsusb' in a terminal?

You know, I actually have no idea whatsoever what you're asking me. I've been held dumb by using windows for the better part of my life. (Aside from an msx2 and an Amiga 500+) 

Can you rephrase it for me or tell me where I should look?

---

### Post by ahbart on 2009-05-04
Assuming you are using the 'normal' Ubuntu and not kubuntu or Xubuntu,
Go to applications in the menu - accessories - and click terminal.

In this new black window type ```
lsusb
```
You can them select the output with your mouse and right click on it to copy it, and paste it here. ;)

---

### Post by SBloke on 2009-05-05
This was all I got:


```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1532:0001 Razer USA, Ltd RZ01-020300 Optical Mouse [Diamondback]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by ahbart on 2009-05-05
It seems this Ralink wireless card is not connected to usb.
Can you give a lspci instead?

---

### Post by SBloke on 2009-05-05
```
00:00.0 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:06.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
```


So far so good, just talk me through it :)

---

### Post by ahbart on 2009-05-05
Hmm. This "Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)" should work out of the box. Are you sure it is not working? 

What does: iwconfig (in a terminal again) report?

If you left click on the networkmanager (normally in the right top corner) don't you see any scanned networks?

---

### Post by SBloke on 2009-05-06
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions
```



When I try and look for networks I can't. The "Wireless networks" button is lightgray and can't be clicked.

---

### Post by ahbart on 2009-05-06
Well, hmm. Your wireless card is working. But not usable. 
If you click the networkmanager icon you can see:
wired network (grey)
auto eth0
Wireless network (grey)
with normally under here the available networks.

Are you sure you have a wireless network in your neighbourhood?

If you know your network settings you can try to set  wireless up manually in: menu - system - settings - network connections - tab wireless.

Else, I'm out of ideas, for the moment.

---

### Post by clarkjd on 2009-05-07
I am having the exact same problem. I have a network in my house. the wireless on my laptop works fine but my pci wireless card isn't doing anything.

---

### Post by ahbart on 2009-05-08
Does it concen the same chip? lspci in a terminal.

---

### Post by SBloke on 2009-05-08
I'm absolutely positive that there is a wireless network. Set it up myself and if I switch to windows 7 on this same laptop I have a connection right away (How do you think I'm writing this post ;) )

---

### Post by ahbart on 2009-05-08
> **SBloke said:**
> (How do you think I'm writing this post ;) )
Other computer?

---

### Post by SBloke on 2009-05-16
> **ahbart said:**
> Other computer?

Ah yes....  ](*,) should have thought of that one. 

But uhm, no... All I have is this R1801 easynote at the moment. 

WLAN s still not working though and still can't find the problem.

---

### Post by unutbu on 2009-05-16
Please post the output of 
```

ifconfig
iwconfig
iwlist scan
cat /etc/network/interfaces
cat /etc/resolv.conf
sudo /etc/init.d/networking restart
```

Wrapping the output in [code tags](" http://ubuntuforums.org/showpost.php?p=5490091&postcount=43") would be appreciated.

---

### Post by SBloke on 2009-05-17
Edited them, sorry about that one, new user here. ):P


It's still not working however.

---

### Post by Rahmenlos on 2010-07-10
nvm... my stupidity made me blind. solved. sometimes it's too easy to press fn+F2 to activate the wlan card >>

---

### Post by HDave on 2010-07-13
> **Rahmenlos said:**
> nvm... my stupidity made me blind. solved. sometimes it's too easy to press fn+F2 to activate the wlan card >>

Well your stupidity saved me, because I was struggling with this issue for over an hour before reading your post and realizing the wireless was disabled!

Sheesh...  Thanks.:D

---

