---
title: "Getting broadcom 4318 wireless to work"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by deavik on 2007-01-28
Hello,

I have been a happy Ubuntu user for the past year -- recently I got a [new laptop]("http://www.newegg.com/Product/Product.asp?Item=N82E16834228002") that came with the Broadcom 4318 wireless chipset. Now I have looked through and followed instructions from the Ubuntu guide, the ubuntu forums, and other sources on the internet but I just can't get it to work.

As of now I have ndiswrapper-1.35 installed (downloaded from sourceforge) and the driver is copied over from my windows xp partition (where wireless works, btw). I don't know where the problem is, so here are 2 terminal commands which i thought might be useful: 
```

avik@gumbo-jr:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

avik@gumbo-jr:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

```

The wireless light just doesn't turn on on my laptop whatever i do, and of course i can't access the internet -- I would be really grateful for any ideas...

Thanks

/edit: I have 6.10 installed

---

### Post by warkro on 2007-01-29
i have the same card.  My light doesn't go on either.  But my connection works.  follow this howto [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

---

### Post by CCBalla10 on 2007-01-29
try this one also...got my light turned on...using Ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Enjoy!

---

