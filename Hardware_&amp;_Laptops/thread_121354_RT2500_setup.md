---
title: "RT2500 setup"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by Bivitor_42 on 2006-01-25
First let me say that ubuntu rocks. when I was searching and searching for an OS that would work with my machine ubuntu finally came to the rescue.

However I would like to be able to use WPA encryption instead of WEP. So I went to the wiki's and found the page for the rt2500 chips. I followed the instruction up untill i tried "sudo insmod rt2500.ko", which failed with a "-1 file exists"

I also looked at the rest of the doc and found that ~/rt2500-cvs-daily/Utilitys doesn't exist and i don't know where it came from.

---

### Post by Who on 2006-01-25
Hiya,

I know that it isn't necessary under breezy, but I like to use the RaConfig2500 utility - it is actually very competant (my Windows-using housemates are jealous!) 

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig)

explains how to get it. I didn't need to compile or install the driver, only the utility (though, the driver will probably be newer than the one with Breezy - so if things work not, you could try it)

Note: you need to download quite a lot of stuff in order to build this - so I would run the router in WPA mode, which is supported natively without any hassle while using Synaptic or apt-get install and then put WPA on afterwards. 

As far as I can tell, this utility sets up the driver so that it starts up using WPA - which is handy!

Good luck,

Who

---

### Post by jml on 2006-01-25
I agree with Who.  It turns out that the Ralink rt2500 chipset is not supported by WPA_Supplicant, the software required to impliment WPA encryption.  I spent over a week trying to get my Ralink based chipset to work before I found that little perl out.  Raconfig actually supports WPA encryption for the rt2500 chipset without needing WPA_Supplicant.  To be totally honest, I got rid of the laptop that used the rt2500 chipset before I found that bit of information out.  Hope this helps.

---

