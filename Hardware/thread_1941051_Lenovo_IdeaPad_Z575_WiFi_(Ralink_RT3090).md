---
title: "Lenovo IdeaPad Z575 WiFi (Ralink RT3090)"
date: 2012-03-14
forum: Hardware
---

### Post by gdea73 on 2012-03-14
Well I got my IdeaPad in the mail today and immediately opened it, formatted the entire drive, and installed Ubuntu 10.10. My first and only challenge so far has been getting the wireless to work. Each thing I've tried so far, possibly incorrectly, I've undone individually so I'm open to any troubleshooting / driver-finding advice.

According to Lenovo's records on my serial number, the laptop in question has a Ralink RT3090 PCIe wLAN chipset. I tried installing Ralink's drivers, but after doing so the "Additional Drivers" menu told me that "rt3090sta" was activated but not currently in use. Network manager says that wireless is disabled. My laptop's LEDs say that wireless is enabled correctly.

EDIT: It appears that I've finally found a solution; my wireless is working quite well now. See my last post for a quick-and-dirty tutorial, which I plan on editing/merging with something else, later. ;)

---

### Post by gdea73 on 2012-03-15
Well now my current problem, after trying many things and undoing them, is merely compiling Ralink's drivers from their website. I was told to install build-essential and linux-headers-generic, and it worked once, but now I get error 2 when trying to compile anything. I've tried reinstalling linux-headers-generic, but I still get the following error message:

```
*** /lib/modules/2.6.35-22-generic/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

```

---

### Post by gdea73 on 2012-03-15
I fixed the previous problem by installing not only Linux-headers-generic, but also the headers specific to my kernel version (linux-headers-2.6.35-22-generic). However I still can't get the "rt3090a" module to load, it says the device is busy.

---

### Post by Bucky Ball on 2012-03-15
Try uninstalling everything you've installed from the Ralink site (or blacklist that driver) and activate and use only the driver Ubuntu has automagically offered in 'Additional Drivers'. Sounds to me like you are getting some conflicts (the driver offered and activated by Ubuntu and the driver you have installed are both loading/loaded).

*Always* plug in the cable first, get online, get updates, check additional drivers (some cards are installed in a couple of clicks this way) and use the driver/firmware offered to see if that works FIRST before going on a wild goose chase attempting to install and compile drivers manually. You can save that for if the driver/firmware is not offered or what is offered doesn't work. ;)

Still no luck? Try this:

[https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

... or dig around in here for clues:

[http://www.google.com.au/#hl=en&sclient=psy-ab&q=Ralink+RT3090+ubuntu+10.10&oq=Ralink+RT3090+ubuntu+10.10&aq=f&aqi=g-v1&aql=&gs_sm=3&gs_upl=2718l7813l0l8648l14l10l0l4l4l2l437l2649l2-9.0.1l14l0&gs_l=hp.3..0i15.2718l7813l0l8648l14l10l0l4l4l2l437l2649l2-9j0j1l14l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597](http://www.google.com.au/#hl=en&sclient=psy-ab&q=Ralink+RT3090+ubuntu+10.10&oq=Ralink+RT3090+ubuntu+10.10&aq=f&aqi=g-v1&aql=&gs_sm=3&gs_upl=2718l7813l0l8648l14l10l0l4l4l2l437l2649l2-9.0.1l14l0&gs_l=hp.3..0i15.2718l7813l0l8648l14l10l0l4l4l2l437l2649l2-9j0j1l14l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597)

But again, you possibly have conflicting drivers and may need to uninstall or blacklist what you have manually installed to check if the one offered works (and if it is in Additional Drivers it should) ...

---

### Post by gdea73 on 2012-03-15
hey Bucky Ball, I appreciate your help with this. The reason I went directly to Ralink's website is because the Additional Drivers (jockey-gtk) utility didn't offer any for my wireless, only for the AMD Hybrid Graphics, which I have yet to configure. The only reason "rt3090sta" was ever listed as a module there was after it was stalled manually, so I guess it comes up as if it were installed via the Additional Drivers utility, as a custom-compiled kernel module.

I've made a bit more progress with my laptop; I've realized that suspend somehow/finally works, and also regarding the wireless chipset. I used this thread ([http://ubuntuforums.org/showthread.php?p=11768543#post11768543](http://ubuntuforums.org/showthread.php?p=11768543#post11768543)) for my guide, replacing all directions with RT2080, or whatever the chipset in question was, with RT3090. I also disabled the "80211" support in the config.mk file, as that was part of another solution I found might be worth trying, I never use 802.1x authentication and IIRC it only caused problems connecting to WEP networks on WinXP. Anyway, I got the module to compile correctly. I previously got an error sort of like "device busy" when running sudo modprobe rt3090sta. Now I get nothing, which is apparently good. The problem is, network manager still says "device not ready" when I try to use my wireless. Not sure where to go from here, but I'll do what I can and post back...

---

### Post by gdea73 on 2012-03-15
Awesome! I've finally got the mystery that is the Ralink RT3090 solved on Maverick! Unfortunately I'm not exactly sure what I did, but I can give a general idea of how to get it working for those who need it (fellow Lenovo users, I may also post on the Lenovo forums once I sort out exactly what it was that I did).

I used a combination of fixes. First, follow__ [this tutorial](http://ubuntuforums.org/showthread.php?t=1476007), which was wonderful. Remember to replace any references of the RT2800, or whatever other adapter they were referring to, to RT3090. Also, don't follow the blacklisting module part. I did that separately. Important note: in the Config.mk file, I also searched for "80211," and put an N, to disable the according line. Try that, it may help you as well.

Now the part that truly fixed this was, actually twofold: 1, the acer_wmi module needed to be removed (rmmod'ed) and blacklisted (I'll elaborate...), and 2, blacklisting the other Ralink chipset modules. Here's what I think I did:

Before you really do anything, make sure you run ifconfig wlan0 down (?), and afterward you can run ifconfig wlan0 up. Also, restart network-manager (sudo restart network-manager), when you're done. And reboot, if it doesn't work right away.

1. Open a terminal, and you may as well type "sudo su" so that you don't have to type sudo for the rest of the commands. Then run "lsmod | grep rt." Look at the list of modules included. Besides "paraport," those others need to be removed. I'll show you how.

2. Run the command "gksudo gedit /etc/modprobe.d/blacklist.conf" to open the blacklist configuration file. Skip to the bottom (Ctrl + End), and add the following lines, according to the previous command. Slashes should indicate line breaks, so add each chunk of text separated by a forward slash on its own line at the end of the file. "blacklist rt2800pci / blacklist rt2800usb / blacklist rt2800lib / blacklist rt2x00usb / blacklist rt2x00pci / blacklist rt2x00lib". I think it helps to do it in that order as one of the rt2x00 modules depends on rt2800lib, as you'll see if you rmmod them manually. **Also, I added "blacklist acer_wmi", which is an important part of the solution.**

3. Re-enable wireless and reboot. At this point it worked for me. Results may vary.

I'll write a true tutorial, perhaps in a separate thread later, and when that's done I'll link to it here in this thread. At the moment this is just an excited list of all the random things I tried; eventually, I plan on organizing it into a help page for others struggling with the RT3090 chipset. Also to note, I didn't use the precompiled package available from That Guy's repository; I compiled it myself. To do so I needed to not only install "linux-headers-generic," but the ones that pertained specifically to my kernel, i.e. "linux-headers-2.6.35-22-generic," otherwise the make command would result in an error 2. Good luck! 

If you have problems following what I wrote (very possible), please post here and I'll try to help, as we'd be helping many others if we can solve your problem.

---

### Post by Bucky Ball on 2012-03-15
> **gdea73 said:**
> 

If you have problems following what I wrote (very possible), please post here and I'll try to help, as we'd be helping many others if we can solve your problem.

Indeed you would as this appears a tricky beast. Great news! Enjoy ... ;)

---

### Post by gdea73 on 2012-03-17
Also, the guide is still somewhat disorganized, but I figured I'd correct a bit of it in a new post as I just redid the whole process. (I had to reformat for a different reason and was glad I essentially wrote myself a public guide on how to redo this! XD)

But some things I may have left out which were necessary at some point: rfkill list all, rfkill unblock all, sudo rmmod acer_wmi (manually remove the acer module, this was very important), also ifconfig is helpful to see if your wireless is "up"/listed yet.

And to help document some errors, when I ran "modprobe rt3090sta" I got an "operation not permitted" error until I explicitly removed the module "acer_wmi," AND blacklisted it. Good luck, anyone else with the RT3090 or Z575 :)

---

### Post by alx.kuzza on 2012-03-18
Even I'm using Suse Linux this solution worked for me as well. I did only this:

1) rmmod acer_wmi (after that Network Manager immediately discovered all wifi hotspots)
2) blacklisted acer_wmi in /etc/modprobe.d/modprobe.conf (you need to add 1 line at the end as:
blacklist acer_wmi)

Note: a traditional configuration on Suse worked even without blacklisting acer_wmi

Network Manager after removing that module works for Gnome and KDE

KUDOS to gdea73. :p

---

### Post by gdea73 on 2012-03-18
thanks for the input - glad to hear it worked well, especially with less steps.

I figured the guide could be both expanded upon and simplified in various ways, good to know that that worked for you. I think for me I needed to blacklist rt2800pci and those other preinstalled Ralink drivers, but your results may vary so thanks for letting us know. ;)

---

### Post by dtzortzis on 2013-02-06
> **alx.kuzza said:**
> Even I'm using Suse Linux this solution worked for me as well. I did only this:

1) rmmod acer_wmi (after that Network Manager immediately discovered all wifi hotspots)
2) blacklisted acer_wmi in /etc/modprobe.d/modprobe.conf (you need to add 1 line at the end as:
blacklist acer_wmi)

I didn't manage to compile the driver but that's ok. I just did these two steps above and it worked :)
FYI, I'm using Xubuntu 12.10 on my Lenovo Z575.

My problem was not that wireless did not worked. It worked ok but the speed was 10x lower compared to Windows or to when I was using a wired connection.

---

### Post by dtzortzis on 2013-11-27
This fix doesn't work after updating to the latest kernel 3.2.0-52.
Any ideas?

```

$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


```

---

