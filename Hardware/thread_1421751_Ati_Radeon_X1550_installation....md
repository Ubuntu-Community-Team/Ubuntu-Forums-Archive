---
title: "Ati Radeon X1550 installation..."
date: 2010-03-04
forum: Hardware
---

### Post by Josebas on 2010-03-04
Hi everybody!

I have just installed ubuntu in my desktop with AMD64 X2 1gb RAM and ati xpress200 integrated graphic card. Now I have just received an ati radeon X1550 from a friend but I am having problems installing it. I have pluged it in but after reboot the computer wont start. If I have to download the drivers first I would like to know which ones should I use. Now with the Xpress200 works fine but cant get it to work on widescreen 1366x768 resolution which is my screen resolution.

Any help with this would be highly appreciated, as you can see I am quite a newbie!! :p

---

### Post by pme 72 on 2010-03-04
In order to use the X1550 you will probably have to go into Setup before Ubuntu loads and change the Primary Video Adapter setting from Onboard to PCI-E.

---

### Post by Josebas on 2010-03-05
Thanks for the reply pme 72!

I had a similar ati video card installed before with windows xp and it installed automatically. However I have already been in BIOS before and there are no options to change that. Could it be that I have to install the drivers beforehand and then reboot with the card fisically installed? because once I install the card it never boots to Ubuntu... 

Thanks for your help! :)

---

### Post by efflandt on 2010-03-05
Does it boot at all (even to BIOS splash screen and CMOS setup)?  When I installed a hotter video card in my HP desktop long ago it would only start to boot for a few seconds and then shut off.  After I installed a conservatively rated 330 watt power supply, I discovered that it was using maximum power from the wall outlet of about 130 watts, but that was too much for the apparently over rated 250 watt original PSU.  Does your card require a drive cable connection?

That was when I was using an nVidia 6800 I think.  I have not checked power used for my 256 MB Radeon X1300 AGP card (same modules as X1550), but did not have to do anything special for 64-bit Ubuntu on an old AMD64 3200+ (all standard modules).  Except my old AMD64 lacks the lahf_lm instruction used by 64-bit flash, and although someone posted a flashplugin-lahf-fix, it does not work with Hulu, so I am using flashplugin-installer (32-bit flash with nswrapper).

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]

So it depends if by "not booting" you mean it immediately shuts down.  If your display is digitally connected (DVI or HDMI) and it freezes after making a selection from grub menu, try disabling "splash" as a boot parameter and/or try booting into a (recovery) grub menu entry and see if **startx** works after logging in there.  Sometimes splash fails if /etc/usplash.conf is not the native resolution of a digitally connected display.

If using VGA (for your integrated video or the other card), you may need to play around with **cvt** or **gtf** and **xrandr** to find an optimum resolution (1360x765 or 1360x768 ).  I used 1360x765 from my laptop because that was listed (but not enabled) in /var/log/Xorg.0.log and it said 1360x768 was too many lines (maybe due to 1280x800 laptop display).  WinXP uses 1360x764 for that supposedly 1366x768 LCD.

For an older laptop with X200 video, xrandr says maximum 1360 x 1360 and will not let it be set more than 1360.  So if I connect it to a 1080p display, 1360x768 is the most it will do properly full screen.

---

### Post by pme 72 on 2010-03-07
Josebas,

I enabled my onboard Xpress 200 video card. It worked beautifully. I turned the machine off, installed the X1550, loosed the fastners that held the monitor cable to the back of the machine but did not move it and rebooted. When the machine started there is a menu that shows F1=Setup. I quickly pressed F1 and was presented with the Main Setup Menu (not the BIOS). I arrowed over from the Main menu to the Advanced menu. I arrowed down to the field labeled Primary Video Adapter and changed the tic mark from Onboard to PCI-E. I saved my changes and exited Setup. I quickly moved the monitor cable to the VGA slot on the back of the X1550. By that time the Ubuntu Grub Menu was showing and it booted me into Ubuntu with no issues.

I did not have to make any changes to the driver.

---

### Post by Josebas on 2010-03-08
Hi guys!

Been out the whole weekend so now I have time to finally work on my Ubuntu!

efflandt, I will try to do the things you have suggested but as mentioned I am quite a newbie and I am only starting to get used to Ubuntu (Linux) environment. I will report you back when Im done. Or when my desktop is done... :D

pme72, If I install the x1550 but still keep the tv plug (hdmi through dvi adapter, in case it matters ?)connected to the integrated graphic card the screen just wont show anything at all. If I connect it to the x1550 I will see the booting sequence and I can access the BIOS (where no usefull PCI-E options are available) but when Ubuntu would be supposed to load theres nothing on the screen and I cannot hear the sound of it loading (the melody when you ar prompted to log in). I was quite excited about your F1 advice but just nothing happened when I pressed it :sad:

Any other suggestions? I have seen lots of problems around in other threads with the ATI cards but none with a similar problem as mine...

However thanks for your help!

---

### Post by Josebas on 2010-03-08
Hi again, this is a nightmare! For some reason today my Ubuntu has started crashing (in the midle of anything, firefox surfing, rhythmbox, etc I get a white screen and only option is to reset). I had installed the security updates (only those) which I was prompted for right after installation and a couple of Canonical maintained games and now it crashes every 5 to 10 mins if I am actively using the computer. If I am not it can continue its work (mostly torrent download until now) without problems. 

Since I just installed Ubuntu a couple of days ago I just decided to reinstall the whole thing again and start from the scratch but to my surprise, after installation I get the same problem!!!(without any extra installation)

I really dont know what it might be but I am starting to worry myself that i might have to go back to windows!? :confused:

My specs are [http://ixbtlabs.com/articles2/mainboard/barebone-shuttle-st20g5.html](http://ixbtlabs.com/articles2/mainboard/barebone-shuttle-st20g5.html) with a AMD64 x2 4700 1gb ram 200gb seagate barracuda. And I also have a Ati Radeon x1550 card which I am on my way on installing but now there are some more pressing issues, any help with this!? thanks!

PS: efflandt I didnt manage to check any of your advices with my desktop continously crashing...

---

### Post by pme 72 on 2010-03-09
That is an interesting looking piece of hardware you have there. I tried searching Google for "Shuttle PC and Ubuntu" and received a lot of replies. The Ubuntu Forums has a Search function too, upper right hand corner. You could try searching for other posts from Shuttle owners. Perhaps there could be help there too. 

Wish I could be more help.

---

### Post by luotinen on 2010-12-12
Following this thread enabled me to install Ati Radeon X1550 on Ubuntu 10.04 LTS Lucid Lynx:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1604866](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1604866)

---

### Post by liverpoolatnight on 2011-01-08
I have the PCI-E ATi Sapphire Radeon x1550 (256MB) and im just posting to say it works out the box on ubuntu 10.10 both 64 bits and 32 bit. I know as i installed 32 bit then upgraded to 64 bits no issue at all.

---

### Post by mjones141 on 2011-01-12
Hi All
Noob here, I cannot get the ATI drivers to work on my X1550 Radeon. I am running UBUNTU Studio 10.10. I have tried everything in this thread. When I run ATI config, I get no supported Devices found...
Can someone help?
This is my LSPCI - K description of my card
01:00.0 VGA compatible controller: ATI Technologies Inc RV505 [Radeon X1550 64-bit]
    Subsystem: PC Partner Limited Device 0850
    Kernel driver in use: radeon
    Kernel modules: radeon
01:00.1 Display controller: ATI Technologies Inc Device 7167
    Subsystem: PC Partner Limited Device 0851
PLEASE HELP!!! I don't want to use Win-Blows anymore!!

---

### Post by Yellow Pasque on 2011-01-13
> **mjones141 said:**
> Hi All
Noob here, I cannot get the ATI drivers to work on my X1550 Radeon. I am running UBUNTU Studio 10.10. I have tried everything in this thread. When I run ATI config, I get no supported Devices found...
Can someone help?
This is my LSPCI - K description of my card
01:00.0 VGA compatible controller: ATI Technologies Inc RV505 [Radeon X1550 64-bit]
    Subsystem: PC Partner Limited Device 0850
    Kernel driver in use: radeon
    Kernel modules: radeon
01:00.1 Display controller: ATI Technologies Inc Device 7167
    Subsystem: PC Partner Limited Device 0851
PLEASE HELP!!! I don't want to use Win-Blows anymore!!
ATI dropped proprietary support for your GPU a couple years ago. The pre-installed driver open-source is the one you want to use, and trying to install fglrx/Catalyst is just a good way to bork your system: See: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

