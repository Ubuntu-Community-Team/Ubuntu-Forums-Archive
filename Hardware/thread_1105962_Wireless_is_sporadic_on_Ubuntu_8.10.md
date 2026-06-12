---
title: "Wireless is sporadic on Ubuntu 8.10"
date: 2009-03-25
forum: Hardware
---

### Post by ccotton333 on 2009-03-25
I'm running a Ubuntu 8.10 Dell Inspiron 600 with 1GB of RAM and a Intel 2200 built-in wireless card. I have other laptops that run windows and connect to my netgear wireless well. Any ideas of what I could do to make it more stable? It jumps on and off constantly. Is there some setting that could fix this?  When this laptop was running Windows it would at least stay on the wireless!!!

---

### Post by coffeecat on 2009-03-25
My Sony laptop has the same wireless chip, and it keeps a reliable wireless connection with both 8.04 and 8.10. I wonder if it might be a hardware fault that has developed. Have you got a little hardware switch for switching the wireless on and off? Many laptops do. Make sure it's securely switched on.

Have you got any live CDs of any other distros that can run the Intel 2200 chipset out of the box? Ubuntu 8.04, recent Fedoras and PCLinuxOS 2007 spring to mind. (Not PCLinuxOS 2009 - it doesn't, at least not in my experience.) Or possibly a recent Mandriva. Try connecting wirelessly while running live. If you get a stable connection then it must be something to do with your 8.10 installation. If not, it's more likely to be a hardware problem.

---

### Post by ccotton333 on 2009-03-25
I don't have a hardware switch. It's all software based. I wondered if it might be that my wired interface it active even though it's not getting and IP or even connected. I guess I could try that, but I'm not sure why that would matter... I mean I did run my wireless fine on the live cd but when i installed it had some issues and I had to change some settings to get it to work,  The drivers had to be installed as well i believe it just didn't install correctly during the install process. I installed a older Ubuntu and it worked from the beginning a couple years ago and then I had to convert because Wine wasn't stable enough to run some of my apps back then. Now Wine works much better and I can run everything in Ubuntu so I'm back to Ubuntu.  I just wish i could figure out what's going on.

---

### Post by coffeecat on 2009-03-25
> **ccotton333 said:**
> I wondered if it might be that my wired interface it active even though it's not getting and IP or even connected. I guess I could try that, but I'm not sure why that would matter...

No, that shouldn't matter. If an ethernet cable isn't plugged in, wireless should work just fine.

But....

> **ccotton333 said:**
> I mean I did run my wireless fine on the live cd but when i installed it had some issues and I had to change some settings to get it to work, The drivers had to be installed as well i believe it just didn't install correctly during the install process.

Aha! You didn't say this wasn't a vanilla install as far as wireless is concerned. [-X :wink:

It *should* work just fine ootb with the Network Manager applet. I don't know why you had some issues when you first installed, but if you've installed some additional drivers, I guess you're using wicd or ndiswrapper or madwifi or something. In which case I haven't a clue, and I have no idea how you would clean up the system to get yourself back to a vanilla Network Manager.

Two suggestions:

Post details of exactly what you've installed for wireless and someone with experience of whichever box of tricks it is may be able to help you. Perhaps NM is fighting with whatever else you've installed.

or

Think of reinstalling and relying on Network Manager.

---

### Post by ccotton333 on 2009-03-25
Hey sorry for the confusion. Yes it is a vanilla install. I installed network manager and everything like the forums said. I read about ndiswrapper but never used it. I'm not sure what the rest of those are.  I downloaded network manager through Synaptic and did the installation through there. When I get home, I'll try to check for ndiswrapper and anything else, but I didn't install that unless it was installed with Network Manager.  I installed some other utilities but nothing that would have any effect on the wireless or any of the network connections.  I guess i could try uninstalling network manager and reinstalling it? I'm really not sure. If it worked on the live cd there should be a simple package that i should install that will make it work without any special configuration. Right?

---

### Post by coffeecat on 2009-03-25
> **ccotton333 said:**
> Yes it is a vanilla install. I installed network manager and everything like the forums said.

<snip>

I downloaded network manager through Synaptic and did the installation through there.

Now I'm confused. Ubuntu comes with Network Manager already in the tin so to speak. In fact it's what the live CD uses for all network management. Hence the name. :p So I can't understand how or why Synaptic let you install NM when it was already installed. :?

OK. Don't install ndiswrapper and all the rest. You shouldn't need any of them. This is what should have happened:

Install Ubuntu. Do first boot. Once the desktop has loaded, click on the Network manager applet icon at top right and a small menu drops down showing you wireless networks in range. You click on the one it wants, it prompts you for the WEP or WPA passphrase and you're connected. First time round it probably prompts you for a keyring password as well, but after that it should simply autoconnect every time you boot up.

And that's what happened for me. Honest.

All I can suggest is to right click on the NM applet icon and choose 'Edit Connections'. Click on the Wireless tab and remove any and all entries there. Close that Window. Now left click on the NM icon, choose your wireless network and type in your passphrase as before.

I'm not sure that will help, but it's worth a try. And I'm still puzzled about installing an app that's already there. Right-click on the NM icon again and choose 'about'. Is it version 0.7.0?

---

### Post by ccotton333 on 2009-03-25
I just got my wife to take a look at my PC. Ok here is the deal without further testing. I had a old Ubuntu 8.06 Dapper disc.  I installed that. once that was up and running, it asked me to upgrade to 8.10. So i did the upgrade to 8.10. I then couldn't get on my wireless, and so I installed network manager. I then installed Wine and a couple other apps.  Somehow and I'm not completely sure how or why, ndiswrapper had been installed. Whatever the case I got her to uninstall ndiswrapper, and check to be sure i still have internet, which i did.  I'm not sure if that was the problem or not.  I will check it out this evening and post back in the AM.

---

### Post by ccotton333 on 2009-03-26
Ok well I tested again last night after removing ndiswrapper. Same problem. I was kicked off my wireless in the middle of the game. I had my older XP laptop along side and this time it couldn't get out, which appeared to be a WAN issue since i could still get to my router.  I went and plugged in the laptop direct to the router and after a while same thing (got kicked off) however i would get out on my XP laptop for internet.  I upgraded the router's firmware and played and it seemed to be working then. However I didn't play very long.  I'll have to try another stress test or two to figure this out. The firmware upgrade didn't say anything about network issues. Maybe it was the restart that it needed. I restart it fairly frequently though... I'm not sure what's going on with this.  Another thing i wish i could figure out is why when i run apps though Wine my CPU spikes but that's another question all together. anyways. I will check again tonight and get the results of that test in. Thanks for all of your help.

---

### Post by ccotton333 on 2009-03-27
Ok maybe there is a deeper issue here... I installed Ubuntu on a Intel P4 2.4 GHz (not dual or quad core), 512MB of RAM, and 32 MB ( yes it was the only video card I had spare at the time). Ubuntu and Wine installed. I can play my game great. the graphics are much better than my Laptop and it has a 64MB video card and 2 GB of RAM.  What gives?  Is there something that I'm missing here? I mean for it to run on that old video card and older than that NIC something has to be up.   Or are the devices made a long time ago built that much better than the ones today? (that was prolly a stupid question) Point being that I still am having problems with my laptop. I'm just trying to understand what could be causing this.  Is my laptop by chance not throttling/scaling the CPU correctly? would that be the cause?

---

