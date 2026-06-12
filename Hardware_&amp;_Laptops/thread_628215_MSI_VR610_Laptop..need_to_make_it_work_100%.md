---
title: "MSI VR610 Laptop..need to make it work 100%"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by Vavo on 2007-12-01
OK i was reading forums and books and I have managed to make 7.10 work with 99% of the hardware  (after 10 days). Have MSI VR610X laptop, feel like I am the only one on this planet having it :lolflag:

I want to make few more adjustments to make it work as I want:

1. Brightness levels. It works but seems like it works fine only with Fn keys. Ubuntu do not detect the levels properly so when I adjust from KB I reach max faster..Brightness applet had reached only ~40%.. on way down it also go to 60%...Can I prevent Ubuntu with having control over this...or.. correct the levels. If I pick custom level from KB it will restore it to the settings in the power manager..annoying... if I use the applet the level jumps up/down...on some % it goes to 100% it non linear

2. When I started using it, audio card was correctly detected with all audio channels. Now there are less selectable and laptop speakers do not turn off when I plug speakers. :guitar: I get strange effect now as my speakers are inversed (right speaker is on left side so I can plug it in the outlet)+ laptop speakers. ideas?

PS. Some helpful tips if you have this laptop:

-Suspend/Hibernate does not work bcs of the ATi driver..need to get older kernel to work ..haven't tried.

-Wireless works with ndiswrapper..but it is very unusual...sometimes work sometimes not at all..locks boot sequence.. wicd program is best to make it work. Gonna post more when I make it work 100%.. madwifi will support it SOON

-Special keys: P1 is for webcamera or search but is not detected by X. FnF2 should change display, it is detected but do not assign it to other functions..FnF12..now locks the screen..at least some way to be used.

---

### Post by svetan on 2008-01-30
You not the only one :) Ubuntu 7.10 works perfect for me, wireless with 64bit wep etc... but webcam is not recognised by X too :( Did any one have idea?

---

### Post by 00void on 2008-02-26
Could you post a guide, telling how to get the wireless working? I cant figure it out.

---

### Post by sevoir on 2008-06-06
Hi!

So, in terminal:
-wifi-
sudo su
echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist
sudo apt-get update
sudo apt-get install ndisgtk
wget -c [http://www.freeweb.hu/sevoir/ar5006eg.tar.gz](http://www.freeweb.hu/sevoir/ar5006eg.tar.gz)
tar -xf ar5006eg.tar.gz
sudo ndiswrapper -i net5416.inf
sudo ndiswrapper -ma && sudo ndiswrapper -mi

-sound (speakers off if plugged head speakers)-
sudo echo "options snd-hda-intel model=targa-dig" >> /etc/modprobe.d/alsa-base  

restart laptop and be happy!

..::Sevoir::..

---

