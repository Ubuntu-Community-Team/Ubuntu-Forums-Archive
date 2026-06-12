---
title: "Intel 4965 AGN WiFi Driver"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by diatondas on 2007-03-29
Hello

I am new to this community. I've been reading these forums a lot lately and I appreciated the level of support and the politeness of the community.

I've recently got a Dell 6400 and after reviewing the pre-installed new Vista, I decided I've had enough with MS and want to gradually move as much of my computing as I can to linux. 
I've deleted everything, re-installed Vista and left a sizable separate partition to install linux as I will gradually migrate software, data, and habits to the new environment.

Before installing I want to make sure I have drivers for critical hardware components.

The laptop came with the new Intel WiFi 4965AGN adapter 
So far I haven't been able to find a driver for it.

Does anyone know if there is a driver available for it? 
Alternatively, would older drivers work with it, even with reduced functionality?

Many thanks for taking the time to read this

---

### Post by dinokpir on 2007-04-02
I am also a newbie - am interested if you try using ndiwrapper, would it work? and if so please post which dell driver you use (R#####.exe). I dont believe the intel 2200 linux driver could wotk on it. Good luck! Hopefully the support for this card comes about sometime soon.

Yoshi

---

### Post by borntoride on 2007-04-10
I'm exactly in the same case as you.

I have installed BackTrack Linux and not able to make work the wireless card (4965). Did you find a way ?

Thanks !

Jonathan

---

### Post by CrzySdrs on 2007-04-10
I too have recently gotten the 4965AGN Intel Wireless card in a my laptop (Gateway NX570X). The card shows up in lspci as:
 Network controller: Intel Corporation Unknown device 4229 (rev 61)
I have tried ndiswrapper with the 11.1.0.86 XP drivers, only to have a kernel panic upon module insertion. I haven't found any kernel options or other ways to do it and the ipw2200 doesn't work (I wasn't expecting it to). I am using Gentoo but any solutions found for Ubuntu would probably work.

---

### Post by kickabear on 2007-04-11
[http://www.intel.com/support/wireless/wlan/sb/CS-025330.htm](http://www.intel.com/support/wireless/wlan/sb/CS-025330.htm)

The Linux drivers for this card should be out by the end of June, hopefully sooner.

---

### Post by diatondas on 2007-04-12
Thanks everyone for the replies !
Unfortunatelly, I haven't managed to make it work either.
I guess I'll have to wait for Intel to release the drivers in a couple of months...

---

### Post by InfoSec812 on 2007-04-14
I seem to have had more luck than others here. I can insert the ndiswrapper module after installing the driver, and the mouse and applications still work fine. I can navigate around in KDE etc... Unfortunately, I cannot use my keyboard!!! Weird!! I am on a Toshiba Satellite A205-S4629:

T5500 CPU
2GB RAM
Ubuntu Feisty Fawn

---

### Post by rye_ on 2007-04-23
hello,

I too have the intel 4965 card and though there does not seem to be a linux compatible driver (yet)
it works perfectly well on my dell 640m laptop if ndiswrapper is used;

1) install ndiswrapper (I did it from source but I think it may be in apt)
2) look for the windows drivers on the intel website (V11.1.0.0_XP_DRIVERS.ZIP)
I think the one your looking for is netw4x32.INF

3)in the directory of the extracted driver file in the terminal type:
        ndiswrapper -i NETw4x32.INF

4)then;
        ndiswrapper -m

5)check its there with;
       ndiswrapper -l
6) I think the driver may need forwarding with (though step 3 may do this);
       modprobe ndiswrapper;


And that's it.

Some observations;

make sure that wireless is turned off when you exit/ enter ubuntu (fn + f2).  If it remains on (wireless) then ubuntu can fail to boot or shutdown.

once in ubuntu, and having switched wireless the light should flash periodically (perhaps once every 5 seconds, this is normal behaiour).

after wireless has been turned on go to the network manager (nm-applet) and deselect then reselect enable networking to restart it (right-click).  it should no become aware of the available wireless connections.

if your network manager shows no connections, check if any are available with the command;
          sudo iwlist scan


That's it.  Sorry if its over-simplified, its just a quick guide for noobs.

Ryan

---

### Post by InfoSec812 on 2007-04-25
Wow!!!! That's awesome. On my Toshiba Satellite A205, turning off the physical switch and then loading ndiswrapper, it works!!! Thanks for the tip!!!

---

### Post by renerey on 2007-05-20
i had the same problem with my new intel 4965 wifi that came with my dell laptop. i just got ndiswrapper to work. my only thing is don't get the ndiswrapper from the repositories. i read somewhere that there's a bug with it and it's not updated. go get the ndiswrapper from the ndiswrapper website. i believe it's the ndiswrapper-1.43.

---

### Post by CrzySdrs on 2007-05-20
Hey thanks renere, I updated my version of ndiswrapper to 1.43 and it worked like a charm.

---

### Post by renerey on 2007-05-22
im glad i could help. im also new to linux and this forum. there's quite a learning curve if you've come from windows. i got myself scripting to run my wifi. it sure is fun.

---

### Post by RobotJox on 2007-06-10
Hi,

I got the 4965 working with Ndiswrapper, but I experience dropouts all the time.
Now I found this project: [http://www.intellinuxwireless.org/?p=iwlwifi&n=Info](http://www.intellinuxwireless.org/?p=iwlwifi&n=Info) 
which sounds great, but I can't get the iwlwifi driver to work on ubuntu.

There are packages for many distros but no debs as far as I can see...

Any ideas?

---

### Post by renerey on 2007-06-11
hey robotjox, i have been also looking into that iwlwifi driver. i haven't seen anyone use it here in the forums so im a bit afraid to make and build it with my kernel. as the warning on the page, it may or may not work. my wireless hasn't given me any problems yet so far. let us know if it works out for you.

thanks,
renerey

---

### Post by fflarex on 2007-06-12
I doubt I'm the only one to have discovered this, but if you do a manual network configuration then you don't have to worry about disabling wireless when you boot up your system. Just right-click the network icon in the notification area, select manual configuration, select your wireless card from the window that pops up and click properties. Then enter the information about the network you want to connect to and that's it. 

In my case the only information I actually needed to provide was the name of the network, and you might also have to provide a password. Nothing technical about that at all, unless the network you're connecting to has some crazy settings. You can save the configuration as a location to easily use it again later, if you ever need to connect to another network. And if you ever need to connect to a network you don't have information about, you can always go back to roaming mode temporarily.

One slight annoyance is that the notification icon will not give you any indication that you are connected, but in my opinion this is far better than having to switch wireless on and off everytime the computer is turned on.

EDIT: Disregard everything above. This was a completely unrelated issue that happened to be fixed accidentally about the same time I changed my network preferences. If you haven't fixed the boot problem, you forgot to add ndiswrapper as a module to load during boot and it's fairly easy to figure out how to do it.

---

### Post by RobotJox on 2007-06-12
I have no problem connecting to the network, it just stops responding after a few seconds. I'm still connected, but I can't ping anything...

---

### Post by kitpierce on 2007-06-12
Hello all.  I'm using a Dell Inspiron 6400 with the Intel WirelessPRO 4965 under Kubuntu 7.04.  I have yet to get wireless to work, even though I've tried every thread I could find.  I think I might have done something wrong because when I run ***ndiswrapper -l*** I get this:

ndiswrapper -l
netw2 : invalid driver!
netw4k32 : invalid driver!
netw4v32 : invalid driver!
netw4x32 : driver installed
        device (8086:4229) present
w29n51 : driver installed

I have installed ndiswrapper using Automatix but it looks like I have installed too many drivers (after much trial and error.)  When I look under KNetworkManager it shows the wired connection, but not the wireless.  I tried disabling the connection and restarting it, but no wireless still.

Also, I think I did something that enabled wireless because my computer didn't shut down last night, which from what I hear means I have the ndiswrapper running still.

Any help getting the un-needed drivers removed and getting my wireless up and running would be MOST appreciated!

Edit:

Running **sudo ndiswrapper -e XXXX** (name of driver to remove) will remove the invalid drivers, but now I can't figure out which of the two installed drivers to keep nor how to make the wireless work.  Again, any help would be most appreciated.  Thanks again!

---

### Post by kitpierce on 2007-06-12
I got it!!!  It took me forever, but I got it up and running.

I wrote up a little how-to for how I did it under Kubuntu Feisty and [posted it here]("http://ubuntuforums.org/showthread.php?t=471794").  Hopefully it'll help some other people too.  Enjoy!

---

### Post by fflarex on 2007-06-12
> **kitpierce said:**
> Hello all.  I'm using a Dell Inspiron 6400 with the Intel WirelessPRO 4965 under Kubuntu 7.04.  I have yet to get wireless to work, even though I've tried every thread I could find.  I think I might have done something wrong because when I run ***ndiswrapper -l*** I get this:

ndiswrapper -l
netw2 : invalid driver!
netw4k32 : invalid driver!
netw4v32 : invalid driver!
netw4x32 : driver installed
        device (8086:4229) present
w29n51 : driver installed

I have installed ndiswrapper using Automatix but it looks like I have installed too many drivers (after much trial and error.)  When I look under KNetworkManager it shows the wired connection, but not the wireless.  I tried disabling the connection and restarting it, but no wireless still.

Also, I think I did something that enabled wireless because my computer didn't shut down last night, which from what I hear means I have the ndiswrapper running still.

Any help getting the un-needed drivers removed and getting my wireless up and running would be MOST appreciated!

Edit:

Running **sudo ndiswrapper -e XXXX** (name of driver to remove) will remove the invalid drivers, but now I can't figure out which of the two installed drivers to keep nor how to make the wireless work.  Again, any help would be most appreciated.  Thanks again!

You need to install the latest version of ndiswrapper from *source*, because the versions in the ubuntu/automatix repos are outdated. Removing the redundant drivers couldn't hurt either.

---

### Post by stchman on 2007-06-12
> **diatondas said:**
> Hello

I am new to this community. I've been reading these forums a lot lately and I appreciated the level of support and the politeness of the community.

I've recently got a Dell 6400 and after reviewing the pre-installed new Vista, I decided I've had enough with MS and want to gradually move as much of my computing as I can to linux. 
I've deleted everything, re-installed Vista and left a sizable separate partition to install linux as I will gradually migrate software, data, and habits to the new environment.

Before installing I want to make sure I have drivers for critical hardware components.

The laptop came with the new Intel WiFi 4965AGN adapter 
So far I haven't been able to find a driver for it.

Does anyone know if there is a driver available for it? 
Alternatively, would older drivers work with it, even with reduced functionality?

Many thanks for taking the time to read this

The 4965 is not supported by Ubuntu.  You can get a 3945 wireless card for around $30 and they work quite well.  Both cards have teh same physical dimensions so you can swap them out.

---

### Post by kuscsik on 2007-06-19
I wrote a small preliminary HOW-TO for the iwlwifi driver. 

[http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html)

Any feedback is wellcome. Good luck.

Zoltan Kuscsik

---

### Post by vronp on 2007-06-19
> **stchman said:**
> The 4965 is not supported by Ubuntu.  You can get a 3945 wireless card for around $30 and they work quite well.  Both cards have teh same physical dimensions so you can swap them out.

This wasn't a very helpful post.

The Intel Linux drivers for the 4965 should be out any day now.  I would do some extensive searching for "4965" on these forums before you make a decision about getting a new card.

I have the 4965 in a brand new laptop and I'm going to wait for the Intel drivers.  In the meantime, I'm using a Linksys USB wifi setup.

---

### Post by vronp on 2007-06-19
> **kuscsik said:**
> I wrote a small preliminary HOW-TO for the iwlwifi driver. 

[http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html)

Any feedback is wellcome. Good luck.

Zoltan Kuscsik

Zoltan,

Thanks for doing this.  I ran into a problem (I think).  I followed the instructions but got a Segmentation Fault on the last step:

 sudo modprobe iwl4965
Segmentation fault

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] Oops: 0002 [#1]

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] SMP 

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] CPU:    0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] EIP:    0060:[<f9132975>]    Tainted: P      VLI

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] EFLAGS: 00210246   (2.6.20-16-generic #2)

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] EIP is at iwl_pci_probe+0x95/0x1250 [iwl4965]

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] eax: c211f048   ebx: ebcb81c0   ecx: 00000000   edx: ebcb8040

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] esi: c211f000   edi: f9150280   ebp: 00000000   esp: e3a7bdd0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] Process modprobe (pid: 3238, ti=e3a7a000 task=e4ff0a90 task.ti=e3a7a000)

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] Stack: 0000a1ff c21266c0 c01b805c 00000000 c01b8015 c21266c0 00200246 c0379c2f 
dave@9400:~/Desktop/4965/iwlwifi-4965-ucode-4.44.15$ 
Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]        c0379c36 ee57bc87 c01b8eee 0000a1ff 00000020 f91502cc 00000000 c211f0c0 

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]        c01fb963 f91328e0 c211f000 f9150280 f91502b4 c01fba86 c211f048 c211c048 

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] Call Trace:

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [sysfs_make_dirent+28/144] sysfs_make_dirent+0x1c/0x90

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [sysfs_dirent_exist+69/112] sysfs_dirent_exist+0x45/0x70

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [sysfs_create_link+110/352] sysfs_create_link+0x6e/0x160

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [pci_match_device+19/192] pci_match_device+0x13/0xc0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [<f91328e0>] iwl_pci_probe+0x0/0x1250 [iwl4965]

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [pci_device_probe+86/128] pci_device_probe+0x56/0x80

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [really_probe+102/400] really_probe+0x66/0x190

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [driver_probe_device+73/192] driver_probe_device+0x49/0xc0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [__driver_attach+158/160] __driver_attach+0x9e/0xa0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [bus_for_each_dev+59/96] bus_for_each_dev+0x3b/0x60

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [driver_attach+36/48] driver_attach+0x24/0x30

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [__driver_attach+0/160] __driver_attach+0x0/0xa0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [__pci_register_driver+116/192] __pci_register_driver+0x74/0xc0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [<f8fdc02b>] iwl_init+0x2b/0x76 [iwl4965]

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [sys_init_module+349/7072] sys_init_module+0x15d/0x1ba0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [sys_mmap2+205/208] sys_mmap2+0xcd/0xd0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  =======================

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] Code: 24 08 a9 20 14 f9 c7 04 24 40 70 14 f9 25 00 ff ff 0f 83 f8 01 19 c0 83 e0 0c 83 c0 49 89 44 24 04 e8 a0 42 ff c6 8b 6b 5c 31 c9 <89> 5d 00 8d 95 10 2b 00 00 89 b5 7c 05 00 00 a1 10 11 15 f9 89 

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000] EIP: [<f9132975>] iwl_pci_probe+0x95/0x1250 [iwl4965] SS:ESP 0068:e3a7bdd0

Message from syslogd@9400 at Tue Jun 19 12:57:43 2007 ...
9400 kernel: [129402.848000]  [bus_add_driver+123/416] bus_add_driver+0x7b/0x1a0

---

### Post by kuscsik on 2007-06-19
Another solution is to install the latest ndiswrapper driver (1.47) but I experienced some stability problems (some people wrote it is ok with the specific wireless card).
 I have no problem with installation of iwlwifi on gutsy and feisty. I am not a kernel guru so I am not able to debug the posted message. Intel says,  the official driver will be out in few weeks.

---

### Post by vronp on 2007-06-19
Zoltan,

Does your blog cover every step?  I was wondering about the mac80211 stuff and wanted to be sure there were no missing steps.

thanks

---

### Post by kuscsik on 2007-06-20
I tried these steps on gutsy and feisty machine with kernels: 2.6.22 and 2.6.20-16-server. As I understood, the step "make patch_kernel" patches the mac80211 in to the kernel source.
Without this step, iwlwifi compilation fals.

---

### Post by vronp on 2007-06-20
> **kuscsik said:**
> I tried these steps on gutsy and feisty machine with kernels: 2.6.22 and 2.6.20-16-server. As I understood, the step "make patch_kernel" patches the mac80211 in to the kernel source.
Without this step, iwlwifi compilation fals.

Hi,

I don't have any compilation failures.  My problem occurs when I run the modprobe command; the last step.

If I reboot, the reboot hangs until I blacklist those modules.  I posted a bug about this with the Intel folks.

I am hoping others can try this and let us know what happens.

---

### Post by kuscsik on 2007-06-21
> **vronp said:**
> Hi,

I don't have any compilation failures.  My problem occurs when I run the modprobe command; the last step.

If I reboot, the reboot hangs until I blacklist those modules.  I posted a bug about this with the Intel folks.

I am hoping others can try this and let us know what happens.

1. Please check whether you have other wireless drivers loaded before modprobe the 4965 drivers

```

lsmod | grep 3945
lsmod | grep ipw2200
lsmod | grep ndiswrapper

```

If yes, try to unload them with rmmod command. 

2. Try to load the module with physical wireless switch On and Off

Thx

Zoltan

---

### Post by Fortean on 2007-06-21
Kuscik, I think there's a step missing from your guide. You're patching the mac80211 patches into the kernel but you're not compiling anything against the patched source. It's quite natural that there are problems since iwlwifi cannot load against the kernel mac80211 module, making the system unbootable.

Could you please check your instructions once again? TIA.

EDIT: Apologies, works fine in gutsy... No idea why it doesn't work in feisty, though...

---

### Post by RobotJox on 2007-06-21
kuscsik - THANK YOU SO MUCH!!!!!!!!!!

your guide worked for perfectly me - but only running Gutsy - Feisty fails on me, but what the heck - I have a WORKING wifi-card now.

The only thing I have to do - for some odd reason - is to turn my ethernet card on and off, whenever I reboot.

Thank you!

---

### Post by colby500 on 2007-06-24
followed rye_'s post on the first page and I was able to get my 4965 card to work with my t61.

---

### Post by syxbit on 2007-06-26
i followed that guide too, but i still get constant disconnects.
i was initially having to modprobe ndiswrapper every time, so i added ndiswrapper to /etc/modprobe

---

### Post by stchman on 2007-06-26
You can get a 3945 Intel card for your laptop and it works perfectly under Ubuntu.

The 3945 and the 4965 are the same dimension so it will fit.  You can get this card for around $30.  I have seen them new on ebay even cheaper.

If the card will fit properly an Atheros card will work well too.

---

### Post by syxbit on 2007-06-26
but we don't want to buy a different card.
ideally, someone could figure out how to use the actual linux drivers
ndis is lame. i keep getting disconnected

---

### Post by ktakahashi on 2007-06-27
I was able to use the intel driver on feisty with the 2.6.22 kernel backported from gutsy.

Has anyone else been able to do this?

---

### Post by stchman on 2007-06-27
> **syxbit said:**
> but we don't want to buy a different card.
ideally, someone could figure out how to use the actual linux drivers
ndis is lame. i keep getting disconnected

You need to figure out HOW much time you are going to spend in this endeavor.  Since you can get the 3945 which works perfectly with Feisty for a pretty cheap price, then that is a good alternative.

If you wait a few more months, it sounds like Gutsy supports the 4965.

It is your choice.

---

### Post by Krymzon on 2007-06-28
I actually paid extra for upgrading from 3945 to 4965 which was normally unavailable for my laptop =/ I expected some problems with it at the beginning, but I hope I'll be able to use it in two months… As its the standard Santa Rosa card, soon there will be plenty of users with it.

---

### Post by VeloSol on 2007-06-29
Please read Zoltan's blog for a complete rundown of what I was trying to do - the short version is installing .34 drivers after having disabled the radio from within Windows Vista - it didn't help it.

Posting back here from windows - I did all the install and I went to reboot after reading about getting my 965GM/X3100 working with the latest drivers from git and the computer doesn't boot!  I eventually get it to fail out to a prompt by getting out of the splash with Alt+F1 and then Ctrl+Alt+Del and iwl4965 is loading, yet I hadn't modprobe'd it...  Trying to blacklist again so I can boot, but as of yet I was unable to get iwlwifi/iwl4965 with the .34 drivers.

Also posted at zoltan's page.

---

### Post by rye_ on 2007-06-29
hi all,

First of all the drop-outs with ndiswrapper; (which tend to occur occasionally).  I tend to find the following is the best solution;

1. Create a (very) small script as follows; (in order to reinsert the ndiswrapper module)

#!/bin/bash

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

2. place the script on the desktop and change its properties to make it executable

3. on experiencing a drop-out;

3.1 switch off wifi (i.e. fn+f2)
3.2 execute the script (i.e. double click, select run in terminal, and type in password)
3.3 switch wifi back on 

-------------------------
-------------------------

the description may seem messy but its actually very quick and simple, even if not ideal.

------------------------
-----------------------

as far as using the gutsy kernel in feisty, I tried this without any acknowledging from the OS.
and in using the feisty kernel my system kaputs.
I think I'll wait a couple of months until the iwlwifi team release a stable version.

Ryan

---

### Post by B-jammin on 2007-06-29
I've got my 4965AGN intel card working with ndiswrapper.  although sometimes I run into the problem of the crashes on reboot even though i thought i disabled the card completely.  i try turning the adapter on at different times during boot and when it logs in and sometimes i can get the right combination that works after a few tries.  does anyone know a quick way to solve this problem?   

Last time I logged into a safe terminal then "sudo reboot"  and it boot up fine.  Feedback anyone?

---

### Post by rye_ on 2007-06-30
could you post a little more more information.

version of ndiswrapper,
the version of the windows wireless driver you use

the result of ndiswrapper -l. i.e. does your computer recognise the driver.

also might be of interest to post you computer model.

Ryan

---

### Post by B-jammin on 2007-06-30
I'm using ndiswrapper v1.38 with the Windows XP Professional 4965AGN drivers from the Intel site.  

ben@ben-laptop:~$ ndiswrapper -l
netw4x32 : driver installed
        device (8086:4229) present

The device works once the computer finally starts up I'm posting with it now.  The problem is even if i disable everything it still crashes on startup.

---

### Post by ciphermonk on 2007-07-01
I would get away from using ndiswrapper. It's messy at best and not necessary for getting the 4965 card working. You can follow the procedure that I posted below to get the card working the "right" way using the opensource intel drivers.

[http://forums.fedoraforum.org/forum/showthread.php?t=159550](http://forums.fedoraforum.org/forum/showthread.php?t=159550)

---

### Post by rye_ on 2007-07-01
b-jammin,

ceratinly I'd have a go at the previous messages method. (I intend to try this today).
One thing though; when messing around with low level stuff like this its often a good idea to 
have two kernels to boot into, such that if one fails, you can always boot into the other.

But failing that, for using ndiswrapper you really need to build the latest version from source (1.47).
When using you'll find that within a couple of minutes, the connecting goes down. If you do as I posted previously (i.e. remove and reinsert the ndiswrapper module) the connection should be stable indefinately.
This method is not too troublesome.

Ryan.

---

### Post by ciphermonk on 2007-07-01
theres not any risk bjammin. the method that i gave "adds" an additional boot option. it doesn't replace the kernel that you're using now.

BTW... some of the instabilities/crashes that you guys are experiencing with ndiswrapper have to do with the kernel using 4K stacks instead of 8k. If you compile your own kernel and disable 4K stacks, ndiswrapper will work much better. If you're going to do that though, you might as well use the drivers on intellinuxwireless as they're what are designed to run under linux and support things that ndiswrapper doesn't

---

### Post by ehmdjii on 2007-07-01
> **VeloSol said:**
> Please read Zoltan's blog for a complete rundown of what I was trying to do - the short version is installing .34 drivers after having disabled the radio from within Windows Vista - it didn't help it.

Posting back here from windows - I did all the install and I went to reboot after reading about getting my 965GM/X3100 working with the latest drivers from git and the computer doesn't boot!  I eventually get it to fail out to a prompt by getting out of the splash with Alt+F1 and then Ctrl+Alt+Del and iwl4965 is loading, yet I hadn't modprobe'd it...  Trying to blacklist again so I can boot, but as of yet I was unable to get iwlwifi/iwl4965 with the .34 drivers.

Also posted at zoltan's page.

i can confirm this. when modprobing the iwl4965 the script seems to hang and the system wont boot anymore without blacklisting those modules

hopefully the intel guys fix this soon!

---

### Post by rye_ on 2007-07-02
ciphermonk

I've tried compiling the kernel as outlined in your guide and I'm afraid I get a kernel panic on reboot.


Ryan.

---

### Post by ciphermonk on 2007-07-02
This is on a T61 and you used my supplied kernel config file?

---

### Post by rye_ on 2007-07-02
I'm using a dell 640m core 2 duo.

yes, I used your config file.

Ryan.

---

### Post by ciphermonk on 2007-07-03
I can't see their being that big a difference in internal hardware between the Dell and Lenovo with the exception of perhaps the processor. That very config is working on T61s, so perhaps open up menuconfig and play with some of the options under processor and Dell Laptop support. I believe that I did turn some of the Dell specific stuff off, but you can always double check me. If I had to guess though, I'd probably say that the processor selection in my config is what's causing your machine to hang. What error does it throw before it Panics?

---

### Post by TeeJR on 2007-07-03
> **ciphermonk said:**
> theres not any risk bjammin. the method that i gave "adds" an additional boot option. it doesn't replace the kernel that you're using now.

BTW... some of the instabilities/crashes that you guys are experiencing with ndiswrapper have to do with the kernel using 4K stacks instead of 8k. If you compile your own kernel and disable 4K stacks, ndiswrapper will work much better. If you're going to do that though, you might as well use the drivers on intellinuxwireless as they're what are designed to run under linux and support things that ndiswrapper doesn't

How can I check the buffer size? I had a suspicion about this since downloading large files is what causes the driver to stop working in my case. If I just surf the web and get email and stuff like that I can go for hours and hours, but as soon as I try to download a large file; I would say around 10 meg or greater, then the driver stops working. Small files are fine; I actually experimented to make sure. ndiswrapper also stops working if I watch any videos on Google videos. This is clearly a problem with downloading and not Google video.

As interesting as spending time building a Kernel sounds, I'd rather make sure that's what I need to do first.

Laptop Setup:
7.04 Feisty
I am using a Toshiba P205-S6267
4965AGN wireless with ndiswrapper and the Intel 11.1.1.11 drivers.

---

### Post by ciphermonk on 2007-07-03
If you haven't changed it, then it's most likely set. It's pretty much the default in most of the distros that are shipping these days. If you have access to the kernel config for the kernel that you're currently running,    grep for "4K" in that file... It'll probably return a line that looks like

CONFIG_4KSTACKS=y

To my knowledge, the option to turn that off doesn't exisit in menuconfig anymore. You have to edit .config manually, set that directive to "n" and then recompile the kernel and modules.

---

### Post by TeeJR on 2007-07-03
Thanks

I actually printed  a copy of your instructions from the FedoraForum.org. I am not familiar with building a kernel since I'm a Windows convert. I have downloaded the latest kernel and will follow the instructions on your other post.

---

### Post by ciphermonk on 2007-07-03
That's honestly the best option in my opinion. Using ndiswrapper is a bad hack at best. A bg part of why the kernel developers made it more difficult to use stacks bigger than 4K, is that you end up wasting more memory as well as to discourage the use of things like ndiswrapper. The how-to that I wrote up is fairly detailed and should be able to get you up and going without much issue. Let me know if you run into any problems.

---

### Post by rye_ on 2007-07-03
Thankyou ciphermonk,

if the tone of my previous posts haven't shown it (as I look over them now) I very much appreciate your input, the 4965 has been an irritating problem for a number of us on this forum.  I'll have a go at your suggestion.

am I  correct in that are primarily a fedora core user, rather than  a Ubuntu user?
As you seem to be a much more experienced linux user than myself (I've used suse, ubuntu, sabayon) does fedora core offer something that ubuntu doesn't? (just a point of interest)

Ryan

---

### Post by ciphermonk on 2007-07-03
Not a problem Ryan. I'm always glad to help out in any way that I can. Getting wireless working on linux is normally a point of frustration for people; even experienced administrators. Sharing information is the only way to make it easier  for everyone involved. 

As far as linux distributions go, I primarily work with RedHat Enterprise Linux at my job so using Fedora just makes sense for me. Since '96 though I've run Caldera, Redhat Debian,Slack, Gentoo, Yellowdog, RHEL, and currently Fedora. Every distribution has it's good points and bad points. 

I end up doing a custom kernel and rebuilding some of the libraries no matter what I run, so in the end, Fedora just ends up being another linux distro that happens to use RPM as the package manager. As far as working very well with the most hardware out of the box, Ubuntu does very well. I wouldn't necessarily change unless there's something about it that you dislike or if there's something about another distro that you'd like to try out. At the end of the day it's all Linux. Let me if I can help out...

---

### Post by ehmdjii on 2007-07-09
the guys at intellinuxwireless have a new release up.

has anyone gotten it to work so far?

thanks!

---

### Post by Merritt.kr on 2007-08-26
Hello, I think I need a little help if you're willing.

I followed your guide at [http://forums.fedoraforum.org/forum/showthread.php?t=159550](http://forums.fedoraforum.org/forum/showthread.php?t=159550)

First understand I've been using Linux for 3 months and I've never compiled a kernel before!
I'm running Feisty Fawn on a Dell 6400 with Core 2 Duo.


I thought your config file would take care of all the question answering, but it only seemed to answer about 95% of questions, the rest I filled in a best I could. :confused: Regarding someone's earlier post, during those questions one was about CPU, and I chose Core 2. So I'm not sure if THAT is a problem.

After a loong time, it finally finished, and I rebooted, however the only options for kernel were the ones I had before (2.6.20-15-generic and 2.6.20-16-generic). I went to check my grub.conf only to find out I apparently don't have one. I only have /boot/grub/menu.lst  .... so maybe this is why it didn't load properly. I attempted to add the 2.6.22.5 kernel I compiled manually, but after choosing it upon boot I got a kernel panic as follows:

```
Starting up ...
Uncompressing Linux ... Ok, booting the kernel.
Kernel panic - not syncing:VFS:Unable to mount root fs on unknown-block(0,0)
```

Here was my menu.lst:

```
title		Ubuntu, kernel 2.6.22.5
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22.5 root=UUID=98d90b42-bb88-4bd4-a632-3dec5e384e6b ro quiet splash
initrd		/boot/initrd.img-2.6.22.5
quiet
savedefault

title		Ubuntu, kernel 2.6.22.5 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22.5 root=UUID=98d90b42-bb88-4bd4-a632-3dec5e384e6b ro single
initrd		/boot/initrd.img-2.6.22.5

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=98d90b42-bb88-4bd4-a632-3dec5e384e6b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=98d90b42-bb88-4bd4-a632-3dec5e384e6b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

after that I tried update-grub, but the same Kernel Panic occured. Here was menu.lst then:

```
title		Ubuntu, kernel 2.6.22.5 Default
root		(hd0,0)
kernel		/boot/vmlinuz root=UUID=98d90b42-bb88-4bd4-a632-3dec5e384e6b ro quiet splash
quiet
savedefault

title		Ubuntu, kernel 2.6.22.5 Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=UUID=98d90b42-bb88-4bd4-a632-3dec5e384e6b ro single

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=98d90b42-bb88-4bd4-a632-3dec5e384e6b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=98d90b42-bb88-4bd4-a632-3dec5e384e6b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

I was quite afraid I would not be able to boot at all, but I can still get in my 2.6.20-15 kernel. So I am now stuck. Any advice would be greatly appreciated. Thanks in advance.

---

