---
title: "Wireless Networking"
date: 2011-01-23
forum: Hardware
---

### Post by Coolio G on 2011-01-23
Today, I was riding in my car, tapping away on my laptop's keyboard. I had pressed the hardware button on my computer's wireless network card to turn it off and save power. Soon after that, Ubuntu goes "lol, sucks to be u. power off work gone" and shuts down. Now, I can't connect to the internet because I can't turn my wireless network card on via the hardware button.

So, is there any terminal command or something that I can use to turn it back on?

Thanks in advance.

---

### Post by ankum16 on 2011-01-23
Hi all,

I am planning to buy one laptop, not netbook (with very less budget/ may be an old one). I want my laptop to have Ubuntu 10.10, good wireless connectivity. The only purpose of laptop is wireless/LAN internet access. Brand may be HP/Dell. Please suggest the minimum configuration which is required to run internet at good speed on ubuntu 10.10. I got the link - [https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html](https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html). But I am sure if this is sufficient.

Any suggestions welcome.

---

### Post by drpjkurian on 2011-01-23
> **ankum16 said:**
> Hi all,

I am planning to buy one laptop, not netbook (with very less budget/ may be an old one). I want my laptop to have Ubuntu 10.10, good wireless connectivity. The only purpose of laptop is wireless/LAN internet access. Brand may be HP/Dell. Please suggest the minimum configuration which is required to run internet at good speed on ubuntu 10.10. I got the link - [https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html](https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html). But I am sure if this is sufficient.

Any suggestions welcome.

Hi
The Min RAM for Ubuntu 10.10 is 512MB with intel celeron processor and for wireless card I would suggest Broadcom or Atheros. Becaiuse I have tried them both and it works fine with me. Moreover I would like to bring to your attention that the URL which you have suggested are for Servers...

---

### Post by drpjkurian on 2011-01-23
Hi Ankum
Possibly could be hardwarre problem. Not sure though
You might try
```
sudo ifconfig **wlan0** up
```
replacing the bold with your interface name (if it is other than wlan0 of course).

---

### Post by frankjeffries on 2011-01-23
> **ankum16 said:**
> Hi all,

I am planning to buy one laptop, not netbook (with very less budget/ may be an old one). I want my laptop to have Ubuntu 10.10, good wireless connectivity. The only purpose of laptop is wireless/LAN internet access. Brand may be HP/Dell. Please suggest the minimum configuration which is required to run internet at good speed on ubuntu 10.10. I got the link - [https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html](https://help.ubuntu.com/10.10/serverguide/C/preparing-to-install.html). But I am sure if this is sufficient.

Any suggestions welcome.I had the same idea and last week I bought a lenova ibm x60 only cost 150 dollars australian and only 3 years old I installed ubuntu 10.10 but it would not hook up to wifi, I then installed ubuntu 10.10 netbook,at first this also could not find wifi!!! tried everything to get it going then i found a little switch underneath the front of laptop and when i turned it on it immediately found every wifi that was within reach. The laptop is an lenova ibm x60 12" screen 1.83ghz Dual core can be upgradedto 2.0ghz 80gig hd will take up to 4gig ram 667ddr2 and is going very well i hope this helps you make a choice. I installed a program called WIFI RADAR FROM UBUNTU PROGRAMS.

---

### Post by Coolio G on 2011-01-23
Yeah, as much as I care about your current netbook stuffs, I just don't.

Can we get back on topic with solving my problem?

Further information:

It's a HP G50 with a Atheros wireless card and a hardware button that turns it on and off.

---

### Post by Coolio G on 2011-01-23
Ah! I fixed it using the instructions in this post -

[http://ubuntuforums.org/showpost.php?p=10326568&postcount=2](http://ubuntuforums.org/showpost.php?p=10326568&postcount=2)

---

### Post by drpjkurian on 2011-02-16
Please mark it as solved

---

