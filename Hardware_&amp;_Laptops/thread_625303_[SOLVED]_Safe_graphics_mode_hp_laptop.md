---
title: "[SOLVED] Safe graphics mode hp laptop"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by Benchrest on 2007-11-27
I am trying to install Feisty on my new HP laptop DV6646US with AMD processor, Nvidia GeForce Go 7150M graphics. My live cd will not boot with graphics errors. So I tried Safe Graphics mode and it works fine except low resolution of 800x600. I figured I could install the proper graphics driver after installation. I plan to run dual boot and used the vista partition manager to set aside 2 gb for swap and 25 gb for root.

But when I get to the partitioner screen and select manual, the next screen has my partitions. I edit the entries but then found I cannot reach the bottom of the screen to select enter or go etc. The low resolution has the bottom of the screen to low to see and I cannot resize the screen. What to I do now?

---

### Post by rfruth on 2007-11-27
I had to use safe graphics mode on my desktop, good :confused:

---

### Post by Benchrest on 2007-11-27
Thanks for your reply, but I failed to get my question entered correctly. sorry , please read now.

---

### Post by rfruth on 2007-11-27
sorry I didn't answer your question correctly, during manual edit, scroll arrow keys or tab / mouse ?

---

### Post by Benchrest on 2007-11-28
I downloaded the Feisty 7.04 alternate iso last night. I understand it has a text mode install that seems like it would get around my graphics problem. Also supposed to work better with an AMD processor although I don't see what my processor would have to do with my graphics problem.  will build the cd from the download today and hopefully try again tonight. My first Ubuntu system was 5.04 and I am disappointed that each system has seemed to be a little harder to install rather than easier. I am trying 7.04 because I have heard so much bad about 7.10 with hp laptops.

---

### Post by rfruth on 2007-11-28
I agree AMD or Intel, don't see what that has to do with graphics problem - anyway if no luck try dpkg-reconfigure -phigh xserver-xorg then see if X will start (startx)

---

### Post by Benchrest on 2007-11-28
With a false start or two I finally installed Feisty dual boot. Feisty gets the same error it had with the live cd, guess I should have expected that, no safe graphics mode in normal startup so I could use the restricted driver manager to fix this. (I hope) I was able to login in text mode and try the suggested reconfigure command. Got fatal error 104 with startx. I am able to get to /etc/x11/xorg.conf from the live cd in safe graphics mode. I was able to start the editor but not sure it would let me save changes. Anyhow I am now going to search on nvidia and xorg.conf and see if there are any fixes I can make there to get graphics going. Rich

I ran the reconfigure command without the -phigh parameter and it gave me many more options. Tobe safe I set resolution to 800x600. Wala it worked. But then instead of rerunning reconfigure for the higher resolution I used the restricted driver manager to install the nvidia driver. Now when I reboot after the logo screen with a bar I got a blank screen. Now  need to use the restore/correction feature of the alternate cd or restore the original xorg.conf using live cd or reinstall or something else.

---

### Post by Benchrest on 2007-11-30
I have made some progress, but doesn't look good for short term.

I have been able to install Feisty with 800x600 graphics as follows:

Used the 7.04 alternate cd in text mode. After installation issued command sudo dpkg-reconfigure xserver-xorg, Some parameters I entered were vesta driver,  200000 graphics buffer, generic monitor, 1280x800 resolution, 1280x960 60hz    Then sudo startx and I had graphics at 800x600. 

I then attempted to install Envy. I received an error that dependancy xorg.conf.dev was missing. I attempted to install it and was not found. Another entry I found eluded to that it doesn't exist till system is updated. I installed 141 files and then Envy installed.

I ran Envy and it could not determine my graphics card and wanted me to manually enter the driver. I went to the Envy site and could not find my driver listed. Perhaps someone has the answer for me or my card is so new it might be a few weeks before a driver is available. I will research. Rich

---

### Post by Benchrest on 2007-11-30
I tried the restricted driver manager , rebooted and get a blank screen.  I rebooted in recovery mode (text) and when I startx I get the blank screen again. I will try reconfigure command again when I get time and see if I can change. Otherwise I will need to reinstall again with no resolution in sight. I could use some ideas or better yet a good tutorial. Those I have found don't address my graphics card.

---

### Post by Benchrest on 2007-12-03
Found a post on this site, [http://ubuntuforums.org/showthread.php?t=568785](http://ubuntuforums.org/showthread.php?t=568785)  that user said they couldn't get this card to work with Feisty but were able to get it to work with Gutsy. So I installed the Gutsy alternate CD, installed all updates. Then installed the Nvidia driver with the Restricted Driver Manager. Rebooted and its working. I have 1280 x 800 resolution and looks nice.  However my refresh rate is 50 hz, I believe it is 60 hz on vista. I don't see offhand how to change it or which is right. More research.


Although the "screen resolution" shows refresh rate of 50 hz, the Nvidia Control Panel shows 59.98 hz  I'm calling this good

---

### Post by UnixWarrior on 2007-12-04
Greetings ...

I can confirm that Gutsy works with the NVidia 7150 on a HP laptop.  It takes some roundabout work, but it is possible.

I just got a HP dv9500z ( AMD TL-64, NVidia 7150, etc.  w/ Vista, of course. YUCK! ):

NOTE: I used ubuntu 7.10 AMD64 & kubuntu 7.10 AMD64.

0. Gutsy 7.10 (ANY FLAVOR) will only boot in SAFE GRAPHICS mode on a hp laptop w/ 7150.

1.  The SAFE GRAPHICS mode resolution makes the ubuntu 7.10 screens too big for the screen, so you can't click the buttons on the bottom.  I used kubuntu 7.10, in SAFE GRAPHICS mode to format and partition the drive.  The KDE screens don't extend past the bottom of the screen, so clicking the buttons is possible.  Good bye Vista.:)

2.  Once the drive was partitioned w/ kubuntu 7.10, I installed ubuntu 7.10 in SAFE GRAPHICS mode.  Yes it's a pain in the *** to basically install twice, but once the drive is formatted you can just press enter on the ubuntu  7.10 install screens, so clicking the hidden buttions is irrelevant.

3.  This gives a bootable system w/ 800x600 rez. using the vesa driver.

4.  Install the restricted nvidia driver.

5. Use the "Admin" menu to change the scrren resolution to 1440x900 (in my case), YMMV.

6. Log out and log back in.  Screen should now be in high rez. mode.  The setting won't stick on a reboot, at least not in my case.  So do one more thing.

7. Down load and compile (you need GCC & Make, etc.) nvidia-xconfig-1.0.tar.gz from the nvidia Linux driver website.  You only have to unpack and run make, then run the compiled executable.
This creates a usable xorg.conf file that does have the correct settings for the nvidia card. Now you can pick your desired rez and it sticks.

8. Whew!  This was a pain, but the end result is a working ubuntu system with high rez graphics.
and it looks pretty darn good.

9.  I'm still screwing with the driver settings since I've only had this laptop 4 days, but the above should get you started.

Hope this helps.

---

### Post by t2technology on 2007-12-07
I have the same laptop (dv9500z) with the same graphics card (NVidia 7150) and everything works perfectly, without a double install. I now have the correct resolution (1680 x 1050), WiFi, and Skype with video.

Here's what I did:

**Graphics**
1. Load installer in Safe Graphics Mode.
2. Move the panels to the left and right sides of the screen. This will allow you to see the buttons on the bottom of the screen.
3. Install your favorite Ubuntu flavor (I used Linux Mint. Gotta love flash, mp3, and dvd support OOTB)
4. Click the "Restrictive driver notification" and enable the nvidia driver. 

***************DO NOT ENABLE THE BROADCOM DRIVER*********** 

5. Restart the computer and click System>Administration>Screens and Graphics
6. Click on the model and select Manufacturer>Generic and Model>LCD Panel 1680x1050
7. Make sure to also select the "Widescreen Monitor" checkbox on the bottom left of the window.
8. Click "OK" and "OK" and "Keep this resolution"

**WiFi** 
Follow these steps exactly and the blue light will come on and you will happily have wireless. Steps taken from [here]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")
1. Uninstall ndiswrapper & bcm43xx-fwcutter

```
sudo apt-get remove ndiswrapper-common 
ndiswrapper-utils-1.9
sudo apt-get remove bcm43xx-fwcutter
```

2. Blacklist the nonworking bcm43xx driver that Ubuntu tries to recommend.

```
sudo gedit /etc/modprobe.d/blacklist
```

3. add this line: &#8220;blacklist bcm43xx&#8221; (without the quotation marks&#8220;&#8221;). Save and close the file.

4. Reboot

5. Download driver for BCM94311MCG wlan mini-PCI to your home directory (/home/yourname)
[Click here to download]("http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html")

6. Move the file to your home directory if you didn't save it there in step 5 above.

7. Install ndiswrapper from source:
Make sure to hit enter after you paste each line into the terminal
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper
cd ~/bcm43xx/ndiswrapper
sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz
tar xvzf ndiswrapper-1.49.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install
```

8. Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper
```
cd /home/yourname/WLANBroadcom/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo gedit /etc/modules
```

9. Add the line: &#8220;ndiswrapper&#8221; (without the quotation marks&#8220;&#8221;) to the file. Save. Close.
```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

10. Reboot

**WEBCAM**

1. Installed Linux Mint and it worked automatically.
2. Installed Skype from Synaptic and clicked on the video preferences and the webcam showed up fine. Woo Hoo.

---

