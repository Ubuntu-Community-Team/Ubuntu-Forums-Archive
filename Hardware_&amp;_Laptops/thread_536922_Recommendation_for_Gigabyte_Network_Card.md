---
title: "Recommendation for Gigabyte Network Card"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by Betaride on 2007-08-28
Hi

I'm using my Ubuntu server (Ubuntu 6.06 LTS) mainly as NAS for backups. Since the 100MByte Network structure is to slow I'dlike to install a gigabyte network card.

I already tried a Linksys EG1032 without success. Ubuntu didn't recognise the card correctly.

Can somebody give me a recommendation about a card that is known to work on a plain Ubuntu 6.06 LTS?
My favorite (because I can get it from my local shop) would be a D-Link DGE-528T. Any experiences with this card?

Best Regards
Betaride

---

### Post by sebald on 2008-02-06
workin' on the same thing... want to upgrade 6.06LTS server with gigabit... got both Linksys EG1032 and DLink DGE-530t, on the theory that one of 2 might work out of the box... but no luck... now researching what's necessary. We may have to do something to make hardware updates happen, I expect things would not be very automatic with a command line server.... more to come...

---

### Post by krazyderek on 2008-02-23
any updates guys? i'm in the same boat, i want to upgrade my ubuntu 6.06 lts NAS to gigabit since most of the other computers on the network are already.

I can find plenty of gigabit cards that say they're supported by linux kernel ### but i can't find where ubuntu 6.06 lts kernel # is to compare?

The Dlink DGE-530T was my first local choice aswell but i don't mind ordering in one or two cards if they're reasonably priced online.

---

### Post by Fire_Chief on 2008-02-23
You might want to try an Intel PRO/1000 PCI NIC in the system. NewEgg has one [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106121") for $30 + shipping. 

There were some reports of speed issues with this NIC on 6.06 LTS but installing the driver from Intel may have fixed it. Read more on that [here]("http://ubuntuforums.org/showthread.php?t=473966&highlight=82541PI")

Cheers

---

### Post by krazyderek on 2008-02-24
actually i picked up a dlink DGE-530T and plugged it in my ubuntu 6.06 box, disabled the onboard lan in the bios then booted up and the new card works. I'm having a little trouble installing ntop so i can see what kinda speed i'm getting sharing files over the network but the card it's self it working fine for surfing.

anyone want to help me with installing ntop :) ?

derek@ubuntu:~$ cp [https://svn.ntop.org/svn/ntop/trunk/ntop](https://svn.ntop.org/svn/ntop/trunk/ntop) my_ntop_goes_here
cp: cannot stat 'https://svn.ntop.org/svn/ntop/trunk/ntop' : No such file or directory

I can browse to the page online and it's working fine... so i duno???

---

