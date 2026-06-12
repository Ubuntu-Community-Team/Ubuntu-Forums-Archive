---
title: "No intel pro 2200bg support for wifi auth in 12.04?"
date: 2012-04-06
forum: Hardware
---

### Post by jcwilk on 2012-04-06
Hey all,

Relatively experienced linux user here, not so much in debugging low level driver issues.

So the issue I'm having is that I'm running the beta2 release of 12.04 xubuntu, and in both the xfce and xubuntu environments I'm not able to connect to a password protected AP. Unprotected works fine, but whether it's WEP, WPA, WPA2, no dice. It displays all the APs fine in the network manager dropdown, though anything above WEP (ie, WPA/WPA2) makes the name grayed out (never seen this before and been using xubuntu/ubuntu for quite some time) and you can't select it to connect. If you try to connect to a WEP it brings up a prompt: "Authentication required by wireless network    Passwords or encryption keys are required to access the wireless network '<ap name here>'."  with two options, cancel or connect... Except connect is grayed out. Very strange.

I realize this is a beta release, but because it's all grayed out rather than throwing some bogus error I thought maybe I had a setting wrong somewhere that's preventing me from using authenticated wifi.

Here's a bit of info to provide some background, please feel free to request further info as needed, and any help is greatly appreciated in advance.

```
$ lspci | grep net -i
01:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
``````
$ modprobe -l | grep ipw
kernel/drivers/tty/ipwireless/ipwireless.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/usb/serial/ipw.ko
```Not sure where to go from here, I failed to find any info via searching about grayed out APs or what that means, this all worked just fine in 11.10 and I'll probably revert back to that if you guys don't have any ideas, would be nice to get a head start on the LTS though.

---

### Post by ahallubuntu on 2012-04-06
Please file a bug.  The purpose of these pre-releases is to find bugs before the releases.  It may already be filed.  If not, the longer people wait to file bugs, the longer it will take for them to be fixed.

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by Boogerhead on 2012-04-09
> **jcwilk said:**
> Not sure where to go from here, I failed to find any info via searching about grayed out APs or what that means, this all worked just fine in 11.10 and I'll probably revert back to that if you guys don't have any ideas, would be nice to get a head start on the LTS though.

I was using 11.04 for quite a while, and in the last two days upgraded through to 12.04b2. The BG2200 card was working fine, but I noticed in the network manager applet that it didn't know what it was connected to. So I disconnected ... and now I can't get back in, similar problem as you. I can see about 8 other networks in my neighborhood, and it'd only let me connect to 3 of them, so I think this is an encryption problem.

There's lots of stuff in the bug tracker archives suggesting similar (albeit largely uncured) problems with the BG2200. I don't know if downgrading, then, would necessarily fix our problems.

I'll file a bug report. Hope for the best.

Edit: Filed. [https://bugs.launchpad.net/ubuntu/+bug/977688](https://bugs.launchpad.net/ubuntu/+bug/977688)

---

### Post by Boogerhead on 2012-04-16
This was patched (via network manager) a couple days back. Amazing.

---

### Post by Carambakaracho on 2012-05-06
Hi there, 

The fix didn't help me. The card is detected, same output on lspci and modprobe -l like above, but "enable wireless" remains grayed out.

Most recent updates are installed. This card was ever detected since 5.10 and I never had any problems (except the light wasn't working until 8.04)

Someone's experiencing the same problems and found a workaround?

Thanks, help is really appreciated.

```
lspci | grep -i wireless
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

```
modprobe -l | grep ipw
kernel/drivers/tty/ipwireless/ipwireless.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/usb/serial/ipw.ko
```

---

### Post by WestWallPoma on 2012-05-06
Same issue here - installed 12.04 Desktop on my Vaio VGN-BX297XP ; Intel 2200BG worked fine during console-based install, but now fails to function.

Noticed a few others having these issues, so decided to check for similar issues with 11.10:

[http://ubuntuforums.org/showpost.php?p=8650466&postcount=15](http://ubuntuforums.org/showpost.php?p=8650466&postcount=15)

The above link seems to have the answer - so try this before adding to your rc.local

```

sudo echo 100 > /sys/class/firmware/timeout 
sudo rmmod -f ipw2200 
sudo modprobe ipw2200

```

Magic should happen and network manager will now show your WLAN SSIDs.

Cheers,

-Gregor-

---

### Post by Carambakaracho on 2012-05-07
So, while I was writing a reply complaining nothing works - and while I traced back my command to show I really tried everything I figured I did everything - just not in the right order.

So, after hours of trial and error - most likely the following sequence turned out to solve the problem:
Installing network-manager version 0.9.4.0-0ubuntu4 and kernel 3.2.0-24.38 from precise-proposed update repository (activated via synaptic-package-manager).

Then I figured the damn wireless was all blocked
```
sudo rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
```

Allright, pushing the button didn't change anything until 
```
sudo rfkill unblock 0
sudo rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
```
now the button gained function but it was not yet working
```
sudo rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
```
So, I repeated the command above
```
sudo rfkill unblock 0
sudo rfkill unblock 1
sudo rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

And finally it's working!!!

Bye the way, installing linux-backports-modules-wireless-precise-generic didn't help anything.

---

