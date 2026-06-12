---
title: "Howto: Ubuntu on HP dv9000 series laptop (Covers dv9000 and dv9500 series)"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by EXCiD3 on 2007-07-28
**[COLOR=Red][SIZE=5]THIS TUTORIAL IS DEPRECATED. Most recent tutorial is available here: [/SIZE][/COLOR]**[[SIZE=4]http://excid3.pcriot.com/wordpress/?page_id=28[/SIZE]]("http://excid3.pcriot.com/wordpress/?page_id=28")
[B][COLOR=Red][SIZE=5]
[SIZE=4][COLOR=Navy] Howto: Ubuntu on HP dv9000 series laptop (Covers dv2000, dv6000, and dv9000 series)[/COLOR][/SIZE][/SIZE][/COLOR][/B]

**FOR FEISTY ONLY!** Gutsy is not supported for this Howto. Many problems have sprung up in the Gutsy release and fixes for these problems have not shown to fix the problem for everyone, therefore I have decided to wait to write another Howto until the release of Hardy Heron.

**You can download FEISTY 7.04 here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)**

This Howto is meant for Gnome users. KDE, XFCE, etc users can replace "gedit" in the following tutorial with the text editor of their choice.

_**[SIZE=4] 1) Choosing the right flavour of Ubuntu[/SIZE]**_
Many of you may be wondering whether or not you should install the 32-bit or 64-bit version of Ubuntu. Simply put, if your system supports 64-bit, and you install 64-bit Ubuntu, you will have the best performance. However there is a catch to running 64-bit Ubuntu. Some software, including Flash, do not natively support 64-bit operating systems. Work arounds exist that allow these programs to run on 64-bit operating systems, but they require work to setup. If you want your operating system to "just work" or you are new to Ubuntu/Linux, I would recommend 32-bit as you will not have to fix these issues, but you will have a slightly (maybe not noticeable) slower system.

[SIZE=4]_** 2) Boot into the Ubuntu installation CD.**_[/SIZE]
    Should I install with the LiveCD or the AlternateCD?
    AMD based laptop models will have trouble booting into the LiveCD. I would recommend these users to choose the AlternateCD for installation. The AlternateCD uses a terminal-style installation method that allows for more flexibility on installation.
    Intel based laptop models are almost completely compatible with Ubuntu and do not require any modification in order to boot into the LiveCD. I would recommend LiveCD installation on these models, unless you need the AlternateCD for a more complex installation or you prefer the terminal-style interface.

[SIZE=2]**     A) Booting into the LiveCD**[/SIZE]
    If boot hangs or fails, reboot. At the menu press F6 and add these parameters: ```
noapic irqpoll noirqdebug
```Any required parameters used to access the LiveCD will also be needed to boot into the installation. You can add them at the Grub boot menu later. Once you are in Ubuntu, modify /boot/grub/menu.lst and change the necessary parameters. Save this file and you wont need to add the parameters each bootup.
 NOTE: Only adding 'noapic' to the boot parameters has been reported to disable the USB ports. Only adding 'nolapic' has been reported to prevent the NVIDIA driver from loading correctly. However use of both 'noapic and 'nolapic' is not know to cause these problems. Also if you use "IRQPOLL" or "IRQFIXUP" along with "noapic" will enable usb support. Feedback on this would be appreciated.

If you receive the tty job control problem, please read this thread: [http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control](http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control)
and this: ```
Select  safe mode, hit F6 and add the option: "all_generic_ide" right before "quiet splash"
```[SIZE=2]**     B) Booting into the AlternateCD**[/SIZE]
    You should have no probelms booting into the AlternateCD on any HP laptop.

[SIZE=4]_** 3) Install Ubuntu**_[/SIZE]
    NOTE: drives are 'sd??' because these laptops use SATA hard drives.
    Recommended for Dual-booting on a laptop with 2 hard drives:

        GRUB installed to MBR of sda1
        sda1 - Windows
        sdb1 - Ubuntu
        sdb2 - Swap (Size of RAM, must not be less or hibernate will not work)

    This is just what I would recommend for installation. If you have burned off the Recovery CD/DVD's feel free to delete the Quickplay and Recovery partitions. I never used either of them, so they were just wasted space for me. It is best to remove these partitions before installing Ubuntu, but you can remove their GRUB entries later by editing /boot/grub/menu.lst. This configuration also will allow you to reinstall Windows using the Recovery CD/DVD's with losing your Ubuntu installation. These CD/DVD's format your entire first hard drive which would wipe your Ubuntu install. There is no easy way to use the Windows bootloader to launch Ubuntu from different harddrive. I looked into this in case I wanted to remove Ubuntu later. It is probably possible, but it would be very complicated. Installing GRUB to the MBR of sda is your best and safest option.

[SIZE=4]_** 3) Try out Ubuntu!**_[/SIZE]
    If your Ubuntu installation failed to boot the LiveCD you must add the same options to the GRUB boot line.
    To do so, at the GRUB menu, hit 'e' and add 'noapic' to the end linux image boot line. Make sure you leave a space in front of it.
**     NOTE: **If a new kernel is added, this option will need to be added to its entry also.

[SIZE=4]_** 4) Install drivers**_[/SIZE]
**     NVIDIA/ATI graphics driver**
Install via the Restricted Drivers Manager which can be found at System->Administration->Restricted Drivers Manager

**Useful links: **
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)





**     Intel 3945ABG Wireless** - No driver installation needed
If you are having problems connecting, enable the extra package repositories and install linux-restricted-modules, and don't forget wpa-supplicant if you need to use WPA security.

**         NOTE:** Booting will sometimes pause if the wireless switch is set to "on". It has been reported that turning the wireless switch to off during bootup will fix this problem and increase boot times. It only resulted in no available networks for me.

**     Intel 4965AGN Wireless**
[http://ubuntuforums.org/showthread.php?t=493095&highlight=4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=4965)
        Best if you have the most recent drivers.
        [http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi) has been reported to work.

**     Broadcom 43xx Wireless**
    Usually fairly tough to configure properly, the Broadcom wireless card aren't support out of the box in Ubuntu. To install the drivers, follow this link: 
    [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

**         NOTE:** Sometimes recognized as "Broadcom Corporation Dell Wireless 1390"
    
    Other helpful links:
    [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
        Use the most recent drivers from the HP webiste for best results: [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe).
        NDISwrapper tutorial:[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

**     Ricoh Webcam**
Works out of the box using V4L2 driver (in Ekiga Softphone).
        Reports of this not working correctly out of the box. Try using this driver here: [http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/)

**     Sonix/Microdia Webcam**
        Open a console and enter: ```
lsusb
``` If it looks similar to the following ```
Bus 002 Device 002: ID 0c45:62c0 Microdia
``` 1) Install subversion from the repos. Open Terminal type this: ```
sudo apt-get install subversion
```    2) In Terminal enter this:
            ```
svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
            cd trunk/
            gedit Makefile
```        3) Change the following in the Makefile:
            INSTALL_MOD_DIR := usb/media
            to
            INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo

        4) Save it and close. In Terminal type:
            ```
make
            sudo make install
            sudo modprobe uvcvideo
            gstreamer-properties
```        5) Under VIDEO, select v4l2 and choose USB 2.0 for device.

**         Synaptics Touchpad**
            1) Install GSynaptics (or KSynaptics if you use KDE) through Synaptic Package Manager

            2) Edit xorg.conf to enable Touchpad app to use touchpad.
                ```
sudo gedit /etc/X11/xorg.conf
``` Scroll down to the "Synaptic Touchpad" section and add the following line:
                ```
Option         "SHMConfig" "true"
``` Save xorg.conf

            3) Xserver must be restarted for this to take effect. You can do this by pressing Ctrl-Alt-Backspace.

**[SIZE=4]_ 5) Other items_[/SIZE]**

[B]Slow Bootup Times
[/B]If you are experiencing long boot times, try this fix:
Comment out all lines in /etc/network/interfaces by puttig a "#" in front of everything except:
1) Open terminal
```
sudo gedit /etc/network/interfaces
```2) Comment out every line (put a # at the beginning of the line) **except** for this:
```
auto lo
iface lo inet loopback
```This is what mine looks like:```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```After trying this boot times increase impressively and wireless should still work. If it doesnt work, go back and uncomment those lines.
**     Media Card Reader**
        Works out of the box. Only SD cards have been tested. Please send feedback for the other types of media (MS, MS Pro, MMC, and XD cards)

**     VGA Out**
        Works out of the box. Screen is cloned by default. Does not work with the nv driver when the xserver is running however,
        just bunch of randomness on the screen. Install the NVIDIA driver as described above if you would like to use this.
**         NOTE:** Use Nvidia-Settings to configure resolution and refresh rate as the Screen Resolution app does not correctly detect refresh rates.

**     SVideo Out**
        ???

**     HDMI Out**
        ???

**     Remote Control**
        Works out of the box

**     Firewire**
        Works out of the box

**     SPDIF**
        ???

**     Battery Calibration**
        HP recommends battery calibration every three months. This means disabling low power shutdown and allowing the computer to discharge the battery to 0% charge.
        To do this, change your Power Management setting "When battery power is critically low:" to "Do Nothing".

**     Laptop Mode**
        Laptop mode is disabled by default in Ubuntu. To enable this open Terminal and type:
        ```
sudo gedit /etc/default/acpi-support
``` At the bottom of the file, there is the ENABLE_LAPTOP_MODE variable, set this equal to true. A restart is required to enable this setting.
        Read through this file to see some of the other options.

        Other power applications can be found in the Extra Repositories. To install them, open Synaptic and install the following packages:
        laptop-mode
        laptop-mode-tools
        laptop-detect
        cpufreqd
        cpufrequtils

**     Suspend/Hibernate**
        Supposedly adding "nosmp" as a boot option, disabling Sync To Vblank in Beryl, and if you edit the /etc/default/acpi-support and set POST_VIDEO=false, suspend and hibernate
        should work better. QUESTION: Is "nosmp" the option that makes this work? Anyone know?

**     Suspend**
        Works! Scary looking whitewashed screen on resume, but it works. Intel wireless sometimes stops working after suspend/hibernate.
        First suspend, wireless doesnt come back, every suspend after, wireless works.

**     Hibernate**
        Works! Same results as suspend. Unfortunately, after tweaking Feisty it is faster to shutdown and bootup than it is to hibernate. 

**     Lightscribe**
        Lightscribe has been reported to not be functional even using the Automatix2 Lightscribe and the packages directly from the Lightscribe website.

**     Microphones**
        Works out of the box. Volume may be muted by default. Just change the 'Int Mic' volume in Volume Control if it happens to be muted.

**     Speakers**
        Works out of the box. Some complaints about low volume and other sound issues.

**     Headphone Jacks**
        Works out of the box. Requires a more recent build of ALSA than what was packaged with Edgy.

**     TV Tuners**
        No known drivers

**     Bluetooth**
        Works out of the box

**Fingerprint Reader**
[http://reactivated.net/fprint/wiki/Main_Page](http://reactivated.net/fprint/wiki/Main_Page) - Thanks to [mo0n_sniper]("http://ubuntuforums.org/member.php?u=324199")

If you have any information that I forgot to include, please, please let me know!! Thank you guys for all your help in getting this information together! Please ask questions and post results!

I would like to thank all the contributors at the "Official Hp Dv9000 Laptop Thread!!" which can be found here: [http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815) Several of these sections are based off of posts in that thread. Thanks guys!

---

### Post by Kingsley on 2007-07-30
Step 2 of Sonix/Microdia didn't work for me.

This did:
```

svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
cd trunk/
gedit Makefile

```

---

### Post by EXCiD3 on 2007-07-31
> **Kingsley said:**
> Step 2 of Sonix/Microdia didn't work for me.

This did:
```

svn checkout http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
cd trunk/
gedit Makefile

```

Thanks for cathing that for me. Did everything else you tried work?

---

### Post by Kingsley on 2007-07-31
Yeah, everything is working as I expected. My laptop is a dv6000t btw.

---

### Post by codetroll on 2007-08-04
Installed Kubuntu on an AMD HP dv9000 using your walkthrough.  Thanks so much for having it all in one post.  I am new to Linux and your post made it a much less daunting task than I thought it would be.  I only had one major issue.  After I got everything setup I hit Full Upgrade in Adept.  After my next reboot I got a blank screen with a blinking cursor at the top.  I saw on the forums that it was probable because of the kernel upgrade.  

I actually saw on an unrelated post that I could hit 'Ctrl-Alt-F1' to get back to the shell.  Once I did that I just ran envy again to recompile the nvidia driver for the new kernel.  Since then it has been smooth sailing.

---

### Post by ryandle on 2007-08-05
Hey all,

I stumbled upon this thread while desperately searching for a fix for my hp dv9420us (AMD processor, i dont know if that makes a difference).  Im actualy trying to install Kubuntu, does anyone know what steps need to be taken with KDE?  Ive tried noapic and nolapic and it boots into kubuntu now but the system locks up within 5 minutes (mouse still moves around but no windows / menus respond)



im very frustrated, i read great reviews about this laptop but i never thought it wouldnt be linux friendly!

---

### Post by ryandle on 2007-08-05
Got everything working now, thanks to your directions.  I'm embarrassed to say that somehow my CD's got mixed up and i was isntalling 6.10 instead of 7.04.  I dont know if this had anything to do with it, but 7.04 gave me no trouble! Thank you so much for creating this thread.

---

### Post by Inxsible on 2007-08-09
My lsusb states ```
Bus 001 Device 003: ID 0c45:62c0 Microdia
```
But it worked out of the box for me in Ekiga. If I follow what you have outlined, will the webcam work in other software ?

I might also try the suspend and hibernate as that is something that I havent quite figured out yet. i tried a bunch of things with uswsusp, but it didnt work.

---

### Post by EXCiD3 on 2007-08-09
> **Inxsible said:**
> My lsusb states ```
Bus 001 Device 003: ID 0c45:62c0 Microdia
```
But it worked out of the box for me in Ekiga. If I follow what you have outlined, will the webcam work in other software ?

I might also try the suspend and hibernate as that is something that I havent quite figured out yet. i tried a bunch of things with uswsusp, but it didnt work.

If it worked out of the box in Ekiga, check to see if it was using the V4L2 driver. As long as the driver support V4L2 then you should be able to use it in anything else.

**NOTE:** The suspend/hibernate stuff worked fairly well, certain things had problems upon resume, however it appear to work most of the time. It is definitely still unstable so don't use either of them if you need stability. Its just nice to have them. Try it out, see if it works well for you, let us know how it goes and if you find anything useful. ;)

---

### Post by Felipe_U on 2007-08-10
Hello,
I have a dv9275la Notebook and it came with the Ricoh Webcam, and it didn't work out of the box. I have the 1810 Ricoh webcam, I didnt' found the drivers exactly for the model but I did find drivers for the 1830 and above. The good news is the driver worked out just fine and you can download a .deb for your kernel[COLOR=Red] **[here]("http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/")**[/COLOR]. I installed the .deb with gdebi and the webcam runs perfectly. Hope this help someone :)

One question, how can I test if my bluetooth is working? I dont have any apps that use bluetooth

Regards,
Felipe

---

### Post by EXCiD3 on 2007-08-10
I'm not sure how you could test bluetooth out, maybe connect it to a phone? there are a couple of apps in the repositories you could install to see if it would do anything. If you don't mind, ill prolly add that deb link to the tutorial. thanks for the input.

---

### Post by MarsdaleSA on 2007-08-11
I see a lot of threads continue to recommend the installation and use of automatix. I understand that it's a nice easy tool to use but I feel it's important that you understand it's not good practice and is deemed 'Actively Dangerous' to ubuntu.

You may read what has been found here in the forums : [http://ubuntuforums.org/showthread.php?t=517202]("http://ubuntuforums.org/showthread.php?t=517202")
as well as on /. when they covered the article : [http://linux.slashdot.org/article.pl?sid=07/08/04/1944211]("http://linux.slashdot.org/article.pl?sid=07/08/04/1944211")

After you've read what it does and have understood it, by all means use it if you feel compelled to do so. As someone else mentioned, if you want out of the box multimedia try Linux Mint (it is ubuntu based). Check it out at distrowatch : [http://distrowatch.com/table.php?distribution=mint]("http://distrowatch.com/table.php?distribution=mint")

---

### Post by EXCiD3 on 2007-08-11
If you noticed, Automatix is basically one of the last options to install the things i mention. It is safe for installing the Lightscribe driver as it only uses alien to convert the rpm to deb. and it is next to installing from the repositories which is probably more out dated.

---

### Post by philvdm on 2007-08-11
My system : HP dv9000  ( Dual AMD64 ) running Ubuntu 7.04 for 64 bits

My wireless controller :
03:00.0 Network controller [0280]: Broadcom Corporation BCM4310 UART [14e4:4312] (rev 02)


I struggled with my wireless card for a while and got very frustrated until I managed to make it finally work with ndiswrapper.

With an AMD64, the trick is to get the latest driver from HP web site. Download sp34152.exe here [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe) and cabextract it  ( Caution : sp33008.exe which I tried first does not work with this chip)

---

### Post by EXCiD3 on 2007-08-15
Hey thanks for the input, i'll add that link in the HOWTO.

---

### Post by kornface13 on 2007-08-16
YOU ARE AMAZING!!!!  This worked perfectly.  Kopete still doesn't recognize the webcam...maybe I need to reboot. 

THanks a million!!!!!

---

### Post by EXCiD3 on 2007-08-16
> **kornface13 said:**
> YOU ARE AMAZING!!!!  This worked perfectly.  Kopete still doesn't recognize the webcam...maybe I need to reboot. 

THanks a million!!!!!

It could just be that you don't have V4L2 selected inside Kopete. Which webcam did you have, the Sonix/Microdia or Ricoh webcam?

***EDIT*** If you experiencing slow bootup times, I have found several posts that cut bootup time by at least half. I will add then steps along with a *hopefully* working version of the Broadcom 43xx ndiswrapper section... Should be up by tomorrow night.

---

### Post by BluChaoz on 2007-08-22
Hopefully someone can help me out, I have read over the forum here so I won't ask any obvious questions I will only give my situation and maybe someone can either PM me or feel free to post a reply, I am only trying not to annoy anyone.

I have an dv9208nr basic HP Pavilion, I had a friend of mine mail me over a copy of Ubuntu Studio...when I say mail me I am currently stationed in Baghdad,Iraq so I don't have any kind of stable connection to the internet. I was able to install Ubuntu to my laptop but then everytime I try to reboot my screen looks like it's melting and I just keep having problem after problem with it, I really wanted to stick with Ubuntu so I looked into it and found out it was a graphics driver issue, easy fix but the issue I am having now is it seems that Ubuntu is download heavy which you all should know, but I can't do that without an internet connection. So I guess my actual question would be how in god's name do I get Ubuntu up and running on a dv9208nr when I have no access to any kind of stable internet?

If someone can help me it would be an incredible act of kindness. Thanks for taking the time to read this.

SGT Greene,Richard
Bco 2-3 BTB, 2BCT, 3ID

---

### Post by udz2002 on 2007-08-23
I installed the Ubuntu 7.04 AMD64 using the text installer. Everything went great until I performed the full upgrade and aplied all 116 updates. I restarted the system and now it loads to one block and sits there. I rebooted and tried loading the (recovery) and it hungs on "*Loading hardware drivers...".

Can anybody help me?

---

### Post by EXCiD3 on 2007-08-23
Can you Ctrl-Alt-F1 to a command prompt? Does the recovery boot option do anything different for you?

---

### Post by adrman on 2007-08-24
Well for my first post I need to say thanks for this thread.  As a complete newbie to Ubuntu and linux in general, it was a huge help for the install of 32bit 7.04 on my HP dv6000 (AMD Turion).  Now for the stupid newbie question:  I'm still encountering difficulties with hibernate and suspend.  I've followed the suggestions with one exception, disabling sync to vblank in Beryl.  Why?  Because I can't find the Beryl Manager.  Any searches I perform refer to Beryl as beta, but I presume that was before 7.04. since a search of my hard drive reveals a few Beryl files present.  Any chance someone can point me in the right direction?  Thanks.

---

### Post by udz2002 on 2007-08-24
I added noapic to the boot options and booted fine.  I have a new problem though...

I stalled Envy and rebooted, now my wireless does not work. In xorg.conf under device section, driver is nv (rather than nvidia). The video looks the same as it did before the update, I thought maybe I would be able to use the TV Out feature.

---

### Post by EXCiD3 on 2007-08-24
> **adrman said:**
> Well for my first post I need to say thanks for this thread.  As a complete newbie to Ubuntu and linux in general, it was a huge help for the install of 32bit 7.04 on my HP dv6000 (AMD Turion).  Now for the stupid newbie question:  I'm still encountering difficulties with hibernate and suspend.  I've followed the suggestions with one exception, disabling sync to vblank in Beryl.  Why?  Because I can't find the Beryl Manager.  Any searches I perform refer to Beryl as beta, but I presume that was before 7.04. since a search of my hard drive reveals a few Beryl files present.  Any chance someone can point me in the right direction?  Thanks.

The Beryl section is meant only for people who are using Beryl itself. If you are using any kind of compositing window manager (Beryl, Compiz, or Compiz Fusion) you will want to change this setting. I have no idea why/how it works and had just seen this mentioned in a thread. I figured it would be helpful to post as hibernate/suspend have had very little success so far. Gutsy Gibbon (Ubuntu 7.10 to be released in October) will have better support hopefully. If you absolutely need these options, you will probably have to wait. However, [http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/) is a Howto that you can use to speed up Ubuntu. It has sped up my boot/shutdown times so fast that i shutdown rather than suspend/hibernate. It is almost just as fast.

> **udz2002 said:**
> I added noapic to the boot options and booted fine.  I have a new problem though...

I stalled Envy and rebooted, now my wireless does not work. In xorg.conf under device section, driver is nv (rather than nvidia). The video looks the same as it did before the update, I thought maybe I would be able to use the TV Out feature.

Did you use Envy to configure your xorg.conf for you? Did you set the driver to "nv" yourself? What laptop are you using, and what wireless card does it have? A little bit more info would be helpful.

You could try reinstalling the graphics driver using Envy and having it configure the xorg for you again. You shouldnt be using the "nv" driver, it should be set to "nvidia".

Hope this helps guys!

---

### Post by Spirit_of_68 on 2007-08-24
I am a total noob, I am trying to get the live cd to run on a HP DV6000 AMD Turion with no success. :(

I have followed the instructions and added noapic irqpoll noirqdebug but it still fails and comes up with the message about the X window system

Am I typing it in correctly? 

Code: noapic irqpoll noirqdebug

Any help would be much appreciated.

Thanks

---

### Post by EXCiD3 on 2007-08-24
I think your best bet is to install using the AlternateCD and then use the boot parameters on the installed copy of Ubuntu. For some reason there are troubles booting using the LiveCD on the AMD based systems. I personally don't have one and therefore can't recommend much other than using the Alternate CD to install with.

---

### Post by adrman on 2007-08-24
> **Spirit_of_68 said:**
> I am a total noob, I am trying to get the live cd to run on a HP DV6000 AMD Turion with no success. :(

I have followed the instructions and added noapic irqpoll noirqdebug but it still fails and comes up with the message about the X window system

Am I typing it in correctly? 

Code: noapic irqpoll noirqdebug

Any help would be much appreciated.

Thanks

I know it's not any help, but I have the same system and those parameters did allow me to boot the live cd.  Before I found this thread I had successfully booted the live cd adding just noapic.

---

### Post by adrman on 2007-08-24
> **EXCiD3 said:**
> The Beryl section is meant only for people who are using Beryl itself. If you are using any kind of compositing window manager (Beryl, Compiz, or Compiz Fusion) you will want to change this setting. I have no idea why/how it works and had just seen this mentioned in a thread. I figured it would be helpful to post as hibernate/suspend have had very little success so far. Gutsy Gibbon (Ubuntu 7.10 to be released in October) will have better support hopefully. If you absolutely need these options, you will probably have to wait. However, [http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/](http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/) is a Howto that you can use to speed up Ubuntu. It has sped up my boot/shutdown times so fast that i shutdown rather than suspend/hibernate. It is almost just as fast.

Hope this helps guys!

Thanks.  I was pretty much coming to the same conclusion myself, but it's good to have confirmation.  Everything else is working perfectly.  I'll give the boot/shutdown tips a go and work that way until GG appears.  Cheers!

---

### Post by EXCiD3 on 2007-08-24
Hey no problem. That's what we are here for. Any questions dont feel bad about asking! Good luck!

---

### Post by gogodidi on 2007-08-25
Hello, I got a brand new dv9510eo yesterday and I installed ubuntu using the alternate CD

I resized the NTFS partition (letting vista keep 50 gb) and parceling the rest out to result in the following partition table:

sda:
sda1: pri /media/windows
sda2: pri /
sda3: pri /boot
sda4: log /home
sda5: log swap

My swap space is 2.4 GB.

After the install, I reboot into ubuntu. a little text, then black.

I try the "noapic irqpoll noirqdebug" ... sequence in the boot parameters, with no result.

I remove the splash from the end of the line and then text scrolls:

(various numbers saying that it cant allocate memory for device at pci 5:0-0 (the screen)

*reading files needed to boot... [OK]
*setting preliminary keymap... [OK]
*preparing restricted drivers... [OK]
*starting basic networking... [OK]
*starting kernel event managers... [OK]
*loading hardware drivers
error receiving uevent message: No buffer space available

When I add "noapic irqpoll noirqdebug", it happily skips beyond that and then allows me to log in on the command line.

But, the X server cant start. Reading the output, it seems that no screens have been configured.

So, what I have gathered is that it cant reserve any memory for the screen and that no screens have been configured, what do I do?

I think the first step is to configure my screen. Anybody know how to help me with this?

[EDIT]
[UPDATE]
Alright, The solution is fairly simple:
Boot using the "noapic irqpoll noirqdebug" parameters, you can remove the splash if you want, it wont ever show anyway.
Then wget the envy package:
$ wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)
$ sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
$ envy -t

Let it do all the work. Then restart. Now you have X.
On my version of the series: dv9510eo, most things will work out of the box. 

I cant for the life of me get wireless working though. Note Im not that great. Its certainly possible.

---

### Post by EXCiD3 on 2007-08-25
Oh yeah, sorry about not adding that section about installing the graphics drivers for the newer video cards. My friend had the exact same problem. I'll update it for you guys. Thanks!

What wireless card do you have? Is it the wireless N card? I have not gotten hardly any feedback on those cards. Please post some more informatoin or message me so we can try to figure it out. Hopefully Gutsy will have increase compaitiblity with these laptops.

---

### Post by gogodidi on 2007-08-25
Hello,
I got wireless working for a while (It's a broadcom). Right now I am struggling with not being able to boot into Linux at all!

Its a guessing game.

It hangs either at the very beginning of the boot process, or at "configuring network interfaces". I can't Ctrl+c/Ctrl+z there to skip it either, so it's very irritating!

Are there any boot parametres to skip the network init?

[EDIT]
I managed to boot in by adding only noapic to the boot parameters, There do not seem do be any problems. I do not have wireless access. I will just keep a log here of how things go. Then later, we can just filter out the junk.

Update #2:
I think that we just need to add noapic to the boot parameters, no longer hangs. I will try to see if we can't have that fancy splash parameter also.
Wireless still not working. Reinstalling ndiswrapper. Installing the "experimental" ie unstable development release. Now restarting

Update #3:
Splash does not work at all. If you use a dv9510eo, remove the "splash" parameter and add "noapic" parameter. Boot should work.
Wireless is now the problem. It seems that if I have the wicd network manager installed, it hangs at startup unless there is a connection to the network available by means of cable.
I'm going to see what happens if I use the ndiswrapper tool available in the repository.

---

### Post by gogodidi on 2007-08-25
Alright, I have it pretty much down to a science now. There are some small problems with the wireless, but I think it works. I would like to do some more reboots before putting my seal of approval over it though.

How to Install Ubuntu 7.04 64 bit on a hp dv9510eo laptop :

**Step 1: Which disk?**
Download and burn the alternate cd: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Boot into the installation. You should not need to edit any boot flags yet.

**Step 2: Installation**
Install Ubuntu. This is left mostly up to you. At some points I recall there being the need for the internet, so if you let the installer configure your network already, leave the cable in, don't take it out.

**Step 3:  booting**
When rebooting into your fresh, clean Ubuntu, press 'e' on the first option at the grub menu. remove the splash boot parameter and add "noapic irqpoll noirqdebug" to the end, so that it looks something like this:
```
kernel		/vmlinuz-2.6.20-15-generic root=UUID=91ab0c9e-4e06-4db7-9e3a-9e9da72b0adf ro quiet noapic irqpoll noirqdebug
```

Hit enter and then b to boot into your Ubuntu installation.

**Step 4: NVidia and Grub**
You will have to put up with some complaints from the X server for a while. But this sequence will remedy your problems. 
The envy installer will want to reboot, so first we will get our grub stuff done:

Open your grub menu up for editing:
```
$ sudo nano /boot/grub/menu.lst
```

And edit the same entry as before. (It should be the first non-commented entry)
It should now look like this: (changed place is in bold. Note there is NO "splash" entry).
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=91ab0c9e-4e06-4db7-9e3a-9e9da72b0adf ro **quiet noapic irqpoll noirqdebug**
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault
```

That's done, now we do our NVidia stuff:

```
$ wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
$ sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
$ envy -t
```

Run through the program, the defaults are pretty much good enough.

Reboot.

You should now have X. Sign in.

**Step 5: Wireless and wired network connections**

This is where I don't feel very comfortable. I have many problems with the wireless stuff. I am currently on a wireless connection, it's pretty magical that I have managed to glue it together, but this is what I did.

I installed ndiswrapper using the guide here: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) . I used the experimental version. No not bother to install the newest driver from hp, It is extremely annoying, requires windows, and ends up not working.

Run the installer, It tells you that you might want to reboot, we will do this later.

Open a terminal. Type:
```
$ sudo apt-get install wicd
```

I don't know how gnome does it, but you might want to make sure that "wicd-tray" starts up at every login, it will be a little icon in your system tray. (kde users just symlink in ~/.kde/Autostart).

(if you want, you could put a reboot in here, just to be safe)

Now open your grub menu file again:
```
$ sudo nano /boot/grub/menu.lst
```
We are going to change the boot parameters again. Note again that there is no "splash" parameter:
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=91ab0c9e-4e06-4db7-9e3a-9e9da72b0adf ro quiet **noapic nolapic irqpoll noirqdebug**
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

```

That would lead you to the Setup i have now. 

Update: **Headphone jacks do not work!** It just duplicates the sound to from the internal speakers, The speakers do not go silent.

Good luck, seriously!

I want to thank EXCiD3 for this great guide, it really helped a lot. I'm just trying to fill the void between the systems. Not sure about how well I did though.

---

### Post by kmfdmk on 2007-08-26
I'm running a HP DV2000 (came pre-loaded w/ Vista).  AMD Turion X2 64bit

Running Ubuntu Feisty Fawn on it I believe (If I could figure out where to find out for sure).

I was able to do the Synaptic TouchPad part.

I was also able to successfully perform the Microdia web cam bit, and was also able to successfully install the NVidia drivers via Envy.

---

### Post by udz2002 on 2007-08-26
It seems like any time I install something, my wireless quits working. I have got it to work twice, right now it is not working.

---

### Post by siralphred on 2007-08-26
thanks for your guide  i have always had everything workin on my hpdv6000se  except for my microdia webcam,  sometimes it works in ekiga but in amsn it give a chopy image and it freezes with the output: cannot capture from image. So i followed your guide and when i run gstreamer-properties and try to test the video after selecting V4l2 i get this error:

The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 51 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


hopefully you can help me or point me in the right direction, thanks

Anyone having problems with the broadcom wireless drivers for their hp should follow this thread, its the best i have come across....very simple and it works [http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless](http://ubuntuforums.org/showthread.php?t=405990&highlight=wireless)

---

### Post by EXCiD3 on 2007-08-26
That makes it sounds like a programming error with the driver....I dont know what to tell you. It appears to be something that the driver programmers would need to fix. You could try looking for other threads about this webcam on the forums, or google your problem. Sorry I cant be of any help.

---

### Post by siralphred on 2007-08-26
yeh thats wat i was thinking too...but i will play with it till i find something, good work on your guide

---

### Post by EXCiD3 on 2007-08-26
post back if you get things figured out

---

### Post by siralphred on 2007-08-26
One last thing...i had already tried to compile uvc before i saw your guide, so i just went ahead the edited the Makefile and recompiled, do u think i should have removed the first compilation before trying your guide? if so how can i remove it.....  make uninstall?

---

### Post by EXCiD3 on 2007-08-26
You know, im not really sure... I think its best to remove it first, but i dont really know what command "make uninstall" or "make remove" im not sure...sorry. I havent been much help today... :(

---

### Post by siralphred on 2007-08-26
i tried both remove and uninstall to no avail....how about jus deleting the entire folder and starting afresh?

---

### Post by BongoBob on 2007-08-26
Just wanted to let everyone know, I just got a pavilion dv6448se, and thanks to this guide have gotten everything working great. Thanks alot man :)

---

### Post by EXCiD3 on 2007-08-26
Yeah, but that wont matter if it has already been installed. That folder is just used for storing the source code. Once you install it it puts the appropriate files in the folders such as the /bin folders, etc. So I'm not exactly sure what you can do. You might try searching the repositories ofr it.

---

### Post by solongfx on 2007-08-27
Thanks for this guide, it's been wonderful in helping me set up ubuntu on my Pavilion DV9565ea.

the only problem i have is that the splash screen doesn't load and nothing appears until the login screen, though this isn't a big problem as I just remove splash and quiet from the grub entry.

The other annoyance i'm experiencing is that sometimes X wont start, saying the filesystem is read only.. this happens even if I remove "ro" from the grub line... any idea what is causing this? Sometimes it happens, other times it doesn't...

Also, does anyone know of a fingerprint reader application/drivers for the HP integrated fingerprint reader? It just feels a bit of a waste having it sit there integrated but doing nothing. And does anyone have a recommendation for a speech recognition program? 

Thanks for your time and this guide!

---

### Post by EXCiD3 on 2007-08-27
For the splash problem, did you remove splash from the boot parameters?

I have no idea what is wrong with the xserver not starting, can you post a little more info?

As for the finger print reader, I forgot to include that in the tutorial. I have not heard of any drivers yet. Could you post the results of "lspci" and "lsusb" ? Hopefully it will be detected in one of those, from there we can search for the appropriate drivers if they exist...

---

### Post by solongfx on 2007-08-27
~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration a 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)



lsusb:
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 064e:a101 Suyin Corp. 
Bus 001 Device 001: ID 0000:0000  

As you can see, the webcam didn't show up (i don't think?) in either, as the guide stated. However, it installed using the method for  the  Sonix/Microdia Webcam. Anyway.. I can't see the fingerprint reader there? I think though that vista uses Bioscrypt VeriSoft to control it?

---

### Post by EXCiD3 on 2007-08-27
I dont think the webcam showed up either. Unless it is actually a Ricoh webcam...i dont know.

I don't know exactly what the Authen Tec, and the Suyin Corp devices are but they could possibly be your finger print reader. I personally don't think I have even read anything about finger print readers in ubuntu yet...

---

### Post by solongfx on 2007-08-27
Alright, well I'll keep searching around and if I find anything I'll let you know.

---

### Post by siralphred on 2007-08-27
I finally got my Microdia inbuilt webcam for my hp dv6000 i used the Sn9cxxx driver, anyone interested can download the deb here [http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7](http://www.linux-projects.org/modules/mydownloads/viewcat.php?op=&cid=7)  i read its for the 2.6.20-16 generic kernel but with some luck it will work with other kernels, so finally all my components are working pefectly...whew:)

---

### Post by EXCiD3 on 2007-08-27
Thanks for the post, ill add it to the tutorial ;)

---

### Post by siralphred on 2007-08-27
no problem, hopefully it will save someone the hustle, btw i saw your post in a different thread suggesting the use of CF installer  for compiz....i tried it once but it doesnt have the screensaver and the swift shifter plugins, at least it didnt when i tried it 2 days ago,  do u know how to get those plugins(i really like and use them) with that installer ?

---

### Post by Darkangel14615 on 2007-08-28
Has anyone tried this with the similar Presario Series notebooks?

I've got a Presario V6210US (RP203UA#ABA) that has similar hardware, and I've been able to install Fedora Core 6 (minus the Broadcom 1390 Wireless drivers), but I've always liked Ubuntu a bit better because of the greater support. I might try your guide to see if it helps.

If it makes any difference the V6210US is:

AMD Turion 64 Mobile MK-36
nVidia GeForce Go 6150
nForce 410 Motherboard
Broadcom Dell (lol) Wireless 1390 MiniPCI WLAN
Ricoh Media Card Reader

Seems to be almost exactly the same hardware, and I shouldn't have to deal with those pesky webcam drivers ;D

I'll give it a go and see how things turn out, and post my results here (I'm surprised I haven't found any threads on the Presarios, this laptop was a real steal at $650 ^_~).

---

### Post by EXCiD3 on 2007-08-28
> **siralphred said:**
> no problem, hopefully it will save someone the hustle, btw i saw your post in a different thread suggesting the use of CF installer for compiz....i tried it once but it doesnt have the screensaver and the swift shifter plugins, at least it didnt when i tried it 2 days ago, do u know how to get those plugins(i really like and use them) with that installer ?

You know, I just realized I'm missing those plugins too. I found this thread on the Screensaver plugin, but have yet to try it out: [http://forum.compiz-fusion.org/showthread.php?t=492](http://forum.compiz-fusion.org/showthread.php?t=492). Also the Swift switcher plugin is included with Compiz Fusion here is a link to that thread: [http://ubuntuforums.org/showthread.php?t=534614](http://ubuntuforums.org/showthread.php?t=534614).


> **Darkangel14615 said:**
> Has anyone tried this with the similar Presario Series notebooks?

I've got a Presario V6210US (RP203UA#ABA) that has similar hardware, and I've been able to install Fedora Core 6 (minus the Broadcom 1390 Wireless drivers), but I've always liked Ubuntu a bit better because of the greater support. I might try your guide to see if it helps.

If it makes any difference the V6210US is:

AMD Turion 64 Mobile MK-36
nVidia GeForce Go 6150
nForce 410 Motherboard
Broadcom Dell (lol) Wireless 1390 MiniPCI WLAN
Ricoh Media Card Reader

Seems to be almost exactly the same hardware, and I shouldn't have to deal with those pesky webcam drivers ;D

I'll give it a go and see how things turn out, and post my results here (I'm surprised I haven't found any threads on the Presarios, this laptop was a real steal at $650 ^_~).

As far as I know, no one has tried it on a Presario...Please try it out as it appears that it will relate closely to the AMD based dvxxxx laptops. Please let us know your results! Anything you have change wise, please let me know and I will update the tutorial when I can.

---

### Post by Darkangel14615 on 2007-08-28
Well, gave it a go last night, I've not quite tested everything yet but here's my status as of now:

-Ubuntu 7.04 Feisty 32Bit Installed Successfully
-Boot using noapic and nolapic (just noapic works as well)
-nVidia GeForce Go 6150 Working Using restricted driver (this way it won't break after kernel upgrade)
-Sound works OOB using ALSA
-Mic Works OOB (have to un-mute as mentioned)
-Wireless works using ndiswrapper (from installer on the link provided) and Wicd
-USB *unsure* external 320GB Seagate FreeAgent drive isn't detected/mounted like it did in Fedora, may have to check different boot options, haven't tested any other devices on USB
-Suspend/Resume not working (haven't added nosmp to boot options yet, will try that later)
-Hibernate Not tested (I probably won't bother, I never liked hibernate =p)
-Media Card Reader not tested, but I'm gonna guess it works, I'll check it out and update this as well

Well so far I've been able to do one thing I never could - Get Wireless working! I'm chalking this one up as a success. Finally a working Linux partition!

I'd say you can add Presario V6000 series to your guide as well, so other people that picked up this model can find it and enjoy Linux success with Ubuntu.

(I also love that Ubuntu has built in NTFS support and Finds/Mounts my NTFS partition so I can access my music/movies =D)

---

### Post by EXCiD3 on 2007-08-28
Hey thanks Darkangel14615, I'll be sure to update it when I get the chance. I'm working on my own webpage, where I'm also going to host this tutorial.

**NOTE: **I am currently in development of a script that will detect laptop hardware and setup the drivers, laptop mode, etc itself. Unfortunately, with the vast majority of configurations I will have to limit it a bit. I will update you guys if I do get a script working, but due to the Gutsy release coming up here in October I may wait to release it.

PLUS! I have read that Broadcom cards will be supported in the Restricted Drivers Manager!!!! But don't believe me 100% as this is no guarantee. I saw it on a link from [Digg]("http://www.digg.com/")

---

### Post by Darkangel14615 on 2007-08-28
An install script would be excellent, since writing out commands can be a pretty daunting task, and there are many people who want to install Ubuntu and may not know very well what hardware they have or what commands to run.

---

### Post by siralphred on 2007-08-29
thanks EXCiD3, but i just went back to using trevinos repos, that has all the plugins, and your script would be awesome, i would suggest you do a general script for the hp and then attach guidelines on how each user could modify it to suit their hp dv series because the variations can be very vast and i doubt one script can handle all of them

---

### Post by EXCiD3 on 2007-08-29
Yeah, I plan on writing the script for any laptop, containing the supported hardware. Once the hardware is detected it will install the drivers, allowing it to install drivers for any laptop containing that hardware. I think I will wait until Gutsy is released before I write anything. I will probably start writing a general script, easily modifiable for later use. Thanks, any ideas, etc, message me or post back here!

---

### Post by vivalant on 2007-08-29
Some of the webcams in the  dv6000 series are supported by the SN9CXXX driver at [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by EXCiD3 on 2007-08-29
In order for me to start coding this project, would people please post their system specs, and include the outputs of both lspci and lsusb? Please state your model number and any other info you may think relevant. I will gather this, figure out which hardware the first version will support and then will go from there.

My goal will be that you download this script directly after a fresh install, update Ubuntu to the newest packages, then run this script to have your drivers installed. Any help would be greatly appreciated and will help newer Linux users to be more at ease with their transition from Windows.

---

### Post by adrman on 2007-08-29
Another stupid newbie question.  How does one go about generating the output of lspci and lsusb?  Thanks.

---

### Post by EXCiD3 on 2007-08-29
Open a terminal and type the commands. Copy the output and post it here. Sorry if i didnt make that clear for you. I'm just used to running commands now. I started using linux about 2 months ago, so I'm pretty new still too.

**NOTE:** If anyone finds information on other threads pertaining to these laptops, such as job tty control turned off, suspend/hibernate, whatever, please post info here and I will read through it. I'm hoping to greatly help out any HP/Compaq laptops users. I am going to start my own website also, where I will have links and other information pertaining to these laptops. I'll post a link for you guys once i get it up. I'm pretty busy with school at the moment so it might be a bit. But I'm always AIM, MSN, Gtalk, and Yahoo so just drop me a message, I'd be glad to help/chat whatever.

---

### Post by siralphred on 2007-08-29
from the poll i think dv9000 and dv6000 are in the majority,  but again there are various specs for these two so i dont know, also it would be helpful if people will give the detail model number (usually found under the laptop). I will start off with my detailed specs,  everything worked out of box using  "noapic nolapic"  except wireless and webcam, wireless was very easy using the bmartin script, the real problem was with the Microdia built in webcam.

HP Pavilion dv6000
Model: 6258se  Special Edition :)
Graphic card: Nvidia Go 1650
Processor: AMD Turion Dual Core Mobile Technology
webcam: Microdia
Media Reader: Ricoh
Wireless card: Broadcom



$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)



~$ lsusb
alphred@zzyzyx:~$ lsusb
Bus 002 Device 002: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by EXCiD3 on 2007-08-29
So far I have the dv9000t, and dv6000 outputs. If someone will post the dv9000z (AMD version), dv6500, dv9500, and dv2000 outputs that would be great!

---

### Post by dawg on 2007-08-29
ive got the 6500 special edition
heres the specs on it
Intel(R) Core(TM) 2 Duo processor T7300 (2.00 GHz, 4 MB L2 Cache, 800MHz FSB)
15.4" WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
2GB DDR2 (2 Dimm)
383MB NVIDIA GeForce 8400M GS
HP Imprint (Influx) + Fingerprint Reader + Webcam + Microphone
Intel(R) PRO/Wireless 4965AGN Network Connection and Bluetooth(TM)
160GB 5400RPM
 LightScribe SuperMulti 8X DVD+/-RW with Double Layer Support
```
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1)
02:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

and 

```
Bus 007 Device 005: ID 04f2:b015 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0461:4d2e Primax Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
```

---

### Post by EXCiD3 on 2007-08-29
Okay, thanks. By the way, is it an Intel based laptop?

---

### Post by solongfx on 2007-08-30
I've stumbled on a problem.. 

I have the Ricoh 5-in-1 card reader (R5C822), and when I first followed this guide it was working out of the box with my SD card. 

Now .. it's stopped recognising my SD card.. I don't think it's a problem with the card, or the reader, because I can read/write to the card in Vista and also on the card reader we have on our all-in-one printer thing. I'm wondering if there is something I can do to get the reader working again, or install the drivers again? I can't seem to find them anywhere...

thanks in advance.

---

### Post by EXCiD3 on 2007-08-30
What drivers did you install? It should still work because you havent messed with it. I personally don't have much experience with the media reader as i have no cards to use in it. Can you detail what steps you took exactly?

---

### Post by solongfx on 2007-08-30
that's the problem, I didn't do anything that should have messed it up, it just stopped working. I've got an external card reader and that reads the card in ubuntu fine, but this integrated one just wont play ball.

the only things i've really done since installing ubuntu and following this guide are tweaks to try and get it to run faster following some of the other guides around here, oh and compiz-fusion etc...

---

### Post by EXCiD3 on 2007-08-30
Hmmm...thats odd. Do you know if there is a file in /dev for it? You could try a reinstall and see if you can figure out what disabled it. But to tell you the truth, I'm not quite sure what would be doing it.

---

### Post by siralphred on 2007-08-30
I had a similar problem a few weeks back....sometimes when i put in my sd card it will load two sd icons on my desktop and sometimes it wont load at all .... usually when i boot into vista and back into ubuntu it works fine....that might not be the right solutions but it works for me

---

### Post by EXCiD3 on 2007-08-30
Hmmm....thats kind of wierd. Does anyone know about this problem with Gutsy?

---

### Post by AlokaParyetra on 2007-08-30
I'm having trouble getting all of Feisty to work properly on my brand new dv9500t laptop.

Some basic specs:
Processor: Intel Core 2 Duo
Graphics Card: nVidia 8600M GS
Chipset: Intel 82801H (ICH8 )
Sound: Intel (Integrated) HD Audio Controller (ICH8 )
Cdrom: LightScribe SuperMulti 8X DVD+/-RW

Ok, now for my problems:

1) Sound does not work.
I've messed with ALSA, turned everything up, unmuted everything and all that, but it still does not work. I searched on the net, and all i could find was a patch of some sort for ALSA, but i had no idea how to apply it.

2) Does not recognize cdrom drive.
I put in a CD, does not load it. I go to places/computer/cdrom, but it says it cannot mount it. I checked the /dev folder, and much to my surprise, there were no files indicating a cdrom drive; no scd0, no cd0, none of that.

3) Every once in a while, things run slow.
I got a really nice processor and stuff, so this is disappointing. Most of the time, it runs fine, but things like compiz-fusion and avant-window-manager run with a lag now and then.

Please help. If there is any way i can provide more of my system's info, let me know so i can post it. I am also a relative newbie. While i know how to use a terminal, i only got ubuntu a month ago (on an older desktop. Everything worked perfectly on that, which is why it hurts to see it not work as well on my newer laptop), so please dumb things down for me.

---

### Post by Darkangel14615 on 2007-08-30
here're my lspci and lsusb outputs

Specs again:

Compaq Presario V6210US (RP203UA#ABA)

AMD Turion64 Mobile Technology MK-36 2.0GHz 1066MHz FSB
nVidia nForce 410 Motherboard
1024MB DDR2 RAM
80GB 5400RPM SATA II HDD
Broadcom Dell 1390 WLAN MiniPCI Card
15.4" WXGA HD Brightview Widescreen LCD Display (1280x800)
288MB nVidia GeForce Go 6150 (64MB on-board)
Dual-Layer DVD±R/RW
Ricoh SD/MMC/MS/MSPro/XD Media Card Reader

lspci
```
anthony@FASterBOX:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

lsusb
```
anthony@FASterBOX:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

---

### Post by AlokaParyetra on 2007-08-31
I got my sound to work following instructions from here:
[http://ubuntuforums.org/showthread.php?p=3212750](http://ubuntuforums.org/showthread.php?p=3212750)

If anyone can help me with the other problems, i'd much appreciate it.

---

### Post by EXCiD3 on 2007-08-31
I'm not exactly sure what is wrong with your CD-Rom drive. My friend recently installed Ubuntu on his Acer laptop and got the same problem. It appears that Ubuntu is not detecting you CD drive for some reason. What drive did you purchase? (dvd-rw, lightscribe, hddvd) I'll talk to my friend and see what he ended up doing.

As for your system lagging, I have had the exact same problem. It is not due to Compiz-Fusion, but I think that is has to do with Avant and/or Kiba-dock. I was using Kiba-dock and noticed my system lagging like crazy. After disabling it, and switching to Avant it helped but still was quite laggy. I have since stopped using Avant and Kiba-dock, but I haven't had time to look into the problem. Since there is a three day weekend I will research some of these things and hopefully gather some more info. As for now, I suggest searching the forums and/or google.

---

### Post by siralphred on 2007-08-31
hey EXCID3 its me again :) in the thread you said the remote control worked out of box, but mine doesnt seem to work. Also how do i configure the QuickPlay (blue multimedia buttons on above the keyboard)?  For now only the volume button works i would like to associate them with vlc so that when i hit "dvd" button it will automatically launch vlc  thanks

---

### Post by EXCiD3 on 2007-09-01
siralphred, I'm sorry for not stating that the keys may not be mapped. When I said that the remote works, only a few of the buttons are mapped properly. In order to set up your buttons, you will need to use xbindkeys. To install this, Open a terminal and run these commands:
```
sudo apt-get install xbindkeys
sudo apt-get install xbindkeys-config
```To run xbindkeys just press Alt-F2 and run xbindkeys or run it in terminal. For a graphical configuration tool run xbindkeys-config the same way.

More information can be found about xbindkeys at their website: [http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)
Note the utilities section at the bottom of the page as some of those may be quite helpful.

**NOTE: **If your custom command requires using sudo, replace sudo with gksu as this will give you a graphical password input that will be more appropriate than entering your root password in the command line. For example, this is what is used when you start Synaptic Package Manager and are asked to enter the root password.

Once I get the time for trying this out, I will write a good configuration section for the Howto. Since this is a common problem, I will be updating the Howto with this relatively soon. I will try to update the tutorial this weekend if time permits. Please let us know how it turns out for you! ;)

---

### Post by fulio on 2007-09-01
Hi, awhile back everything went great with the installation. and the only problem i been having since i had ubuntu 7.04 is with my desktop effects.
i have installed the lastest drivers and tryd using envy. and when it reboots and boots i get failed to start x server, i would have to reconfigure it and run vesa again.

my laptop is a hp pavilion dv6000 AMD Turion64 Graphics nvidia. Please help its been so long. i tryd to get help. and this could be it.

if anyone else have a hp pavilion dv 6000 can you help me out and can you also post your output on the /etc/X11/xorg.conf please.

---

### Post by Felpuppy on 2007-09-01
Thanks for the info... I am a Linux noob, but well ready to climb out of the M$ box...This will be extremely helpful.:)

---

### Post by Darkangel14615 on 2007-09-02
I would like to report that the SD card reader and USB do indeed work. Though it seems my external HDD has to be plugged in on boot to be recognized/automounted.

Also, I don't seem to be able to get sleep to work. I set the nosmp boot option and POST_VIDEO to False. It goes to sleep but when I wake it up I get green text on a red background, then it acts like it's going to come back up and all I get is black screen+Cursor and nothing else. Could it be Compiz Fusion? Is there a sync to v-blank option? 'Cause I didn't see one anywhere. Sleep's the only thing left, then I'll probably use Ubuntu more than WinXP ;D

---

### Post by siralphred on 2007-09-02
thanks for the help EXCID3 will do that and if any issue arise i will report them

---

### Post by EXCiD3 on 2007-09-02
> **Darkangel14615 said:**
> I would like to report that the SD card reader and USB do indeed work. Though it seems my external HDD has to be plugged in on boot to be recognized/automounted.

Also, I don't seem to be able to get sleep to work. I set the nosmp boot option and POST_VIDEO to False. It goes to sleep but when I wake it up I get green text on a red background, then it acts like it's going to come back up and all I get is black screen+Cursor and nothing else. Could it be Compiz Fusion? Is there a sync to v-blank option? 'Cause I didn't see one anywhere. Sleep's the only thing left, then I'll probably use Ubuntu more than WinXP ;D

Sleep and Hibernate still are very picky when it comes to Feisty. Unfortunately the Nvidia driver causes problems with this and we still arent quite sure what is wrong. The other day I tried using the nosmp option again, but it prevented Feisty from booting. I think that VBlank is the same as VSync which Compiz Fusion might have instead. I'm not quite sure about compatibility with Compiz Fusion as it is still in early development stages. I'm doing a fresh install of Ubuntu at the moment and will try out Compiz Fusion and see what happens.

**Script Update:** I have started coding a script to do some of this installation for you. I will try to incorporate as much of the tutorial as possible. I'm working on getting a website up and running where I will hosts the script and the tutorials and some other information regarding Ubuntu on laptops. I am still leaning towards releasing the script shortly after Gutsy is released as there should be alot of these problems fixed *hopefully*.

If you have any ideas for the script please let me know. I would love to have an all in one script that would install and configure laptop hardware not only for the HP/Compaq laptops but for various other brands. Please keep posting your laptop specifications and lspci outputs as this will help determine which hardware I should I support first in the script.

---

### Post by Darkangel14615 on 2007-09-02
Hoho! I missed the "General Options" button in Compiz Fusion. Disabled Sync to V-Blank, and tada! Sleep works great!

Ubuntu Feisty now 100% functional on Compaq V6210US

Woulda taken forever without your guide, thanks a lot! *Runs off to play with Ubuntu*

---

### Post by EXCiD3 on 2007-09-02
> **Darkangel14615 said:**
> Hoho! I missed the "General Options" button in Compiz Fusion. Disabled Sync to V-Blank, and tada! Sleep works great!

Ubuntu Feisty now 100% functional on Compaq V6210US

Woulda taken forever without your guide, thanks a lot! *Runs off to play with Ubuntu*

Glad to know it helps! I just got Compiz Fusion installed but unfortunately there is a new episode of Diggnation out and I **have** to go watch that now. ;) I'll test it out on mine once again and I am going to update my tutorial tonight, but I probably wont be able to upload it right away....

---

### Post by lowracer on 2007-09-02
Hi, I have a new 17" widescreen HP Pavilion laptop, DV9410US, that I have attempted to install Ubuntu Feisty on.  Since this is an AMD CPU with Nvidia graphics and Broadcom wireless, I am obviously one who loves a challenge.   

The install went well, I used the alternate CD based on the recommendation of the first post in this thread (after confirming the LiveCD wouldn't work, which it didn't).  However, upon reboot after install, and after the Ubuntu splash screen and progress bar finishes, the screen appears to melt.  There's no better way to describe it.  It gets a strange pattern on it that appears splotchy and fluid, almost biological, or something out of a Pollock painting, and the intensity varies and fades, eventually fading to black.  I never dropped acid in my younger days, but this is what I imagine a bad acid trip would look like.

Anyway, I suspect I need to tweak the Nvidia driver.  Problem is, CTRL-ALT-F1 through F6 have no effect.  The acid-melt screen stays unchanged.  Tried rebooting, same problem.  Tried completely reinstalling the OS again, same problem.

I need to get to a command line so I can try tweaking the nvidia drivers.  I don't know how to boot into a command line if CTRL-ALT-F1 is not working.  Any ideas?  For my next trick I'm going to try to install a text-only install, but not sure what to do from there.

Thanks,
-Mark
aka lowracer

edit to add: downloaded and burned the kubuntu 64-bit alternate CD, and it seems to be working graphically so far.

---

### Post by Inxsible on 2007-09-03
This is my lsusb
```
Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000 
```Can someone tell me what device the Hewlett Packard line points to? I have no other devices connected except for a mouse. 

also, I installed the deb file pointed to by siralphred a few pages back. How do I select V4L2 drivers in Kopete or aMSN ?

---

### Post by EXCiD3 on 2007-09-03
> **lowracer said:**
> Hi, I have a new 17" widescreen HP Pavilion laptop, DV9410US, that I have attempted to install Ubuntu Feisty on.  Since this is an AMD CPU with Nvidia graphics and Broadcom wireless, I am obviously one who loves a challenge.   

The install went well, I used the alternate CD based on the recommendation of the first post in this thread (after confirming the LiveCD wouldn't work, which it didn't).  However, upon reboot after install, and after the Ubuntu splash screen and progress bar finishes, the screen appears to melt.  There's no better way to describe it.  It gets a strange pattern on it that appears splotchy and fluid, almost biological, or something out of a Pollock painting, and the intensity varies and fades, eventually fading to black.  I never dropped acid in my younger days, but this is what I imagine a bad acid trip would look like.

Anyway, I suspect I need to tweak the Nvidia driver.  Problem is, CTRL-ALT-F1 through F6 have no effect.  The acid-melt screen stays unchanged.  Tried rebooting, same problem.  Tried completely reinstalling the OS again, same problem.

I need to get to a command line so I can try tweaking the nvidia drivers.  I don't know how to boot into a command line if CTRL-ALT-F1 is not working.  Any ideas?  For my next trick I'm going to try to install a text-only install, but not sure what to do from there.

Thanks,
-Mark
aka lowracer

edit to add: downloaded and burned the kubuntu 64-bit alternate CD, and it seems to be working graphically so far.

I have no idea why the screen is doing that. I have experienced that same screen melting when I suspend/hibernate. However I havent heard of anyone getting that problem upon boot up. Did you install the Nvidia driver using Envy?

> **Inxsible said:**
> This is my lsusb
```
Bus 005 Device 003: ID 0c45:62c0 Microdia 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000 
```Can someone tell me what device the Hewlett Packard line points to? I have no other devices connected except for a mouse. 

also, I installed the deb file pointed to by siralphred a few pages back. How do I select V4L2 drivers in Kopete or aMSN ?

That's one thing i have been trying to figure out myself. The Hewlett-Packard entry must be something built into the laptop. I'm not quite sure what it would be however...

As for the V4L2 (Video 4 Linux 2) drivers here is some info I found about it:
From the kopete website: > Kopete uses the Video4Linux 2 system for video. This shows a blue square if no video device is found, or a preview if the camera is working. For up-to-date information on Kopete webcam support, see the [Kopete Webcam Support wiki page]("http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support").
and here is a little info on aMSN:> WebcamWizard is an easy way to configure and fine-tune your webcam. The WebcamWizard provides options to maximize the quality of your webcam broadcast. The WebcamWizard can be started from within a chat window by clicking 'Actions' &#8594; 'Configure Webcam'. The Configure Webcam dialog will then be shown.  You may change your video settings by clicking “Change video settings” button.

Hopefully this will work for you guys, I personally don't use either of these IM programs (Pidgin rulez!!!) so until I get back to school I wont be able to download these apps and try out the webcam...Let me know if you find anything.

---

### Post by siralphred on 2007-09-03
About the Microdia webcam, i found this page which talks extensively about it, [http://wiki.eagle-usb.org/wakka.php?wiki=WebCamSonix](http://wiki.eagle-usb.org/wakka.php?wiki=WebCamSonix) under **Infos about the uvcvideo driver** it says to "copy the uvcvideo.ko file from /lib/modules/2.6.17-6mdvcustom/usb/media/uvcvideo.ko to /lib/modules/2.6.17-6mdv/usb/media/uvcvideo.ko them depmod -ae " but that directory is not available in ubuntu or at least my ubuntu so if anyone knows where it is it could be of help thanks

---

### Post by EXCiD3 on 2007-09-03
I think it basically means to move it to your kernel's mdv folder

I would assume that you would need to move it to: /lib/modules/[SIZE=-1]2.6.20-16mdv/usb/media/uvcvideo.ko

I cant really tell you excatly what to do, but you could try finding the folder in Nautilus (File browser). I will look into whenever I get the chance, school is keeping me hellaciously busy.
[/SIZE]

---

### Post by solongfx on 2007-09-03
> **EXCiD3 said:**
> Hmmm...thats odd. Do you know if there is a file in /dev for it? You could try a reinstall and see if you can figure out what disabled it. But to tell you the truth, I'm not quite sure what would be doing it.

Ok, well the card seems to be recognised again, i'm not sure if this is what fixed it, but it seems like it's the only thing that could have fixed it..

Anyway, I was trying to install the nvidia-glx drivers rather than the nvidia-glx-new drivers in an effort to get some of compiz-fusion's effects running more smoothly (minimise/restore is extremely jerky). Anyhoo, installing the nvidia-glx drivers broke x, so I reinstalled the nvidia-glx-new drivers using envy on the command line again after manual install didn't work at all, and part of envy's install updates the kernel if i'm not mistaken? Anyway, I think that's what fixed it.. so if your SD card reader stops working, try uninstalling and reinstalling your graphics drivers using envy and it should start working again :p

---

### Post by EXCiD3 on 2007-09-03
Thanks for the info, I'll update the howto asap...which might not be real soon. School and friends have been keeping me really busy for the last 2 weeks...I'm working on getting a website up and running, anyone know of a good free webhost that could possibly run drupal? I'm looking into my2gig.com and guildhost.org atm...PM or IM me as I dont want to get off topic on this thread.

What do you think should be the first couple of drivers that my script should install? I'm thinking downloading Envy for use would be one of the first and most important drivers...Any feedback would be great!

---

### Post by Inxsible on 2007-09-03
I tried the gstreamer-properties and when I do a test, my webcam does work.

But when I go into Kopete -- >Settings --> Configure --> Devices tab, i just get a green screen.

I have attached a png to show what I mean.

Can someone help me out ? /i am not sure if this is a webcam issue or kopete issue. I tried the kopete wiki that excid3 provided but no love :(

---

### Post by rwmcgwier on 2007-09-03
You say noapic in your instructions, but I did  noacpi.  It has been about a decade since I had a problem with the Advanced Programmable Interrupt Controller.  On HP Pavilion computers,  many are sent out with buggy bios.  This means you want to use noacpi (Advanced Configuration and Power Interface).  I did the latter on my HP Pavilion 9428nr and the interrupts were much better behaved.  Thanks again for your very helpful note.

---

### Post by EXCiD3 on 2007-09-03
Hey thanks for the info, none really explained the difference and they seemed to be used interchangeably by everyone I talked to...I will go ahead and fix that.

---

### Post by kigango123 on 2007-09-04
thanks for info

---

### Post by brittai on 2007-09-04
Hi,

i have an HP dv9574 and, besides some problems (all already mentioned in this thread), the one that is concerning me the most right now is overheating (as it can damage hardware).

In my case, the cooling fans seem to never turn on on (work ok with windows vista). There are also some reports of cooling fans never turning off (which drains batery).

I've been reading many threads about this and it seems to be an open issue with multiprocessing kernels (constant cpu use) and an (aparently) broken acpi support.

Does someone have the same problem and/or a SAFE/PROVEN workaround for this?
I'm using 7.04.

Regards

---

### Post by Pilot07 on 2007-09-04
I'm hoping this will work on my dv9420ca. Has anyone else with a simmilar model installed this with success?

---

### Post by EXCiD3 on 2007-09-04
if you post your specs I can check and see

---

### Post by Pilot07 on 2007-09-05
Vista Ultimate
AMD Athlon 64 X2 Dual core processor TK-53
1GB Ram
nVidia Geforce Go 6150

---

### Post by the.unclean.cpp on 2007-09-05
Thanks so much for posting! I spent about 2 hours trying to config the X server on my DV9500 laptop before seeing this thread. The X wouldn't start at all. "No screens found" I end up using the vesa driver, but now I got the graphics driver fully accelerated.
The problem is that I have [COLOR="Red"]**no sound**[/COLOR] on the laptop. What could be the problem?
Thanks in advance.

Additional details: My sound card is from Realtek and it's HD.

---

### Post by EXCiD3 on 2007-09-05
> **Pilot07 said:**
> Vista Ultimate
AMD Athlon 64 X2 Dual core processor TK-53
1GB Ram
nVidia Geforce Go 6150

Ok looks like it should work just fine. You will have a much harder time installing than I did as much of my hardware (wireless most notably) works out of the box. Just follow the instructions and links and it should work just fine.

---

### Post by EXCiD3 on 2007-09-05
> **the.unclean.cpp said:**
> Thanks so much for posting! I spent about 2 hours trying to config the X server on my DV9500 laptop before seeing this thread. The X wouldn't start at all. "No screens found" I end up using the vesa driver, but now I got the graphics driver fully accelerated.
The problem is that I have [COLOR=Red]**no sound**[/COLOR] on the laptop. What could be the problem?
Thanks in advance.

Additional details: My sound card is from Realtek and it's HD.


I'm not quite sure what is wrong with your sound, this has been reported various times along with reports of very low sound volume. You should definitely check out this thread: [http://ubuntuforums.org/showthread.php?t=205449&highlight=complete+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=complete+sound)

---

### Post by the.unclean.cpp on 2007-09-05
Thanks for the info, the instructions are comprehensive. I'll let you know if they worked.

---

### Post by EXCiD3 on 2007-09-05
> **the.unclean.cpp said:**
> Thanks for the info, the instructions are comprehensive. I'll let you know if they worked.

Yeah, I have looked into that thread myself...and frankly was a little bit overwhelemed. If you get something working please let me know, I'm going to add it to the Howto when I get the chance.

---

### Post by kalium on 2007-09-05
[SIZE="6"]HP Pavilion dv9500 series[/SIZE]

**[SIZE="4"]Working out of the box[/SIZE]**

[LIST]
[*]Processor: 2x Intel® Core™ 2 Duo T7300 @ 2 GHz , 4 MB cache lv2 **Works out of the box**.
[*]Motherboard: Intel Crestline GL960/GM965/PM965 **Works out of the box**.
[*]Graphics Card: nVidia GeForce 8400M GS (128 MB) **Works out of the box**.
[*]RAM Memory: 2x Qimonda DDR2-667MHz SDRAM 1GB **Works out of the box**.
[*]Hard Drive: 2x Toshiba MK1237GSX ATA 120GB **Works out of the box**.
[*]Optic Unit: HL-DT-ST DVDRAM GSA-T20L ATA w/ Lightscribe **Works out of the box**.
[*]LAN Adapter: Realtek RTL8168/8111 (NDIS 6.0) **Works out of the box**.
[*]Firewire Controller: Ricoh RL5C832 **Works out of the box**.
[*]SD·MS/Pro·MMC·XD Card Reader: Ricoh RL5C/822/592/843/852 **Works out of the box**.
[*]Touchpad: Synaptics PS/2 Port TouchPad **Works out of the box**.
[/LIST]

**[SIZE="4"]Also supported (but configuration needed)[/SIZE]**

[LIST]
[*]Wireless adapter: Intel 3945ABG PRO/Wireless
```
apt-get install firmware-iwlwifi
```
[/LIST]

[LIST]
[*]HP Webcam
```

apt-get install linux-uvc-tools libpt-plugins-v4l2 linux-uvc-source
module-assistant a-i linux-uvc

```
[/LIST]

[LIST]
[*]Sound Card: Realtek ALC268 @ Intel 82801HBM ICH8M
```

# apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf

$ hg clone http://hg.alsa-project.org/alsa-driver alsa-driver
$ hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel

$ CD alsa-driver
$ ./hgcompile

# make install-modules

```
[/LIST]

[LIST]
[*]Fingerprint Reader: AunthenTec Inc. AES2501A
```
apt-get install aes2501-wy
```
[/LIST]

[SIZE="4"]ISSUES LEFT:[/SIZE] _HELP NEEDED HERE_

[LIST]
[*]Multimedia Keys (both F's and Touch sensible)
[*]Set brightness and contrast permanently
[*]Motorola SM56 Modem
[*]Fully configure HP Remote Control
[*]Camera is not working in Kopete or aMSN
[/LIST]

[SIZE="3"]Update on ISSUES LEFT:[/SIZE] _HELP NEEDED HERE_

This are the keycodes for touch sensible multimedia buttons:

```
Quickplay: 205
DVD: 237
Back: 144
Play/Pause: 162
Forward: 153
Stop: 164
Mute/Unmute: 160
Increase Volume: 174
Decrease Volume: 176
```

---

### Post by EXCiD3 on 2007-09-05
hey thanks for the info, im getting ready to rewrite the entire howto over again and add the awesome amount of info you guys gave me!

---

### Post by Veinor on 2007-09-05
I have Feisty on my dv9235nr, and it works. However, after I installed the restricted nvidia drivers and beryl 0.2, the computer occasionally freezes. Not even ctrl-alt-sysrq-b causes it to reboot, so I have to hold down the power switch. I haven't tried it without the drivers and without beryl; does anybody here know of similar problems? I'm up to date on everything.

---

### Post by EXCiD3 on 2007-09-05
It could be that beryl is still in very early development and something is not configured correctly. I would use Envy to reinstall the drivers so that you have the most up-to-date drivers. This might fix your problem.

---

### Post by Veinor on 2007-09-05
> **EXCiD3 said:**
> It could be that beryl is still in very early development and something is not configured correctly. I would use Envy to reinstall the drivers so that you have the most up-to-date drivers. This might fix your problem.

I tried this with Envy on my old Edgy system; same thing happened. I'll try it with beryl just plain disabled.

---

### Post by EXCiD3 on 2007-09-05
I'm not quite sure what the problem would be, but disabling beryl would help determine the problem. You shouldnt be getting any problems with the graphics drivers...but you never know, something could be messed up.

---

### Post by the.unclean.cpp on 2007-09-06
> **EXCiD3 said:**
> Yeah, I have looked into that thread myself...and frankly was a little bit overwhelemed. If you get something working please let me know, I'm going to add it to the Howto when I get the chance.

Unfortunately, I didn't manage to get anything working. My DV9500 it's still soundless. I'm looking forward for the solution and if I'll find it somewhere else than this forum I'm gonna post it here also.

---

### Post by kalium on 2007-09-06
> **the.unclean.cpp said:**
> Unfortunately, I didn't manage to get anything working. My DV9500 it's still soundless. I'm looking forward for the solution and if I'll find it somewhere else than this forum I'm gonna post it here also.

I've already posted it:

```

# apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf

$ hg clone http://hg.alsa-project.org/alsa-driver alsa-driver
$ hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel

$ CD alsa-driver
$ ./hgcompile

# make install-modules

```

Where # means root command and % user command (don't copy this symbols).

---

### Post by niC666 on 2007-09-06
Hi

apologies for cross posting.. originally posted to the wrong thread...

I have a dv9521ei which i am trying to install feisty on with no luck
I've tried just about all the switches at the kernel boot phase, but still get dumped into a busybox shell.

its an intel core II duo T7200 2GHz based system.

if i turn off quiet and splash in the boot options the last messages i see before the busybox shell are

kjournald starting. commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode

repeated over and over again..

any advice?
I am busy downloading the alternate cd image in case but its gonna take a while on my connection

thanks
niC

---

### Post by Inxsible on 2007-09-06
Has anyone been able to get their webcam working in aMSN or Kopete  or any other messaging service.

I am even willing to try other IMs if the webcam works !!!

---

### Post by solongfx on 2007-09-06
It might be worth adding a couple of things to the next how-to

If your screen resolution isn't set automatically by envy on reboot you'll need to edit it yourself

```
sudo gedit /etc/X11/xorg.conf
```
All of these laptops are 1440x900 I believe, so add "1440x900" next to the other options under the 24 colour depth section.
(pretty basic, but maybe not for a newbie)

Also, in the graphics card driver section, add
```
    Option      "NoLogo"   "true"
```
in order to remove the nvidia splash when X starts.

---

### Post by lowracer on 2007-09-06
I have an HP dv9410us, it is locking up. This is one of the the AMD / Broadcom wifi / Nvidia machines.  Sometimes it will run overnight, sometimes for just a few hours, but ultimately it freezes.  I'm running Feisty 7.04.  We have the clock set to display seconds, and when the seconds no longer update, we know we have a freeze.  The mouse pointer doesn't move, and ctrl-alt-F1 does not switch to a text console.  I suspect the kernel has died at this point.

What I want to know, and pardon me if this is "Linux 101," but is there a log file that might give a clue as to what's happening to cause the lockup?  Or has anyone else encountered such lockup and what did you do about it?  I boot with "noapic irqpoll noirqdebug" as recommended, and have gotten the broadcom wireless working by using ndiswrapper and wicd.  

Thanks...
-Mark

edit to add, i just noticed that the boot parameters in the howto have changed from noapic to noapci...  I've made the change and will see if that helps with the lock ups.

---

### Post by Ayuthia on 2007-09-06
> **lowracer said:**
> I have an HP dv9410us, it is locking up. This is one of the the AMD / Broadcom wifi / Nvidia machines.  Sometimes it will run overnight, sometimes for just a few hours, but ultimately it freezes.  I'm running Feisty 7.04.  We have the clock set to display seconds, and when the seconds no longer update, we know we have a freeze.  The mouse pointer doesn't move, and ctrl-alt-F1 does not switch to a text console.  I suspect the kernel has died at this point.

What I want to know, and pardon me if this is "Linux 101," but is there a log file that might give a clue as to what's happening to cause the lockup?  Or has anyone else encountered such lockup and what did you do about it?  I boot with "noapic irqpoll noirqdebug" as recommended, and have gotten the broadcom wireless working by using ndiswrapper and wicd.  

Thanks...
-Mark

edit to add, i just noticed that the boot parameters in the howto have changed from noapic to noapci...  I've made the change and will see if that helps with the lock ups.

I have a dv6000 with a similar setup and I am booting with noapic noirqdebug and it has been pretty stable on gutsy.  When using feisty, I was using noapic nolapic, but over time my USB ports would be disabled.  You can look in /var/log for various system messages, but I have found dmesg useful in finding out if the kernel decided to go for a walk.

---

### Post by EXCiD3 on 2007-09-06
By any chance are you running Beryl or Compiz? I have had lockups such as those when I am using Compositing Window Managers

---

### Post by solongfx on 2007-09-06
I've had these lockups too, AMD, NVidia, Broadcom, Compiz-fusion.
it's annoying, because you have to do a hard reboot, which doesn't unmount the partition properly, which for me, gives it errors every time and I have to go to recovery mode, run fsck to fix everything, then reboot, and hope it boots without errors. sometimes it doesn't and I have to do this 3 or 4 times..

---

### Post by lowracer on 2007-09-06
Thanks for the responses.  Changing the boot parameters did not fix the problem, I came back home from work today to find the laptop locked up tighter than a drum.  

I've looked at dmesg after the crash, but since I'm always looking at it after a fresh reboot (i have to cycle power to get the machine to reboot), it seems to only have boot messages in there, and I can't find any clues leading up to the crash.

FWIW I'm running a plain-vanilla Gnome, out of the box Ubuntu alternate 32 bit install, no fancy compiz or beryl.

You got Gutsy working eh?  Maybe I'll give that a shot.   This is my wife's laptop, replacement for her iBook G4.  So far she's been patient with it.  Not sure how long that will last...

---

### Post by EXCiD3 on 2007-09-06
Hopefully gutsy will solve some of these problems and FYI Gutsy Tribe 6 is supposedly being released sometime later today! I'm still waiting for the link to go up on digg... ;)

---

### Post by lowracer on 2007-09-06
I did some googling and discovered /var/log/kern,log.  In there I discovered some spurious interrupts with IRQ7 and IRQ15.  I have added nolapic to my boot parameters in grub to see if that will help stop the freezes.

---

### Post by EXCiD3 on 2007-09-06
Ok let me know if that helps any... I unfortunately am currently running VIsta only (i know...dont hate me) I'm trying to get my stuff done for school and am waiting patiently for the Tribe 6 release...even though I will probably just use Feisty until its official...

It feels wierd not having Ubuntu!

---

### Post by the.unclean.cpp on 2007-09-07
Yet another configuration problem on Ubuntu with DV9500. As you well know, this model comes with Sata HDDs. I have 2 of them. Each has 160 GB and 7200 RPMs. Anyway, the problem is that they do not automount.
I can easily mount them, that's not a problem. The problem is that I can't access them as a normal user and I need access to that drives for music, movies and other stuff.
Can this be fixed? (sorry for asking so many question, I don't have experience with Linux)

---

### Post by hondaman on 2007-09-07
I have read this thread, hoping to find an answer, but alas, I am still stuck.  I'd like to dual boot XP and ubuntu 7.04 i386 on my dv9548us, but when I try the livecd, I get dumped to a shell.  The exact bug is here: [https://bugs.launchpad.net/ubuntu/+bug/75135](https://bugs.launchpad.net/ubuntu/+bug/75135)

"BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu2) Built-in shell (ash)

Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off

(initramfs)"

I have tried all the boot switches, and its still a no-go.

Any help would be awesome.  Thanks!

---

### Post by niC666 on 2007-09-07
hondaman,

i had the same problem, 

you can try modprobe piix then exit when in the busybox shell.. if that works you will need to do some other stuff to get the module in permanently.. check out [http://ubuntuforums.org/showthread.php?p=3324442](http://ubuntuforums.org/showthread.php?p=3324442)

i didnt do that, i just got an ubuntu alternate install disc and installed with that which worked with no problems.

hth
nic

---

### Post by EXCiD3 on 2007-09-07
I've been meaning to post the fix for that in the howto but have had very little time since classes have started. I'm planning and completely rewriting the tutorial as there are several things that need to be updated.

In any case, if this doesn't help you, searching the forums surely will find you something.

---

### Post by niceguy123 on 2007-09-07
> **ryandle said:**
> Hey all,

I stumbled upon this thread while desperately searching for a fix for my hp dv9420us (AMD processor, i dont know if that makes a difference).  Im actualy trying to install Kubuntu, does anyone know what steps need to be taken with KDE?  Ive tried noapic and nolapic and it boots into kubuntu now but the system locks up within 5 minutes (mouse still moves around but no windows / menus respond)



im very frustrated, i read great reviews about this laptop but i never thought it wouldnt be linux friendly!


I've got the same type of problem on a Compaq Presario M2000, It freezes after I see the first Ubuntu screen and the opening melody.  it has Windows XP home edition preinstalled,but I would like to move over to Ubuntu.

---

### Post by lowracer on 2007-09-07
noapic and nolapic boot parameters set,  but the dv9410us still locks up.  Still looking for clues.  The last entry in the kern.log was 2 hours before the lockup and did not report any trouble.

---

### Post by Inxsible on 2007-09-07
> **the.unclean.cpp said:**
> Yet another configuration problem on Ubuntu with DV9500. As you well know, this model comes with Sata HDDs. I have 2 of them. Each has 160 GB and 7200 RPMs. Anyway, the problem is that they do not automount.
I can easily mount them, that's not a problem. The problem is that I can't access them as a normal user and I need access to that drives for music, movies and other stuff.
Can this be fixed? (sorry for asking so many question, I don't have experience with Linux)

you need to add the 'auto' option for the drives in the fstab. post your fstab, maybe someone might be able to help you.

---

### Post by the.unclean.cpp on 2007-09-07
My fstab is
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=071098f2-f583-4150-9f54-bfb133c68fd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a10485fc-aef0-4e5c-b2c2-c2cced06523c none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

My Vista partition is sda1 and my other HDD is sdb1. I'm not sure how do I add the 'auto' option. Help is welcome.

---

### Post by hondaman on 2007-09-07
K, thanks for the help on the modprobe piix, that got me to the desktop.  However I'm stuck again.

One thing to note first however, if you allow it to dump you to a prompt, the modprobe piix wont work.  You HAVE to put the break=top in.

So back to my problem now:  the desktop is too big for my screen.  I cant see the bottom dialog, so its impossible for me to navigate through the installer.  The resolution says its 800x600 (im booted in safe graphics mode)

Second, if I want to keep my XP install intact, and only want to install on the second hdd, is there some special trickery I should do to make sure I can boot to both OSSs?  Where should I install the grub boot loader without messing up windows?

Thanks again for this guide!

---

### Post by hondaman on 2007-09-07
> **the.unclean.cpp said:**
> My fstab is
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=071098f2-f583-4150-9f54-bfb133c68fd6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a10485fc-aef0-4e5c-b2c2-c2cced06523c none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

My Vista partition is sda1 and my other HDD is sdb1. I'm not sure how do I add the 'auto' option. Help is welcome.

Change "ext3" on this line: 

UUID=071098f2-f583-4150-9f54-bfb133c68fd6 /               ext3    defaults,errors=remount-ro 0       1

to "auto"

so it would read:

UUID=071098f2-f583-4150-9f54-bfb133c68fd6 /               auto    defaults,errors=remount-ro 0       1

---

### Post by the.unclean.cpp on 2007-09-07
But my sdb1 drive is not listed here.

---

### Post by hondaman on 2007-09-07
> **hondaman said:**
> K, thanks for the help on the modprobe piix, that got me to the desktop.  However I'm stuck again.

One thing to note first however, if you allow it to dump you to a prompt, the modprobe piix wont work.  You HAVE to put the break=top in.

So back to my problem now:  the desktop is too big for my screen.  I cant see the bottom dialog, so its impossible for me to navigate through the installer.  The resolution says its 800x600 (im booted in safe graphics mode)

Second, if I want to keep my XP install intact, and only want to install on the second hdd, is there some special trickery I should do to make sure I can boot to both OSSs?  Where should I install the grub boot loader without messing up windows?

Thanks again for this guide!

Answered my questions.

a)  If the screen is too big on the livecd, right click on the top and bottom bars, and "autohide"  Then you can see the installer screens

b) ubuntu automajically sets up dual booting.

Now I have a new problem:  None of my network works.  Wired or wireless.  I didnt expect wireless to work out of the box as thats hit and miss, however, the WIRED doesnt work either?  Thats pretty poor imo.

Any ideas on this one?

---

### Post by hondaman on 2007-09-07
> **the.unclean.cpp said:**
> But my sdb1 drive is not listed here.

ah, I missred your original question.  

In fstab, add this to the bottom:

/dev/sda1     <mount point>     auto     defaults 0 0

replacing <mount point> with where youd like to mount your windows partition, ie, /home/windows or whatever

---

### Post by fredwbauer on 2007-09-07
> **lowracer said:**
> noapic and nolapic boot parameters set,  but the dv9410us still locks up.  Still looking for clues.  The last entry in the kern.log was 2 hours before the lockup and did not report any trouble.

I was trying to install Ubuntu on my dv9410us and it would keep locking up. I installed Archlinux (64bit) and it would lock up too. The problem seems to be accessing the real time clock by the program hwclock. I had tried KNOPPIX and it didn't have the same problem so I copied the kernel config from that and compiled a new kernel for Arch using the 2.6.19 version that worked for KNOPPIX. I've had it running for a while now and it seems to work.

The quickest and dirtiest fix I can tell you is to get rid of hwclock and ntpd.
If you know how to make a custom 2.6.19 kernel for Ubuntu, I would try that.
None of the kernel command line options would save me from hwclock crashing the machine before using the KNOPPIX kernel config and version.

I'm going to try to install Ubuntu again and see how it goes. Wish me luck.

---

### Post by EXCiD3 on 2007-09-07
Hmmm, that sounds quite technical. If you figure out what is going on and find a simple set of steps to ifx this please let us know. Do you know if Gutsy has the same problems?

---

### Post by ATrentino on 2007-09-08
Following the advices given on this thread, I was able to install Ubuntu 7.04 32-bit (from the Alternate CD) on my new DV9408nr, which has an AMD Turion 64x2 and the NVidia GeForce 6150 graphic card. Everything seems to work properly, except that when I try to Hibernate it freezes quite badly, so that's my next thing to sort out. Thanks to all of you who have posted instructions!!!

ATrentino

---

### Post by the.unclean.cpp on 2007-09-08
> **hondaman said:**
> ah, I missred your original question.  

In fstab, add this to the bottom:

/dev/sda1     <mount point>     auto     defaults 0 0

replacing <mount point> with where youd like to mount your windows partition, ie, /home/windows or whatever

Ok, so now the device mounts at startup, but I still need root permission to access it. How can I change this?

---

### Post by bmxmarine on 2007-09-10
ok so i have searched and now i pose the question....has anyone secussfully installed a 64 bit version on their laptop? i have beentrying for awile now but to no avail.....

---

### Post by EXCiD3 on 2007-09-10
There should be no diffrence between installing the 64 bit version compared to the 32 bit version.

---

### Post by bmxmarine on 2007-09-10
thats what i thought but the onlyway i have been able to install ubuntu secussfully is with the alternate 32 bit version....i was wandering if maybe it had something to do with the fact that it is dual core, i know it doesn't. i was mainly wondering if anyone has done it yet. you would think that with a 64 bit system it would be nice and fast, i already love the visualations and everything compared to the shitsta operating system it came with...

---

### Post by EXCiD3 on 2007-09-10
Dont worry too much about using 64, 32 bit is plenty fast, but slightly slow for encoding, etc. Is there no 64 bit alternate cd? You may just want to wait until Gutsy is released to try 64 bit...its up to you.

---

### Post by MikeDK on 2007-09-11
by the way, has any one of you still this boot-error message "failed to allocate mem resources", on 32bit's on AMD systems??

Kind regards MikeDK

---

### Post by niC666 on 2007-09-11
I have that on a 32bit intel system, but it boots up fine anyway so i just ignore it.

---

### Post by MikeDK on 2007-09-11
ok, but what about FPS on graphics, hows that on your intel? what videocard do you have, for that matter?
My Nvidia 7600 GO geforce 256mb show not over 60fps in compiz benchmark and on glxgears.

Regards MikeDK

---

### Post by niC666 on 2007-09-11
mm do you have the latest nvidia drivers? 

I have a geforce 8600m gs 256mb and i get 4000+ fps from glxgears with desktop effects enabled (1000+ fps maximised). yours shouldnt be much lower.

---

### Post by MikeDK on 2007-09-11
i get that fps to, but i modyfied some of nvidia-settings, antialiasing etc...
running on nvidia-glx-new at the moment, but I'm about to do clean install of either feisty or gutsy tribe-5

---

### Post by EXCiD3 on 2007-09-11
I'm pretty sure that it is some setting you have configured oddly. I remeber one time I had changed a setting and Compiz started running horribly slow. I never got over 60 fps. My 7600 Go, when configured properly usually gets about 9000 fps without desktop effects, and 6000 with. I'm also running 100.14.11 drivers.

---

### Post by kalium on 2007-09-11
[LIST]
[*]How can I make permanent the Contrast and Brightness settings of nvidia-settings? The only load if I execute the program everytime I boot, and --load-config-only doesn't work for that. If not, Is there any other way to configure brightness and contrast? (I managed to configure brightness, but not contrast).

[*] How can I make suspend work? (After opening the laptop, X server doesn't show up again and I hve to hit CTRL+ALT+BACKSPACE
[/LIST]

Thank you.

---

### Post by solongfx on 2007-09-11
Just wanna say thanks again every one for all the contributions and work towards all this, it's helped me a lot.

Unfortunately I had to reinstall ubuntu the other day after I managed to get everything thrown into lost+found and just got exasperated with it all and reinstalled.. however now I can't access my second hard drive (sdb1, or at least, it should be).

It is accessible fine from Vista, but ubuntu doesn't discover it at all (it doesn't show up in /dev). Is there something I can do to get ubuntu to at least recognise that the drive exists? I tried adding it into fstab but it just says "special deivce /dev/sdb1 not found" (i tried a number of other names for it as well, but nothing). Any help greatly appreciated.

---

### Post by lowracer on 2007-09-12
Just wanted to check back in to this thread.  I have a resolution on the hp dv9410us locking up problem...  Might be of use to someone else.   I just installed the 2.6.22-11 kernel, and *poof* my troubles are gone.  Well the lockup problem seems to be gone anyway.  Ran it for over 24 hours, no freeze.  Just FYI, here is the link to the page that stepped me through the very painless kernel upgrade.  No compiling was required...  [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by EXCiD3 on 2007-09-12
Hopefully once Gutsy is released, this thread wont be of much use anymore. I hope that most of the items work out of the box once it comes out.

---

### Post by fredwbauer on 2007-09-12
> **EXCiD3 said:**
> Hmmm, that sounds quite technical. If you figure out what is going on and find a simple set of steps to ifx this please let us know. Do you know if Gutsy has the same problems?

I just now installed Gutsy AMD64 on my HP Pavilion dv9410us. I booted with the noapic option and it seems I can run hwclock all I want. I did get a "irq 7: nobody cared" message in the kernel log, tho. (Irq 7 serves ehci_hcd:usb2)

Ndiswrapper works well with the Dell Wireless 1390 Broadcom drivers.

Wired ethernet, webcam, and audio work automatically.

---

### Post by rbrewer on 2007-09-13
Try booting with "noapic irqfixup" with the gutsy kernel.  That is currently the best option for me, though still far from ideal.  My system runs very stable with that, but powertop shows 250 spurious ehci interrupts per second.

I invite anyone running gutsy who is experiencing this problem to see if they can contribute to the bug report about this.  It is definitely not fixed for gutsy yet, but by trying different things to see what works and what doesn't we are trying to understand it better with the hope of eventually getting it fixed:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89746)

---

### Post by the.unclean.cpp on 2007-09-13
Hello. I have a DV9500 laptop and the HP Webcam is incorporated in the laptop. Feisty doesn't detect it. How can I find out which device is the webcam and what drivers do I need to install to get the cam working? Thanks.

---

### Post by EXCiD3 on 2007-09-13
run lspci and lsusb... I'm pretty sure the output is located in lsusb. It should give you something like "Microdia" or the other one. Then you can follow the howto and attempt to install the drivers.

---

### Post by alqualond on 2007-09-14
Hello, and thanks for the advice, everyone. I set up Feisty on an HP6541 a couple of weeks ago, following these instructions, and they worked straight away for me. I had a few problems with the LiveCD, so I used the alternate instead, and the installation went smoothly. I've only encountered a few problems which I think are fixable or which I can ignore:

At first the CD/DVD drive wasn't recognised, but adding "all_generic_ide" (without quotes) at the "kernel" line in boot/grub/menu.lst fixed this.
I have yet to test wireless, but the card is recognised so I'm not anticipating any problems (hopefully)
Suspend works, although I think it runs a little slower after resuming, though that may just be my idea. I've tried Hibernate once, but it didn't work (it froze while hibernating, not resuming)
The screen resolution keeps getting reset to 1024x768 whenever I start the computer, and then I have to change it back to 1280x800. I've saved the changes to xorg.conf, this is the default setup (as far as I can tell), so I'm not sure what to do about this.
Finally, my biggest trouble is that sound is not working. I followed the instructions at [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
but I still don't get any sound. I'll try to experiment with this some more and get it fixed.

Other than that, everything is great. Thanks again for the instuctions and everyone's input!

EDIT: Wireless works, and I got the sound working by looking at this thread: [dv6500 Sound Problems with Feisty]("http://ubuntuforums.org/showthread.php?t=489757") (I used realtek10.tar.gz).

---

### Post by the.unclean.cpp on 2007-09-14
> **EXCiD3 said:**
> run lspci and lsusb... I'm pretty sure the output is located in lsusb. It should give you something like "Microdia" or the other one. Then you can follow the howto and attempt to install the drivers.
I found the webcam device. It's a Ricoh, but the drivers don't work.

---

### Post by Endless Bard on 2007-09-15
Yeah, I'm actually having the same webcam problem.  I've got the Ricoh model, according to lsusb, and I went and installed the uvcvideo drivers suggested (much) earlier in the thread ... they load automatically but there's no video device.  I tried Exiga and Kopete and neither shows any available video device.

(On Exiga, I change the Video Plugin to V4L2 and click "discover devices," and no device is found.)

Haven't any idea what to do from here.  Works fine under Vista, would like to be able to use it here as it's really the only thing (that I'd want to use) that I can't seem to make work.

---

### Post by quicksilver1024 on 2007-09-15
Hi, 

I just bought the DV9548 model, and chose to use the entire 2nd hard drive for the linux installation. I selected the guided installation to do this, however I can running into troubles with my graphics card (or that's what I think).

First, when I try booting the system I get a black screen.
And when I try adding the line "noapic irqpoll noirqdebug" at the end of the boot parameters, the system loads and does its thing but after a short while the screen just shuts off (I don't even just get a black screen).

Can anyone help please?

---

### Post by Farhan on 2007-09-15
excellent guide. installed feisty on my dv6383ea and almost everything was working out of the box however the ricoh 1810 webcam wasn't working, the link provided in the howto worked like charm. a bit of tuning really and things are smooth now, almost perfect.

here is link that will help with the slow boot due to network configuration. i get to boot under 30 seconds now: [http://ubuntuforums.org/showthread.php?t=452774](http://ubuntuforums.org/showthread.php?t=452774)
hope that helps other people as well.

thank you again for the guide,

---

### Post by Endless Bard on 2007-09-16
Ugh, never mind, solved my own problem.  There's a link in the OP under Ricoh webcams that links to a different set of drivers ... thought I had installed that but hadn't.  Did so and it works just peachy.

---

### Post by MikeDK on 2007-09-18
have tryed the tribe-5 testing cd, any of you have problems on getting it to work??
My Lap is a DV9000eu series AMD TL-52 CPU, Nvidia GO 7600.

Any help and I will be very thankfull

Kind Regards MikeDK

---

### Post by Veinor on 2007-09-19
I keep having this weird pseudo-hard-lock: i can move the cursor around, and click on, say, the menus on top, but I don't actually get the menus. However, I can minimize the windows using the list on bottom. The keyboard does nothing except when I use the ctrl-alt-sysrq combinations, and cron jobs still run on time. I am running Ubuntu 7.04 on a dv9235nr using the NVIDIA drivers from the Restricted Driver Manager and this has happened with both Beryl 0.2.1 and Compiz-fusion 0.5.3; I am trying it out right now with just Metacity. Could this be a driver issue, or is it an issue with compiz/beryl?

---

### Post by rbrewer on 2007-09-19
Veinor: sounds like a compiz/beryl issue to me.  My dv6000 model (AMD cpu, nvidia gpu) is solid if I boot with "noapic noirqdebug".  Its problem is a high rate of spurious ehci interrupts as shown by top and powertop.  I'm running ubuntu 7.10 and the restricted nvidia driver.  Within an hour of enabling compiz I had my first-ever X session crash on this box.  I went back to metacity and I'm rock steady again.

---

### Post by EXCiD3 on 2007-09-19
What if you guys try installing the newest Nvidia driver using Envy? I've never had a problem using Envy's installed drivers and Compiz Fusion/Beryl. I think the the driver from the repositories is slightly out of date and this could be causing your problems with the graphics intensive applications like Compositing Window Managers.

---

### Post by PsychedelicReaction on 2007-09-20
Hi guys. I have a HP dv2172 and the mc card reader works fine but just with sd! i tried with a micro mmc dual voltage, the 64mb micro mmc included in my nokia 6680 phone, but is not recognized by ubuntu, just in windows.
any suggestion?

---

### Post by EXCiD3 on 2007-09-20
Possibly the drivers don't fully support the card reader's full functionality. I havent had the need for the card reader, so I wont be able to help.

Anyone else who cant use the card reader?

---

### Post by ENDI1111 on 2007-09-20
I need some serious help with Ubuntu installation.  This is like my ninth time trying to install this OS.  It is the alternate CD...the intergrity of it is fine.  When done and I reboot...in the boot menu the status bar completes, but the OS does not load.  In safe mode it shows that it stalls at the hardware drivers and goes no further.  I have a New HP dv6000 with the AMD64 x2 process, broadcom wireless...which does not work...need help with that too.  Would be great to hear from somebody as soon as possible.  :mad:

---

### Post by gimp0r on 2007-09-20
@ENDI1111

I think i have the same model. Does it say DV6500 on the label on the bottom, if so i bought one from staples last week, All working fine now?

Why dont you try the AMD64 Livecd rather than the alternate. It should be straight forward to install.

---

### Post by EXCiD3 on 2007-09-20
> **gimp0r said:**
> Why dont you try the AMD64 Livecd rather than the alternate. It should be straight forward to install.


Due to problems with the AMD laptops, the alternate cd allows for an easier installation without special configuration just to install. Once installed you will still need to configure the installation however.

---

### Post by pigphish on 2007-09-21
> **EXCiD3 said:**
> In order for me to start coding this project, would people please post their system specs, and include the outputs of both lspci and lsusb? Please state your model number and any other info you may think relevant. I will gather this, figure out which hardware the first version will support and then will go from there.

My goal will be that you download this script directly after a fresh install, update Ubuntu to the newest packages, then run this script to have your drivers installed. Any help would be greatly appreciated and will help newer Linux users to be more at ease with their transition from Windows.


HP dv9225us (HP Pavilion dv9000 series)
AMD Turion 64x2 tl-60, 2gb of ram, 160gb sata x2 (installed second hard drive)
Installed 7.04 x64 (64 bit) with minor issues

Added to Boot: noapic nolapic irqpoll
did not edit grub after install however. 

Updated nvidia gfx driver using automatix (though envy worked as well)
Updated Broadcom wireless driver using wrapper script mentioned in the howto
(both above worked flawlessly)

have not tested webcam though no errors. SD card reader works (did not try others) 

USB plug and play OOB

lspci: 
> 
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
george@pigphish:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)



lsusb:
> 
Bus 002 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000  


---

### Post by mrojas73 on 2007-09-21
The lastest updates fix any issues with dv6000.  I just finished installing and this is what I did: Installed using alternate CD, edited the grub entry so that I could boot, connected to the internet and did in the command: sudo apt-get update and sudo apt-get dist-upgrade.  This downloaded all the latest updates, installed and rebooted normaly without having to change anything.

I hope this helps.

---

### Post by EXCiD3 on 2007-09-22
> **mrojas73 said:**
> The lastest updates fix any issues with dv6000.  I just finished installing and this is what I did: Installed using alternate CD, edited the grub entry so that I could boot, connected to the internet and did in the command: sudo apt-get update and sudo apt-get dist-upgrade.  This downloaded all the latest updates, installed and rebooted normaly without having to change anything.

I hope this helps.

I take it you are using Gutsy then? I'm glad they are finally sorting the problems out. After all the final release is coming up in just about a month!

---

### Post by kalium on 2007-09-22
[Here it is]("http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&p=43489") the complete guide to HP Pavilion DV9575ES.

Only one thing left: ***_How to configure both HP touch-sensible keys and HP iR Remote Control?_***

---

### Post by EXCiD3 on 2007-09-22
Nice job dude

---

### Post by dfreer on 2007-09-25
Has anyone had issues with somewhat random freezing on their HP dv6000 Laptops? Specifically, I have a Intel core 2 duo model with Nvidia GeForce 7400 and Intel PRO/3945 Wireless. In both 32/64 bit versions of Ubuntu Edgy/Feisty, and Debian Etch/Lenny, it seems that my laptop will become completely unresponsive except for the mouse, which oddly enough moves just fine. I'm not sure, but I think it really only happens when using the scroll wheel in Firefox.

---

### Post by solongfx on 2007-09-26
> **solongfx said:**
>  now I can't access my second hard drive (sdb1, or at least, it should be).

Solved this by installing the developing Gusty kernel, see here: [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by ahsid on 2007-09-26
the camera works fine with Amsn 0.97rc1 but not with 0.93
Hope this helps. :)

---

### Post by EXCiD3 on 2007-09-26
Just make sure you are running the latest version of the software to ensure the most compatibility. As a warning though, the betas and alphas are not completely stable, however they will most likely include much more support and have a greater compatibility with your hardware.

---

### Post by aldeby on 2007-09-26
Hi! Thank you for this interesting thread, it helped me a lot to get rid of M$ windows.

Have you run Intel **powertop** power optimization program? 
What is the highest CPU power state **(Cn)** you get? 
Despite our laptops should support C4 power state I only get C3 as a maximum (of course I have the C4 switch in the BIOS to ENABLED).

Have you updated your BIOS to latest version **F.22A**? (this applies to all dv9xxx,dv6xxx,dv2xxx owners we all have same bios)
I did and with that particular BIOS version the CPU is suck at C0 state (the running one and most power consuming). Also the highest version powertop reported was C2.

I had to downgrade to F.09 BIOS in order to bring back C3 power state and get my some 90 minutes with the battery.

Shame on HP coders, they release BIOS updates which break such important features!
If you know some way to tell them of the mistake and urge them an update, maybe letting Linux support also C4 power state...

Thank you!!

---

### Post by Jott on 2007-09-30
Hi,

I've got gutsy installed on my hp dv9000.  Specificly:

Hp pavillion dv9208nr notebook
AMD turion 64 x2
NVIDIA geoforce go 6150 graphics
BCM94311MCG wlan mini-PCI (rev 01) wireless

using ndiswrapper and latest drivers for wireless
using 'nv' driver for graphics

gutsy installed and updated.

booting with noapic irqpoll irqfixup noirqdebug nosmp boot options.

There are two problems that I'm having.  The first and most serious is that I'm experiencing regular hard crashes - everything will just freeze and I'm dead in the water.  I'm still learning my way around linux, so I'm not really sure how to go about diagnosing the problem.  Any help would be greatly appreciated - the laptop is barely usable as is, which is very very sad.

The other problem is that every few seconds the hard drive or the fan spins up, just for a second or two, and then spins down.  This isn't very serious, but it's annoying and I can't imagine it's very good for the life of the machine.

I'm hoping that it will all be fixed before gutsy goes gold, but with each update my hope dwindles a little.  I'm supposed to be buying this machine from a friend, but if it can't run ubuntu without freezing, I don't really want it. 

Thanks!

---

### Post by skinnie on 2007-09-30
> **aldeby said:**
> Hi! Thank you for this interesting thread, it helped me a lot to get rid of M$ windows.

Have you run Intel **powertop** power optimization program? 
What is the highest CPU power state **(Cn)** you get? 
Despite our laptops should support C4 power state I only get C3 as a maximum (of course I have the C4 switch in the BIOS to ENABLED).

Have you updated your BIOS to latest version **F.22A**? (this applies to all dv9xxx,dv6xxx,dv2xxx owners we all have same bios)
I did and with that particular BIOS version the CPU is suck at C0 state (the running one and most power consuming). Also the highest version powertop reported was C2.

I had to downgrade to F.09 BIOS in order to bring back C3 power state and get my some 90 minutes with the battery.

Shame on HP coders, they release BIOS updates which break such important features!
If you know some way to tell them of the mistake and urge them an update, maybe letting Linux support also C4 power state...

Thank you!!

I have the latest bios...but I don't know nothing about that states..why don't u email them?they are very quick answering..but most of the time,they seems robots..

---

### Post by ahsid on 2007-10-01
Hi,
Has someone tried to make work the** microdia camera** with the uvc drivers and **Amsn0.97rc1** yet?
Because I did so with debian Testing and it worked fine, but I didn't try with ubuntu feisty.

---

### Post by Ayuthia on 2007-10-01
> **Jott said:**
> Hi,

I've got gutsy installed on my hp dv9000.  Specificly:

Hp pavillion dv9208nr notebook
AMD turion 64 x2
NVIDIA geoforce go 6150 graphics
BCM94311MCG wlan mini-PCI (rev 01) wireless

using ndiswrapper and latest drivers for wireless
using 'nv' driver for graphics

gutsy installed and updated.

booting with noapic irqpoll irqfixup noirqdebug nosmp boot options.

There are two problems that I'm having.  The first and most serious is that I'm experiencing regular hard crashes - everything will just freeze and I'm dead in the water.  I'm still learning my way around linux, so I'm not really sure how to go about diagnosing the problem.  Any help would be greatly appreciated - the laptop is barely usable as is, which is very very sad.

The other problem is that every few seconds the hard drive or the fan spins up, just for a second or two, and then spins down.  This isn't very serious, but it's annoying and I can't imagine it's very good for the life of the machine.

I'm hoping that it will all be fixed before gutsy goes gold, but with each update my hope dwindles a little.  I'm supposed to be buying this machine from a friend, but if it can't run ubuntu without freezing, I don't really want it. 

Thanks!

You might want to try to take some of those options out of your kernel boot parameters and see if it helps.  I am running a dv6000 with similar hardware and booting with noapic  noirqdebug and it seems to be running ok.  If it does keep locking up, you might want to take a look at the logs in /var/log and check messages and dmesg.0.  One of those two might help tell you what happened.  If you can't make any sense of the logs, you can post them as attachments and someone here will most likely try to help.

---

### Post by Ayuthia on 2007-10-01
> **ahsid said:**
> Hi,
Has someone tried to make work the** microdia camera** with the uvc drivers and **Amsn0.97rc1** yet?
Because I did so with debian Testing and it worked fine, but I didn't try with ubuntu feisty.
Have you tried it after installing libpt-plugins-v4l2?  I had some success getting the webcam to turn on and was able to see myself but I was not able get past the firewall (borrowing a neighbor's connection--yes he knows about it) so I have not gotten any further.

---

### Post by ahsid on 2007-10-01
Ayuthia
libpt-plugins-v4l2 is installed on my computer, amsn says that I'm behind a firewall and it works okay.
Have you installed the last version of amsn?

---

### Post by Jott on 2007-10-01
Thanks Ayuthia,

it seems to be stable with just noapic and irqfixup.  Haven't had a lockup in almost two days.  How do I find out what all these boot options actually do?  I saw in one of the logs (/var/log/kernel.log, maybe) something about that option impacting system performance.

I still have the excessive drive spinning issue.  When I check dmesg, I fiind the following:

[ 6799.564000] ide: failed opcode was: unknown
[ 6799.564000] hda: drive not ready for command
[ 6799.564000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }

over and over and over again.  Any ideas?

EDIT:
after a reboot, I get a bunch of different stuff from dmesg:

[  102.368000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0xd0). Trying to recover by ending request.
[  108.372000] hda: packet command error: status=0xd0 { Busy }
[  108.372000] ide: failed opcode was: unknown
[  113.160000] eth1: no IPv6 routers present
[  126.372000] hda: packet command error: status=0xd0 { Busy }
[  126.372000] ide: failed opcode was: unknown
[  128.372000] hda: packet command error: status=0xd0 { Busy }
[  128.372000] ide: failed opcode was: unknown
[  132.372000] hda: packet command error: status=0xd0 { Busy }
[  132.372000] ide: failed opcode was: unknown

drive is still spinning up, spinning down.  It does appear confused.

---

### Post by idkwot on 2007-10-01
i have the confused hard drive going also :-X

---

### Post by hvymtlsteve on 2007-10-02
> **ahsid said:**
> the camera works fine with Amsn 0.97rc1 but not with 0.93
Hope this helps. :)

I don't have a DV9000, I have a TX1000, but I will chime in here anyway--- I concur with this. 

Last night, when I did 
```
sudo apt-get install amsn
```

I got version 0.96 and when I tried a video conf with somebody, I was able to receive video, but when I sent my feed, I was told it was blank... I also couldn't see my own video. 
(I had confirmed my camera to work by testing it in gstreamer-properties and ekiga). 

So I removed that and tonight and got the distribution independent installer which had 0.97RC and gave it another shot. Worked like a charm!

---

### Post by Ayuthia on 2007-10-02
> **Jott said:**
> Thanks Ayuthia,

it seems to be stable with just noapic and irqfixup.  Haven't had a lockup in almost two days.  How do I find out what all these boot options actually do?  I saw in one of the logs (/var/log/kernel.log, maybe) something about that option impacting system performance.

Here is a link to the kernel parameters.  It mainly gives a brief description on what they do.
[http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)

---

### Post by Ayuthia on 2007-10-02
> **ahsid said:**
> Ayuthia
libpt-plugins-v4l2 is installed on my computer, amsn says that I'm behind a firewall and it works okay.
Have you installed the last version of amsn?
I have not tried as of yet.  I just recently wiped out my linux partitions and had to rebuild.  I will try that out sometime.  Thanks!

---

### Post by Ayuthia on 2007-10-02
> **Jott said:**
> Thanks Ayuthia,

I still have the excessive drive spinning issue.  When I check dmesg, I fiind the following:

[ 6799.564000] ide: failed opcode was: unknown
[ 6799.564000] hda: drive not ready for command
[ 6799.564000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }

over and over and over again.  Any ideas?

EDIT:
after a reboot, I get a bunch of different stuff from dmesg:

[  102.368000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0xd0). Trying to recover by ending request.
[  108.372000] hda: packet command error: status=0xd0 { Busy }
[  108.372000] ide: failed opcode was: unknown
[  113.160000] eth1: no IPv6 routers present
[  126.372000] hda: packet command error: status=0xd0 { Busy }
[  126.372000] ide: failed opcode was: unknown
[  128.372000] hda: packet command error: status=0xd0 { Busy }
[  128.372000] ide: failed opcode was: unknown
[  132.372000] hda: packet command error: status=0xd0 { Busy }
[  132.372000] ide: failed opcode was: unknown

drive is still spinning up, spinning down.  It does appear confused.

I am not for sure exactly what is causing this.  It could be with the kernel options again.  Here is a link that discusses this issue a little further and provides different solutions that might work:
[http://ubuntuforums.org/showthread.php?t=24634](http://ubuntuforums.org/showthread.php?t=24634)

You might try using noirqdebug instead of irqpoll.  That might help.  I used irqpoll for a while, but I was running into problems where my keyboard would have some keyboard response issues.

---

### Post by starcannon on 2007-10-02
> **MikeDK said:**
> by the way, has any one of you still this boot-error message "failed to allocate mem resources", on 32bit's on AMD systems??

Kind regards MikeDK

Brand Spankin new dv2600 w/Intel CPU and Nvidia GPU:confused:
I have that problem, and it drops me to BusyBox, unfortunately I have no idea how to use BusyBox so I am stuck.

---

### Post by EXCiD3 on 2007-10-02
What is the error that you receive? Is it tty job control by any chance?

---

### Post by kittH on 2007-10-04
> **EXCiD3 said:**
> What is the error that you receive? Is it tty job control by any chance?

Hi, I'm new here, trying to install Ubuntu for the first time.

I am receiving exactly that error, the tty job control.

I have tried all of the F6 options that I saw mentioned in the first couple pages but it does not appear to be having any effect.

Any suggestions ? 

It is a DV9535 for the record.

---

### Post by EXCiD3 on 2007-10-04
> **kittH said:**
> Hi, I'm new here, trying to install Ubuntu for the first time.

I am receiving exactly that error, the tty job control.

I have tried all of the F6 options that I saw mentioned in the first couple pages but it does not appear to be having any effect.

Any suggestions ? 

It is a DV9535 for the record.

There are many reasons as to why this is happening. Here are several threads that may be of help. If one of these works for you please let me know.

[http://ubuntuforums.org/showthread.php?t=415009&highlight=job+tty+control](http://ubuntuforums.org/showthread.php?t=415009&highlight=job+tty+control)

[http://ubuntuforums.org/showthread.php?t=478715&highlight=job+tty+control](http://ubuntuforums.org/showthread.php?t=478715&highlight=job+tty+control)
[http://ubuntuforums.org/showthread.php?t=386688&highlight=job+tty+control](http://ubuntuforums.org/showthread.php?t=386688&highlight=job+tty+control)

**NOTE:** I will be updating my tutorial once Gutsy is released. I will be looking for contributors of their steps to install Gutsy from a LiveCD of the official Gutsy release. If you would like to help, please contact me via PM, IM, or email!

[B][SIZE=4][COLOR=Lime] A NEW HOWTO WILL BE CREATED FOR THE GUTSY RELEASE! Until then, this Howto supports only Feisty, some things may work on Gutsy beta, but have not been tested.
 [SIZE=3][COLOR=Blue]
If you would like to contribute your installation/configuration steps of the Official Gutsy release, please contact me. I will be creating the Howto only AFTER the official Gutsy release and will be looking for contributors with the following HP laptop models:
[/COLOR][/SIZE][/COLOR][/SIZE][/B][B][SIZE=2]- HP Pavilion HDX
-HP Pavilion dv9500t
-HP Pavilion dv9500z
-HP Pavilion dv9000z
-HP Pavilion dv6500t Special Edition
-HP Pavilion dv6500t
-HP Pavilion dv6500z
-HP Pavilion dv6000z
-HP Pavilion tx1000z
-HP Pavilion dv2500t Broadband Wireless
-HP Pavilion dv2500t
-HP Pavilion dv2000
-Compaq Presario V6000TX
-Compaq Presario V6500Z
-Compaq Presario C500T
-Other HP/Compaq Laptops you would like included in the Howto[/SIZE][/B]

---

### Post by Scroobytec on 2007-10-06
**[COLOR="Lime"] A NEW HOWTO WILL BE CREATED FOR THE GUTSY RELEASE![/COLOR]**

EXCiD3 I look forward to it, as by then my dv 9521Ei will be ready to receive the best Ubuntu release yet.

I just hope that I have a few niggles as I have had on my desktop.

---

### Post by jamarsa on 2007-10-07
> **kittH said:**
> Hi, I'm new here, trying to install Ubuntu for the first time.

I am receiving exactly that error, the tty job control.

I have tried all of the F6 options that I saw mentioned in the first couple pages but it does not appear to be having any effect.

Any suggestions ? 

It is a DV9535 for the record.


The tty job control error is due to it not detecting the ide bus at boot, thus missing the CDROM (type 'cat /casper.log' for details). It happened to me yesterday, and loading the 'alternate CD' did solve it. But I'm still struggling to finish the install, though... It shows a messed text interface, supposedly trying to configure Xorg (I need to debug it now) :(. All this in a dv6535.

follow-up: Actually, it was the console-setup package wich messed the screen (all coloured boxes). Adding the 'nofb' option solved it for the moment.

---

### Post by skinnie on 2007-10-07
kittH I had that problem even with the alternate cd..solution,ubuntu 7.10 alternate..

---

### Post by solongfx on 2007-10-07
Has anyone managed to get their headphone jacks to work? Mine neither mute the laptop speakers nor play through the external ones. Mine's a dv9565

---

### Post by EXCiD3 on 2007-10-07
[SIZE=5]**GUTSY THREAD HAS BEEN CREATED: **[/SIZE][http://ubuntuforums.org/showthread.php?t=569789](http://ubuntuforums.org/showthread.php?t=569789)

---

### Post by nelliott71 on 2007-10-07
Thanks to everyone who contributed here - it went a long way towards getting my DV9207us running.:)

Since I often watch movies on my laptop, I was frustrated by having to disable vsync to get suspend working.  I hate the tearing you get without vsync.  After a while an idea occured to me, and so far it is working great.  Is this a rube-goldberg solution..?  Is there an easier way to have suspend and vsync?

I created a simple script to disable vsync, I called it "disable-vsync.sh" (how orignal!!)

```
#!/bin/sh
/usr/bin/gconftool -s /apps/compiz/general/screen0/options/sync_to_vblank -t boolean false
```

Then in /etc/acpi/suspend.d I created a new script call 01-disable-vsync.sh that looks like this:
```

#!/bin/sh
su <myusername> <path-to-script>/disable-vsync.sh
```

I found I had to use "su" to effect the changes.  I'm sure there is a way to add some magic here to determine the username automaticaly... but since I'm the only one who uses my laptop... I was lazy and hard-coded the username.

I did the reverse of this to re-enable vsync on resume... and used 99-enable-vsync.sh instead of 01...

I think I read all the pages of this thread, and didn't see another solution... if I missed it please feel free to make fun of me.  :lolflag:

---

### Post by yakovyarmo on 2007-10-07
i am really happy that i found this post and it helped me a lot.
but there are some stuff that are maybe specific for my laptop.
and i didn't see them in these post. 
a) you need to load the piix module for the dvd burner to work.
b) my suspend works just by canceling the Sync To Vblank in compiz and adding "nvagp"  "1"
in xorg.conf.

---

### Post by EXCiD3 on 2007-10-07
> **nelliott71 said:**
> I think I read all the pages of this thread, and didn't see another solution... if I missed it please feel free to make fun of me.  :lolflag:
I'm just gonna make fun of you anyways! :lolflag:

---

### Post by aldeby on 2007-10-07
Hi!
My question concerns my laptop **fingerprint reader **and integrated **webcam**,
those are integrated devices internally connected to the USB bus. 
Hardware information applet shows me these devices consume 600mA altogether which means more or less 6 Watts power even if they are not in use (as far as I understand, since the applet states under tab USB > Power Usage the same amount regardless of they being in use or not)

So, the question is: **How could I disable and power off these devices? **

They are integrated, so no way to phisically disconnect them, what's more they are connected via usb, so no way to disable them by simply removing device drivers (I need USB ports!).

Thankyou

---

### Post by mariodavidpalacio on 2007-10-07
Hi, everyone! I'm here because I'm a Ubuntu fan. I mean, I like very much this "way of thinking". As you might guess, I'm here because I have problems intalling Ubuntu (FF) on my BRAND NEW LAPTOP 

[http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Display&v1=14.1%26quot%3B&series_name=dv2500t_series](http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Display&v1=14.1%26quot%3B&series_name=dv2500t_series)

(I'm happy about it, so pardon me). The first thing I noticed was that none of the Linux distros, namely (K,X) Ubuntu, Damn Small Linux or Zenwalk, booted properly. They just hanged in the middle of the booting like there was something wrong with my pc, not a linux-capable notebook, just kidding. I had to boot Ubuntu live cd using f6 and the break=top option. Then modprobe piix and exit. That was something I didn't expect because I have been using linux in several machines lately and, AT LEAST, they booted with no problem at all.

After a little searchin' and googlin'  I could boot. I only tried this with Ubuntu because I would have to search a solution for every distro and the truth is I just wanna install my Ubuntu.

But then I come to this other issue, I CAN NOT RESIZE MY VISTA/NTFS partition with gparted.

"ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software."

I ran chkdsk /f on startup but it will hang too.

I really need to resize it, because I don't have any swap-linux partition yet and I can not just format the whole disk.

By the way, I really expect none of this will be happening with the new Ubuntu version. They should be having this kind of notebook problems in mind IMHO.

And other thing: will my little remote controll (included) work? I know that it will not work with the same  applications, but will it be able to be controlling some of the features of Rythmbox, for example? And what about the Quickplay buttons?

Please, guys, help me. I know you can solve it right away :)

My e-mail is [email]mariodavidpalacio@gmail.com[/email] if you like to talk about it.

THANKS!

---

### Post by aldeby on 2007-10-08
yes, the littele remote control will definitely work out of the box. if you would like to personalize the buttons you just have to go to **system > preferences > keyboard shortcuts**

for what concerns the partition resizing I have used a third party partition manager program bootable via CD.

anyway I suggest you to try the gutsy beta, there are lots of improvements, also you will not have to issue any special argument ar grub for booting.

---

### Post by punkdad1 on 2007-10-08
i used noapic nolapic and worked

---

### Post by PsychedelicReaction on 2007-10-08
since i upgraded to gutsy i have this problem with alsa. the main volume controller (the one controlled by the multimedia keys) is called headphones but it does not affect the volume of my pc! i have to manually set the pcm to change volume. it just worked with prevous version.

EDIT: i have hp dv2000 serie

---

### Post by Jott on 2007-10-08
Just for the record, with the latest update I was able to remove all the extraneous boot options (I was using noapic and irqpoll) and all seems fine.  I'm no longer getting weird messages about confused drives.  It seems like the machine runs a little hot, and the hard drive spins up and down more often than it should, and I lose networking after coming back from suspend, but I'm going to wait and see what happens after Gutsy goes gold.  


Hp pavillion dv9208nr notebook
AMD turion 64 x2
NVIDIA geoforce go 6150 graphics
BCM94311MCG wlan mini-PCI (rev 01) wireless

using ndiswrapper and latest drivers for wireless
using 'nv' driver for graphics

gutsy installed and updated.

EDIT:with  the newest kernel updates - *.14 - the system no longer boots.  Gets through all the stuff it loads when the splash screen is up, then flashes a few times and freezes up.  Haven't tried it with the noapic boot option yet, I just went back to the .*13 kernel for now.  See what tonight's updates bring.

---

### Post by EXCiD3 on 2007-10-10
Has anyone had trouble with the system time? My bios always seems to be about 5 hours different than the regular time. I change, save the settings, but upon EVERY reboot the time is set to 5 hours in the future. What could be causing this? I have set the bios back to normal time, but it seems to be changing every time...Is my bios battery dead?

Also please check out the Gutsy thread, [http://ubuntuforums.org/showthread.php?t=569789](http://ubuntuforums.org/showthread.php?t=569789) and be sure to read through the hardware list to check to see if I am missing anything!

---

### Post by nostick on 2007-10-12
Yeah! It really helps me fix my graphic card, web camera!

Thanks a lot!

---

### Post by mariodavidpalacio on 2007-10-13
I have Ubuntu already installed, but when I put a CD in the cdrom I get no automatic mounting, so I double click on the cd-rom 1 click on nautilus but I get this:
 
mount: /dev/hda is not a block device

How to fix this? I have no idea, but maybe some one there is reading this and thinkingto the way to solve it.

Thanks

---

### Post by EXCiD3 on 2007-10-13
I am preparing a list of hardware to be included in the new tutorial for Gutsy that I am writing. Will anyone read through the hardware list and see if I am missing anything? [http://ubuntuforums.org/showthread.php?t=569789](http://ubuntuforums.org/showthread.php?t=569789) Any help would be greatly appreciated!

Chris

---

### Post by sbussy89 on 2007-10-17
thank you for the GREAT walkthrough... i just have one problem.  when i go to edit the code to install the webcam, it doesnt say "INSTALL_MOD_DIR := usb/media", it says "INSTALL_MOD_DIR=$(INSTALL_MOD_DIR) ".  What should i do?

---

### Post by EXCiD3 on 2007-10-17
> **sbussy89 said:**
> thank you for the GREAT walkthrough... i just have one problem.  when i go to edit the code to install the webcam, it doesnt say "INSTALL_MOD_DIR := usb/media", it says "INSTALL_MOD_DIR=$(INSTALL_MOD_DIR) ".  What should i do?

Could you post your Makefile? I just did svn checkout on it once again, and mine looks like this: ```
KERNEL_VERSION    := `uname -r`
KERNEL_DIR    := /lib/modules/$(KERNEL_VERSION)/build
INSTALL_MOD_DIR    := usb/media

PWD        := $(shell pwd)

obj-m        := uvcvideo.o
uvcvideo-objs   := uvc_driver.o uvc_queue.o uvc_v4l2.o uvc_video.o uvc_ctrl.o

all: uvcvideo

uvcvideo:
    @echo "Building USB Video Class driver..."
    @(cd $(KERNEL_DIR) && make -C $(KERNEL_DIR) SUBDIRS=$(PWD) CROSS_COMPILE=$(CROSS_COMPILE) modules)

install:
    @echo "Installing USB Video Class driver..."
    @(cd $(KERNEL_DIR) && make -C $(KERNEL_DIR) SUBDIRS=$(PWD) INSTALL_MOD_DIR=$(INSTALL_MOD_DIR) INSTALL_MOD_PATH=$(INSTALL_MOD_PATH) modules_install)
    depmod -ae

clean:
    -rm -f *.o *.ko .*.cmd .*.flags *.mod.c Modules.symvers
    -rm -rf .tmp_versions
```

The third line is the one you are to change. $(INSTALL_MOD_DIR) means to replace that with the value of variable INSTALL_MOD_DIR. If you don't know programming it can be hard to understand.

Your Makefile should look like this after step 3:```
KERNEL_VERSION    := `uname -r`
KERNEL_DIR    := /lib/modules/$(KERNEL_VERSION)/build
INSTALL_MOD_DIR    := kernel/ubuntu/media/usbvideo

PWD        := $(shell pwd)

obj-m        := uvcvideo.o
uvcvideo-objs   := uvc_driver.o uvc_queue.o uvc_v4l2.o uvc_video.o uvc_ctrl.o

all: uvcvideo

uvcvideo:
    @echo "Building USB Video Class driver..."
    @(cd $(KERNEL_DIR) && make -C $(KERNEL_DIR) SUBDIRS=$(PWD) CROSS_COMPILE=$(CROSS_COMPILE) modules)

install:
    @echo "Installing USB Video Class driver..."
    @(cd $(KERNEL_DIR) && make -C $(KERNEL_DIR) SUBDIRS=$(PWD) INSTALL_MOD_DIR=$(INSTALL_MOD_DIR) INSTALL_MOD_PATH=$(INSTALL_MOD_PATH) modules_install)
    depmod -ae

clean:
    -rm -f *.o *.ko .*.cmd .*.flags *.mod.c Modules.symvers
    -rm -rf .tmp_versions
```

Hope that helps!

Chris

---

### Post by sbussy89 on 2007-10-17
ok my browser scrolled down to the bottom on its own so i missed the first few lines of code lol, but now i have a  new problem... when i change all of those things through the terminal i click the test button and the camera works, but if i go to camorama or try to make a facebook video neither detect the camera.  i went through the whole terminal thing again and the settings were the same (so they saved) and clicking the test button still made the camera work from there... wuts up?

---

### Post by EXCiD3 on 2007-10-17
> **sbussy89 said:**
> you guys are amazing!   i didnt realize that my editor was scrolling to the bottom of the code automatically, so i missed the first few lines of the code.  i changed it like it said and now it works perfectly!!! thank you so much... live and let linux :)

Haha, glad I could help! So long as I don't cause you to switch back to Windows ;)

Chris

---

### Post by sbussy89 on 2007-10-18
actually, i had to edit my post because i ran into a new problem lol

---

### Post by EXCiD3 on 2007-10-18
You need to make sure the applications are running with the V4L2 drivers. I am pretty sure this is the only driver that can communicate with the webcams.

---

### Post by sbussy89 on 2007-10-18
ok im not sure exactly how 2 check that... i do kno that these prgrams work with the webcam fine when im running vista, but idk wut the translation is to ubuntu

---

### Post by christophre on 2007-10-19
Hi Guys,

It seems that I wouldn't be the first with these problems, but I still haven't gotten to the bottom of them :P

Using the 7.10 desktop LiveCD (amd64), I get the ubiquitous black screen after the installer leaves the boot menu screen (ie, when it actually starts to boot).  I've tried seemingly every permutation of 'noapic', 'nolapic', 'irqpoll' and 'noirqdebug' in both the default install option and the "safe graphics" install option, none to any avail.  I've also tried setting the vga=771 and resolution to 1680x1050x32 (the native resolution for this screen), along with the aforementioned permutations, to no avail, just blackness...

If anyone has any advice considering the above, please do let me know!

Thanks everyone,

-c

dv9500t: Intel Core2 Duo, nVidia 8400m GS, 4965AGN

---

### Post by christophre on 2007-10-19
So, to reply to myself...

...it turns out that the machine wasn't really hung, but that the screen was dead due to the default "splash" option still being present in the boot options and the initialization of the installer taking somewhere between 2-3 full minutes...

So, a note to anyone out there that comes across the black screen problem -- just remove the "splash" boot option, or just wait it out (it takes several minutes).

---

### Post by Scroobytec on 2007-10-19
Just a quick not to all


I have booted 7.10 Live CD on my HP dv9521ei with no hassles or mods at all.\\:D/

I was worried that there would be Black screens or other funnies after reading all the other user problems, so things are looking good for (I hope an uneventful) install on Sunday - that is if the PARTY on Saturday night after the BOKS beat ENGLAND in the Rugby Cup Final is not too hectic.

Will record my findings here and at [http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815).

Ofcouse they will be forwarded to the GURU EXCiD3

---

### Post by EXCiD3 on 2007-10-19
> **christophre said:**
> So, a note to anyone out there that comes across the black screen problem -- just remove the "splash" boot option, or just wait it out (it takes several minutes).

Oh man! I feel stupid for not thinking of that! I *have  *had that problem before, i just completely forgot all about that. Thanks for posting the solution, I will make sure it is in the Howto.

> **Scroobytec said:**
> Ofcouse they will be forwarded to the GURU EXCiD3

:D Thanks Scroobytec. If anyone else would like to let me know how their installation went, please contact me. The more users' information I can get, the better support for the HP/Compaq hardware we will have!

---

### Post by DRAGONPOWER on 2007-10-20
any news on the audio probs with hp laptops and 7.10?

---

### Post by skinnie on 2007-10-20
my hp dv9575ep worked good after installing and compiling the latest alsa..:popcorn:

---

### Post by EXCiD3 on 2007-10-20
**FOR THOSE OF YOU CONSIDERING THE UPGRADE TO GUTSY** Please choose carefully. All the things that work in Feisty are not necessarily going to work in Gutsy such as: dual monitors, nvidia driver (doesnt work for me), audio, wireless, among many others.

Please be cautious when deciding whether or not to use Gutsy. I personally would **NOT** recommend it. It is a step back from Feisty. Less things work that with Feisty.

For further info please read this: [http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by bfledderjohn on 2007-10-20
I'm running a dv6000z, and have not had the issues that you have had, EXCid3.  I figured out the problem with the screen going black when the cord was unplugged or plugged in (it was a power setting issue, which I have tweaked and all is hunky dory now... The only other issue that I have had in 64 bit is that evince has had some garbling issues, so I switched to kpdf and all is good.  I've been with Gutsy for about a month now, and those are the only two issues that I have had... Actually, I like a lot of the updated packages too, some added functionality as well as more polished interfaces.

---

### Post by EXCiD3 on 2007-10-20
I'm glad to hear that Gutsy is working good for you. However I feel that Gutsy doesnt have good enough all around support. Some people may have good luck with it and others may have a terrible time. Therefore I will continue to encourage the use of Feisty instead of Gutsy. Until the features in Gutsy have been fixed I will not encourage its use.

---

### Post by bfledderjohn on 2007-10-21
One of the tools that helped me a boatload back when I started with Edgy on this machine, was the following wiki.... Great resource for the dv6000 series and it may be helpful in this case too.... Once I took care of these issues in edgy, they carried over into Feisty... Except the Broadcomm wireless support.  That failed miserably UNTIL Feisty, and then all was well.

Just my experience, but per your response, you have to make recommendations based on your experience...  I didn't mean to minimize your concerns.


Anyway here's that link!  [https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29)

-Bret

---

### Post by christophre on 2007-10-21
hello hello!

after well over a solid 12 hours (off-and-on, thankfully) of googling and mucking about, i'm glad to say that my sound problems in gutsy (7.10) were finally solved!

solution in two easy steps!!!:

1) i need some form of update ALSA drivers, either via:

1a)  ```
sudo apt-get install linux-backports-modules
```

OR (but I highly recommend 1a, since it's trivial and better yet, a *package*):

1b) mercurial:

```
sudo apt-get install mercurial automake automake1.4 autoconf
mkdir alsa && cd alsa
hg clone http://hg.alsa-project.org/alsa-driver alsa-driver
cd alsa-driver
hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel
./hgcompile
make install-modules
```

NB: the third option i've come across, installing via "module-assistant," may or may not work -- i never went back to check after i discovered the "magic" module options.  it appeared to me to be building the same version of the ALSA code that comes in the stock ALSA packages, so i fear that this might not work (since the stock ALSA packages *do not* in fact work properly, even with the "magic" module options).  in any case, (1a) is much less effort...

2) ensure that /etc/modprobe.d/alsa-base contains:

```
options snd-hda-intel model=hp position_fix=1
```

et voila!  for me, the crux of the solution lied in (2) (ie, the "magic" options), since i'd seen some form of the suggestion to get updated ALSA drivers in tons of places on the interweb, but i only just now came across (2).

credit should go to the author of:

[http://www.linlap.com/wiki/HP+Pavilion+dv9000z](http://www.linlap.com/wiki/HP+Pavilion+dv9000z)

for the "magic" options.

thanks for all the help!  if even just one person benefits from this posting, i'd be happy!

-chris

---

### Post by Rex_Mundi on 2007-10-22
Just a quick question I hope someone can enlighten me. Just before the boot screen i get a pci memory error at address something. I cant read it in time. Not that anything is malfunctioning but im just curious what it is. 

I have the notebook: HP DV9055ea
(all the details of this system can be found on the HP site)

---

### Post by Stoked on 2007-10-22
Hi, I am new to Linux/Ubuntu and I have tried to install Feisty and Gutsy.  With Feisty I can get to the Live CD using the Alternate CD and then I try to install it and it got hung up at 90% trying to install "Floppy Linux"(I believe it was called).  I haven't tried to reinstall that one yet, maybe it was just a bad install.  But then I tried to install Gutsy and everything installs correctly and when I go to boot it gets hung up at a black screen.  What can I do to fix this?

I am using a HP DV9000 laptop
I am also dual booting with vista(with vista installed already)
The dual booting seems to work fine.

Thanks, 
Mike

---

### Post by EXCiD3 on 2007-10-22
remove the splash parameter from the boot line in grub's /boot/grub/menu.lst

---

### Post by Stoked on 2007-10-22
Hi, thanks for your response but I don't really know how to edit the splash line.  I am in GRUB and I see three lines of Ubuntu which say.

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10 kernel 2.6.22.14-generic (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)

Where would I go to edit the splash line and how exactly would I go about it. 

Thanks,
Mike

I figured it out. Thanks for the help.

---

### Post by EXCiD3 on 2007-10-22
Glad you found it. Did it fix your problem?

Only other thing i can advise is to remove that Vista installation ;)

---

### Post by djnapster on 2007-10-24
i'm having a cannot allocate mem resource error and the red loading bar gets stucked while loading. I've tried alot of code's but.. often it works. When it works i get a black screen and it stucks there.

---

### Post by mnederlanden on 2007-10-24
Model: HP Pavilion dv9009nr
Processor: 1.6 GHz AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-52
Wireless Card: Broadcom 802.11b/g WLAN
Graphics Card: NVIDIA GeForce Go 6150 (UMA)
Gutsy: 7.10 final + updates
Boot Parameters: apci=off

I got it to work by selecting LCD Panel 1440x900 widescreen at 60hz and the "nv - nVidia Riva 128, RIVA TNT, GeForce, nf..." driver...

Firmware for Broadcom 43xx chipset family works for the 9009nr... (I never could get it to work in fiesty)... however the switch on the front of my pc that allows me to turn off my wireless to conserve power is in constant off mode according to ubuntu...

hope the display settings helps somebody... anyone know how to disable my power saving device or a driver that will enable it to work correctly?

---

### Post by EXCiD3 on 2007-10-24
> **mnederlanden said:**
> I got it to work by selecting LCD Panel 1440x900 widescreen at 60hz and the "nv - nVidia Riva 128, RIVA TNT, GeForce, nf..." driver...

Firmware for Broadcom 43xx chipset family works for the 9009nr... (I never could get it to work in fiesty)... however the switch on the front of my pc that allows me to turn off my wireless to conserve power is in constant off mode according to ubuntu...

hope the display settings helps somebody... anyone know how to disable my power saving device or a driver that will enable it to work correctly?

I'm not sure about the wireless, but as for the Nvidia card, the nv driver is only for 2D applications currently. If you want to use Compiz you will need to use the nvidia driver. This will allow for many more options and 3D support. However I have been unable to get the nvidia driver functioning correctly in Gutsy :( It works perfect in Feisty though! :)

---

### Post by mnederlanden on 2007-10-24
Yes unfortunately it does only work in 2d... but when I first installed gutsy I could only display 800x600 and the display colors were all screwed up... It doesn't let me use 3d effects but at least I can use my computer again... primary colors to millions and 800 to 1440 is a big improvement... especially for a noob like myself...

it may not be flashy but it works for now... until they make a hotfix for the restricted NVDIA drivers...
thanks for the help

---

### Post by EXCiD3 on 2007-10-24
Yeah, I love compiz so much I had to revert back to Feisty...nv driver doesnt work with dual monitors anyways. Figured I would rather have that instead of Gutsy since I can do everything I want in Feisty anyways.

---

### Post by lightningstormz on 2007-10-25
I don't know if this was posted before, but if you startup the 64bit Gutsy Live CD on the dv9500t in safe graphics mode, it works perfectly. The screen might automatically turn off, but all you have to do is move your mouse and the Ubuntu desktop will appear. This is a big step up from Feisty because I couldn't even use the Feisty Live CD.

---

### Post by EXCiD3 on 2007-10-25
Yeah, this has to do with some of the things in the new kernel, im pretty sure. Unfortunately the new release works great for some, like you, and horrid for others. If it works for you, thats awesome! I'm glad some people are able to use it. As for me and many others, we are either forced to fight our way through the muck or go back to running Feisty, which is what I have done. Hopefully soon things will start getting fixed and we can all enjoy gutsy. :D

---

### Post by elect on 2007-10-25
Hi, my friend have a 6236ea with a ipw3945 on, but I cant see the wifi interface, it miss.

But in the "restricted drivers" I can see that the closed drivers its in use...

I have tried many howto but no1 worked, what i can do?

---

### Post by the.unclean.cpp on 2007-10-25
I remove the linux partition because I wanted to resize the primary partition that has vista installed on it. I forgot that GRUB is written on the linux partition. Now I can't access my recovery partition to fix my mbr. what can I do?
Grub gives me the error 22, but I know I can't fix it...

---

### Post by EXCiD3 on 2007-10-25
> **the.unclean.cpp said:**
> I remove the linux partition because I wanted to resize the primary partition that has vista installed on it. I forgot that GRUB is written on the linux partition. Now I can't access my recovery partition to fix my mbr. what can I do?
Grub gives me the error 22, but I know I can't fix it...

Just reinstall grub using the LiveCD or the AlternateCD. It is straight forward using the AlternateCD, but slightly more complicated for the LiveCD. A tutorial for the LiveCD can be found here: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by the.unclean.cpp on 2007-10-25
I can't boot from the live cd :( It gives me an error that I think it's related to the graphics card. and I don't have an alternate disc :((
Can I doo that from DamnSmallLinux? That LiveCD boots!

---

### Post by EXCiD3 on 2007-10-25
Technically you should be able to do it from ANY disc that is able to install grub. You should be able to use the same steps in order to install Grub.

---

### Post by jo.angel on 2007-10-27
great help
i have been looking for a solution 4 my webcam (sonix) issue for a while.

Here I got a true step-by-step manual how to get my webcam work.

Thanks, a life saver!

J

---

### Post by hammanu on 2007-10-29
I'm not sure if this information is still useful or not, but your walk through worked perfect for me.

HP dv9000z

[quote='lspci']00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)[/quote]

[quote='lsusb']Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000[/quote]

---

### Post by EXCiD3 on 2007-10-29
> **hammanu said:**
> I'm not sure if this information is still useful or not, but your walk through worked perfect for me.

Glad it worked. If anyone is interested, I have created a website (its a free hosting site :() that I am going to maintain. It is going to have writeups for Ubuntu on HP and Compaq computers. **If anyone would like to contribute stories, ideas, thoughts**, please let me know! I can set your account up and we can collect any information on the HP Laptops in one spot. This will be a good location for us to discuss Ubuntu related information and then we can collect it together and post Howto's on these forums. Also I was thinking about writing a script to install/configure the drivers/hardware that still are not configured by default. If anyone would like to contribute on any of this please let me know!

Chris

---

### Post by aMADme on 2007-10-31
awesome help here guys, thanks a lot ...installation on a dv6000 worked like a charm!

However after I've been playin around with a few window managers and fell in love with xfce I noticed that the remote control as well as the LED volume controls don't work, which work w/o a problem under gnome.

Anybody got a clue on how to make that stuff work under xfce?

cheers
MAD

---

### Post by KevinCLovesU on 2007-11-03
Hello all. I'm in the middle of doing my install to a dv6500z with the GUTSY LiveCD (64-bit). It took a whopping 10 MINUTES to load, but ive got SOUND! I'll keep everybody posted.

Update: Everything installed smoothly. However, DESPITE that the LiveCD recognized my resolution just fine, the install won't, I'm working on it. Sound works, QuickPlay controls work. (Yes it's gutsy!) More updates to come.

Last Update: ALL IS WELL! Envy isntalled the right driver and gave me the NVIDIA menu, which allowed me to set the proper resolution.

---

### Post by hammanu on 2007-11-03
> **KevinCLovesU said:**
> Hello all. I'm in the middle of doing my install to a dv6500z with the GUTSY LiveCD (64-bit). It took a whopping 10 MINUTES to load, but ive got SOUND! I'll keep everybody posted.

Update: Everything installed smoothly. However, DESPITE that the LiveCD recognized my resolution just fine, the install won't, I'm working on it. Sound works, QuickPlay controls work. (Yes it's gutsy!) More updates to come.

Last Update: ALL IS WELL! Envy isntalled the right driver and gave me the NVIDIA menu, which allowed me to set the proper resolution.

If you can find the time would you mind posting a step-by-step of how you got everything to work?  Perhaps it is just an issue with those of us that have the dv9000.

---

### Post by EXCiD3 on 2007-11-03
> **KevinCLovesU said:**
> Hello all. I'm in the middle of doing my install to a dv6500z with the GUTSY LiveCD (64-bit). It took a whopping 10 MINUTES to load, but ive got SOUND! I'll keep everybody posted.

Update: Everything installed smoothly. However, DESPITE that the LiveCD recognized my resolution just fine, the install won't, I'm working on it. Sound works, QuickPlay controls work. (Yes it's gutsy!) More updates to come.

Last Update: ALL IS WELL! Envy isntalled the right driver and gave me the NVIDIA menu, which allowed me to set the proper resolution.

Interesting...Could you please post your hardware specs and your what you did for installation? This could be very helpful for other users with the same specs.

---

### Post by Nordkraft on 2007-11-03
Thanks for all the help:)

I've been having some problems with my usb pen-drive: it does not mount. In fact, sudo fdisk -l shows it isn't even recognized as a partition. 
At first, I thought this might be related to the (auto)mount issues a lot of people have had, but I have a feeling it's rather related to my usb ports in general not functioning properly under Gutsy (actually, I had the same problem under Feisty) since unplugging my usb mouse while the laptop is turned on and plugging it back in renders the mouse useless. I have to have all the usb devices (mice and ext. drive) plugged in at boot-up for them to be recognized.
Anyone have any suggestions?

Cheers

btw: laptop: hp dv6507eo

---

### Post by Nordkraft on 2007-11-04
Well, just found out that my mouse DOES actually work being disconnected and then connected while the laptop is on. 
So the problem is only related - it seems - to the usb-drives. Plugging one in, dmesg tells me the device is detected but it's not automounted and I cannot mount it myself since the device (sdb1 I guess) doesn't exist :(
Running lsusb locks up the terminal - something weird is going on.

Anyone?

---

### Post by mork_on_tour on 2007-11-06
Hi
I just installed gutsy amd-64 on my hp dv9585el and i do report that lightscribe (simplelabeler app) works. I just downloaded the deb packages on lightscribe website, installed them with --force-architecture and that's all.
bye

marco

---

### Post by KevinCLovesU on 2007-11-06
Here are my specs (just the details I think are relevant to the installation):

HP dv6500z

AMD Turion(TM) 64 X2 Dual-Core Mobile Technology TL-62 (2.1 GHz, 512KB+512KB L2 Cache )
15.4" WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
2GB DDR2 System Memory (2 Dimm)
128MB NVIDIA GeForce 8400M GS
Wireless LAN 802.11a/b/g/n and Bluetooth
120GB 5400RPM SATA Hard Drive

It was simpler than I thought. I used the Gutsy LiveCD for AMD64. I believe I started it in Safe Graphics mode, but I do know that the only change I made to the boot parameters was removing "quiet", and I didn't add any parameters. In fact, noapic would just freeze the whole thing up. Removing quiet allowed me to watch what was happening during the process, and I'm glad I did, because the entire process took 10 minutes. If I hadn't had the output, I would have given up. But just stay with it.

Once it finished, the bulletproof X manager launched, and I used it to set my screen res. For that session, it worked. Then I did a normal LiveCD install. Once I booted into the install, my screen settings were wrong, and BulletProof X couldn't fix it. I had to use a 640x480 res until I installed Envy, which gave me access to the NVIDIA settings manager, where I set the proper resolution. At that point everything was working, except my broadcom wireless, which I fixed with [this](http://ubuntuforums.org/showthread.php?t=405990) installer.

So here's the rundown:
-LiveCD works (maybe only in safe graphics mode, and it takes ten minute to start)
-Remove quiet from boot parameters to confirm that something IS in fact, happening.
-The install process is smooth, and has no issues from what I could tell.
-Sound works out of the box.
-Wireless support (broadcom 34xx) is NOT out of the box.
-This GPU pretty much requires the NVIDIA closed source driver, which I installed through envy (it's a great tool.)
-NVIDIA Settings Manager will propersy configure EVERYTHING. (Res, multi-monitor.
-Both the HDMI and VGA outputs work, and can be used as second monitors (not just cloned desktops).
-I haven't gotten HDMI sound to work, but I only tested it once and I think I way be able to get it to work. (I'll update this later.)
-The card reader reads SD cards and Memory sticks out of the box. 
-The webcam works with V4L.
-Compiz-fusion works beautifully.

Anything I missed? Just ask.

---

### Post by EXCiD3 on 2007-11-07
For more information on Gutsy and HP and Compaq laptops, please read my website: [http://excid3.pcriot.com]("http://excid3.pcriot.com/drupal/") Some important information is included on there.

Also, if anyone would like to contribute their laptop experiences and tweaks please register and post to your blog! Once enough information has been gathered I will be writing a tutorial for Gutsy so any information you would like to post on the site that you think would be relevant for the tutorial feel free to post. I would appreciate it.

---

### Post by mvtt on 2007-11-08
Hello everyone. I decided to make a dual-boot, with Win XP and Ubuntu (or Kubuntu, not sure what ill stay with) on my HP dv9500t. Unfortunetly, a problem occurred right at the beginning. I boot from the LiveCD, choose "Start or Install Ubuntu" and a loading screen appears. After about 7-10 sec. of loading, i get an error:

'/bin/sh: can't access tty: job control turned off'  

I read that some people get this error AFTER they finish installing. I haven't found any advice on why this might be happening before i even start installing the system. 

I have 2 HDD's in my laptop. 2x 100Gb. Each hard drive is separate for each system. The first one has Windows XP already isntalled. The other is a clean HDD w/o any partitions on it. 

I would be thankful for any help, since I'm a total Linux n00b. So writting in a simple language would be much appreciated. 

P.S. Oh and I tried typing in the commands that are at the beginning of the How To. 

Thx,
-Matt

---

### Post by scorp123 on 2007-11-11
> **EXCiD3 said:**
>  **Suspend/Hibernate**
        Supposedly adding "nosmp" as a boot option, disabling Sync To Vblank in Beryl, and if you edit the /etc/default/acpi-support and set POST_VIDEO=false, suspend and hibernate should work better. QUESTION: Is "nosmp" the option that makes this work? Anyone know?  On my dv2108ea I use these options:

**/boot/grub/menu.lst:**
```
...
# defoptions=splash vga=791 pci=bios acpi_sleep=s3_bios
...
``` And then execute "sudo update-grub". What those options do: They tell the kernel to let the system's BIOS handle the PCI interrupts and the deep-sleep modes. Works tip top. I can standby + hibernate + resume without problems, even when Beryl or Compiz-Fusion are active. Resume takes me right back into my 3D desktop where I left off.

**/etc/default/acpi-support:**
```
ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
[COLOR="Red"]MODULES="ipw3945"[/COLOR]
MODULES_WHITELIST=""
SAVE_VBE_STATE=false
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=true
USE_DPMS=true
HIBERNATE_MODE=platform
LOCK_SCREEN=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=true
``` That line MODULES="ipw3945" keeps the Intel WiFi kernel module in memory; else it may unload and WiFi stops working when resuming. So the line above prevents this, now my Intel 3945abg *always* works after a resume.

What I would be interested in is how to get CPU scaling + throttling working properly. Anyone have any experience with this?

---

### Post by scorp123 on 2007-11-12
> **scorp123 said:**
> What I would be interested in is how to get CPU scaling + throttling working properly. Anyone have any experience with this? Self-response.... I think I found it :)  **/etc/laptop-mode/laptop-mode.conf** ...  "CONTROL_CPU_FREQUENCY=1" and "CONTROL_CPU_THROTTLING=1" (I left anything else untouched); and for good measure I added this to **/etc/modules:**
```
acpi-cpufreq
cpufreq_userspace
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
freq_table
``` Now my dv2108ea will throttle down to 800 MHz (instead of continuing to run at max. speed) which helps a great deal when running on batteries. :)

---

### Post by scorp123 on 2007-11-16
Self-response .... On Ubuntu 7.10 "Gutsy" **[COLOR="Red"]*DO NOT*[/COLOR]** use any of the parameters I mention in my postings above (those are for 7.04 "Feisty" and work tip top there!) ... Just leave everything "as is" and suspend + hibernate + resume and everything else will work (at least this is the case with my **dv2108ea** ... things started to break as soon as I started to mess around with the config files I mention above).

Also ... doing a clean install and not carrying over any old settings (this includes some system config files and .gnome* folders in the /home directory) seems to help a great deal to get "Gutsy" working cleanly ... at least as far as my HP laptop is concerned.

---

### Post by EXCiD3 on 2007-11-16
Thanks for the info scorp123! I wont be updating my Howto until either a 7.11 release or 8.04. I personally do NOT feel Gutsy is worth writing a Howto as there are far too many problems for a new release. Several important issues relating to HP Laptops and Gutsy can be found at my website: [http://excid3.pcriot.com]("http://excid3.pcriot.com/")

Please post your results of Gutsy if you decide to try it. I am not officially supporting Gutsy until it has become more stable. Sorry to disappoint, but Fiesty has much better quality support, even if it takes a bit longer to configure :(

Chris

---

### Post by punischdude on 2007-11-17
For those, who use HP dv9533eg and audio jack sensing does'nt work:

I got it working :guitar: . Check this out: [ Audio Jack Sense on HP Notebooks](http://punischdude.kilu.de/?p=7)

---

### Post by scorp123 on 2007-11-17
> **EXCiD3 said:**
>  Please post your results of Gutsy if you decide to try it. I am not officially supporting Gutsy until it has become more stable. Sorry to disappoint, but Fiesty has much better quality support, even if it takes a bit longer to configure :( I so totally second that. Up there I wrote that "Gutsy works if you leave everything 'as is' ...." -- Well ... nope, it doesn't. At least not 100% ... maybe 90% at max. There are still a few ugly glitches you need to fix. Example: After suspend or hibernate I noticed that my network interfaces will not come back anymore, even though "Network Manager" is showing that it has 100% WiFi signal strength ... but there just  isn't any connection any more. I can "ping" around as long as I want, all interfaces are dead, regardless of what "Network Manager" claims. So I used my workaround for Feisty (see my posting above) and modified the "MODULES=" line again in **/etc/default/acpi-support** ... So now it again says [COLOR="Red"]MODULES="ipw3945"[/COLOR] as in my "Feisty" example above. This seems to have helped. But it takes a few second to have the connection re-established whereas in "Feisty" this works almost instantly.

There are many other strange things in "Gutsy". I mean .... why change things that worked OK in "Feisty"? "If it ain't broken, don't fix it ... " as the saying goes. Would be cool if the Ubuntu developers adhered to that principle.

---

### Post by skinnie on 2007-11-20
HI guys,I am running ubuntu gusty and all things that I need work (webcam,sound,buttons,touchpad,etc) but when I try to send a pic from my sharp 903 to my pc via bluetooth the things just cancels the receipt..I tried some options in the bluetooth icon,but none work..any suggestion?

---

### Post by HalphaZ on 2007-11-21
Ricoh webcam still not working even with appropiate drivers!!! 


Hi...
I've a big problem. big big problem.
First of all, presentations:

uname -a
```

stefano@stefano-laptop:~$ uname -a
Linux stefano-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

lsusb
```

stefano@stefano-laptop:~$ lsusb
Bus 001 Device 004: ID 0518:0005 EzKEY Corp. 
Bus 001 Device 005: ID 062a:0201 Creative Labs 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 05ca:1810 Ricoh Co., Ltd   <-- bad bad bad device...
Bus 002 Device 001: ID 0000:0000  
stefano@stefano-laptop:~$
```


from [http://download.tuxfamily.org/arakhn...22-14-generic/](http://download.tuxfamily.org/arakhn...22-14-generic/) I downloaded this file: ricoh-webcam-r5u870-2.6.22-14-generic_0.10.0-4_i386.deb and I saved it into the desktop. I double-clicked it and a window said that all dependencies were ok. So I installed this .deb and I restarted.

Camorama says me "unable to capture image" and closes. Before of this the blue led near the camera lights up for a while.

aMSN isn't able of doing something... just an error window...

Kopete makes his windows appear, but is unusable and uses 100% of my CPU, so I've to kill him (before installing this driver, kopete worked properly).

gqcam
```

stefano@stefano-laptop:~$ gqcam -v /dev/video0 
Segmentation fault (core dumped)
```

my dmesg | grep -i r5:
```
stefano@stefano-laptop:~$ dmesg | grep -i r5
[   18.056000] usbcam: registering driver r5u870 0.10.0
[   18.056000] r5u870-0: Detected HP Pavilion Webcam
[   18.224000] usbcore: registered new interface driver r5u870
[   79.216000] r5u870-0: set_format: fmtidx:1 frameidx:1 640x480 ival:500000
[  199.100000] r5u870-0: set_format: fmtidx:1 frameidx:4 320x240 ival:500000
[  321.552000] r5u870-0: set_format: fmtidx:1 frameidx:1 640x480 ival:500000
[ 2261.548000] r5u870-0: could not set altsetting: -110
[ 2262.948000] r5u870-0: warning: short frame (exp:614400 got:477131)
[ 2351.584000] r5u870-0: uvc_req 01/0200/0200 failed: -110
[ 2762.676000] r5u870-0: uvc_req 01/0200/0200 failed: -110
stefano@stefano-laptop:~$
```

I need help... please...

(I'm not english... sorry for my language's mistakes...)

---

### Post by UpSignal on 2007-12-02
Hello, i have a notebook Hp pavilion 6680 (Dv6000 series), and i can't boot using your methods. it gives me this error:

> /bin/sh: can't access tty; job control is turned off
(initramfs)

Previously i had version 7.10 but i couldn't get my sound working, so i decided to format and go to 7.04. And i can't boot! please help!

edit: tried this method once:

> Select  safe mode, hit F6 and add the option: "all_generic_ide" right before "quiet splash"

i sucefully installed ubuntu in safe mode ( had a hard time, since the graphics were ugly and i could hardly push the buttons "next" and so on.. )
so, when i got to desktop ( yep, no sound yet.. ) , i did all the ubuntu updates. when i reboot, it just freezes on a black screen. So , i suppose installing ubuntu this way, it's not a good solution. any ideas

---

### Post by EXCiD3 on 2007-12-02
Yes for anyone with tty job control problems please read this: [http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control](http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control)

---

### Post by Newbie1978 on 2007-12-04
Hello, I try again unsuccessfully to install Linux Ubuntu in my HP dv 6660SE, this time I use Ubuntu 7.10 Gusty, first I get a message "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I hit continue soon after I get "error microcode bcm43xx_microcode5.fw not available" some other time after the "UBUNTU IS RUNNING IN LOW GRAPHICS MODE" I try to configure the drivers for the graphics card and the screens with the same result and the same error message "error microcode bcm43xx_microcode5.fw not available" I think the problem is the graphic card, Please help me at this point I only have Linux at work, does anyone knows if this directions will work for me? I have an HP Pavilion dv6660SE this are my specs HP Pavilion Entertainment-center notebook PC 64-bit 1.9 GHz AMD Turion 64 X2 TL-58 processor, 250 GB hard drive, 2 GB RAM Nvidia GeForce Go 7150 graphics. Thank you

---

### Post by EXCiD3 on 2007-12-04
I would recommend using 7.04 Feisty instead of Gutsy. There are an unknown amount of problems when installing/running Gutsy. Almost all the problems you should encounter when installing Feisty on your laptop have already been found and fixed.

---

### Post by Newbie1978 on 2007-12-04
I downloaded the alternate CD for AMD 64 bit, I will try it tonight hoping it will work, I don't like the idea of being stuck in Windows, plus I love Linux

---

### Post by EXCiD3 on 2007-12-04
Good luck! Contact me over IM if you have any problems.

---

### Post by colomob on 2007-12-05
i try putting the code in the GRUB menu but it satill dosent work..on the second loading screen it just freezes..how can i resolve that. am trying to dual boot  it with XP.i have a HP pavillion dv6000

---

### Post by EXCiD3 on 2007-12-05
Post your /boot/grub/menu.lst and what locations/drives Windows and Ubuntu are installed on

---

### Post by DizzyTech on 2007-12-05
On my new HP dv6654us, everything works fine out of box (using LiveCD now), even wireless.  However, Compiz doesn't work.  Videos work very well.

On start, Compiz gives the following info (causing the Appearance applet to give me the Effects could not be started error):```

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

```

On a whim, I skipped the checks and Compiz worked beautifully, although video didn't work in anything.  Output is as follows:```

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

This is an HP laptop with Intel Dual Core, Intel Graphics X3100.

---

### Post by Newbie1978 on 2007-12-06
Hey! I use to have that same laptop and "noapic" work for me, when you get the first Ubuntu screen in the live CD press F6 and then type "noapic" without the quotes at the end of the line then enter

---

### Post by ozzyprv on 2007-12-10
After spending the whole day reading, I got my wireless card to work.

That is until I rebooted. 

I followed this guide: [https://help.ubuntu.com/community/Wi...bcm43xx/Feisty](https://help.ubuntu.com/community/Wi...bcm43xx/Feisty)  section 1.3
Wireless worked perfectly until I restarted the laptop. I went to the terminal and check with iwconfig, nothing (no wireless extensions).

I got the card to work by going into the terminal and running "sudo modprobe bcm43xx"

Do I have to do that every time I reboot?

And even after "sudo modprobe bcm43xx" I got an error:
"Message from syslogd@xxxx at Mon Dec 10 ...
machinename kernel: [ 229.146442] Disabling IRQ #7

Please help. Thanks.

---

### Post by scorp123 on 2007-12-10
> **ozzyprv said:**
>  I got the card to work by going into the terminal and running "sudo modprobe bcm43xx" ....  Do I have to do that every time I reboot? Modify your **/etc/modules** file so that the module gets loaded automatically upon boot, e.g. :
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

bcm43xx
```

> **ozzyprv said:**
>  And even after "sudo modprobe bcm43xx" I got an error:
"Message from syslogd@xxxx at Mon Dec 10 ...
machinename kernel: [ 229.146442] Disabling IRQ #7  Hmmm ... Does anything stop to work after that? If everything continues to work I'd say you can ignore this error.

---

### Post by Jeff_From_VA on 2007-12-10
> **ozzyprv said:**
> After spending the whole day reading, I got my wireless card to work.

That is until I rebooted. 

I followed this guide: [https://help.ubuntu.com/community/Wi...bcm43xx/Feisty](https://help.ubuntu.com/community/Wi...bcm43xx/Feisty)  section 1.3
Wireless worked perfectly until I restarted the laptop. I went to the terminal and check with iwconfig, nothing (no wireless extensions).

I got the card to work by going into the terminal and running "sudo modprobe bcm43xx"

Do I have to do that every time I reboot?

And even after "sudo modprobe bcm43xx" I got an error:
"Message from syslogd@xxxx at Mon Dec 10 ...
machinename kernel: [ 229.146442] Disabling IRQ #7

Please help. Thanks.

If you would like it to load at boot, add it to /etc/modules

I don't know how to fix the error you get.

---

### Post by ozzyprv on 2007-12-11
Ok, I fix the problem, now my wireless card loads at start-up.
I added "bcm43xx" to /etc/modules

But I keep having the error message when using my terminal (see below).

> 
"Message from syslogd@Mybox at Mon Dec 10 21:58:47 2007
Mybox kernel: [   229.146442] Disabling IRQ #7


or
> 
"Message from syslogd@Mybox at Mon Dec 10 21:58:47 2007
Mybox kernel: [   197.251709] Disabling IRQ #7


---

### Post by marcellosales on 2007-12-12
Although my BIOS displays 4GB, I don't have it complete on my dv9500... Any suggestions? Went to other forums, but there's no Memory Ramap option on the BIOS...

cat /proc/meminfo

MemTotal:      3106960 kB
MemFree:       2085408 kB
Buffers:        116004 kB
Cached:         410948 kB
SwapCached:          0 kB
Active:         567816 kB
Inactive:       364720 kB
HighTotal:     2227008 kB
HighFree:      1395296 kB
LowTotal:       879952 kB
LowFree:        690112 kB
SwapTotal:     2931852 kB
SwapFree:      2931852 kB
Dirty:             176 kB
Writeback:           0 kB
AnonPages:      405576 kB
Mapped:          86112 kB
Slab:            56636 kB
SReclaimable:    40844 kB
SUnreclaim:      15792 kB
PageTables:       2840 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   4485332 kB
Committed_AS:   938328 kB
VmallocTotal:   114680 kB
VmallocUsed:     44764 kB
VmallocChunk:    63988 kB

---

### Post by scorp123 on 2007-12-12
> **marcellosales said:**
> Although my BIOS displays 4GB, I don't have it complete on my dv9500... Any suggestions?  Are you using the 64-bit version of Ubuntu or the 32-bit one? 32-bit OS'es can't address more than 4 GB of RAM and depending on the BIOS you won't even get the full 4 GB but only around 3 GB.

Guessing from your output I guess you have the 32-bit version of Ubuntu installed?

---

### Post by marcellosales on 2007-12-12
> **scorp123 said:**
> Are you using the 64-bit version of Ubuntu or the 32-bit one? 32-bit OS'es can't address more than 4 GB of RAM and depending on the BIOS you won't even get the full 4 GB but only around 3 GB.

Guessing from your output I guess you have the 32-bit version of Ubuntu installed?

You're right... I forgot about this detail... I had installed the 32-bit version because I couldn't have U7.06 installed, then as I had read the thread that 7.10 was not good, I gave it a try with the 32-bit and everything is working...  The problem is that I had configured this machine (all the drivers, Compix Fusion, AWN, etc...) and I don't want to do everything again... Is there a way to keep the profile/driver's information some how?

The BIOS lists 4GB of memory... So it's ok with that... It came with Vista 32bit too, and they did not warn me about the memory loss...

Any suggestions regarding the upgrade Ubuntu 32->64?

Thanks!

---

### Post by EXCiD3 on 2007-12-12
I think you will have to do a fresh install in order to have a 64bit install.

---

### Post by scorp123 on 2007-12-12
> **marcellosales said:**
>   The problem is that I had configured this machine (all the drivers, Compix Fusion, AWN, etc...) and I don't want to do everything again... Is there a way to keep the profile/driver's information some how? Backup your /home e.g. to DVD or to an external USB harddisk ... and when you're done with the reinstallation, copy everything back again. If you have your /home on a separate partition then it gets even easier, just make sure your /home partition doesn't get overwritten during the installation (best thing here probably is to select "Manual Partitioning" during the installation and then make sure the installer gets it right and doesn't overwrite /home) ... and after the installation is done you should still have all your settings (which is the point why a having a separate /home partition is highly recommended).

---

### Post by Newbie1978 on 2007-12-12
This is the answer to all my prays, I use this guide and it works just fine, just download the alternate CD amd 64 ubuntu 7.10 gusty and thats it, my HP Pavilion DV 6660SE is working great, go ahead and follow this guide.

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by JDogHerman on 2007-12-13
Alright Im having a problem with this install and the guys on the IRC said I should give the fourms a try.

I am trying to install Ubuntu 7.10 on my HP DV9407.

I was following the instructions on the original starting post but I run into a problem.


I have installed the OS but when I try to boot into it from the GRUB It freezes with a white screen the does a white screen fade over 15 sec.

I have tried passing the commands that I used for the install and it doesn't seem to pass thoes commands to the start command. (FYI I use the e command on grub to edit the start line an change the splash command and 2 other blank commands tonoapic irqpoll noirqdebug on 3 lines, and I do put a space before typing the command.

I really would like to get this going, thanks guys and girls.

---

### Post by EXCiD3 on 2007-12-13
Can you post the specs (hardware) of your laptop?

I would also recommend NOT using Gutsy...Feisty has much better support even though it may take a bit more configuration.

---

### Post by JDogHerman on 2007-12-13
Processor: AMD Athlon 64 X2 Processor TK-53 1.7 GHz
Installed Memory:	2 GB
Total Hard Drive Capacity:	120 GB
Drive Controllers:	SATA-150
Rotational Speed:	5400 RPM

Video Chipset NVIDIA GeForce Go 6150

---

### Post by ozzyprv on 2007-12-15
I cannot access a Memory Stick Pro inserted in the Media Card Reader.
I see the peripheral with lspci, that is about it.

HP dv9005ca, Ubuntu 7.04

Any help please?

Thanks.

---

### Post by menonfire12 on 2007-12-16
I've a HP dv9500t and my dvdrom doesn't work, it says:

Unable to mount the selected volume.
mount: special device /dev/hda does not exist

:confused:

Plus others things maybe you solve then on that tutorial but first things first i solved the Nvidia problem and now this is the next, i hope i find the answer because i haven't seen that problem in any forum :(

---

### Post by PsychedelicReaction on 2007-12-16
> **ozzyprv said:**
> I cannot access a Memory Stick Pro inserted in the Media Card Reader.
I see the peripheral with lspci, that is about it.

HP dv9005ca, Ubuntu 7.04

Any help please?

Thanks.

Maybe are not supported yet by ubuntu. For example SD works fine to me but MicroSD are not recognized.

---

### Post by scorp123 on 2007-12-16
> **PsychedelicReaction said:**
> Maybe are not supported yet by ubuntu. For example SD works fine to me but MicroSD are not recognized. Here all my cards (SD, MicroSD, MemoryStick, etc.) work tip top. Maybe your card has some Windows DRM stuff on it and Linux can't read it. I have had that with some "MagicGate" enabled Sony MemorySticks and some SD cards. Did you try what happens if you try to format those cards / sticks on Linux? Attention: You will lose data if you do that! So it's probably best if you try that with a card that isn't holding any important information and/or make a backup beforehand. Usually after a format on Linux the card will work both on Linux and Windows (make sure you use the Microsoft "FAT" filesystem).

---

### Post by ozzyprv on 2007-12-16
> **scorp123 said:**
> Here all my cards (SD, MicroSD, MemoryStick, etc.) work tip top. Maybe your card has some Windows DRM stuff on it and Linux can't read it. I have had that with some "MagicGate" enabled Sony MemorySticks and some SD cards. Did you try what happens if you try to format those cards / sticks on Linux? Attention: You will lose data if you do that! So it's probably best if you try that with a card that isn't holding any important information and/or make a backup beforehand. Usually after a format on Linux the card will work both on Linux and Windows (make sure you use the Microsoft "FAT" filesystem).

I could try that. The only problem is that I do not even "see" the media. It does not show at /media

O.

---

### Post by scorp123 on 2007-12-17
> **ozzyprv said:**
> The only problem is that I do not even "see" the media. It does not show at /media  That's only relevant for mounting ... not for formatting. But hold on, when you say you don't "see" the card ... did you ever check what the system says about this issue? Here is how: Open a terminal (e.g. "gnome-terminal", "xterm", or whatever) and leave it open. Then insert the SD card into the card reader ... there should be some reaction to that, e.g. the card reader's LED should start to blink. When this happens type this command into the terminal:  **dmesg**

That's short for "daemon messages"; and before anyone thinks we're into satanism or something: "daemon" stands for **D**isk **A**nd **E**xecution **Mon**itor ... so "dmesg" will spit out all the things those background programs monitoring your system have to say. The output from "dmesg" might be rather long because all its messages go all the way back to the system boot; what would be interesting here are the last couple of lines because those will likely be about what it has to say about your SD card. Copy & paste that here please.

---

### Post by PsychedelicReaction on 2007-12-17
Uhm i've tried but nothing happens to dmesg after inserting the MicroSD. Mine has been formatted by Nokia itself cause it's the one i got with my 6680, i don't think it contains DRM.

---

### Post by rootware on 2007-12-23
Greetings,

I have a problem with my laptop: I have installed Ubuntu 7.10 from the live cd, and everything was ok. 

**After reboot it failed to load** Ubuntu. **It freezes **showing that i must complain to my vendor about changing the mac into a random one, and it shows also a memory error. 

It's a dual boot with windows vista, which works perfect.

What I ve** tried and failed**:

parameters on grub: **noapi, nolapi, irqpool, noirqdebug** -> they all failed to boot the system. I also removed the splash option.

Tried to install from the text-based installation CD, it does the same. 

Tried the 64 bit version...the same.

What can I do? _I'm desperate!_ :(

My hardware:

NB **HP PAVILION DV9645ED**, 17'' (WXGA+), **Turion64 X2 TL-58 1.9GHz**, NVIDIA GF 8400M GS, 2GB DDR2, 160GB, DVD+/ -RW DL LIGHT SCRIBE, 56K, LAN, WIR, CARD READER, CAMERA, WIN VISTA HOME PREMIUM

Note: I can't access any tty, it shows only a cursor :(

---

### Post by fredwbauer on 2007-12-23
rootware,

I've had lots of trouble running Linux on this beast, too.
The boot (grub) option acpi=off will at least get you booted.

I've tried lots of boot options including:
acpi_osi="!Linux" (no effect)
acpi_os_name="Windows 2006" (no effect)
noapic (ofter works)
different vga modes (vga=ask)
irqpoll
pci=conf1
pci=conf2 (wont boot)
smp=off (wont boot)
agp=off (no effect)

Nothing seems to give me a reliable system with everything working.

---

### Post by rootware on 2007-12-23
So, can anyone help us? :(

---

### Post by Newbie1978 on 2007-12-23
Hello! just download the alternate CD amd 64 (no live CD) ubuntu 7.10 gusty and thats it, my HP Pavilion DV 6660SE work great, go ahead and follow the text base installation.

---

### Post by rootware on 2007-12-24
Tried the alternate cd textmode install but sometimes it freeze and sometimes can boot!
Here are my messages and my dmesg files:

Dmesg: [http://www.geocities.com/invizibilperadar/dmesg.txt](http://www.geocities.com/invizibilperadar/dmesg.txt)

Messages: [http://www.geocities.com/invizibilperadar/messages.txt](http://www.geocities.com/invizibilperadar/messages.txt)

---

### Post by rootware on 2007-12-24
anyone? :(

---

### Post by rootware on 2007-12-25
> **rootware said:**
> Greetings,

I have a problem with my laptop: I have installed Ubuntu 7.10 from the live cd, and everything was ok. 

**After reboot it failed to load** Ubuntu. **It freezes **showing that i must complain to my vendor about changing the mac into a random one, and it shows also a memory error. 

It's a dual boot with windows vista, which works perfect.

What I ve** tried and failed**:

parameters on grub: **noapi, nolapi, irqpool, noirqdebug** -> they all failed to boot the system. I also removed the splash option.

Tried to install from the text-based installation CD, it does the same. 

Tried the 64 bit version...the same.

What can I do? _I'm desperate!_ :(

My hardware:

NB **HP PAVILION DV9645ED**, 17'' (WXGA+), **Turion64 X2 TL-58 1.9GHz**, NVIDIA GF 8400M GS, 2GB DDR2, 160GB, DVD+/ -RW DL LIGHT SCRIBE, 56K, LAN, WIR, CARD READER, CAMERA, WIN VISTA HOME PREMIUM

Note: I can't access any tty, it shows only a cursor :(


> **rootware said:**
> Tried the alternate cd textmode install but sometimes it freeze and sometimes can boot!
Here are my messages and my dmesg files:

Dmesg: [http://www.geocities.com/invizibilperadar/dmesg.txt](http://www.geocities.com/invizibilperadar/dmesg.txt)

Messages: [http://www.geocities.com/invizibilperadar/messages.txt](http://www.geocities.com/invizibilperadar/messages.txt)




Tried the server version, but comes with no-GUI ](*,) This version can boot with noapic option.

What can I do to boot the desktop version? ](*,)

---

### Post by rootware on 2007-12-25
And Merry Christmas everyone!

---

### Post by scorp123 on 2007-12-25
> **rootware said:**
> Tried the server version, but comes with no-GUI ](*,) This version can boot with noapic option. And why do you need the "noapic" option?

---

### Post by EXCiD3 on 2007-12-25
If the server version worked you can do```
sudo apt-get install kubuntu-desktop
``` and that will install the default KDE desktop environment for you. 

You could also try using Feisty instead: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by rootware on 2007-12-25
> **scorp123 said:**
> And why do you need the "noapic" option?

Cos it says so! Says it can't boot and suggests that I should use that option :confused:

---

### Post by EXCiD3 on 2007-12-25
Are you following this tutorial using a Gutsy disc? This tutorial is written for Feisty, not Gutsy. Lots of changes have been made and Gutsy does not require the same steps. As I recall you should not need to modify the boot parameters for Gutsy.

---

### Post by rootware on 2007-12-25
> **EXCiD3 said:**
> Are you following this tutorial using a Gutsy disc? This tutorial is written for Feisty, not Gutsy. Lots of changes have been made and Gutsy does not require the same steps. As I recall you should not need to modify the boot parameters for Gutsy.

Oh, my bad. Now I downloaded the Feisty disk, and I am try to install envy.

wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb)

sudo dpkg -i envy_0.8.1-0ubuntu6_all.deb # here I got the error: 

>  package python 2.4 is not installed
dpkg: error processing envy
dependency problems - leaving unconfigured
Errors were encountered while processing:
envy

What should I do? I tried apt-get install python and it says that's already the latest version installed .

---

### Post by EXCiD3 on 2007-12-25
wait, first you should download the newest version of envy, which is version 0.9.9 anyways: [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu3_all.deb)

cd to the directory you downloaded this too...probably ~/Desktop
```
sudo dpkg -i envy_0.9.9-0ubuntu3_all.deb
sudo apt-get install -f
sudo dpkg -i envy_0.9.9-0ubuntu3_all.deb
```

that should do the trick. basically the first dpkg notifies the os that there are dependencies that you dont have. sudo apt-get install -f downloads and installs them so that the next time you use dpkg on the .deb it will have the necessary dependencies to install/run. Good luck!

---

### Post by slick_8199 on 2007-12-29
Thank you for the how-to. I have a hp pavilion dv9535nr and this helped a lot. The sound did not work for me out of the box. I had to update alsa to the newest version I think it is 1.0.15 and it seems to work ok. i still have problems with the headphone jacks though. If I plug in it mutes the laptop speakers but if you turn up the volume it will unmute them. If anyone has any sugestions on this please let me know.

---

### Post by slkwcy on 2007-12-30
First, I like to thanks EXCiD3 for posting a how-to for HP laptop.

I was first installed Gutsy to my wife's Sony Laptop (about 2 years old), and it was installed so smoothly everything just work right out of the box.

Then when I started to install Gutsy to my HP laptop (dv9005) things are starting to be challenging.  

Anyways, I am so happy that I like to report that my suspend and hibernate are now working, with no option added to the boot menu (menu.lst).  \\:D/

I only have to add "NvAGP" "1" in xorg.conf as an option under device.

But in order to be able to boot into LiveCD for fresh installation, noapic still required I believe.

---

### Post by EXCiD3 on 2007-12-31
I would like to let everyone know that the Zen Kernel fixes important bugs related to the AMD based HP Laptops. I strongly encourage anyone interested in fixing these problems take a look at the Zen Kernel here: [http://ubuntuforums.org/showthread.php?t=623874](http://ubuntuforums.org/showthread.php?t=623874)

[B]Important Information: 
[/B]-Kernel fix for the nolapic issue...it's a patch that disables C1E on AMD machines, which is causing the kernel to incorrectly report lapic is broken. This allows us (with newer custom kernels like zen) to use High Res Timers and Dynamic Ticks. 

On kernels without this patch, reported to work on the dv9205us, without disabling lapic (even though it is broken without C1E disabled):
```
noisapnp iommu=off noirqdebug noapic pci=assign-busses
```
The patch can be found here (may have to mod it to work depending on which kernel source you are using):
[http://tinyurl.com/ytyhfe](http://tinyurl.com/ytyhfe)

This fix allows you to boot without using nolapic, fully enabling nolapic. If you have a kernel like Zen, you can use the features Dynamic Ticks and High Resolution timers, which should increase both speed and battery life. The boot parameters I posted allow you to do the same with older kernels without patching, without high resolution timers and dynamic ticks, as they are experimental features added in the newest bleeding edge kernels.

Much thanks to ilikenwf, Official Zen Kernel Maintainer!!!

---

### Post by jppranker on 2008-01-01
hello all after 33 pages I have a question. My laptop is a hp pavilion9000 tk-53 2 gig ram with 120gig hd and nivida go 7150. I intstalled kubuntu 7.10 by using safe graphics mode to start and then clicking install once the live cd booted. I realize after reading that I should have did it differnently but here is what happens. It will start to boot I get just a littel splash bar loading and it just sits there. I was wonder should I just start over download alternate cd or it there a way to get past this point. I am using live cd amd 64bit. Would it be better to go back to 7.04  which I do not see in the download list. I see 6.06 dapper. Advice would be great. I am working with mty spare hd removed my vista drive. So no dual booting or anything that I worried about losing. THanks JP

---

### Post by EXCiD3 on 2008-01-01
Yes I would recommend downloading Feisty 7.04 and using it over Gutsy 7.10. Any release of Ubuntu (including Feisty 7.04) can be downloaded here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by chriswyatt on 2008-01-02
I'm using a Pavilion DV2058ea using the realtime kernel and I'm having problems installing the Microdia drivers:

```
chrisw@chrisw-laptop:~/trunk$ make
Building USB Video Class driver...
cd: 1: can't cd to /lib/modules/2.6.22-14-rt/build
make: *** [uvcvideo] Error 2
chrisw@chrisw-laptop:~/trunk$ sudo make install
Installing USB Video Class driver...
cd: 1: can't cd to /lib/modules/2.6.22-14-rt/build
make: *** [install] Error 2
chrisw@chrisw-laptop:~/trunk$ sudo make install
Installing USB Video Class driver...
make[1]: Entering directory `/lib/modules/2.6.22-14-rt/build'
make[1]: *** No rule to make target `modules_install'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.22-14-rt/build'
make: *** [install] Error 2

```

The second time I did a make install I tried creating a blank directory called 'build'.  Could this be something to do with the realtime kernel, I'm kind of a n00b so I'm a bit stuck with this really.

---

### Post by chicobo329 on 2008-01-09
I had a problem installing the latest Linux version on my dv2000. I'm about to try putting in 7.04 now. I ran into a few problems: no sound, no wireless connection, and a strange 'PCI BIOS BUG' which 50% of the time causes the screen to completely white out until I restart the computer! I can guess the sound and wireless can be fixed properly with this howto, but does anybody know about this PCI BIOS BUG?

---

### Post by EXCiD3 on 2008-01-09
[SIZE=-1]I would like everyone to know that I have created a new thread for testing Hardy 8.04 prerelease on HP and Compaq laptops. If you have tried or are going to try out a prerelease of Hardy, please post any information you have here: [http://ubuntuforums.org/showthread.php?t=660384](http://ubuntuforums.org/showthread.php?t=660384)[/SIZE]

---

### Post by scorp123 on 2008-01-10
BTW: I noticed that the latest BIOS upgrades from HP seem to disable the multimedia keys under Linux (while changing some functions so that they'd work under Vista .... but who uses Vista anyway??). I had to *downgrade* the BIOS for my dv2108ea again.

---

### Post by A Pragmaticist on 2008-01-10
Hail,

First of all thank you for the instructions and information about setting up Ubuntu for HP laptops.

Second of all I am a complete newbie.

As per instruction, I used the alternate cd for 7.04 and was able to set up Ubuntu with a dual boot.  My partitioning went a little weird because I think I could not figure out how to do sdb, so I used sda3 to partition Ubuntu, if I remember correctly...if anyone could help me figure out for sure how it's configured, I would appreciate it since I cannot exactly recall.

I did not do anything with drivers after I got to the desktop.  Since then I have been using it for a couple weeks and have also been quite lazy about doing anything, as I was able to use pidgin and surf the net; my wireless does not yet work, but I do not care enough to do anything as I just plugged the laptop directly for now.

However, I now have a big problem when I turn on the comp.  As usual, I select which kernel to load.  Then it goes to the Ubuntu bar to show that it's loading, but then it does not finish and instead of going to the desktop, it goes to DOS-type screen.  This is basically what it says:

Loading hardware devices...
firmware_helper [3696]: main: error loading '/lib/firmware/bcm43xx_microcode.fw' for device '/class/firmware/0000:03:00.0' with driver 'unknown'
firmware_helper [3805]: main: error loading '/lib/firmware/bcm43xx_microcode.fw' for device '/class/firmware/0000:03:00.0' with driver 'unknown'
firmware_helper [3815]: main: error loading '/lib/firmware/bcm43xx_microcode.fw' for device '/class/firmware/0000:03:00.0' with driver 'unkown'
Loading kernel modules
Loading manual drivers
Activating swap
Checking root file system...
fsck 1.40-WIP (14-Nov-2006)
/dev/sda3 has been mounted 30 times without being checked, check forced.
firmware_helper[4103]: main: error loading '/lib/firmware/bcm43xx_microcode.fw' for device '/class/firmware/0000:03:00.0' with driver 'unknown'
[  54.216000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

After all that, it then ends with "/dev/sda3: |====" and a percentage at the end, and the percent is different every time I attempt to load up the comp.

It seems to me that it has something to do with the forced check, which I didn't even know would happen, and I think that is the reason this has started happening.  If anyone has suggestions on what I should do, even if just start from scratch again with Ubuntu  and not be so lazy the second time around, I would appreciate them.

I have an HP Pavilion dv6000 (dv6436nr) Entertainment Notebook PC
AMD Turion 64x2
NVIDIA GeForce Go 6150
Broadcom wireless

Not sure what else info to give, or even probably how to get it, but just let me know if there is anything else you need to know (and how I should get the info).

I came here since I know this is the place to go for HP laptop issues.

Thank you.

Edit: Okay, this is a bit more of what the comp says and the end is different now, I know not why.

* Reading files needed to boot...                                                [OK]
* Setting preliminary keymap...                                                   [OK]
* Preparing restricted drivers...                                                  [OK]
* Starting basic networking...                                                      [OK]
* Starting kernel event manager...                                              [OK]
* Loading hardware drivers...
error receiving uevent message: No buffer space available
firmware_helper [3705]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
firmware_helper [3776]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
firmware_helper [3786]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
                                                                                                       [OK]
* Loading kernel modules...
* Loading manual drivers...                                                           [OK]
* Activating swap...                                                                       [OK]
* Checking root file system...
fsck 1.40-WIP (14-Nov-2006)
/dev/sda3 has been mounted 30 times without being checked, check forced.
/dev/sda3 |===================                                  / 34.4%

Everything is the same with all of it except the numbers for each firmware helper, the number of the percent at the end, the last error no longer appears (i.e., the error that says the microcode is not available or load failed); and I am not sure about the "no buffer space available", I might have missed that before.

Also, my kernel number is 2.6.20-16-generic, if that helps at all.

---

### Post by dimmubodom84 on 2008-01-13
I'm also new to Ubuntu, I want to install Ubuntu 7.04 Desktop AMD64. But I am not sure if this howto would help. I just bought  an Hp Pavilion dv9607us Notebook PC and just wanted to know if anyone has the same computer and has ubuntu running with no problems? This computer came with Vista and I really hate it, can't wait to get rid of it. My computer specs are:

**Product Number **	GS726UA#ABA
**Microprocessor **	1.7 GHz AMD Athlon 64 X2 Dual-Core Mobile Technology TK-53
**Microprocessor Cache **	512KB L2 Cache
**Memory **	1024 MB (2 x 512 MB)
**Memory Max **	Up to 4 GB
**Video Graphics** 	NVIDIA GeForce Go 7150M
**Video Memory **	Up to 559 MB
**Hard Drive** 	120 GB (5400 rpm)
**Multimedia Drive** 	SuperMulti 8X DVD±R/RW with Double Layer Support
**Display** 	17.0" WXGA+ High-Definition BrightView Widescreen Display (1440 x 900)
**Fax/Modem** 	High speed 56K modem
**Network Card **	Integrated 10/100BASE-T Ethernet LAN
**Wireless Connectivity** 	802.11b/g WLAN
**Sound** 	Altec Lansing speakers
**Keyboard **	101-key compatible with scroll bar and integrated numeric keypad; 2 Quick Launch Buttons-HP Quick Play
**Pointing Device **	Touch Pad with On/Off button and dedicated vertical and horizontal Scroll Up/Down pad
**PC Card Slots **		One ExpressCard/54 slot (also supports ExpressCard/34) 
**External Ports** 		5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards 
•	4 Universal Serial Bus (USB) 2.0 
•	1 Headphone out w/SPDIF Digital Audio 
•	1 microphone-in 
•	1 VGA (15-pin) 
•	1 TV-Out (S-video) 
•	1 RJ-11 (modem) 
•	1 RJ -45 (LAN) 
•	1 notebook expansion port 3 
•	1 IEEE 1394 Firewire (4-pin) 
•	1 Consumer IR 

Also came with a control.

I did install ubunto 7.04 but when i turn it on everything seems to big, I went to system>Preferences>Screen Resolution to try to fix the problem but it doesn't give me the option 1440x900. I only get 800x600 & 640x480. please help. I also tried to find drivers for the Nvidia Geforce go 7150m but found nothing. and did anyone manage to get the wireless working?

---

### Post by EXCiD3 on 2008-01-13
*[I]A Pragmaticist, *[/I]I'm not sure what would be causing that, however it is failing to finish checking your hard drive parittion for errors. This could be a bug with the partition, or with fsck itself. Reinstalling and wiping that parition might fix your problem.

dimmubodom84, you are going to need to install the nvidia drivers to get the correct resolution. Download and install the drivers using Envy as stated in the tutorial: [http://www[SIZE=-1].albertomilone.com/nvidia_scripts1.html[/SIZE]]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by dimmubodom84 on 2008-01-13
**[SIZE="4"]HELP!!![/SIZE]**
Ive been trying to install the drivers for the NVIDIA GeForce Go 7150M but haven't had luck with it I went to

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I have tried many times and i just keep getting an error saying:

*"Envy Error: Envy does not recognise your card as compatible with any version of the driver. this might happen because either your card is not supported by the driver or envy's hardwaredetection failed. you can try the manual installation at your risk."*

But when i do it manually I get a blue screen when rebooting can someone help me please

M I supposed to be doing something else?

---

### Post by EXCiD3 on 2008-01-13
Interesting...so how new is your laptop? I cant imagine the 7150M not being supported by the nvidia driver...have you checked around on the forums in other places?

---

### Post by dimmubodom84 on 2008-01-13
Yes and Can't find anything :( I guess I shouldn't have switched to Ubuntu yet.

but vista was getting on my nerves i was desperate! lol

I can't find anything on the NVIDIA Geforce Go 7150M.

Im not sure how new the laptop is but i was also having trouble finding it only, I was trying to find the price for it, lol it was a gift.


well I did find this. but its a .RUN file:

[I]HOW TO: install your Nvidia driver in Ubuntu 7.10

(Please MAKE SURE with ANY commands (or path names) that you capitalized what I capitalize!!!! This is VERY important!)

I will start by giving you two options. Both options require that you have a internet connection of some kind. (preferably high-speed)

Option #1. Install your Nvidia driver with "Envy" 
(usually MUCH easier then installing the driver the manual way)

OR

Option #2. Install your Nvidia driver manually. (use this if Envy won't work)


If you choose Option #1 "Install your Nvidia driver with "Envy"" Then please proceed from here on.

1.1 
Go to your (System>>Administration>>Software Sources) make sure you have all your repositories enabled. (Check mark them all)

Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvid...untu10_all.deb](http://albertomilone.com/ubuntu/nvid...untu10_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

1.2
Double click on the file you just downloaded and tell it to install

1.3
If all those steps went well then Envy should be installed and you should be able to find it in (Applications>>System tools), just run it and you should be able to install your driver all by your self very easily.


Option #2.

2.1
Open up a terminal window (Applications>>Accessories>>Terminal) type this in "sudo apt-get install build-essential"


2.2
In a terminal window type "lspci | grep VGA" find the part that has these around it "[ ]", write down what it says then go here 
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) 
If the name of your graphics card is in the list (such as "Geforce 6800") then download this driver to your Desktop
[http://us.download.nvidia.com/XFree8...14.19-pkg1.run](http://us.download.nvidia.com/XFree8...14.19-pkg1.run) 
(if that link is old go to this page to get driver) 
[http://www.nvidia.com/object/linux_d...100.14.19.html](http://www.nvidia.com/object/linux_d...100.14.19.html) 
(if that link is old, go here and select the driver that starts with "100")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).


(EXAMPLE 

"carl@carlubuntu1:~$ lspci | grep VGA
01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
carl@carlubuntu1:~$"

The "GeForce4 MX 420" is the name you are looking for. So "GeForce4 MX 420" is what I would look for on the list here.
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

end of example)

2.3
IF YOUR GRAPHICS CARD NAME IS NOT ON THAT LIST look and see if it's on this one
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If it was in the "The 1.0-96xx driver supports the following set of GPU" section, then download this driver to your Desktop
[http://us.download.nvidia.com/XFree8...43.01-pkg1.run](http://us.download.nvidia.com/XFree8...43.01-pkg1.run)
(If that link is old then go here)
[http://www.nvidia.com/object/linux_d..._96.43.01.html](http://www.nvidia.com/object/linux_d..._96.43.01.html)
(If that link is old go here and select the driver that starts with "96")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

[B]If you graphics card name was in the "The 1.0-71xx driver supports the following set of GPUs" section,
then download this driver to your Desktop.
[http://us.download.nvidia.com/XFree8...86.01-pkg1.run](http://us.download.nvidia.com/XFree8...86.01-pkg1.run)
(If that link is old go here)
[http://www.nvidia.com/object/linux_d..._71.86.01.html](http://www.nvidia.com/object/linux_d..._71.86.01.html)
(If that link is old go here and select the driver that starts with "71")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)[/B]


2.4
Print out this page!

2.5
Restart your computer! At the Grub boot menu (if it doesn't pop up click ESC before it's to late) and select the "recovery mode" kernel, and hit enter!

2.6
Once booted, type in "sh /home/yourusername/Desktop/NVIDIA" but DON'T HIT ENTER!!
(replace "yourusername" with your user name) 
click the TAB button on your key board twice, and it should fill out the rest of the name for you, 
THEN hit enter.

2.7
The installer will ask you some question (don't worry if it says your in "runlevel 1" it doesn't matter) just make sure you answer all the questions so that it will continue the installation process.

2.8
Once the installer is done restart your computer by pressing CTRL+ALT+DELETE, boot up normally. And your Nvidia driver should be installed!

TROUBLE SHOOTING

If you have problems installing "Envy" ether ask about it on the forums, or just do Option #2.

If (in Option #2) when you reboot you get a black screen don't worry it can be fixed!
Just press these keys ALT+F2 and then type this in at the command prompt "sudo nano -w /etc/X11/xorg.conf"
Find the part of the file that says "Device", find "Driver "nvidia"" change "nvidia" to "nv".
Press ALT+X and save the file.
Restart your computer, try installing it again, or ask about it on the forums. (When asking on the forums, error messages are VERY helpfull please write down, or copy any you get)[/I]

---

### Post by nemlah on 2008-01-16
Hello all,
Just got a HP dv9630ed, with following specs:

Intel Core 2 Duo T5250 (1.50 GHz, Level 2 cache 2MB).
 17'' WXGA BrightView, &#956;&#949; &#945;&#957;&#940;&#955;&#965;&#963;&#951; 1440 x 900.
 2 x 1024MB DDR2, &#965;&#960;&#959;&#963;&#964;&#951;&#961;&#943;&#950;&#949;&#953; &#956;&#957;&#942;&#956;&#951; &#956;&#941;&#967;&#961;&#953; 4 GB.
 120 GB SATA 5400 rpm.
 Lightscribe Super Multi DVD Writer (+/-R +/-RW) &#956;&#949; &#965;&#960;&#959;&#963;&#964;&#942;&#961;&#953;&#958;&#951; &#948;&#953;&#960;&#955;&#959;&#973; &#963;&#964;&#961;&#974;&#956;&#945;&#964;&#959;&#962;.
NVIDIA GeForce 8400M GS &#956;&#949; 128MB &#945;&#965;&#964;
Intel PRO/Wireless 3945 802.11a/b/g.

I downloaded 7.04 Install CD (AMD 64) and well i see a screen where it tell me about the screen resolution which i anticipated since i will need the binary drivers, but after i click ok, the system hangs at:

Running Local Boot Scripts [OK]

I did enter noacpi ... right after the -- after hitting f6 at the boot (did i need to add -- between all arguments?). Apparently i can use a console, and i looked at the syslog, which ... well didn't tell me much..

I appreciate any pointer into the right direction.

Regards Vasilis

---

### Post by lightningstormz on 2008-01-16
I have the dv9500t with same graphics card as you and I was able to get the 7.10 live installation disk to work by selecting the safe graphics mode option at the boot menu. Let me know if this works for you. You just have to give it time to boot (the screen stays black for a while).

---

### Post by WisdomWolf on 2008-01-19
I have a dv9000t with the following specs:

C2D T5600
100GB HD
160GB HD
G0 7600 256MB RAM
Broadcom wireless (I replaced it for OSX)
HDMI out

I have used Feisty in the past, but that was over 6 months ago, haven't touched linux on it since.  I want to use it as a media center for HD content and have found Vista horribly lacking with popping and hissing in the audio. I was going to go back to XP until I remembered that the greatest media player in the world (XBMC) was ported to linux and ubunut was recommended.

I have a few simple questions before I dive in...
How hard is it to setup the broadcom wireless?
Has anyone gotten Audio out to work with HDMI and if so how?
What would be a better choice currently (Fiesty or Gutsy or wait for Hardy)?
Has anyone tested output to an HDTV at 1080p?

Thanks for all the help in advance.

---

### Post by EXCiD3 on 2008-01-19
Glad to see your interest in ubuntu. K Here goes:

**Wireless:** Fairly easy with the tools given, if you are a linux noob, it can be quite tough.
**HDMI:** Nobody has tested it as far as I know. I havent even had an HDTV to test it out until recently, which Ive never gotten around to because I have been at college. Will try it out tonight!:)
**Version:** Feisty is your best bet currently as far as im concerned. Gusty has been known to really shaft people, and others have had better luck with gutsy (especially with broadcom) Hardy is too early to tell, all the problems ive experienced with Gutsy are fixed in the Alpha 3 release of Hardy (which im currently running)
**HDTV at 1080p: **Not as far as i know, but i will check it out tonight as soon as my dad goes to bed! I will post back later with the results!

---

### Post by EXCiD3 on 2008-01-20
Update:

**HDMI: **Works, no audio. I am not sure how to send audio out through the HDMI port. I used the Nvidia driver to configure the HDMI out, it detected my TV right away.
**HDTV at 1080p: **Output at 1920 x 1080. True 1080p resolution automatically detected by the Nvidia drivers.

HDMI Audio does not work, but probably just needs some minor configuration somewhere. I will do a little more digging and see what i can come up with. :)

---

### Post by jppranker on 2008-01-20
your video does work in linux I am using a dv9617nr which is very close to your laptop. I have the 7150 work in suse 10.3. I was just trying a different linux and was able to get everything thing working but realplayer in firefox 64. I am not saying switch I like kubuntu. I was just trying out something new. Nvidia video drivers

Search for nvidia and mark the following packages for installation:

    * nvidia-gfx-G01-kmp-default
    * x11-video-nvidiaG01

This is part of the instructions I used to get my video working look here for full instructions [http://www.softwareinreview.com/linux_optimizations/hacking_opensuse_10.3.html](http://www.softwareinreview.com/linux_optimizations/hacking_opensuse_10.3.html) Hope this helps.

> **dimmubodom84 said:**
> Yes and Can't find anything :( I guess I shouldn't have switched to Ubuntu yet.

but vista was getting on my nerves i was desperate! lol

I can't find anything on the NVIDIA Geforce Go 7150M.

Im not sure how new the laptop is but i was also having trouble finding it only, I was trying to find the price for it, lol it was a gift.


well I did find this. but its a .RUN file:

[I]HOW TO: install your Nvidia driver in Ubuntu 7.10

(Please MAKE SURE with ANY commands (or path names) that you capitalized what I capitalize!!!! This is VERY important!)

I will start by giving you two options. Both options require that you have a internet connection of some kind. (preferably high-speed)

Option #1. Install your Nvidia driver with "Envy" 
(usually MUCH easier then installing the driver the manual way)

OR

Option #2. Install your Nvidia driver manually. (use this if Envy won't work)


If you choose Option #1 "Install your Nvidia driver with "Envy"" Then please proceed from here on.

1.1 
Go to your (System>>Administration>>Software Sources) make sure you have all your repositories enabled. (Check mark them all)

Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvid...untu10_all.deb](http://albertomilone.com/ubuntu/nvid...untu10_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

1.2
Double click on the file you just downloaded and tell it to install

1.3
If all those steps went well then Envy should be installed and you should be able to find it in (Applications>>System tools), just run it and you should be able to install your driver all by your self very easily.


Option #2.

2.1
Open up a terminal window (Applications>>Accessories>>Terminal) type this in "sudo apt-get install build-essential"


2.2
In a terminal window type "lspci | grep VGA" find the part that has these around it "[ ]", write down what it says then go here 
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) 
If the name of your graphics card is in the list (such as "Geforce 6800") then download this driver to your Desktop
[http://us.download.nvidia.com/XFree8...14.19-pkg1.run](http://us.download.nvidia.com/XFree8...14.19-pkg1.run) 
(if that link is old go to this page to get driver) 
[http://www.nvidia.com/object/linux_d...100.14.19.html](http://www.nvidia.com/object/linux_d...100.14.19.html) 
(if that link is old, go here and select the driver that starts with "100")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).


(EXAMPLE 

"carl@carlubuntu1:~$ lspci | grep VGA
01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
carl@carlubuntu1:~$"

The "GeForce4 MX 420" is the name you are looking for. So "GeForce4 MX 420" is what I would look for on the list here.
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

end of example)

2.3
IF YOUR GRAPHICS CARD NAME IS NOT ON THAT LIST look and see if it's on this one
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If it was in the "The 1.0-96xx driver supports the following set of GPU" section, then download this driver to your Desktop
[http://us.download.nvidia.com/XFree8...43.01-pkg1.run](http://us.download.nvidia.com/XFree8...43.01-pkg1.run)
(If that link is old then go here)
[http://www.nvidia.com/object/linux_d..._96.43.01.html](http://www.nvidia.com/object/linux_d..._96.43.01.html)
(If that link is old go here and select the driver that starts with "96")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

[B]If you graphics card name was in the "The 1.0-71xx driver supports the following set of GPUs" section,
then download this driver to your Desktop.
[http://us.download.nvidia.com/XFree8...86.01-pkg1.run](http://us.download.nvidia.com/XFree8...86.01-pkg1.run)
(If that link is old go here)
[http://www.nvidia.com/object/linux_d..._71.86.01.html](http://www.nvidia.com/object/linux_d..._71.86.01.html)
(If that link is old go here and select the driver that starts with "71")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)[/B]


2.4
Print out this page!

2.5
Restart your computer! At the Grub boot menu (if it doesn't pop up click ESC before it's to late) and select the "recovery mode" kernel, and hit enter!

2.6
Once booted, type in "sh /home/yourusername/Desktop/NVIDIA" but DON'T HIT ENTER!!
(replace "yourusername" with your user name) 
click the TAB button on your key board twice, and it should fill out the rest of the name for you, 
THEN hit enter.

2.7
The installer will ask you some question (don't worry if it says your in "runlevel 1" it doesn't matter) just make sure you answer all the questions so that it will continue the installation process.

2.8
Once the installer is done restart your computer by pressing CTRL+ALT+DELETE, boot up normally. And your Nvidia driver should be installed!

TROUBLE SHOOTING

If you have problems installing "Envy" ether ask about it on the forums, or just do Option #2.

If (in Option #2) when you reboot you get a black screen don't worry it can be fixed!
Just press these keys ALT+F2 and then type this in at the command prompt "sudo nano -w /etc/X11/xorg.conf"
Find the part of the file that says "Device", find "Driver "nvidia"" change "nvidia" to "nv".
Press ALT+X and save the file.
Restart your computer, try installing it again, or ask about it on the forums. (When asking on the forums, error messages are VERY helpfull please write down, or copy any you get)[/I]

---

### Post by richandcreamy on 2008-01-21
I'm not 100% sure what webcam my dv9220us is using but after opening Ekiga Software and selecting  V4L2 Softphone was able to use the webcam.  I'm trying to use the webcam on [www.stickam.com](www.stickam.com) which accesses the webcam through flash but no video is displayed.

Tried searching this thread under webcam and the rest of the forum under stickam... not sure where to look next or what to test!

By the way how do I thank someone for a post?  I tried installing Ubuntu last March and gave up but with this thread and Feisty I'm writing on this forum through Ubuntu. Yay!

---

### Post by richandcreamy on 2008-01-21
Webcam not working for [http://www.woome.com](http://www.woome.com) either so I'm thinking it may be for any flash based webcam app.

---

### Post by chriswyatt on 2008-01-28
I'd love to be able to get the brightness control to work on my laptop, it's the DV2058ea, sort of worked on Feisty, doesn't work at all on Gutsy :'( .  On Feisty I had to press brightness down lots of times until there was any change in screen brightness, and there were only two states, the lowest and the highest (or highest could just be the brightness set from the BIOS, not sure).

I'd love to see this working out of the box in Hardy Heron :) .

---

### Post by MasterAslan on 2008-01-31
I am getting so frustrated.  I just can't figure out what is going on here.  When I boot up it hangs on starting bluetooth services.  By changing to tty5 and startx and then disable bluetooth.  Whenever I try lsusb it hangs.  Ndiswrapper -l and modprobe ndiswrapper hangs.  LSPCI lists the usb hardware just fine.  I just can't figure out why this all hangs.  I have tried nolapic, noapic and irqfixup and several combinations.  Is my hardware just not going to be supported here?  It is funny though bluetooth seems to actually work once I'm into X I can see my phone from it anyway.  There is something with the hardware that is just not quite right.  

Any ideas?  Wish I was a really experienced user that could do all my own debugging.

I want to use linux but I'm getting a bit exasperated.

---

### Post by EXCiD3 on 2008-01-31
> **MasterAslan said:**
> I am getting so frustrated.  I just can't figure out what is going on here.  When I boot up it hangs on starting bluetooth services.  By changing to tty5 and startx and then disable bluetooth.  Whenever I try lsusb it hangs.  Ndiswrapper -l and modprobe ndiswrapper hangs.  LSPCI lists the usb hardware just fine.  I just can't figure out why this all hangs.  I have tried nolapic, noapic and irqfixup and several combinations.  Is my hardware just not going to be supported here?  It is funny though bluetooth seems to actually work once I'm into X I can see my phone from it anyway.  There is something with the hardware that is just not quite right.  

Any ideas?  Wish I was a really experienced user that could do all my own debugging.

I want to use linux but I'm getting a bit exasperated.

Which version of ubuntu are you using?

---

### Post by MasterAslan on 2008-01-31
Tried Fiesty, Gutsy and Hardy all with the same results.

---

### Post by EXCiD3 on 2008-01-31
I'm not sure what would be causing this. Post a list of your hardware and we'll see if there is any known problems with something you might have.

---

### Post by A Pragmaticist on 2008-02-01
Heyo,

For the most part the guide worked fine for me, and I reinstalled Ubuntu as suggested; so far no more problems with booting up.

I am having an issue though with the laptop mode.  I did all that and everything was fine, but then I decided I wanted to go back to powernowd instead of using cpufreqd.  Unfortunately, that did not work out and now neither powernowd nor cpufreqd work.  I checked with my Vista dual boot and it seems that I should be able to do frequency scaling.  Here's the thread where I originally posted this problem: [http://ubuntuforums.org/showthread.php?t=672903](http://ubuntuforums.org/showthread.php?t=672903)

If I could get any help with this, that would be awesome.

---

### Post by MasterAslan on 2008-02-01
I've used PC Wizard and created an exhaustive list of info.  If anyone can take the time to take a look and give  me some tips I would be greatful.  

Thanks



```
PC Wizard 2008 Version 1.83
------------------------------------------------------------------------------------------


Operating System: Windows Vista (TM) Home Premium Home Edition 6.00.6000 
Report Date: Friday 01 February 2008 at 16:30

------------------------------------------------------------------------------------------


<<< System Summary >>>

  > Mainboard : Quanta 30DA

  > Chipset : nVidia nForce 520

  > Processor : AMD Turion 64 X2 Mobile TL-56 @ 1800 MHz

  > Physical Memory : 2048 MB (2 x 1024 DDR2-SDRAM )

  > Video Card : Nvidia Corp GeForce 8400M GS

  > Hard Disk : TOSHIBA (120 GB)

  > Hard Disk : TOSHIBA (120 GB)

  > DVD-Rom Drive : HL-DT-ST DVDRAM GSA-T20L ATA Device

  > DVD-Rom Drive : RH7065S XFX251A SCSI CdRom Device

  > Monitor Type : LGPhilipsLCD  - 17 inches

  > Network Card : Nvidia Corp MCP65 Ethernet

  > Network Card : Broadcom Corp BCM4310 UART

  > Operating System : Windows Vista (TM) Home Premium Home Edition 6.00.6000 

  > DirectX : Version 10.00

  > Windows Performance Index : 3.5

<<< Mainboard >>>

  > Manufacturer : Hewlett-Packard

    >> General Information
      Product : HP Pavilion dv9500 Notebook PC
      Version : Rev 1
      Serial Number : CNF733128S
      Unique ID : 434E4637-33333132-3853001B-2477306A
      SKU : GS467EA#ABU
      Family : 103C_5335KV
      Start mode : Power Switch

    >> OEM Information
      OEM #1 : $HP$
      OEM #2 : LOC#ABU
      OEM #3 : ABS 70/71 6A 6B 6C 6D

  > Mainboard : Quanta 30DA

    >> General Information
      Manufacturer : Quanta
      Product : 30DA
      Version : 85.24
      Serial Number : None2
      Support MP : Yes, 2 CPU(s)
      Version MPS : 1.4

    >> Chassis Information
      Manufacturer : Quanta
      Type : Notebook
      Version : N/A
      Serial Number : None
      Asset : Unspecified

    >> On-Board Device Information
      Device :   (Video)
      Embedded Controller : Yes

    >> Slots Information
      Slot PCI-Express : Available (64-bit) 5.0v, 3.3v
      Slot PCI-Express : Available (64-bit) 5.0v, 3.3v

    >> External Connectors

  > Bios : Hewlett-Packard

    >> General Information
      Manufacturer : Hewlett-Packard
      Version : F.25
      Date : 11/29/2007  (mm/dd/yyyy)
      Address : 0x0 on 1024 KB
      DMI Version : 2.4

    >> Characteristics
      Flashable : Yes
      Socketed : No

    >> Functionality
      APM : No
      ACPI : Yes
      ESCD : Yes
      PnP : Yes
      PCI : Yes
      ISA : Yes
      AGP : Yes
      USB : Yes
      PCMCIA : No
      Smart Battery : Yes

    >> Boot Information
      Selectable Boot : Yes
      CD-ROM Boot : Yes
      PC Card (PCMCIA) Boot : No
      I20 Boot : No
      LS-120 Boot : No
      1394 Boot : No
      ATAPI ZIP Boot : No
      Network Boot : No

  > Chipset : nVidia nForce 520

    >> General Information
      NorthBridge (SPP) : nVidia nForce 520
      NorthBridge : AMD K8 Bridge
      SouthBridge (MCP) : MCP65 LPC Bridge

    >> NorthBridge Information
      Architecture : Northbridge
      Manufacturer : nVidia (Hewlett-Packard Company)
      Codename : MCP65
      Revision : A3

    >> NorthBridge Information
      Architecture : Northbridge
      Manufacturer : AMD
      Revision : 00
      Bus Speed : 200.9 MHz
      HT Link : 803.7 MHz
      HyperTransport Clock : 800 MHz
      Upstream : 16-bit
      Downstream : 16-bit
      HTT max. Support : 2000 MHz
      RAM max. Support : DDR2 (800 MHz)

    >> Memory Information
      Type : DDR2-SDRAM PC2-2600
      Frequency : 160.7 MHz
      DRAM/FSB Ratio : CPU/5
      Supported Channels : Dual  (128-bit)
      Activated Channels : Dual
      ECC Diagnostic : No
      CAS Latency (tCL) : 5 clocks
      RAS to CAS (tRCD) : 5 clocks
      RAS Precharge (tRP) : 5 clocks
      Cycle Time (tRAS) : 15 clocks
      Bank Cycle Time (tRC) : 21 clocks
      Command Rate : 2 T

    >> Physical Capabilities
      Multi-Processor : No
      128-bit RAM : Yes
      ECC : No
      ChipKill ECC : No
      HTC : Yes
      UnGanging Support : No
      Multi VID Plane : No
      DRAM Scrub Rate : Disabled
      L3 Cache Scrub Rate : Disabled
      L2 Cache Scrub Rate : Disabled
      L1 Cache Scrub Rate : Disabled

    >> APIC Information
      Version : 1.01
      Maximum Interrupts : 24
      IRQ Handler enabled : No

    >> Device Capabilities (PCI)
      I/O Access : No
      Memory Access : Yes
      Bus Master Capable : Yes
      Special Cycle Recognition : No
      Memory Write & Invalidate : No
      VGA Palette Snoop : No
      Parity Error Response : No
      Cycle Wait : No
      System Error Line : No
      Fast Back-to-Back : No
      Detects Parity Errors : No
      User Defined Format : No
      PCI 66Mhz Bus Support : Yes
      New Capability List : Yes
      PCI Support : Hyper-Transport
      PCI Support : Hyper-Transport

  > Physical Memory : 2048 MB DDR2-SDRAM

    >> General Information
      DIMM 1 (Bank 0,1 ) : 1024 MB - DIMM
      DIMM 2 (Bank 2,3 ) : 1024 MB - DIMM

    >> Information SPD EEPROM (DIMM 1)
      Manufacturer : Samsung
      Part Number : M4 70T2953EZ3-CE6 
      Serial Number : 8404965E
      Type : DDR2-SDRAM PC2-5300 (333 MHz)  -  [DDR2-666]
      Format : SO-DIMM (67.6 x 3)
      Size : 1024 MB (2 ranks, 4 banks)
      Module Buffered : No
      Module Registered : No
      Module SLi Ready (EPP) : No
      Width : 64-bit
      Error Correction Capability : No
      Max. Burst Length : 8
      Refresh : Reduced (.5x)7.8 µs, Self Refresh
      Voltage : SSTL 1.8v
      Prefetch Buffer : 4-bit
      Manufacture : Week 33 of 2007
      Supported Frequencies : 200 MHz, 266 MHz, 333 MHz
      CAS Latency (tCL) : 3 clocks @200 MHz, 4 clocks @266 MHz, 5 clocks @333 MHz
      RAS to CAS (tRCD) : 3 clocks @200 MHz, 4 clocks @266 MHz, 5 clocks @333 MHz
      RAS Precharge (tRP) : 3 clocks @200 MHz, 4 clocks @266 MHz, 5 clocks @333 MHz
      Cycle Time (tRAS) : 9 clocks @200 MHz, 12 clocks @266 MHz, 15 clocks @333 MHz
      Min TRC : 12 clocks @200 MHz, 16 clocks @266 MHz, 20 clocks @333 MHz

    >> Information SPD EEPROM (DIMM 2)
      Manufacturer : Samsung
      Part Number : M4 70T2953EZ3-CE6 
      Serial Number : 780567F7
      Type : DDR2-SDRAM PC2-5300 (333 MHz)  -  [DDR2-666]
      Format : SO-DIMM (67.6 x 3)
      Size : 1024 MB (2 ranks, 4 banks)
      Module Buffered : No
      Module Registered : No
      Module SLi Ready (EPP) : No
      Width : 64-bit
      Error Correction Capability : No
      Max. Burst Length : 8
      Refresh : Reduced (.5x)7.8 µs, Self Refresh
      Voltage : SSTL 1.8v
      Prefetch Buffer : 4-bit
      Manufacture : Week 33 of 2007
      Supported Frequencies : 200 MHz, 266 MHz, 333 MHz
      CAS Latency (tCL) : 3 clocks @200 MHz, 4 clocks @266 MHz, 5 clocks @333 MHz
      RAS to CAS (tRCD) : 3 clocks @200 MHz, 4 clocks @266 MHz, 5 clocks @333 MHz
      RAS Precharge (tRP) : 3 clocks @200 MHz, 4 clocks @266 MHz, 5 clocks @333 MHz
      Cycle Time (tRAS) : 9 clocks @200 MHz, 12 clocks @266 MHz, 15 clocks @333 MHz
      Min TRC : 12 clocks @200 MHz, 16 clocks @266 MHz, 20 clocks @333 MHz

    >> Memory Controller Information
      Memory Controller : System Memory
      Location : Mainboard
      Error Correction Capability : No
      Number of connectors : 2
      Max. Module Size : 2048  KB

  > ISA Bus : Yes

    >> Bus Information
      Type : ISA
      Device : MCP65 LPC Bridge
      Revision : A3
      Number of ISA Connectors : 0

    >> Device Capabilities (PCI)
      I/O Access : Yes
      Memory Access : Yes
      Bus Master Capable : Yes
      Special Cycle Recognition : Yes
      Memory Write & Invalidate : No
      VGA Palette Snoop : No
      Parity Error Response : No
      Cycle Wait : No
      System Error Line : No
      Fast Back-to-Back : No
      Detects Parity Errors : No
      User Defined Format : No
      PCI 66Mhz Bus Support : Yes
      New Capability List : No
      PCI Support : Power Management Interface

  > PCI Bus : Yes

    >> General Information
      Number of PCI Bus : 4
      Number of PCI Connectors : 0

    >> Peripheral Type
      Device 12, Bus 0 : PCI-Express
      Device 13, Bus 0 : PCI-Express
      Device 14, Bus 0 : PCI-Express
      Device 15, Bus 0 : PCI-Express
      Device 1, Bus 5 : PCI-Express

    >> General Features
      Support PCI Mechanism 1 : Yes

    >> Bus Information #0
      Device : MCP65 Memory Controller
      Device : MCP65 LPC Bridge
      Device : MCP65 SMBus
      Device : MCP65 SMU
      Device : MCP65 USB Controller
      Device : MCP65 USB Controller
      Device : MCP65 Ethernet
      Device : MCP65 High Definition Audio
      Device : MCP65 PCI bridge
      Device : MCP65 IDE
      Device : MCP65 SATA Controller
      Device : Nvidia Corp
      Device : MCP65 PCIe bridge
      Device : MCP65 PCIe bridge
      Device : MCP65 PCIe bridge
      Device : Athlon64/Opteron/Sempron (K8 Family) HyperTransport Technology Configuration
      Device : Athlon64/Opteron/Sempron (K8 Family) Address Map
      Device : Athlon64/Opteron/Sempron (K8 Family) DRAM Controller
      Device : Athlon64/Opteron/Sempron (K8 Family) Miscellaneous Control

    >> Bus Information #3
      Device : BCM4310 UART

    >> Bus Information #5
      Device : GeForce 8400M GS

    >> Bus Information #7
      Device : R5C832 IEEE-1394 Controller
      Device : SD Bus Host Adapter
      Device : MMC Bus Host Adapter
      Device : Memory Stick Bus Host Adapter
      Device : xD-Picture Card Controller

  > Bus PCI-Express : Yes

    >> PCI-Express Information
      Number of connectors : 2

    >> Bus PCI-Express
      Device : Nvidia Corp
      Version : 1.0
      Port : 3
      Physical Slot : #0
      Slot Populated : Yes
      Link Width : x2   (max. x2)
      Link Speed : 2.5 GB/s

    >> Bus PCI-Express
      Device : MCP65 PCIe bridge
      Version : 1.0
      Port : 2
      Physical Slot : #0
      Slot Populated : Yes
      Link Width : x1   (max. x1)
      Link Speed : 2.5 GB/s

    >> Bus PCI-Express
      Device : MCP65 PCIe bridge
      Version : 1.0
      Port : 0
      Physical Slot : #0
      Slot Populated : Yes
      Link Width : x16   (max. x16)
      Link Speed : 2.5 GB/s

    >> Bus PCI-Express
      Device : MCP65 PCIe bridge
      Version : 1.0
      Port : 1
      Physical Slot : #0
      Slot Populated : No
      Link Width : x8   (max. x1)
      Link Speed : 2.5 GB/s

    >> Bus PCI-Express
      Device : GeForce 8400M GS
      Version : 1.0
      Port : 0
      Link Width : x16   (max. x16)
      Link Speed : 2.5 GB/s

  > USB Bus : Yes

    >> Device Information
      Device : MCP65 USB Controller
      Version : 1.0
      Interface : UHCI
      Frequency : 48 MHz

    >> Device Information
      Device : MCP65 USB Controller
      Version : 2.0
      Interface : EHCI

    >> Device Information
      Device
      Version : 1.0
      Interface : UHCI
      Frequency : 48 MHz

  > SMBus/i2c Bus : Yes

    >> General Information
      Device : MCP65 SMBus
      Revision : A1
      Frequency : 16 KHz
      Address #1 : 0x3040
      Address #2 : 0x3000

    >> Device Capabilities (PCI)
      I/O Access : Yes
      Memory Access : No
      Bus Master Capable : No
      Special Cycle Recognition : No
      Memory Write & Invalidate : No
      VGA Palette Snoop : No
      Parity Error Response : No
      Cycle Wait : No
      System Error Line : No
      Fast Back-to-Back : No
      Detects Parity Errors : No
      User Defined Format : No
      PCI 66Mhz Bus Support : Yes
      New Capability List : Yes
      PCI Support : Power Management Interface

  > Bus HyperTransport : Yes

    >> HyperTransport Host Information
      Device : Athlon64/Opteron/Sempron (K8 Family) HyperTransport Technology Configuration
      HyperTransport Clock : 800 MHz
      HyperTransport Frequency : 1600 MHz
      Upstream : 16-bit
      Downstream : 16-bit
      Version : 1.02
      Host : Yes

  > Bus CardBus : No

  > Bus FireWire : Yes

    >> Bus Information
      Device : R5C832 IEEE-1394 Controller

<<< Processor >>>

  > Processor : AMD Turion 64 X2 Mobile TL-56

    >> General Information
      Type : AMD Turion 64 X2 Mobile
      Internal Specification : AMD Turion(tm) 64 X2 Mobile Technology TL-56
      Model Number : TL-56
      Revision
      Technology : 0.065µ
      CPU ID : F.8.1
      CPU IDEx : F.68.1
      Brand ID : 2
      Microcode : MU0F810
      K8 Revision : 6.0
      Mobile : Yes

    >> Instructions
      IA-64 Technology : No
      X86-64 Technology : Yes
      FPU128 : No
      SSE5 : No
      SSE4a : No
      SSE4.2 : No
      SSE4.1 : No
      S-SSE3 : No
      SSE3 : Yes
      SSE2 : Yes
      SSE : Yes
      Extended 3DNow! Technology : Yes
      3DNow! Technology : Yes
      3DNOW Prefetch : No
      3DNow! Pro Technology : Yes
      AMD MMX Technology : Yes
      MMX Technology : Yes
      Cyrix MMX Technology : Yes
      CLF - Cache Line Flush : Yes
      CX8 - CMPXCHG8B : Yes
      CX16 - CMPXCHG16B : Yes
      CMOV - Conditionnal Move Inst. : Yes
      MON - Monitor/Mwait : No
      POPCNT : No
      RDTSCP : Yes
      SEP - Fast System Call : Yes

    >> Miscellaneous
      NX - No-execute Page : Yes
      VT - Vanderpool Technology : Yes
      SVM - Secure Virtual Machine : Yes
      FPU - Co-processor Built-in : Yes
      FXSR - Fast Float Save & Restore : Yes
      xTPR - Send Task Priority : No
      DAZ - Denormals Are Zero : Yes
      FFXSR : Yes
      LAHFSAHF : Yes
      CMPLEGACY : Yes
      ALTMOVCR8 : Yes
      ExtApicSpace : Yes
      3DNow! Technology : Yes
      PBE - Pend. Brk. EN. : Yes
      LAHF - LAHF/SAHF Inst. : No
      ABM : No
      MASSE - Misaligned SSE : No
      OSVW - OS Visible Workaround : No
      IBS : No
      P1GB - 1GB Page Size : No
      SKINIT, STGI, DEV : No
      WDT - Watchdog Timer : No

    >> Features
      VME - Virtual Mode Ext. : Yes
      DE - Debugging Extension : Yes
      PSE - Page Size Extension : Yes
      TSC - Time Stamp Counter : Yes
      MSR - Model Specific Registers : Yes
      PAE - Physical Address Extension : Yes
      MCE - Machine Check Exception : Yes
      APIC - Local APIC Built-in : Yes
      MTRR - Memory Type Range Reg. : Yes
      PGE - Page Global Enable : Yes
      MCA - Machine Check Architecture : Yes
      PAT - Page Attribute Table : Yes
      PSE36 - 36-bit Page Size Extension : Yes
      PSN - Unique Serial Number : No
      DS - Debug Trace & EMON Store : No
      SS - Self Snoop : No
      ACPI - Software Clock Control : No
      TM - Thermal Monitor : No
      TM2 - Thermal Monitor 2 : No
      EST - Enhanced SpeedStep Technology : No
      HTT - Hyper-Threading : Yes
      SBF - Signal Break on FERR : No
      DSCPL - CPL qualified Debug Store : No
      CID - Context ID : No
      LT - LaGrande Technology : No
      PDCM : No
      DCA - Direct Cache Access : No
      EPS - Enhanced PowerSaver : No
      SMP - MP Capability : No

    >> Features Hyper-Threading
      Technology : Yes   -   Disabled

    >> Features Multi-Core
      Physical Processor #1 (Core #1) : Apic ID 0
      Physical Processor #1 (Core #2) : Apic ID 1

    >> Power Status
      Voltage Control : Yes
      Frequency Control : Yes
      Thermal Sensor Built-in : Yes
      Thermal Trip : Yes
      Thermal Monitoring : Yes
      Software Thermal Control : Yes
      100MHz Steps : Yes
      HW P-State Control : No
      Invariant TSC : No

    >> Addressing Information
      Physical Addressing max. : 40-bit
      Linear Addressing max. : 48-bit

    >> Secure Virtual Machine Information
      Codename : Pacifica
      Revision : 1.0
      Address Space ID : 64
      LBR Virtulization : Yes

    >> Mainboard Upgradeability
      Socket/Slot : Socket S1
      Upgrade interface : Unspecified
      Supported Speed : 1800 MHz (or more)
      Supported Voltage : 1.6V

  > Frequency : 1800 MHz

    >> General Information
      Performance Rating : PR-5600 (estimated)
      Real Frequency : 803.57 MHz
      Multiplier : 4x
      Low/High Multiplier : 4x / 9x

    >> Front Side Bus Information
      Bus Speed : 200.9 MHz
      HT Link : 803.6 MHz

    >> Initial Frequencies
      Frequency : 1800 MHz
      Bus Speed : 200.00 MHz
      Multiplier : 9x

    >> Frequency Control
      Core #1 : 803.66 MHz
      Core #2 : 803.69 MHz

    >> Control Clock Frequency
      Type : PowerNow!

    >> Thermal Information
      Thermal Design Power : 65 W
      Core Power : 29.02 W (estimated)

    >> Processor Performance Information
      CPU Throttle Temperature : 88°C

  > Number of Core : 2

  > Support : Socket S1

  > Cache L1 : 2 x 128 KB

    >> General Information
      Type : Asynchronous
      Write Mode : Write-Back
      Place : On Chip

    >> Cache Information
      Data Cache : 2 x 64 KB (2-way, 64 bytes line size)
      Code Cache : 2 x 64 KB (2-way, 64 bytes line size)

  > Cache L2 : 2 x 512 KB

    >> General Information
      Type : Synchronous
      Write Mode : Write-Through
      Place : On Chip
      Multiplier : 1/1x   (803.7 MHz)

    >> Cache Information
      Associativity : 16-way
      Line Size : 64 bytes
      Bus : 128-bit
      Prefetch Logic : Yes

  > Voltage : 0.800 V

    >> General Information CPU
      Voltage : 0.800 V
      StartupVID : 0.800 V
      MaxVID : 1.125 V

  > Processor Temperature : 25 °C

    >> General Information

  > FPU Coprocessor : Present

    >> General Information
      Integrated : Yes
      Model : Compatible Intel

  > Core 1 Activity : 0%

  > Core 2 Activity : 0%

<<< Video >>>

  > Number of monitor : 1

    >> Monitor Information #1
      Monitor : Generic Non-PnP Monitor
      Linked on : NVIDIA GeForce 8400M GS
      Resolution : 1024x768
      Working desktop : 1024x738
      Main monitor : Yes

  > Monitor Type : LGPhilipsLCD 

    >> General Information
      Manufacturer : LGPhilipsLCD
      Product ID : LPLA002
      Manufacture : 2007
      Video Input Type : Digital in 0.7/0.3v
      Max. Horiz./Vert. Size : 37 cm / 23 cm
      Monitor Size : 17 inches (estimated)
      Aspect Ratio : 16:10
      Gamma Factor : 2.2
      DPMS Active-Off : No
      DPMS Suspend : No
      DPMS Standby : No
      EDID version : 1.2     

    >> Features
      Maximum Resolution : 1440 x 900 @ 59 Hz

  > Video Card : NVIDIA GeForce 8400M GS

    >> General Information
      Manufacturer : Nvidia Corp  (Hewlett-Packard Company)
      Model : NVIDIA GeForce 8400M GS
      Bus Type : PCI-Express
      Total Memory : 128 MB
      Texture Memory : 880 MB
      Processor : GeForce 8400M GS
      Converter : Integrated RAMDAC
      Refresh Rate (min/max) : 50/59 Hz

    >> GPU Information
      Number of GPU : 1
      Codename : G86
      Revision : A2
      Bus : 128-bit
      Memory Type : DDR2
      GPU Frequency : 400 MHz
      Shader Clock : 1188 MHz
      Memory Frequency GPU : 400 MHz
      Pixel Shader Version : 3.0

    >> nForceware Configuration
      Standard 2D : GPU: 169 MHz - Memory: 100 MHz
      3D Performance : GPU: 400 MHz - Memory: 400 MHz
      3D Low Power : GPU: 275 MHz - Memory: 200 MHz

    >> GPU Configuration
      Technology SLi : No
      AA Mode : OFF
      Frame Buffered : 3

    >> Video Bios Information
      Date : 09/06/07
      Version : Version 60.86.4F.00.23 
      Forceware : 7.15.11.5665

    >> i2C Bus Information
      Number of Bus : 4

    >> General Features
      Width : 361 mm
      Height : 271 mm
      Pixel per inch : 96x96 dpi
      bits per pixel : 32
      Colour Bits/Planes : 1
      Brushes : 4294967295
      Pens : 4294967295
      Markers : 0
      Device Fonts : 0
      Device Colours : 4294967295
      Clip Output to Rectangle : Yes
      Hardware Acceleration : No

    >> Raster Capabilities
      Banding : No
      Transfer Bitmaps : Yes
      Bitmap >64 KB : Yes
      Fonts larger than 64 K : Yes
      DIBs : Yes
      DIBTODEV : Yes
      Flood Fills : Yes
      Scaling : No
      StretchBlt : Yes
      StretchDIB : Yes

    >> Curves Capabilities
      Chord Arcs : Yes
      Circles : Yes
      Elipses : Yes
      Interiors : Yes
      Pie Wedges : Yes
      Rounded Rectangles : Yes
      Styled Borders : Yes
      Wide Borders : Yes
      Wide, Styled Borders : Yes

    >> Lines Capabilities
      Interiors : Yes
      Markers : Yes
      Polylines : Yes
      Polymarkers : Yes
      Styled : Yes
      Wide : Yes
      Wide, Styled : Yes

    >> Polygonal Capabilities
      Interiors : Yes
      Alternate Fill Polygons : Yes
      Winding Fill Polygons : Yes
      Rectangles : Yes
      Scan Lines : Yes
      Styled Borders : Yes
      Wide Borders : Yes
      Wide, Styled Borders : Yes

    >> Text Capabilities
      Stroke Precision : Yes
      Stroke Clip Precision : Yes
      90° Character Rotation : No
      Any Angle Character Rotation : No
      Independent X-Y Scaling : No
      Double Weighted Characters : No
      Italic : No
      Underline : Yes
      Strikeout : Yes
      Raster Fonts : Yes
      Vector Fonts : Yes

    >> Color Management Capabilities
      CMYK : No
      Gamma Ramp : Yes
      ICM Device : No

  > Current Display : 1024x768 pixels at 60 Hz in True Colors (32-bit)

    >> General Information
      Depth : 32-bit/pixel
      Refresh Rate : 59 Hz
      Birghtness : 75%

    >> Supported Resolutions
       720 x 576 in  : 32-bit at 60 Hz
       720 x 576 in  : 32-bit at 25 Hz
       720 x 576 in  : 32-bit at 60 Hz
       720 x 576 in  : 32-bit at 25 Hz
       720 x 576 in  : 32-bit at 60 Hz
       720 x 576 in  : 32-bit at 25 Hz
       720 x 576 in  : 65536 colours (16-bit) at 60 Hz
       720 x 576 in  : 65536 colours (16-bit) at 25 Hz
       720 x 576 in  : 65536 colours (16-bit) at 60 Hz
       720 x 576 in  : 65536 colours (16-bit) at 25 Hz
       720 x 576 in  : 65536 colours (16-bit) at 60 Hz
       720 x 576 in  : 65536 colours (16-bit) at 25 Hz
       720 x 576 in  : 256 colours at 60 Hz
       720 x 576 in  : 256 colours at 25 Hz
       720 x 576 in  : 256 colours at 60 Hz
       720 x 576 in  : 256 colours at 25 Hz
       720 x 576 in  : 256 colours at 60 Hz
       720 x 576 in  : 256 colours at 25 Hz
       320 x 200 in  : 32-bit at 60 Hz
       320 x 200 in  : 32-bit at 25 Hz
       320 x 200 in  : 32-bit at 60 Hz
       320 x 200 in  : 32-bit at 25 Hz
       320 x 200 in  : 32-bit at 60 Hz
       320 x 200 in  : 32-bit at 25 Hz
       320 x 240 in  : 32-bit at 60 Hz
       320 x 240 in  : 32-bit at 25 Hz
       320 x 240 in  : 32-bit at 60 Hz
       320 x 240 in  : 32-bit at 25 Hz
       320 x 240 in  : 32-bit at 60 Hz
       320 x 240 in  : 32-bit at 25 Hz
       400 x 300 in  : 32-bit at 60 Hz
       400 x 300 in  : 32-bit at 25 Hz
       400 x 300 in  : 32-bit at 60 Hz
       400 x 300 in  : 32-bit at 25 Hz
       400 x 300 in  : 32-bit at 60 Hz
       400 x 300 in  : 32-bit at 25 Hz
       480 x 360 in  : 32-bit at 60 Hz
       480 x 360 in  : 32-bit at 25 Hz
       480 x 360 in  : 32-bit at 60 Hz
       480 x 360 in  : 32-bit at 25 Hz
       480 x 360 in  : 32-bit at 60 Hz
       480 x 360 in  : 32-bit at 25 Hz
       512 x 384 in  : 32-bit at 60 Hz
       512 x 384 in  : 32-bit at 25 Hz
       512 x 384 in  : 32-bit at 60 Hz
       512 x 384 in  : 32-bit at 25 Hz
       512 x 384 in  : 32-bit at 60 Hz
       512 x 384 in  : 32-bit at 25 Hz
       640 x 400 in  : 32-bit at 60 Hz
       640 x 400 in  : 32-bit at 25 Hz
       640 x 400 in  : 32-bit at 60 Hz
       640 x 400 in  : 32-bit at 25 Hz
       640 x 400 in  : 32-bit at 60 Hz
       640 x 400 in  : 32-bit at 25 Hz
       640 x 480 in  : 32-bit at 60 Hz
       640 x 480 in  : 32-bit at 25 Hz
       640 x 480 in  : 32-bit at 60 Hz
       640 x 480 in  : 32-bit at 25 Hz
       640 x 480 in  : 32-bit at 60 Hz
       640 x 480 in  : 32-bit at 25 Hz
       720 x 480 in  : 32-bit at 60 Hz
       720 x 480 in  : 32-bit at 25 Hz
       720 x 480 in  : 32-bit at 60 Hz
       720 x 480 in  : 32-bit at 25 Hz
       720 x 480 in  : 32-bit at 60 Hz
       720 x 480 in  : 32-bit at 25 Hz
       800 x 600 in  : 32-bit at 60 Hz
       800 x 600 in  : 32-bit at 25 Hz
       800 x 600 in  : 32-bit at 60 Hz
       800 x 600 in  : 32-bit at 25 Hz
       800 x 600 in  : 32-bit at 60 Hz
       800 x 600 in  : 32-bit at 25 Hz
       1024 x 768 in  : 32-bit at 60 Hz
       1024 x 768 in  : 32-bit at 25 Hz
       1024 x 768 in  : 32-bit at 60 Hz
       1024 x 768 in  : 32-bit at 25 Hz
       1024 x 768 in  : 32-bit at 60 Hz
       1024 x 768 in  : 32-bit at 25 Hz
       320 x 200 in  : 65536 colours (16-bit) at 60 Hz
       320 x 200 in  : 65536 colours (16-bit) at 25 Hz
       320 x 200 in  : 65536 colours (16-bit) at 60 Hz
       320 x 200 in  : 65536 colours (16-bit) at 25 Hz
       320 x 200 in  : 65536 colours (16-bit) at 60 Hz
       320 x 200 in  : 65536 colours (16-bit) at 25 Hz
       320 x 240 in  : 65536 colours (16-bit) at 60 Hz
       320 x 240 in  : 65536 colours (16-bit) at 25 Hz
       320 x 240 in  : 65536 colours (16-bit) at 60 Hz
       320 x 240 in  : 65536 colours (16-bit) at 25 Hz
       320 x 240 in  : 65536 colours (16-bit) at 60 Hz
       320 x 240 in  : 65536 colours (16-bit) at 25 Hz
       400 x 300 in  : 65536 colours (16-bit) at 60 Hz
       400 x 300 in  : 65536 colours (16-bit) at 25 Hz
       400 x 300 in  : 65536 colours (16-bit) at 60 Hz
       400 x 300 in  : 65536 colours (16-bit) at 25 Hz
       400 x 300 in  : 65536 colours (16-bit) at 60 Hz
       400 x 300 in  : 65536 colours (16-bit) at 25 Hz
       480 x 360 in  : 65536 colours (16-bit) at 60 Hz
       480 x 360 in  : 65536 colours (16-bit) at 25 Hz
       480 x 360 in  : 65536 colours (16-bit) at 60 Hz
       480 x 360 in  : 65536 colours (16-bit) at 25 Hz
       480 x 360 in  : 65536 colours (16-bit) at 60 Hz
       480 x 360 in  : 65536 colours (16-bit) at 25 Hz
       512 x 384 in  : 65536 colours (16-bit) at 60 Hz
       512 x 384 in  : 65536 colours (16-bit) at 25 Hz
       512 x 384 in  : 65536 colours (16-bit) at 60 Hz
       512 x 384 in  : 65536 colours (16-bit) at 25 Hz
       512 x 384 in  : 65536 colours (16-bit) at 60 Hz
       512 x 384 in  : 65536 colours (16-bit) at 25 Hz
       640 x 400 in  : 65536 colours (16-bit) at 60 Hz
       640 x 400 in  : 65536 colours (16-bit) at 25 Hz
       640 x 400 in  : 65536 colours (16-bit) at 60 Hz
       640 x 400 in  : 65536 colours (16-bit) at 25 Hz
       640 x 400 in  : 65536 colours (16-bit) at 60 Hz
       640 x 400 in  : 65536 colours (16-bit) at 25 Hz
       640 x 480 in  : 65536 colours (16-bit) at 60 Hz
       640 x 480 in  : 65536 colours (16-bit) at 25 Hz
       640 x 480 in  : 65536 colours (16-bit) at 60 Hz
       640 x 480 in  : 65536 colours (16-bit) at 25 Hz
       640 x 480 in  : 65536 colours (16-bit) at 60 Hz
       640 x 480 in  : 65536 colours (16-bit) at 25 Hz
       720 x 480 in  : 65536 colours (16-bit) at 60 Hz
       720 x 480 in  : 65536 colours (16-bit) at 25 Hz
       720 x 480 in  : 65536 colours (16-bit) at 60 Hz
       720 x 480 in  : 65536 colours (16-bit) at 25 Hz
       720 x 480 in  : 65536 colours (16-bit) at 60 Hz
       720 x 480 in  : 65536 colours (16-bit) at 25 Hz
       800 x 600 in  : 65536 colours (16-bit) at 60 Hz
       800 x 600 in  : 65536 colours (16-bit) at 25 Hz
       800 x 600 in  : 65536 colours (16-bit) at 60 Hz
       800 x 600 in  : 65536 colours (16-bit) at 25 Hz
       800 x 600 in  : 65536 colours (16-bit) at 60 Hz
       800 x 600 in  : 65536 colours (16-bit) at 25 Hz
       1024 x 768 in  : 65536 colours (16-bit) at 60 Hz
       1024 x 768 in  : 65536 colours (16-bit) at 25 Hz
       1024 x 768 in  : 65536 colours (16-bit) at 60 Hz
       1024 x 768 in  : 65536 colours (16-bit) at 25 Hz
       1024 x 768 in  : 65536 colours (16-bit) at 60 Hz
       1024 x 768 in  : 65536 colours (16-bit) at 25 Hz
       320 x 200 in  : 256 colours at 60 Hz
       320 x 200 in  : 256 colours at 25 Hz
       320 x 200 in  : 256 colours at 60 Hz
       320 x 200 in  : 256 colours at 25 Hz
       320 x 200 in  : 256 colours at 60 Hz
       320 x 200 in  : 256 colours at 25 Hz
       320 x 240 in  : 256 colours at 60 Hz
       320 x 240 in  : 256 colours at 25 Hz
       320 x 240 in  : 256 colours at 60 Hz
       320 x 240 in  : 256 colours at 25 Hz
       320 x 240 in  : 256 colours at 60 Hz
       320 x 240 in  : 256 colours at 25 Hz
       400 x 300 in  : 256 colours at 60 Hz
       400 x 300 in  : 256 colours at 25 Hz
       400 x 300 in  : 256 colours at 60 Hz
       400 x 300 in  : 256 colours at 25 Hz
       400 x 300 in  : 256 colours at 60 Hz
       400 x 300 in  : 256 colours at 25 Hz
       480 x 360 in  : 256 colours at 60 Hz
       480 x 360 in  : 256 colours at 25 Hz
       480 x 360 in  : 256 colours at 60 Hz
       480 x 360 in  : 256 colours at 25 Hz
       480 x 360 in  : 256 colours at 60 Hz
       480 x 360 in  : 256 colours at 25 Hz
       512 x 384 in  : 256 colours at 60 Hz
       512 x 384 in  : 256 colours at 25 Hz
       512 x 384 in  : 256 colours at 60 Hz
       512 x 384 in  : 256 colours at 25 Hz
       512 x 384 in  : 256 colours at 60 Hz
       512 x 384 in  : 256 colours at 25 Hz
       640 x 400 in  : 256 colours at 60 Hz
       640 x 400 in  : 256 colours at 25 Hz
       640 x 400 in  : 256 colours at 60 Hz
       640 x 400 in  : 256 colours at 25 Hz
       640 x 400 in  : 256 colours at 60 Hz
       640 x 400 in  : 256 colours at 25 Hz
       640 x 480 in  : 256 colours at 60 Hz
       640 x 480 in  : 256 colours at 25 Hz
       640 x 480 in  : 256 colours at 60 Hz
       640 x 480 in  : 256 colours at 25 Hz
       640 x 480 in  : 256 colours at 60 Hz
       640 x 480 in  : 256 colours at 25 Hz
       720 x 480 in  : 256 colours at 60 Hz
       720 x 480 in  : 256 colours at 25 Hz
       720 x 480 in  : 256 colours at 60 Hz
       720 x 480 in  : 256 colours at 25 Hz
       720 x 480 in  : 256 colours at 60 Hz
       720 x 480 in  : 256 colours at 25 Hz
       800 x 600 in  : 256 colours at 60 Hz
       800 x 600 in  : 256 colours at 25 Hz
       800 x 600 in  : 256 colours at 60 Hz
       800 x 600 in  : 256 colours at 25 Hz
       800 x 600 in  : 256 colours at 60 Hz
       800 x 600 in  : 256 colours at 25 Hz
       1024 x 768 in  : 256 colours at 60 Hz
       1024 x 768 in  : 256 colours at 25 Hz
       1024 x 768 in  : 256 colours at 60 Hz
       1024 x 768 in  : 256 colours at 25 Hz
       1024 x 768 in  : 256 colours at 60 Hz
       1024 x 768 in  : 256 colours at 25 Hz

    >> ICM Information
      Profil : sRGB Color Space Profile.icm
      Copyright : LinoColorCMM © by Heidelberger Druckmaschinen AG
      Version supported : Windows 5
      Compatibility : Windows 4
      ICC Signature : Win 

  > OpenGL : Yes

    >> General Information
      Manufacturer : NVIDIA Corporation
      Version : 2.1.1
      Renderer : GeForce 8400M GS/PCI/SSE2/3DNOW!
      Acceleration : Yes, Hardware

  > GDI Plus : Yes

    >> GDI+ Image Decoders
      Format BMP (1.0) : *.BMP;*.DIB;*.RLE
      Format JPEG (1.0) : *.JPG;*.JPEG;*.JPE;*.JFIF
      Format GIF (1.0) : *.GIF
      Format EMF (1.0) : *.EMF
      Format WMF (1.0) : *.WMF
      Format TIFF (1.0) : *.TIF;*.TIFF
      Format PNG (1.0) : *.PNG
      Format ICO (1.0) : *.ICO

    >> GDI+ Image Encoders
      Format BMP (1.0) : *.BMP;*.DIB;*.RLE
      Format JPEG (1.0) : *.JPG;*.JPEG;*.JPE;*.JFIF
      Format GIF (1.0) : *.GIF
      Format TIFF (1.0) : *.TIF;*.TIFF
      Format PNG (1.0) : *.PNG

<<< IO Ports >>>

  > Port installed : HDAUDIO Soft Data Fax Modem with SmartCP

    >> General Information
      Type : Serial

    >> Port Properties
      Packet version : 2
      Packet Size : 64 bytes
      Current/Max Receive Buffer : 8192/0 bytes
      Current/Max Transmit Buffer : 0/0 bytes
      Speed : Programmable
      Type : Modem

    >> Features
      DTRDSR : Yes
      RTSCTS : Yes
      RLSD : Yes
      PARITY_CHECK : Yes
      XONXOFF : Yes
      SETXCHAR : Yes
      TOTALTIMEOUTS : Yes
      INTTIMEOUTS : Yes
      SPECIALCHARS : No
      16BITMODE : No

    >> TimeOut Features
      ReadIntervalTimeout : 0 ms
      ReadTotalTimeoutMultiplier : 0 ms
      ReadTotalTimeoutConstant : 0 ms
      WriteTotalTimeoutMultiplier : 0 ms
      WriteTotalTimeoutConstant : 0 ms

    >> Default Port Configuration
      Speed : 115200 bps
      Data Bits : 8
      Stop Bit(s) : 2
      Parity : None
      Binary Transmission : Unspecified
      CTS output flow control : No
      DSR output flow control : No
      DTR flow control : Disabled
      RTS flow control : Disabled
      DSR sensitivity : No
      XOFF continue transmission : No
      XON/XOFF output flow control : No
      XON/XOFF input flow control : No
      Error Replacement : No
      Null Stripping : No
      Abort on Errors : No

  > Port installed : Standard Modem over Bluetooth link

    >> General Information
      Type : Serial

  > Port installed : Standard Modem over Bluetooth link #2

    >> General Information
      Type : Serial

  > Port installed : Standard OpenHCD USB Host Controller

    >> General Information
      Type : Universal Serial Bus (USB)
      Number of ports : 10

    >> USB Port 3
      Manufacturer : Broadcom Corp
      Product : HP Integrated Module
      USB Version : 2.00
      Device Version : 1.00
      Product ID : VEN_03F0,DEV_171D,PRT_01
      Max. Packet Size : 64 bytes
      Open Pipes : 7

    >> USB Port 9
      USB Version : 1.10
      Device Version : 6.23
      Product ID : VEN_08FF,DEV_2580,PRT_FF
      Max. Packet Size : 8 bytes
      Speed Device : 480 Mb/s
      Open Pipes : 2

    >> USB Port 4
      Manufacturer : Ricoh co. Ltd.
      USB Version : 2.00
      Device Version : 76.01
      Product ID : VEN_05CA,DEV_1812,PRT_01
      Max. Packet Size : 64 bytes
      Speed Device : 480 Mb/s
      Max. Power : 100 mA
      Open Pipes : 1

<<< Drives >>>

  > Number of Disk Controller : 2

    >> General Information
      Disk Controller : Nvidia Corp MCP65 IDE
      Disk Controller : Nvidia Corp MCP65 SATA Controller

    >> Drive Controller Features #1
      Mode : IDE
      AHCI : No

    >> Drive Controller Features #2
      Mode : IDE
      AHCI : Yes
      IDE Legacy : No
      NCQ : No
      Port Multiplier : No

  > Number of Hard Disk : 2

    >> General Information
      SMART : Version 1.1

    >> Informations Hard Disk TOSHIBA MK1237GSX
      Model : TOSHIBA MK1237GSX
      Serial Number : 77UTF1GVS
      Revision : DL132C
      Serial ATA : Yes
      Serial ATA version : 1.0  -  (SATA-150)
      Support : ATA/ATAPI-7
      Size : 120 GB
      ECC Size : 4
      Multiple Sector : 16
      IORDY : Yes
      LBA Mode : Yes
      DMA Mode : Yes
      NCQ Mode : No
      SCT Mode : Yes
      DCO Mode : Yes
      NV Cache : No
      TCQ Mode : No
      CFA Power Mode : No
      SETMAX : No
      Multiword DMA Mode : 2
      PIO Mode : PIO 4
      UDMA Mode max. : 5 (ATA-100)
      UDMA Mode Enabled : 5 (ATA-100)
      SMART : Yes   -   Enabled
      SMART Self-Test : Yes
      AAM : No
      Write Cache : Yes
      Streaming Mode : No
      Power Management : Yes
      APM Mode : Yes   -   Enabled
      APM Level : 128
      PUIS Mode : No
      Security Mode : No
      Trusted Computing : No
      48-bit Address : Yes
      Cylinders : 232581
      Heads : 16
      Sectors per Track : 63

    >> Informations Hard Disk TOSHIBA MK1237GSX
      Model : TOSHIBA MK1237GSX
      Serial Number : 77UTF1GUS
      Revision : DL132C
      Serial ATA : Yes
      Serial ATA version : 1.0  -  (SATA-150)
      Support : ATA/ATAPI-7
      Size : 120 GB
      ECC Size : 4
      Multiple Sector : 16
      IORDY : Yes
      LBA Mode : Yes
      DMA Mode : Yes
      NCQ Mode : No
      SCT Mode : Yes
      DCO Mode : Yes
      NV Cache : No
      TCQ Mode : No
      CFA Power Mode : No
      SETMAX : No
      Multiword DMA Mode : 2
      PIO Mode : PIO 4
      UDMA Mode max. : 5 (ATA-100)
      UDMA Mode Enabled : 5 (ATA-100)
      SMART : Yes   -   Enabled
      SMART Self-Test : Yes
      AAM : No
      Write Cache : Yes
      Streaming Mode : No
      Power Management : Yes
      APM Mode : Yes   -   Enabled
      APM Level : 128
      PUIS Mode : No
      Security Mode : No
      Trusted Computing : No
      48-bit Address : Yes
      Cylinders : 232581
      Heads : 16
      Sectors per Track : 63

    >> SMART Information Disk TOSHIBA MK1237GSX
      Health : 99% (estimated)
      Performance : 91% (estimated)
      Threshold Exceeding : No
      
      Raw Read Error Rate (01) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Throughput Performance (02) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Spin Up Time (03) : 00690	(Threshold : 002   -   Worst : 100   -   Max : 100)
      Start/Stop Count (04) : 00426	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Reallocated Sector Count (05) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Seek Error Rate (07) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Seek Time Performance (08) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Power On Hours Count (09) : 004B5	(Threshold : 000   -   Worst : 097   -   Max : 097)
      Spin Retry Count (0A) : 00000	(Threshold : 030   -   Worst : 100   -   Max : 120)
      Power Cycle Count (0C) : 00402	(Threshold : 000   -   Worst : 100   -   Max : 100)
       (BB) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
       (BC) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
       (BD) : 00000	(Threshold : 001   -   Worst : 100   -   Max : 100)
       (BE) : D0030	(Threshold : 045   -   Worst : 027   -   Max : 052)
       (BF) : 0010C	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Power-Off Retract Count (C0) : 30053	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Load/Unload Cycle Count (C1) : 01305	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Temperature (C2) : 80030	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Reallocation Event Count (C4) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Current Pending Sector Count (C5) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Off-Line Uncorrectable Sector Count (C6) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Ultra ATA CRC Error Rate (C7) : 00000	(Threshold : 000   -   Worst : 200   -   Max : 200)
      Disk Shift (DC) : 00042	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Loaded Hours (DE) : 003F5	(Threshold : 000   -   Worst : 098   -   Max : 098)
      Load Retry Count (DF) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Load Friction (E0) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Load-In Time (E2) : 00133	(Threshold : 000   -   Worst : 100   -   Max : 100)

    >> SMART Information Disk TOSHIBA MK1237GSX
      Health : 99% (estimated)
      Performance : 92% (estimated)
      Threshold Exceeding : No
      
      Raw Read Error Rate (01) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Throughput Performance (02) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Spin Up Time (03) : 00657	(Threshold : 002   -   Worst : 100   -   Max : 100)
      Start/Stop Count (04) : 00705	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Reallocated Sector Count (05) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Seek Error Rate (07) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Seek Time Performance (08) : 00000	(Threshold : 050   -   Worst : 100   -   Max : 100)
      Power On Hours Count (09) : 00462	(Threshold : 000   -   Worst : 098   -   Max : 098)
      Spin Retry Count (0A) : 00000	(Threshold : 030   -   Worst : 100   -   Max : 135)
      Power Cycle Count (0C) : 00403	(Threshold : 000   -   Worst : 100   -   Max : 100)
       (BB) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
       (BC) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
       (BD) : 00000	(Threshold : 001   -   Worst : 100   -   Max : 100)
       (BE) : 20024	(Threshold : 045   -   Worst : 048   -   Max : 064)
       (BF) : 00035	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Power-Off Retract Count (C0) : 00140	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Load/Unload Cycle Count (C1) : 02C70	(Threshold : 000   -   Worst : 099   -   Max : 099)
      Temperature (C2) : 90024	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Reallocation Event Count (C4) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Current Pending Sector Count (C5) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Off-Line Uncorrectable Sector Count (C6) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Ultra ATA CRC Error Rate (C7) : 00000	(Threshold : 000   -   Worst : 253   -   Max : 200)
      Disk Shift (DC) : 00058	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Loaded Hours (DE) : 00136	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Load Retry Count (DF) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Load Friction (E0) : 00000	(Threshold : 000   -   Worst : 100   -   Max : 100)
      Load-In Time (E2) : 0011B	(Threshold : 000   -   Worst : 100   -   Max : 100)

    >> Partitions
      Hard Disk #1 : Partition #1 (111 GB)
      Hard Disk #2 : Partition #1 (107 GB)
      Hard Disk #2 : Partition #2 (4 GB)

    >> Monitoring Information
      TOSHIBA MK1237GSX : 48 °C

    >> Monitoring Information
      TOSHIBA MK1237GSX : 36 °C

  > Number of CD-ROM Drive : 1

    >> Informations CD-Rom HL-DT-ST DVDRAM GSA-T20L
      IDE Channel : #1  -  Master Drive
      Manufacturer : HL-DT-ST
      Model : HL-DT-ST DVDRAM GSA-T20L
      Serial Number : K2A77O11421
      Revision : NC08
      Serial ATA : No
      Support : ATA/ATAPI-7
      IORDY : Yes
      LBA Mode : Yes
      DMA Mode : Yes
      NCQ Mode : No
      SCT Mode : No
      DCO Mode : No
      NV Cache : No
      TCQ Mode : No
      CFA Power Mode : No
      SETMAX : No
      Multiword DMA Mode : 2
      PIO Mode : PIO 4
      UDMA Mode max. : 0 (ATA-33)
      UDMA Mode Enabled : 0 (ATA-33)
      SMART : No
      SMART Self-Test : No
      AAM : No
      Write Cache : No
      Rotation Control : CLV
      
      CD-R Read : Yes
      CD-RW Reading : Yes
      DVD-Rom Reading : Yes
      DVD-RAM Reading : Yes
      DVD-R Reading : Yes
      DVD-RW Reading : Yes
      DVD+R Reading : Yes
      DVD+RW Reading : Yes
      DVD+R DL Reading : Yes
      DVD BD Reading : No
      DVD BD-RE Reading : No
      DVD BD-R Reading : No
      DVD BD-Rom Reading : No
      DVD HD Reading : No
      
      CD-R Writing : Yes
      CD-RW Writing : Yes
      DVD-RAM Writing : Yes
      DVD-R Writing : Yes
      DVD+R Writing : Yes
      DVD-RW Writing : Yes
      DVD+RW Writing : Yes
      DVD+R DL Writing : Yes
      DVD BD Writing : No
      DVD BD-RE Writing : No
      DVD BD-R Wrting : No
      DVD HD Writing : No
      DVD HD-RW Writing : No
      
      SMART : Yes
      DVD CSS : Yes
      DVD CPRM : Yes
      AACS : No
      VCPS : No
      Mount Rainier (MRW) : No
      Buffer Underrun : Yes
      JustLink : No
      LabelFlash : No
      LightScribe : Yes
      LightScribe Drive Speed : Yes
      SolidBurn : No
      
      Method 2 : Yes
      CD-Audio Support : Yes
      MultiSession or Photo-CD : Yes
      Side Change Capable : No
      
      Reading CD-Rom : 62x  (11080 KB/s)
      Reading DVD-Rom : 20x
      
      Writing CD-R : 62x  (11080 KB/s)
      Writing CD-RW : 38x
      Writing DVD-R : 12x
      Writing DVD-RW : 6x
      Writing DVD+R : 12x
      Writing DVD+RW : 6x
      Writing DVD+R DL : 4x
      
      Region Code : Installed
      Region : 1
      User Changes : 4
      Vendor Changes : 4
      RPC Phase II : Yes

  > Drives Letters :  C:\ D:\ F:\ G:\

    >> General Information
      Boot Drive :  :\

    >> Disk #0, Partition #0
      Bootable : Unspecified
      Active : Unspecified
      Primary : Unspecified
      Type : Installable File System
      Number of Blocks : 234 437 857
      Block Size : 512 bytes
      Size : 120 032 182 784 bytes
      Offset :  32 256 bytes

    >> Disk #1, Partition #0
      Bootable : Unspecified
      Active : Unspecified
      Primary : Unspecified
      Type : Unknown
      Number of Blocks : 224 829 612
      Block Size : 512 bytes
      Size : 115 112 761 344 bytes
      Offset :  32 256 bytes

    >> Disk #1, Partition #1
      Bootable : No
      Active : No
      Primary : No
      Type : Extended Partition
      Number of Blocks : 9 606 870
      Block Size : 512 bytes
      Size : 4 918 717 440 bytes
      Offset : 115112 793 600 bytes

  > Drive C: (Hard Disk) : 61 GB available on 120 GB

    >> General Information
      Disk Type : Hard Disk
      Peripheral Type : ATA
      Model : TOSHIBA MK1237GSX                                               
      Free Space : 51%

    >> Drive Information
      Volume Name : OS
      Serial Number : 66C0-32EB
      Files Name : 255
      File Management : NTFS
      Volume is Compressed : No
      Case Sensitive Search : Yes
      Preserves Filename Case : Yes
      Unicode Filenames : Yes
      Access Control List : Yes
      Named Streams : Yes
      Object Identifiers : Yes
      Reparse Points : Yes
      Sparse Files : Yes
      User Disk Quotas : Yes
      Individual File Compression : Yes
      Encryption : Yes
      Share : No

    >> Logical Features
      Sectors per Cluster : 8
      Bytes per Sector : 512
      Cluster size : 4  KB
      Free Clusters : 15017331
      Total Clusters : 29304732

    >> Physical Features
      Cylinders : 14593
      Heads : 255
      Sectors per Track : 63
      Bytes per Sector : 512

  > Drive D: (CD-Rom) : 0 KB available on 0 KB

    >> General Information
      Disk Type : CD-Rom Data

  > Drive F: (DVD-Rom) : 0 KB available on 717 MB

    >> General Information
      Disk Type : CD-Rom Data
      Peripheral Type : ATAPI
      Model : HL-DT-ST DVDRAM GSA-T20L                                        
      Recordable : Yes
      Free Space : 0%

    >> Drive Information
      Volume Name : Ubuntu 8.04 amd6
      Serial Number : BF2D-3B3F
      Files Name : 110
      File Management : CDFS
      Volume is Compressed : No
      Case Sensitive Search : Yes
      Preserves Filename Case : No
      Unicode Filenames : Yes
      Access Control List : No
      Named Streams : No
      Object Identifiers : No
      Reparse Points : No
      Sparse Files : No
      User Disk Quotas : No
      Individual File Compression : No
      Encryption : No
      Share : No

    >> Logical Features
      Sectors per Cluster : 1
      Bytes per Sector : 2048
      Cluster size : 2  KB
      Free Clusters : 0
      Total Clusters : 350120

    >> Physical Features
      Cylinders : 170
      Heads : 64
      Sectors per Track : 32
      Bytes per Sector : 2048

  > Drive G: (DVD-Rom) : 0 KB available on 0 KB

    >> General Information
      Disk Type : CD-Rom Data
      Peripheral Type : SCSI
      Manufacturer : RH7065S                                                         
      Model : XFX251A                                                         

<<< Printers >>>

  > Default Printer : \\Main\Canon iP4300

    >> General Information
      Printer : \\Main\Canon iP4300

    >> Current Configuration
      Version : 0.00
      Format : personnalised
      Orientation : Landscape
      Color printing : No
      TTF Download : No
      Number of copies : 0
      Hatching : Specifical
      Paper Type : Specifical
      ICM Method : Specifical

  > Printer installed : Microsoft XPS Document Writer

    >> General Information
      Port : XPSPort:
      Print Processor : WinPrint
      Data : RAW
      Priority : 1/99
      Printing Mode : Spooler
      Connection : Local
      Bidirectionnal Mode : No
      Shared Printer : No
      Jobs in progress : 0
      Color printing : Yes

    >> Loader Information
      Loader : Automatically Select

    >> Format Information
      Format : Letter
      Format : Letter Small
      Format : Tabloid
      Format : Ledger
      Format : Legal
      Format : Statement
      Format : Executive
      Format : A3
      Format : A4
      Format : A4 Small
      Format : A5
      Format : B4 (JIS)
      Format : B5 (JIS)
      Format : Folio
      Format : Quarto
      Format : 10x14
      Format : 11x17
      Format : Note
      Format : Envelope #9
      Format : Envelope #10
      Format : Envelope #11
      Format : Envelope #12
      Format : Envelope #14
      Format : C size sheet
      Format : D size sheet
      Format : E size sheet
      Format : Envelope DL
      Format : Envelope C5
      Format : Envelope C3
      Format : Envelope C4
      Format : Envelope C6
      Format : Envelope C65
      Format : Envelope B4
      Format : Envelope B5
      Format : Envelope B6
      Format : Envelope
      Format : Envelope Monarch
      Format : 6 3/4 Envelope
      Format : US Std Fanfold
      Format : German Std Fanfold
      Format : German Legal Fanfold
      Format : B4 (ISO)
      Format : Japanese Postcard
      Format : 9x11
      Format : 10x11
      Format : 15x11
      Format : Envelope Invite
      Format : Letter Extra
      Format : Legal Extra
      Format : A4 Extra
      Format : Letter Transverse
      Format : A4 Transverse
      Format : Letter Extra Transverse
      Format : Super A
      Format : Super B
      Format : Letter Plus
      Format : A4 Plus
      Format : A5 Transverse
      Format : B5 (JIS) Transverse
      Format : A3 Extra
      Format : A5 Extra
      Format : B5 (ISO) Extra
      Format : A2
      Format : A3 Transverse
      Format : A3 Extra Transverse
      Format : Japanese Double Postcard
      Format : A6
      Format : Japanese Envelope Kaku #2
      Format : Japanese Envelope Kaku #3
      Format : Japanese Envelope Chou #3
      Format : Japanese Envelope Chou #4
      Format : Letter Rotated
      Format : A3 Rotated
      Format : A4 Rotated
      Format : A5 Rotated
      Format : B4 (JIS) Rotated
      Format : B5 (JIS) Rotated
      Format : Japanese Postcard Rotated
      Format : Double Japan Postcard Rotated
      Format : A6 Rotated
      Format : Japan Envelope Kaku #2 Rotated
      Format : Japan Envelope Kaku #3 Rotated
      Format : Japan Envelope Chou #3 Rotated
      Format : Japan Envelope Chou #4 Rotated
      Format : B6 (JIS)
      Format : B6 (JIS) Rotated
      Format : 12x11
      Format : Japan Envelope You #4
      Format : Japan Envelope You #4 Rotated
      Format : PRC Envelope #1
      Format : PRC Envelope #3
      Format : PRC Envelope #4
      Format : PRC Envelope #5
      Format : PRC Envelope #6
      Format : PRC Envelope #7
      Format : PRC Envelope #8
      Format : PRC Envelope #9
      Format : PRC Envelope #10
      Format : PRC Envelope #1 Rotated
      Format : PRC Envelope #3 Rotated
      Format : PRC Envelope #4 Rotated
      Format : PRC Envelope #5 Rotated
      Format : PRC Envelope #6 Rotated
      Format : PRC Envelope #7 Rotated
      Format : PRC Envelope #8 Rotated
      Format : PRC Envelope #9 Rotated

    >> Resolution Information
      Resolution : 600 x 600 dpi

    >> General Features
      Width : 216 mm
      Height : 279 mm
      Pixel per inch : 600x600 dpi
      bits per pixel : 32
      Colour Bits/Planes : 1
      Brushes : 4294967295
      Pens : 40
      Markers : 0
      Device Fonts : 0
      Device Colours : 8
      Clip Output to Rectangle : Yes

    >> Physical Capabilities
      Physical Offset X : 0
      Physical Offset Y : 0
      Physical Width : 5100
      Physical Height : 6600

    >> Raster Capabilities
      Banding : No
      Transfer Bitmaps : Yes
      Bitmap >64 KB : Yes
      Fonts larger than 64 K : Yes
      DIBs : Yes
      DIBTODEV : Yes
      Flood Fills : No
      Scaling : No
      StretchBlt : Yes
      StretchDIB : Yes

    >> Curves Capabilities
      Chord Arcs : Yes
      Circles : Yes
      Elipses : Yes
      Interiors : Yes
      Pie Wedges : Yes
      Rounded Rectangles : Yes
      Styled Borders : Yes
      Wide Borders : Yes
      Wide, Styled Borders : Yes

    >> Lines Capabilities
      Interiors : Yes
      Markers : Yes
      Polylines : Yes
      Polymarkers : Yes
      Styled : Yes
      Wide : Yes
      Wide, Styled : Yes

    >> Polygonal Capabilities
      Interiors : Yes
      Alternate Fill Polygons : Yes
      Winding Fill Polygons : Yes
      Rectangles : Yes
      Scan Lines : Yes
      Styled Borders : Yes
      Wide Borders : Yes
      Wide, Styled Borders : Yes

    >> Text Capabilities
      Stroke Precision : Yes
      Stroke Clip Precision : Yes
      90° Character Rotation : No
      Any Angle Character Rotation : Yes
      Independent X-Y Scaling : Yes
      Double Weighted Characters : No
      Italic : Yes
      Underline : Yes
      Strikeout : Yes
      Raster Fonts : No
      Vector Fonts : Yes

    >> Color Management Capabilities
      CMYK : No
      Gamma Ramp : No
      ICM Device : No

  > Printer installed : \\Main\Canon iP4300

  > Universal Driver : Not Installed

<<< Devices >>>

  > Type of mouse : Synaptics PS/2 Port TouchPad

    >> General Information
      Buttons number : 5

    >> Settings
      Wheel : Yes
      Scrolling : 3 Lines
      Buttons reversed. : No
      Cursor : 32x32 pixels

    >> Features
      Double-click speed : 500 ms
      TRAILS : No
      SONAR : No
      VANISH : Yes
      SHADOW : Yes
      X/Y Threshold : 6/1
      PEN Windows : No

    >> Accessibility
      Function Activated : No

  > Type of keyboard : HID Keyboard Device

    >> General Information
      Type of keyboard : 4
      Keyboard Sub-type : 0
      Function keys : 12

    >> Features
      Delay : Medium
      Frequency : 31
      User Preference : No
      Underligned menu shortcut : No
      OEM Code Page : 850
      ANSI Code Page : 1252
      ID : 00000809
      Layout Type : 1
      MAJ Key Enabled : No
      NUM Key Enabled : Yes

    >> Filter Keys Accessibility
      Activity keys : No

    >> Sticky Keys Accessibility
      Activity keys : No

    >> Toggle Keys Accessibility
      Activity keys : No

  > Type of keyboard : Standard 101/102-Key or Microsoft Natural PS/2 Keyboard

    >> General Information
      Type of keyboard : 4
      Keyboard Sub-type : 0
      Function keys : 12

    >> Features
      Delay : Medium
      Frequency : 31
      User Preference : No
      Underligned menu shortcut : No
      OEM Code Page : 850
      ANSI Code Page : 1252
      ID : 00000809
      Layout Type : 1
      MAJ Key Enabled : No
      NUM Key Enabled : Yes

    >> Filter Keys Accessibility
      Activity keys : No

    >> Sticky Keys Accessibility
      Activity keys : No

    >> Toggle Keys Accessibility
      Activity keys : No

  > Joystick : None

  > HID Devices : Yes

    >> General Information
      Device : TabletPC Key Buttons
      Device : Bluetooth Remote Control HID Device

  > Modem : HDAUDIO Soft Data Fax Modem with SmartCP

    >> General Information
      Model : HDAUDIO Soft Data Fax Modem with SmartCP
      Manufacturer : CXT
      Connected : COM3
      RAS Connection : No

    >> Port Properties
      Packet version : 2
      Packet Size : 64 bytes
      Current/Max Receive Buffer : 8192/0 bytes
      Current/Max Transmit Buffer : 0/0 bytes
      Speed : Programmable
      Type : Modem

    >> Features
      DTRDSR : Yes
      RTSCTS : Yes
      RLSD : Yes
      PARITY_CHECK : Yes
      XONXOFF : Yes
      SETXCHAR : Yes
      TOTALTIMEOUTS : Yes
      INTTIMEOUTS : Yes
      SPECIALCHARS : No
      16BITMODE : No

    >> TimeOut Features
      ReadIntervalTimeout : 0 ms
      ReadTotalTimeoutMultiplier : 0 ms
      ReadTotalTimeoutConstant : 0 ms
      WriteTotalTimeoutMultiplier : 0 ms
      WriteTotalTimeoutConstant : 0 ms

    >> Default Port Configuration
      Speed : 115200 bps
      Data Bits : 8
      Stop Bit(s) : 2
      Parity : None
      Binary Transmission : Unspecified
      CTS output flow control : No
      DSR output flow control : No
      DTR flow control : Disabled
      RTS flow control : Disabled
      DSR sensitivity : No
      XOFF continue transmission : No
      XON/XOFF output flow control : No
      XON/XOFF input flow control : No
      Error Replacement : No
      Null Stripping : No
      Abort on Errors : No

    >> Call configuration
      Wait for dialling tone before calling : Yes
      Cancel if the call does not succeed : Yes  ( in 60 s.)

    >> Specific Information
      ATI Command0 : 56000
      ATI Command1 : 255
      ATI Command3 : SoftK56V_B2.1_V7.67.00
      ATI Command4 : HDAUDIO Soft Data Fax Modem with SmartCP
      ATI Command5 : 256
      ATI Command6 : SoftK56 CModem Version 12Rksample Version 342
      ATI Command7 : 255
      ATI Command8 : Jun 20 2007 # 11:27:16
      ATI Command9 : GENERIC
      AT+GMM : MM+GMM: HDAUDIO Soft Data Fax Modem with SmartCP

  > Modem : Standard Modem over Bluetooth link

    >> General Information
      Model : Standard Modem over Bluetooth link
      Manufacturer : Standard Cell Phones
      Connected : COM4
      RAS Connection : No

    >> Call configuration
      Wait for dialling tone before calling : Yes
      Cancel if the call does not succeed : Yes  ( in 0 s.)

  > Modem : Standard Modem over Bluetooth link

    >> General Information
      Model : Standard Modem over Bluetooth link
      Manufacturer : Standard Cell Phones
      Connected : COM5
      RAS Connection : No

    >> Call configuration
      Wait for dialling tone before calling : Yes
      Cancel if the call does not succeed : Yes  ( in 0 s.)

  > SCSI Host #0 : 1 Device(s)

    >> Device Information #0
      Type : CD-Rom
      Specification : ATA/ATAPI
      Manufacturer : HL-DT-ST
      Name : DVDRAM GSA-T20L
      Revision : NC08
      Transfert : 8-bit
      Bus : 8-bit
      Multi-Port : No
      Normal ACA : Yes
      Connected : Yes
      Address : 0:0:0

    >> Device Recording Parameters #0
      Recorder Type : CD-RW
      Writing Speed : 62x
      Max. Writing Speed : 62x
      Audio Gap : 2 sec.

  > SCSI Host #2 : 1 Device(s)

    >> Device Information #0
      Type : Drive
      Specification : ATA/ATAPI
      Manufacturer : TOSHIBA
      Name : MK1237GSX
      Revision : DL13
      Transfert : 8-bit
      Bus : 8-bit
      Multi-Port : No
      Normal ACA : No
      Connected : Yes
      Address : 2:0:0

  > SCSI Host #3 : 1 Device(s)

    >> Device Information #0
      Type : Drive
      Specification : ATA/ATAPI
      Manufacturer : TOSHIBA
      Name : MK1237GSX
      Revision : DL13
      Transfert : 8-bit
      Bus : 8-bit
      Multi-Port : No
      Normal ACA : No
      Connected : Yes
      Address : 3:0:0

  > SCSI Host #5 : 1 Device(s)

    >> Device Information #0
      Type : CD-Rom
      Specification : SCSI-2
      Manufacturer : RH7065S
      Name : XFX251A
      Revision : 1.0 
      Transfert : 8-bit
      Bus : 8-bit
      Multi-Port : No
      Normal ACA : No
      Connected : Yes
      Address : 5:0:0

  > SCSI Controller : SCSI/RAID Ho

```

---

### Post by Ayuthia on 2008-02-01
> **MasterAslan said:**
> I am getting so frustrated.  I just can't figure out what is going on here.  When I boot up it hangs on starting bluetooth services.  By changing to tty5 and startx and then disable bluetooth.  Whenever I try lsusb it hangs.  Ndiswrapper -l and modprobe ndiswrapper hangs.  LSPCI lists the usb hardware just fine.  I just can't figure out why this all hangs.  I have tried nolapic, noapic and irqfixup and several combinations.  Is my hardware just not going to be supported here?  It is funny though bluetooth seems to actually work once I'm into X I can see my phone from it anyway.  There is something with the hardware that is just not quite right.  

Any ideas?  Wish I was a really experienced user that could do all my own debugging.

I want to use linux but I'm getting a bit exasperated.
Can you post the following information:
```
dmesg
cat /proc/interrupts
```
I am thinking that ndiswrapper and your usb modules are using the same interrupt so they are having the same problem.  The dmesg will help us see what kernel paramaters you are using and if you are experiencing any interrupt issues.  The second item will list out what is using which interrupt.  It might be a matter of using acpi=off as a parameter or maybe trying some other combination.  You mentioned that you have tried Hardy.  Did you try the 32 or 64 bit flavor?  I have heard that the 32-bit version have worked without the noapic options, but I have not tried it out myself.

---

### Post by MasterAslan on 2008-02-01
I would like to say that lsusb hangs and boot hangs at 'starting bluetooth services' before I even install ndiswrapper.  I have booted this time with acpi=off and it still is hanging.  I am on an install of hardy 64 right now without ndiswrapper installed.

dmesg output:
```
[    0.000000] Linux version 2.6.24-5-generic (buildd@yellow) (gcc version 4.2.3 20080114 (prerelease) (Ubuntu 4.2.2-7ubuntu1)) #1 SMP Thu Jan 24 19:29:14 UTC 2008 (Ubuntu 2.6.24-5.8-generic)
[    0.000000] Command line: root=UUID=208db64b-560b-4224-bfd9-9d91eed498b4 ro acpi=off
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff60000 (usable)
[    0.000000]  BIOS-e820: 000000007ff60000 - 000000007ff6e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff6e000 - 000000007ff6f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff6f000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524128) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ff60000
[    0.000000] Entering add_active_range(0, 0, 157) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524128) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ff60000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      157
[    0.000000]     0:      256 ->   524128
[    0.000000] On node 0 totalpages: 524029
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1207 pages reserved
[    0.000000]   DMA zone: 2734 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7109 pages used for memmap
[    0.000000]   DMA32 zone: 512923 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: nVIDIA   MPTABLE: Product ID: MCP65-EMU    MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] I/O APIC #2 at 0xFEC00000.
[    0.000000] Setting APIC routing to flat
[    0.000000] Processors: 2
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515657
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=208db64b-560b-4224-bfd9-9d91eed498b4 ro acpi=off
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PIT
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.000000] time.c: Detected 1808.207 MHz processor.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 6032000000 size 32 MB
[    0.000000] Aperture too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] Memory: 2054932k/2096512k available (2460k kernel code, 41184k reserved, 1302k data, 316k init)
[    0.000000] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] Calibrating delay using timer specific routine.. 3620.33 BogoMIPS (lpj=7240675)
[    0.000000] Security Framework initialized
[    0.000000] SELinux:  Disabled at boot.
[    0.000000] AppArmor: AppArmor initialized
[    0.000000] Failure registering capabilities with primary security module.
[    0.000000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.000000] Mount-cache hash table entries: 256
[    0.000000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.000000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.000000] CPU 0/0 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 0
[    0.000000] SMP alternatives: switching to UP code
[    0.000000] Early unpacking initramfs... done
[    0.000000] ExtINT not setup in hardware but reported by MP table
[    0.000000] Using local APIC timer interrupts.
[    0.000000] APIC timer calibration result 12556984
[    0.000000] Detected 12.556 MHz APIC timer.
[    0.000000] SMP alternatives: switching to SMP code
[    0.000000] Booting processor 1/2 APIC 0x1
[    0.000000] Initializing CPU#1
[    0.000000] Calibrating delay using timer specific routine.. 3616.40 BogoMIPS (lpj=7232811)
[    0.000000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.000000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.000000] CPU 1/1 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 1
[    0.000000] AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 01
[    0.000000] Brought up 2 CPUs
[    0.000000] CPU0 attaching sched-domain:
[    0.000000]  domain 0: span 03
[    0.000000]   groups: 01 02
[    0.000000]   domain 1: span 03
[    0.000000]    groups: 03
[    0.000000] CPU1 attaching sched-domain:
[    0.000000]  domain 0: span 03
[    0.000000]   groups: 02 01
[    0.000000]   domain 1: span 03
[    0.000000]    groups: 03
[    0.000000] net_namespace: 120 bytes
[    0.000000] Time: 19:38:04  Date: 02/01/08
[    0.000000] NET: Registered protocol family 16
[    0.000000] PCI: Using configuration type 1
[    0.000000] ACPI: Interpreter disabled.
[    0.000000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.000000] pnp: PnP ACPI: disabled
[    0.000000] PCI: Probing PCI hardware
[    0.000000] PCI: Probing PCI hardware (bus 00)
[    0.000000] PCI: Transparent bridge - 0000:00:08.0
[    0.000000] NET: Registered protocol family 8
[    0.000000] NET: Registered protocol family 20
[    0.000000] AppArmor: AppArmor Filesystem Enabled
[    0.000000] PCI: Bridge: 0000:00:08.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: f2100000-f21fffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:0b.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:0c.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: f2000000-f20fffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:05:00.0
[    0.000000] PCI: Bridge: 0000:00:0d.0
[    0.000000]   IO window: 4000-4fff
[    0.000000]   MEM window: cc000000-ceffffff
[    0.000000]   PREFETCH window: d0000000-dfffffff
[    0.000000] PCI: Bridge: 0000:00:0e.0
[    0.000000]   IO window: 5000-5fff
[    0.000000]   MEM window: f0000000-f1ffffff
[    0.000000]   PREFETCH window: f2600000-f27fffff
[    0.000000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.000000] NET: Registered protocol family 2
[    0.000000] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.000000] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.000000] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.000000] TCP: Hash tables configured (established 262144 bind 65536)
[    0.000000] TCP reno registered
[    0.000000] checking if image is initramfs... it is
[    0.000000] Freeing initrd memory: 7495k freed
[    0.000000] audit: initializing netlink socket (disabled)
[    0.000000] audit(1201894684.324:1): initialized
[    0.000000] VFS: Disk quotas dquot_6.5.1
[    0.000000] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.000000] io scheduler noop registered
[    0.000000] io scheduler anticipatory registered
[    0.000000] io scheduler deadline registered
[    0.000000] io scheduler cfq registered (default)
[    0.000000] Boot video device is 0000:05:00.0
[    0.000000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0b.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0c.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0d.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0e.0:pcie00]
[    0.000000] Real Time Clock Driver v1.12ac
[    0.000000] Linux agpgart interface v0.102
[    0.000000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    0.000000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.000000] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.000000] PNP: No PS/2 controller found. Probing ports directly.
[    0.000000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.000000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.000000] mice: PS/2 mouse device common for all mice
[    0.000000] cpuidle: using governor ladder
[    0.000000] cpuidle: using governor menu
[    0.000000] NET: Registered protocol family 1
[    0.000000] registered taskstats version 1
[    0.000000]   Magic number: 12:644:646
[    0.000000]   hash matches device ptydb
[    0.000000] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.000000] Freeing unused kernel memory: 316k freed
[    0.000000] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.000000] Clocksource tsc unstable (delta = 199959461 ns)
[    0.000000] fuse init (API version 7.9)
[    0.000000] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    0.000000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    0.000000] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    0.000000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.000000] SCSI subsystem initialized
[    0.000000] WARNING: at /build/buildd/linux-2.6.24/drivers/ssb/main.c:883 ssb_tmslow_reject_bitmask()
[    0.000000] Pid: 1318, comm: modprobe Not tainted 2.6.24-5-generic #1
[    0.000000] 
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff880118ca>] :ssb:ssb_tmslow_reject_bitmask+0x4a/0x60
[    0.000000]  [<ffffffff88012316>] :ssb:ssb_device_is_enabled+0x16/0x50
[    0.000000]  [<ffffffff88014731>] :ssb:ssb_pcicore_init+0x21/0x70
[    0.000000]  [<ffffffff88011656>] :ssb:ssb_attach_queued_buses+0x106/0x2d0
[    0.000000]  [<ffffffff88013250>] :ssb:ssb_pci_get_invariants+0x0/0x2d0
[    0.000000]  [<ffffffff88011d0e>] :ssb:ssb_bus_register+0x17e/0x200
[    0.000000]  [<ffffffff88011e22>] :ssb:ssb_bus_pcibus_register+0x32/0x60
[    0.000000]  [<ffffffff88013cdd>] :ssb:ssb_pcihost_probe+0x7d/0xc0
[    0.000000]  [<ffffffff80358278>] pci_device_probe+0xf8/0x170
[    0.000000]  [<ffffffff803b8d7c>] driver_probe_device+0x9c/0x1b0
[    0.000000]  [<ffffffff803b9049>] __driver_attach+0xc9/0xd0
[    0.000000]  [<ffffffff803b8f80>] __driver_attach+0x0/0xd0
[    0.000000]  [<ffffffff803b7fbd>] bus_for_each_dev+0x4d/0x80
[    0.000000]  [<ffffffff803b83cc>] bus_add_driver+0xac/0x220
[    0.000000]  [<ffffffff803584f9>] __pci_register_driver+0x69/0xb0
[    0.000000]  [<ffffffff8801c052>] :ssb:ssb_modinit+0x52/0x80
[    0.000000]  [<ffffffff80263a3e>] sys_init_module+0x18e/0x1a90
[    0.000000]  [<ffffffff803b85f0>] bus_register+0x0/0x270
[    0.000000]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[    0.000000] 
[    0.000000] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    0.000000] usbcore: registered new interface driver usbfs
[    0.000000] usbcore: registered new interface driver hub
[    0.000000] usbcore: registered new device driver usb
[    0.000000] libata version 3.00 loaded.
[    0.000000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.000000] forcedeth 0000:00:06.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:77:30:6a
[    0.000000] forcedeth 0000:00:06.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    0.000000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    0.000000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.000000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.000000] ehci_hcd 0000:00:02.1: debug port 1
[    0.000000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    0.000000] ehci_hcd 0000:00:02.1: irq 7, io mem 0xf2488000
[    0.000000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    0.000000] usb usb1: configuration #1 chosen from 1 choice
[    0.000000] hub 1-0:1.0: USB hub found
[    0.000000] hub 1-0:1.0: 10 ports detected
[    0.000000] pata_amd 0000:00:09.0: version 0.3.10
[    0.000000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    0.000000] scsi0 : pata_amd
[    0.000000] scsi1 : pata_amd
[    0.000000] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    0.000000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    0.000000] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.000000] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[    0.000000] usb 1-4: configuration #1 chosen from 1 choice
[    0.000000] ata1.00: configured for MWDMA2
[    0.000000] ata2: port disabled. ignoring.
[    0.000000] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[    0.000000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.000000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.000000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.000000] ohci_hcd 0000:00:02.0: irq 11, io mem 0xf2486000
[    0.000000] usb usb2: configuration #1 chosen from 1 choice
[    0.000000] hub 2-0:1.0: USB hub found
[    0.000000] hub 2-0:1.0: 10 ports detected
[    0.000000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[15]  MMIO=[f2100000-f21007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    0.000000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    0.000000] ahci 0000:00:0a.0: version 3.0
[    0.000000] usb 2-9: new full speed USB device using ohci_hcd and address 2
[    0.000000] usb 2-9: configuration #1 chosen from 1 choice
[    0.000000] ahci 0000:00:0a.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    0.000000] ahci 0000:00:0a.0: flags: 64bit ncq sntf pm led clo pmp pio 
[    0.000000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    0.000000] scsi2 : ahci
[    0.000000] scsi3 : ahci
[    0.000000] scsi4 : ahci
[    0.000000] scsi5 : ahci
[    0.000000] ata3: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484100 irq 5
[    0.000000] ata4: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484180 irq 5
[    0.000000] ata5: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484200 irq 5
[    0.000000] ata6: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484280 irq 5
[    0.000000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0058c23e00]
[    0.000000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.000000] ata3.00: ATA-7: TOSHIBA MK1237GSX, DL132C, max UDMA/100
[    0.000000] ata3.00: 234441648 sectors, multi 16: LBA48 
[    0.000000] ata3.00: configured for UDMA/100
[    0.000000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.000000] ata4.00: ATA-7: TOSHIBA MK1237GSX, DL132C, max UDMA/100
[    0.000000] ata4.00: 234441648 sectors, multi 16: LBA48 
[    0.000000] ata4.00: configured for UDMA/100
[    0.000000] ata5: SATA link down (SStatus 0 SControl 300)
[    0.000000] ata6: SATA link down (SStatus 0 SControl 300)
[    0.000000] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL13 PQ: 0 ANSI: 5
[    0.000000] scsi 3:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL13 PQ: 0 ANSI: 5
[    0.000000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    0.000000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    0.000000] Driver 'sd' needs updating - please use bus_type methods
[    0.000000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    0.000000] sd 2:0:0:0: [sda] Write Protect is off
[    0.000000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.000000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    0.000000] sd 2:0:0:0: [sda] Write Protect is off
[    0.000000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.000000] Driver 'sr' needs updating - please use bus_type methods
[    0.000000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.000000] Uniform CD-ROM driver Revision: 3.20
[    0.000000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.000000]  sda1
[    0.000000] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.000000] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[    0.000000] sd 3:0:0:0: [sdb] Write Protect is off
[    0.000000] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.000000] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[    0.000000] sd 3:0:0:0: [sdb] Write Protect is off
[    0.000000] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.000000] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000]  sdb: sdb1 sdb2 < sdb5 >
[    0.000000] sd 3:0:0:0: [sdb] Attached SCSI disk
[    0.000000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.000000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.000000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    0.000000] Attempting manual resume
[    0.000000] swsusp: Resume From Partition 8:21
[    0.000000] PM: Checking swsusp image.
[    0.000000] PM: Resume from disk failed.
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.000000] input: PC Speaker as /devices/platform/pcspkr/input/input2
[    0.000000] shpchp: Unknown symbol acpi_run_oshp
[    0.000000] shpchp: Unknown symbol pci_hp_change_slot_info
[    0.000000] shpchp: Unknown symbol pci_hp_register
[    0.000000] shpchp: Unknown symbol pci_hp_deregister
[    0.000000] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[    0.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.000000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[    0.000000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[    0.000000] ricoh-mmc: Ricoh MMC Controller disabling driver
[    0.000000] ricoh-mmc: Copyright(c) Philip Langdale
[    0.000000] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 12)
[    0.000000] ricoh-mmc: Controller is now disabled.
[    0.000000] sdhci: Secure Digital Host Controller Interface driver
[    0.000000] sdhci: Copyright(c) Pierre Ossman
[    0.000000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 22)
[    0.000000] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[    0.000000] mmc0: SDHCI at 0xf2100800 irq 10 DMA
[    0.000000] ieee80211_crypt: registered algorithm 'NULL'
[    0.000000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[    0.000000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    0.000000] bcm43xx driver
[    0.000000] Linux video capture interface: v2.00
[    0.000000] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1812)
[    0.000000] general protection fault: 0000 [1] SMP 
[    0.000000] CPU 1 
[    0.000000] Modules linked in: uvcvideo snd_seq snd_timer snd_seq_device compat_ioctl32 videodev bcm43xx v4l1_compat ieee80211softmac v4l2_common ieee80211 ieee80211_crypt snd psmouse sdhci serio_raw ricoh_mmc i2c_nforce2 i2c_core shpchp mmc_core soundcore pcspkr evdev pci_hotplug snd_page_alloc k8temp ext3 jbd mbcache sg sr_mod sd_mod cdrom amd74xx ide_core ahci pata_acpi ohci1394 ieee1394 ata_generic ohci_hcd pata_amd ehci_hcd libata usbcore scsi_mod forcedeth ssb fuse
[    0.000000] Pid: 3023, comm: modprobe Not tainted 2.6.24-5-generic #1
[    0.000000] RIP: 0010:[<ffffffff88280763>]  [<ffffffff88280763>] :uvcvideo:uvc_get_video_ctrl+0x153/0x1a0
[    0.000000] RSP: 0018:ffff81007d25da98  EFLAGS: 00010286
[    0.000000] RAX: e914788d44029044 RBX: ffff81007df457c0 RCX: ffff81007ccd67c8
[    0.000000] RDX: 0000000000000000 RSI: ffff810001019ea0 RDI: ffffffff805be298
[    0.000000] RBP: 000000000000001a R08: 0000000000000000 R09: ffff81007fe5c788
[    0.000000] R10: ffff81000101cfe0 R11: 0000000000000001 R12: ffff81007cc1c048
[    0.000000] R13: ffff81007df45780 R14: ffff81007df457c0 R15: ffff81007cc1c048
[    0.000000] FS:  00007fcb7ebb16e0(0000) GS:ffff81007dc01700(0000) knlGS:0000000000000000
[    0.000000] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[    0.000000] CR2: 00007f15448b7000 CR3: 000000007c035000 CR4: 00000000000006e0
[    0.000000] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[    0.000000] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[    0.000000] Process modprobe (pid: 3023, threadinfo ffff81007d25c000, task ffff81007c302000)
[    0.000000] Stack:  ffffffff0000001a ffffffff000003e8 0000000000000000 0000000000000000
[    0.000000]  0000000000000000 ffffffff80230000 0000003000000030 ffff81007d25dba8
[    0.000000]  0000000000000001 ffff81007cd5d900 ffff81007cc1c048 ffffffff88280925
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff80230000>] putreg32+0x2b0/0x320
[    0.000000]  [<ffffffff88280925>] :uvcvideo:uvc_video_init+0x35/0x160
[    0.000000]  [<ffffffff8827b8b9>] :uvcvideo:uvc_register_video+0x489/0x6c0
[    0.000000]  [<ffffffff8827c425>] :uvcvideo:uvc_probe+0x755/0x1ae0
[    0.000000]  [<ffffffff802c2302>] iput+0x42/0x80
[    0.000000]  [<ffffffff880662fa>] :usbcore:usb_probe_interface+0xda/0x160
[    0.000000]  [<ffffffff803b8d7c>] driver_probe_device+0x9c/0x1b0
[    0.000000]  [<ffffffff803b9049>] __driver_attach+0xc9/0xd0
[    0.000000]  [<ffffffff803b8f80>] __driver_attach+0x0/0xd0
[    0.000000]  [<ffffffff803b7fbd>] bus_for_each_dev+0x4d/0x80
[    0.000000]  [<ffffffff803b83cc>] bus_add_driver+0xac/0x220
[    0.000000]  [<ffffffff88065da9>] :usbcore:usb_register_driver+0xa9/0x120
[    0.000000]  [<ffffffff8801c080>] :uvcvideo:uvc_init+0x80/0x98
[    0.000000]  [<ffffffff80263a3e>] sys_init_module+0x18e/0x1a90
[    0.000000]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[    0.000000] 
[    0.000000] 
[    0.000000] Code: 8b 40 e8 89 43 14 48 83 c4 40 31 c0 5b 5d 41 5c c3 31 c0 48 
[    0.000000] RIP  [<ffffffff88280763>] :uvcvideo:uvc_get_video_ctrl+0x153/0x1a0
[    0.000000]  RSP <ffff81007d25da98>
[    0.000000] ---[ end trace d144f1ee31be1790 ]---
[    0.000000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.000000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[    0.000000] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input3
[    0.000000] loop: module loaded
[    0.000000] lp: driver loaded but no devices found
[    0.000000] Adding 4803392k swap on /dev/sdb5.  Priority:-1 extents:1 across:4803392k
[    0.000000] EXT3 FS on sdb1, internal journal
[    0.000000] powernow_k8: Unknown symbol acpi_processor_notify_smm
[    0.000000] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[    0.000000] powernow_k8: Unknown symbol acpi_processor_register_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[    0.000000] NET: Registered protocol family 10
[    0.000000] lo: Disabled Privacy Extensions
[    0.000000] ppdev: user-space parallel port driver
[    0.000000] audit(1201894704.212:2): operation="inode_permission" request_mask="a::" denied_mask="a::" name="/dev/tty" pid=4810 profile="/usr/sbin/cupsd" namespace="default"
[    0.000000] Bluetooth: Core ver 2.11
[    0.000000] NET: Registered protocol family 31
[    0.000000] Bluetooth: HCI device and connection manager initialized
[    0.000000] Bluetooth: HCI socket layer initialized
[    0.000000] Bluetooth: L2CAP ver 2.9
[    0.000000] Bluetooth: L2CAP socket layer initialized
[    0.000000] Bluetooth: RFCOMM socket layer initialized
[    0.000000] Bluetooth: RFCOMM TTY layer initialized
[    0.000000] Bluetooth: RFCOMM ver 1.8
[    0.000000] NET: Registered protocol family 17
[    0.000000] eth0: no IPv6 routers present

```

interrupts:
```
           CPU0       CPU1       
  0:        843          0   IO-APIC-edge      timer
  1:          0       1402   IO-APIC-edge      i8042
  2:          0          0    XT-PIC-XT        cascade
  5:          6      14365   IO-APIC-edge      ahci
  7:          0         16   IO-APIC-edge      ehci_hcd:usb1
  8:          0          0   IO-APIC-edge      rtc
 10:         75      68345   IO-APIC-edge      sdhci:slot0, eth0
 11:          0        603   IO-APIC-edge      ohci_hcd:usb2, HDA Intel
 12:         79     181471   IO-APIC-edge      i8042
 14:          0        857   IO-APIC-edge      libata
 15:          0          3   IO-APIC-edge      libata, ohci1394
NMI:          0          0   Non-maskable interrupts
LOC:     140767     140566   Local timer interrupts
RES:      15266       6905   Rescheduling interrupts
CAL:        124         92   function call interrupts
TLB:        556        447   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
SPU:          0          0   Spurious interrupts
ERR:          0

```

---

### Post by MasterAslan on 2008-02-01
New development booting acpi=off on the gutsy live cd allows me to hit lsusb without hanging.  I will try to install this and run ndiswrapper.  What implications is there for running with this boot parameter?  Is there possibly any other alternatives?

Edit: acpi=off worked twice on the live cd then stopped working.  Now getting kernel panic

edit 2: installed gutsy again and booted with apci=off and noapic and lsusb is hanging again.  There must be something that live cd does not load that the installed system does.

---

### Post by Ayuthia on 2008-02-02
> **MasterAslan said:**
> I would like to say that lsusb hangs and boot hangs at 'starting bluetooth services' before I even install ndiswrapper.  I have booted this time with acpi=off and it still is hanging.  I am on an install of hardy 64 right now without ndiswrapper installed.

dmesg output:
```

[    0.000000] Linux video capture interface: v2.00
[    0.000000] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1812)
[    0.000000] general protection fault: 0000 [1] SMP 
[    0.000000] CPU 1 
[    0.000000] Modules linked in: uvcvideo snd_seq snd_timer snd_seq_device compat_ioctl32 videodev bcm43xx v4l1_compat ieee80211softmac v4l2_common ieee80211 ieee80211_crypt snd psmouse sdhci serio_raw ricoh_mmc i2c_nforce2 i2c_core shpchp mmc_core soundcore pcspkr evdev pci_hotplug snd_page_alloc k8temp ext3 jbd mbcache sg sr_mod sd_mod cdrom amd74xx ide_core ahci pata_acpi ohci1394 ieee1394 ata_generic ohci_hcd pata_amd ehci_hcd libata usbcore scsi_mod forcedeth ssb fuse
[    0.000000] Pid: 3023, comm: modprobe Not tainted 2.6.24-5-generic #1
[    0.000000] RIP: 0010:[<ffffffff88280763>]  [<ffffffff88280763>] :uvcvideo:uvc_get_video_ctrl+0x153/0x1a0
[    0.000000] RSP: 0018:ffff81007d25da98  EFLAGS: 00010286
[    0.000000] RAX: e914788d44029044 RBX: ffff81007df457c0 RCX: ffff81007ccd67c8
[    0.000000] RDX: 0000000000000000 RSI: ffff810001019ea0 RDI: ffffffff805be298
[    0.000000] RBP: 000000000000001a R08: 0000000000000000 R09: ffff81007fe5c788
[    0.000000] R10: ffff81000101cfe0 R11: 0000000000000001 R12: ffff81007cc1c048
[    0.000000] R13: ffff81007df45780 R14: ffff81007df457c0 R15: ffff81007cc1c048
[    0.000000] FS:  00007fcb7ebb16e0(0000) GS:ffff81007dc01700(0000) knlGS:0000000000000000
[    0.000000] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[    0.000000] CR2: 00007f15448b7000 CR3: 000000007c035000 CR4: 00000000000006e0
[    0.000000] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[    0.000000] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[    0.000000] Process modprobe (pid: 3023, threadinfo ffff81007d25c000, task ffff81007c302000)
[    0.000000] Stack:  ffffffff0000001a ffffffff000003e8 0000000000000000 0000000000000000
[    0.000000]  0000000000000000 ffffffff80230000 0000003000000030 ffff81007d25dba8
[    0.000000]  0000000000000001 ffff81007cd5d900 ffff81007cc1c048 ffffffff88280925
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff80230000>] putreg32+0x2b0/0x320
[    0.000000]  [<ffffffff88280925>] :uvcvideo:uvc_video_init+0x35/0x160
[    0.000000]  [<ffffffff8827b8b9>] :uvcvideo:uvc_register_video+0x489/0x6c0
[    0.000000]  [<ffffffff8827c425>] :uvcvideo:uvc_probe+0x755/0x1ae0
[    0.000000]  [<ffffffff802c2302>] iput+0x42/0x80
[    0.000000]  [<ffffffff880662fa>] :usbcore:usb_probe_interface+0xda/0x160
[    0.000000]  [<ffffffff803b8d7c>] driver_probe_device+0x9c/0x1b0
[    0.000000]  [<ffffffff803b9049>] __driver_attach+0xc9/0xd0
[    0.000000]  [<ffffffff803b8f80>] __driver_attach+0x0/0xd0
[    0.000000]  [<ffffffff803b7fbd>] bus_for_each_dev+0x4d/0x80
[    0.000000]  [<ffffffff803b83cc>] bus_add_driver+0xac/0x220
[    0.000000]  [<ffffffff88065da9>] :usbcore:usb_register_driver+0xa9/0x120
[    0.000000]  [<ffffffff8801c080>] :uvcvideo:uvc_init+0x80/0x98
[    0.000000]  [<ffffffff80263a3e>] sys_init_module+0x18e/0x1a90
[    0.000000]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[    0.000000] 
[    0.000000] 
[    0.000000] Code: 8b 40 e8 89 43 14 48 83 c4 40 31 c0 5b 5d 41 5c c3 31 c0 48 
[    0.000000] RIP  [<ffffffff88280763>] :uvcvideo:uvc_get_video_ctrl+0x153/0x1a0
[    0.000000]  RSP <ffff81007d25da98>
[    0.000000] ---[ end trace d144f1ee31be1790 ]---


```
Well, it looks like the general protection fault was a problem with acpi=off.  Do you know if you tried noapic noirqdebug?  I don't know if that will help or not.  The other route to try is to add nosmp to the list of your noapic parameters.  If I recall, it will turn off one of your cores (might stop the fault).  You also might try the 32-bit version of Hardy.

Can you check and see what dmesg says when you just use noapic?  Also, what happens when you don't use any parameters?  If it stops during boot, where does it stop?

---

### Post by EXCiD3 on 2008-02-02
> **Ayuthia said:**
> You also might try the 32-bit version of Hardy

I agree. The 32 bit versions are much more reliable and compatible at the moment. Alpha 4 of Hardy has just been released.You can download it here: [http://cdimage.ubuntu.com/releases/hardy/alpha-4/](http://cdimage.ubuntu.com/releases/hardy/alpha-4/)

---

### Post by JimmyBEng on 2008-02-02
MasterAslan:  If you look at dmesg the uvcvideo module is crasing, and messing with your usb this causes the lsusb to hang and bluetooth to hang etc.  this happened with my laptop also.  give this a try.
```
sudo gedit /etc/modprobe.d/blacklist
```
add the following lines to the bottom.
```
# causes error with ricoh 1812 webcam that disables USB
blacklist uvcvideo
```
restart and see if that helps.

this is disabling the uvcvideo webcam module, so it may make it more difficult to get your webcam working.  Although, if usb wasn't working, i doubt your webcam was.

---

### Post by MasterAslan on 2008-02-02
THANK YOU

Can now boot after blacklisting uvcvideo with no boot options.  Doesn't freeze and lsusb runs.  Don't have time to test everything but if anyone else gets this issue please try that.  Thanks again.  Been trouble for days.

Now the question is...is there some driver or something I can download to enable uvcvideo?

---

### Post by A Pragmaticist on 2008-02-02
bump

---

### Post by Elv13 on 2008-02-03
Hi, i am trying to install Ubuntu on a friend laptop, but this laptop (dv9000) make me crazy!!!!!

I can not boot in grapphic mode, including with vesa driver +gdm (just startx fres rescue shell work with vesa, but not nvidia)

I dont have ethernet 

I did install Feisty with alternate cd then i sshed into it to upgrade to gutsy because feisty was getting KP every 30 second, but now, at the exeption of kp, nothing work...

I dont have time to read the complete thread, if someone can link me to the right post, it would save me a lot of time that i dont have.

And why every distribution more recent than 1 years dont start X and older yes!?!

---

### Post by MasterAslan on 2008-02-03
Have you tried manually installing the nvidia drivers?  Try the boot option forcevesa.  Could you give some more info on your errors?

---

### Post by psharboneaux on 2008-02-05
Hello,

I have an HP Pavilion dv9308nr laptop.  When trying to install Ubuntu 7.04, I had to use the following kernel parameters;

nomsi nomce irqpoll pnpbios=off

When trying to install Ubuntu 7.10, these parameters did not work.  I tried the above mentioned parameters, and they did not work either.

So, I decided combining both sets of parameters as follows;

**nomsi nomce noapic irqpoll pnpbios=off noirqdebug**

My laptop booted into the Ubuntu 7.10 LiveCD without problems. managed to install Ubuntu, and now my laptop is running just fine.

---

### Post by HippyRandall on 2008-02-05
lspci:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

lsusb:

Bus 002 Device 002: ID 0c45:62c0 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c03f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

the logitech in lsusb is my usb mouse.

I was able to get everything but the wireless card working. I am still working on that. I assume that according to lspci I have a Broadcom 4328? Any tips on how to get this working?
I cannot thank you all enough for this great guide. I thought I would be stuck in Vista forever.

Thanks sooo much,
Hippy Randall

---

### Post by MasterAslan on 2008-02-06
Hippy Randall have you tried ndiswrapper yet?  Can you run lspci -nn and give us the output?

---

### Post by skinnie on 2008-02-06
as anyone tried alsa 1.0.16 on dv9500?1.0.15 used to work for me using the hda intel sound how to tutorial,but with 1.0.16 it doesn't work :(

---

### Post by EXCiD3 on 2008-02-06
> **skinnie said:**
> as anyone tried alsa 1.0.16 on dv9500?1.0.15 used to work for me using the hda intel sound how to tutorial,but with 1.0.16 it doesn't work :(

Which version of ubuntu are you using?

---

### Post by slkwcy on 2008-02-09
For some funny reason, I did not know how I was able to load into Ubuntu i386 without any boot option as stated in my first post.  After my post, I went ahead and installed Gutsy Ubuntu AMD64.  noapic option was then needed again.  But the suspend to RAM was working no problem.  Then after upgrading it to Ubuntu Studio, suspend to ram fail.

Right after that, I did a reinstall to Gutsy Kubuntu AMD64, noapic was required but suspend to RAM was working until a recent Kernel upgrade.  I don't recall the version and I don't seem to be able to find anywhere in the web.  Anyhow, with that upgrade, suspend to RAM was wracked and I was trying to put the old Kernel back.  As being a newbie, I have no idea what I did, Suspend to Ram problem remain no matter what I tried fixing it.  Without wasted more time, I reinstall Kubuntu.

With some frustrations with AMD64, I had i386 version installed this time.  noapic was needed and suspend to ram was still a problem despite a new installation.

Then I searched and this came up: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI), a very good documentation explaining ACPI options.  But this is the line that really point me to a right direction: " Try to hibernate/suspend and then restart the system and attach /var/log/kern.log."  By reading this log, I discovered that it suggested me to use at the boot option... pci=routeirq

So in summary, at my boot option, I took out the noapic and use only pci=routeirq, magically my kubuntu was able to run, but more importantly suspend to ram is working as well.

Since with my first experience taught me that what is working now may not work the next time,  So I will continue do more testing to confirm what I found is the ultimate solution.

Again my laptop is HP Dv9005ca.
currently running Gutsy Gibbon i386 Kubuntu.

> **slkwcy said:**
> First, I like to thanks EXCiD3 for posting a how-to for HP laptop.

I was first installed Gutsy to my wife's Sony Laptop (about 2 years old), and it was installed so smoothly everything just work right out of the box.

Then when I started to install Gutsy to my HP laptop (dv9005) things are starting to be challenging.  

Anyways, I am so happy that I like to report that my suspend and hibernate are now working, with no option added to the boot menu (menu.lst).  \\:D/

I only have to add "NvAGP" "1" in xorg.conf as an option under device.

But in order to be able to boot into LiveCD for fresh installation, noapic still required I believe.

---

### Post by jamer on 2008-02-11
Hey. I'm a complete noob at this linux stuff. I read through this article on how to install Ubuntu on my HP DV6000. I installed it using the alternet cd and it installed fine except for every time I try to load the OS, it only loads like...1 fifth of the way through on the start up screen and then nothing happens. it's like my computer is frozen. My friend seems to think it's a video card problem but neither of us have any clue as to what it is we need to do. 

Any help would be greatly appreciated.

Jamer

---

### Post by HippyRandall on 2008-02-11
> **MasterAslan said:**
> Hippy Randall have you tried ndiswrapper yet?  Can you run lspci -nn and give us the output?

sorry been gone for a few days. I did finally get my wireless up and running but here is the output of lspci -nn you asked for:

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 PCI Express Bridge [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation Unknown device [14e4:4328] (rev 03)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832]
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

The only real problems I am having now are on reboot/shutdown and coming out of suspend.
On a reboot/shutdown the system sometimes(read most times) hangs at a black screen and nothing I do gets me out of it. I have tried alt+ctrl+bckspace, ...f1,f7, alt+sysreq+r and all sorts of other variations that I read about in another thread with no change.
On coming out of suspend my network fails to reconnect. either through my wireless or wired connection. /shrug
I am so happy with just having this up and running. I first tried linux about 11 years ago and have fiddled with it from time to time over the intervening years but this is far and away the best and most stable I have ever been.

Thanks for all the help with this guide and the forums in general.

Hippy

---

### Post by Ayuthia on 2008-02-11
> **jamer said:**
> Hey. I'm a complete noob at this linux stuff. I read through this article on how to install Ubuntu on my HP DV6000. I installed it using the alternet cd and it installed fine except for every time I try to load the OS, it only loads like...1 fifth of the way through on the start up screen and then nothing happens. it's like my computer is frozen. My friend seems to think it's a video card problem but neither of us have any clue as to what it is we need to do. 

Any help would be greatly appreciated.

Jamer
Welcome!

If you have an AMD and Nvidia combination, there is a good chance that you will need to use some kind of noapic combination when you load the OS.  If you are doing it from the CD, press F6 and add noapic to the end of the line.

You might check the first post (step 2) to see how to get it started.  I am currently using noapic noirqdebug.  Hope that helps.

---

### Post by MasterAslan on 2008-02-16
I got my headphones to mute the main speakers. Found it on a post for another laptop and its so simple.

> Fixing the Sound Card
For some reason my laptop speakers refused to auto-mute when the headphones were plugged in. If your laptop is doing this as well simply open up the file /etc/modprobe.d/alsa-base and add "options snd-hda-intel model=laptop" to a new line. Note: This may require you to update to alsa 1.0.15, if you find this is the case or just want to upgrade alsa simply follow these steps.


---

### Post by MikeDK on 2008-02-18
I was wondering about the sata disks, but the disks is not sata, they are using sata adapters.

my screen has just crashed after the kernel upgrade, and im sending it for repair at the local store, bought it 05/14/2007 so theres still warranty on it, sitting on my dell latitude C540 at the moment, running hardy.

Kind Regards MikeDK

---

### Post by EXCiD3 on 2008-02-18
> **MikeDK said:**
> I was wondering about the sata disks, but the disks is not sata, they are using sata adapters.

my screen has just crashed after the kernel upgrade, and im sending it for repair at the local store, bought it 05/14/2007 so theres still warranty on it, sitting on my dell latitude C540 at the moment, running hardy.

Kind Regards MikeDK

IDE Drives using sata adapters will probably still show up as sata drives. This prevents XP from installing unless you slipstream the sata driver into a custom XP disc as XP was released *before* sata drives. Vista supports these and so does Linux. Was there any help u needed with your drives?

---

### Post by MikeDK on 2008-02-18
my fault, its the other way around, its SATA disks using ATA/IDE adapters

Kind regards MikeDK

My lap is a DV9232eu AMD TL-52

---

### Post by Denbert on 2008-02-19
I'm trying to install 7.04 on dv6565eo - Live CD works fine with sound and all - The install hangs at 90% while install USB.

Any suggestions?

/ Denbert

---

### Post by WildWillie on 2008-02-19
Hey guys. I've been looking at this thread for a few weeks and couldn't find the answers, so please don't stab me too quickly if it's obvious. Here goes nothing:

I'm using a DV9730us. It seems to be just new enough that the walkthrough doesn't  work.

I installed with the 7.04 Feisty, and it hung at 85% for a good while and did nothing, so I rebooted and the GRUB hadn't been fully installed, so I couldn't even load my XP partition. Frowns. I tried again, resizing the partition and going back through the install. It hung again, but I just left it and while I was sleeping I heard it spin up and finish the install fully an hour later.

My comp uses GeForce 7150, and Ubuntu can't seem to do anything with it. X will not start. This isn't all that strange since Fedora didn't know what to do either, but I was at least able to use a textless browser and download and sh Nvidia's driver for the card and then it worked fine. (I'm switching to Ubuntu because this thread made it seem like everything would work). There is not textless on the 7.04 disc and aptitude doesn't seem to be able to put one in, so it's also possible that my ethernet isn't working either, although on bootup it seems to work fine, and ifconfig shows what looks like workable circumstances.

Any suggestions? I feel like a lot more of this should be working out of the box....

---

### Post by EXCiD3 on 2008-02-19
> **WildWillie said:**
> Hey guys. I've been looking at this thread for a few weeks and couldn't find the answers, so please don't stab me too quickly if it's obvious. Here goes nothing:

I'm using a DV9730us. It seems to be just new enough that the walkthrough doesn't  work.

I installed with the 7.04 Feisty, and it hung at 85% for a good while and did nothing, so I rebooted and the GRUB hadn't been fully installed, so I couldn't even load my XP partition. Frowns. I tried again, resizing the partition and going back through the install. It hung again, but I just left it and while I was sleeping I heard it spin up and finish the install fully an hour later.

My comp uses GeForce 7150, and Ubuntu can't seem to do anything with it. X will not start. This isn't all that strange since Fedora didn't know what to do either, but I was at least able to use a textless browser and download and sh Nvidia's driver for the card and then it worked fine. (I'm switching to Ubuntu because this thread made it seem like everything would work). There is not textless on the 7.04 disc and aptitude doesn't seem to be able to put one in, so it's also possible that my ethernet isn't working either, although on bootup it seems to work fine, and ifconfig shows what looks like workable circumstances.

Any suggestions? I feel like a lot more of this should be working out of the box....

Have you tried using the Alternate disc. Also you should note that this was tutorial was written as a general guideline for the HP laptops released around christmas of last year. Have you tried searching the forums/google for ubuntu on your specific laptop model? There are MANY tutorials floating around and this is just one that inspired many others. Don't give up yet. What exact hardware and laptop model do you have? I'd be glad to help get you started in the right direction at least.

---

### Post by WildWillie on 2008-02-20
I am using the alternate disc, I have googled lots and lots. I have found nothing.

HP dv9730us:
   	
Processor: AMD Turion 64 X2 Dual-Core Mobile Technology TL-64 (2.2 GHz, 512KB+512KB L2 Cache)
HD: 250gb
RAM: 3gb
Optical: supermulti blah blah blah
Video: Nvidia GeForce 7150m
Ethernet: Nvidia something or other
Wireless: broadcom 
Audio: connexant

Unfortunately I can't be more specific because xp can't actually "see" the wireless and audio, and linux can't until I get the video driver in.

---

### Post by MasterAslan on 2008-02-20
> **Denbert said:**
> I'm trying to install 7.04 on dv6565eo - Live CD works fine with sound and all - The install hangs at 90% while install USB.

Any suggestions?

/ Denbert

Hi Denbert,

Yes I think I can help you.  This happened to me also.  You will need to use the alternate install CD.    Most likely the cause is the uvcvideo is not compatible with your webcam.  Once you install with the  alternate install it will most likely hang on boot at 'loading bluetooth service'.  It doesn't actually have to do with bluetooth but the fact that its messing up your usb.  Once your at this point ctrl+alt+F7 or F6 or whatever.  Then:

```
sudo nano /etc/modprobe.d/blacklist 
```


add 
```
# incompatible with current webcam hardware
blacklist uvcvideo
```
and save and exit

Now 

```
sudo reboot
```

You SHOULD be able to boot into your system now.

I guess it could be another hardware component that is messing it up for you but thats what it was for me.  Give it a go and see what happens.

---

### Post by MasterAslan on 2008-02-20
> **WildWillie said:**
> Hey guys. I've been looking at this thread for a few weeks and couldn't find the answers, so please don't stab me too quickly if it's obvious. Here goes nothing:

I'm using a DV9730us. It seems to be just new enough that the walkthrough doesn't  work.

I installed with the 7.04 Feisty, and it hung at 85% for a good while and did nothing, so I rebooted and the GRUB hadn't been fully installed, so I couldn't even load my XP partition. Frowns. I tried again, resizing the partition and going back through the install. It hung again, but I just left it and while I was sleeping I heard it spin up and finish the install fully an hour later.

My comp uses GeForce 7150, and Ubuntu can't seem to do anything with it. X will not start. This isn't all that strange since Fedora didn't know what to do either, but I was at least able to use a textless browser and download and sh Nvidia's driver for the card and then it worked fine. (I'm switching to Ubuntu because this thread made it seem like everything would work). There is not textless on the 7.04 disc and aptitude doesn't seem to be able to put one in, so it's also possible that my ethernet isn't working either, although on bootup it seems to work fine, and ifconfig shows what looks like workable circumstances.

Any suggestions? I feel like a lot more of this should be working out of the box....

If your ethernet IS working you can always use wget

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
sudo sh NVIDIA-Linux-x86-169.09-pkg1.run
```

and reboot.

This should get you running.

Otherwise have you tried the forcevesa boot option so you can get into x and set up that way?

---

### Post by blumagic on 2008-02-21
All,

I just received my dv9700t laptop. I am having multiple problems with sound, wireless and my cdrom drive isnt working. Just trying to keep drive bay open results in:

eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for : `cdrom'

Any ideas how to resolve this issue?

I am still working on the sound and wireless, but this has been a difficult install. Not user friendly at all...

thanks,
blu.....

---

### Post by WildWillie on 2008-02-22
wget throws an error that it can't write. If I sudo it, there's no error, but either way, it downloads an html file, although if I put in the same url to firefox in xp, it downloads normally. What's broke here?

---

### Post by MasterAslan on 2008-02-22
WildWillie

Try this

```
wget download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```

Getting rid of the http:// worked for me.  Let me know if this doesn't work.  I can see about uploading the file to somewhere else if needed.
 
Are you downloading this to your home directory?  If not then thats why you have to sudo it.  Although as long as you can get the file thats all that matters.

blumagic have you tried any of the boot options that the thread starts with?

---

### Post by Ayuthia on 2008-02-22
> **WildWillie said:**
> wget throws an error that it can't write. If I sudo it, there's no error, but either way, it downloads an html file, although if I put in the same url to firefox in xp, it downloads normally. What's broke here?

When you use wget, it will download the file to the directory that you are currently at.  From what it sounds like, you were in a directory that you did not have write permission.  If you tried using wget in your home directory, you should not experience this.

---

### Post by chelfc on 2008-02-22
w00t!! will try this when i get home. Thanks looks like this might fix my installation problems!

---

### Post by WildWillie on 2008-02-22
The weird thing about my home directory is there is nothing in it besides something called Examples and the spurious html crap that I downloaded. Is this indicative of something going terribly wrong on install? Don't we normally keep Desktop in here?

I tried w/o the http and it still farted.

---

### Post by Ayuthia on 2008-02-22
> **WildWillie said:**
> The weird thing about my home directory is there is nothing in it besides something called Examples and the spurious html crap that I downloaded. Is this indicative of something going terribly wrong on install? Don't we normally keep Desktop in here?

I tried w/o the http and it still farted.
Upon install, it should have created the Desktop folder.  Since you have an Nvidia/AMD combo, do you use any type of boot/kernel parameter?  If you have no clue what I am talking about, can you post the following:
```
cat /proc/cmdline
```
Also, do you know if you installed the desktop version or the server version of Ubuntu?  The server edition does not come with GUI.  If you do have the desktop edition, do you see any error messages in dmesg?

---

### Post by Denbert on 2008-02-23
Trying to install Ubuntu 7.04 on

dv6565eo - dualcore AMD - nVIDIA 8400 GS - 2 gb RAM - 200 gb HDD

X fails to start - log says:

No screen found

Anyone seen this, and have a work around?

---

### Post by skinnie on 2008-02-23
> **Denbert said:**
> Trying to install Ubuntu 7.04 on

dv6565eo - dualcore AMD - nVIDIA 8400 GS - 2 gb RAM - 200 gb HDD

X fails to start - log says:

No screen found

Anyone seen this, and have a work around?

why don't u try 7.10,I think that could help too..

---

### Post by Denbert on 2008-02-23
I didn't try version 7.10 due to this in the start of this tread:

If you have an HP Laptop - especially an HP 6000 or 9000 series laptop, steer clear of Gutsy 7.10 release. 

Are you running 7.10?

I'm downloading it now.

---

### Post by skinnie on 2008-02-23
> **Denbert said:**
> I didn't try version 7.10 due to this in the start of this tread:

If you have an HP Laptop - especially an HP 6000 or 9000 series laptop, steer clear of Gutsy 7.10 release. 

Are you running 7.10?

I'm downloading it now.

with my dv9575ep all run good in 7.10,only had to upgrade alsa.
Now I am using the 8.04 alpha,because one day,on a fresh ubuntu 7.10 install it refused to have sound,no matter what alsa I compiled,with upgrades,without,so 8.04 :D

---

### Post by Denbert on 2008-02-24
> **EXCiD3 said:**
> 

**     Bluetooth**
        Works out of the box



After install machine hangs under first boot up under loading bluetooth module.

How do I skip loading bluetooth under boot up?

---

### Post by MasterAslan on 2008-02-24
> **Denbert said:**
> After install machine hangs under first boot up under loading bluetooth module.

How do I skip loading bluetooth under boot up?

I had posted this above but I'll post it again for you.

This is most likely the UVCVIDEO not being compatible.  It took me ages to find that.  
Ctrl - Alt - F3 (or f4 f5 whatever) to get to a new screen.

login

then input this to blacklist UVCVIDEO
```

echo "# incompatible with current webcam" | sudo tee -a /etc/modprobe.d/blacklist
echo "blacklist uvcvideo" | sudo tee -a /etc/modprobe.d/blacklist
```

now reboot and it shouldn't hang

And 7.10 works great for me.

---

### Post by Denbert on 2008-02-24
> **MasterAslan said:**
> Hi Denbert,

Yes I think I can help you.  This happened to me also.  You will need to use the alternate install CD.    Most likely the cause is the uvcvideo is not compatible with your webcam.  Once you install with the  alternate install it will most likely hang on boot at 'loading bluetooth service'.  It doesn't actually have to do with bluetooth but the fact that its messing up your usb.  Once your at this point ctrl+alt+F7 or F6 or whatever.  Then:

```
sudo nano /etc/modprobe.d/blacklist 
```


add 
```
# incompatible with current webcam hardware
blacklist uvcvideo
```
and save and exit

Now 

```
sudo reboot
```

You SHOULD be able to boot into your system now.

I guess it could be another hardware component that is messing it up for you but thats what it was for me.  Give it a go and see what happens.

Thanks MasterAslan

Now the HP dv6565eo seems to be rocking. :guitar:

I'm setting this up for my daugther, as the original Vista Home Edition was impossible to use....

Once again, thanks.

---

### Post by Arko on 2008-02-24
Hi all!

I have just installed Ubuntu 7.10 in a laptop HP dv2710us but I got a problem: sometimes it starts sometimes freezes on boot.

I took out "quite" and "splash" options from grub menu.lst and, when it freezes, the last messages are:

"[    7.544000] Uniform CD-ROM driver Revision: 3.20", which lasts long time, then some messages about "atkbd.c Unknow key released"

After that it comes with "missing modules, devices..." and "ALERT! /dev/disk/by-uuid/5ff..... does not exist. Dropping to shell".
Then BusyBox (initramfs).

Any help?

---

### Post by MasterAslan on 2008-02-25
Your very welcome Denbert.  Just glad I could help.  I know when I was looking for the issue on my machine it took forever.  Thats whats great about the ubuntu community.  There is so much help out there and with the forums when you help one person you could end up helping 10 or 100 or more.

---

### Post by MasterAslan on 2008-02-25
Arko:

I don't know if I can help.  Try posting the output of dmesg on here, thats how people were able to help me.  Also output lspci -nn

---

### Post by Arko on 2008-02-25
MasterAslan,

Thank you for your interest. I have just figured out how load ubuntu. I added everything I found:

"all_generic_ide noapic nolapic irqpoll noirqdebug" to grub

loaded ata_piix module and ran update-initramfs -u

I don't know which one solved the problem, but now it is just fine.

Thanx again.

---

### Post by Denbert on 2008-02-25
> **MasterAslan said:**
> Your very welcome Denbert.  Just glad I could help.  I know when I was looking for the issue on my machine it took forever.  Thats whats great about the ubuntu community.  There is so much help out there and with the forums when you help one person you could end up helping 10 or 100 or more.

Yep, this is the real power of internet and linux, but I had to admit that my 4 - 5 years of experience with linys had been in the server room whitout X Servers installed - for this I always use Debian.

After Windows Vista came along, I think more people will be ready to use Linux in the Desktop.

I've setup Ubuntu 7.10 and everything works execpt Broadcom Wireless Network - The adapter is BCM4328.

I've tried [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) with no luck.

In restricted Drivers I only have the nVIDIA graphic driver.

Do you have any suggestions?

---

### Post by Ayuthia on 2008-02-25
> **Denbert said:**
> Yep, this is the real power of internet and linux, but I had to admit that my 4 - 5 years of experience with linys had been in the server room whitout X Servers installed - for this I always use Debian.

After Windows Vista came along, I think more people will be ready to use Linux in the Desktop.

I've setup Ubuntu 7.10 and everything works execpt Broadcom Wireless Network - The adapter is BCM4328.

I've tried [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) with no luck.

In restricted Drivers I only have the nVIDIA graphic driver.

Do you have any suggestions?
The b43/bcm43xx drivers do not support the 4328 cards at this point so the option is not available in the restricted drivers.  I think that the best chance is to use NDISwrapper.  Here is a link that I found that has someone with a dv6000z and a 4328:

[http://ubuntuforums.org/showthread.php?t=572005](http://ubuntuforums.org/showthread.php?t=572005)

Hope that helps.

---

### Post by Denbert on 2008-02-25
Thanks Ayutia - I'll keep the dialog in that tread : [http://ubuntuforums.org/showthread.php?p=4404240#post4404240](http://ubuntuforums.org/showthread.php?p=4404240#post4404240)

As i still have some way to go - but gee I'm impressed over the ubuntu 7.10 so far.

Everything besides WLAN works fantastic.

---

### Post by nonmi9 on 2008-02-27
Sorry if this has come up already. I was able to boot into the live CD, before i loaded it i chose to press f4 and change it to the highest resolution i could. for some reson it worked and i was able to install Ubuntu. now that it is installed i can't get into Ubuntu.  I get a screen that starts out black and slowly goes to white then green then black.btw i have an HP DV6425us, AMD turion64x2 mobile tech, nvidia 6520 go, 2gb ram. Using 7.4

---

### Post by Den1aL on 2008-02-27
Good day All

Sorry for butting in here. 

I'm starting to go insane with this problem. My sounds not working on Gutsy, using a HP DV 9500 series lappie (DV 9521e).

I've tried the linux-backports-modules fix, and the HdaIntelSoundHowto but no luck. My sound icon on my keyboard stays muted (orange) although alsamixer reports that the sound level is not muted and should be working
 
If anyone can please give me a link to a post or tut where I can fix my sound issue it will be much appreciated

Thx

---

### Post by MasterAslan on 2008-02-27
> **nonmi9 said:**
> Sorry if this has come up already. I was able to boot into the live CD, before i loaded it i chose to press f4 and change it to the highest resolution i could. for some reson it worked and i was able to install Ubuntu. now that it is installed i can't get into Ubuntu.  I get a screen that starts out black and slowly goes to white then green then black.btw i have an HP DV6425us, AMD turion64x2 mobile tech, nvidia 6520 go, 2gb ram. Using 7.4

Try this:

```

sudo dpkg-reconfigure xserver-xorg
```

You will need to ctrl + alt + f1 to get to a command line to do that.

If this doesn't work try the forcevesa boot option.  This will probably get you into gnome then you can install restricted driver.  Is your video Nvidia?

---

### Post by nonmi9 on 2008-02-27
yes it is Nvidia. OK tried to the ctrl + alt + f1, but nothing happened, where do i use it at. I can get to the Grub boot thing (sorry new to Ubuntu/Linux. and whats forcevesa boot option?

---

### Post by MasterAslan on 2008-02-27
If the above doesn't work try installing the nvidia drivers manually as outlined [http://ubuntuforums.org/showpost.php?p=4367441&postcount=377](http://ubuntuforums.org/showpost.php?p=4367441&postcount=377)

---

### Post by MasterAslan on 2008-02-27
> **nonmi9 said:**
> yes it is Nvidia. OK tried to the ctrl + alt + f1, but nothing happened, where do i use it at. I can get to the Grub boot thing (sorry new to Ubuntu/Linux. and whats forcevesa boot option?

When you get to grub highlight the boot option you use and hit e to edit it.  Then when you get into it highlight the line that starts with kernel.  Go to the end of that and add forcevesa to the line.  Hit enter and then hit b to boot.

---

### Post by nonmi9 on 2008-02-27
Ok going to upload a vidieo so yall can see what it does.
[http://s103.photobucket.com/albums/m142/nonmi9/?action=view&current=MOV00199.flv](http://s103.photobucket.com/albums/m142/nonmi9/?action=view&current=MOV00199.flv)

---

### Post by MasterAslan on 2008-02-27
> **nonmi9 said:**
> Ok going to upload a vidieo so yall can see what it does.
[http://s103.photobucket.com/albums/m142/nonmi9/?action=view&current=MOV00199.flv](http://s103.photobucket.com/albums/m142/nonmi9/?action=view&current=MOV00199.flv)

When you get to the grub screen try hitting e on the first line.  Then scroll down to the kernel line hit e again and delete the quiet splash bit.  Add forcevesa to the end of it.  Hit enter and hit b to boot.  Does that work for you?

---

### Post by nonmi9 on 2008-02-27
> **MasterAslan said:**
> When you get to the grub screen try hitting e on the first line.  Then scroll down to the kernel line hit e again and delete the quiet splash bit.  Add forcevesa to the end of it.  Hit enter and hit b to boot.  Does that work for you?

No just did that, still the same washout screen.

---

### Post by MasterAslan on 2008-02-27
Boot into recovery mode and try.

```
sudo dpkg-reconfigure xserver-xorg
```  then restart.  If that doesn't work try booting into recovery mode and following the above link to install the nvidia drivers manually.  Although I just remembered this worked for me before.  Before trying the above go the grub and instead of adding forcevesa try vga=6 also try forcevesa=true if that doesn't work.  I forgot about the =true part.  Let us know.  I'm sure we can this sorted for you.

---

### Post by nonmi9 on 2008-02-27
Well recovery mode hangs at some point, have a pic to show yea where.
[http://i103.photobucket.com/albums/m142/nonmi9/DSC00203.jpg](http://i103.photobucket.com/albums/m142/nonmi9/DSC00203.jpg)
i did vga=6 and forcevesa=true. nothing has worked yet.

---

### Post by nonmi9 on 2008-02-27
Ok did the vga=6 and got it to go to the login part, but can't input anything.
[http://i103.photobucket.com/albums/m142/nonmi9/DSC00206.jpg](http://i103.photobucket.com/albums/m142/nonmi9/DSC00206.jpg)

---

### Post by jebasan on 2008-02-27
Need help with pavillion 6000 and ubuntu 7.04. 
after i finish the instalation and reboot, the graphic could not be loaded. the error was about wrong video configuration. 
i had the ubuntu 7.10 installed in this same laptop and the only few things not working were integrated webcam, mic and sound. but i was able to use cd-dvd, use usb, wireless. now i'm stuck with win?!@# 

jebasan

---

### Post by EXCiD3 on 2008-02-27
> **jebasan said:**
> Need help with pavillion 6000 and ubuntu 7.04. 
after i finish the instalation and reboot, the graphic could not be loaded. the error was about wrong video configuration. 
i had the ubuntu 7.10 installed in this same laptop and the only few things not working were integrated webcam, mic and sound. but i was able to use cd-dvd, use usb, wireless. now i'm stuck with win?!@# 

jebasan

If gutsy is working for you fine, why are you trying to use an older version?

---

### Post by jebasan on 2008-02-27
I thought the webcam, mic and sound would work this time, i figured.

---

### Post by EXCiD3 on 2008-02-27
> **jebasan said:**
> I thought the webcam, mic and sound would work this time, i figured.
So they arent working in gutsy then?

---

### Post by nonmi9 on 2008-02-27
An idea, how do i get to the command line, instead of load the interface. that way i can load the drivers for the GFX?

---

### Post by jebasan on 2008-02-27
no, they arent working on gutsy. but everything else is just fine. even a wireless Microsoft mouse worked out of the box. 
now i just re-installed the gutsy again because  i need the lap for tomorrow.
if i can work around these small problems (i don't use the webcam, mic or sound a lot) it would be good to have everything working, though.

---

### Post by EXCiD3 on 2008-02-27
> **jebasan said:**
> no, they arent working on gutsy. but everything else is just fine. even a wireless Microsoft mouse worked out of the box. 
now i just re-installed the gutsy again because  i need the lap for tomorrow.
if i can work around these small problems (i don't use the webcam, mic or sound a lot) it would be good to have everything working, though.

Try this for you audio if you have Intel HD Audio [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

What webcam do you have? open terminal and post the output of lspci and lsusb if you arent sure about which sound card or wecam you ahve.

---

### Post by jebasan on 2008-02-27
ok, here is my lspci post:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

now the lsusb

Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000 

is an integrated webcam and mic. the model of my laptop is HP pavillion DV 6000 (dv6629ca).

---

### Post by nonmi9 on 2008-02-27
Well so much for linux, thanks guys...

---

### Post by EXCiD3 on 2008-02-28
The above link should work for getting your audio to work since you ahve that card.

As for the webcam...it isnt one of the older webcams (ricoh and microdia) someone mentioned this page: [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)
I also found this for gentoo with your webcam: The built-in webcam on the top of the screen will work, but needs a module not currently in the 2.6.22 kernel.  Emerge **linux-uvc**, then run **modprobe uvcvideo**.  This will provide you with a V4L2 (/dev/v4l/video0) interface to the camera.  Currently I've only tested with [luvcview]("http://www.linuxlogin.com/hardware/dv6575us.php#sources"), and found the camera to work at 640x480 at 25FPS. You can find uvc as described here: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by EXCiD3 on 2008-02-28
> **nonmi9 said:**
> Well so much for linux, thanks guys...

Have you tried any other distro's? Mandriva has excellent hardware detection and might work better for you.

---

### Post by nonmi9 on 2008-02-28
FINALY got it to work, just how do i edit the menu.lst file so i don't have to keep inputing the stuff?

---

### Post by EXCiD3 on 2008-02-28
open terminal and do ```
sudo gedit /boot/grub/menu.lst
```

then scroll down towards the bottom, it has the menu entires listed there, add the same boot options you used before and then save the file.

---

### Post by nonmi9 on 2008-02-28
> **EXCiD3 said:**
> open terminal and do ```
sudo gedit /boot/grub/menu.lst
```

then scroll down towards the bottom, it has the menu entires listed there, add the same boot options you used before and then save the file.

Thank you so much!

---

### Post by EXCiD3 on 2008-02-28
I'd just like to remind everyone of the Thanks button (little star at the bottom right of a post. Use this button if a specific post has proven useful to you so that other users can find posts like these easier.

---

### Post by Nikolaiownz on 2008-03-01
> **gogodidi said:**
> Hello, I got a brand new dv9510eo yesterday and I installed ubuntu using the alternate CD

I resized the NTFS partition (letting vista keep 50 gb) and parceling the rest out to result in the following partition table:

sda:
sda1: pri /media/windows
sda2: pri /
sda3: pri /boot
sda4: log /home
sda5: log swap

My swap space is 2.4 GB.

After the install, I reboot into ubuntu. a little text, then black.

I try the "noapic irqpoll noirqdebug" ... sequence in the boot parameters, with no result.

I remove the splash from the end of the line and then text scrolls:

(various numbers saying that it cant allocate memory for device at pci 5:0-0 (the screen)

*reading files needed to boot... [OK]
*setting preliminary keymap... [OK]
*preparing restricted drivers... [OK]
*starting basic networking... [OK]
*starting kernel event managers... [OK]
*loading hardware drivers
error receiving uevent message: No buffer space available

When I add "noapic irqpoll noirqdebug", it happily skips beyond that and then allows me to log in on the command line.

But, the X server cant start. Reading the output, it seems that no screens have been configured.

So, what I have gathered is that it cant reserve any memory for the screen and that no screens have been configured, what do I do?

I think the first step is to configure my screen. Anybody know how to help me with this?

[EDIT]
[UPDATE]
Alright, The solution is fairly simple:
Boot using the "noapic irqpoll noirqdebug" parameters, you can remove the splash if you want, it wont ever show anyway.
Then wget the envy package:
$ wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)
$ sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
$ envy -t

Let it do all the work. Then restart. Now you have X.
On my version of the series: dv9510eo, most things will work out of the box. 

I cant for the life of me get wireless working though. Note Im not that great. Its certainly possible.


I got exacly the same problem when i try to bootup a fresh install on my dv6000 - the wierd thing is that i installed it a week ago and never had thoes problems, but yesterday my computer ******, and i tryed to reinstall and now i get this error :(

---

### Post by djou on 2008-03-01
Good morning, I have a DV9033CL with Vista and Ubuntu 7.10, everything works unless the TV tuner, someone would have the solution

---

### Post by EXCiD3 on 2008-03-01
> **djou said:**
> Good morning, I have a DV9033CL with Vista and Ubuntu 7.10, everything works unless the TV tuner, someone would have the solution

This unfortunately has not been tested very well as few owners have purchased the TV card. This may work however:

> 
**_24. TV Tuner_**

 New v4l-dvb drivers have been released with support for this card’s chispet (Conexant **cx23885 **) here: [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
 Drivers are actually at a very early stage and in fact they “officially” support only these cards:
 cx23885[0]:    card=0 -> UNKNOWN/GENERIC
cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
 insmod /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx23885/cx23885.ko card=4
 and also card=3 argument does correctly recognises the video card, however tuning chipset **XC3028 **is still not supported due to firmware issues.
 I have spoken with Hauppage and linux-dvb developers and they confimed support for these chipset and this card in particular is currently being focused due tu high demand. Working drivers should be expected to be released within December.
 **Note1:** to get linux recognise the video card you must have it inserted into the express card slot at boot time. Unofrtunately it is actually not plung&play. At least so far.
 **Note2: **v4l-dvb breaks webcam support, to bring it back working you have either to uninstall these drivers or recompile **gspca** driver (howto will follow)



Thanks to aldeby for this information. Taken from [http://aldeby.org/blog/?page_id=87#tv](http://aldeby.org/blog/?page_id=87#tv)

---

### Post by Nikolaiownz on 2008-03-01
How do i save my grub? 

I've removed "splash", but its not saved, so next time i bootup i have to delete it again.

---

### Post by EXCiD3 on 2008-03-01
> **Nikolaiownz said:**
> How do i save my grub? 

I've removed "splash", but its not saved, so next time i bootup i have to delete it again.
If you edit the entry in /etc/boot/menu.lst and remove splash from that it will save.

---

### Post by Nikolaiownz on 2008-03-02
> **EXCiD3 said:**
> If you edit the entry in /etc/boot/menu.lst and remove splash from that it will save.

Hm i dont have access to do that - and i cant remember setting a root pw for the system.

its in /boot/grub/ aswell on my system

---

### Post by EXCiD3 on 2008-03-02
> **Nikolaiownz said:**
> Hm i dont have access to do that - and i cant remember setting a root pw for the system.

its in /boot/grub/ aswell on my system

You weren't told to specifically enter a root pw for your system, however this is typically the same password as your user account. If you want to modify the existing root pw follow this guide: [http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

---

### Post by Bonkerz on 2008-03-04
My dv9410us HP Pavilion laptop seems to run perfectly fine for a while and then hard crashes. Can't escape to terminal, restart X server, move mouse, etc and have to power off manually. It does this with multiple kernels ( I even compiled one vanilla style ). I suspect it is either the nvidia driver or the alsa driver, moreso the alsa driver since it has crashed with the nv driver in use rather than nvidia. Although, in a previous kernel I did not use nvidia at all and it never crashed. 

Help me? :o(

---

### Post by deos on 2008-03-07
man i have a pavilion dv6448se laptop. i try to install ubuntu and it work, but when my instalation is finished,i reboot my system, and here i have a problem, my system dont' want to start, it's blocked when ubuntu try to start. what do you think is the problem??? :(((

---

### Post by jebasan on 2008-03-08
Two HP pavilion laptop [almost the same hardware!] one with sound issues the other no issues.

Ok, here's the new occurence with hp pavilions laptop and ubuntu gutsy 7.10...
I first installed ubuntu in my laptop 2 weeks ago and, i don't know is anybody read my Threads, but i'm having problems with my Intel sound card only, evrything else worked out of the box [cd-dvd-after installing a few codecs, webcam-installing cheese, MS wireless mouse, USB, etc.]

what happen is that i've just got another pavilion dv to my wife and, besides the processor speed, everithing else is the same. O this one, gutsy worked out of the box for every little aspects of the hardware, even the sound and mic. it just works great![thanks for writing ubuntu!]

back to my hp pavilion [no sound,yet]
searching for some answers, [why it works just fine on hers and not in mine?] [and the sound works just fine in windows] and i think that some conflict might be happening.. i started to search for the asound files and i noticed that in the file [/proc/asound/pcm], the line with the modem info is coming before the audio line as folow;

/proc/asound/pcm
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: HDA Generic : HDA Generic : playback 1 : capture 1

i don't know if that could be the problem or not.

in the path /proc/asound/cards  - i just have the following code:
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8600000 irq 22

and in the path /proc/asound/card0   - i have:
luiz@jebasan666:/proc/asound/card0$ ls
codec#0  codec#1  id  oss_mixer  pcm0c  pcm0p  pcm6c  pcm6p

the file codec#0 is the audio codes and looks alwright [acording to comparison with my other laptop]

the problem is on the laptop dv2700 that's working good [sound], it doesn't have the codec#1 which is the modem codes in mine dv6629a.

also, i couldn't change the ownership of the asound directory and i didn't know if it would work after all.

what should i do?

can somebody help me? :)

---

### Post by abedbajia on 2008-03-10
> **deos said:**
> man i have a pavilion dv6448se laptop. i try to install ubuntu and it work, but when my instalation is finished,i reboot my system, and here i have a problem, my system dont' want to start, it's blocked when ubuntu try to start. what do you think is the problem??? :(((

so what exactly happens when u boot 

the splash screen freezes ??

---

### Post by maestrodelux on 2008-03-10
this info was helpful-finally got my laptop working with usb, this is my 1st linux
i havn't tried wireless or any thing else yet but i have tried about 10 different variations of linux but this one with the noapic irqpoll noirqdebug added to the boot worked--hpdv9000nvidia-amd64--ubuntu 7.10-alternate-amd64 version

---

### Post by ozzyprv on 2008-03-11
> **scorp123 said:**
> That's only relevant for mounting ... not for formatting. But hold on, when you say you don't "see" the card ... did you ever check what the system says about this issue? Here is how: Open a terminal (e.g. "gnome-terminal", "xterm", or whatever) and leave it open. Then insert the SD card into the card reader ... there should be some reaction to that, e.g. the card reader's LED should start to blink. When this happens type this command into the terminal:  **dmesg**

That's short for "daemon messages"; and before anyone thinks we're into satanism or something: "daemon" stands for **D**isk **A**nd **E**xecution **Mon**itor ... so "dmesg" will spit out all the things those background programs monitoring your system have to say. The output from "dmesg" might be rather long because all its messages go all the way back to the system boot; what would be interesting here are the last couple of lines because those will likely be about what it has to say about your SD card. Copy & paste that here please.

> **PsychedelicReaction said:**
> Uhm i've tried but nothing happens to dmesg after inserting the MicroSD. Mine has been formatted by Nokia itself cause it's the one i got with my 6680, i don't think it contains DRM.

Same here, nothing happens when I insert the media in the slot (memory stick).

Does anybody has a fix yet?

Thanks.

---

### Post by vicanbas on 2008-03-13
Evertything works perfectly! Thanks!

---

### Post by Mushed on 2008-03-14
The strangest thing happens with my webcam. Following the steps I finnally got my webcam to work, but it only works with ekia and using the test button in "Multi-Media Selector" - With camorama it says no device can be found at "dev/video0" - same with Mercury(msn clone)
How can my camera work, but not work! Hlp plz.

---

### Post by Ace2016 on 2008-03-16
I've gotten most of the things on my system to work

Anyone else seeing really high temperatures for amd cpu and nvidia gpus?

Idle in a cold room, cold enough for me to need a blanket:

ace@Linux:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +61.0°C
Core0 Temp:  +58.0°C
Core1 Temp:  +53.0°C
Core1 Temp:  +53.0°C

However i have seem it hitting +81°C the nvidia gpu always runs hotter than the cpu, but i have not had a chance to look at the temperatures since i run Xgl and the nvidia temperatures cannot be read from Xgl. This is very hot, the laptop temperatures is higher than that of my desktop which is very worrying, and the worst thing is that the cpu is close to the battery, if the cpu goes the battry might blow so i'm a bit scared of the temps myself. So how hot is your system?

MasterAslan: i sent you another pm, ty for the help

---

### Post by champracer29 on 2008-03-22
I have HP DV9417cl, with Broadcom BCM94311MCG wireless and Ricoh webcam.

I was able to get everything works execpt Ricoh Webcam which is 05ca:1810. and I followed one of your link and downloaded .deb link and saw nothing show last four number 1870 but nothing show 1810. I decide to give a risk and install it. Now I am able to view myself just fine using Ekiga. I have not tested with Pidgin yet.

I just wanted to say thank you all for all effort fixing most of laptops all over the technology world. :)

---

### Post by jwill1515 on 2008-03-23
The caps lock and num lock lights don't work on my Pavilion dv9205us. Any suggestions? Thank you.

---

### Post by gameryoshi600 on 2008-03-24
does this work with compaq presario v6000

---

### Post by EXCiD3 on 2008-03-24
What hardware do you have?

Processor?
Wireless?
Video Card?
etc

---

### Post by teeleef on 2008-03-25
Hi Excid3,  following excellent installs on two pc's I decided to install Hardy Beta on to my HP DV9500.  Sound and graphics worked out of the box, the only hiccup is wifi.  The network is scanned and passphrase entered but no connection.   I tried the ndiswrapper install at 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)


No joy there.    

Is it a known problem, and has anyone come up with a solution?


Regards


Teeleef

---

### Post by nrcooled on 2008-03-25
> **Den1aL said:**
> Good day All

Sorry for butting in here. 

I'm starting to go insane with this problem. My sounds not working on Gutsy, using a HP DV 9500 series lappie (DV 9521e).

I've tried the linux-backports-modules fix, and the HdaIntelSoundHowto but no luck. My sound icon on my keyboard stays muted (orange) although alsamixer reports that the sound level is not muted and should be working
 
If anyone can please give me a link to a post or tut where I can fix my sound issue it will be much appreciated

Thx

I am having the EXACT same problem.  Hopefully, someone can chime in but in the meanwhile I will keep plugging away trying to get this issue resolved.

---

### Post by rohit2412 on 2008-03-26
thanks man..........gosh i came here late................
anyway i couldnt have done the webcam and wireless without this......
thanks for writing in such detail

---

### Post by rohit2412 on 2008-03-26
can u please tell when hardy heron will be out and its performance on dv6000.......
i think gutsy was easy...only i messed it

---

### Post by EXCiD3 on 2008-03-26
> **rohit2412 said:**
> can u please tell when hardy heron will be out and its performance on dv6000.......
i think gutsy was easy...only i messed it

Hardy Heron's official release date is April 24th. This might change slightly depending on the progress made by then. Hardy beta runs excellent however if you are looking for a stable system Gutsy or Feisty is a better option. You can download the beta to try it out and continue updating it to keep uptodate.

---

### Post by rohit2412 on 2008-03-26
so i can switch to beta just by upgrade icon on the desktop........
or do i have to do a fresh install

---

### Post by EXCiD3 on 2008-03-26
> **rohit2412 said:**
> so i can switch to beta just by upgrade icon on the desktop........
or do i have to do a fresh install

You can use the update manager, however you need to tell it you want to upgrade to Hardy. Its fairly simple and straight forward. Just follow the steps here: [http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron-beta.html)

---

### Post by sushr on 2008-03-26
Hi,

I'm unable to install X (Feisty) on my dv 9000. I have the intel mobile integrated graphic card - 965g chipset.

I found the drivers at the following location - [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

While building the driver I get the following errors:

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_FLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Has anyone encountered the same problem? I have all the required packages installed. 

I dunno what the problem is. Thanks in advance!

---

### Post by Punkristo on 2008-03-29
Im having problems with the card reader. Everything else works fine. Anyy help with the card reader?

---

### Post by nrcooled on 2008-04-03
> **nrcooled said:**
> I am having the EXACT same problem.  Hopefully, someone can chime in but in the meanwhile I will keep plugging away trying to get this issue resolved.

My sound woes are gone!!!  I used this command:

```
sudo apt-get install linux-backports-modules-generic
```

Rebooted and everything works!!!  I'll try to find the guide again to give everyone the how-to and also give the author credit.

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by eyestrain on 2008-04-03
I'm completely new to Linux but decided to try installing it.  I've got a HP Pavillion DV9000 (specifically the DV9715nr) and I've been following the walkthrough for installation (using 7.04 Alternate).  I partitioned the hard disk as I want to keep Vista for now.

I got it installed okay, apart from the networking bit, which I skipped.  Initially the bootup goes well until I get a page saying:

**Failed to start the x server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the x server output to diagnose the problem?**

If I say yes I get this:

[B]X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
markers: (--) probed, (**) from config file, (==) default setting,
              (++) from command line, (!!) notice, (II) informational,
              (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log" Time: Fri Apr 4 03:06:38 2008
(==) Using config file: "/etc/X11/xorg.conf"[/B]

then when I say yes to **'Would you like to view the detailed X server output as well?'**  I get the same page.  When I hit ok I get **'The X server is now disabled.  Restart GDM when it is configured correctly'**

If I hit okay it goes back to the bootup process.  It says

[B]Starting up ...
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash Using mode 1024x768
kinit:name_to_dev_t(/dev/sda5 = sda5(8,5)
kinit: trying to resume from /dev/sda5
kinit: No resume image, doing normal boot...
Ubuntu 7.04 ubuntu ttyl

ubuntu login:
[/B]
I think I'm entering my login info correctly (even though you can't see any indication that the password is actually being typed in!) but then I get a bunch of text about free software, no warranty, and a bt about running command.  The next line says:

**username@ubuntu:~$**

I don't know what to do from there.  Sorry for the long post, I tried doing a search but nothing I tried gave me any results.  I also have no idea what info (if any!) is relevant so I thought I should include it all :)

Can someone please help me fix this?  Also, if there's an idiot's guide to Linux/Ubuntu out there feel free to post the links, I think I'll probably need them!

---

### Post by EXCiD3 on 2008-04-03
I'm not sure why your xorg wont start correctly. You can edit it to use the vesa or nv drivers to temporarily use the xserver.

In terminal type:
```
sudo nano /etc/X11/xorg.conf
```
Change the Driver under the graphics section to either "nv" or "vesa" and save the file. Restart and hopefully this will get you into the xserver.

From there you can install the nvidia driver using the Restricted Drivers manager, Envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) or by compiling the drivers yourself.

If you cant get into the xserver after changing the xorg.conf file you can try using Envy in text mode instead.

You may also want to try using Gutsy or even Hardy Beta (which i would recommend) Feisty is quite outdated now however Gutsy still is pretty much a hit or miss on HP laptops. Hardy however has come to work very nicely and stably on most laptops. You may want to try using that instead.

---

### Post by marcellosales on 2008-04-25
[SIZE="6"]FRESH INSTALLATION OF UBUNTU 8.04, on a Machine with Ubuntu 7.10...[/SIZE]

Procedures and experience of using a 32bit to a 64bit Ubuntu! 

Hello folks,

I finally have Ubuntu 64bit alternate CD installed, and I did that right after the release of Ubuntu 8.04... I did not know what would happen, but I had Ubuntu 7.10 installed and I decided to have a fresh installation since I had installed the 32bit version while having 4GB of physical memory. Everything is just great!!! No Firefox nor Eclipse crashes!!!! I can finally work without worrying about it... Here are the procedures for those who wants to do the smoothest transition:

0. Downloaded Ubuntu 8.04 alternate CD and burned it to a CD :P (duhh)

1. I shrank one of my partitions and I created a new one with about 30Gb of space. Since I still have an old partition with Windows Vista, I just used the management tool to resize a partition after trying to use GParted (which couldn't do that much) [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

2. I logged back to my Ubuntu 7.10 and using GParted I created and formatted a new partition using ex3 on the new created free space. You can get this free space from your Ubuntu partition as well, depending if you have just one Hard Disk or the free spaces were created on the same Hard Disk.

3. Rebooted my machine with Ubuntu 8.04... The only different thing is that the installation procedure is done all using the text interface. So, it was kind of "back to 10 years ago" installation procedure :) 

   3.1 Pass over the steps just confirming, and chose the new ext3 partition created. It also asked about formating it again. One important detail in the process is that the installation already recognized I had a SWAP partition. So, the idea was to share the same SWAP partition with both 7.10 and 8.04; 

   3.2 I recommend you to have an Ethernet cable plugged, since wireless might not be recognized... I even don't remember if there are access to external resources during the installation;

   3.3 The beauty and power of this installation was that it recognized all my other operating systems installed (Vista, Ubuntu 7.10). Just confirm on the creation of a new Grub manager on the new partition with the complete list of all your operating systems installed... Thanks to the UBUNTU team, at this point, I was not concerned about losing the access to my other OS's anymore;   

   3.4 Follow the instructions to finish the installation, creating new user, etc...

4. After the installation, I just got a new instance of Grub with the list of my OS's. There was still a concern about if the 64bit would run on my Intel processor... It was the best and pleasant Linux installation EVER! It did everything without headaches!!! 
   4.1 I accessed my new Ubuntu 8.04. The very first command to my new OS, was free!

[marcello ~]$ free 
             total       used       free     shared    buffers     cached
Mem:       4050272    2023344    2026928          0     124604     747524
-/+ buffers/cache:    1151216    2899056
Swap:      2931852          0    2931852

   As you can see, now I have 4GB being addressed! This is after I configured and enabled Compiz and Screenlets (No need to install Compiz this time, just follow some configuration instructions at [http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA), or look for your card setup process on that wiki).

   4.2 As Ubuntu mounts all the other linux partitions, I'm copying over my /home directory and other customized softwares installations from Ubuntu 7.10. I preferred this new installation because 7.10 was crashing all the time and I had dozens of modules I had installed, so I wanted to start it fresh... 

[SIZE="5"]PROBLEMS AFTER THE INSTALLATION:[/SIZE]

1. JAVA 5 doesn't run!!! I'm a Java developer and I'm currently using JDK 5 so I just decided to install only this version. As a result, all JAVA applications could not open properly.  The workaround was installing JAVA 6 and additional extended drivers as described [http://ubuntuforums.org/showthread.php?t=687413](http://ubuntuforums.org/showthread.php?t=687413). 

2. FIREFOX 3.0 is HELL!!! It is ultra fast, but it consumes memory too much!!! It was crashing all the time after accessing my GMAIL account... So, I downgraded and this was another long debugging time!!!! 

  2.1 Uninstall Firefox 3 permanently and install Firefox 2.0.0X
  2.2 Delete the folder ~/.mozilla (rm -rf ~/.mozilla). This step MUST be done before installing any add-on...

From that, everything is so much more stable... I still haven't configured Compiz completely since it doesn't show the Window Shadows and other eye-candies, but just the fact that I can open Easy Eclipse and Eclipse IDE's without crashing!!! 

UBUNTU 8.04 definitely represents a very stable release... I'm very happy with this installation!!!

Good luck everyone!

---

### Post by MikeDK on 2008-04-28
the only thing i'm afraid of is, will it run on dv9200 series, with TL-52 CPU's, and the BCMxx wireless, I will however install one of these days, a fresh install from 7.10 i386 to 8.04 i386, i'll try the ordinary livecd install as i know the alternate cd, usually works fine, so on to see if it works, ill get back to tell about it.

Kind Regards MikeDK

ooh and by the way, your all welcome to message me on skype if your running skype.

---

### Post by EXCiD3 on 2008-04-28
> **MikeDK said:**
> the only thing i'm afraid of is, will it run on dv9200 series, with TL-52 CPU's, and the BCMxx wireless, I will however install one of these days, a fresh install from 7.10 i386 to 8.04 i386, i'll try the ordinary livecd install as i know the alternate cd, usually works fine, so on to see if it works, ill get back to tell about it.

Kind Regards MikeDK

ooh and by the way, your all welcome to message me on skype if your running skype.

Works great! No boot parameters are needed to boot into the LiveCD anymore as far as i know. The Broadcom wireless will also work for you. Its worth the upgrade. If you need  anything let me know.

---

### Post by ZeldaFan on 2008-04-28
I have an HP dv9000t custom configured laptop from HP.com. It has a Core 2 Duo T5600 processor and I'm pretty sure an Intel i945PM chipset. Right now I have 2 gb of RAM, but I was wondering, is it possible to upgrade to 4 gb of RAM? Does the hp dv9000t support it (assuming the OS does) if I have the BIOS updated and compatible RAM chips?

---

### Post by EXCiD3 on 2008-04-28
Unfortunately you wont be able to. The Intel i945 chipset is unable to detect up to 4gb of ram. Im not sure what the maximum is. The 965  Santa Rosa chipset will support 4GB however.

---

### Post by ZeldaFan on 2008-04-29
Thanks for the reply. Another question. You know how the hp dv9000t series have two bays for hard drives. I have one hard drive right now (100 gb) but I plan on purchasing another (with the caddy kit), maybe at around 160 gb. I have vista installed on the 100 gb HDD, and I plan on installing ubuntu hardy on the 160 gb hard drive which should be in the second HDD bay. How does this all work when it comes to booting my OSes. How will grub work and will both operating systems be recognized? When installing ubuntu on my second HDD, I will have the vista HDD unattached, so I don't expect the grub to automatically recognize it when I put it back in and load my computer with both HDD's in their respective bays. Can I add an option to load vista later to my grub file?

---

### Post by EXCiD3 on 2008-04-29
> **ZeldaFan said:**
> Thanks for the reply. Another question. You know how the hp dv9000t series have two bays for hard drives. I have one hard drive right now (100 gb) but I plan on purchasing another (with the caddy kit), maybe at around 160 gb. I have vista installed on the 100 gb HDD, and I plan on installing ubuntu hardy on the 160 gb hard drive which should be in the second HDD bay. How does this all work when it comes to booting my OSes. How will grub work and will both operating systems be recognized? When installing ubuntu on my second HDD, I will have the vista HDD unattached, so I don't expect the grub to automatically recognize it when I put it back in and load my computer with both HDD's in their respective bays. Can I add an option to load vista later to my grub file?

This will work perfectly. I have the exact same setup you will be using:

First Drive: Vista
Second Drive: Ubuntu

I recommend partitioning your second drive into 3 partitions as follows:

Partition 1: /boot = 256MB
Partition 2: /swap = Size of RAM
Partition 3: / = Rest of Drive

You could also shrink / to a smaller size and have a separate /home partition to save your settings in case you need to reinstall.

In order to be able to boot correctly I would recommend keeping your Vista drive attached. Leave the Grub settings alone. This will install Grub to the MBR of your vista drive and allow you to be able to access both operating systems. If you remove your Vista drive and then re-attach it, then Vista will be the only OS available. Installing grub to the MBR of your Vista drive will be completely safe and having the drive attached will also automatically add Vista as an option to the Grub boot list.

---

### Post by ZeldaFan on 2008-04-29
Do I have to manually partition the ubuntu drive or can I set it to automatically partition for me, considering I'm using it to occupy the entire second HDD. And is there any way I can install ubuntu in such a way that grub is only on the second HDD yet still have it recognize my vista OS perhaps by adding an entry later. I want my vista OS to be completely windows, without any remnants of linux, including the grub.

---

### Post by EXCiD3 on 2008-04-29
If you want it customized with the partitions like I mentioned you would need to do Manual, however if you plan on using the entire drive you might as well just use the automatic full drive install. 

Adding an option to the vista boot loader may take some work. There is a Windows program called [EasyBCD]("http://neosmart.net/dl.php?id=1") that you should be able to use to edit the Vista boot loader. You will want to install grub the the hard drive however.

Here are instructions on adding the linux option to your boot loader also: [http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

---

### Post by WarningXdezzy on 2008-04-30
[FONT="Garamond"][COLOR="Green"]I have the dv9608nr for the 9500 series.
I havent tried this yet, but i will deff. give it a go. I have
been wanting to do this since i bought the laptop in december but had no luck when i first bought it and havent had time to try since.
I have a dv8000 also and it seems to be the only laptop in its series that makes installing any distro a walk in the park. The only touble i had with it was the wireless, which i finally fixed not long ago.[/COLOR][/FONT]

---

### Post by EXCiD3 on 2008-04-30
> **WarningXdezzy said:**
> [FONT=Garamond][COLOR=Green]I have the dv9608nr for the 9500 series.
I havent tried this yet, but i will deff. give it a go. I have
been wanting to do this since i bought the laptop in december but had no luck when i first bought it and havent had time to try since.
I have a dv8000 also and it seems to be the only laptop in its series that makes installing any distro a walk in the park. The only touble i had with it was the wireless, which i finally fixed not long ago.[/COLOR][/FONT]

I would use Hardy Heron to install with. Hardy fixes lots of bugs since this tutorial was written. If the dv8000 is Intel based then yes, it will be extermely easy to install. My dv9000 is intel based and has next to no issues with Ubuntu.

---

### Post by ZeldaFan on 2008-05-07
Ok, so I purchased a new internal HDD with the caddy and installed it in the second HDD bay. It's a 160 GB western digital, and my primary hard drive is a 100 gb fujitsu. They didn't have to be the same right? Anyway, where do I go from here? How do I get my computer to recognize the hard drive?

---

### Post by EXCiD3 on 2008-05-08
The drive should be automatically detected and you should be able to install to it. The drive will not be formatted when you purchase it so it may not show up on any operating systems you currently have installed until you format it.

---

### Post by AlanB66 on 2008-05-08
Thank you for the Synaptic Touchpad steps:
[INDENT]Synaptics Touchpad
1) Install GSynaptics (or KSynaptics if you use KDE) through Synaptic Package Manager

2) Edit xorg.conf to enable Touchpad app to use touchpad.
[INDENT]sudo gedit /etc/X11/xorg.conf[/INDENT]

3) Scroll down to the "Synaptic Touchpad" section and add the following line:
[INDENT]Option         "SHMConfig" "true"Save xorg.conf[/INDENT]

4) Xserver must be restarted for this to take effect. You can do this by pressing Ctrl-Alt-Backspace.[/INDENT]

My wife is really big on using the double-click on the touchpad to drag items ... and I'm trying to make Ubuntu friendly for her so she one day says those magical words, "Please change my laptop from Windows to Linux." :lolflag:

Thanks again!! Worked like a charm. 

I am using Ubuntu 8.04 on a Compaq F750US, for the record.

---

### Post by iwallet on 2008-05-08
lol could have used this a few months ago!!! :P
Great Work!!!

---

### Post by lordawesome on 2008-05-08
Effen RAD!!!  Im sticking with gutsy for now because it seems as if 8.04 does not agree with my laptop.... had to use battery just to get the disc to boot! Either way... awesome! Ill try to upgrade to heron some other time and have everything work with gutsy.

---

### Post by EXCiD3 on 2008-05-13
I just finished my newest tutorial on installing Hardy on HP and Compaq laptops! You can view it here: [http://excid3.pcriot.com/wordpress/?page_id=28](http://excid3.pcriot.com/wordpress/?page_id=28)

---

### Post by ZeldaFan on 2008-05-17
Has anyone experienced any problems shutting down with Ubuntu Hardy on an hp dv9000? In Gutsy, I've had no problems but with Hardy, when I click shutdown from the upper right icon all my applications seem to close, even AWN, but the screen just remains on my wallpaper until I type ctrl + alt +backspace, which then initiates the shutdown sequence. However the screen remains on the wallpaper until I type that, which is annoying because sometimes I may forget to type it in and come back a couple hours later to realize that my laptop hasn't shut off yet.

---

### Post by EXCiD3 on 2008-05-17
Hmm, seeing as you have done some customization to Ubuntu you probably have something changed by accident that prevents shutdown from working correctly. Try disabling apps you have running one at a time and trying shutdown to see if you can narrow down which application it is that is preventing shutdown.

---

### Post by msbroadf on 2008-05-18
I have a dv9005tx laptop and my suspend was not working at all until i upgraded the kernel to 2.6.24-17.  Now the suspend works the first time.

However after the first suspend and then resume, it wont suspend anymore, it gets stuck with the LCD light still on.

Anyone else have similar issue?

-----------------------------------------------------

HP dv9005tx, 2G, 2.0ghz intel core duo, GeForce Go7600, 2x 120GB hdd

---

### Post by EXCiD3 on 2008-05-18
Ive been noticing similar issues with my laptop. I have basically the same laptop as yours, core 2 duo, 2gb ram, 7600go, 2x80gb hdds and after suspend last night I resumed, logged in, only to be brought right back to the login screen again. Apparently the xserver crashed and restarted. I cant really say what is causing this but ill look into it and post back if i find anything.

---

### Post by ZeldaFan on 2008-05-25
This is a question in general about the HP dv9000 laptop. Do BIOS settings exist to change settings on power management. Because I can't find them but I suspect there is something in my BIOS preventing me from manually changing power management settings in ubuntu. When ever I use hdparm -B to set my power management value to 200, it says it was successfully changed but after reboot, I type in "hdparm -B /dev/sda" (without quotes) to check my power management value and it claims that it is missing/bad. Yes, I am sure my hard disk is sda and not hda, so I don't know what else could be the problem.

---

### Post by EXCiD3 on 2008-05-26
> **ZeldaFan said:**
> This is a question in general about the HP dv9000 laptop. Do BIOS settings exist to change settings on power management. Because I can't find them but I suspect there is something in my BIOS preventing me from manually changing power management settings in ubuntu. When ever I use hdparm -B to set my power management value to 200, it says it was successfully changed but after reboot, I type in "hdparm -B /dev/sda" (without quotes) to check my power management value and it claims that it is missing/bad. Yes, I am sure my hard disk is sda and not hda, so I don't know what else could be the problem.

As i set my hdparm -B to 255 on both my drives in my dv9000 a while back i never though to check to the status of hdparm and sure enough just like you said, it gives an error that there is no value set.

---

### Post by ZeldaFan on 2008-05-26
...which is a bad thing, right?

---

### Post by EXCiD3 on 2008-05-26
> **ZeldaFan said:**
> ...which is a bad thing, right?

lol yeah im assuming so. I will try to look into it, anyone else noticing these problems? Have you had a chance to check for bugs on [http://launchpad.net](http://launchpad.net) ? i will if i get the chance but i have been pretty busy recently, if you do find something make sure to post it and hopefully we can get this figured out.

---

### Post by Kingsley on 2008-05-30
Anybody else experiencing an annoyance with the touchpad, where it automatically turns on after every reboot? I turn my touchpad off, but it turns back on after every reboot. This never happened to me in Fedora 8 or Gutsy Gibbon.

---

### Post by EXCiD3 on 2008-05-30
> **Kingsley said:**
> Anybody else experiencing an annoyance with the touchpad, where it automatically turns on after every reboot? I turn my touchpad off, but it turns back on after every reboot. This never happened to me in Fedora 8 or Gutsy Gibbon.

I havent turned mine off but i will take a look and see if it happens on mine also.

---

### Post by ZeldaFan on 2008-05-31
EXCid, referring to problem with setting hdparm settings, I was wondering if it could be a problem with Hardy incorrectly recognizing my ACPI settings. Because in addition to not being able to set hdparm, my laptop runs very hot, even more so than when it is running vista (I have a dual boot set up). I can try cleaning out the dust that may be in the fan, but I suspect that my fan is not fully utilized/effective in ubuntu because of incorrect ACPI settings or something. Do you experience rather high temperatures too? If so, this could be a problem with all dv9000s and maybe not just mine. My output with acpi -V is between 52-58 C.

---

### Post by ZeldaFan on 2008-05-31
Ok, actually I think I found a fix. I simply used the "unofficial ugly fix for Hardy" mentioned in this thread: [http://ubuntuforums.org/showthread.php?p=5030999](http://ubuntuforums.org/showthread.php?p=5030999)
I'm assuming that you changed the hdparm -B settings to lower the load cycle count, so this thread deals with that problem. However, after applying the fix, we still receive a "bad/missing" value for hdparm -B. I think that is irrelevant however because the fix doesn't change hdparm -B but changes the APM value directly. I checked out my /etc/hdparm.conf and the values for hdparm -B were commented out, which is probably why the value is "missing". However, I think for the fix in the thread to work, we need to leave that value commented so that it doesn't interfere with the script being made. My load cycle count has seemed to reduce for now, but I'll continue to monitor it. However, although my load cycles have gone down, my laptop temperatures are a little bit higher as a result of the less aggressive power management. I'm trying to look for a tool that allows me to control my laptops internal fan, if you know of any relevant apps/tools, that would be great.

---

### Post by EXCiD3 on 2008-05-31
I have noticed my laptop getting awfully hot, however i also think this is due to MAJOR dust in my laptop...(it overheats and shuts off after 15 mins of battlefield 2). As it looks like they are changing over to pm-utils which is different yet. 

I just checked and my primary hdd in my laptop has a load cycle count of 127,000 currently and ive only had it for little over a year. I dont have time to try the fix at the moment but let me know how it goes. Good find on the post.

If anyone else has experimented with load cycles please let us know!

---

### Post by Ayuthia on 2008-06-01
> **ZeldaFan said:**
> This is a question in general about the HP dv9000 laptop. Do BIOS settings exist to change settings on power management. Because I can't find them but I suspect there is something in my BIOS preventing me from manually changing power management settings in ubuntu. When ever I use hdparm -B to set my power management value to 200, it says it was successfully changed but after reboot, I type in "hdparm -B /dev/sda" (without quotes) to check my power management value and it claims that it is missing/bad. Yes, I am sure my hard disk is sda and not hda, so I don't know what else could be the problem.

hdparm -B is used to set the power management value, but you will not be able to view the current value using that command.  To view the value, you need to use "hdparm -I /dev/sda".  It will give you a lot of information, but it does list the value under Capabilities.

---

### Post by ZeldaFan on 2008-06-01
Oh no wonder it wasn't giving me any value before. Now I can confirm I have an APM settings value 254. Do you by any chance know how I can control my fan settings (cooling fan and CPU fan) to run faster much sooner than when it does now?

---

### Post by ZeldaFan on 2008-06-01
Sorry, I didn't notice your last post initially, EXCiD3. Although my laptop does get exceedingly hot as well, it never overheats. The load cycle problem seems fixed with the post I found, as my load cycles have only increased by 1 after each shutdown/reboot but that is natural and can't be changed. Unfortunately changing the APM settings to 254 should only cause our laptops to run even hotter, so if the computer is overheating too often, you might want to see how the fix affects you or hold off on it. I have another hard drive with vista on it, so I'll observe how the temperatures change. If temperatures are similarly high with both hard drives, I guess its same to assume we have a dust problem clogging our fans (I haven't cleaned by fans out since purchasing my computer which is like 1.5 yrs ago). If temperatures are lower in vista, I'll have to conclude that there's a problem with ubuntu and controlling fan speeds.

---

### Post by EXCiD3 on 2008-06-01
Good idea. I can see lots of dust in mine, and i sit my laptop on a cooling pad (i use it as a desktop quite often) and it sits open where dust collects on it. I will try the fix.. If i remember right, mine idles at approximately 67C in Vista and then gets up to 85+C gaming...of course this temp in vista is from the graphics driver. I just checked in nvidia-settings and have it idling at 67C.

I highly doubt a slight increase in hdd temps is going to affect my laptop much. With a 7600go it emits enough heat to warm a couple of rooms on occasion. I will apply the fix and continue monitoring it.

I don't have the hddtemp package installed so i cant monitor the drive temp until i get on wifi sometime soon. What tool do you use for monitoring the temperature in windows?

---

### Post by ZeldaFan on 2008-06-02
In windows I use speedfan and the speedfan widget with yahoo widgets. After booting into windows, I found temperatures of my CPU cores and GPU reaching 62-68 C which is too high but my HDDs were at around 49 or 50 C. I guess those temperatures are too high for vista too, so I'll try cleaning out my fans.

---

### Post by EXCiD3 on 2008-06-02
Ok i will download speedfan and try monitoring my temperatures. I've been monitoring my load cycles and they have been only increasing a consistent rate after I used the hdparm -B 254 value. This could be quite an issue as it will wear out drives quickly if it goes unnoticed and no fix is applied in the ubuntu release.

What video card do you have? I'm sure my 67C is not healthy whatsoever for my laptop but im not sure what else i can do other than try to clean the dust out. Hopefully that doesnt require much work to take off the back panel to get to the fan...

---

### Post by ZeldaFan on 2008-06-03
I have the 512 mb dedicated VRAM Nvidia Go 7600 graphics card. It runs at around those temperatures as well, even a little hotter sometimes. Although nvidia-settings mentions that the threshold temp however is 110 C, I'm not sure if it means that it still okay for the graphics card to reach temperatures as high as 70 C or not.

---

### Post by EXCiD3 on 2008-06-03
Its fine for the graphics card to get up to 70C. The threshold i *thought* meant the hottest the videocard would get before it would shutdown your computer...but thats awfully high for that, so im not really sure.

---

### Post by ZeldaFan on 2008-06-03
Well it mentions it as the "Slowdown Threshold", I'm assuming that it means that 110 C is the temperature at which the Graphics card begins to slow down or function at less power. 
By the way, do you know how to go about cleaning an HP dv9000 laptop? I finally bought a can of compressed air but I'm not really sure where to start, lol.

---

### Post by EXCiD3 on 2008-06-03
I was just looking at mine on the bottom to see how i could get access to the fan...it does not look like much fun. At least the hard drives and keyboard have easy access. The screws are labeled for them on the bottom. The fan looks like it is going to required removing the entire bottom panel. :( If i take mine apart ill be sure to take pictures and post it on my blog.

Right now im in the car wardriving and its unbearably hot to have on my lap but its still running at 67C.

---

### Post by inwo on 2008-06-05
Thanks so much for this thread!

I just have one problem.  no matter what I try my screen won't go above 800x600.  I have a dv9823cl its an AMD with a nVidia 7150 (UMA) and the screen's native is 1440x900  I have used adept to update my system to all current patches, and installed envyng-qt (I'm on kubuntu) and updated my xorg.conf .   I'm using the closed-source binary (which still isn't auto detected, says vesa...)  and when I try to select another monitor (or edit manually with some values found in another post) I get the (EE) No Screens Found message.  Anyone have some more pointers?

---

### Post by EXCiD3 on 2008-06-05
Not sure why its doing that, usually it works great out of the box. Best thing to do is download the new driver (not in the repositories yet) from nvidia.com and follow starcannon's guide here (its a little ways down) [http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)

---

### Post by mbach_007 on 2008-06-07
I am trying to get my finger print reader on my HP dv9700t laptop working.  The how to I found said to type in this command and when I do it says I have to be in root.  How do I get into root.

Matt

---

### Post by EXCiD3 on 2008-06-07
> **mbach_007 said:**
> I am trying to get my finger print reader on my HP dv9700t laptop working.  The how to I found said to type in this command and when I do it says I have to be in root.  How do I get into root.

Matt

To run a command in root just put "sudo" in front of it. For example, you can run "nvidia-settings" in terminal, or you can run it as root in terminal like this "sudo nvidia-settings". The second way is unrestricted access and lets you modify important parts of the operating system with it. Sudo gives the commands you are running unrestricted access. Just make sure you know what the commands do before you run it. Some people are going around posting commands like "sudo rm..." that can pretty much wipe your hard drive. Not trying to scare you, but its better safe than sorry! Good luck on the reader, let me know how it goes, i've been needing some feedback on how well they work.

---

### Post by MikeDK on 2008-06-08
USB-read dont work after install, I've added noapic irqpoll noirqdebug to kopt, but not working, also tryed with noapic irqpoll irqfixup, still dosnt work, i've install from usb-stick made with unetbootin from sourceforge, think its [http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)
btw its a dv9232eu 1.6ghz, 2gb of ram kingston, 120gb Fujitsu-siemens harddrive.

dont know if its because i installed with no battery in the bay, think i'll try with a cd install instead.

Kind regards MikeDK

---

### Post by EXCiD3 on 2008-06-08
Not sure if that will make a difference. It seems that just one of my usb drives will not automount, yet the other 3 will work just fine. Plug in the drive and run "lsusb" to see if it detects it at least.

---

### Post by MikeDK on 2008-06-08
it solved the problem by installing with a cd, but another question is, i dont remember the vert and horiz rates from the old installs of feisty and gutsy. any of you running with 17" screen and 7600 GO geforce 256mb??
I remember that both feisty and gutsy catched the screen rates nice and as it should be, but i cant seem to find my note where i wrote the rates down............pretty typical :)
any suggestions would be more than appreciated.

Thanks in advance.......MikeDK

---

### Post by EXCiD3 on 2008-06-09
Thats the exact same videocard/screen im running on. Just use "sudo nvidia-settings" to configure your monitor and have it save it to your xorg.conf. You get more refresh rate options when you click advanced. Actually...check the menu on the monitor, should  display the refresh rates on there somewhere, but its much better to have nvidia-settings setup the refresh rates for you instaed of manually entering them. On everything but the newest driver (which isnt in the repositories yet, you have to manually install) i had to use 60(2) to get the right refresh in nvidia-settings. Now that seems fixed and Auto works fine in the 173 nvidia driver from nvidia.com

---

### Post by MikeDK on 2008-06-12
done, but still text is looking awfull, in some sites in FF3, so ill go look for the Vert and Horizsync refreshrates, or maybe ill contact HP to get the rates, i know it'll solve the problem, once ive found them ill post them here
Think ill just install gutsy on my amd 3800 X2, and connect my Acer AL1916w cause that screen got the same refreshrates.

be back with results.

Kind Regards MikeDK

---

### Post by EXCiD3 on 2008-06-12
really? thats odd, mine is looking great. I've also got hte AL1916w that I use as an external on the laptop and everything is crisper on it but they both seem to be pretty clear. What screen did you get with your laptop? mine is the mid range capable of 1440x900. That might have something to do with it, not sure, but i think they should all use the standard 60hz vert refresh that most laptops have.

My xorg.conf is attached, see if there is anything useful in there for ya. I've got it configured for default to be just my laptop monitor, but the other configuration is loaded if it detects my external monitor and uses it as the only display.

---

### Post by c_olin on 2008-06-13
After I upgraded to Hardy whenever I reboot, or suspend, my screen will turn black and the pixels will start filling in slowly until the screen is just noise.  (it looks kind of cool).  But I'd like ot fix it.  I've tried re-installing but it still does it.

HP dv9000 with nVideo Go

I will try downgrading to gutsy

---

### Post by EXCiD3 on 2008-06-13
Don't know if there is anything you can do to fix it, mine does the same thing and it is an issue with the nvidia driver. Resuming always gives me that, not sure about reboots.

---

### Post by ZeldaFan on 2008-06-19
Has anyone gotten lm-sensors to work with an hpdv9000 so that it can detect fan speeds and such?

---

### Post by EXCiD3 on 2008-06-19
Have you tried anything like: [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

I will try to get it working tomorrow and ill let you know how it goes.

---

### Post by ZeldaFan on 2008-06-19
Yea, I've followed multiple guides in an attempt to get it working but the only sensors that work are the CPU core temperatures, but not the fan speeds/voltgaes. As a result, I cannot use pwmconfig. By the way, Excid, I've seen your latest guide (the .pdf on your blog) to installing ubuntu on an hp dv9000t. You said you needed testers for the TV tuner, I downloaded the required drivers. I have a tv tuner that I could test the drivers with, but I'm not exactly what you would call an expert with linux. I'm not really sure how to install the drivers, I just have the v4l-dvb drivers downloaded. Where do I go from there?

---

