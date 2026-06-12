---
title: "Does Jaunty support wlan ralink rt2870?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by AlanRick on 2009-04-23
Hi,
It took a fair amount of work to get my logilink wlan usb-stick working on 8.10.
Does 9.04 include a driver for  ralink rt2870 or would I have to go through that all again?

Plea: Hope it does - wlan is one of the most important aspects of ubuntu for many. Once you get that working you can install updates for everything else easily.

---

### Post by velislavv on 2009-04-23
> **AlanRick said:**
> Hi,
It took a fair amount of work to get my logilink wlan usb-stick working on 8.10.
Does 9.04 include a driver for  ralink rt2870 or would I have to go through that all again?

Plea: Hope it does - wlan is one of the most important aspects of ubuntu for many. Once you get that working you can install updates for everything else easily.
I think Ubuntu 9.04 includes drivers for rt2870, but if it dosent, see this it can help you [http://ubuntuforums.org/showthread.php?t=766850]("http://ubuntuforums.org/showthread.php?t=766850")

---

### Post by jimbob on 2009-04-23
Take a look at /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

If you have it, that is the driver you need.

---

### Post by AlanRick on 2009-05-17
I did a fresh jaunty install and it did support the ralink rt2870 after all. However there seems to be a bug (reported in another thread) that the 802.11n is not suppported since only 54MB/s is reached. (tracked as Bug #377745)

---

### Post by jimbob on 2009-05-17
I don't know if that could be classified as a bug since as far as I know the 802.11n standard is not yet finalized.

What is the link to the thread you found?

---

### Post by AlanRick on 2009-05-18
> **jimbob said:**
> I don't know if that could be classified as a bug since as far as I know the 802.11n standard is not yet finalized.

It's still draft but since the ralinktech driver does support more than 54Mb/s then the jaunty kernel version should too.

I thought the minor problem worth logging but if you think it's not useful I'll close the bug. 

> **mizunoX said:**
> I'm having the same issue with a ralink 2870 and a fresh Jaunty install.
It finds the card and works without any additional driver compiling/installing however it maxes out at 54Mb/s.   I achieved much higher with the same card and Intrepid (though I had to compile and install a driver as above)

-- EDIT -- I followed someone else's instructions to download the new ralink driver from their website: [http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz]("http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2870_Linux_STA_V2.1.1.0.tgz")
Extract to a folder, enter the folder and 'sudo make', 'sudo make install', reboot and voila.  It's connecting to 5Ghz networks at 300Mb/s.


The main thing is the chip is recognized in jaunty which is a huge step forward :-({|=

---

### Post by chitowner2 on 2009-09-04
> **jimbob said:**
> I don't know if that could be classified as a bug since as far as I know the 802.11n standard is not yet finalized.

What is the link to the thread you found?



JIMBOB-

Any ideas how to get WIDC to apply the rt2870 driver and get it to recognize a USB device so that WLAN can be established?

Thanks!

---

### Post by jimbob on 2009-09-04
> Any ideas how to get WIDC to apply the rt2870 driver and get it to recognize a USB device so that WLAN can be established?


Do you mean WICD?  I don't know anyone who has done that.  If you have the driver built and installed and it works with Network Manager then it would be easy to install Wicd (which if I recall automatically removes NM during the installation) and give it a try.  You can always go back the other way.

---

### Post by AlanRick on 2009-09-11
> **jimbob said:**
> I don't know if that could be classified as a bug since as far as I know the 802.11n standard is not yet finalized.


Rumor has it that 802.11n has [now been finalized]("http://s2n.merunetworks.com/2009/09/802-11n-approved-official-notification/") :D

---

