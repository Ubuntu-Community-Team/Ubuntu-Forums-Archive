---
title: "Intel 3945 aargh!"
date: 2008-04-27
forum: Hardware
---

### Post by too_tall on 2008-04-27
Hello,

I got tired of booting my BT2 CD every time I had wireless work to do, so I installed Ubuntu 7.10  I was never able to get ipwraw running correctly in that version, but all indicators seemed to say use the new iwlwifi drivers.  I saw that they were to be included with 8.04 so I waited and just installed 8.04.

Now the trouble...

When I use airmon-ng to put my card into monitor mode I get:

```
airmon-ng start wlan0

Interface    Chipset        Driver

wlan0            iwl3945 - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)
```



So now I'm thinking booting from a CD might not be such a big deal...
unless someone here can help?

Thanks in advance.

---

### Post by steveneddy on 2008-04-27
Try installing the backports for Hardy.

```

sudo apt-get install linux-backports-modules-hardy-generic
```

and then restart

---

### Post by too_tall on 2008-04-27
Unfortunately no joy there.  I did the install and no change in the error.

---

### Post by bluewizard on 2008-04-28
This thread is more established. Try the fixes here:
[http://ubuntuforums.org/showthread.php?t=765647](http://ubuntuforums.org/showthread.php?t=765647)

---

### Post by too_tall on 2008-05-02
Thanks for the reference to the other thread, it made me do some other in-depth searching.  Unfortunately that thread does not touch on my issue. My issue was about not being able to put my Intel3945 card into monitor mode nor to do packet injection.  

My problem was caused by my assumption that the new iwl3945 driver would allow packet injection.  I was wrong.  By simply downloading and installing the old ipwraw drivers (as per instructions found all over the place) everything works fine.

Interestingly, when I use airmon-ng to place the wifi0 interface into monitor mode, the system does not seem to see any interface.  Ignoring that, I went ahead and used airodump-ng and was able to see normal wireless traffic.  I used aireplay-ng to inject packets and everything worked great.

Sorry for taking your time with my ignorance.

---

