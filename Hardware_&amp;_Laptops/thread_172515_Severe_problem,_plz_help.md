---
title: "Severe problem, plz help"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by azazel00 on 2006-05-08
Hello,

I'll try to get right to the point. I've installed several Linux distros in the past months (after my OnBoard NIC failed). All of them have failed. The most common case is that I get to play for like 3-5 minutes in the OS, and then it simply crashes. I've tried Suse 10, FC 4 and FC 5. Same problem with all of them.

Last night I decided to give Ubuntu a go. I'd played with it using a VMware setup and it was working quite good. First I tried the Live CD, unlike most Live CDs I had tried, it went through a setup. During the setup, it failed after it tried a hardware detection step.

Then I tried the install CD. It failed while seting up the network. So I just disabled both NICs (didnt know wether eth0 was the OnBoard one or eth1 was the one). It continued with the install after disabling the network, but then while installing the Kernel it gave the "Intallation failed" screen. I called it quits.

Later I decided to retry FC 5 (not that Im too proud of it... I really like how Ubuntu worked from my VM experience). It completed the install (after disabling both NICs again). To my surprise, I passed the 20 minute mark using the system. I enabled one of the cards, and I was browsing with Firefox and trying to install some packages with their GUI app. Then it crashed again.

At this point I think it's quite obvious that the problem lies in my Onboard NIC. But, if it's disabled why did it crash?

I dont know how to proceed. I tried to disable my onboard NIC in the motherboard, but I didnt find an option for it. Most of the times the systems crashed it was while I was trying to do something "network" related. ie: Installing packages, browsing, etc. But in Ubuntu's case, it was during the kernell install.

Any advice will be well recieved. (Except suggestion to buy a new PC, unless you wanna donate :p )

Btw, both of my NICs are Realtek RTL8139/810x

Regards,
az

---

### Post by cilynx on 2006-05-08
Your problem most likely comes from the fact that you have to have the driver for the broken NIC loaded to run the functional NIC.  If the init or addressing portion of the broken NIC is the problem, you're going to get crashes even with it "disabled".  My advice would be to go out and get a $20 NIC that isn't RTL8139 based so that you don't have to load that module.  Blacklist the RTL8139 module and you should be good to go.

---

### Post by azazel00 on 2006-05-08
[QUOTE=cilynx]Your problem most likely comes from the fact that you have to have the driver for the broken NIC loaded to run the functional NIC.  If the init or addressing portion of the broken NIC is the problem, you're going to get crashes even with it "disabled".  My advice would be to go out and get a $20 NIC that isn't RTL8139 based so that you don't have to load that module.  Blacklist the RTL8139 module and you should be good to go.[/QUOTE]

Sounds like a plan. Can you point me out on a good place to learn how to blacklist a driver? Did a couple of google searches, but all it's returned is some crappy pages with not a lot of usefull info.

Thanks a lot

az

---

### Post by cilynx on 2006-05-08
Make a new file in /etc/hotplug/blacklist.d/ and call it "broken_nic" or something else to remember it by.  In the file, put one line: 'rtl8139' or whatever the name of the module you need to blacklist is.

---

