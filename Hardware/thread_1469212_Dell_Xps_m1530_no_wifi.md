---
title: "Dell Xps m1530 no wifi"
date: 2010-05-02
forum: Hardware
---

### Post by TheZodiac on 2010-05-02
Just installed Ubuntu 10.04 (dual booting with windows 7) 

in Ubuntu i am unable to detect my wireless router 

Laptop model: Dell Xps M1530 

wireless built into laptop: (made by Broadcom) 1505 Draft 802.11n WLan Mini Card

any way i can fix this? 





(when i boot into windows 7 it detects the wireless card no problem)

---

### Post by pedro_cesar on 2010-05-02
I am having this same issue, with the same hardware and same circumstances.
(Although, I installer mine with Wubi, dunno if that the case for the previous)

---

### Post by TheZodiac on 2010-05-02
> **pedro_cesar said:**
> I am having this same issue, with the same hardware and same circumstances.
(Although, I installer mine with Wubi, dunno if that the case for the previous)


yes, i installed via Wubi as well

---

### Post by pedro_cesar on 2010-05-02
@TheZodiac, I followed this tutorial and now I'm happily connected with my wi-fi :)
[http://swiss.ubuntuforums.org/showthread.php?t=1467458](http://swiss.ubuntuforums.org/showthread.php?t=1467458)

The only downside is that you MAY need a working wired connection.

When you download your corresponding file you will find a README inside, open it (with your favorite text editor) and there you'll find installation instruction.

Post back if anything ;)

---

### Post by bunkie21 on 2010-05-02
I followed the instructions provided on this blog:

[http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-and-broadcom-bcm43xx-wireless/](http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-and-broadcom-bcm43xx-wireless/)

And it worked.  I did need to connect to the internet with a wired connection and I also had to enable the "source" sources.

It was a simple fix and now a few minutes later I am up and running.

FYI, My Dell laptop uses the Broadcom BCM4311 802.11b/g WLAN controller.

---

### Post by TheZodiac on 2010-05-02
> **pedro_cesar said:**
> @TheZodiac, I followed this tutorial and now I'm happily connected with my wi-fi :)
[http://swiss.ubuntuforums.org/showthread.php?t=1467458](http://swiss.ubuntuforums.org/showthread.php?t=1467458)

The only downside is that you MAY need a working wired connection.

When you download your corresponding file you will find a README inside, open it (with your favorite text editor) and there you'll find installation instruction.

Post back if anything ;)


thanks ill give it a shot the next time i have access to wired internet connection.

---

### Post by pedro_cesar on 2010-05-03
> **pedro_cesar said:**
> The only downside is that you MAY need a working wired connection.

I meant that only to complete the installation.
Just to clarify, after you are done with the install you should not need any wired connection. :)

---

