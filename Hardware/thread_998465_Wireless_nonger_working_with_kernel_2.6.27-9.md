---
title: "Wireless nonger working with kernel 2.6.27-9"
date: 2008-11-30
forum: Hardware
---

### Post by scottjohnanderson on 2008-11-30
Has anyone else found that the wireless networking is no longer working  after they have updated to kernel 2.6.27-9? I have a Toshiba satellite laptop with a Atheros AR5007EG wireless card. I am using Madwifi as my driver. The networking works when I boot up with 2.6.27-7.

---

### Post by Mizzou_Engineer on 2008-12-01
You probably need to rebuild the madwifi kernel modules since you updated the kernel and your original drivers do no work with the new kernel. Probably the easiest way is to install module-assistant and then use it to build the madwifi. How to do that:

1. Install module-assistant: sudo apt-get install module-assistant
2. Run module-assistant: sudo m-a (it brings up a menu)
3. Update the cached package information (second menu item)
4. Prepare the system to compile modules (third menu item)
5. Select modules (fourth menu item)
6. Scroll down until you see madwifi. Press space bar to change [ ]madwifi to [*]madwifi to select it. Another menu will pop up.
7. Get the source package (third menu item)
8. Build the driver (fourth menu item.) Say yes when it asks you if you want to install the module.
9. Hit Esc several times until you leave module-assistant.
10. Now load the madwifi drivers: sudo modprobe madwifi

Your wireless card should work now. If it does not, then reboot your computer and then it will work.

---

### Post by Beetlebum_007 on 2008-12-01
Will this method work with my Acer Aspire 5315 too? I'm unable to get my wireless connection to work and am open to any reasonable suggestions. Thanx
Beetlebum

---

### Post by Beetlebum_007 on 2008-12-01
tried the above but my terminal says 'couldn't find package module - assistant' ........ what do I do now???
HELP PLEASE.......
Beetlebum

---

### Post by Mizzou_Engineer on 2008-12-01
> **Beetlebum_007 said:**
> tried the above but my terminal says 'couldn't find package module - assistant' ........ what do I do now???
HELP PLEASE.......
Beetlebum

It is in the universe repository, which is not enabled by default. You will need to enable this and there are three ways to do it:

1. Go to System -> Software Sources. Check the second box which says "Community-maintained Open Source software (universe)" and refresh the package list in Synaptic.

2. Open up Synaptic and go to Settings -> Repositories. Check the second box which says "Community-maintained Open Source software (universe)" and then refresh the package list in Synaptic.

3. Open up a terminal and use your favorite text editor as sudo to open /etc/apt/sources.list. Remove the pound sign from in front of the four lines with "universe" at the end. Run apt-get update as root.

Now you should be able to install module-assistant.

---

### Post by Mizzou_Engineer on 2008-12-01
> **Beetlebum_007 said:**
> Will this method work with my Acer Aspire 5315 too? I'm unable to get my wireless connection to work and am open to any reasonable suggestions. Thanx
Beetlebum

Run "sudo lspci" and post the output and we should be able to tell you.

If you see Network controller: Broadcom Corporation BCM43xx" (where xx is a pair of numbers, such as 12) then chances are the new wl driver should work. It works with my BCM4312 on anything but MSCHAPv2 PEAP networks.

---

### Post by Beetlebum_007 on 2008-12-02
Thanx so much for your suggestions! I am very grateful to you for your efforts in assisting me.
However, still having problems installing module assistant. I tried to do this using sudo /etc/apt/sources.list and got the line......

sudo: /etc/apt/sources.list: command not found

I am in the process of downloading 4 DVD images from Debian by BitTorrent which I am hoping will have all the missing apps and programs I need. Is this what I need??

---

### Post by Beetlebum_007 on 2008-12-02
After running sudo lspci I got this.........
 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.1labg Wireless PCI Express Adapter (rev 01)
 
I sincerely hope this will help you to help me!
Thanx again,
Beetlebum

---

### Post by Beetlebum_007 on 2008-12-02
After running sudo lspci I got this.........

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics controller (rev 03)
00:02.1 Display controller:  Intel Corporation Mobile GM965/GL960 Integrated Graphics controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0  Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.1labg Wireless PCI Express Adapter (rev 01)

I sincerely hopr this will help you to help me!
Thanx again,
Beetlebum

---

### Post by emada on 2008-12-02
> **Mizzou_Engineer said:**
> You probably need to rebuild the madwifi kernel modules since you updated the kernel and your original drivers do no work with the new kernel. Probably the easiest way is to install module-assistant and then use it to build the madwifi. How to do that:

1. Install module-assistant: sudo apt-get install module-assistant
2. Run module-assistant: sudo m-a (it brings up a menu)
3. Update the cached package information (second menu item)
4. Prepare the system to compile modules (third menu item)
5. Select modules (fourth menu item)
6. Scroll down until you see madwifi. Press space bar to change [ ]madwifi to [*]madwifi to select it. Another menu will pop up.
7. Get the source package (third menu item)
8. Build the driver (fourth menu item.) Say yes when it asks you if you want to install the module.
9. Hit Esc several times until you leave module-assistant.
10. Now load the madwifi drivers: sudo modprobe madwifi

Your wireless card should work now. If it does not, then reboot your computer and then it will work.

when i get to step 7 i get this error:
Installation of the madwifi-source source failed.
Ignoring this package. Maybe you need to add something to
sources.list, maybe the contrib and non-free archives.

any ideas??

---

### Post by asgard_command on 2008-12-02
I have the same issue with the same wireless card after the new kernel update.
At the moment I have gone back to using the older kernel.
Will post if I find a solution.

---

### Post by Mizzou_Engineer on 2008-12-02
> **Beetlebum_007 said:**
> Thanx so much for your suggestions! I am very grateful to you for your efforts in assisting me.
However, still having problems installing module assistant. I tried to do this using sudo /etc/apt/sources.list and got the line......

sudo: /etc/apt/sources.list: command not found



My fault, I said that you needed to run a text editor as sudo and open up /etc/apt/sources.list but didn't give the name of a text editor. Using GNU Nano works and it is one of the easier-to-use CLI text editors (I'm not going to spring vi on you...)

sudo nano /etc/apt/sources.list

This will work for you as you have an Atheros WLAN card:

```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.1labg Wireless PCI Express Adapter (rev 01)
```

---

### Post by Mizzou_Engineer on 2008-12-02
> **emada said:**
> when i get to step 7 i get this error:
Installation of the madwifi-source source failed.
Ignoring this package. Maybe you need to add something to
sources.list, maybe the contrib and non-free archives.

any ideas??

The error message is telling you what you should do; I'll tell you how to do that. The error message is telling you to add the contrib and non-free repositories, which means you need to enable the Ubuntu universe repository (contrib and non-free are the Debian equivalent of Ubuntu's universe repository, and module-assistant is a Debian-developed program.) You can do that by going to System -> Software Sources and then checking the box for the community-supported/universe repository. Then go back to your terminal and refresh the package information by typing in "sudo apt-get update." 

At this point, re-running module-assistant should work. I would do it myself first, except I really don't want to install the madwifi driver on my machine, which uses an Intel WLAN card.

---

### Post by BKonkle on 2008-12-02
I've actually been having this same issue since 2.6.27-8 with an HP Pavilion dv6810us - bug filed [here]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/298399").  It looks like the ath_pci module (from madwifi) that our AR242x adapters depend on hasn't been included in the latest kernel builds.  I'm going to try checking out the madwifi source from svn to see if that works.  In the meantime, I'm also using the -7 kernel.

---

### Post by BKonkle on 2008-12-02
Alright, I found the answer.  The old ath_pci module from MadWifi is deprecated because it depends on a proprietary component.  It's been replaced by the fully open-source ath5k module, but it's not in the standard, multiverse, or universe repositories - it's in the backports.

So, to correct the issue, while you're on the 2.6.27-7 kernel go to System --> Administration --> Software Sources --> Updates, and enable Unsupported Updates (intrepid-backports).  Once the backports are enabled, reload your software sources and install the linux-backports-modules-intrepid package.

```

sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid

```

Now, for me anyway, I simply had to restart under the -10 kernel and wireless automatically connected, using the ath5k module.  Hooray!

---

### Post by asgard_command on 2008-12-03
> **BKonkle said:**
> Alright, I found the answer.  The old ath_pci module from MadWifi is deprecated because it depends on a proprietary component.  It's been replaced by the fully open-source ath5k module, but it's not in the standard, multiverse, or universe repositories - it's in the backports.

So, to correct the issue, while you're on the 2.6.27-7 kernel go to System --> Administration --> Software Sources --> Updates, and enable Unsupported Updates (intrepid-backports).  Once the backports are enabled, reload your software sources and install the linux-backports-modules-intrepid package.

```

sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid

```


Now, for me anyway, I simply had to restart under the -10 kernel and wireless automatically connected, using the ath5k module.  Hooray!

Great work, this sorted it for me thanks very much.

---

### Post by Beetlebum_007 on 2008-12-04
> **Mizzou_Engineer said:**
> My fault, I said that you needed to run a text editor as sudo and open up /etc/apt/sources.list but didn't give the name of a text editor. Using GNU Nano works and it is one of the easier-to-use CLI text editors (I'm not going to spring vi on you...)

sudo nano /etc/apt/sources.list

This will work for you as you have an Atheros WLAN card:

```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.1labg Wireless PCI Express Adapter (rev 01)
```

Hi after much ado I finally managed to get my internet connection working with the cable attached but still no wireless.
I tried your suggestion above but have come accross another problem with the module assistant. When I run sudo nano /etc/apt/sources.list this opens up the text editor and I followed your instructions regarding the #signs. So far so good. When I go to Terminal and run sudo apt-get install module-assistant the program starts then as it progresses it asks me to insert Hardy Heron release i386 (20080702.1) CD. Where do I find a download which will give me this? Or am I having a Homer moment in that it is already on the CD I used to install Ubuntu I downloaded?
Yours in Frustration,
Beetlebum

---

### Post by Mizzou_Engineer on 2008-12-04
> **Beetlebum_007 said:**
> Hi after much ado I finally managed to get my internet connection working with the cable attached but still no wireless.
I tried your suggestion above but have come accross another problem with the module assistant. When I run sudo nano /etc/apt/sources.list this opens up the text editor and I followed your instructions regarding the #signs. So far so good. When I go to Terminal and run sudo apt-get install module-assistant the program starts then as it progresses it asks me to insert Hardy Heron release i386 (20080702.1) CD. Where do I find a download which will give me this? Or am I having a Homer moment in that it is already on the CD I used to install Ubuntu I downloaded?
Yours in Frustration,
Beetlebum

It is asking you for your Ubuntu 8.04 install CD. Did you upgrade from 8.04 to 8.10 by chance?

---

### Post by Beetlebum_007 on 2008-12-04
Mizzou_Engineer, thanks for your support. I have now managed to get as far as the build process of the suggested actions on page 1 from yourself. I am now being told madwifi could not be found. It does suggest other installs which I have completed but to no avail. As a result I am still stuck in the loop of no madwifi. As for upgrading to 8.10 - well - erm............ to be honest I tried to install it yesterday morning from boot up on a DVD RW but as far as I know it didn't upgrade however, I am open to the possibility it did. Any further suggestions would be most welcome.
Beetlebum

---

### Post by Mizzou_Engineer on 2008-12-04
Well, it looks like you have 8.04 installed since the CD-ROM line in your sources.list called for 8.04's CD. You could always check to see if you did in fact upgrade by looking at System -> About Ubuntu and seeing if it says 8.04 or 8.10. 

I looked at the Ubuntu package search tool and found that madwifi-tools and linux-restricted modules are the only packages with "madwifi" in the name or description. The madwifi-tools is in the universe repository for both 8.04 and 8.10 and the linux-restricted-modules packages are in the restricted repository. If you followed the instructions, then your system has access to both packages, so I don't know what you could do other than compile the madwifi stuff yourself from source. [Here]("http://madwifi-project.org/") is the MadWifi page, which has the sources and installation instructions.

---

### Post by asgard_command on 2008-12-04
Have you tried the tip given by BKonkle above worked great for me.
I don't know if it the same situation as you are on Hardy and I am on Intrepid but if madwifi is removed from the new intrepid kernel it may well be from the hardy kernel too.
Try following his directions for enabling backports and installing linux-backport-modules just replace intrepid with hardy for each step.

---

### Post by asgard_command on 2008-12-04
An extra thought if you are still having trouble with it prompting you for a cd go to System/Administration/Software Sources and at the bottom make sure the installable from cd box isn't checked. I think if this is checked it will try and look for software on your install cd before it goes to the online repositories. But I am not 100% on this if someone else wants to clarify.

---

