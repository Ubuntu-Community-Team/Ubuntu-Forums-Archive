---
title: "Hardware switch or internal motherboard issue? HP G62 wireless woes..."
date: 2011-06-08
forum: Hardware
---

### Post by trekon86 on 2011-06-08
Hey all,
I bought an HP G62 after my old college lappy got fried by a lightning strike.

The wired connection works, but I'd prefer to use the wireless (so's it doesn't happen again) but it seems that when I went and wiped the disk, Windows effed something up insofar as the wireless goes. It seems like the wireless card is recognized, and there are driver(s) installed. One is called "ath9k generic" and the other is called "ath9k hw" but I'm afraid to disable either of them. I am not much of a computer guy unfortunately... 

(I did what it said on this entire page: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)). 

The readout says:for

```

pmz@pmz-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
 
```
pmz@pmz-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
pmz@pmz-laptop:~$ 


[/CODE]


What to do? I don't know how to switch the wireless card back on, or if that's even possible. The card is an Atheros 9285.  I tried the old FN + F12 trick, even experimenting with various combinations and durations of pressing. No dice.

I am afraid I may be forced to buy a copy of Windoze if I want to get my crap working again:mad:

Thanks for any help you all may be able to give me!
PMZ

---

### Post by jramshu on 2011-06-08
The g62 has the 'key' to activate it doesn't it? There has to be a way to activate it, it should have came on by itself.

EDIT: I have looked around and haven't found much, may be a way to enable the alt-f12 keys in bios. Still looking.

---

