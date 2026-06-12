---
title: "AMD Drivers breaking my system."
date: 2012-10-22
forum: Hardware
---

### Post by myromance123 on 2012-10-22
**[SOLVED] Read how I solved this in the 3rd post below. Answer is in the 3rd post.**

Hey there.
Alright, so I'm about to go a little crazy now. I have Ubuntu 12.10 64bit installed (twice now).
I have tried installing AMD's 12.9 beta and 12.10 catalyst driver from their website. Each time I do, my system breaks upon reboot. I literally cannot do anything. Not even Ctrl+Alt+F1.
The messages each time are different on screen . Once even, all it said was Starting* then Stopping*
That's it. No other information. I've tried to add an image of my screen below.
[http://i519.photobucket.com/albums/u360/my-_-romance/d89746cd477c94253884a4707063b641.jpg](http://i519.photobucket.com/albums/u360/my-_-romance/d89746cd477c94253884a4707063b641.jpg)

On the second clean install, Ubuntu already tells me I have a manual driver installed in the Additional Drivers section so I can't choose anything. How is this possible? I thought a clean install would mean that the hdd would be completely cleansed first. 500gb hdd and it only has Ubuntu installed on it. This is a desktop system.
I have an Asus AMD RadeonHD 6870 card. Heck, even phoronix had the same card and had no problems with installing the driver. What the heck is wrong with mine?

I've never had amd driver problems like this before. My card isn't even that old!
Right now it looks like I have to reinstall Ubuntu all over again, but the question is:
How in the heavens do I install my bloody AMD driver?
I've tried sudo apt-get install fglrx-updates, but although that works its seriously choppy in 3D usage!
I can't game using it. I can watch movies, albeit moving the mouse makes any video I watch flicker like mad and leave window artifacts across the screen until I minimise and maximise the window again.


I'm installing from a pen drive.
My system specs
CPU - amd 965 phenom ii 3.4ghz
Gpu - aforementioned
Ram - 8 gb corsair ddr3

**EDIT:**
On third install, I decided to try and install AMD Catalyst 12.10 using this method.
First, install the needed items:
```
sudo apt-get install ia32-libs linux-headers-generic build-essential
```

Second, in a terminal head to the driver directory. Then do this:
```
sh ./amd-driver-installer-12-1-x86.x86_64.run --buildpkg Ubuntu/oneiric
```

After it is done making the package, we now install it. Like this:
```
sudo dpkg -i fglrx*.deb
```

At this point in my install it gave me an error, saying there were unresolved dependencies. Basically it needs dkms lib32gcc1 libc6-i386. So, to make it fix itself, I then did:
```
sudo apt-get -f install
```

There, the errors were fixed. Now to do the last part:
```
sudo aticonfig --initial -f
```

Alright, its done. So I then restarted. BAM! Same problem as can be seen in the image above. Anyone reading this, I really suggest you DON'T waste your time trying to install this 12.10 Catalyst driver. It just won't work.

To summarize, I've tried installing it in these ways:
1. GUI Method ( Right click driver. set execute. Double click driver and install)
2. --force method
3. building the package method like described above

NOTHING works. I'm currently on my fourth reinstall of Ubuntu 12.10 (actually fifth, but whos counting).
I'm too scared to even try the Additional Drivers. I don't even know what the difference between fglrx and fglrx-updates is. Why? Because unlike Jockey, Additional Drivers here doesn't bother to give you information about it in the slightest.

I have no idea if fglrx is secretly 12.9 Beta or 12.10, or if fglrx-updates is 12.9beta or 12.10 Catalyst. Not a clue. I'm currently with the Open Source graphics driver now, but it means no gaming for me. For shame. Since no one has replied yet, I will guess there is no fix at the time of writing this. Non foreseeable either, since AMD only just released the new useless Catalyst 12.10.

---

### Post by myromance123 on 2012-10-23
Alright, so on my current install I decided to give the **fglrx-updates [proprietary]** driver from System Settings -> Software Sources -> Additional Drivers a go.

Long story short, it was a bad idea. Not system breaking bad though. Just that Unity and its global menu decided to not ever appear again bad. It also decides to put the resolution at 2560x1600, which is far beyond what my screen should be capable of. I'm using a HP 2509p screen with a resolution of 1920x1080. Heres a **screenshot** of it:

[http://i519.photobucket.com/albums/u360/my-_-romance/ScreenshotDesktop640x640_zpsab749e9e.png](http://i519.photobucket.com/albums/u360/my-_-romance/ScreenshotDesktop640x640_zpsab749e9e.png)

The only way to fix this is to revert back to the open source Radeon driver.
Right click -> Change Desktop Background -> All Settings -> Software Sources -> Addition Drivers, then select xserver-xorg-video-ati.

I may very well have to return to 12.04 like this.
I am going to give just the fglrx(proprietary) driver a go, but I honestly doubt its going to work at this point.

What has **NOT** worked for me thus far:
1. AMD Drivers from their website
- Catalyst 12.9 Beta
- Catalyst 12.10
2. AMD Drivers from Ubuntu's repositories
- fglrx-updates (proprietary)

What has worked so far:
1. The OSS driver.

Thankfully my Home is on a different partition, so I don't have to lose or continously backup my files. I can't imagine how many tears I'd have shed if I had not made a new partition for Home before this...

If anyone has even the slightest hint or idea on how/what I may try to fix this, please let me know.

---

### Post by myromance123 on 2012-10-24
Alright, since no one replied I am going to guess that no one knew why my system broke or just didn't care.

For all those who read this:
[SIZE="3"]The AMD Catalyst driver 12.9 Beta AND 12.10 driver on the AMD website DO NOT SUPPORT Ubuntu 12.10.[/SIZE]

More specifically, they don't support Xorg 1.13.
However, today AMD released a new Catalyst 12.11 Beta which does support Ubuntu 12.10 (Xorg 1.13).

If you are on Ubuntu 12.10 and are you using an AMD graphics card (specifically a 6000 series or 7000 series card, and I believe 5000 series cards), then you have 3 choices available to you at the time of this writing.

They are:
1. The Open Source driver (installed by default in Ubuntu 12.10)
2. The fglrx-updates(proprietary) driver from Additional Drivers
3. The AMD Catalyst 12.11 Beta driver from AMD's website.

**READ:** For AMD users who have cards from the 4000 series or OLDER, you only have the open source driver for Ubuntu 12.10. Your cards are now considered Legacy by AMD, which means the last driver to support your cards is the AMD Catalyst 12.6 driver (if I am not wrong).

**_Installing the fglrx-updates(proprietary) driver_**
This driver is technically AMD Catalyst 12.9 Beta, but AMD have made sure this one actually works with Ubuntu 12.10.

BEFORE INSTALLING IT, you must first do this. Otherwise it will not work and you will be left with a desktop with NO Unity or Global Menu.

Open the Dash, type in Terminal. Click the Terminal.
Now type this in the Terminal:
```
sudo apt-get install ia32-libs linux-headers-generic build-essential dkms lib32gcc1 libc6-i386
```

Hit Enter. When prompted, type in your password. Hit Enter again.
If it asks y/n at anytime, just hit y and hit Enter to continue.
After it has finished installing, you may now proceed with the fglrx-updates(proprietary) driver installation.

Open the Dash, type in System Settings. Click on System Settings.
In System Settings, go to Software Sources.
Now go to the Additional Drivers tab.
Click the one that has fglrx-updates(proprietary) at the end.
Click the Apply Changes Button.
After it is done installing, simply restart Ubuntu to let the driver take over. There, you're done installing fglrx-updates.

**_Installing AMD Catalyst 12.11 Beta_**
This is the latest driver from AMD at the time of this writing. It works on Ubuntu 12.10, I am using it now.

There are two ways you can install this driver.
1. GUI Method (easiest method)
2. Build it yourself (slightly more challenging)
Either one will do. The advantage of building it yourself means that whenever Ubuntu updates later on, you won't have to reinstall the driver.

_GUI Method_
Download the driver from AMD's website.
Once downloaded, extract the .zip file anywhere. To make it easy, just extract it to your desktop.

Right click the .run installer (installer name should be amd-driver-installer-catalyst-12.11-beta-x86.x86_64.run) Go to Properties. Under the Permissions tab, make sure "Allow executing file as a program" is ticked. Click the Close button.

Now double click the .run file. When it prompts you, click the Run button.
It will ask you for your password, type it in and hit Enter. Click Continue. Click I agree when the EULA appears. Make sure Automatic is clicked, then click Continue.

Once the installer is complete, just restart Ubuntu to let the driver take over.

By now you're probably noticing a small AMD Testing Only watermark on the bottom right. To get rid of this, open a Terminal.

Type in:
```
sudo gedit /etc/ati/signature
```

You will see in big letters UNSIGNED.
Highlight that and delete it. Now paste this into there:
```
b67d452b67e1e4baee18b65de7643cc0:8e537c1d56ccd588de2c866886490df38148761a24cca5eea7388168d3560bf9:8e1870185082d5dedb2ed53e835104f8d21877485fd7d282d62e8264d7005af38e4c711350d7d5dbdc2cd53e865159a5d74a76135fd0d2828a2b836bd7065af9
```

Save and close that text editor. Now log out of Ubuntu. Log back in. There should be no watermark anymore. You're done with the installation.

I obtained this signature from here:
[http://ubuntuforums.org/showthread.php?t=1988444]("http://ubuntuforums.org/showthread.php?t=1988444")
It is the signature for Ubuntu 12.04, but it works on 12.10. I have been unable to get the signature for Ubuntu 12.10.

_Build it yourself_
Download the driver from AMD's website.
Once downloaded, extract the .zip file anywhere. To make it easy, just extract it to your desktop.

Now open a Terminal. Type in this and hit Enter:
```
sudo apt-get install ia32-libs linux-headers-generic build-essential dkms lib32gcc1 libc6-i386
```

After that is done, now CD to Desktop (or where ever you extracted it).
```
cd Desktop
```

Type this in and hit Enter:
```
sh ./amd-driver-installer-catalyst-12.11-beta-x86.x86_64.run --buildpkg Ubuntu/quantal
```

After that is done, then type this in and hit Enter:
```
sudo dpkg -i fglrx*.deb
```

Once that is done, type this in:
```
sudo aticonfig --initial -f
```

Now restart your computer, and the driver will take over.
You will have the watermark on the bottom right. Do the steps as written in the GUI method above to remove that watermark and you're all set!

I'm just glad I've got my system working.
From my personal experience, the fglrx-updates(proprietary) are buggy.
They leave window artifacts on screen every once in a while and when watching movies/videos in Totem/VLC/MPlayer, if you move your mouse then it will suddenly have parts of Windows from the background appear on top of the video. I have to minimize and maximize the player to remove the artifacts.

So far, AMD Catalyst 12.11 Beta seems pretty stable (even abit smoother).

Hopefully this information may help someone out there. All the best to anyone reading this.

---

### Post by JmCourir on 2012-10-24
> **myromance123 said:**
> 
Hopefully this information may help someone out there. All the best to anyone reading this.

Hi Myromance123

Your my MAN! I was having the issue.

I am not so much familiar with Ubuntu.... Before I saw your post, I tried to install Ati drivers and FAILED! 

I'm very happy to find this article on how to do it. 
Thank you very very very much myromance, 

I very appreciate !!! 

Will try your trick tonight at home.... 

**I have a question for you.... **

I have in my computer 3 video cards: 

1X ATI HD7850  same ATI drivers
2X ATI HD6450 

Do you think I'll be able to make it all work together? 

Also, I have to mention that I have 6 monitors 
Here are the config.... 

My monitors are :
3x LG W2343TV 23" with DVI and VGA input 1920x1080
1x Acer AL2216W 22" with DVI and VGA input 1650x1050
1x Acer AL1916W 19" with DVI and VGA input 1440x900
1x Samsung Syncmaster 953BW 19" with DVI and VGA input 1280x1024

Gigabyte HD7850 GV-R7850C-2GD wich you can see on this web 
link [http://www.newegg.com/Product/Produc...YTE-_-14125419](http://www.newegg.com/Product/Produc...YTE-_-14125419)

Asus HD6450 [http://www.asus.com/Graphics_Cards/AMD_Series/EAH6450_SILENTDI512MD3LP/](http://www.asus.com/Graphics_Cards/AMD_Series/EAH6450_SILENTDI512MD3LP/)

Thank you again to have shared your tricks! :)

JmCourir

---

### Post by nardusg on 2012-10-24
I don't think it will matter but, don't you mean "quantal" instead of "oneiric" ;)

---

### Post by myromance123 on 2012-10-24
> I don't think it will matter but, don't you mean "quantal" instead of "oneiric"

Thank you for pointing that out, I mistyped that and didn't see it even after proof reading. Corrected it now, thanks again.


@JmCourir are your cards in CrossFire? I have never personally tried CrossFire, so in all honesty I have no clue.

If your HD7850 was alone, I can almost guarantee it would work.
If your two HD6450s are mixed with the HD7850, this is something outside of my knowledge. I have a feeling it may not though.

If it was just the two HD6450s, I think you would be able to CrossFire no problem.

If you can't get it to work, go ahead and make a new thread here in the Hardware section regarding it. Hopefully someone with more knowledge will be able to guide you on the matter. All the best.

---

### Post by JmCourir on 2012-10-24
> **myromance123 said:**
> Thank you for pointing that out, I mistyped that and didn't see it even after proof reading. Corrected it now, thanks again.


@JmCourir are your cards in CrossFire? I have never personally tried CrossFire, so in all honesty I have no clue.

If your HD7850 was alone, I can almost guarantee it would work.
If your two HD6450s are mixed with the HD7850, this is something outside of my knowledge. I have a feeling it may not though.

If it was just the two HD6450s, I think you would be able to CrossFire no problem.

If you can't get it to work, go ahead and make a new thread here in the Hardware section regarding it. Hopefully someone with more knowledge will be able to guide you on the matter. All the best.

Hi, 

I did your trick and it worked very good. 

No crossfire.. all independant... 

It has detected my cards very good. I did ati config and configure monitors, reboot and it went very good until I .... 
Issues on mouse, not able to move to another monitor. 

Than I activated Xinerama and reboot.... after that I saw all the same wallpaper on all monitors and able to move mouse everywhere very good.... but........ compiz crashed... not able to do anything, not even right clic on the mouse...  

:/
Now I dont know what to do ... 

JmCourir

---

### Post by sarvigalava on 2012-10-25
Hello I have a problem with ati 6750M on ubuntu 12.10. I've tested all available drivers ( from amd site and from repositories). In all cases the xserver fails with segmentation fault. The only way to start xserver is to delete xorg.conf (no unity, no window decoration, no acceleration). Amdcccle say's that no supported hardware was detected. I reinstalled ubuntu also 5 or 6 times but i haven't found any decent driver. I cannot use open source driver because  I get only 1 hour battery life (from 6 in windows). My laptop is Samsung series 7. Please help if you have any suggestions

---

### Post by myromance123 on 2012-10-25
@JmCourir, I have only ever tried multiple display configurations with a previous Nvidia setup. I wish I could help you more here, but I really don't know how to. If you really can't get it up and running, do make a new thread in this Hardware section. I'm almost certain the multi-monitor users will be able to help you.

@sarvigalava, I believe your Samsung laptop has Hybrid graphics. This means that there is no driver for your system. I personally have struggled with a 6850M Hybrid paired with Intel graphics on a HP Envy 17" earlier this year, and to this day have not been able to get it working. At best, it will only use the Intel graphics. I am sorry to say I think all you have is the Open Source driver to use. Don't hesitate to ask in a new thread within the Hardware section though. Someone may have found a way to make it work.

---

### Post by JmCourir on 2012-10-25
Hi! :)
After searching more than 3 hours, I finally found that kubuntu will work with my monitors. 

On Ubuntu 12.10 with Unity, when I activate Xinerama and reboot, Unity wont start. 

Than I installed KDE. Log into KDE and Voilà, everything is fine now. 

At least, I'll be able to switch to Ubuntu now. I want to get rid of Windows... specially that I dont want to pay no more on OS. 

:popcorn:Thank you again to explain how to install ATI Driver! You saved me a lot of time :) 
:P

---

### Post by nardusg on 2012-10-25
> **sarvigalava said:**
> Hello I have a problem with ati 6750M on ubuntu 12.10. I've tested all available drivers ( from amd site and from repositories). In all cases the xserver fails with segmentation fault. The only way to start xserver is to delete xorg.conf (no unity, no window decoration, no acceleration). Amdcccle say's that no supported hardware was detected. I reinstalled ubuntu also 5 or 6 times but i haven't found any decent driver. I cannot use open source driver because  I get only 1 hour battery life (from 6 in windows). My laptop is Samsung series 7. Please help if you have any suggestions

Hi Man


you are not alone, I am in the same boat as you are. Maybe one day...

Nar

---

### Post by sarvigalava on 2012-10-25
Thanks for reply. But Amd driver does support 6600M series. I don't think there is a laptop with 6600M card that is not hybrid. Why to release a driver it it doesn't work ?


That was a big mistake to buy a laptop with amd card. With nvidia 540m on old laptop I never had any problems

---

### Post by myromance123 on 2012-10-25
How did you manage to get a 540M working?
My sister's laptop has a 550M, and since its under Optimus there is no working driver. The open source driver is the only working thing.

Do let me know, as I'd love to get my sister's laptop fully operable with Ubuntu. Right now on the open source driver, it can play videos but I can't get the games I bought for her and my siblings to work.

---

### Post by sarvigalava on 2012-10-25
Install bumblebee. It works very well, I think that the Windows driver is better because it have GUI.

---

### Post by myromance123 on 2012-10-25
Thanks for letting me know. I've studied it a bit, and it seems Bumblebee does not yet support Ubuntu 12.10...

I guess I'll have to wait first.

---

### Post by HRH_H_Crab on 2012-10-25
> **myromance123 said:**
> 
2. The fglrx-updates(proprietary) driver from Additional Drivers


On my system at least this driver is buggy as hell has resulted in horrible screen artifacts, X freezing, and about 9 gnome-panels stacked on top of each other. I'm sticking to the open source driver until someone at Ubuntu and / or ATI works out what the hell they are doing.

---

### Post by myromance123 on 2012-10-25
Yeah it was pretty buggy for me as well, with the screen artifacts. However, yours seems a lot more serious. What card are you using?

If you're really in need, you may as well give the Catalyst 12.11 Beta driver a go. I am currently using it now, and there are no screen artifacts or any problems (yet).

With fglrx-updates(proprietary), there was also the problem where if you opened Unity's dash any videos in the background would suddenly start crawling in playback (for me). The 12.11 Beta doesn't have this problem.

Lets say you do try the Catalyst 12.11 Beta and it just isn't working for you and you want to revert back to the open source driver, heres what you can do. _This is only if you installed it via the GUI Method._ I still don't really have a clue how to uninstall it when building it myself (looks like I use the Additional Drivers section).

Open a Terminal, and:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

This should uninstall the AMD driver naturally, and after you restart you should have the open source driver back in its place. There was also an amd-uninstall.sh script in that same folder, and that was the one I used to run to uninstall the driver and it works just as well (in my experience).

---

### Post by HRH_H_Crab on 2012-10-26
I've got a Radeon HD7500 series card.
I'm not really desperate enough to put the time into drivers downloaded from ATI although I don't dispute that they may work very well.

My philosophy is that if I can hose Xorg completely by using drivers distributed (if not supported) by Ubuntu then I'm not going to mess with those distributed by a third party.

Regarding your question about uninstalling the AMD package from the commandline, since it was made as a deb I guess you can use apt-get / dpkg.

---

### Post by mastablasta on 2012-10-26
> **myromance123 said:**
>  
**READ:** For AMD users who have cards from the 4000 series or OLDER, you only have the open source driver for Ubuntu 12.10. Your cards are now considered Legacy by AMD, which means the last driver to support your cards is the AMD Catalyst 12.6 driver (if I am not wrong).
.
 
that is nto exactly true. it is the legacy driver as it is no longer developed (was already developed to the max they say). so in order to use fglrx on those older cards you need to install the legacy packages not the regular catalyst. and it should work with 12.10.
 
LINK with instructions and explanation: [http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)

---

### Post by myromance123 on 2012-10-26
@mastablasta, I am still technically correct. You should read further down into the comments. To make the current Legacy 12.6 driver work, his PPA downgrades Xorg to 1.12.

To say that there is no current legacy driver for Ubuntu 12.10 is in fact correct, if you stay with the default Xorg 1.13 that Ubuntu 12.10 uses.

But it is good you highlighted that article, hopefully others may benefit from it. His PPA can help anyone using Ubuntu 12.10 that has no real need for Xorg 1.13 (although I don't know if this will cause problems later on or not). Thanks for the information.

NOTE: If however, the Legacy driver from AMD's website has been updated then it will hopefully support Xorg 1.13. I don't yet see this though.

---

### Post by harpal on 2012-12-22
helo myromance, I downloaded amd 12.11 beta drivers for my radeon HD7600m series graphic card for quantal quetzal. I tried to install them with GUI but it does not show any text. All the buttons are displayed but not the text. I also tried to build it, but it displayed an error. Then I installed proprietory drivers from software sources. When i rebooted my laptop it showed me black screen with an error dialog box saying that your computer is running at low graphics memory. When I pressed <enter> it showed me four options but I can't do anything. No pointer nor the <enter>  is working. All I can do is open virtual console. I am new to ubuntu plz tell me what to do??




Anyone please help..??

---

### Post by velocity303 on 2013-01-08
Thank you so much for this :) I have the exact same problem and have been struggling with it! I actually have the exact same graphics card.

---

### Post by Narf on 2013-01-09
I have an ATI Mobility HD 7650M and neither fglrx-updates or the beta drivers work. Both produced the same result - my laptop freezes during boot time (and I guess X crashes) with no option to do anything, even the keyboard doesn't work.

---

### Post by starfyredragon on 2013-01-11
> **myromance123 said:**
> **Awesome set of information.** I just thought you might like to know, I've been trying to get AMD drivers to work on 12.10 for DAYS now. However, every post that helped that I've seen has seemed to reference the detective work you've done.

I think you're officially the Radeon HD 5XXX+ for Ubuntu 12.10 guru of the internet. ;)

---

### Post by Narf on 2013-01-13
> **harpal said:**
> helo myromance, I downloaded amd 12.11 beta drivers for my radeon HD7600m series graphic card for quantal quetzal. I tried to install them with GUI but it does not show any text. All the buttons are displayed but not the text. I also tried to build it, but it displayed an error. Then I installed proprietory drivers from software sources. When i rebooted my laptop it showed me black screen with an error dialog box saying that your computer is running at low graphics memory. When I pressed <enter> it showed me four options but I can't do anything. No pointer nor the <enter>  is working. All I can do is open virtual console. I am new to ubuntu plz tell me what to do??




Anyone please help..??

FYI, you most likely doesn't have the kernel headers installed. However I do and I have a graphics card from the same series - when the driver is properly installed it's even worse - you can't even switch with Ctrl+Alt+FX.

---

### Post by harpal on 2013-01-17
can you please tell me how to install them?

i actually have reinstalled ubuntu so i don't want to loose my system again..

---

### Post by myromance123 on 2013-01-17
@starfyredragon
Thanks for the kind words, my good man :)

@Narf and @harpal,
The 'm' on your card's names means it's a mobile component.
This means you guys are using a laptop/netbook or some form of mobile computer. If you have an Intel CPU (Ivy Bridge or Sandy Bridge) then you most likely have _Hybrid graphics_.

I personally **_do not know_** how to get Hybrid graphics working in Ubuntu.

My information is meant specifically to help desktop users.

I have done some searching for you guys, and these two posts seem like they might help you guys out:
[Original AskUbuntu post]("http://askubuntu.com/questions/205112/ubuntu-12-10-amd-intel-hybrid-graphics-not-working")
[Ubuntuforums post]("http://ubuntuforums.org/showthread.php?t=2083181")

All the best.

---

### Post by harpal on 2013-01-19
yeah i have intel sandybridge graphic card..
thanx for your help myromance..:-)

---

### Post by harpal on 2013-01-19
Hey myromance I followed the guide and installed the required files. But when I tried to build the package I got the following error:

Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
./packages/Ubuntu/ati-packager.sh: 295: ./packages/Ubuntu/ati-packager.sh: dpkg-buildpackage: not found




How to fix it??

---

### Post by myromance123 on 2013-01-21
Lets make sure your computer has the necessary tools to build packages first.

Open any terminal, and Enter this:
```
sudo apt-get install build-essential
```

I could be wrong, but the errors seem to me like your system doesn't have what it needs to build the package. Hopefully by installing build-essential, you should be able to get past those errors.

According to your debclean error, I think you need to install devscripts. I am not sure what it's called in the repositories at the moment but try :
```
sudo apt-get install devscripts
```

I have never run into these kinds of errors before, so my attempts at helping you here are guess work. Hopefully someone more knowledgeable may guide us on what the necessary solution to these errors are.

---

### Post by harpal on 2013-01-25
Hey myromance I followed the guide.
I am going crazy now.. I installed the files and then downloaded the two .deb files from the updated ppa. After reconfiguring Xorg ang rebooting, virtual console instead of login screen opens up.

Now what's this???

---

