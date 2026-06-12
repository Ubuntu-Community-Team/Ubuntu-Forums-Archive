---
title: "Ubuntu Crisis!"
date: 2008-10-09
forum: General Help
---

### Post by catfive on 2008-10-09
Hi all.

I've been running Hardy as my primary OS for about a year now and had just started to get to the point where everything was really clicking--things were just going swimmingly.

Out of nowhere I started to get network weirdness; no dhcp without a manual dhclient command, bridged networking to VirtualBox failing after a few minutes of working fine, eth0:avahi acting strange, etc.

So, deciding it was time to build some backup/restore chops, I wiped out my system. Did a ground up install.

The network issue is *identical* on my fresh-as-a-daisy install.

Normally, I would exonerate the software at this point and look at the infrastructure, but I'm on a seriously enterprise Cisco backbone here and everything else is working great. And Ubuntu is working too after I force the dhcp request--but something about that is not right (I shudder to think what will happen when I go to re-setup the virtual networking bridge).

On top of it all, I had my dual-head configuration working perfectly before I restored. I backed up by xorg file and hoped I could just restore it, but no dice. I tried to start over from scratch but cannot get anywhere (it's an ATI card running on flgrx which adds to the pain). Why is my old xorg file not just giving me my old configuration? Is there something else I can do or is it back to the tedious, tedious manual config grinding stone?

**To recap my questions buried in this rambling post:**
Why is my network freaking out and what can be done about it?
How can I get my old X11 config working?

Thanks for any input!

---

### Post by caleb12 on 2008-10-09
The network stuff sounds kinda washy... not sure what to do about that, but I would start by examining the packages that are installed - it sounds like there is a conflict somewhere in there. I had really weird problems for a while when something auto installed resolvconf for me. I couldnt get to a webpage but I could ping any address, and to make it worse if I put the IP in the browser... of course it worked. Resolvconf was screwing with DNS config, uninstalling fixed it... Make sure the module for your card is the correct one, check DMESG for errors, etc... 

Now the ATI card... fglrx uses amdccle for configuration and unless you specifically tell it to use xorg.conf it usually doesn't pay attention to it. Check in man aticonfig but I think the command is something like aticonfig --initial --input=/etc/X11/xxorg.conf which will tell it to use the xorg.conf config. 

Hope that helps...

---

### Post by phantomgunex on 2008-10-09
Try doing a reset for your network card!

1) plug out the power cord of your computer( remember to off it!)

2) open your chasis (the casing)

3) plug out your network card completely

4) insert the network card back to the slot you plug it out from

5) thats it!

hope this works

---

### Post by catfive on 2008-10-09
Thanks for a quick response, caleb12.

I do know that aticonfig is writing to xorg.conf, it says so when I perform the command.

As far as a package conflicts go, I don't know... I mean this is still a virgin install here, and I never had a problem with my first install (until recently of course).

I would like to investigate the module for the card though, can you tell me how?

---

### Post by caleb12 on 2008-10-09
> **catfive said:**
> 

I would like to investigate the module for the card though, can you tell me how?


sudo lspci -v  will list all the devices in your system... Look for your network adapter, in that blurb will be kernel module and kernel driver in use. 

you can also lsmod to see all listed modules 

and sudo modprobe -l  will list all modules on the system, this is only useful with the grep command so perhaps something like this: 

sudo modprobe -l | grep net (this will still probably give you about 150 results) 

in case you're unfamiliar, grep is a sorting command, so you can replace the 'net' search string with wireless or the specific module to narrow down results.

It's possible that this issue has to do with the wrong module being loaded, my realtek card will sometimes load the 8139cp module instead of the 8139too - so I have to go into /etc/modprobe.d/blacklist and enter the module I don't want. Then, just for good measure, I enter the module I do want into /etc/modules 

/etc/modules tells the kernel which modules you want loaded, and /etc/modprobe.d/blacklist tells the kernel which modules to not load... that should get you started... 

In any case, if it is a module conflict chances are someone out there in internetland has come across it. A quick search on google with the name of your module should turn up most relevant results. Have a good one...

---

### Post by catfive on 2008-10-09
Phantomgunex, that sounds easy, but for me that process would involve a soldering iron (it's integrated) ;)

I do have some spare PCI NICs laying around though, maybe I'll pop one in and give it a shot.

It still doesn't sit well with me though that the exact same hardware that once worked now just doesn't!

---

### Post by caleb12 on 2008-10-09
I don't know if you had compiled your kernel while you had been running hardy for the last year. If you haven't that could be the source, if hardy's automatic upgrades gave you a new version of your kernel or a new version of the module that your network card happens to be using. That will cause problems out of nowhere... and since you re-installed - which means you were running the most current version and then re-installed the most current version... well, the problem would stay the same in that case. Dunno, just brainstorming... hope it works out...

---

### Post by catfive on 2008-10-09
That is a very good call caleb. I didn't compile the kernel. But if I had, are you saying the OS wouldn't push new modules on me?

---

### Post by caleb12 on 2008-10-09
Personally, I always compile my kernel... which adds the modules into a static location - /usr/lib/modules/linux-2.6.XX-my.kernel/  Whenever I select that kernel in grub, the corresponding modules are loaded as well. 

I've seen ubuntu update their linux image frequently, along with their locations of linux restriced modules and linux ubuntu modules. So, if these locations were updated by automatic installs, it's very possible you would be using a different kernel image and module set. 

If you can identify that the issue is coming from a module, blacklisting it will solve the problem and listing the proper module to be loaded of course. Although, personally, recompiling your kernel is always a good exercise - purely for what you learn from it. 

Check your lspci -v in a terminal, and copy and past the results of your network card... we'll see what we come up with...

---

### Post by catfive on 2008-10-09
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
	Subsystem: Dell OptiPlex 755
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at febe0000 (32-bit, non-prefetchable) [size=128K]
	Memory at febdb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ecc0 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] #13 [0306]

---

### Post by caleb12 on 2008-10-09
huh... well, it looks like you have a network card that wants to use the infamous e1000 module. This happens to be a horrible time for that... So, some things you should know: 

[http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

Now this really only applies to the 2.6.27 kernel, which supposedly has already been patched as of the rc8 release of the kernel. I'm not up for testing it though... :) 
~~
Firstly, figure out which kernel you are running  sudo uname -r - if it's in the 2.6.27 range, well I wouldnt load this module... You did say you were running hardy though, correct? This shouldnt be an issue in hardy... perhaps they have changed some of the config files, I know they blacklisted this module in Intrepid perhaps they did so in Hardy as well... 

At any rate, you can check to see if you have the module by... 

sudo modprobe -l |grep e1000

~~~
Although, what interests me is in your first post you said it will work after you force a dhcp request. Is it possible that the connection is falling back to another card, or perhaps another module? 

also try: sudo lshw -C network for good measure

post the results... and we'll see if we can narrow it down. 

~~~~~~~~~~~~~
By the way: some stuff I was finding... 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194832](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194832)

---

### Post by lisati on 2008-10-09
Caleb12: interesting call in the bug

(Thinks aloud) I'm just wondering if the router might need a restart.

---

### Post by catfive on 2008-10-15
Sorry I've been away from this for a while. Thanks for your continued support.

You're probably not going to believe this (or perhaps you will depending on your linux experience) but the issue has gone away.

At a suggestion previously in the thread, I popped in a PCI NIC that had no affect on the issue. While data mining for Caleb, I pulled it out. When I powered back up, networking was **working perfectly!**

So it's settled: if you have weird network problems in hardy, install a second NIC, but don't configure it, run it for a while, then take it out. ;) They should put that in the documentation!

I still don't understand why my exact X11 config file fails to give me anything close to the same results I had before; I think I'm going to look into an older version of flgrx.

Also, I've had some weird crashes lately, but I think Compiz is to blame (which is going away anyway when the dual-head setup comes back).

If anyone wants to jump into this with me, I'll take all the ideas I can get.

THANKS AGAIN for all the help thus far.

---

