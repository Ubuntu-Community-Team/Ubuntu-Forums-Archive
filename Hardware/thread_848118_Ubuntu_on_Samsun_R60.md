---
title: "Ubuntu on Samsun R60"
date: 2008-07-03
forum: Hardware
---

### Post by Bavarian on 2008-07-03
Hi.I know there is thread for R60 but i'm searching for way without internet connection.How i can install that driver in command line without internet connection if the driver is on USB flash or CD?
[http://ati.amd.com/support/drivers/l...ux-radeon.html](http://ati.amd.com/support/drivers/l...ux-radeon.html) that is the driver.Or if there is now way to install it how i can configure my wireless on command line?Because i can't start Gnome on a Samsung R60 notebook.Or my last chance.How i can load VGA driver on command line to get basic graphics to configure wireless and then download drivers.Please help if someone know i want to share Ubuntu with one my friend.

---

### Post by beN..87 on 2008-07-03
> **Bavarian said:**
> Hi.I know there is thread for R60 but i'm searching for way without internet connection.How i can install that driver in command line without internet connection if the driver is on USB flash or CD?
[http://ati.amd.com/support/drivers/l...ux-radeon.html](http://ati.amd.com/support/drivers/l...ux-radeon.html) that is the driver.Or if there is now way to install it how i can configure my wireless on command line?Because i can't start Gnome on a Samsung R60 notebook.Or my last chance.How i can load VGA driver on command line to get basic graphics to configure wireless and then download drivers.Please help if someone know i want to share Ubuntu with one my friend.


follow the thread - download the files with the connection you're using now , put them on usb , burn your CD ; print the instructions .... no more internet connection needed

---

### Post by Bavarian on 2008-07-03
Ok but i'm at work and i'm with Windows now.Where i can download files without apt-get?Thread says this 
> 1. Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
2. Start text mode installer and install Ubuntu/Kubuntu.
3. Finish Install and reboot.
4. Update package list and upgrade any packages needed.
Code:

sudo apt-get update
sudo apt-get dist-upgrade

5. Install fglrx closed source driver for ATI video cards.
Code:

sudo apt-get install xorg-driver-fglrx

6. Update loaded modules.
Code:

sudo depmod -a

7. Configure /etc/X11/xorg.conf
Code:

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

8. Reboot 

First i must install it without alternate CD from command line.I will download fglrx drivers with Windows but i don't know how.If the drivers are in USB flash or CD what is the commands for install them directly from CD or flash?

---

### Post by beN..87 on 2008-07-03
easy as ABC - heres my howto

[http://ubuntuforums.org/showthread.php?t=839000](http://ubuntuforums.org/showthread.php?t=839000)


just download the files you need stick them on a usb, burn an ALTERNATE install CD - print the guide - you're good to go... ps follow it carefully and use a clean and healthy drive for the ati driver - its a very sensitive graphics driver and needs to be perfect

---

### Post by Bavarian on 2008-07-03
Ok thanks for the guide but is there any way to install without installing Alternate CD,because i was installed Ubuntu with Wubi and don't want to partitioning.Can i just install the drivers from USB flash when Ubuntu boots without graphic
ubuntu@ubuntu:

---

### Post by beN..87 on 2008-07-03
yeah just get your drivers downloaded and skip the first few steps start where the guide says


your computer will now boot into your installed ubuntu system - without your graphics installed , you will be met by some code and a screen that will flash for 10 seconds or so, when its stopped flashing

press Alt and F2

login prompt: enter your username and password as instructed

enter the following code:

---

### Post by Bavarian on 2008-07-04
Everything is perfect but the white screen.I think to try again to fix the white screen but i haven't enought time.When he buy new notebook.Is there someone who installed new Ubuntu 8.04.1 on Samsung R60 because at the moment i haven't CD's to try.And my internet is slow to download it (30kb/sec) :(

---

### Post by beN..87 on 2008-07-05
yes, the guide i linked to is for installation of 8.04 HH Alternate CD on a new Samsung R60 notebook - to avoid whitescreen follow the guide exactly

---

### Post by haylun98 on 2008-08-25
I'm quite new to Ubuntu. I've followed the guide (with little modifications/shortcuts) to install/reinstall Ubuntu on my R60plus many time. I've encounter the white screen nearly every time. I think the ati installer failed to enable the driver. To enable it yourself first login Gnome in safe mode. Then goto System -> Admin -> Hardware driver. Check enable ATI driver and reboot. It worked the 8.4 and 8.5 but might not work with 8.8 version of ati driver

---

