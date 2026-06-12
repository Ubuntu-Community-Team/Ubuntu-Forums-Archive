---
title: "Wireless driver works, now how do I connect to the netwrok?"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by Balistic on 2007-06-01
I managed finally to get my wireless card to work on my dell e1705 (the wireless card is intel 4965).  Now when I write ```
sudo iwlist scanning
``` I see a list of networks, however I wasn't able to connect to any.  I tried both secure and non secure networks.  Is there something else I need to do before I can connect to a network?

---

### Post by stchman on 2007-06-01
> **Balistic said:**
> I managed finally to get my wireless card to work on my dell e1705 (the wireless card is intel 4965).  Now when I write ```
sudo iwlist scanning
``` I see a list of networks, however I wasn't able to connect to any.  I tried both secure and non secure networks.  Is there something else I need to do before I can connect to a network?

What Ubuntu are you using?  It sounds like Edgy.  If that is the case then you need to install the network manager.  Follow this procedure on my website.

To be able to connect to an encrypted wireless network you need network manager and wpasupplicant installed.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Follow the portion about WEP and WPA functionality.

FYI, Feisty is far better with wireless than Edgy as network manager is installed by default and WEP, WPA, and WPA2 are supported.

Hope this helps.

---

### Post by Balistic on 2007-06-01
Yeah sorry for not mentioning the version.  I'm actually using Ubuntu 7.04 (feisty).  You know if there's anything I need to configure there?

---

### Post by Balistic on 2007-06-02
anyone...  :)

---

### Post by masterthor on 2007-06-02
you should be able to right click the network connection icon (the two computers in the upper right of your screen if you're running on a wired connection) and click Enable Wireless, and then left click it and you should see a list of wireless networks you can connect to. If you don't have such an icon, maybe you need to manually start the gnome connection manager..

---

### Post by Balistic on 2007-06-02
> **masterthor said:**
> you should be able to right click the network connection icon (the two computers in the upper right of your screen if you're running on a wired connection) and click Enable Wireless, and then left click it and you should see a list of wireless networks you can connect to. If you don't have such an icon, maybe you need to manually start the gnome connection manager..

I did that, but wireless network already had a check mark next to it.  Also, tried manualy configuring the netwrok (by choosing from the list), it displays a little bar saying its configuring the network or something like that.  No error message or anything.. But also no internet.  :(

Edit:  The message I get after manualy configuring is : "changing interface configuration"

---

### Post by Balistic on 2007-06-02
Another piece of information...
When I try to ping my router it gives me a message:
```
From xxx.xxx.xxx.xxx  icmp seq=2 Destination Host Unreachable
```
when I try to ping [www.google.com](www.google.com) for example, I get:
```
ping: unknown host www.google.com
```

So I get different replies for web sites than my router, maybe it means it sees my router but can't connect to it?

---

### Post by masterthor on 2007-06-02
maybe you need to supply some firmware for your wireless device for it to function properly. What kind of card is it? (maybe  "sudo lspci | grep Wireless" will tell you that) 

For my current setup, meaning a Broadcom wireless adapter, i had to manually supply firmware (you can probably tell if there are some file not found errors while booting up). I think that i could scan for networks before i supplied the files, but if i would to connect, it wouldn't actually work. hope it helps in some way.

---

### Post by Balistic on 2007-06-02
As I mentioned I'm on a Dell E1705 and my wireless card is intel wireless N, aka intel 4965.
I tried "sudo lspci | grep Wireless" but it doesn't say anything.
Man.. This is getting old, I've been over a week now just trying to configure my damn wireless.

---

### Post by Balistic on 2007-06-02
when I look at: System->Administration->Windows Wireless Driver it shows on the left window an icon and beneath it reads: "Hardware present: No"
I don't get this part...  I've installed ndiswrapper and the windows driver, also my wireless led is on (flashing), and I can detect wireless networks.  What else is there to do, so it "detects" the hardware?
Though I find it weird that it can detect wireless networks (using the wireless card..) but it cannot connect to them..

---

### Post by Balistic on 2007-06-03
bump

---

### Post by stchman on 2007-06-04
> **Balistic said:**
> Yeah sorry for not mentioning the version.  I'm actually using Ubuntu 7.04 (feisty).  You know if there's anything I need to configure there?

Wireless works out of the box for MOST wireless card using Feisty.  Broadcom cards will need ndiswrapper.  You should just click on the network manager icon near the clock and it will tell you what networks are available.

---

### Post by susan_1890 on 2007-06-23
Did you ever figure this out? I'm having a similar problem. I can connect to an unsecured network, but I can't connect to my secure network at home. It will ask me for the key and try to connect but it never actually works.

I'm also running Feisty and have the 4965 card. My system is dual boot and I can connect fine in Vista so I know I've got the right key and everything.

Any ideas?

---

### Post by masterthor on 2007-06-23
are you sure you're using the right key type ? (eg. you might have an ASCII key but selecting the Hex type from the drop-down box).

---

### Post by Scooter7 on 2007-06-23
I'm having a similar problem - I can see the networks on the list, but not ping them.   The only way I can connect is by enabling 'Roaming mode' for my connection and selecting a network from the list.

Otherwise, after manually entering the information, I don't get the message 'changing interface configuration'.   And often if I've done that, I have trouble re-enabling roaming mode - after I do so, sometimes I get a signal, other times I don't.   And when I do, 'connection information' gives me a bunch of zeroes for connection information, i.e IP Address: 000.000.0.0.

I'm not using ndiswrapper.   When I installed Feisty, I was told it was using restricted drivers for my wireless card.   I'm posting this now using roaming mode.

---

### Post by vronp on 2007-06-25
> **susan_1890 said:**
> Did you ever figure this out? I'm having a similar problem. I can connect to an unsecured network, but I can't connect to my secure network at home. It will ask me for the key and try to connect but it never actually works.

I'm also running Feisty and have the 4965 card. My system is dual boot and I can connect fine in Vista so I know I've got the right key and everything.

Any ideas?


Folks,

Don't you folks know how to use search on the Ubuntu forums?  If you search on "4965" or "4965agn" and then do a small amount of reading, you will learn everything you need to know.

1) the 4965 is brand new and Linux drivers are very close to being released by Intel.  Some have apparently been successful in getting the beta versions of the drivers working.

2) some have been successful using ndiswrappers to get  this to work

Please, do some searching and reading instead of starting yet another thread.

---

