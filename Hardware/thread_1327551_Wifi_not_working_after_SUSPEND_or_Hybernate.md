---
title: "Wifi not working after SUSPEND or Hybernate"
date: 2009-11-15
forum: Hardware
---

### Post by manolomanolo on 2009-11-15
Hi to all.

My **wireless card** is not able to connect to any (protected or unprotected) netword after resuming the system in case of **SUSPEND** or **HYBERNATE**. I had the same problem in Jaunty as now in Karmic. The problem persists when using **Network Manager** or **WICD**.

I notice that (not in case of SUSPEND or HYBERNATE) turning the wifi off and then on doesn't cause the problem. I mean, everithing works perfectly in case of deactivating wireless using WICD or pressing the wireless button of my **Acer Aspire 5730z**, when not resuming my system from a SUSPEND or HYBERNATE condition.
On the other hand, in case of having resumed the system after SUSPEND or HYBERNATE, I see that even disabling/enabling wireless make it work. Nor logging off and back on the current user.

Any suggestion please?
Thanks.

```
lspci | grep Wireless
03:00.0 Network controller: **Atheros** Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

```
lsmod | grep ath
ath9k                 258744  0 
mac80211              181236  1 ath9k
ath                     8060  1 ath9k
cfg80211               93052  3 ath9k,mac80211,ath
led_class               4096  2 ath9k,acer_wmi
multipath               7744  0 
```

Ubuntu Karmic Koala - kernel 2.6.31-14-generic

---

### Post by manolomanolo on 2009-11-16
Up!

---

### Post by blindeinstein on 2009-11-16
I have the exact same issue. When resuming from suspend I can't even detect any wireless networks.

---

### Post by manolomanolo on 2009-11-16
Hi blindeinstein.

Could you please paste the output of those commands of above and paste the informations about your system as I did above?
Also, is your problem new or (as in my case) persisting from previous versions of Ubuntu?

Thanks for your time.

---

### Post by cespinal on 2009-11-17
bump... Have been having this issue since de last version of ubuntu...

under WICD, the systems fails to connect after waking from suspend. under Network Manager, the networks are found, but the bit rate is ridiculously slow...

---

### Post by vtanger on 2009-11-17
having the same problem. wicd wont detect any wireless after suspend or hibernate.
im running karmic with atheros wireless card.
any help would be appreciated.
already tried editing /etc/default/acpi-support/ to say
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"

wont do the job..

---

### Post by blindeinstein on 2009-11-18
```
lspci | grep Wireles
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

```
lsmod | grep ath
ath5k                 124260  0 
mac80211              181236  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
led_class               4096  2 ath5k,sdhci
```

For me it's a new problem since I upgraded to Karmic from Jaunty.

---

### Post by manolomanolo on 2009-11-18
Strange things happen in the Karmic world.

Now I'm able to connect to wireless lan after resuming from Suspend.

I changed nothing related to wireless since my last post. Also, there's been no Ubuntu updates related to network connection, AFAICR.

Hope the problem has been solved for Hybernating too.
Hope the problem has been solved for you all too.

Stay tuned!
*Nam myoho renge kyo* ;)

---

### Post by manolomanolo on 2009-11-18
As a result of my tests, the problem has been solved as for Suspend.
On the other hand, my system is now unable to Hybernate at all or at least it would probably take a longer time than expected... but I don't know because I have not been waiting so much.

---

### Post by manolomanolo on 2009-11-20
bump

---

### Post by blindeinstein on 2009-11-25
The issue seems to be fixed with the latest update. Anyone else's problem corrected?

---

### Post by blindeinstein on 2009-11-26
Scratch that. Just had the problem reoccur. grr....

---

### Post by anlazarov on 2011-06-25
So what do we do? Anyone found a solution. I installed Natty yesterday.... and still have problems with my wireless after suspend. I simply doesn't work!

```

lspci | grep Wireless
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

```
lspci | grep Wireless
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

---

### Post by puca mor on 2011-09-21
*bumpy*

This problem continues to plague me (hyperbole) from lynx to natty... I have tried a great many lines of code in an attempt to restart the networking without rebooting - but no luck so far. 

Last attempt was 

```
/etc/init.d/networking stop
```

That seemed to suggest it had stopped the networking - but when i tried the same again with start it seemed to say the networking was stop/waiting?


I wonder if this is a problem?

```
 lsmod | grep 819
r8192se_pci           482505  0 
cfg80211              156212  1 r8192se_pci
r8192e_pci            251260  0 
```

Well, if anyone has any further ideas... ):P

```
lspci | grep Wireless
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)

```

---

