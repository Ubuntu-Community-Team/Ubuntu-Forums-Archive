---
title: "Acer Aspire 7551-7422"
date: 2011-12-10
forum: Hardware
---

### Post by jcer93705 on 2011-12-10
Hello guys how is you're Acer Aspire 7551-7422 running under latest Ubuntu 11.10? Anything that doesn't work out of the box with Ubuntu 11.10? I'm expecting my laptop on Monday.

---

### Post by ilikelinuxitisthebest on 2011-12-10
ubuntu has a live cd, which means that you can take for a test drive first. download it here [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) 
that page will explain everything you need to know. if you have questions. me and alot of other people are here to help. have fun.:)

---

### Post by jcer93705 on 2011-12-11
> **ilikelinuxitisthebest said:**
> ubuntu has a live cd, which means that you can take for a test drive first. download it here [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) 
that page will explain everything you need to know. if you have questions. me and alot of other people are here to help. have fun.:)

Thanks but I'm not new to Linux and neither Ubuntu. But I haven't received the laptop and wanted to know if anyone having any issue with latest Ubuntu version before I get it. I guess it doesn't matter anyways I will be finding out this coming up Monday.

---

### Post by ilikelinuxitisthebest on 2011-12-11
i've surfed around for a little bit trying to find problems and there dont appear to be any. either way you bought the laptop and your going to install ubuntu on it. when you get it you should come back to this thread and post if you had any problems. ill be glad to help.

---

### Post by jcer93705 on 2011-12-12
> **ilikelinuxitisthebest said:**
> i've surfed around for a little bit trying to find problems and there dont appear to be any. either way you bought the laptop and your going to install ubuntu on it. when you get it you should come back to this thread and post if you had any problems. ill be glad to help.

Yea I will post if there any issue I'm not entirely new to linux but always a need for help sometimes.

---

### Post by jcer93705 on 2011-12-17
> **ilikelinuxitisthebest said:**
> i've surfed around for a little bit trying to find problems and there dont appear to be any. either way you bought the laptop and your going to install ubuntu on it. when you get it you should come back to this thread and post if you had any problems. ill be glad to help.

Hi well I installed via wubi. Then installed ATI driver using [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
Then did a updated. By the way the video driver is the latest. Everything is so slow compare to window 7. The first day I received it I installed ubuntu and it ran good until I installed the driver. I tried different driver from the Additional driver manager. Even the internet is slower. What is wrong?

---

### Post by tonglen on 2011-12-17
...Hi I have linux Ming 9 stable long term release on my acer 5332 , absolutely no issues at all, works straight out of the box and nice and fast...perhaps you may like to try it out and see if you notice any differences...between it and the Ubuntu distro you have on your machinerie - good luck let me know if you how you get on...cheers...

---

### Post by jcer93705 on 2011-12-17
> **tonglen said:**
> ...Hi I have linux Ming 9 stable long term release on my acer 5332 , absolutely no issues at all, works straight out of the box and nice and fast...perhaps you may like to try it out and see if you notice any differences...between it and the Ubuntu distro you have on your machinerie - good luck let me know if you how you get on...cheers...

You're laptop is totally different. Older kernel might not have the latest drivers for my laptop. My laptop is a newer laptop. But I'm downloading latest Linux Mint 12. I have no cdr or dvdr disk to burn but I'll be using the window installer. See how it goes. I check my log yesturday and it loaded my os with nvidia driver wtf LOL. Anyways I'm downloading linux mint 12. I had to uninstall ubuntu due to being so slow like a snail. Would take 5 min to turn off would take 3 min to close a window uninstalling anything on it would take forever.

---

### Post by tonglen on 2011-12-17
good luck with 12 some find it works fine others are having problems with especially graphics drivers...I chose 9 as it is long term and very stable for 3 years, think it starts to lose support around June 2013 not certain though from top of my head, I will wait for around 6 months before I check out 12 by then hopefully most of the bugs will be ironed out...good luck...

---

### Post by jcer93705 on 2011-12-17
> **tonglen said:**
> good luck with 12 some find it works fine others are having problems with especially graphics drivers...I chose 9 as it is long term and very stable for 3 years, think it starts to lose support around June 2013 not certain though from top of my head, I will wait for around 6 months before I check out 12 by then hopefully most of the bugs will be ironed out...good luck...

The problem with the latest linux is gnome 3 and linux ati proprietary driver compatibility problem with the gnome 3. I tried linux mint but it has gnome 3 I notice if I run gnome classic it run better. Yea I should try out the version you're on I need to buy blank cd unless if it can be installed in windows like version 12. Open source video driver works better but still slow. I think if I try the version you're on out of the box my wifi won't be working I bet. Not even ubuntu 10.10 detect my wifi. Anyways damn.

---

### Post by tonglen on 2011-12-17
...can only speak for my own experience at the moment with the laptop that I have and graphics issues I have had in the past...:) will be staying on Gnome 2 for quite a while...lol...

---

### Post by TBABill on 2011-12-17
I have the Acer 5552-7677 and it has an Atheros wireless card. Not sure if your model does -as well, but you may have to make one tiny change as follows (only if you have the Atheros AR9287): ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

To find out if this effects you, just open a terminal window and type in lspci (LSPCI in lowercase). If it lists a network device Atheros AR9287, just run what I listed above. That fixed my slow wireless connection in Ubuntu 11.10. I was only getting 900Kbps to 1.3Mbps on a 10Mbps service. Now i get the full 10.

---

### Post by jcer93705 on 2011-12-17
> **TBABill said:**
> I have the Acer 5552-7677 and it has an Atheros wireless card. Not sure if your model does -as well, but you may have to make one tiny change as follows (only if you have the Atheros AR9287): ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

To find out if this effects you, just open a terminal window and type in lspci (LSPCI in lowercase). If it lists a network device Atheros AR9287, just run what I listed above. That fixed my slow wireless connection in Ubuntu 11.10. I was only getting 900Kbps to 1.3Mbps on a 10Mbps service. Now i get the full 10.

Hi I have Atheros AR5B97. I'm installing kubuntu 11.10 I'll see if that works for me of the code you posted.

---

### Post by TBABill on 2011-12-17
To activate the fix you may also need to logout and back in after the change...or restart.

---

### Post by ilikelinuxitisthebest on 2011-12-20
prehaps try to start a new thread. more people will respond.

---

### Post by jcer93705 on 2012-05-24
Hi guys I finally switch over. I tried Xubuntu 12.04 for over a week dual booting with Window 7. I fell in love with Xubuntu 12.04 everything is working correctly except I had to modified so I can have a stablet internet speed. Wow it was slow without doing so. Sometime it wont response. This is what I did. 

Create a new file /etc/modprobe.d/ath9k.conf:

sudo nano /etc/modprobe.d/ath9k.conf

Add the following line to it:

options ath9k nohwcrypt=1

So this is the fix for Atheros AR9287 wifi.

---

