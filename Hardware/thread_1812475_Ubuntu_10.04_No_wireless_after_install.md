---
title: "Ubuntu 10.04 No wireless after install"
date: 2011-07-26
forum: Hardware
---

### Post by octopiocyopi on 2011-07-26
I've had so many issues with 11.04 Natty that could not be solved so I just fresh installed Ubuntu 10.04 from a USB as my netbook does not have a CD drive. Well, after installing and restarting I have no wireless. I ran iwconfig and I got pan0      no wireless extensions. How do I fix this?

---

### Post by octopiocyopi on 2011-07-26
I also have no access to a wired connection for my Netbook, so how can I fix this without a wired connection?

---

### Post by TBABill on 2011-07-26
We need specs on the device you are trying to enable before we can help. Have you run ```
lspci
``` in a terminal to know what the wireless device is? Paste the output here as a first step.
 
Also, have you been offered any drivers by "additional drivers"?

---

### Post by IWantFroyo on 2011-07-26
> **TBABill said:**
> We need specs on the device you are trying to enable before we can help. Have you run ```
lspci
``` in a terminal to know what the wireless device is? Paste the output here as a first step.
 
Also, have you been offered any drivers by "additional drivers"?

He hit the nail on the head. I just want to add that there are firmware installers in Synaptic, so do a few searches there after you figure out what card you have.

You can do these from another computer, and then put the drivers on a usb and install from that.

---

### Post by octopiocyopi on 2011-07-26
> **TBABill said:**
> We need specs on the device you are trying to enable before we can help. Have you run ```
lspci
``` in a terminal to know what the wireless device is? Paste the output here as a first step.
 
Also, have you been offered any drivers by "additional drivers"?
  I have run update manager and says no updates..offered no additional drivers

ken@ken-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by octopiocyopi on 2011-07-26
> **IWantFroyo said:**
> He hit the nail on the head. I just want to add that there are firmware installers in Synaptic, so do a few searches there after you figure out what card you have.

You can do these from another computer, and then put the drivers on a usb and install from that.

Synaptic was no help to me. It had nothing.

---

### Post by octopiocyopi on 2011-07-26
> **thrallgg said:**
> i have same problem :(

I may just have to re-install Natty 11.04 if this cannot get solved which I do not want to do as Natty had wireless out of the box, but caused my computer to constantly crash due to graphics card.

---

### Post by otto67at on 2011-07-26
I don't think, that a reinstall would help, when lspci doesn't find any wireless network card. I think, you have to download drivers from the vendor-page.
But I even think, that won't help, too. When lspci don't find the card, i am shure, you don't get it to work with drivers. Most Notebooks have a switch, where you can turn off wireless devices, i belive, this is switched off.

---

### Post by octopiocyopi on 2011-07-26
> **otto67at said:**
> I don't think, that a reinstall would help, when lspci doesn't find any wireless network card. I think, you have to download drivers from the vendor-page.
But I even think, that won't help, too. When lspci don't find the card, i am shure, you don't get it to work with drivers. Most Notebooks have a switch, where you can turn off wireless devices, i belive, this is switched off.

I tried installing the drivers, no worky. My netbook does not have a switch. The wireless is just lights.

---

### Post by octopiocyopi on 2011-07-26
Wireless works straight out of the box for every Ubuntu 11.04 fresh install every time so it is just 10.04 that has issues.

---

### Post by otto67at on 2011-07-26
Not, when the card isn't visible on the pci-bus :)

---

### Post by octopiocyopi on 2011-07-26
> **otto67at said:**
> Not, when the card isn't visible on the pci-bus :)

 it is ALWAYS recognized when I have 11.04 installed. I just went back to 11.04. Re-installed 11.04 natty and wireless showed instantly. I really wish I could've gotten 10.04 wireless to work as Natty has graphics issues that are unfixable. See post here: [http://ubuntuforums.org/showthread.php?t=1811832](http://ubuntuforums.org/showthread.php?t=1811832)

---

### Post by otto67at on 2011-07-26
And what about 10.10 Maverick? I am very happy with it and it will be supported until April 2012, i think, thats ok. Maybe, until then, the natty will work satisfying :)

---

### Post by TBABill on 2011-07-26
```
sudo add-apt-repository ppa:lexical/hwe-wireless
```
then ```
sudo apt-get update
```
then ```
sudo apt-get install rtl8192ce-dkms

``` Then restart the machine and see if it works. Pretty sure your chipset requires the 8192 driver.

---

### Post by octopiocyopi on 2011-07-26
> **TBABill said:**
> ```
sudo add-apt-repository ppa:lexical/hwe-wireless
```then ```
sudo apt-get update
```then ```
sudo apt-get install rtl8192ce-dkms

``` Then restart the machine and see if it works. Pretty sure your chipset requires the 8192 driver.

That no worked

---

### Post by mkeyes001 on 2011-07-26
I had that issue with 11.04 on my dell, not sure your hardware but I installed the b43-fwcutter driver and that fixed my issue.

edit:  just seen it was a netbook..

why not run natty in classic mode...

---

### Post by octopiocyopi on 2011-07-26
> **mkeyes001 said:**
> I had that issue with 11.04 on my dell, not sure your hardware but I installed the b43-fwcutter driver and that fixed my issue.

edit:  just seen it was a netbook..

why not run natty in classic mode...

I do run it in Natty classic mode no effects and same issue.

---

