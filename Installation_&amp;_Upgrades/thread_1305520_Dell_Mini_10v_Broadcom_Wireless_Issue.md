---
title: "Dell Mini 10v Broadcom Wireless Issue"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by nemarasu on 2009-10-29
Hey All,

This is for Ubuntu 9.10

I cannot get the proprietary driver for the (Broadcom) BCM4322 to activate via the Hardware Drivers GUI. It shows the driver, I click Activate, it prompts for my password, then never activates it. 

During the LIVE Desktop environment it will Activate the driver and I can see the wireless networks in the area. But once I boot from the netbook, the driver is not loaded and it will not activate. I show the kernel packages bcmwl-kernel-source and bcmwl-modaliases as installed.

Any help is appreciated.

Thanks!

---

### Post by dvlchd3 on 2009-10-30
Try:

```

sudo apt-get install b43-fwcutter

```

Select 'yes' if it prompts you to download and extract firmware.

---

### Post by GeraldoJon on 2009-10-30
> **dvlchd3 said:**
> Try:

```

sudo apt-get install b43-fwcutter

```Select 'yes' if it prompts you to download and extract firmware.

Thanks dvlchd!

The code helped a bunch. I am on a Mini 9 trying to run UNRemix 9.10. I've been having problems all day trying to fix the wireless.

I've tried the downloading of the packages with Synaptic through a wired connection. All the tips on the forum didn't work. Using your code, I was able to restart and see "Wireless Network Available".

However, it still doesn't work. Could you get any tips?

Thanks!
   Zhe

---

### Post by nemarasu on 2009-10-30
It was installed already:

$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I just re-installed, but I am still having the same issue. 9.04 worked out of the box in the live enviro and after first boot.

:(

---

### Post by nemarasu on 2009-10-30
$ lspci -vnn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

---

### Post by NormanFLinux on 2009-10-30
No problems here in 9.10 running a Broadcom card on a Dell Inspiron e1505. The settings carried over smoothly from Jaunty to Karmic.

---

### Post by nemarasu on 2009-10-30
Here is the fix that worked for me:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185)

Re-install: bcmwl-kernel-source and bcmwl-modaliases via Synaptic Package Manager

Once that was done I rebooted and wireless was working.

Thanks for the assistance. :KS

---

### Post by dvlchd3 on 2009-10-30
Try installing the firmware again:

```

/usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

```

---

### Post by usererror on 2009-10-30
I'm running an HP 6735b, and this post worked for me.  I think my initial install of the hardware drivers for Broadcom STA driver broke. So I tried the cutter one, and that did not work.  I re-did the STA driver and now it seems to be working.

I had major issues with this wifi card in Windows, I'm hoping it works better under linux, or I think I can rule it a hardware problem...

---

### Post by surfincrow on 2009-10-31
Also try to remove your stored network from your preferences in System->Preferences->Network Connections.
Now try to connect again (and providing the password again). That was the trick for me, after applying the tricks above.

---

### Post by moonwreath on 2009-11-05
I have a Dell mini 9, and I could not activate the Broadcom STA driver. The Hardware Drivers program prompted me for admin password, but nothing happened after I typed it in.

I found several forum posts saying that the package bcmwl-kernel-source had to be reinstalled. This did not work for me. However, after uninstalling the package ("sudo aptitude remove bcmwl-kernel-source" in the terminal), I finaly managed to activate the Broadcom STA driver in the Hardware Drivers program. :D

---

### Post by CJay554 on 2009-12-11
Heres my experience:

Dell 10v Broadcom STA proprietary Driver.

When installing Ubuntu 9.10 through USB live boot:
  -Everything works except wireless
     1. when going to Hardware Drivers it stated that i didn't have the Broadcom STA
        driver activated so i pressed the "activate" button and put in my password.. 
        ...Nothing happened. Tried reinstalling b43-fwcutter, bcmlw-* but, 
        re-installed successfully but nothing worked on reboot...

Installed Ubuntu 9.04 (everything worked including wireless)
    -Did a Distro update to 9.10 (took about 2-3 hours) 
          1.Wireless stopped working... BUT!
          2. Wireless showed as "Installed but not activated" in Hardware Drivers.
          3. I proceded to do the reinstallation of fwcutter and bcmlw drivers 
          4. Reboot, and it worked flawlessly! 

So far i seem to have gotten it to work and havent had problem with a couple of test reboots to see if the wireless stays connected or not.

My pet peeve... Why go through all of this?! 
If the drivers work in a past distro (8.04 and 9.04) why does an upgrade ruin the drivers? Why not leave them be as its obvious that the older drivers are activated and fully functional while the newly installed drivers are not activated or working!
I smell a driver rollback function to be encorporated to "Hardware Drivers"?

---

### Post by benfindlay on 2010-01-29
I've been looking into this a little bit more. It seems that the issue is tied more to the kernel updating than the version of ubuntu. I've also had the same problems as previously documented when 9.04 is installed,a nd then upgraded to 9.10. I've just done a fresh install of 9.10, got everything working with b43-fwcutter, bcmwl-kernel-sources and bcmwl-modaliases, then updated the kernel, and its all stopped working. Anyone else found this?

---

