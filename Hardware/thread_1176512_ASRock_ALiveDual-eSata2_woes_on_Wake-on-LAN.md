---
title: "ASRock ALiveDual-eSata2 woes on Wake-on-LAN"
date: 2009-06-02
forum: Hardware
---

### Post by Verzweifler on 2009-06-02
I am facing some issues with my ASRock ALiveDual-eSATA2 mainboard and its onboard Gigabit-NIC. 

It took quite some while until I found a hint that the NIC won't work with kernels higher than 2.6.24 unless boot parameter "pci=nomsi" is added... (I was really close to buying another PCI(express)-NIC)!!

Now comes the next trouble: although my onboard NIC is capable of wake-on-LAN, it won't wake up!
```
sudo ethtool eth0
```
returned appropriate information, i.e.
```
Supports Wake-on: pumbg
Wake-on: g
```
but when I send my server to sleep (using halt), it will rest in peace and won't wake up when sending magic-packets to its NICs MAC... 
I observed the following that might be the reason for it: The moment the machine goes silent, the associated link indicator of the switch the NIC is connected to goes dead and comes alive after about a second. When using a PCI-NIC (well, on my previous mainboard), that link stayed up...

Any ideas?

---

### Post by Verzweifler on 2009-06-12
Anyone?

---

### Post by yotis on 2011-03-01
Hello,

By any chance this you solved this issue? I have the same environment (Ubuntu 10.04 and ALiveDual-eSata2)

Thanks!

---

### Post by yotis on 2011-03-07
Hello all,

Everytime when I searched on Google for words like ASRock, AliveXFire, Dual-eSata2 and Ubuntu + WOL, I did arrived in the first 10 results to this thread. Since I did solve this issue in the meantime,  I said to add the solution here for whoever is looking.

1st AliveXFire eSata2 support Wake Up events in BIOS [[http://www.asrock.com/mb/overview.asp?Model=ALIVEXFIRE-ESATA]("http://www.asrock.com/mb/overview.asp?Model=ALIVEXFIRE-ESATA2")], so this is not an issue. This means that any operating system can be convinced to do WOL, including Ubuntu

2nd, go to this post: [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588) and follow the steps in the _Manual Way_ and it will work perfect. Thanks [Chris  Tucker]("http://ubuntuforums.org/member.php?u=49236")

If this is not working you're doing something wrong or you're not sending the WOL packets. I have a Linksys router with DD-WRT in front and I have to problem to "wake-up" my ubuntu machine, even from remote end through DD-WRT web interface.

I hope this will help you all that arrive on this page!

---

