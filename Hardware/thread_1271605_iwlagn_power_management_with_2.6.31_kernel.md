---
title: "iwlagn power management with 2.6.31 kernel"
date: 2009-09-21
forum: Hardware
---

### Post by mika91 on 2009-09-21
Hi everyone,

I installed karmic alpha 6 x64 on my laptop.
Everythings seems ok, except wifi power management. Impossible to write in "/sys/class/net/wlan0/device/power_level".

I googled it, and found that support has been disabled temporary. And the solution is to install karmic-backports-modules. 
I did it, but there is no /sys/class/net/wlan0/device/power_level file anymore !!!
How can I solve it please ?

Thanks


(and a bonus question: I migrated from kde, and I'm a litte disappointed with gnome-power-manager. Impossible to edit profiles (cpu scaling, screen dim...) )

---

### Post by DLGandalf on 2009-09-21
try:
$ iwconfig wlan0 power on

word of advice, the backport module is simply put a piece of crap, you connect with highest link speed, but gradually goes down to 1mbit/s. Zo don't even think about getting draft-N speeds.

Check the bug report on launchpad, which probably already found:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/405158](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/405158)

---

### Post by Ayuthia on 2009-09-21
Are you getting anything in /sys/class/net/wlan0?

---

### Post by KMK_ECS on 2009-10-31
Hi,
 
I have the same problem with my Thinkpad T61 and Intel 4965 Wireless after upgrade to Karmic. No matter what I write in /sys/class/net/wlan0/device/power_level, the value remains 0. The alternative does also no work:

$ sudo iwconfig wlan0 power on 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

I found this post: [http://patchwork.kernel.org/patch/46906/](http://patchwork.kernel.org/patch/46906/) which states that powersave was disabled (possibly permanently?) for 4965 in 2.6.32 because of a bug. That explains why power_level is not present anymore with karmic-backports-modules installed.

Unfortunately, without powersaving mode the power consumption of my laptop is 1-1.5 W higher :(. I just need it to connect to slow ADSL routers so I never had problems with powersaving mode.

Does anybody know a solution?

Many thanks 

Karl Martin

---

### Post by PatrickVogeli on 2009-10-31
i had the same problem and I installed the compat-wireless iwlwifi drivers and its working again now. 

[http://linuxwireless.org/en/users/Download/stable/#Stable_compat-wireless_releases](http://linuxwireless.org/en/users/Download/stable/#Stable_compat-wireless_releases)

EDIT: By the way, after installing those new drivers, you activate power management by doing sudo iwconfig wlan0 power on

---

### Post by DLGandalf on 2009-10-31
compat-wireless..

does that install the same iwlagn as linux-backports-modules-karmic contains?
Because installing that package also solves the problem. Although I do doubt the older/newer iwlagn module to be a "better" job performance wise, sometimes there unexplainable long waits while browsing.

---

### Post by KMK_ECS on 2009-10-31
Man thanks for the hint with the compat-wireless iwlwifi drivers! They did not help directly but I found a way to get powersave working! :D

Installing linux-backports-modules-karmic does not help with the 4965 wireless card as powersave was explicitly deactivated for this card in 2.6.32. iwconfig shows the same error message as mentioned in my last post.

However, this is how I got powersave working again:

I downloaded compat-wireless-2.6.32-rc5.tar.bz2 from this page [http://linuxwireless.org/en/users/Download/stable/#Stable_compat-wireless_releases](http://linuxwireless.org/en/users/Download/stable/#Stable_compat-wireless_releases) and extracted the archive. Then, I downloaded the patch to deactivate powersaving on the 4965 from this page [http://patchwork.kernel.org/patch/46906/](http://patchwork.kernel.org/patch/46906/). 

The next step is to remove this patch from the compat-wireless drivers:
```
patch -p1 -R < patchfile
```
Compiling and installation:
```
make
sudo make install
sudo make unload
modprobe iwlagn

```

And powersaving is working again using the following command:
```
sudo iwconfig wlan0 power on
```

Now power consumption with active wlan is back to normal (10-10.5W idle, lowest brightness) on my Thinkpad T61 with NVIDIA card (Bios 1.26).

**However, I take no responsibility for any problems this may cause! Powersaving was deactivated for a reason in 2.6.32.** I have not had any problems so far but I do not need fast transfer speeds.

---

### Post by target1 on 2010-01-29
This is great.   I missed having wireless power saving with 9.10.   With your instructions I have it back.  My x301 is down to 7.5 W.

---

### Post by Wojtek Kinastowski on 2010-02-08
> **target1 said:**
> This is great.   I missed having wireless power saving with 9.10.   With your instructions I have it back.  My x301 is down to 7.5 W.

could you advice any other tricks to get 7.5W on x301.
thanks

---

### Post by target1 on 2010-02-09
> **Wojtek Kinastowski said:**
> could you advice any other tricks to get 7.5W on x301.
thanks

This is all with Ubuntu 9.10, 64 bit.   These are the things I know of:

1) Run powertop:

% sudo powertop

Hit all the keys it suggests to enter various power saving modes.
Powertop will also show if there are processes that are putting the CPU in higher power states.

2) Enable wireless power save:

% sudo iwconfig wlan power on

3) Turn down screen brightness
(Having the screen on full brightness definitely takes more power, but not nearly as much as previous laptops I've had.)

4) Turn off bluetooth

5) Don't do anything CPU intensive!

6) Earlier on I found additional savings by powering off CD drive (make sure it's not mounted).   These seemed to have a pretty good effect, but I really don't understand what undesired consequences there might be.  I haven't done it recently:

% echo 1 > /sys/devices/platform/dock.0/undock

---

### Post by DLGandalf on 2010-02-09
look into laptop-mode

after that, look into it's conf files like, and enable where applicable
/etc/laptop-mode/conf.d

and after that alter /usr/share/laptop-mode-tools/modules/wireless-iwl-power, because it uses a deprecated way of altering power levels. Make a dirty hack so it calls iwconfig wlan0 power on & off. If you're need more detailed info let me know, I've reduced my power usage from ~11W to 6-7W

---

### Post by aboutblank on 2010-03-31
I would like to enable power-saving on my Intel 4965 wifi, but can't:

$ sudo iwconfig wlan0 power on
[sudo] password for user: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

Any ideas?

---

### Post by mihai.ile on 2010-05-18
> **aboutblank said:**
> I would like to enable power-saving on my Intel 4965 wifi, but can't:

$ sudo iwconfig wlan0 power on
[sudo] password for user: 
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

Any ideas?

Yes, the answer is this thread actually. You do have to read it though...

---

### Post by ogoun on 2010-05-27
> **KMK_ECS said:**
> 
**However, I take no responsibility for any problems this may cause! Powersaving was deactivated for a reason in 2.6.32.** I have not had any problems so far but I do not need fast transfer speeds.

Hi, I have iwlagn with iwlwifi-5000 firmware and I was able to turn on power save without a patch. 

Do you know why it was/is disabled and does this also effect my card (WiFi Link 5300)?

---

### Post by ddurdle on 2012-03-07
Does anyone have a link to the patch?  patchwork.kernel.org doesn't resolve and hasn't for months.

---

