---
title: "Dell Precision M4800"
date: 2014-08-08
forum: Hardware
---

### Post by nuts2 on 2014-08-08
I am running 14.04 with all the latest updates. So far I have tried the wifi and the bluetooth and neither of them work. I loaded the driver for the wifi using the native additional drivers app that comes with the OS. I can see AP's but when I attempt to connect to them it fails every time. Same thing happens with bluetooth I can see the devices and it will try to pair them but it always fails. For right now I am using a wired connection and a USB bluetooth dongle so I am operational but I would like to use the wireless and built in bluetooth. This laptop runs Ubuntu really well and it is super fast but not being able to use all the hardware is bothering me. Are there any other M4800 owners out there?

My config...
i7 CPU
32Gb of memory
nVidia graphics
512Gb SSD

---

### Post by ibjsb4 on 2014-08-09
A suggestion

Your title does not describe your problem.  Maybe change it to inform readers this is a wireless problem.

And then, click on the report post button (bottom right, in your post) and ask that your thread be moved to the network/wifi sub forum.

That should pull in the wifi troubleshooters.

Good luck :)

---

### Post by nuts2 on 2014-08-09
> **ibjsb4 said:**
> A suggestion

Your title does not describe your problem.  Maybe change it to inform readers this is a wireless problem.

And then, click on the report post button (bottom right, in your post) and ask that your thread be moved to the network/wifi sub forum.

That should pull in the wifi troubleshooters.

Good luck :)

Those are all good suggestions and I appreciate the feedback but this thread isn't just about wireless. I opened this thread to talk to other M4800 owners that are using Ubuntu and I figured I would start it by mentioning the wireless issue. The thread is really intended to cover anything dealing with running Ubuntu on the M4800 however I will keep your recommendations in mind with all future posts. I am a long time user and poster but I lost access to my original account and that is why I am posting under the nuts2 nickname instead of my original nickname which was nuts.

---

### Post by ph-h on 2014-08-13
Hello,

I'm the owner of a Dell M4800 (i7, 32gb,...) since January 2014. Dual boot win8 and Ubuntu 13.10 later upgraded to 14.04.

I never managed to make Wireless nor Bluetooth work !  Same problems as described above:  I can see the wireless network but can to authenticate a connection to it.

Pairing Bluetooth devices fails as well.

No problems with ethernet connections.

I tried all the solutions found on the forums, it never worked.

So (shame on Dell and/or Ubuntu) I need to use Win8 to use the wifi.

Hope this helps.

---

### Post by ph-h on 2014-08-13
Found this : 
_[COLOR=#800080][http://ubuntuforums.org/showthread.php?t=2229472&highlight=m4800](http://ubuntuforums.org/showthread.php?t=2229472&highlight=m4800)[/COLOR]_

Broadcom made new drivers in June 2014 :

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by nuts2 on 2014-08-13
> **ph-h said:**
> Found this : 
_[COLOR=#800080][http://ubuntuforums.org/showthread.php?t=2229472&highlight=m4800](http://ubuntuforums.org/showthread.php?t=2229472&highlight=m4800)[/COLOR]_

Broadcom made new drivers in June 2014 :

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Have you tried the newer driver yet?

---

### Post by ph-h on 2014-08-19
Yes.

I followed the README.TXT from [http://www.broadcom.com/docs/linux_sta/README_6.30.223.248.txt](http://www.broadcom.com/docs/linux_sta/README_6.30.223.248.txt)


So, I first did an update of the driver : 
 [I]sudo apt-get update
 sudo apt-get --reinstall install bcmwl-kernel-source

[/I]It didn't fix it for me (it is not the latest driver as you can dowload it from the link above) but you can always try.

So 

1. I unpacked the last driver 
2. I run the *make *commands which gave me some Warnings but I continued
3. I followed the readme.txt and did this :

# rmmod wl 
Did a find on all wk.ko on my computer and renamed all (except the newly created by the makefile)
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

Got some errors so I did this :

[I]# rmmod wl

[/I]and run (from the place where I copied the new wl.ko file):
[I]# modprobe cfg80211

Then:
# insmod wl.ko

[/I]After a reboot of my machine and could activate wireless from the network icon (desktop right upper corner), and could connect to my private (wpa/wpa2) network with password.

---

### Post by ph-h on 2014-08-20
I did some tests yesterday and the network performances are not as good as under Win8.

Loosing sound randomly.

Need more investigations.

---

### Post by nuts2 on 2014-09-02
> **ph-h said:**
> I did some tests yesterday and the network performances are not as good as under Win8.

Loosing sound randomly.

Need more investigations.

Sorry I have been away for a while and haven't been able to respond. I am going to try that other Broadcom driver you pointed out today and I will report back here with the results.

Have you tried the latest nVidia driver version 340.32 yet? I am still running the 331.38 driver from the additional drivers utility and I am curious if the new driver is any better.

---

### Post by bananax1822 on 2014-09-17
Just wanted to mention that ph-h's fix above fixed the issue for me.

Wifi hasn't worked on my M4800 with Ubuntu 14.04 since I got the laptop. I spent some time trying to fix the issue a few months ago but none of the suggestions on other threads worked. I even tried the broadcom drivers (before the new ones were released). Finally got everything working just now by running the make steps above for the drivers on [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by nuts2 on 2014-09-17
> **bananax1822 said:**
> Just wanted to mention that ph-h's fix above fixed the issue for me.

Wifi hasn't worked on my M4800 with Ubuntu 14.04 since I got the laptop. I spent some time trying to fix the issue a few months ago but none of the suggestions on other threads worked. I even tried the broadcom drivers (before the new ones were released). Finally got everything working just now by running the make steps above for the drivers on [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The driver did work for me but the connection still isn't stable. I can connect but after a while the connection drops and sometimes it will reconnect but most of the time it won't.

---

### Post by augusto.sisa on 2014-09-25
Hi ph-h,

I'm interested in buy a Dell M4800 with two drives one of 8GB SSD and other of 1TB HDD. I want to ask you if there has been any further problem with this system and dual boot? 

Thanks in advance.

---

### Post by nuts2 on 2014-09-27
> **augusto.sisa said:**
> Hi ph-h,

I'm interested in buy a Dell M4800 with two drives one of 8GB SSD and other of 1TB HDD. I want to ask you if there has been any further problem with this system and dual boot? 

Thanks in advance.

Other than the WLAN being unreliable and the Bluetooth not working it runs Ubuntu really well.

---

### Post by ph-h on 2014-10-17
I totally agree ! 

Althrough I tought that the problem was solved, I can not longer use the WLAN and I had to buy a new mouse.  I will buy a portable wifi adapter and connect with Ethernet on it.

Install of Ubuntu alongside Win8 is tough but not impossible.

Anyway, M4800 is a great laptop.

---

