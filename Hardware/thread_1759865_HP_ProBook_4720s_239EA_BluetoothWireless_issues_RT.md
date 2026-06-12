---
title: "HP ProBook 4720s 239EA: Bluetooth/Wireless issues RT3090"
date: 2011-05-16
forum: Hardware
---

### Post by HainjeDAF on 2011-05-16
L.S.

I have bought a HP ProBook 4720s (WT239EA).
It came with Core I3-370M 2.40GHz and 3Gb RAM
The wireless device is RT3090 

Yes, I've been reading postings on this horrible chipset

I upgraded RAM to 8Gb

Under Win 7 Pro 64 the machine works fine. WLAN performs
at 150mbit, bluetooth connects flawless with HTC desire HD and Jabra BT8010 headset.

Ubuntu 10.04 and 10.10 installed, but reboot into system hung on
RT2800 drivers. Blacklisting those, made system boot.
With the RT3090-dkms modules, WLAN would work at 54mbps and no Bluetooth

Now I run 11.04 Natty 64bit. 
Wlan still sticks at 54mbps max.
Also, bluetooth is present. but I can't connect to bluetooth devices.
Devices won't see the laptop (made discoverable) and laptop doesn't see
devices.

HELP? I'm reading and reading on internet and no solution pops up.
I tried the 3090-dkms. They install, but mess up networking...


Regards,
Marout

---

### Post by zztoninho on 2011-06-20
dear friend 

i have the same problem but i read in some brazilian(i`m brazilian) foruns if you log in on windows 7 and turn off the wireless devices with dedicated key like fn+f12(in my case)and reboot the computer, after that log in in ubuntu and turn on the wireless devices with dedicated key like fn+f12(in my case).


it`s work fine in my case !

i hope help

---

### Post by owiknowi on 2011-06-20
just to let you know: i've just posted a thread titled HP dv6-3185ED
[http://ubuntuforums.org/showthread.php?t=1786836](http://ubuntuforums.org/showthread.php?t=1786836).

although my hp is a dv6 it looks like it uses the same (bunk)chipset.
maybe some answers will come up which might help you too?

regards from holland ;)

---

### Post by Pifilatakanemu on 2011-08-25
Any news on this problem?

---

### Post by heinz42 on 2011-08-26
Hello

I have a HP ProBook 4720s too. It work now fine.

For your problems see:
[http://georgovassilis.blogspot.com/2011/01/ubuntu-1010-64-bit-on-hp-probook-4720s.html](http://georgovassilis.blogspot.com/2011/01/ubuntu-1010-64-bit-on-hp-probook-4720s.html)
and
[http://georgovassilis.blogspot.com/2011/04/hp-probook-4720s-on-ubuntu-1104-64bit.html](http://georgovassilis.blogspot.com/2011/04/hp-probook-4720s-on-ubuntu-1104-64bit.html)

Regards from Switzerland
heinz42

---

### Post by djove on 2012-06-19
Any news on this? I haven't had problem with wireless with 12.04 neither with 11.10 but I cannot make bluetooth work. It only scans and does not find any device. I have HP ProBook 4520s

---

### Post by angiolucci on 2012-09-27
I had some problems with the bluetooth (the wireless adapter is OK)...

Try to run this on terminal:
bccmd psset -r -s 0x0000 0x028c 0x0001

It works fine on HP Pavilion dv5 2115 (brazilian model), wich has a
RT3090 wifi card. It also runs OpenSUSE 12.1.

It's not my solution, take a look at the original text: 
[http://www.linlap.com/wiki/hp+pavilion+dm1-3100](http://www.linlap.com/wiki/hp+pavilion+dm1-3100)

Good luck and be careful :lolflag:

---

### Post by mths95 on 2012-09-29
> **angiolucci said:**
> I had some problems with the bluetooth (the wireless adapter is OK)...

Try to run this on terminal:
bccmd psset -r -s 0x0000 0x028c 0x0001

It works fine on HP Pavilion dv5 2115 (brazilian model), wich has a
RT3090 wifi card. It also runs OpenSUSE 12.1.

It's not my solution, take a look at the original text: 
[http://www.linlap.com/wiki/hp+pavilion+dm1-3100](http://www.linlap.com/wiki/hp+pavilion+dm1-3100)

Good luck and be careful :lolflag:
OMG, my friend! After a year, finally a solution. I'm also Brazilian and I have the same laptop model, so I registered here just to thank you. Tomorrow is my birthday, so imagine how happy I am, because my ubuntu installation was stopped with no support to bluetooth, hdmi and clickpad. I finally installed ati drivers with success and now bluetooth works like a charm.

Hm... just wondering... do you know how to enable clickpad working like on windows? Multi-touch, gestures, click and drag...?

---

