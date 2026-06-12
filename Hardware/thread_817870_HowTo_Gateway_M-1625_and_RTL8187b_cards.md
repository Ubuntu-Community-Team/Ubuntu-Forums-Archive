---
title: "HowTo: Gateway M-1625 and RTL8187b cards"
date: 2008-06-04
forum: Hardware
---

### Post by Dark_Stang on 2008-06-04
**UPDATE**
lasegui has reported that the latest release of Ubuntu (8.10) does not need the drivers I have posted. All you have to do is update the kernel and you're golden. Also, wittelw has reported a couple hiccups with 9.04. See his post further down this page for further information.

Okay, so here's a little background story. My buddy got a new laptop last week (gateway M-1625 on a crazy sale) and he wanted to dual boot with it. After finding no real informative how-to guides for this laptop or the wireless card inside it... so, like with my laptop, I decided to write my own. Better yet, I've included a nice little file that will take care of 95% of the work on the wireless card install.

**Ubuntu HowTo on a Gateway M-1625**

Note to veterans: If you're comfortable setting up Linux before and are looking for areas where you're going to run into problems, skip straight to the wireless portion of this guide. The wireless card was the only thing that was a pain in my ***, however I've got it all nearly automated for you. Lucky you... This laptop is mostly easy for an experienced user.

**Sections of this Guide**
1. Pre Install Notes
2. Requirements - Stuff you need for this to work
3. Initial Install
 - Partitioning the hard drive for dual boot
4. Post Install configuration
 - Graphics Card
 - Wireless Card
5. Post Install Notes




**1. Pre Install Notes**
 - If you have not bought this laptop yet and are planning at putting Linux on it, do not purchase it. The wireless card is not linux friendly. My roomate bought this laptop and he wanted to try Linux (currently dual booting). If he had not had an experienced Linux user to set this up for him he would not have been able to get up and running. I could not find any guide for this laptop, so as far as I know this is the first.
 - If you already have this laptop and want to put Linux on it, there is hope. You will need to run WEP encryption or an open network for the wireless card to work, and you will not be able to use network manager. If you don't know what network manager is, it an application Ubuntu uses for managing network connections on the fly.

**2. Requirements**
 - A high speed internet connection
 - An RJ-45 (ethernet) cable to hook up to your high speed connection
 - An Ubuntu Disk (in this guide we will be using 8.04 LTS)
 - An open mind

**3. Initial Install**
 - Pop the Ubuntu disk in, boot up the machine, and wait. Once it's up go up to the top panel and click System > Administration > Partition Editor. This will load gparted. If you're going to use only Ubuntu and don't want vista on the machine at all, go ahead and delete both partitions on the hard drive, and hit apply changes. Then skip the next paragraph. If you want to dual boot, continue onto the next paragraph.
 - My roomate wanted to dual boot with his lIf you're a veteran please feel free to skip through the guide to the wireless card.aptop because he's not comfortable with Linux yet and isn't sure if he's ever going to be (although after owning it for a week he uses Linux almost all the time now). Click the second partition and hit resize. If you're just trying Ubuntu shrink the partition 12 gigs. If you plan on using it a lot shrink it about 60 gigs. If it's going to be your primary OS shrink it 120 gigs. If you want to get rid of vista later you can. After you shrink it hit apply and close out of this.
 - Now that the hard drive has some extra space on it go ahead and go through the install process. This is pretty much straight forward until you get to the partitioning section. Select manual and hit next. If you're dual booting skip to the next paragraph. If you're scrapping windows stick around. Make a new partition that's about 2gb in size. Make the filesystem swap. After that make a partition that's 10-20 gb in size, make the filesystem ext3 (or something else if you would like to use something else), and this will be your root or "/" directory. Now use up the remaining space as ext3 (or whatever) and make it your home directory. Skip the next paragraph.
 - So you're dual booting and you shrank vista's partition down. First make a small partition, about 2gb in size, and make the filesystem swap. Next, make a partition 10-15 gigs in size, make the filesystem ext3, and set the mount point as "/" (aka "root"). Now use the rest of the free space (if you have any), make the filesystem ext3, and make the mount point /home.
 - Okay, now your hard drive is partitioned and ready. Go ahead and finish with the installation process and reboot.

**4. Post Install**
 - First hook up your ethernet cable. Go System > Administration > Software Sources. Check everything in the first tab except for the cd. Hit close. It's going to ask you to reload, go ahead and do that. After this you should see a system update icon pop up. Go ahead and update and reboot.
 - Now for your graphics card. This one is pretty simple. Go System > Administration > Hardware Drivers. Check the box that you see. Ubuntu will setup your graphics card drivers and screen resolution for you and ask you to reboot. That was easy...

 - Now for the wireless card. Download this file... ([linky here]("http://darkstang.com/linux/rtl8187b_install.tar.bz2")) ([or here]("http://gotode.com/rtl8187b_install.tar.bz2")). Now extract the contents somewhere, the desktop or your home folder will be fine. Now open a terminal window and navigate to the folder where you saved and extracted the files. (see next paragraph for newbie instructions, skip next paragraph if you know how to do this)
 - To navigate in terminal use "cd" to change directory (go to another folder) and use "ls" to list the documents/folders in that folder. You will see that "ls" color codes things for you as well. The more you use terminal the more you will learn about linux.
 - Once in the directory read the READ_ME_FIRST file. Edit the wifi_setup file with your network settings. Then run the auto_installer file. It contains all the commands you need with the exception of one. You need to manually add the line "ndiswrapper" to the end of "/etc/modules".
 - Alternatively, if you move between networks you can make files similar to the file at /etc/init.d/wifi_stuff/wifi_setup and place it on the desktop, or anywhere that's convenient for you, and run it any time you like. So if you're at a buddie's house/college/home/whatever you can change it on the fly.

**5. Post Install Notes**
 - Normally I keep these things up to date. However this guide was written for a friend of mine's laptop, and he has since moved a few hours away from me. Because of this I won't be able to test solutions or update them. However, if somebody has some solutions to known problems please post them. I will try to keep this main post up to date with the information from your posts.

---

### Post by TRWulfgar on 2008-07-31
I'm having issues.

The installer removed network-manager, and then bombed, saying it couldn't find the files from the repository, and now I can't get it back.  I tried to change the repository to one near me, hoping it was just timing out.  However, I can't change to a new one, because network-manager is dead, and won't recognize the ping from Synaptic.

I've removed "ndiswrapper" from my etc/modules, and then tried running the removal tool, but I have no network manager.  Now I can't even get online to update the packages.  I'm dead in the water after running your script.

---

### Post by Dark_Stang on 2008-07-31
So re-install the packages from a flash drive or the ubuntu disk. I ran that script several times on my ex-roomates machine and it worked every time. You were hardwired to a network when you ran it, right?

---

### Post by rudyfella on 2008-08-12
Thumbs up for this how-to. I am using Gateway m-1624 and i believe there is not much difference. I have been using my system for a few months now and it is great. However I am unable to adjust the brightness level. Fn+Up and Fn+down keys do not respond. Only Fn+F8 works and that gives me either the maximum or minimum brightness. 

I have tried the gnome panel brightness applet and it didn't work either. Please help me out if you can.

PS: are you able to access WPA protected networks?

---

### Post by Dark_Stang on 2008-08-12
This method doesn't allow you to access wpa protected networks. As far as I know, the rtl8187b wireless card cannot do that under linux at this point.

I'm unsure on the screen brightness and my ex roomates laptop worked "out of the box".

---

### Post by lasegui on 2008-11-16
**[COLOR="DarkRed"]This is NOT an issue anymore.[/COLOR]** It has been solved since Kernel 2.6.26. I have installed [Kubuntu]("http://www.kubuntu.org") 8.10 with kernel 2.6.27 in my Gateway M-1625 and the wireless is working with no problems at all :). Just upgrade kernel and you will have no more troubles with the RTL8187b card.

---

### Post by Dark_Stang on 2008-11-16
> **lasegui said:**
> **[COLOR="DarkRed"]This is NOT an issue anymore.[/COLOR]** It has been solved since Kernel 2.6.26. I have installed [Kubuntu]("http://www.kubuntu.org") 8.10 with kernel 2.6.27 in my Gateway M-1625 and the wireless is working with no problems at all :). Just upgrade kernel and you will have no more troubles with the RTL8187b card.
It's good to hear that wireless works, and it's good to hear that 8.10 works. (It does not work on my HP).

---

### Post by wittelw on 2009-05-02
I had a slightly bumpy upgrade (not reinstall) from intrepid to jaunty WRT rtl8187b and wanted to pass along my experience. Booting from LiveCD wireless worked flawlessly, but after the 8.10->9.04 upgrade Network Manager didn't even show wireless as available. BTW, I had tried verious things to get wireless working on 8.10 (never did succeed) including installing ndiswrapper. Here's what I had to do to get rtl8187b wireless working after the jaunty upgrade:

1) Uninstall ndiswrapper (from Snaptic or your favorite method)
2) Manually remove ndiswrapper out of /etc/modprobe.d. You should be able to just delete it but I was chicken and used sudo mv to move it to my desktop instead.
3) sudo modprobe rtl8187
4) Connect to your wireless access point using Network Manager

Note that I was able to connect after issuing the 'sudo modprobe rtl8187' command however after a reboot wireless was not available in Network Manager again. After moving the ndiswrapper file from /etc/modprobe.d wireless is now enabled (and automatically reconnects) after a reboot.

Depending on what you did during 8.10 your mileage may vary, but hopefully this helps someone else.

---

### Post by zhhansen on 2009-05-23
I had always had problems with my rtl8187b wireless card in hardy, but ever since the ibex and jaunty releases with fresh installs, it works right out of the box with no tweaking. Does anyone else *not* suffer from rtl8187b?

---

### Post by Dark_Stang on 2009-05-24
> **zhhansen said:**
> I had always had problems with my rtl8187b wireless card in hardy, but ever since the ibex and jaunty releases with fresh installs, it works right out of the box with no tweaking. Does anyone else *not* suffer from rtl8187b?
The updated kernels have pretty much made this guide pointless. Nobody should be having issues with it anymore.

---

