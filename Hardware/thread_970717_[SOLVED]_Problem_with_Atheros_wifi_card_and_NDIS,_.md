---
title: "[SOLVED] Problem with Atheros wifi card and NDIS, and some other issues with 8.10"
date: 2008-11-04
forum: Hardware
---

### Post by ravl on 2008-11-04
Hello,

I´m testing Kubuntu Intrepid on my laptop, I made a dual boot with Hardy just in case Intrepid fails.

I got the Nvidia card working properly. :D

Since I use the amd64 distro, I don´t have a madwifi driver for my Atheros wireless card. On Hardy, I followed the tutorial to use NDIS and the card works wonderfully. On Intrepid, the exact same procedure gives me a wlan0 interface and I can scan for available networks. But NetworkManager fails to connect, and when I use wpa_cli to connect, I get a series of messages, saying that it did connect to the wireless router, and then gets disconnected immediately. This repeats a few times until it just remains disconnected.

Also, I installed my favorite X11 cursor set because I really don't like the default Oxygen. But only a few of the cursors were replaced, others remain as the default. This really annoyed me.

This might not be a bug, but I just can't find a way to make the panel vertical on the right edge of the screen. I'm very used to this configuration and I'd like to set it up in KDE 4.1.2.

Thanks for the help!

---

### Post by ravl on 2008-11-05
I've been using Kubuntu 8.10-RC so far, with no luck on activating the wireless card.

On Hardy, I just use ndiswrapper, I don't blacklist any module. And NetworkManager easily connects.

I tried a suggestion in a blog, saying to simply disable the stock driver in the Hardware Drivers Manager and install linux-backports-modules-intrepid-generic. This didn't work for me, since jockey-kde crashed every time I tried disabling the driver.

I will try tonight with the final release of Kubuntu 8.10 to see if that makes a difference.

---

### Post by vincirufus on 2008-11-05
Hi I too have similar problems with my Atheros Wifi.
I installed the latest version of Kubuntu 8.10..
It manages to detect my wifi Router, the signal strength and all but doesn't connect, I've enabled WPA (Personal)on my router.
Another strange thing is if I go to Internet > Network Manager, it doesn't open up anything, does that happen with you too. 

I'm also still struggling with my Nvedia card.. it shows 2 options of the Drivers 7.13 and 7.15 but when I select either it tries to connect to the repositories I guess and since my wifi isnt working that doesn't download.. How did you manage to get your Nvedia to work.

Looks like we have similar laptops mine is a Compaq CQ60 101AU, AMD X2 Athlon, Nvedia, Atheros etc.

Vinci

---

### Post by ravl on 2008-11-05
To enable my Nvidia card:
```
sudo aptitude install envyng-core
sudo envyng -t
```

I followed the prompts, it gives you a choice between the driver version 177 (newest) and version 173 (previous). I chose version 173, since that worked perfectly in Kubuntu 8.04, and my video card works great. Envyng will download and install the drivers and dependencies. You do need a connection to the internet to do this, you can plug a network cable to the wireless router, they usually have ports.

About the Atheros wifi card, I've been wandering around the forums and found what seems to be a simple solution. I haven't tried yet, I will when I get home and I install the final release of Intrepid.

In Hardware Drivers Manager, disable the stock Atheros support, reboot.

Then:
```
sudo aptitude install linux-backports-modules-intrepid-generic
```

This should give you the ath5k kernel module, that someday will replace madwifi. People report that the card works after installing this and rebooting. I hope they're right :D

---

### Post by ravl on 2008-11-06
Success!!!

I can confirm that the process I previously posted to enable Atheros wifi cards works!

System > Hardware Drivers: Disable the stock Atheros support. Something odd happened here, when I open the Hardware Driver manager from the K menu, it doesn't ask for the administrator password. I closed it, and then clicked on the tray icon for the Hardware Driver Manager, and then got prompted for the administrator password. Then I could disable the stock driver.

Reboot.

```
sudo aptitude install linux-backport-modules-intrepid-generic
```

Reboot.

Right click NetworkManager, your wireless should be up and running.

Now I will start testing KDE 4.1.2, to see if it will fill my needs:
- Run my favorite MUD client.
- Kontact working properly.
- KMyMoney working properly.
- Looks.

I still have some doubts about looks. I haven't tested thoroughly, but so far I've noticed that system tray icons are ugly, as if they don´t get redrawn once they shift along the tray during boot.

Once convinced all this works, I will delete this test partition and upgrade my trusted 8.04.1.

---

### Post by vincirufus on 2008-11-06
Hi,
Great Congrats,
Well I didnt have much luck at my end, my device manager window never opened up.. and I gave up.
I tried installing the latest Ubuntu 8.10 and it installed like a charm.. Wifi connected immediately. and the Nvidia drivers installed when I installed the updates..
Well so looks like I'm gonna stick on with Ubuntu for now

Vinci

---

### Post by Strider2008 on 2008-11-16
I just installed Ubuntu 8.10 in my HP dv6910us laptop which has this particular Atheros wifi card-
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

I followed the procedure of installing linux-restricted-modules-2.6.24-19-generic and disabling the Atheros 5xxx support in Hardware Drivers. Though now there is "Enable wireless" option being shown ,it is still not detecting any wireless network.
Any help?

Thanks.

---

### Post by fermin on 2008-11-16
Hi. Since there was no official support for this Atheros ar242x 802.11abg wireless pci express adapter in ubuntu 8.04 and madwifi didnt work with it either, i successfully followed the instructions by faktorum in [this post]("http://ubuntuforums.org/showthread.php?t=887531&highlight=atheros+ar242x+802.11abg+wireless+pci+express+adapter&page=4") (#36). It worked perfectly with Hardy but since the upgrade to Intrepid it stopped working. Now when i try to figure what happened i reckon the old madwifi modules are still working and the new ath5k modules are also working and they cause conflict. Could this be true? How can i deactivate the old modules son only the new ath5k modules work? (Meanwhile i have no wifi in that lap). :confused:

---

### Post by ravl on 2008-11-16
> **Strider2008 said:**
> I followed the procedure of installing linux-restricted-modules-2.6.24-19-generic and disabling the Atheros 5xxx support in Hardware Drivers. Though now there is "Enable wireless" option being shown ,it is still not detecting any wireless network.
Any help?

Thanks.

if the NetworkManager option says "Enable Wireless", it means it's disabled. It might be the hardware switch for the laptop been off, or simply the driver keeping the wifi card off (which is the default, I think).
Here's what I did on a friend's laptop:

1. Click on "Enable wireless", it should turn to "Disable wireless" and you should be able to scan and connect to networks. If that doesn't work, go to the next step.

2. Try pressing the wifi button/switch on your laptop, then on a console:
```
dmesg | tail
```

There should be a message there telling you if the card was turned on or off by you pressing the button/switch. Repeat until you're sure the card is on by hardware, then repeat step 1.

:)

---

### Post by ravl on 2008-11-16
> **fermin said:**
> Could this be true? How can i deactivate the old modules son only the new ath5k modules work? (Meanwhile i have no wifi in that lap). :confused:

I know for a fact that the ath5k module in the backport modules for intrepid works, if you follow the instructions previously posted on this thread.

Your wireless broke because the instructions that you followed, though they are correct, they are specific to the kernel you use. When you upgraded to Intrepid, you got a new kernel.
I'm pretty sure if you do that procedure again, compiling that patched module for your current kernel, it should work.

On the other hand, you can try the ath5k solution. For both, do this

```
sudo rmmod wlan_scan_sta
sudo rmmod ath_pci
sudo modprobe -r wlan_scan_sta
sudo modprobe -r ath_pci
```

The previous commands will remove all the modules you compiled, and now 
```
sudo nano /etc/modules
```

Delete the line that says ath_pci, it's probably the last one.

Now you are back to where you started and can recompile the modules just like you did before, or follow my instructions posted on this thread.

---

### Post by ravl on 2008-11-16
> **vincirufus said:**
> 
Well I didnt have much luck at my end, my device manager window never opened up.. and I gave up.

Vinci

It's more of a KDE issue. I had problems with the Hardware Drivers window, if you open it from the K menu, it opened as regular user, and never prompted for sudo password. I closed it, then clicked on the system tray icon, then I got the prompt for sudo password, and I could disable the drivers

---

### Post by fermin on 2008-11-17
Thanks Ravl for your help. I followed your instructions and it nearly worked for me. I just had to do one additional step for it to work properly.

You stated i should input the commands:
```
sudo rmmod wlan_scan_sta
sudo rmmod ath_pci
sudo modprobe -r wlan_scan_sta
sudo modprobe -r ath_pci
```Nevertheless the output said that wlan_scan_sta module did not exist. Instead i input
```
sudo rmmod wlan
sudo modprobe -r wlan
```Moreover removing these modules wasnt enough, since at the upgrade to 8.10 Intrepid my settings file

/etc/default/linux-restricted-modules-common

was reset to the default, and as i followed in [the original post i followed to get wifi working under 8.04 Hardy]("http://ubuntuforums.org/showthread.php?t=887531&highlight=atheros+ar242x+802.11abg+wireless+pci+express+adapter&page=4"), i had to edit this file to ban the "ath_hal" module from ever loading again at startup; so i did it again with:
```
sudo gedit /etc/default/linux-restricted-modules-common
```and added the "ath_hal" in the disabled modules to leave the file like this:
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="ath_hal"
```

(You can review those steps in the previously mentioned [original post i followed for Hardy]("http://ubuntuforums.org/showthread.php?t=887531&highlight=atheros+ar242x+802.11abg+wireless+pci+express+adapter&page=4").) Since i had previously followed your instructions for setting up ath5k modules from the repositories i already had those drivers enabled and from there i just rebooted and voila! I have wifi again! :) I spect no more problems in the future with your solution since it is repository based and will automatically update even when the next version of ubuntu comes. Thanks a lot and i hope my upgrading experience also helps somebody else.

---

