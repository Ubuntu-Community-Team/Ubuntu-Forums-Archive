---
title: "Any 3g mini-pcie adapters that are known to work?"
date: 2012-11-29
forum: Hardware
---

### Post by sona1111 on 2012-11-29
Hello, i have a Thinkpad T60 that i am looking to get set up with WWAN. Their are two 3g antennas, a sim slot, and space to install the pcie device. I like ubuntu very much so far but sometimes I know hardware compatibility can cause problems. Has anyone had success installing an internal 3g device like this before? (USA service plans if that matters) If so, which would you recommend me to buy? thanks.

---

### Post by linrunner on 2012-11-30
Hi,

the T60 &#8211; like all Thinkpads &#8211; accepts only Lenovo cards (with Lenovo part no, called "FRU") contained in it's BIOS whitelist.  

Possible cards are listed here: [http://www.thinkwiki.org/wiki/T60](http://www.thinkwiki.org/wiki/T60)

The Sierra  MC8755 runs out of the box with Ubuntu, the MC5720 I don't know. Just take care to obtain a card without Netlock, as many of them were sold with a Vodafone lock.

---

### Post by sona1111 on 2012-11-30
thank you for the reply and suggestion. However, my laptop is not limited in its selection. The person who sold me the replacement motherboard from thinkpad forums took of the whitelist before he shipped it. For this reason, if their are any better 3g cards you would recommend over the Sierra MC8755, i will accept them.

---

### Post by linrunner on 2012-12-01
Whitelist BIOS, I understand ;-). 

Of course there are better cards in terms of downlink/uplink speed, for example the [Sierra MC8775]("http://www.thinkwiki.org/wiki/Sierra_Wireless_HSDPA_WWAN") or the [Ericsson F3507g]("http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module"). Both work ootb with Linux.

If you can get your hands on the firmware from Windows, the [Qualcomm Gobi 2000]("http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000") is another viable alternative.

However it may be difficult to use the other cards in a T60. Some people ran into difficulties to switch them on and off via rfkill or had to mask off pin 20 with tape.

---

### Post by sona1111 on 2012-12-01
the Ericsson F3507g has provisions for two antennas, which makes it more viable for the thinkpad i have. Is this limited to a specific provider? do you know if t-mobile would be ok? if not any suggestions? sorry but i am new to 3g.

---

### Post by linrunner on 2012-12-02
As far as I know (ThinkPad models sold in Germany) there are no Netlocks with the F3507g &#8211; and later cards in ThinkPads like the Gobi 2000 too. T-Mobile in Germany works of course.

---

### Post by bmork on 2012-12-20
> **sona1111 said:**
> thank you for the reply and suggestion. However, my laptop is not limited in its selection. The person who sold me the replacement motherboard from thinkpad forums took of the whitelist before he shipped it. For this reason, if their are any better 3g cards you would recommend over the Sierra MC8755, i will accept them.

If you are not limited by the whitelist, then I'd seriously consider a LTE card instead.  E.g. a Sierra Wireless MC7700/7710/7750 depending on where in the world you are.

I am very happy with the MC7710 I've got in my Thinkpad X301 (which originally had an Ericsson F3507g).  It has three antenna connectors, but can be configured to use only two of them if necessary (using the same antenna for GPS  and MIMO).

---

