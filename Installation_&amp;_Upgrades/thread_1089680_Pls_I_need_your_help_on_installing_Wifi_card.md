---
title: "Pls I need your help on installing Wifi card"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by waqas87 on 2009-03-07
Hello everyone,

I am new here. This is my first post and I have a problem.
I have windows xp server pack 3 which I use it for work and installing ubuntu for games, playing music and streaming videos. My laptop is Samsung NC10 and I bought it about three months ago. 

I have atheros AR5007EG. I have searched for ndiswrapper and installed it. I have searched and copy the original .inf driver for Atheros AR5007EG in Windows XP. And opened Windows Wireless Driver and install the .inf file. 

What should i do next? Also I have followed other website to setup up ndiswrapper and i am cant open the window wireless driver anymore. I am stuck. Please help......

Please show me how to make this wireless work.....

Thanks

---

### Post by Twitch6000 on 2009-03-07
well there is a gui tool for ndiwrapper to help you with at I do not know the name so I will let someone else tell you.

However If you are using the latest ubuntu you should not need ndiswrapper.

I know with my AR5009 card it works out of the box.

I just have to click the network.

---

### Post by avtolle on 2009-03-07
Here is another way to get your Atheros card working: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) if you are using 8.10.

This method ([http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)) worked on 8.04, and from what I know, works with 8.10.

---

### Post by waqas87 on 2009-03-07
Thanks for the information. I will let you know asap if my wireless adapter worked. And thanks for replying it so fast. This forums is brilliant in helping other in needs. Thanks again!!

---

### Post by waqas87 on 2009-03-07
Hi I have installed the relevent package. I have installed the ndiswrapper but it is not opening... However I am installing madwifi. I need your help on the installing madwifi. I cant understand it. Please help me again.

---

### Post by avtolle on 2009-03-07
First, as the madwifi and ndiswrapper installations will conflict, if you were successful (which it doesn't appear you were) installing the XP driver with ndiswrapper, you would need to remove it. 

Exactly what problems are you having installing the madwifi driver? BTW, there is another option out there to try, if you are interested, I'll get the link and post it here.

---

### Post by avtolle on 2009-03-07
Just happened to think; have you restarted your computer after doing the ndiswrapper attempted installation?

---

### Post by waqas87 on 2009-03-07
I have removed the ndiswrapper now. I will restart my laptop again. lets see what happens

---

### Post by waqas87 on 2009-03-07
I am about to ask a stupid question. How do i know madwifi is installed? I have removed the ndiswrapper. It is still not working.

---

### Post by avtolle on 2009-03-07
OK, you have ndiswrapper removed. Whether madwifi is installed is dependent upon whether you followed the linked ubuntugeek article in full.

I don't want to confuse you further. What have you tried to date, other than trying to use ndiswrapper to install the XP driver?

---

### Post by waqas87 on 2009-03-07
nothing else. I am now following above ubuntugeek steps to install madwifi.

---

### Post by avtolle on 2009-03-07
> **waqas87 said:**
> nothing else. I am now following above ubuntugeek steps to install madwifi.
Good luck. I'll be leaving shortly, but will check before doing so. Others will hopefully be able to chime in with assistance.

EDIT: Please check the posts to that linked piece. There is a new madwifi snapshot you will need to get as opposed to the one given in the linked piece (post 130 or so).

---

### Post by waqas87 on 2009-03-07
To help more in your investigation. 
I have install the linux-backports-modules-intrepid-generic package sucessfully and restarted. Then I tried to install the madwifi. Everything went smooth. No errors occured.
i typed lshw -C network.
*****@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:ae:ec:e5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.0.6 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:7f:34:1b:12:bf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by avtolle on 2009-03-07
For anyone else following this thread: if you have a clean install, use the method set out in the Ubuntu release notes linked in my first post, as that is the easiest (I believe) way for a beginner to proceed.

The next easiest way to proceed, again IMO, is to go to [http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers) and follow the directions there. Be sure to install the build-essential package, whether through Synaptic or from the terminal```
sudo aptitude update
sudo aptitude install build-essential
```Be aware that the tarball with the latest drivers has a different name (no date) than that set out in the directions. Good luck to all (I found that the ath5k driver in this package to give better results than the one that came in the backports module, at least at the time I tried each method).

---

### Post by avtolle on 2009-03-07
You didn't need to install the madwifi driver if you had installed the ath5k driver through the backports module. These are two different ways to achieve the same end.

EDIT: I just went back to my first post, and see where it might have confused you due to my bad wording. I didn't make it clear that you should do one or the either, not both together.

---

### Post by waqas87 on 2009-03-08
I am reinstalling the ubuntu again. And this time I know what i am suppose to do. Before i was newbie. Now after going through your steps. I know what i have made mistakes.

---

### Post by waqas87 on 2009-03-15
Hi guys,
guess what? I done it. Woohooo!!! i followed similar instruction above but from different website. However, I have to deactive and reactive the support hardware for atheros wirelesss adapter. (system > Administration > Hardware Drivers) and deactive it and reactive it. Then click on network icon and connect to wireless router. 

First i did "sudo lshw -C network". I found out that my atheros is AR242X adapter. Then I went on google and typed "AR242x driver" in the search box. This the website: [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html). However, I download compact wireless from different source. But followed the same instruction. Then I install the packages and blacklist the ath5k.

After, that i restart the computer. But i didnt work. So i deactive and reactive the support for hardware drivers. 

This enables me to connect the wireless network. However, everytime i shut down the ubuntu, i have reactive the support for hardware driver again. Then it shows up on the network icon. I need a little help!!!

---

### Post by avtolle on 2009-03-15
If you used the first option, you should not have the ath5k driver blacklisted. I'm guessing a bit here, but have a feeling that is what your problem may be. Go back into the file where it is blacklisted, comment this out (put a # before ath5k), restart and see whether that resolves your problem.

---

### Post by waqas87 on 2009-03-15
Hi, I have followed every step except for last bit. 

"IF after this steps you still cannot make it work, you probably have something left still blacklisting ath5k, thus making it not to load. You should search all the files on /etc/modprobe.d for all lines that had:

blacklist ath5k

And add a # before the start of the line, thus making it into a comment so the above one becomes

    # blacklist ath5k

Save and exit the file

I hope this help for some one to fix their wireless problem."

I dont understand this. I have been through all the files in the modprobe.d folder and couldnt find "blacklist ath5k". What should i do?

---

### Post by avtolle on 2009-03-15
Is there a file blacklist, e.g., /etc/modprobe.d/blacklist that has ath5k located therein? If so, that is where you would comment out ath5k. HTH.

---

### Post by waqas87 on 2009-03-16
Hi,

yes there is "blacklist" file located in /etc/modprobe.d. I have opened the file and read thousand times. But there is no "blacklist ath5k" or the word "ath5k" either. I was thinking of adding a line, will it crashes the file.

---

### Post by Mgiacchetti on 2009-03-26
Hey, just chiming in to see if you finally figured this out.  I have a client that has an AR242x with basically the same problem, we have tried the backports with no luck, in hardware drivers, there are two different entries, we have deselected both, and blacklisted hal and pci, and I am about to guide him through [this](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html) guide.

---

