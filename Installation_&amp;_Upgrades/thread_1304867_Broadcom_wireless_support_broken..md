---
title: "Broadcom wireless support broken."
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by chrisplymouth on 2009-10-29
I think Ubuntu 9.10 has the worst installer of the last three Ubuntu releases. 

1) While Broadcom wireless drivers work effectively when using the liveCD, the installer neglects to install them rendering notebooks with fresh installs without internet access. The solution is to somehow find a wire connection, fire up synaptic, and install bcm-kernel-source to enable wireless support.

2) Despite suggesting (hd1) as the destination of the GRUB 2 loader, the installer seemed unable to achieve this simple task. It even took the liberty of trashing my trusty GRUB in the MBR of my hard drive.

The desktop is plain and boring as ever. Gnome is becoming increasingly tired-looking and needs a fresh lick of paint. Hopefully Gnome 3.0 will be available in time for the Ubuntu 10.04 LTS. 

The lack of built-in flash support, media codecs and MS true type fonts remaining an issue with Ubuntu releases.

The competition is catching up and Mandriva 2010 are going to great lengths to catch users. I was impressed by RC2 and was pleased to see their attempts to get out-of-box wireless support running.

The key to a successful Linux distribution on a notebook/netbook is out-of-box wireless support and increasingly, 3g/GSM dongle support. I hope developers wake up and realise this before Windows 7 becomes too popular for its own good. 

My customised Linux Mint 7 with downgraded X.org drivers (I have a "legacy" ATI graphics chip) can do a better job!

---

### Post by BramWillemsen on 2009-10-29
omg i was just making a topic about no broadcom wireless xD seems like you answered the problem

[http://ubuntuforums.org/showthread.php?t=1304595](http://ubuntuforums.org/showthread.php?t=1304595)

---

### Post by chrisplymouth on 2009-10-29
[SIZE="3"]Unfortunately, Ubuntu 9.10 has a troublesome installer but it should be no problem for most users. Find an internet connect, load Synaptic (after adding and updating the repositories) and install bcm-kernel-source. After installing the program, reboot your PC and hey presto! [/SIZE]

---

### Post by jheaton5 on 2009-10-29
> **chrisplymouth said:**
> I think Ubuntu 9.10 has the worst installer of the last three Ubuntu releases. 

1) While Broadcom wireless drivers work effectively when using the liveCD, the installer neglects to install them rendering notebooks with fresh installs without internet access. The solution is to somehow find a wire connection, fire up synaptic, and install bcm-kernel-source to enable wireless support.

It appears that you attempted to do a fresh install with your wireless connection.  You must be connected to the internet by ethernet to do a fresh install because the wireless is shutdown when new drivers and firmware are installed.

---

### Post by t-timmy on 2009-10-29
Can you please specify how to install those bcm-kernel-source for those of us who don't know?

I had high expectations but when wireless wasn't working I got a little bummed out :(

---

### Post by t-timmy on 2009-10-29
First I must say it's quite disappointing to install Ubuntu and not have wireless work... oh well...

Alright -- here's to those who don't know how to install these. This worked for me on HP DV4 1220us:

Click System->Administration->Synaptic Package Manager

Click Settings->Repositories

Under "Other Software" tick the two rows you find there

Confirm the window you get, and then click Reload

In the quick search box type bcm and you should find bcm-kernel-source (mine says bcmwl-kernel-source -- maybe it's the wrong one? oh well, fixed my problem)

Right click it and mark for installation

Click apply and install everything

After installation reboot Ubuntu

Enjoy

---

### Post by chrisplymouth on 2009-10-29
Yes sure. You will need internet access to do this.

When you plug the LAN connector into the back of your laptop, Ubuntu will automatically connect to the internet.

Go to System, Administration and select Synaptic Package Manager. It may ask you for a password: enter the password you gave during the installation.

Click Settings->Repositories

Under "Other Software" tick the two rows you find there

Confirm the window you get, and then click Reload

Scroll down the list of packages, until you find "bcmwl-kernel-source". Left click the box and select "mark for installation". 

Synaptic will present a dialogue box explaining that it depends on some other programs. Accept by selecting "mark".

You will see an "Apply" button; click on it! Select "apply" again in the summary box.

Your packages will now be installed.

Once Synaptic has finished its work, restart your computer. 

Any problems, just ask!

---

### Post by chrisplymouth on 2009-10-29
> **jheaton5 said:**
> It appears that you attempted to do a fresh install with your wireless connection.  You must be connected to the internet by ethernet to do a fresh install because the wireless is shutdown when new drivers and firmware are installed.

Ubuntu 8.10 and 9.04 installed the Broadcom drivers without the need for the computer to be attached to an ethernet. I noticed this problem in the RC and hoped it would be fixed. 

Out-of-box wireless support is crucual in any modern operating system.

---

### Post by wisam on 2009-10-29
I installed bcmwl-kernel-source and rebooted; It still doesn't work.

From what I understand, these are the source files for the driver. They still have to be compiled to get the driver module (wl.ko). Right?

Still trying to figure it out.

---

### Post by chrisplymouth on 2009-10-29
> **wisam said:**
> I installed bcmwl-kernel-source and rebooted; It still doesn't work.

From what I understand, these are the source files for the driver. They still have to be compiled to get the driver module (wl.ko). Right?

Still trying to figure it out.

It automatically compiles in Synaptic. What Broadcom model do you have?

---

### Post by wisam on 2009-10-29
> **chrisplymouth said:**
> It automatically compiles in Synaptic. What Broadcom model do you have?


Aha. The thing is that I downloaded the packages manually (even went through some dependency hunting like old days) and installed them using gdebi (dpkg's gui).

I'll try to get synaptic install the packages without having a working internet connection. Not sure how.

---

### Post by wisam on 2009-10-30
> **wisam said:**
> Aha. The thing is that I downloaded the packages manually (even went through some dependency hunting like old days) and installed them using gdebi (dpkg's gui).

I'll try to get synaptic install the packages without having a working internet connection. Not sure how.


Waited a few hours till I had access to a wired connection and installed bcmwl-kernel-source through Synaptic. All fine now.

---

### Post by Coldandwet on 2009-10-30
Hi,

 I had this same problem with a hp netbook. I found the following worked for me: go into synaptic (system > Administration > Synaptic Package Manager), then go to settings > repositories. Uncheck all other software sources and then check the Ubuntu CD-ROM at the bottom (Make sure you have the Ubuntu 9.10 CD in your CD drive). Close the settings window. Reload the package list. Then search for "bcm". There should be one package listed: "bcmwl-kernel-source". Mark it for install and then apply. Exit synaptic, restart your system and then when you log back in you should be able to active your card in the usual way.
This way you don't have to mess about with Lan cables etc...
Oh, and remember to re-enable your software source in synaptic once done.

---

### Post by pixelp on 2009-10-30
Thanks, you saved my day!

---

