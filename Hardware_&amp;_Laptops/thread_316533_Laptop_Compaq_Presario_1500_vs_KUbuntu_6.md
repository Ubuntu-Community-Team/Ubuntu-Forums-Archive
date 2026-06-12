---
title: "Laptop: Compaq Presario 1500 vs K/Ubuntu 6"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by jeecol on 2006-12-10
Laptop: Compaq Presario 1500 vs K/Ubuntu 6.0.6 and 6.10


A. Hardware: 

Compaq Presario 1500 (1536 AP) (about 4 years old)

CPU: Intel P-4 2G.
RAM: Hynix PC2100S-25330, 256 Mb, DDR 266 MHz CL2.5 (8 chips: hynix 248A HY5DU561622AT-H KOREA)


I have three 2.5" hard disks for these tests.

1. IBM travelstar, 20 GB, comes with my laptop, and win-xp oem inside
 (Nov-02. 4200 rpm, ATA/IDE. Model: IC25N020ATCS04-0)

2. IBM travelstar, 15.1 GB 
(Aug-01. 4200 rpm, ATA/IDE. Model: IC25N015ATDA04-0)

3. IBM travelstar, 3.25 GB  
(Mar-99. 4200 rpm, ATA/IDE. Model: DKLA-23240)



B. My trials and results


1. Around Sep, 2006. 
   a. I removed 20 GB HD and put on 3.25 GB HD. I used Ubuntu 6.0.6, it was bootable, but it stopped at 50% of installing process. 

   b. Then I used Kubuntu 6.0.6, it was bootable and I successfully installed it on the 3.25 GB HD (net, sound, VGA all worked)
  

2. Dec, 2006.
 
About Ubuntu  
  a. I tried 3.25 GB HD vs Ubuntu 6.10 --> failed to boot
  b. 15.1 GB HD vs Ubuntu 6.10 --> bootable, but menu froze (no responding) soon. 
    information: error of gnome and some things (sorry I forgot)

  c. 20 GB HD vs Ubuntu 6.10 --> failed to boot  
  d. I angrily removed HD (no HD in the laptop) and booted it with Ubuntu 6.10 --> bootable, but menu froze (no responding) soon. 

 I have checked the Ubuntu 6.10 disk and it was zero error.
---------------------
About Kubuntu

  e. 20 GB HD vs Kubuntu 6.10 --> bootable. (I didn't want to destroy original OS inside, thus I didn't install Kubuntu)

  f. 15.1 GB HD vs Kubuntu 6.10 --> bootable. Every thing worked well after installation.



C. My conclusions

1. Gnome is not friendly to this laptop, sorry, I don't know why! But gnome is good at some of my desktops)
2. And KDE is better for compaq presario 1500.


By the way, I am still a newbie in Ubuntu. I appreciate this forum where I learn a lot useful skills and I am glad to share my experiences here (but no guarantee) 


----------
jeecol = one dollar, in my first language

---

### Post by jeecol on 2007-01-31
Well, I tried more and I found the battery program worked well. But the DVD/CD writer combo was ........

This one should be a combo, DVD read only and CD read and wirte. However, the K3B did not recognize the combo driver as a CD writer.......

---

### Post by Aparatey on 2007-07-27
> **jeecol said:**
> Laptop: Compaq Presario 1500 vs K/Ubuntu 6.0.6 and 6.10

C. My conclusions

1. Gnome is not friendly to this laptop, sorry, I don't know why! But gnome is good at some of my desktops)
2. And KDE is better for compaq presario 1500.

By the way, I am still a newbie in Ubuntu. I appreciate this forum where I learn a lot useful skills and I am glad to share my experiences here (but no guarantee) 

----------
jeecol = one dollar, in my first language

Hello jeecol. I have the same Latop, a Compaq Presario 1500US. And I have issues with the video display in Ubuntu 7.04 Feisty Fawn, when I selected the option :
"Start or install Ubuntu"
After a few seconds I saw a garbled display.
But I could fix the problem. If you get the same garbled display follow the next steps :
Boot from the cd and when you see a Garbled Display
Then you must press "**crtl-alt-f2**" and run the command :

**sudo dpkg-reconfigure xserver-xorg**

Then you have to choose the following options :

Attempt to autodetect video hardware? : **"Yes"**
X server driver : **"ati"**
Identifier for your video card : **"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"**
Video card's Bus identifier : **"PCI:1:0:0"**
Amount of memory (KB) to be used by the video card : **"32768"**
Use Kernel Framebuffer device interface : **"Yes"**
Then a few questions about the Keyboard & mouse
Write default files section to configuration file ? : **"Yes"**
Attempt Monitor Autodetection ? : **"Yes"**
Identifier for the monitor : **"Generic Monitor"**
Video Modes to be used by the X server :** "1400 x 1050"**
Method for selecting the monitor characteristics ? : **"Medium"**
Resolution : **"1400x1050 @ 60Hz"**
Write monitor sync ranges to the configuration file : **"Yes"**
Desired default color depth in bits : **"16"**

Then return to the gnome session usign the **crtl-alt-F7**

And press the **ctrl-alt-backspace** twice. Then the gnome will restart with a 1400x1050 @ 60Hz resolution without problem.

Then you will see the gnome desktop without problem. Then from the system menu select Install Ubuntu.

Just in case you are interested in giving a second chance to Gnome/Ubuntu you can see my Blog where I  posted a more detailed guide to install ubuntu 7.04 on this laptop including lm-sensors, CPU frequency scaling, and modem driver. 
[http://aparateys.blogspot.com/2007/06/installing-ubuntu-704-feisty-fawn-on.html]("http://aparateys.blogspot.com/2007/06/installing-ubuntu-704-feisty-fawn-on.html")

I installed PC-BSD and Solaris 10 in this laptop too. 
Here my experiences :
[Solaris 10 on a Presario 1500]("http://aparateys.blogspot.com/2007/02/installing-solaris-10-on-compaq.html")
[PC-BSD on a Presario 1500]("http://aparateys.blogspot.com/2007/02/installing-pc-bsd-1301-on-compaq.html")

Hope this help someone.

                            Good Luck!

                                              Aparatey

---

### Post by clsgis on 2007-12-17
I built a Debian 4.0 installation for this machine. on an external USB drive.  The display's native resolution was not autodetected; it's 1440x1024.  One anomaly:  after booting we see an eth1 which is the Intel e100, which works, and a mysterious eth0 "Uncap" which doesn't correspond with anything shown by lspci.  What's that?  My Oronoco Silver (Lucent+HERMES 1) 802.11b card works, with WEP.  It apparently doesn't have the hardware to do WPA2.

The system doesn't boot my bootable USB drive.  I had to make a boot CD with syslinux.  For various reasons we didn't want to touch the internal drive.

Everything pretty much "just works" except the software modem and the PC Card slot. I have several true hardware PCcard modems which work in other GNU/Linux laptops. (They look like a Hayes-compatible V.90 external modem connected to a standard serial port.)  None of them was recognized here. Apparently Hotplug wants to put it on /dev/ttyS2, but there is already a ttyS2 in the southbridge that is not connected, and they collide.  My friend will be stuck on Windows until we find her a dial-up solution for this otherwise excellent machine.  We're considering USB modems.  This machine does not have a visiible serial port.  I have limited access to this machine (she's using it on the road); will try Ubunt 7.10 next.  You can reply to this message or via my home page [www.greens.org/~cls](www.greens.org/~cls)

Except for the serial port issues it's a really nice machine.  2.5 GHz CPU, great display, decent battery life.

---

