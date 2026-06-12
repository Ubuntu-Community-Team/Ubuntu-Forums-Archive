---
title: "switch for wireless on Dell M3800 laptop"
date: 2014-09-23
forum: Hardware
---

### Post by rustybutt on 2014-09-23
I'm running 14.04 on a Dell M3800 laptop.  Don't know how it happened, but it appears as if the wireless device is switched off.  Older laptops have a physical switch, but not this guy.  I've been fooling with the function keys, yadda, yadda, with no luck.

Is there a keystroke sequence I'm missing?  Something I should do in BIOS?  A special Ubuntu magic wand you have for sale?

Russ

---

### Post by varunendra on 2014-09-25
I think all Dell laptops have a "Fn+" key combination (probably Fn+F2?) to toggle the wireless state on/off. Please refer to its user manual to be sure. But the function keys should also have relevant icons on them to indicate what they control with "Fn" key.

Also check BIOS to make sure it is enabled from there. If these seem to be okay or make no difference, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by tgalati4 on 2014-09-25
Some wireless chips will shut off it fhe antenna is shorted.  Since it is a thin wire that runs through the hinge and Dell is not known for their robustness, it's possible that you have an antenna problem.  I presume this is dual-boot?  Does it work in Windows?  If so, then it may be a software issue.  If it doesn't work in Windows, then it might be a hardware issue and a Dell RMA is in your future.

In the meantime, open a terminal and post:

```
rfkill list
```

It should look like:

> tgalati4@Mint14-Extensa ~ $ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


---

### Post by rustybutt on 2014-10-01
root@slick:~# rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: nfc0: NFC
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

---

### Post by rustybutt on 2014-10-01
[QUOTE=varunendra;13128958]I think all Dell laptops have a "Fn+" key combination (probably Fn+F2?) to toggle the wireless state on/off. Please refer to its user manual to be sure. But the function keys should also have relevant icons on them to indicate what they control with "Fn" key.

Also check BIOS to make sure it is enabled from there. If these seem to be okay or make no difference, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

I ran the script you suggested, but the output is very large.  Much too large for this forum.  So I uploaded it, along with some screenshots, to my web server.  One of the screenshots is of the network tool and the other two are photos of my BIOS screens, not that I expect them to be of much help, but it couldn't hurt for you to see what I'm seeing.  You can pull everything down from the following links:

[http://www.russbutton.com/tmp/wireless-info.txt](http://www.russbutton.com/tmp/wireless-info.txt)
[http://www.russbutton.com/tmp/network_tool.jpg](http://www.russbutton.com/tmp/network_tool.jpg)
[http://www.russbutton.com/tmp/bios1.jpg](http://www.russbutton.com/tmp/bios1.jpg)
[http://www.russbutton.com/tmp/bios2.jpg](http://www.russbutton.com/tmp/bios2.jpg)

---

### Post by varunendra on 2014-10-01
Your wifi is not blocked at all!

The dmesg part also doesn't show any errors. But the "Tx Power" being '0' in "iwconfig" part makes me think if it could be an antenna problem.

If the wireless card is in a user-accessible area (usually under a removable panel at the bottom of the laptop), please check its antenna contacts. If that is okay, maybe try resetting your BIOS to factory defaults.

---

### Post by rustybutt on 2014-10-01
I'll take it down later today and will report back.  Sad to see that it's likely a physical problem.  There is a bottom panel, but it just gives you access to screws.  I'll probably have to pull the bottom case cover off.  I think the wireless card is in one corner of the chassis.

---

### Post by rustybutt on 2014-10-03
I tried to pull the bottom cover off of my Dell, but the screws have the smallest damn Torx heads I've ever seen.  I got a torx head screw driver I thought would work, but it looked like it was stripping the head, so I stopped.  The damn thing is still under warranty from Dell, so I figured I might as well exercise it.  It was delivered as a Windows machine and has 2 drives in it - an SSD and a 500G spinning drive.  I loaded Ubuntu on the spinning drive and left Windows on the SSD, thinking that there might actually come a time when it would be useful.  Dell wants to run diagnostics on a machine before swapping it out, so I booted into Windows.  Lo and behold, the wireless connection worked fine!

So this is *NOT* a physical problem at all.  Booting back into Ubuntu, the wireless connection hasn't changed.  It still acts like it's not there.  Most annoying!

---

### Post by weatherman2 on 2014-10-03
You have an Intel 7260 wireless card, according to your wireless-info.txt output.

This card is known to be especially problematic in Linux.  Even Windows users can have issues with it, apparently:

[http://askubuntu.com/questions/504695/im-unable-to-get-intel-7260-iwlwifi-to-work-kubuntu-14-04](http://askubuntu.com/questions/504695/im-unable-to-get-intel-7260-iwlwifi-to-work-kubuntu-14-04)

---

### Post by rustybutt on 2014-10-03
> **weatherman2 said:**
> You have an Intel 7260 wireless card, according to your wireless-info.txt output.

This card is known to be especially problematic in Linux.  Even Windows users can have issues with it, apparently:

[http://askubuntu.com/questions/504695/im-unable-to-get-intel-7260-iwlwifi-to-work-kubuntu-14-04](http://askubuntu.com/questions/504695/im-unable-to-get-intel-7260-iwlwifi-to-work-kubuntu-14-04)

It's a company owned laptop, so I can't exactly send it back to Dell whining about how it doesn't work with Ubuntu.   The article you reference suggests that going to the 3.15 kernel fixes the problem.  I may have to look into that.

pbffftttt...

---

### Post by varunendra on 2014-10-03
Please just run an update and see if it can improve things -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

The card itself is a good one, whatever problems occasionally occur with it are almost always caused due to the rapidly changing driver/firmware combination. It is one card whose firmware is changing rapidly, some combinations work better than the others, and some don't work at all! [This table]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm") shows only upto version 22.15.8.0 available, while we know that upto version ..9.0 is out.

You seem to be using version ..8.0 which is what usually works the best, may be a driver update is all you need?

If it remains the same after a kernel upgrade (the default one is now 3.13.0-36 or 37), please post a fresh wireless_script report.

---

### Post by rustybutt on 2014-11-03
I finally got this figured out.  There was a file in /etc/modprobe.d/ that was blocking the wireless card.  That file was:

/etc/modprobe.d/iwlwifi.conf

I did the following:

cd /etc/modprobe.d/
mkdir tmp
mv iwlwifi.conf tmp
init 6

That got everything working.  I'd love to know why the damn thing was there in the first place.

---

