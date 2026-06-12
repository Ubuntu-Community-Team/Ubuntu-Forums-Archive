---
title: "WiFi Ubuntu 10.10"
date: 2010-11-21
forum: Hardware
---

### Post by janthonywj on 2010-11-21
I'm shocked that I can't find more relevant information on this issue. But I'm now resorting to making threads calling out for help. 

The goal here is to get ANY Linux distro to work properly on my Viliv S10 Blade. The hardware in this netvertible is VERY similar to MANY devices out there (most not in the US). I've made some progress with it, but the WiFi drivers are killing me. I need some help. I'm basically a noob, but not really. 

Where I'm at: I've installed a fresh copy of Ubuntu 10.10 and used a USB Wifi adapter (that will only stay connected for 1min - 5 min at a time, making this process even more of a headache), to get some files and such on the device. I copied the sd8686_v9.bin and sd8686_v9_helper.bin file to the /lib/firmware/ directory from /lib/firmware/libertas/ direcotry and renamed the files. Although! I have found a very recent patch that I don't know how to apply that should eliminate this need. [https://patchwork.kernel.org/patch/285862/](https://patchwork.kernel.org/patch/285862/). Help?

So, I got the sd8686 chip to power on... Ubuntu detected it... then I can see the available networks in nm-applet. Trying to connect to ANYTHING it will freeze the entire OS upon connection. I've tried using other tools and not network manager with the same result. I couldn't get wpa_supplicant to work. I tried downloading the linux drivers from the Marvell.com website, but there must have been some horrible programming, or I don't have the right tools installed on the system by default because I was getting syntax errors trying to install. 

It seems that this WiFi device has not received the attention needed from the community. I know a lot of new tablets and netbooks are using this, mostly from Asian companies. This netbook also comes with GMA500 which is another Linux issue. We can start on that after the WiFi. 

I also tried the install guide.zip from this forum, [http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=7704&viewmode=flat&order=ASC&start=45](http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=7704&viewmode=flat&order=ASC&start=45) , but I used my current kernel version instead of the older one, hoping it would work. The patch wouldn't work, so no difference. I'd really like to fix this issue without having to be locked in to Ubuntu Karmic or a specific kernel version especially since I'm going to be taking on the touchscreen next and Ubuntu 10.10 has better support for that. 

Please help someone.

---

### Post by fanum on 2011-02-12
> **janthonywj said:**
> I'm shocked that I can't find more relevant information on this issue. But I'm now resorting to making threads calling out for help. 

The goal here is to get ANY Linux distro to work properly on my Viliv S10 Blade. The hardware in this netvertible is VERY similar to MANY devices out there (most not in the US). I've made some progress with it, but the WiFi drivers are killing me. I need some help. I'm basically a noob, but not really. 

Where I'm at: I've installed a fresh copy of Ubuntu 10.10 and used a USB Wifi adapter (that will only stay connected for 1min - 5 min at a time, making this process even more of a headache), to get some files and such on the device. I copied the sd8686_v9.bin and sd8686_v9_helper.bin file to the /lib/firmware/ directory from /lib/firmware/libertas/ direcotry and renamed the files. Although! I have found a very recent patch that I don't know how to apply that should eliminate this need. [https://patchwork.kernel.org/patch/285862/](https://patchwork.kernel.org/patch/285862/). Help?

So, I got the sd8686 chip to power on... Ubuntu detected it... then I can see the available networks in nm-applet. Trying to connect to ANYTHING it will freeze the entire OS upon connection. I've tried using other tools and not network manager with the same result. I couldn't get wpa_supplicant to work. I tried downloading the linux drivers from the Marvell.com website, but there must have been some horrible programming, or I don't have the right tools installed on the system by default because I was getting syntax errors trying to install. 

It seems that this WiFi device has not received the attention needed from the community. I know a lot of new tablets and netbooks are using this, mostly from Asian companies. This netbook also comes with GMA500 which is another Linux issue. We can start on that after the WiFi. 

I also tried the install guide.zip from this forum, [http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=7704&viewmode=flat&order=ASC&start=45](http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=7704&viewmode=flat&order=ASC&start=45) , but I used my current kernel version instead of the older one, hoping it would work. The patch wouldn't work, so no difference. I'd really like to fix this issue without having to be locked in to Ubuntu Karmic or a specific kernel version especially since I'm going to be taking on the touchscreen next and Ubuntu 10.10 has better support for that. 

Please help someone.

That firmware conflicts with network manager (and even wicd), but for some reason I found one version of natty daily image that it works on (after alpha 1, right before alpha 2). I now have it working, but if I update, it breaks again. Not sure who to alert, and what information to provide so that this can be resolved, if you have any ideas, let me know

---

### Post by fanum on 2011-02-12
> **janthonywj said:**
> I'm shocked that I can't find more relevant information on this issue. But I'm now resorting to making threads calling out for help. 

The goal here is to get ANY Linux distro to work properly on my Viliv S10 Blade. The hardware in this netvertible is VERY similar to MANY devices out there (most not in the US). I've made some progress with it, but the WiFi drivers are killing me. I need some help. I'm basically a noob, but not really. 

Where I'm at: I've installed a fresh copy of Ubuntu 10.10 and used a USB Wifi adapter (that will only stay connected for 1min - 5 min at a time, making this process even more of a headache), to get some files and such on the device. I copied the sd8686_v9.bin and sd8686_v9_helper.bin file to the /lib/firmware/ directory from /lib/firmware/libertas/ direcotry and renamed the files. Although! I have found a very recent patch that I don't know how to apply that should eliminate this need. [https://patchwork.kernel.org/patch/285862/](https://patchwork.kernel.org/patch/285862/). Help?

So, I got the sd8686 chip to power on... Ubuntu detected it... then I can see the available networks in nm-applet. Trying to connect to ANYTHING it will freeze the entire OS upon connection. I've tried using other tools and not network manager with the same result. I couldn't get wpa_supplicant to work. I tried downloading the linux drivers from the Marvell.com website, but there must have been some horrible programming, or I don't have the right tools installed on the system by default because I was getting syntax errors trying to install. 

It seems that this WiFi device has not received the attention needed from the community. I know a lot of new tablets and netbooks are using this, mostly from Asian companies. This netbook also comes with GMA500 which is another Linux issue. We can start on that after the WiFi. 

I also tried the install guide.zip from this forum, [http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=7704&viewmode=flat&order=ASC&start=45](http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=7704&viewmode=flat&order=ASC&start=45) , but I used my current kernel version instead of the older one, hoping it would work. The patch wouldn't work, so no difference. I'd really like to fix this issue without having to be locked in to Ubuntu Karmic or a specific kernel version especially since I'm going to be taking on the touchscreen next and Ubuntu 10.10 has better support for that. 

Please help someone.

I had the same problem with my Viliv s7 and eventually found that one version of the natty daily image (after alpha 1, right before alpha 2) worked fine. I do not still have a copy of the image, but I do have a working install, and can provide information about package and kernel version etc, if you are still working on this problem. also not sure who to alert about getting this fixed, seems like I am in the best position to help, but have no idea who to contact.

---

### Post by janthonywj on 2011-04-18
> **fanum said:**
> I had the same problem with my Viliv s7 and eventually found that one version of the natty daily image (after alpha 1, right before alpha 2) worked fine. I do not still have a copy of the image, but I do have a working install, and can provide information about package and kernel version etc, if you are still working on this problem. also not sure who to alert about getting this fixed, seems like I am in the best position to help, but have no idea who to contact.

Are you still here Fanum? I gave up for a while in hopes that new revisions to software might help but I'm still at a loss. Do you still have the information you offered?

---

### Post by Patrulheiro on 2011-04-18
> **janthonywj said:**
> Are you still here Fanum? I gave up for a while in hopes that new revisions to software might help but I'm still at a loss. Do you still have the information you offered?

Hi there!
I'm having the same issue with my Marvell SD8686 card, but I'm trying to install in on Everun UMPC that uses the same card and I'm running BackTrack4, but so far haven't had any luck. Could anyone post detailed instructions on how to get it working please?
Thanks!

---

### Post by mörgæs on 2011-04-19
If you two want answers, you need to provide more information.

Which releases of Ubuntu have you tried? 
Can you get wired access to the internet and download all updates?
What have you tried to solve the problem?

A complete hardware description would also be good to have.

---

### Post by Patrulheiro on 2011-04-20
I'm trying to install BT4 R2 on a Raon Everum UMPC. Here are UMPC specs:
[http://www.notebook-driver.com/lapto...pecifications/](http://www.notebook-driver.com/lapto...pecifications/)

After installing the image into a USB and installing BT4 on the HD, I get almost everything working fine except for my Wifi Card. I came across this at UMPCPORTAL with someone trying to install Debian on it but it is quite outdated. 
What I've seeing so far is that the libertas driver supports Marvell SD8686 but not SDIO, it seems that you can use firmware 8.73.7.p3 from Marvell but I could not find it.
Also, libertas drivers modules seems to come installed already on BT4 Kernel (not 100% sure!) but being a totally newbie I would like if someone could send me specific instructions on how to install it and get it working!

Any help?!?

---

### Post by softseo on 2011-04-20
This will actually get rid of any blocking on the wireless network . For  whatever reason , in the update to Ubuntu 10.10 , there is a rfkill block  command that isn’t taken off after the upgrade . This is also a newer  utility so you’d never actually realize it until you found that you  couldn’t do anything to take that wireless block off .:)

---

### Post by Patrulheiro on 2011-04-21
> **Patrulheiro said:**
> I'm trying to install BT4 R2 on a Raon Everum UMPC. Here are UMPC specs:
[http://www.notebook-driver.com/lapto...pecifications/](http://www.notebook-driver.com/lapto...pecifications/)

After installing the image into a USB and installing BT4 on the HD, I get almost everything working fine except for my Wifi Card. I came across this at UMPCPORTAL with someone trying to install Debian on it but it is quite outdated. 
What I've seeing so far is that the libertas driver supports Marvell SD8686 but not SDIO, it seems that you can use firmware 8.73.7.p3 from Marvell but I could not find it.
Also, libertas drivers modules seems to come installed already on BT4 Kernel (not 100% sure!) but being a totally newbie I would like if someone could send me specific instructions on how to install it and get it working!

Any help?!?

Hi guys,
Here is what I found so far:
[http://www.umpcportal.com/modules/newbb/viewtopic.php?forum=18&post_id=8798&topic_id=1690](http://www.umpcportal.com/modules/newbb/viewtopic.php?forum=18&post_id=8798&topic_id=1690)

This is quite outdated so not sure if helps. Will try to install Ubuntu 10 today and see if works, although I would love to get BackTrack installed instead :)

Any help is appreciated!
Cheers.

---

### Post by janthonywj on 2011-04-23
> **Patrulheiro said:**
> Hi guys,
Here is what I found so far:
[http://www.umpcportal.com/modules/newbb/viewtopic.php?forum=18&post_id=8798&topic_id=1690](http://www.umpcportal.com/modules/newbb/viewtopic.php?forum=18&post_id=8798&topic_id=1690)

This is quite outdated so not sure if helps. Will try to install Ubuntu 10 today and see if works, although I would love to get BackTrack installed instead :)

Any help is appreciated!
Cheers.

When I was attacking this issue several months ago I had also found that resource. I haven't been able to get it to work right, but I'm just now getting back on the issue. 

Who would have thought that I would get the touchscreen and all fixed before the WiFi. My issue now is OOB 11.04 Ubuntu locks up completely upon activation of the WiFi device. I remember reading about this issue, but I haven't found a fix yet. After more research I'll post back, but if anyone knows how to fix it let me know.

---

### Post by Patrulheiro on 2011-04-23
> **janthonywj said:**
> When I was attacking this issue several months ago I had also found that resource. I haven't been able to get it to work right, but I'm just now getting back on the issue. 

Who would have thought that I would get the touchscreen and all fixed before the WiFi. My issue now is OOB 11.04 Ubuntu locks up completely upon activation of the WiFi device. I remember reading about this issue, but I haven't found a fix yet. After more research I'll post back, but if anyone knows how to fix it let me know.

I've tried to install 11.04 on the UMPC but it doesn't go beyond the installation, I get a blank screen when it tries to load X :confused: I believe is the graphics card! Can you tell me what did you do to install 10.04?
Have you tried to use libertas drivers on it? When I installed BackTrack on it I got everything working alright... touchscreen, keyboard, even the touch mouse bit, but no dice on the Wifi... I would have thought that someone would have managed to get it working by now... hope this is the right place to get information!!

Please let me know if you have any luck with it!

---

### Post by janthonywj on 2011-05-11
> **Patrulheiro said:**
> I've tried to install 11.04 on the UMPC but it doesn't go beyond the installation, I get a blank screen when it tries to load X :confused: I believe is the graphics card! Can you tell me what did you do to install 10.04?
Have you tried to use libertas drivers on it? When I installed BackTrack on it I got everything working alright... touchscreen, keyboard, even the touch mouse bit, but no dice on the Wifi... I would have thought that someone would have managed to get it working by now... hope this is the right place to get information!!

Please let me know if you have any luck with it!

Hi Patrulheiro,

Sorry for the delay in response. I've had finals for the past two weeks. I haven't really messed with the Wifi in the meantime. I have done some searching but I haven't found anything useful on the issue. 

There are two files you can copy to the libertas driver directory that are supposed to fix this issue, but the best I've got (And right now I can't recreate it) is that the Wifi would work for random amounts of time ranging from 30 seconds to 5 minutes before it would lose connection and could not re-establish a connection until a reboot. Right now, I still have the system lock issue. I don't know why yet. Touch screen works though, but the resolution isn't correct. (Easily fixed through xrandr.)

---

### Post by Patrulheiro on 2011-05-13
> **janthonywj said:**
> Hi Patrulheiro,

Sorry for the delay in response. I've had finals for the past two weeks. I haven't really messed with the Wifi in the meantime. I have done some searching but I haven't found anything useful on the issue. 

There are two files you can copy to the libertas driver directory that are supposed to fix this issue, but the best I've got (And right now I can't recreate it) is that the Wifi would work for random amounts of time ranging from 30 seconds to 5 minutes before it would lose connection and could not re-establish a connection until a reboot. Right now, I still have the system lock issue. I don't know why yet. Touch screen works though, but the resolution isn't correct. (Easily fixed through xrandr.)

Hi janthonywj,

Thanks for your reply! 
At the moment I'm using a Wireless USB adaptor to use the Wifi, it worked straight away out of the box! It's a shame I can't use the Wifi card from the UMPC, but I'm a persistent person so I will try it out until I get it working and I will post in here is I find something out!
How did you managed to install 11.04 on it?!? I can't go beyond the boot screen, when it's about to load X I get a blank screen! 

Thanks!

---

### Post by janthonywj on 2011-06-06
Any progress. I still can't figure out how to keep the system from freezing when I enable the SDIO Marvell8686 chip. I've tried different firmware versions, and still the same result. 

I wish I knew where I could reach someone that could fix this, pay them to do the work I can't do, and then have this fixed once and for all. I find posts about this ALL OVER then net, but no solutions.

---

### Post by janthonywj on 2011-06-06
> **janthonywj said:**
> Any progress. I still can't figure out how to keep the system from freezing when I enable the SDIO Marvell8686 chip. I've tried different firmware versions, and still the same result. 

I wish I knew where I could reach someone that could fix this, pay them to do the work I can't do, and then have this fixed once and for all. I find posts about this ALL OVER then net, but no solutions.

Ok, well I just made some progress. I renamed the version 8 libertas drivers from the /lib/firmware/libertas directory to simply SD8686.bin and SD8686_helper.bin and moved them to the /lib/firmware directory. 

Then, I removed network-manager and network-manager-gnome from my system. Then I am using iwconfig to connect to my unsecured network at the moment. When I initially tried to do a scan it came up with no networks, but I connected to my essid anyway, and it now has a connection. 

NOW, my problem is that I've never done this before. I feel close, but as iwconfig gives me the connection information for wlan0 as it should be I believe, I still have no connection in my browser. How can I fix this anybody? 

If I make it all the way to a successful wireless connection I will compile a step-by-step guide to getting this to work. Some help please? I'm pretty new.

---

