---
title: "Wireless connectivity issues"
date: 2009-05-16
forum: Hardware
---

### Post by Darth_Canadius on 2009-05-16
I have a Dell Latitude D600 with a Dell TrueMobile 1400 wireless card.

I have been working for two days trying to get this device to work, and today I managed to get the device to work, sort of. It will connect to my Linksys router from ONE spot in my house and no other, not even right next to it! If I click the network connections icon at the top of the screen, it will show the wired connection, and have my wireless network as an option under the wireless network section. However if I try to connect, and by the Grace of God it does, it will only stay connected for about 15-30 seconds, then become disconnected. When I do try to connect, I always unplug the wired connection first. Most of the time it doesn't help.

Thanks in advance for ANY help that is offered, my brain is so toast after these two days of a crash course in bash.

Nathaniel.

---

### Post by xliang on 2009-05-16
Get into a console, "sudo iwconfig" to check if there is a wireless device. Now, most the wireless device is wlan0. If you find it, then use "sudo ifconfig" to check if the interface is working. If you can not find it after "ifconfig", you need bring the interface up by "sudo ifconfig wlan0 up". Then use "sudo iwconfig" to check if the device could work or not. If the iwconfig can give the device mode, security and othe information. That means the deicve works. Then you can use "sudo iwlist wlan0 sc" to search which network you can find in your range.

---

### Post by Game Over on 2009-05-16
> **xliang said:**
> Get into a console, "sudo iwconfig" to check if there is a wireless device. Now, most the wireless device is wlan0. If you find it, then use "sudo ifconfig" to check if the interface is working. If you can not find it after "ifconfig", you need bring the interface up by "sudo ifconfig wlan0 up". Then use "sudo iwconfig" to check if the device could work or not. If the iwconfig can give the device mode, security and othe information. That means the deicve works. Then you can use "sudo iwlist wlan0 sc" to search which network you can find in your range.

I love how all my questions are already answered when I get to the board :)

Makes it hard for this n00b to earn beans, tho...

---

### Post by Aaardwark on 2009-05-16
I think that has a Broadcom chipset. Could you check that for me by pasting this into the terminal?:
lspci | grep broadcom
or
lspci -n | grep '14e4:43'

It should show something like:
Broadcom Corporation BCM4309 802.11b/g (rev 01)

---

### Post by Darth_Canadius on 2009-05-17
I know the device can work, because it can connect to my network, it just cannot stay connected.
And, I know the router is working because the windows user in the house are able to still connect

---

### Post by Darth_Canadius on 2009-05-17
Aaardwark,  when i copy and pasted the first command, nothing happened. When I did the same for the second, this came up 
                                   :02:03.0 0280: 14e4:4324 (rev 02)

hope that ansewers your question.

---

### Post by Muscovy on 2009-05-17
I'm having similar problems. I tried iwconfig and only found results for eth1. What does this signify?

---

### Post by Darth_Canadius on 2009-05-23
OK, so I found out that the Dell TrueMobile 1400 wireless card is based on Braodcom's BC M4309 chipset. Please, someone, I seriously need help. I would like to not be tethered by a cable any more.

---

### Post by kevinmack on 2009-05-23
Was getting this as well on upgrade to 9.04.  Wireless worked on Ubuntu 8, but wasn't recognized on 9.04 until I used System-->Administration-->Hardware Drivers-->Broadcom STA wireless driver-->Activate.  It seems that it was trying to use the incorrect B43 driver before then.

Details before:
kmack@kmack-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Details after:
kmack@kmack-laptop:~$ sudo iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"NETGEAR1"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:22:3F:44:C5:1A   
          Bit Rate=2 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-51 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


kmack@kmack-laptop:~$ lspci -n|grep '14e4:43'
0c:00.0 0280: 14e4:4328 (rev 01)

---

### Post by Darth_Canadius on 2009-05-24
Well, after looking at my hardware drivers, there is an active driver called Broadcom B43 Legacy wireless driver. The description of the driver is: "fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files."The only thing is, I don't remember installing it, and when I tried to install B43-fwcutter, it said it couldn't find it. However, I'm not complaining since it's been working for almost 4 hours now.

---

### Post by mermulade on 2009-05-24
I am having similar problems.

---

### Post by Darth_Canadius on 2009-07-31
Whatever I did the first time, it was apparently kernel-specific, because when I updated, my wireless stopped working. So I re-tried ndiswrapper, and it's been working ever since. Even after a few further updates.:D

---

