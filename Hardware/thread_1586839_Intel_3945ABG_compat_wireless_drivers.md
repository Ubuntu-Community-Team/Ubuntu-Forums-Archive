---
title: "Intel 3945ABG compat wireless drivers"
date: 2010-10-02
forum: Hardware
---

### Post by Bodwin on 2010-10-02
Hi everyone.
I have a HP 550 laptop with a Intel Corporation PRO/Wireless 3945ABG wireless adapter. I was (and still am) having some problems with aircrack-ng. Basically my card was monitoring the wrong channel (-1) whatever I tried. Anyway, I found a solution somewhere that I need to install compat wireless driver from source but first patch it with a certain patch I already have. When I installed the compat drivers my computer did not recognize my wireless card anymore. I could successfully uninstall them and get the wireless working, however, the former problem is still there.
I downloaded the compat-wireless-2.6.35-1 drivers.
Then I executed ```
./scripts/driver-select intel
```
After that ```
make
sudo make install
sudo make unload
```
Ubuntu replied
 ```
Stoping bluetooth service..
 * bluetooth is not running
Unloading iwl3945...
FATAL: Module iwl3945 not found.
Unloading iwlcore...
FATAL: Module iwlcore not found.
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
Unloading bluetooth...

```
After restarting there are no wireless networks in the network manager and I can't do ifconfig wlan0 up - as far as I remember it said it didn't exist.
 Please tell me what other info do you need to help me and what am I missing. Right now I think I have more modules than necessary loaded in my system (even if I do make uninstall). That's because I think I messed something up the first time I tried to install the drivers.

---

### Post by echo6 on 2010-10-02
Try patching the compat wireless drivers with [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)

Also look at [http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

Unfortunately I've moved to 2.6.35.7 kernel, but having another issue which appears to be related to this which I'm trying to track down :-(

---

### Post by Bodwin on 2010-10-03
Hi again.

> Try patching the compat wireless drivers with [http://patches.aircrack-ng.org/chann...ne-maxim.patch](http://patches.aircrack-ng.org/chann...ne-maxim.patch)

Yes this is the patch I used on the source so that I will no longer have the problem with channel -1. I took a look at the link you gave me but it is for different wireless cards and I am not sure which steps are relevant to me.

Here is a full account of what I did. I hope it helps you figure out what went wrong.

I downloaded and untared [HTML]http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-02.tar.bz2[/HTML]
I patched successfully the chan.c file. Then I did: 
```
scripts/driver-select intel

Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
```

I assume that went well. After that:
```
make
```
The output is too big so I uploaded two files called make1 and make2(I had to split them up because they were 19.7kb and the forum allows only 19.5 (*,) )

```
sudo make install
```
And again the output is in install1. After that following the instruction for the installation I did sudo make unload and sudo make load. The unload&load file has the output.

So basically, after all that I end up with my computer not recognizing my wireless card. Or at least when I do
```
sudo ifconfig wlan0 up
```
It says:
```
wlan0: ERROR while getting interface flags: No such device
```

---

### Post by Bodwin on 2010-10-05
Bump

P.S. How many bumps am I allowed before you guys get pissed off?

---

### Post by soad6 on 2010-10-16
are you sure that the card is set to wlan0? maybe its not or maybe its drivers were removed because of this being done? these are the only two things i can think of at the moment. I'm trying to fix the negative one channel issue myself also.

---

