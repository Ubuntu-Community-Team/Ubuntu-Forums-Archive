---
title: "Can't get the wireless to work?"
date: 2011-04-29
forum: Hardware
---

### Post by TechViking on 2011-04-29
Hi, I have recently installed Ubuntu 11.04 on a hp presario cq60, and for some I am having terrible trouble getting the wireless to work. I read another thread of someone having similar trouble here : [http://ubuntuforums.org/showthread.php?t=1049530](http://ubuntuforums.org/showthread.php?t=1049530) , I have tried installing madwifi which I was told would work but can't figure out how to do this if anyone can assist me in this I would most appreciate it :) :D

---

### Post by RedSingularity on 2011-04-29
What is your wireless card manufacturer?  Run the following command to find out:

lspci | grep Network

---

### Post by ThomasVH on 2011-04-29
What card are you exactly talking about?

---

### Post by TechViking on 2011-04-30
hi thanks for the quick response,

i entered that command into terminal and it returned this

```
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

thanks again for any help I'm getting better at linux but i'm still a bit noobish with this :D

---

### Post by redrach on 2011-04-30
> **RedSingularity said:**
> What is your wireless card manufacturer?  Run the following command to find out:

lspci | grep Network

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by RedSingularity on 2011-04-30
> **TechViking said:**
> hi thanks for the quick response,

i entered that command into terminal and it returned this

```
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```thanks again for any help I'm getting better at linux but i'm still a bit noobish with this :D

There is a known bug for that adapter that is being worked on.  Look [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710738")

---

### Post by RedSingularity on 2011-04-30
> **redrach said:**
> 00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Am I correct in assuming you are having wireless issues too redrach?

---

### Post by TechViking on 2011-05-02
> **RedSingularity said:**
> There is a known bug for that adapter that is being worked on.  Look [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710738")

thanks for the response :D, i was wondering if any software installments might resolve this there was a post somewhere about madwifi fixing this issue but every time i try to install it in the terminal as it isn't available in the software centre it keeps breaking :'(, I'm not exactly pro with the terminal, all these years of windows has made this style of installment a bit confusing i think :P

---

### Post by RedSingularity on 2011-05-02
You will need to install the madwifi modules from the source code I believe.  Where did you download the drivers from?  Have a link?

---

### Post by TechViking on 2011-05-04
this is the site i used : [http://madwifi.org/](http://madwifi.org/) i really appreciate the help btw :D

---

### Post by drpjkurian on 2011-05-04
Try my [post]("http://ubuntucrack.blogspot.com/2010/07/howto-install-madwifi-drivers-for.html")

---

