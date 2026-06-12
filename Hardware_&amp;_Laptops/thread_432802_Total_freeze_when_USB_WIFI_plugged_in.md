---
title: "Total freeze when USB WIFI plugged in"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by jago25_98 on 2007-05-04
As soon as this USB WIFI adapter is plugged in everything goes very slow:
[http://www.edimax.com/en/produce_detail.php?pd_id=8&pl1_id=1&pl2_id=44](http://www.edimax.com/en/produce_detail.php?pd_id=8&pl1_id=1&pl2_id=44)

When it is ejected everything freezes completely.

It's hard to diagnose because the machine isn't usable when the device is plugged in.

kernel Linux r40 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux, from fresh install 2 weeks ago.

What should I do next?

Ah, I do have a PCI 2200bg card already, but I was hoping to use both.

---

### Post by dannyboy79 on 2007-05-04
ah, what do you mean use both?? you can't use both unless you're setting up your computer to be a router?

when you plug it in, what do these commands return

dmesg | tail

lsusb

you stated that it's just slow, not unresponsive so you should be able to hit alt and f2, this will bring up a little box, type in the above command and tell it to run in a terminal, do that for both commands and then paste the result into a file or write the results down, shut down the machine (this is of course if you don't have another machine that you can post the info I am asking for in the forum with), then when you start the machine back up, make sure the usb dongle is NOT plugged in so that you can tel me what the output from the above commands were.

---

### Post by jago25_98 on 2007-05-04
it's too slow to even do that. I will try now and crash it

---

### Post by jago25_98 on 2007-05-05
ok. I put dmesg into a loop and inserted the adapter.

I can see that rt25usb v1.1 is mentioned first,
followed by rt73usb 

and that these are part of the rt2x00usb device driver set.

A bug is also mentioned.

I will try to get full output now with lsusb

---

### Post by dannyboy79 on 2007-05-07
yeap, you need to blacklist those Ubuntu provided modules as they don't work. I have been told that here. [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
OR
try the ndiswrapper ([http://ubuntuforums.org/showthread.php?t=430740&page=2&highlight=seamonkey](http://ubuntuforums.org/showthread.php?t=430740&page=2&highlight=seamonkey))

---

### Post by jago25_98 on 2007-05-07
Thanks Danny, I don't need SMP anyway, horah!

---

### Post by dannyboy79 on 2007-05-07
> **jago25_98 said:**
> Thanks Danny, I don't need SMP anyway, horah!

so you're saying that you got it? Also, are you being sarcastic? I would be pretty upset myself if I wanted to use wireless and then I couldn't take advantage of my Dual Core or HT cpu. Trust me, I would be very upset but I am going to guess that you probably won't even notice it unless you're doing video encoding or compiling a kernel etc etc. Something very cpu intensive. Anyway, I hope it's working for ya. Also, the seamonkey drivers will work with SMP soon I have read.

---

### Post by gualo on 2007-05-08
Hi,
I just installed Feisty desktop on an empty machine (Pentium4/1.4Ghz/512Mb/80Gb) and am experiencing the same problem using a SMC USB wifi adapter ([http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&pid=1545)](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&pid=1545)).
The machine also has an Ethernet card that is not connected to the network and that I don't plan to use, at least for the moment.
When the wifi adapter is plugged in the whole system slows down almost to a stop. When I login I get an error window (after a >5 minutes delay) about a Gnome settings daemon error mentioned in many other threads. I followed the advice given for that error but that didn't help.
If I unplug the adapter then the system freezes completely.
I tried to plug the adapter in console mode (Alt+Ctrl+F1 from the login screen) but it's the same so I believe this isn't a Gnome specific problem. When I unplug the adapter the system crashes with the following error message :  [104.961744] BUG: soft lock detected on CPU#0!

What upsets me the most is that when running Ubuntu from the live CD everything works fine, including the wifi connection and I can access my network as well as the internet :-(
Thanks in advance for any help

---

### Post by funchords on 2007-05-08
Just adding a quick note. I found this thread while trying to troubleshoot my problem with the Gnome Settings Daemon message.  

I added a Hawking USB adapter (ZD1211, I'm pretty sure) and, even while not associated with an access point, I had network performance slowdowns and high CPU cycles.  

Then, upon reboot and entering my password into Gnome Desktop Manager (gdm), I had what I thought was a lockup on a  gdm background screen (it looked like it was trying to give me an xterm window, but it didn't work).  

I removed the USB, but the problem did not resolve.  I then used Alt+Ctrl+F1 to log in and 

$ **sudo nano /etc/network/interfaces **

find the lines associated with that USB driver (in my case, they were eth1, and there were two duplicate lines in the file -- one being the last line of the file and the other in the usual placement).

After making that change and rebooting, my system returned to normal operation.

Like another poster said, I don't think the Gnome Settings Daemon is the culprit at all.  I think it's a symptom, but the root case is elsewhere in networking.

---

### Post by gualo on 2007-05-09
> **gualo said:**
> Hi,
I just installed Feisty desktop on an empty machine (Pentium4/1.4Ghz/512Mb/80Gb) and am experiencing the same problem using a SMC USB wifi adapter ([http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&pid=1545)](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_USA&cid=5&pid=1545)).
The machine also has an Ethernet card that is not connected to the network and that I don't plan to use, at least for the moment.
When the wifi adapter is plugged in the whole system slows down almost to a stop. When I login I get an error window (after a >5 minutes delay) about a Gnome settings daemon error mentioned in many other threads. I followed the advice given for that error but that didn't help.
If I unplug the adapter then the system freezes completely.
I tried to plug the adapter in console mode (Alt+Ctrl+F1 from the login screen) but it's the same so I believe this isn't a Gnome specific problem. When I unplug the adapter the system crashes with the following error message :  [104.961744] BUG: soft lock detected on CPU#0!

What upsets me the most is that when running Ubuntu from the live CD everything works fine, including the wifi connection and I can access my network as well as the internet :-(
Thanks in advance for any help

Follow up to my previous message. I compared the configuration of my installation (that doesn't work) to that of the Ubuntu live CD (that works) and they are (or seem to be) exactly the same!! :mad: 

I installed ndiswrapper as advised in many places on the net ([http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html](http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html)) but still the same when I insert the adapter.
ndiswrapper -l reports the driver is installed **and **the hardware present :confused: 
iwconfig didn't respond at all and I waited for more than 10 minutes

I'll try reinstalling everything using the alternate installation... :(

---

### Post by dannyboy79 on 2007-05-09
> **gualo said:**
> Follow up to my previous message. I compared the configuration of my installation (that doesn't work) to that of the Ubuntu live CD (that works) and they are (or seem to be) exactly the same!! :mad: 

I installed ndiswrapper as advised in many places on the net ([http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html](http://www.ubuntugeek.com/how-to-install-netgear-wg111v2-wireless-dongle-card-on-ubuntu-edgy.html)) but still the same when I insert the adapter.
ndiswrapper -l reports the driver is installed **and **the hardware present :confused: 
iwconfig didn't respond at all and I waited for more than 10 minutes

I'll try reinstalling everything using the alternate installation... :(

and did you specifically look at the /etc/network/interfaces file as the above poster mentioned? make sure there aren't 2 of the same interface. also, to try to resolve this easier you could remove the words that state

auto wifi0

OR

auto WHATEVER

so that when networking get's called by the init scripts it doesn't try to automatically bring it up when you plug in your usb adpater. good luck. also, if you just installed fiesty using the live cd, you won't get anything different using hte alt cd as all it does is allow you more choices during the install but has no difference in the end setup! also, did you blacklist those modules before you plug in the usb adapter as I suggested!

---

### Post by jago25_98 on 2007-05-11
No I wasn't being sarcastic; I don't have hyperthreading so [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) appears to work for me.

...

now swscanner crashes on scan

and 

kismet can't connect to it UI port...

so onto the next problem...

---

### Post by jago25_98 on 2007-05-11
solved my problem by making a loopback interface that was accidently deleted!

---

### Post by gualo on 2007-05-12
Finally it's working! :-D 
I followed the advice given by smyrman ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99178/comments/7](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99178/comments/7)) and my adapter is now recognized, activated and communicates, thanks smyrman :cool: 

I'm now struggling with having the connection being established automatically after boot.

---

