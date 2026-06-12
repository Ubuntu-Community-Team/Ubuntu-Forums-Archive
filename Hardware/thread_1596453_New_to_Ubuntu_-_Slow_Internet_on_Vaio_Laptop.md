---
title: "New to Ubuntu - Slow Internet on Vaio Laptop"
date: 2010-10-14
forum: Hardware
---

### Post by steel_rose on 2010-10-14
Hi,

I'm completely new to Ubuntu but so far I'm really enjoying it, there are just a couple of things that are not working well yet.
I installed Ubuntu 10.10 on a Vaio VPCEB1EOE on Monday next to Windows 7 (dual boot).

My laptop connects to the internet very quickly as soon as it's switched on, but the connection is very slow... watching clips on Youtube is painful and even just accessing a Hotmail account takes a very long time.
To check if it was a provider problem, I tried to restart my machine with Windows 7, but on that OS the internet is as speedy as usual.

I had a look around for advice and read somewhere that UbuntuOne might slow your connection down, so I took it away from the "startup applications" list, but there was no visible improvement.

Does anyone have any suggestion?

Thank you very much for your help,

SR

---

### Post by coffeecat on 2010-10-14
Let's see what network chipset and driver you are using. Open a terminal (Applications > Accessories) and post the output of this command:

```
sudo lshw -C network
```It will prompt you for your password. You won't see any feedback as you type it in, but it is going in. When you post the output, please enclose it in [noparse]```

```[/noparse] tags. You can do that by highlighting the output in the message field and clicking on the # icon just above the message field.

---

### Post by steel_rose on 2010-10-14
Hi Coffeecat,

Thank you very much for your response!
I used the command you suggested, the output I received is this:

```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 2c:81:58:f6:c0:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f4c00000-f4c0ffff
  *-network
       description: Ethernet interface
       product: 88E8059 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 11
       serial: 00:24:be:bf:d5:bf
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f2420000-f2423fff ioport:b000(size=256) memory:f2400000-f241ffff

```

I hope this helps...
Thanks again!

SR

---

### Post by coffeecat on 2010-10-14
I should have asked whether the problem was with the wireless connection or the ethernet, but I'll assume it's the wireless. This is your wireless chipset and driver:

> **steel_rose said:**
> product: AR9285 Wireless Network Adapter (PCI-Express)

...

driver=ath9k

I'm posting from 10.10 on a laptop that uses the AR928X chip with the ath9k driver. I'm getting good G speeds. However, my router is N-capable but I switched it to G because one of my laptops (I can't remember which) didn't perform well when I had the router set to N. But this was with Lucid (10.04) which may have  had earlier versions of the wireless driver.

First thing to check: look for the Network Manager icon on the upper panel towards the right. It should be next to the volume control icon. Right-click on it and select 'Connection Information'. What speed does it show?

Next - if you are using a N-capable router, try configuring that for 802.11g only. See if that makes a difference. I know that G speeds are slower than N, but some Linux wireless drivers have been troublesome (at least in the past) with the N protocol. That's why I switched to G, but I can't remember whether it was this Atheros chip or the Intel in my other laptop that was the problem.

I don't think it's a particularly good solution to backtrack to 802.11g but let's see what your situation is before we investigate this further.

What is your router, by the way? Do you know whether it's N-capable?

---

### Post by steel_rose on 2010-10-14
I went to check the connection speed and I noticed something interesting: it was saying 135 Mb/s, then it suddenly switched to 1 Mb/s... after a few seconds it switched back to 135, then 1 and so on... I couldn't see a pattern in the intervals between the two speeds, they kept on randomly alternating.

My router seems to be bg certified, I should have a couple of other routers somewhere in the flat (not sure about their capabilities), if you think that it's a good idea I can look for them and try to set them up somehow.

Thank you very much for your kind help,

SR

---

### Post by coffeecat on 2010-10-14
If you are getting 135 Mb/s then your router is N-capable. G speeds are a maximum of 54. I should imagine the "bg certified" simply means it's backwards compatible with the earlier standards - which it ought to be anyway.

This may or may not signify anything at all, but I tried switching my router back to N and I'm now getting a steady 150 MB/s (the maximum for this router - more expensive ones give you 300) with my laptop only 1-2 metres from the router. However, your chipset is a different though related one, so this could still be an N issue. Or perhaps you are getting interference from some other wireless device in the neighbourhood. Most N routers will operate in the congested 2.4GHz band - which is where G devices operate - but only the more expensive ones can use the less crowded 5GHz band. Do you know which yours uses? If the 2.4GHz band, it won't be just other routers that can interfere.  Baby alarms and microwave ovens can also be a problem.

Anyway, even though my AR928X device seems happy with the Maverick ath9k driver and my N-router, it's certainly worth trying the older G-standard. Try setting your present router to b/g, or have a hunt around for those other routers.

---

### Post by xorkal1985 on 2010-10-14
I see you have a Vaio, with atheros wireless drivers... you're in the same boat I am. You are not going to see very good performance out of the AR9285. But I do have a "fix" for you. I use the exact same wireless card in my Vaio laptop, and after a lot of research, and fooling around, I have a somewhat stable connection with minimal packet loss.

Follow these directions to get your card performing better:

1. Download and extract this file: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

2. Open Terminal and remove the ath9k drivers currently installed.
```
sudo modprobe -r ath9k
```

3. You will notice your wireless disconnect nearly immediately if you are connected. Now in terminal, navigate to the folder of the file I had you download. and type the following:
```
sudo make
```

4. It will take just a minute compiling everything. When that's done type:
```
sudo make install
```

5. That step will take just a second too. But when its done, exit terminal, restart your computer, and BAM! you have about as stable of wireless as you'll get out of the AR9285 card at the moment.

You can test your packet loss by opening terminal and typing:
```
ping www.google.com
```

Let that go for a while, and hit Ctrl+C to stop the pinging and it will give you a report of what your packet loss percentage was.

Hope this helped some!

---

### Post by coffeecat on 2010-10-14
> **xorkal1985 said:**
> 1. Download and extract this file: [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

If you want the compat-wireless drivers, there's an easier way. Simply use Synaptic to install the metapackage linux-backports-modules-wireless-maverick-generic. That pulls in the version of the compat-wireless drivers pre-compiled to go with the current kernel, and it will be updated if the kernel is updated. No compiling, no modprobing - simply reboot after installation. You don't even have to enable the backports repository - the package is in Main.

But good idea. @steel_rose, you might want to try this. I found the backports package useful in Karmic/9.10.

---

### Post by steel_rose on 2010-10-15
Hello!
 
Thanks for the replies, unfortunately things didn't go as planned...
I first tries Coffeecat's solution, but it didn't seem to make a difference.
I then tried Xorcal1985's process.  During the "install" bit it printed on the terminal that something "FATAL" was happening a few times, which didn't look good, but it went on till the end and everything seemed fine.
 
Unfortunately, when I restarted the machine something bad happened: I logged in, the desktop appeared, the wireless icon was trying to get the signal when everything went black, with the cursor stuck in the middle of the screen, unmoveable.
I tried again, with the same result.
 
I'm writing from Windows, here everything is still working fine, no major data was lost as I installed Ubuntu only on Monday.
 
I really like the idea behing "open source" technology and the philosophy of Ubuntu, but it looks like Vaios are not good friends with Linux.  Should I just give up for the moment and come back to Ubuntu when I get a new laptop?  Unfortunaly this one is quite new and I don't plan on getting a new one soon, it's a real shame because I was really enjoying this OS!
 
Thank you very much for the help, I really appreciate!
 
SR

---

### Post by steel_rose on 2010-10-15
Sorry for the negativity of the previous post, I have tried a third time to start the laptop with Ubuntu and now it works!
The connection seems to be slightly more stable, not at the level that I have with Windows 7 but if it holds like it did over the last 10 minutes of web surfing I'm happy.
As I was saying above, I really like the open source and Ubuntu way of thinking as well as finding the OS very nice to use and more flexible than Windows.

I'll keep on using the internet and will let you know how I get along...

Thank you again for all the support!

SR

---

### Post by coffeecat on 2010-10-15
> **steel_rose said:**
> I really like the idea behing "open source" technology and the philosophy of Ubuntu, but it looks like Vaios are not good friends with Linux.

Depends on your Vaio. With my old +5-years old one (almost) everything worked in every version of Ubuntu since Dapper Drake (6.06), and in many other Linux distros.

In my newer (2009) Vaio everything 'just works' except for a minor issue with the Fn brightness keys in Maverick - which I guess is a kernel bug that will get sorted sooner or later because they work using the Lucid kernel in Maverick.

I don't know what's gone wrong with your install, but did you see my post about the backports package? You could have got the compat-wireless driver to try without all that tedious compiling. It's possible the compiled wireless driver is interfering with ACPI, but you'd need to uninstall it to be sure. Unfortunately, it could be a major pain uninstalling it when you can't get to a usable GUI.

Rather than find out which directory you unpacked the tarball and seeing whether or not the developers bothered to include an uninstall script, may I suggest that you reinstall Ubuntu and try the backports package I suggested? If that does the same thing, at least you can uninstall it easily from the command line in a recovery console.

**Edit:** I saw your latest post only after I posted this. Glad to see it's working.

---

### Post by Angelic on 2010-10-16
> **coffeecat said:**
> If you want the compat-wireless drivers, there's an easier way. Simply use Synaptic to install the metapackage linux-backports-modules-wireless-maverick-generic. That pulls in the version of the compat-wireless drivers pre-compiled to go with the current kernel, and it will be updated if the kernel is updated. No compiling, no modprobing - simply reboot after installation. You don't even have to enable the backports repository - the package is in Main.

But good idea. @steel_rose, you might want to try this. I found the backports package useful in Karmic/9.10.

Hi,

I've tried this but it doesn't seem to work for me; after I reboot the system still uses the ath9k driver :(

---

### Post by coffeecat on 2010-10-16
> **Angelic said:**
> Hi,

I've tried this but it doesn't seem to work for me; after I reboot the system still uses the ath9k driver :(

The backports driver is still called ath9k.

---

### Post by Angelic on 2010-10-16
Is there any way I can verify that it's not using the old ath9k driver?

edit: I've installed the package using synaptics but browsing the web still seems slow. On boot it also gives me the error that the module couldn't be loaded.

edit2: The error I get is FATAL: Could not load /lib/modules/2.6.35-22-generic/modules.dep: no such file or directory

The error appears twice, then the GUI appears and I get a wireless connection, but I think it's still the old driver since it's still extremely slow :(

---

### Post by Angelic on 2010-10-16
Okay, I have disabled the onboard card and am now using a USB wifi adapter, and it also doesn't seem to be very fast. Could it be something with my installation?

Edit: I've created a new thread because of this, not sure if it is just related to the wifi adapter or maybe something else is going on:

[http://ubuntuforums.org/showthread.php?p=9982918#post9982918](http://ubuntuforums.org/showthread.php?p=9982918#post9982918)

---

### Post by coffeecat on 2010-10-16
> **Angelic said:**
> Edit: I've created a new thread because of this, not sure if it is just related to the wifi adapter or maybe something else is going on:

[http://ubuntuforums.org/showthread.php?p=9982918#post9982918](http://ubuntuforums.org/showthread.php?p=9982918#post9982918)

Good luck with the new thread. Can I suggest two things that might get you help quicker?

Edit your thread title so that it includes your wireless chipset - in your case AR9285. In that way people with experience of your chipset may be able to help. Mine is different - the AR928X - so I'm limited in what I can suggest.

Next - ask a moderator to move it to the Networking and Wireless subforum. It would be better there and more likely to be seen by the people with good wireless experience. The way you ask a moderator to move it is to click on the Report Abuse button at the bottom left of your post. This one: [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] . Yes, I know it says "report abuse" but that's quite OK for asking for a thread move as well.

---

### Post by coffeecat on 2010-10-16
@steel_rose, I know your Atheros chipset (AR9285) is different from mine (AR928X) but I've had a weird experience with mine and would be interested to see if you get anything like it. If not, what I have to record might be useful for someone else stumbling across this thread.

I reset my N-capable router back to 150MB/s - N - the other day during the course of this thread, and because I was getting good speeds and was able to surf the net seemingly OK I didn't think much more about it. Until last evening that is.

While I was fiddling with the router and checking the response of this laptop I was actually posting from my ethernet connected desktop. Yesterday evening, I logged onto this forum with this Atheros AR 928X laptop using Ubuntu Maverick, picked up a subscribed thread, tried to preview post and waited.... and waited.... and waited.... Long story short: I could log in and log out, read threads, read my User CP, but I could not post. The forum would seem to hang. The few other sites I tried I was  able to surf OK, but not the Yahoo UK home page which took ages to resolve and when it finally did, it was all garbled. The same happened in OpenSUSE which is on another partition, so I was eventually reduced to having to make my posts from Windows 7. :oops: Which worked fine.

I retired to bed puzzled and the penny finally dropped this morning. I changed the router back to b/g and everything was OK again in Ubuntu on this forum. I tried the backports wireless drivers but with the same result with the router set to N. So the backports drivers were no better nor no worse than the default ath9k driver for my wireless chipset.

I'm back with the router set to b/g, which is plenty fast enough for me anyway. It's a Netgear DGN1000, by the way.

Curious story, but I don't know enough about networking and website design to be able to explain it. I can't see how it can be a problem with uploading because I can log in. Strange. :-k

---

### Post by Angelic on 2010-10-16
> **coffeecat said:**
> Good luck with the new thread. Can I suggest two things that might get you help quicker?

Edit your thread title so that it includes your wireless chipset - in your case AR9285. In that way people with experience of your chipset may be able to help. Mine is different - the AR928X - so I'm limited in what I can suggest.

Next - ask a moderator to move it to the Networking and Wireless subforum. It would be better there and more likely to be seen by the people with good wireless experience. The way you ask a moderator to move it is to click on the Report Abuse button at the bottom left of your post. This one: [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] . Yes, I know it says "report abuse" but that's quite OK for asking for a thread move as well.

Thanks for your suggestion, I've done that just now.

---

### Post by steel_rose on 2010-10-17
Hi Coffeecat,

My connection is still very unstable despite the backports package.
I tried the Yahoo homepage and it seemed to work fine with me, but I often have problems with posting on this forum too and now that I think about it I do notice that there seem to be websites that are particularly slow: Hotmail takes long and gives frequent errors, Youtube is a nightmare in terms of loading videos, but the searches seem OK.
Overall it's kind of OK, but not very reliable (compared to Windows 7).

Thank you for all the support,

SR

---

### Post by kammmo on 2010-12-23
i dont know your status,  your problem is resolved or no, try to check your proxy server settings..:smile: >>System>Preferences>Network Proxy :smile:) I had the same problem with internet speed in ubuntu (and Win 7) as you :smile: after set proxy is everything OK :popcorn:

---

### Post by noran on 2011-03-20
I also have a Vaio laptop with a slow ath9k connection. Compiling compat-wireless from source worked perfectly at first, but the problem is I had to recompile it after almost every update.

This last update on Maverick changed everything: now I get an error compiling compat-wireless from source, so I had to use the repository to install it. But there's no effect whatsoever on speed now. I'm back to an extremely slow connection. No idea what that's about.

Appreciate any help on this.

---

