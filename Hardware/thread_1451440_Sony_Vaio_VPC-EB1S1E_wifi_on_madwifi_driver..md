---
title: "Sony Vaio VPC-EB1S1E wifi on madwifi driver."
date: 2010-04-10
forum: Hardware
---

### Post by ultiva on 2010-04-10
Hello !
I've managed to compile madwifi driver with patches to support ar9285 on ubuntu 9.10 32bit.

Wifi seems to be much more reliable now, and quite fast - 2.7-2.8 MB/s. (on Win7 2.9-3.1MB/s)

Problem is I have strange errors in dmesg on this madwifi driver
[http://sonylaptop.sikorski.org.pl/dmesg_madwifi_err.txt](http://sonylaptop.sikorski.org.pl/dmesg_madwifi_err.txt)
(at the very end of the file)

I don't know if it's a real problem coz as I said - wifi works fast and quite stable. Just TX power can be set up max to 14dBm on this driver, when on ath9k it is set to 20dBm.

If someone is interested in how to compile madwifi I'll post details.

Regards
Piotr Sikorski

---

### Post by Cuppa-Chino on 2010-04-11
yes I also have atheros, I use the out of the box driver on Lucid - I did not compile anything, so the ath9k, let me do some digging on the issue

btw ath9k driver should be karmic as well, why did you compile madwifi ?

---

### Post by ultiva on 2010-04-11
Hello. Thank you for reply.
I have serious problem with ar9285 on ath9k driver on karmic as well as on lucid livecd.

I have compiled ath9k driver from sources bleeding edge and even installed ndiswrapper + winxp driver 7.7.0.

Symptoms are: wifi transfer is frequently interrupted, but wifi link is not disassociated (downloading just stops and waits for some time then it resumes and then stops again). Download speed over LAN (between stops) also is not very good (about 60% Win7 speed). I tried almost everything 
- oob ath9k from karmic and lucid
- ath9k from karmic backports
- ath9k from sources
- ndiswrapper driver
- different AP settings (encryption, preamble, txpower) - AP is linksys wrt54gl + tomato 1.27 VPN 
- tried three diffrent APs at two different locations
- disable BT
- wicd instead of network-manager
NONE OF THESE WORKED

It looks for me like some kind of interference - one time it's better, stop are less frequent, another time wifi is barely usable and nothing can be downloaded. But if it's interference - why on Win7 there are absolutely no problems with wifi.

Then I enabled debug for ath9k but there were no errors in dmesg nor in /var/log/messages.

And then I tried to compile madwifi driver (svn) with patches for ar9285 (ported from freebsd) - wifi speed and reliability improved dramatically, transfer is stable, speed is good (>90% of Win7 speed). Just noticed these stange errors in dmesg and weird info returned by iwconfig.

Ps. There is another guy who has same symptoms, he also haven't found solution.

EDIT:
I edited madwifi source and disabled device reset on this ath_fatal_tasklet event. Unfortunately it causes device lock-up on random occasion. Looks like this reset keeps wifi link "in one piece" on madwifi but transfer is still failing due to some reasons.

EDIT2:
When I set ratectl to onoe on this madwifi driver, download speed over LAN (wget) is blazing fast - 3.2MB/s and very stable. Unfortunately ath_fatal_tasklet still show up in logs.

EDIT3:
Hmmm it looks like the problem might be related to HAL...

---

### Post by ultiva on 2010-04-12
Compiled madwifi on lucid beta 2 livecd with 2.6.32-19-generic. Wifi is stable with this driver and there are no ath_fatal_tasklet errors. Transfered several GBs and wifi works flawless with ath_pci. Unfortunately ATH9K is STILL FAILING. God bless madwifi team and the hacker who ported ar9285 support :twisted:

I'm willing to help debug this flaw in ath9k but don't know what test should I do.

---

### Post by Cuppa-Chino on 2010-04-16
ok so you are happy with the madwifi, good!

now can I ask what network protocoll and encryption method you are using?

I struggle when I set my router to N-Mode with ath9k in G-Mode its all fine. I have also noticed that in N-Mode the driver/applet does not show link speed, whereas in G-Mode I can always see link status.

Encryption is WPA2 in all my cases, maybe I should also "upgrade" to madwifi for N-Mode.

thanks

---

### Post by ultiva on 2010-04-16
Unfortunately madwifi+ar9285 patch supports only G-mode for now. I use G-mode WPA2-PSK/AES.

Ps. "HAPPY" is to big word. Madwifi has some issues - signal is week (40-60%), upload is slow and very dependant on laptop position. But at least it works and wifi is usable, however cannot be compared to how it works under Win7 (flawless download, fawless upload and signal strength 90-100%). Week upload on madwifi might be related to the fact that txpower cannot be set > 14dBm. On ath9k it can be set to 20dBm.

I think that ath9k problems might be related that I'm in veery wifi polluted enviroment. Sometimes >20 networks can be seen. Look like ath9k does not work very well in such enviroment.

---

### Post by sertaconal on 2011-01-23
It's worked!! but i have an another compat pack.
My System is Sony Vaio VPC EB1S1E and i have 2.6.32-27-generic..
Wireless : AR9285..
First of all download " [compat-wireless-2.6.35-rc2.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.35/compat-wireless-2.6.35-rc2.tar.bz2") " and copy / paste your Desktop..
After THERE WRITE IN TERMINAL step by step
```

cd Desktop
tar -xf compat-wireless-2.6.35.rc2.tar.bz2
cd compat-wireless-2.6.35.rc2
make
sudo make install
sudo unload

```i hope it'll fix your problems.. almost work like win7's performance

---

