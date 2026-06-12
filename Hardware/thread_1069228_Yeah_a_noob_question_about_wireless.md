---
title: "Yeah a noob question about wireless"
date: 2009-02-13
forum: Hardware
---

### Post by XRichX on 2009-02-13
Hello all,

I'm so gonna get shot down for this lol, but I only use the forums to bug you all as a last resort, and I am just about ripping my hair out at the minute. I am trying to get Ubuntu fully working on the v5535, the only two things I am facing is the wireless and graphics (being stuck at 800x600) on Fujitsu Siemens v5535.

I know the graphics is able to go to 1024x768 within the 8.10 version of Ubuntu, but I have only got a 8.04 at hand so after I get the wireless sorted I'll upgrade :)

As for the wireless (Atheros AR5007EG), I have read all over the forums but just can't get anything to work, I try searching for ath5k but can't find it in Synaptic Manager. I also try to locate a wireless driver for ndiswrapper but they are all .exe's. It has 2 drivers being used within the restricted drivers manager, but I doubt they are doing anything as the wireless isn't working lol.

Can someone point to me as to how to install the ath5k or better yet know to hand where the windows drivers are that arent a .exe?

Thanks very much.

---

### Post by Monster_user on 2009-02-13
> **XRichX said:**
> Can someone point to me as to how to install the ath5k or better yet know to hand where the windows drivers are that arent a .exe?

Thanks very much.

For the *.Exe versions, you could install them in Wine, then use Ndiswrapper to load the INF file.

I'm thinking the wireless adapter should work with Ubuntu 8.04. Which kernel are you booting from?

```


sudo uname -r


```

See if the driver is already installed.

```
 sudo lsmod

sudo lsmod | grep ath


```
Have you tried using the console commands to set the wireless settings?

```


sudo iwconfig wlan0 essid XXXXXXX key 0000000 mode managed

sudo dhclient wlan0


```

Perhaps that will help. replace the X's with your router's ESSID, and the 0's with your WEP/WPA key.

---

