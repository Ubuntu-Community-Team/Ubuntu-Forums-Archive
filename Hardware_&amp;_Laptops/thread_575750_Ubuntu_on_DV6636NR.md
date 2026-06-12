---
title: "Ubuntu on DV6636NR"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by Dark_Stang on 2007-10-14
**This is an archived version of the tutorial. The current, maintained version is located [here]("http://ubuntuforums.org/showthread.php?t=870575").**

This will be an ongoing writeup, so don't be surprised if it changes frequently. If I'm having a problem at any particular point and don't have a solution yet, please check back (or post the solution if you know it).

**Important!** The newest HP Laptops in the AMD family use atheros wireless cards instead of broadcom cards. This guide will not work for those wireless cards as far as I know (unless atheros is using a broadcom chip). So if your laptop is a x500z or x600z series this guide will work. However the x700z series and newer will not.

**Notes on 8.4** See the end of this post for special notes on installing on 8.4 beta. Read them **BEFORE** installing. I **encourage** installing 8.4 after using it for the last few days. It is very stable and the minor issue of caps lock randomly breaking the side scroll on the touchpad is no longer existent. But please be sure to read the special notes at the end of this post before installing 8.4. 

These are detailed instructions in setting up Ubuntu 7.10 x86 on an hp dv6636nr laptop. I have not migrated to 64bit yet because of complications with flash and Java and I suggest sticking with 32bit if you don't want to worry about it either. I don't know if this will work the same for your laptop, even if it's in the same series and has nearly identical hardware. That said, my brain tells me that this *should* work on any hp laptop in the dv2500z, dv6500z,  and dv9500z series that are BEFORE THE x700 series. The newest HP laptops have atheros cards in them and are different as far as I know.

I don't know if this will work for another distro, but I encourage you to try.

Note to veterans and experienced users: This is a step by step, or at least close to it, walk through of setting up Ubuntu on this laptop. I encourage you to skip ahead if you know what you're doing.

Things that don't work the way I want them to yet:
The microphones sound choppy and faint. That's about it.

**Chapters**
Hardware
Pre Installation
Installation Walk Through
Post Installation Setup (nvidia card, wifi card, sound card)
Fixing Open Office Glitches
Miscellaneous Curiosities
Overheating Problems?

**Hardware**
Processor: AMD Turion X2 - TL58.
Graphics Card: NVIDIA 7150M.
Wireless Card: Broadcom BCM 4311 (rev 02) Also known as BCM94311MCG wlan mini-PCI (rev 02)
Memory: 2048 mb
Hard Drive: 160 gb 5400 rpm
Disk Drive: CD/DVD Multi with Light Scribe (haven't tested light scribe out yet)
Card Reader: Untested
Webcam: Works by default
Microphones: Work by default
Speakers: Excellent sound, no distortion.
Media Remote: Works be default

[SIZE="3"]**Pre Installation**[/SIZE]
What do you need?
Ubuntu 7.10 Disk
Ethernet Cable and Working Internet
An Open Mind

[SIZE="3"]**Installation & Setup**[/SIZE]
	You must use the Ubuntu 7.10 (or newer when they come out?). Ubuntu 7.04 crashes the x-server non-stop. I didn't try 6.10 or anything earlier than that. Download and burn yourself a CD. I used the x86 based version, just so I wouldn't have to do any workarounds for flash or anything like that. Until everybody updates their software to 64bit, I encourage to stick with 32bit to prevent any problems.

	After you burn your CD pop it in the laptop and restart. Once the Ubuntu LiveCD boot menu comes up, just select “Start Ubuntu in Safe Graphics Mode”.

**Temporary graphics improvement:**
	Once Ubuntu loads up and you have your little desktop go to System > Administration > Screens and Graphics. Once the window loads click the box next to Model:  Now, select Generic as the manufacturer, and Monitor 1024 x 768. Do this even though this isn't correct. This is just to make our lives easier for this installation. We will install the nvidia drivers later.

**Shrinking Vista**
	Now, some of you may want to keep Vista on your system still. I did just in case I was going to have some major problems with Ubuntu. This part is for you. Go to System > Administration > Partition Editor. Now right click on your Windows partition, and click resize. Enter it's new size in MB, and click resize. I shrank mine down to about 40000mb. If you'll be using Windows a lot more than Ubuntu, or are just testing Ubuntu out, don't shrink it down that much. Now that you've selected what size you want it to be, click apply. We won't bother making the other partitions for Ubuntu yet.

**Installing Ubuntu**
	Now, go ahead and double click the install icon on the desktop. The first few steps are self explanatory. Select your language, your time zone (which is actually dumb because my timezone isn't on there...). Then select your keyboard layout. Now, it's going to say “Starting up the Partitioner.” Select Manual, and go Forward. Now you should see your shrunken Vista partition and the HP Recovery partition if you kept them, and your free space. I now have two ways for you to do this.
	1.If you're just trying Ubuntu out, and didn't shrink Vista that much, do this method. Select your free space, and click “New partition”. For type of partition select logical. For new partition size just do 1000. For location select beginning. Use as swap. And click okay. Now click the rest of your free space and create another new partition. Select primary for the type, all the space left for the size, beginning for the location, and use as ext3. Now click your partition you just created, click edit, and select “/” as your mount point.
	2.For those of us who will be using Ubuntu as our main or only operating system we should do this. Go to the free space and click “New partition”. For the type select logical, for the size do 2000, for the location select beginning, and use as swap. Now click okay. Create another new partition, for the type select primary, for the size do 10000 to 20000 (this will be the operating system's partition), and use as ext3 (or if you have another preference use it). Now create another partition, for type use primary, use the rest of the available space for your size, and use as ext3. Now we need to go back and edit the partitions. For the first one make the mount point “/”, for the second one make the mount point “/home”. This keeps all your files  on a separate partition so you can reformat the Ubuntu partition without fear if you completely screw something up, or want to do a fresh upgrade/install.
	Now go ahead and click forward. Ubuntu is going to tell you there were no users or operating systems suitable for importing from. Go ahead and click forward again.

	Now just fill out the information in front of you. And click forward again.

	Now you have a summary of your settings so far. If you see something incorrect, go back and fix it. If everything is okay, click install. After the installation is finished go ahead and restart your laptop.

[size="3"]**Post Installation Setup**[/size]
Now then, plug in that network cable because it's about to get fun. Undoubtedly Ubuntu will see updates as soon as you hook up the cable, but we'll let them go for now. We have more important things to do.

**Configuring the Nvidia 7150 Card and Screen**
	Lets get this thing going. Go to System > Administration > Restricted Drivers Manager. Check the box to enable the restricted driver for your Nvidia card, but do not enable the wifi card as it is not supported even though it says it is. Now Ubuntu will setup your nvidia card. 
	Now, lets setup your screen. The method I use may seem to overwhelm you at first, but it really is easy. Press Ctrl+alt+F1 to get to terminal. Login. Run  ```
sudo /etc/init.d/gdm stop
```
It will ask for your password. We just shut down the x-server so we can reconfigure it. Now run ```
sudo dpkg-reconfigure xserver-xorg
```
	1.Select no to auto detect our setup.
	2.If the nvidia driver isn't already selected, select it with the arrow keys, hit tab and then enter to continue.
	3.Continue with default options until you are asked if it should use a kernel frame buffer. Select no and continue.
	4.Go ahead and click yes to have it detect the keyboard.
	5.For the mouse use the PS/2 and to emulate the 3 button mouse.
	6.Click yes to writing default files section to configuration file.
	7.Click no for attempting monitor detection.
	8.Go ahead and give your monitor a name.
	9.Now we're at the important part. Scroll down the left side with the arrow keys until you see “1280x800”. Hit the space bar to check that box, a little asterisk will appear. Now uncheck all the other boxes, hit tab and enter to continue.
	10.Select medium for setting the monitor up, we're not entirely dumb.
	11.Scroll down to “1280x960 @ 60 Hz”, hit tab and enter. (i know it isn't 100% right, but it works just fine)
	12.Select yes for writing monitor ranges.
	13.For desired color I chose 24. If you feel like you're getting slow performance you can come back and choose 16 later, however 24 feels great to me.

Now that we're all done enter ```
sudo /etc/init.d/gdm start
``` Your login screen will come right back up. Did you like that nvidia logo? Sexy, isn't it?

**Wireless Card Setup**
Download and extract the files I have [here.]("http://www.darkstang.com/wifi.tar.bz2")
If that link doesn't work, go to [this one here.]("http://www.gotode.com/wifi.tar.bz2") - (one of my client's sites, temporary fix)
Now go to System > Administration > Synaptic Package Manager.
	While we're here we're going to unlock all our repositories. Go Settings > Repositories. Check all the boxes on the first page except for the CD, and hit close. A window will pop up telling you that you need to  reload your packages. Go ahead and close that window, and click reload at the top.
	Once that is finished click in the main window and start typing “ndiswrapper”. It will automatically scroll down and find it. Click the box next to “ndiswrapper-utils” and click “Mark for Installation”. Now go ahead and click Apply at the top.
	After that is installed open a terminal window. Applications > Accessories > Terminal. Navigate to where you saved the drivers I had you download and extract. Now run the following
```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
```
	Our wireless driver is now installed but not working just yet. It's currently being blocked by another driver that is trying to run, so we need to block this other driver. Run 
```
sudo gedit /etc/modprobe.d/blacklist
```
A text editor will pop up with the blacklist. Go to the end, start a new line, and enter “blacklist bcm43xx” without quotes. Save the file.
	Now for some reason ndiswrapper doesn't load automatically when it starts up. So now let's add it to the modules list. 
```
sudo gedit /etc/modules
``` 
Make a new line and add "ndiswrapper".

	After a restart your wireless should be working and the light should be glowing blue. Congratulations, you now have a functional wireless card.

	Now that you have a functional laptop, lets go ahead and do those updates.

**Fixing the Sound Card**
For some reason my laptop speakers refused to auto-mute when the headphones were plugged in. If your laptop is doing this as well simply open up the file /etc/modprobe.d/alsa-base and add "options snd-hda-intel model=laptop" to a new line. Note: This *may* require you to update to alsa 1.0.15, if you find this is the case or just want to upgrade alsa simply follow these steps.

To be honest, I don't know all the dependencies you'll need because I didn't make notes and I've installed a few other packages from source so I may have filled in some dependency problems there. But alsa will tell you if you're missing something and tell you what to get during configure. I know you need build-essential, ncurses-dev, gettext, and your headers, so just run these in a terminal to get those out of the way.
```
sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`
```
Download the driver, lib, firmware, oss, and utils package from the alsa project's website [here]("http://www.alsa-project.org/main/index.php/Download"). Now extract the files.
Now open up a terminal, and you'll have to simply do these steps in each folder you just extracted.
```
./configure
make
sudo make install
```

**Fixing Open Office Glitches**
For whatever reason, OpenOffice.org and Compiz do not play nicely on my laptop. If you want to have nice desktop effects and still work with open office, here's how you fix this.
Open up synaptic package manager. Remove the packages "OpenOffice.org-gtk" and "OpenOffice.org-gnome" and install the package "CompizConfig-Settings-Manager".
After that's all done go System > Preferences > CompizConfig Settings Manager. Now scroll down to the Utility section, click Workarounds (not the checkbox) and uncheck "Legacy Fullscreen Support". Now OpenOffice should work just fine.

**Miscellaneous Curiosities**
The model number for the laptop is dv6500z. This is just a variant of it. Which *should* mean this will work with any dv6500z laptop. Or, for that matter, any dv2500z, or dv9500z laptop.

The wireless card in this laptop is in a lot of other hp laptops. I've heard the drivers I've posted here work for just about all of them. 

The webcam and microphones work by default (webcam works in amsn and cheese). The microphones aren't very clear though, I've tried to play with many alsa settings with no luck yet.

The media remote works by default.

For some reason the login manager comes up very quickly but gnome takes a few seconds to load up. I'm not worried about it, it's just kind of strange.

**Overheating Problems?**
I've heard a few people say they are worried about their HP laptops overheating. I've been keeping an eye on mine and it seems like the hottest my processor gets is about 61C on Core0, and 53C on Core1. However this only happens whenever the processor is running full out. Most of the time my temps are around 41C on Core0 and 32C on Core1. I sent an e-mail to AMD and their response was...
> The temperatures you have reported is still within the safe range.
Turion X2 processors have a built-in failsafe which will trigger system shutdown / reboot when the maximum operating temperature is reached.
I trust AMD. So in my mind, there are no overheating problems. There was a BIOS update released from HP that supposedly has better fan control, however it seems as though it requires you to still have windows on the machine to use it. If you still have windows on it and want to do the update, you can get it [here]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&dlc=en&product=3548621&lang=en") on HP's site.

**Installing on 8.4** Okay, you can pretty much ignore the graphics card and sound card setup in this guide. For the graphics card just install via restricted drivers manager. Ubuntu automatically takes care of your resolution after that. The sound card is configured by default. Follow the wireless card guide plus these extra few steps.
enter ```
sudo gedit /etc/init.d/wifiFix.sh
```
Now copy and paste this into the file, then save it.
```
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 
```
Now enter this into a terminal
```
sudo chmod 755 /etc/init.d/wifiFix.sh
sudo update-rc.d /etc/init.d/wifiFix.sh defaults
```
This fixes a small wireless card glitch that's happening in 8.4 beta (this may be fixed by the release, i'm not sure)

Also, in 8.4 after the nvidia driver install it autodetects the correct resolution to run at on my laptop. So 8.4 users may skip the graphics card section of this guide.

Now, if you're using an external monitor or a tv I suggest installing the NVIDIA X Server Settings package that can be found in Add/Remove programs. This will allow you to change resolutions on the fly and get external monitors working with a simple x restart (logging out and logging back in).

---

### Post by Dark_Stang on 2007-10-14
A mod can delete this.

---

### Post by Dark_Stang on 2007-10-14
A mod can delete this too.

---

### Post by Dark_Stang on 2007-10-14
Delete this post if you feel like it.

---

### Post by Dark_Stang on 2007-10-14
And a mod can delete this too.

---

### Post by ugly_b on 2007-10-20
Your wireless card instructions worked for my laptop!!!

I have given up hope for a few days now and thought I would try your driver just for the heck of it.  And now my wireless works perfectly.  Thanks a bunch for your posting!
I've tried ndiswrapper before, but with version 6 of the windows drivers.  And that did nothing at all.  The drivers you posted nailed it.

Here's my Specs:
Ubuntu 7.10 AMD64
HP Pavilion dv9628nr
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
This is the chipset which won't be supported by bcm43xx for a long, long time.

Cheers.
[www.WheresMyStar.com](www.WheresMyStar.com)

---

### Post by Dark_Stang on 2007-10-21
Good! I'm glad to hear I helped somebody with this. I just looked up your laptop and it looks like it has many of the same parts as mine. Same memory, same processor, same wireless card, same graphics card. If you can confirm the other steps for me I'll start a small compatibility list at the top of the guide.

---

### Post by jardo on 2007-10-21
i'm glad to know that bcm43xx works with that wireless card....could u try those for some day and tell me if still keeps working good...cose i have same wireless card but it gives a lot of problem...at begin seemed working ok,but then,low speed not connected always far away from pc... i want to understand if it's my problem or driver:) thanks

---

### Post by Dark_Stang on 2007-10-21
> **jardo said:**
> i'm glad to know that bcm43xx works with that wireless card....could u try those for some day and tell me if still keeps working good...cose i have same wireless card but it gives a lot of problem...at begin seemed working ok,but then,low speed not connected always far away from pc... i want to understand if it's my problem or driver:) thanks
The bcm43xx doesn't work with this wireless card. My method posted here uses ndiswrapper and the windows drivers.

---

### Post by ugly_b on 2007-10-21
> **Dark_Stang said:**
> Good! I'm glad to hear I helped somebody with this. I just looked up your laptop and it looks like it has many of the same parts as mine. Same memory, same processor, same wireless card, same graphics card. If you can confirm the other steps for me I'll start a small compatibility list at the top of the guide.

Hey Dark_Stang,

Unfortunately I can't confirm your other steps for installation.  Mine was quite different for setting up everything else.  Probably this is because I installed the AMD64 version.  Here's some notable exceptions in my case:

Using the normal Desktop Ubuntu CD, I couldn't install with the first option.  The installation would always hang at the video selection screen.  I installed with the second option.  This loaded the OS with low resolution mode.  Then I used the installation icon on the desktop to install.

I didn't keep Vista on my machine.  I went full on Ubuntu.

I had no problems setting up my video.  After loading the restricted drivers, I ran nvidia_settings and changed the resolution to 1440x900.

My wireless wouldn't work using anyone's instructions online.  At the bcm4xx website, the developers said that my chipset isn't supported and won't be for a long time.  I tried anyway in vain.  My windows drivers came with bcmwl6.inf, bcmwl6.sys, and bcmwl664.sys.  These wouldn't work with ndiswrapper for me.  But your included drivers worked!

I have no OpenOffice glitches either.  Compiz works just fine.

I haven't been able to try the webcam and microphone yet.  I don't even know what app to use with it yet.

Thanks again!

---

### Post by ugly_b on 2007-10-21
I've installed 'cheese' to test out the webcam and microphone.  The webcam works great.  But recorded sound through the microphone sounds terrible.  I've tried the Sound Recorder application as well, with the same results.  The resulting audio is like 50% my voice and 50% static/noise/hissing.

lspci says: 00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
alsamixer says: Card: HDA NVidia, Chip: Conexant CX20549 (Venice)

Here's the levels I have using alsamixer:
Master: 74<>72
PCM: 93
IEC958: MM
Ext Mic: MM 78
Int Mic: 78

I tried fiddling with these levels a bit, but the hissing won't quit.  Is your recorded audio better?
Any ideas?

---

### Post by refusenik on 2007-10-24
Thanks!  The wireless drivers you provided work great with my Compaq Presario C714NR under ndiswrapper!  Though instead of creating that script to load the module at boot time, I just added "ndiswrapper" to /etc/modules.

---

### Post by Dark_Stang on 2007-10-24
> **refusenik said:**
> Thanks!  The wireless drivers you provided work great with my Compaq Presario C714NR under ndiswrapper!  Though instead of creating that script to load the module at boot time, I just added "ndiswrapper" to /etc/modules.
Thanks for that! I didn't even think about adding it to the modules list, now I feel a little dumb. I fixed it in the walk through.

To anybody that has done it my way and wants to change it to this way:
"sudo update-rc.d -f ndiswrapper remove"
Then add ndiswrapper to the modules list.

---

### Post by Dark_Stang on 2007-10-24
> **ugly_b said:**
> I've installed 'cheese' to test out the webcam and microphone.  The webcam works great.  But recorded sound through the microphone sounds terrible.  I've tried the Sound Recorder application as well, with the same results.  The resulting audio is like 50% my voice and 50% static/noise/hissing.

lspci says: 00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
alsamixer says: Card: HDA NVidia, Chip: Conexant CX20549 (Venice)

Here's the levels I have using alsamixer:
Master: 74<>72
PCM: 93
IEC958: MM
Ext Mic: MM 78
Int Mic: 78

I tried fiddling with these levels a bit, but the hissing won't quit.  Is your recorded audio better?
Any ideas?
My microphones aren't working very well now either. They worked okay (not great, but okay) when I first installed. However I noticed my headphone jacks didn't work so I installed Alsa 1.0.15 and now my microphones absolutely suck. This is something I'll be working on as well. However between hacking this laptop, doing all my work for my gen ed classes, programming for my java class, and work my time is pretty stretched out. Just keep track of this thread, I'll let you know if I find anything else out.

Edit: Today I played around with the digital switch. I found out that the more i turn that up the louder everything gets... unfortunately static and all.

---

### Post by Dark_Stang on 2007-12-05
Fixed the headphone jacks and automute, updated the howto. You *may* have to update alsa to the 1.0.15 version for this to work, I never tried it with 1.0.14.

---

### Post by stlcoptony on 2007-12-13
Can anyone confirm that this will work with a HP dv6646us? Seems to have the exact same hardware, except for the wifi, which I think is a broadcom 4321 802.11 a/b/g/n. I bought this to run ubuntu only, only to find that the 7150 is unsupported and that there are apparently a lot of problems with HP laptops and linux. I hope they fix this because I think HP makes some very good laptops.

This is for the person with the microphone problems. I was listening to a podcast (linux action show, I believe) and someone called in with this problem. They said the static/noise is due to the integrated audio card, and that windows drivers correct for this, but linux drivers do not, as it wastes cpu cycles. Their suggestion, if you want a microphone, was to buy a $10 playstation USB headset off ebay. Apparently they work very well. Hope this helps.

let me know if anyone has my model of laptop working, I'm just itching to remove vista....

thanks

---

### Post by stlcoptony on 2007-12-13
Also, I can't get your website or the download for the wireless drivers to work?? [www.darkstang.com](www.darkstang.com) won't even come up.

thanks

---

### Post by stlcoptony on 2007-12-13
Sorry for the multiple posts, but one more thing. So far everything has worked (haven't tried the wireless yet) and I now have a working laptop with ubuntu only. When I configured the x-server, you said to leave the line where it asks you how much memory to devote to the video card blank. Since the 7150M uses system memory, shouldn't that be configured? Or does the system detect that on its own?

thanks, great work on the how-to

---

### Post by Dark_Stang on 2007-12-13
I'm going to have to switch web hosting... friendliest people on the world, but the server I'm on has had a horrible uptime lately. If anybody needs the wireless card drivers just PM me or e-mail me and I'll send them straight to you.

stlcptony - According to HP's website it's the same broadcom driver for your card. So I'm going to guess that it will work for you. I'm not sure if you will get full N functionality though. My site seems to be up now, if you need me to e-mail you the drivers just pm me your e-mail address.

And yes, the system should autodetect how much memory to give it, and even adjust to whatever it needs at the time. Anybody can feel free to correct me on this statement, but as far as I know the 7150m card is flexible and will take 64mb and up, depending on what it needs.

Edit: So for a temporary fix (until I get a different web host) I uploaded the wireless drivers to one of my client's websites. Please don't use it unless the other one is down... although it really won't matter because he has an insane amount of bandwidth that goes unused each month.

---

### Post by iamjfarrell on 2007-12-14
I just recently got the dv9628nr but I can't use it till chirstmas. I plan on installing it then and getting it together. I will try your method, but I want 64bit.

---

### Post by Dark_Stang on 2007-12-14
> **iamjfarrell said:**
> I just recently got the dv9628nr but I can't use it till chirstmas. I plan on installing it then and getting it together. I will try your method, but I want 64bit.
I'd print off a copy of my directions, and take some notes from what ugly_b said about his 64 bit install. And if you wouldn't mind please post any problems you had with it or differences between my notes and what you did. The 9628nr is pretty much a 17" version of the 6636nr with a larger hard drive, so I doubt you'll have any problems.

---

### Post by gfd_2 on 2007-12-14
i was borrowing an Acer 7720 for a while and got everything up and running... i just bought an HP DV6633US from CircuitCity... should have it home in about an hour... I was worried about how things would go when I killed Vista and installed Gusty... I'll let you folks know.

---

### Post by gfd_2 on 2007-12-14
I'm back and while I have a wired HP 6500 there's no sound and no network and it would appear no video card as I'm running at 1024x768.

The lite next to the wireless switch only came up orange and will not recognize my wide open network.  I've gone through the ndiswrapper process twice just to make sure that I didn't miss anything and the 2nd time around it told me the driver was installed and module loaded.

I backed everything out and activated the restricted driver for wireless (firmware for Broadcom 43xx chipset ) and now the blue light is on but still no connectivity.

as far as sound goes.... I've downloaded the three lastest Alsa files and installed them and am voila!  Rhymbox tells me it can't open the source CD.... 

I'm downloading Amarok now...

---

### Post by gfd_2 on 2007-12-14
and da nada... sound light is blue... but Amarok coughs up an error "output device is busy" ... reformat and reinstall and try it again...  


in the meantime... anyone have a suggestion on getting sound/ wifi to work on an HP DV6500?

Thanks.

---

### Post by gfd_2 on 2007-12-14
alrighty then.... third times a charm... wiped the system and reinstalled but didn't go into safe mode... graphics are set to 1280x800.  now the system sees my network so I unplugged the wire and clicked on my wireless network name... the connecting icon starts going but no connection.  Interesting as I have no security setup ( a bonus of not having neighbors with computers) and after ~ 30 seconds no connection...

---

### Post by Dark_Stang on 2007-12-14
The 6633us is a completely different laptop, it uses all intel hardware, which puts it in the 6500t series. Therefor this thread is useless for you... sorry.

---

### Post by stlcoptony on 2007-12-15
Well, for the compatability list, the HP dv6646us works beautifully after following you how-to, darkstang. I now have full functionality, wireless, graphics, etc. 

Just out of curiosity, would these steps (like the terminal commands) work with other distros? I'm wondering because I would like to try out other distros for fun on this laptop. Also, entering commands into the terminal means the same thing as the "bash shell" right? Where could I look to learn things like this? I'm all for using the command line, but I would like to know why I'm doing the things others suggest.

thanks

---

### Post by Dark_Stang on 2007-12-15
> **stlcoptony said:**
> Well, for the compatability list, the HP dv6646us works beautifully after following you how-to, darkstang. I now have full functionality, wireless, graphics, etc. 

thanks
Does your name mean you're a cop in St. Louis? If so... could you remember this if you ever pull over a Blue 2002 S-10 that's a zq8 from Illinois?

---

### Post by stlcoptony on 2007-12-15
Ha, I would if I could. I go to stlcop -- St. Louis College of Pharmacy, thats where the name and lack of free time comes from. Any suggestions about where to go to learn about the command line and what different commands do? For example, are most of them cross-distro? Will the commands I used to set up my laptop work in fedora or sabayon?

I would have thought from the name you had a mustang, or at least a ford. seems we were both decieved.

thanks

---

### Post by Dark_Stang on 2007-12-15
For learning shell you could take a look at [this guide.]("http://gd.tuwien.ac.at/linuxcommand.org/index.php") For commans you're unsure of get familiar with the "man" command so you can lookup information about them. Many commands will be cross distro. However the makeup of filesystems can be different. A debian file tree will be different from a red hat file tree, and so on.

And I don't have the mustang yet, but I love them. I won't be able to afford one until after I graduate and land that dream job at Sun Microsystems or Google.

---

### Post by stlcoptony on 2007-12-15
I don't know where you're at in Illinois, but are you guys getting all this snow too? We're supposed to have a foot in the morning..... That ought to make the drive to work more fun

---

### Post by Dark_Stang on 2007-12-16
Updated howto: Added how to install the alsa 1.0.15 drivers and a few extra goodies because I found out people might be getting stuck there.

Edit: Just wrapped all command line actions in code brackets so they're easier to identify. Thought this might make it easier on some people.

---

### Post by stlcoptony on 2007-12-18
Don't know if this helps, but on my laptop I installed the 64-bit version following the how-to and it also works great. everything worked the same as with the 32-bit version

---

### Post by Ryuji5864 on 2007-12-20
Error >.<

david@david-laptop:~$ sudo apt-get install build-essential ncurses-dev gettext
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


david@david-laptop:~$ sudo apt-get install linux-headers-`uname -r`
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Dark_Stang on 2007-12-20
> **Ryuji5864 said:**
> Error >.<

david@david-laptop:~$ sudo apt-get install build-essential ncurses-dev gettext
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


david@david-laptop:~$ sudo apt-get install linux-headers-`uname -r`
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
You have another package manager running.

---

### Post by stlcoptony on 2007-12-21
Looks like you have either synaptic or the update manager running at the same time

---

### Post by sergiom99 on 2007-12-22
Im a noob, i know, but I am installing Kubuntu Gutsy on a DV6646us, and when I get to the part to stop and/or start gdm, i get a msg that the file doesnt exist.
I cant load KDE when booting, guess are the Nvdia drivers.

Any help please?

---

### Post by pndragon on 2007-12-22
I've tried to update my alsa drivers following your directions. Now, whenever I rollover the speaker icon I'm getting a tooltip that reads "Mixer cannot be found" and no sound at all. The update however went pretty smoothly.

Any help would be appreciated

--- Jim

---

### Post by sergiom99 on 2007-12-22
Hey, I managed to install in a DV6646us (Kubuntu AMD64), got the Nvidia working ([http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)), wireless, and installed the ALSA as you mentioned, however headphone jacks doesnt work and speakers are not turned off when headset is plugged (installing ALSA f$@ked Nvidia BTW).
Anything else I should do?

---

### Post by DonDodge on 2007-12-22
> **Dark_Stang said:**
> 
These are detailed instructions in setting up Ubuntu 7.10 x86 on an hp dv6636nr laptop. I don't know if this will work the same for your laptop, even if it's in the same series and has nearly identical hardware. That said, my brain tells me that this *should* work on any hp laptop in the dv2500z, dv6500z, and dv9600z series. I've become intimately familiar with these laptops as I sell them all day long at my job, but I can't promise anything..

Dark Stang, since you're in the biz, do you know if a Compaq Presario F730US  crosses over to the HP models you mention?

It's a 1.8 GHz AMD Athlon 64 X2 Dual-Core Mobile TK-55 with NVIDIA GeForce Go 6100 (UMA), with 802.11b/g WLAN and internal fax/modem. HP part number is  GR967UA#ABA.

---

### Post by Dark_Stang on 2007-12-22
> **pndragon said:**
> I've tried to update my alsa drivers following your directions. Now, whenever I rollover the speaker icon I'm getting a tooltip that reads "Mixer cannot be found" and no sound at all. The update however went pretty smoothly.

Any help would be appreciated

--- Jim
Did you do the kernel update by any chance? Because the software was custom compiled, whenever you update the kernel or kernel headers you have to recompile alsa and restart the laptop. Alsa stopped working for me with the latest update so I had to recompile it and reinstall.

> **sergiom99 said:**
> Hey, I managed to install in a DV6646us (Kubuntu AMD64), got the Nvidia working ([http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)), wireless, and installed the ALSA as you mentioned, however headphone jacks doesnt work and speakers are not turned off when headset is plugged (installing ALSA f$@ked Nvidia BTW).
Anything else I should do?
Did you alter the last line in the file /etc/modprobe.d/alsa-base? Laptop mode isn't enabled by default. Also, you say it messed up the nvidia driver? What do you mean?

> **DonDodge said:**
> Dark Stang, since you're in the biz, do you know if a Compaq Presario F730US  crosses over to the HP models you mention?

It's a 1.8 GHz AMD Athlon 64 X2 Dual-Core Mobile TK-55 with NVIDIA GeForce Go 6100 (UMA), with 802.11b/g WLAN and internal fax/modem. HP part number is  GR967UA#ABA.
The video card is different, but it should be the same driver. I don't know what kind of wireless card is in it, but it will probably be a broadcom card. If you have one on hand post the output of lspci and we can take a look to be sure.

---

### Post by DonDodge on 2007-12-22
I think it's Broadcom wireless but I can't verify it right now. The computer is for my wife and it's under the Christmas tree for now. I want to get rid of the windozevista that came on it. I hope it's not too much of a workout to get ubuntu functioning properly. I've been reading a lot of horror stories. That's why I was wondering if this Compaq series accurately compares to any particular HP series.

---

### Post by pndragon on 2007-12-22
> Did you do the kernel update by any chance? Because the software was custom compiled, whenever you update the kernel or kernel headers you have to recompile alsa and restart the laptop. Alsa stopped working for me with the latest update so I had to recompile it and reinstall.Sound stopped working with the kernel update. I have hopes that updating ALSA will restore sound.

---

### Post by sergiom99 on 2007-12-22
> **Dark_Stang said:**
> 
Did you alter the last line in the file /etc/modprobe.d/alsa-base? Laptop mode isn't enabled by default. Also, you say it messed up the nvidia driver? What do you mean?

No, I didnt change anything.

After installing ALSA, I rebooted and got a console screen and coudlnt start X. I ran Envy -t again and then I could start KDE.
I did came across the same thing you told when installing the latest updates, had to reinstall Nvidia and ALSA.

I think I have everything running, except the Quickplay buttons.
Any idea for that?
Thanks dude, your howto saved many of us!

---

### Post by syd_loves_lucy on 2007-12-24
hey was really new to this ,, but this post really helped me fix the nvidia driver and wireless issues with 7.10..

thanks a bunch ..mine is dv6646.. nvidia 7150..

:guitar:  at last i have a working ubuntu to play with

---

### Post by sergiom99 on 2007-12-26
I've some issues with my touchpad. When I press the on\off button, the Help Center is opened. I installed the KSynaptics driver, but it was not solved. Thanks for your help!

---

### Post by Dark_Stang on 2007-12-26
> **sergiom99 said:**
> I've some issues with my touchpad. When I press the on\off button, the Help Center is opened. I installed the KSynaptics driver, but it was not solved. Thanks for your help!
I forgot about this little gem. Go System > Preferences > Keyboard Shortcuts. Scroll down to where it says "Launch help browser" click it and hit backspace. That will disable that. Or, if you want to set it for another shortcut go ahead and do that.

---

### Post by sergiom99 on 2007-12-26
> **sergiom99 said:**
> 
:confused::confused:
After installing ALSA, I rebooted and got a console screen and coudlnt start X. I ran Envy -t again and then I could start KDE.
I did came across the same thing you told when installing the latest updates, had to reinstall Nvidia and ALSA.


Men, I changed from Kubunto64 to 32bits and got the video and sound, installed ALSA, rebooted, no video so I ran envy again and once again I have no sound and the speaker is crossed out in systray.
Cannot remember what I did last time, but reinstalling ALSA only got me in the same circle and no video and so on.

Any hints??!
thanks!

---

### Post by Dark_Stang on 2007-12-27
> **sergiom99 said:**
> Men, I changed from Kubunto64 to 32bits and got the video and sound, installed ALSA, rebooted, no video so I ran envy again and once again I have no sound and the speaker is crossed out in systray.
Cannot remember what I did last time, but reinstalling ALSA only got me in the same circle and no video and so on.

Any hints??!
thanks!
I've never used envy so I can't really help you with that. I've only used Ubuntu's restricted drivers manager to install the nvidia driver because that works just fine with this card.

---

### Post by sergiom99 on 2007-12-28
> Lets get this thing going. Go to System > Administration > Restricted Drivers Manager. Check the box to enable the restricted driver for your Nvidia card, but do not enable the wifi card as it is not supported even though it says it is. 
Now Ubuntu will setup your nvidia card.
Now, lets setup your screen. The method I use may seem to overwhelm you at first, but it really is easy. Press Ctrl+alt+F1 to get to terminal. Login. Run

Dark, I started all over again by reinstalling Kubuntu from scratch. When it first starts it wont recognize Nvidia, so instead of using envy I wanted to do it your way.
**How can I enable restricted drivers w/o KDE. I only can run from console.**

Thanks for your help!!!

---

### Post by sergiom99 on 2007-12-28
I managed to do it! (I guess)
I ran dpkg-reconfigure and selected vesa, then I could start KDE and enable restricted drivers and then I moved from there on to install Nvidia as you explain.

Now I am wondering if I should install ALSA or just have the malfunctioning front speaker-jack.

And I couldnt find where to fix the touchpad button/help center issue in KDE. Any command line or file to edit?

Thanks a lot for your help Dark_stang!

---

### Post by Dark_Stang on 2007-12-28
> **sergiom99 said:**
> I managed to do it! (I guess)
I ran dpkg-reconfigure and selected vesa, then I could start KDE and enable restricted drivers and then I moved from there on to install Nvidia as you explain.

Now I am wondering if I should install ALSA or just have the malfunctioning front speaker-jack.

And I couldnt find where to fix the touchpad button/help center issue in KDE. Any command line or file to edit?

Thanks a lot for your help Dark_stang!
Great! You figured it out while I was at work, glad to see you're not afraid of playing with it. I don't use KDE and haven't played with it for... over a year now (gnome is best for me), so I'm not even close to being familiar with the layout of things. But I managed to find this, I hope it helps.
[http://www.hackosis.com/index.php/2007/10/14/linux-customize-kde-keyboard-shortcuts/](http://www.hackosis.com/index.php/2007/10/14/linux-customize-kde-keyboard-shortcuts/)

---

### Post by pndragon on 2008-01-01
> **pndragon said:**
> Sound stopped working with the kernel update. I have hopes that updating ALSA will restore sound.

After much confusion and another fresh install of kubuntu I have found the source my problem and am sharing it here. Maybe it will be of use to someone else. 

What happened was that alsamixer was muted during the first update after install. Interestingly enough, I note that this did not happen with Ubuntu --- only Kubuntu (I had to try the experiment!) To fix this I used information found here: [https://help.ubuntu.com/community/SoundTroubleshooting#head-e84f006dcbea90e29447ef97f32af397487fe7fb]("https://help.ubuntu.com/community/SoundTroubleshooting#head-e84f006dcbea90e29447ef97f32af397487fe7fb")
Afterword, I had no problems...

---

### Post by sergiom99 on 2008-01-02
glad for you.
I had a working Kubuntu, and after a couple of days I decided to go for the front speaker jack.
So I installed ALSA drivers as noted here, without errors except for the plugins that are missing some pkgconfig stuff. Rebooted and once again, the mixer has a cross on it.
I typed>
[I]s@kubuntu:~$ sudo alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
s@kubuntu:~$ aplay -l
aplay: device_list:204: no soundcards found...[/I]

using lspci -v I found this:
[I]00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at f2580000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping[/I]


any ideas please?
I broke my sound again!!

---

### Post by pndragon on 2008-01-03
> I had a working Kubuntu, and after a couple of days I decided to go for the front speaker jack.
That is where my trouble began... did you make sure that just try to
> simply open up the file /etc/modprobe.d/alsa-base and add "options snd-hda-intel model=laptop" to a new line
before updating alsa? That may have been enough.

---

### Post by sergiom99 on 2008-01-03
> this time I forgot to add that line. But i did it the previous times i installed Kubuntu.

Should I now edit the file and recompile ALSA?

Thanks foryour help.

I did that and didn't work either.

So I found this thread and did as it says and got my sound back, by removing and reinstalling ALSA.
[http://ubuntuforums.org/showthread.php?t=631774](http://ubuntuforums.org/showthread.php?t=631774)

now i still have the non-functioning front jack and the file is empty.
Any ideas to go on from now?

Thanks everyone, this is what I like about linux, everything is a lil bit harder, but you have the community helping you out.

---

### Post by sergiom99 on 2008-01-03
:lolflag: OK, guess I am a lucky noob!!!
I added the line to /etc/modprobe.d/alsa-base even though it was empy, rebooted and got sound from my headphones and not on the speakers.
(I am listening as I type)

now the only thing left to finish setting this baby up is to **disable the KDE Help Center from popping up everytime I press the synaptics touchpad on/off button**.
Looked in the places you guys told me but found nothing. I use KUBUNTU GUTSY 32.

**I also cannot use the brightness keys "Fn+F7 /F8" and the screen is killing me.**

Thanks for all the posts here!!

---

### Post by Dark_Stang on 2008-01-04
Glad to see you've got your sound configured. I don't use KDE, I really don't know what to do for the shortcut keys if it isn't covered in what I've posted. You might want to just make a general post about how to do it in the absolute beginner forum as it seems to be patrolled pretty well. A fellow KDEer should be able to help you out.

---

### Post by jgriffinpark on 2008-01-05
Hi, forgive me for my absolute lack of technical proficiency here:

I have a HP dv6000 AMD Athlon 64bit and I just installed 7.10 (32-bit version)
I've followed your instructions as to how to set up the broadcom chipset, but several restarts the light will remain red, not blue. Does this mean the drivers aren't recognized? Oh, I'm not connected by ethernet, instead I have to switch to my Vista partition every time I want to get online -_- 

Any help would be appreciated, thanks very much!

---

### Post by Dark_Stang on 2008-01-05
> **jgriffinpark said:**
> Hi, forgive me for my absolute lack of technical proficiency here:

I have a HP dv6000 AMD Athlon 64bit and I just installed 7.10 (32-bit version)
I've followed your instructions as to how to set up the broadcom chipset, but several restarts the light will remain red, not blue. Does this mean the drivers aren't recognized? Oh, I'm not connected by ethernet, instead I have to switch to my Vista partition every time I want to get online -_- 

Any help would be appreciated, thanks very much!
Do you know your exact model number by any chance? Post the output of lspci for me too, I want to see if it's the same card that I have.

You're not hooked up ethernet? Did you get ndiswrapper and the wifi files on a flash drive? cause... that's actually what I had to do with my last laptop. Total pain in the *** but worth it once I got xp off it.

---

### Post by jgriffinpark on 2008-01-05
Oh, sorry.

I'm in Vista right now, but in system information, my PC model is	HP Pavilion dv6000 (GA445UA#ABA)

and my wireless card is a Broadcom Wireless 1390 WLAN Mini PCI Card (rev 02)

I installed ndiswrapper and the driver files by copying them from my Vista partition onto the Ubuntu desktop... I'm pretty sure that should work? 
Thanks so much for helping me, but don't worry too much about it. This isn't something that is of utmost importance to me.

Thanks Again

---

### Post by gokurab on 2008-01-05
I have just installed gutsy on my HP 6500z. I tried enabling the NVIDIA drivers but the system cannot enable it. Also, when I run *sudo /etc/init.d/gdm stop*, it opens a terminal-like window from which I cannot get out. I tried many commands, but I'm stuck there. I have to dual boot between Ubuntu and vista to get to this forum. Can you please help me?

---

### Post by sergiom99 on 2008-01-06
> **gokurab said:**
> I have just installed gutsy on my HP 6500z. I tried enabling the NVIDIA drivers but the system cannot enable it. Also, when I run *sudo /etc/init.d/gdm stop*, it opens a terminal-like window from which I cannot get out. I tried many commands, but I'm stuck there. I have to dual boot between Ubuntu and vista to get to this forum. Can you please help me?

Check the whole thread. I did install it by following the instructions here and selecting generic VESA and booting into the sistem and THEN activating restricted drivers.

---

### Post by gokurab on 2008-01-07
I got the wireless working, but I cannot enable the drivers for the graphics chip. The restricted drivers manager cannot enable the nvidia drivers.

---

### Post by sergiom99 on 2008-01-07
> **gokurab said:**
> I got the wireless working, but I cannot enable the drivers for the graphics chip. The restricted drivers manager cannot enable the nvidia drivers.

I am not an expert, but in a previous install i managed to get the Nvidia drivers using ENVY ([http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)) , but it has the drawback that (i guess) you have to reinstall it if you update your kernel. But so does ALSA drivers, i think.

Maybe another one has more experience or at least is more sure of what to do.
hope this helps.

---

### Post by jgriffinpark on 2008-01-07
Okay, so...I figured out that I had the wrong driver. lspci says I have a BCM94311MCG, so I got the correct driver (bcmwl6) and installed it, after removing bcmwl5. 

When I input ndiswrapper -l
I get an "alternate driver: bcm43xx" text...

I added bcm43xx to blacklist as well, but it doesn't seem to work.
Upon restart, the light remains red.:confused:

---

### Post by pndragon on 2008-01-08
> **gokurab said:**
> I got the wireless working, but I cannot enable the drivers for the graphics chip. The restricted drivers manager cannot enable the nvidia drivers.

Do you have all of the repositories loaded?

---

### Post by rhyeal on 2008-01-09
This works perfectly on a dv6470us with the 64 bit edition of Ubuntu installed.  I was extremely overjoyed when the blue light came on for my wireless card and it showed up :)

Thanks much for ending my two day struggle to get this card working.  Do you mind if I take your driver package and instructions and post them on my own servers?  I think that the wider this gets spread, the more people will find it and (hopefully) Ubuntu will become easier to use on HP laptops.

Thanks again!

---

### Post by airbornemist6 on 2008-01-10
For quite awhile I had no time to work on this thing and I just now got time to check if I could fix the sound. I tried the guide, and it seems not to have worked. When I click on the sound I get a message telling me I have no device installed. I successfully upgraded to ALSA 1.0.15 however, ALSA does not see my soundcard.

EDIT:

Woot! I got it working. I did a clean install and then upgraded and it worked. Also I changed the procedure slighty.

```
cd alsa-driver-1.0.15
./configure –with-cards=hda-intel
make
sudo make install
```

After that, I just followed the instructions the same.

---

### Post by dope.smugglaz on 2008-01-14
I own a HP dv6502au.
I followed all the steps and got the notebook working.
I am facing a recuring issue. The wireless networking doesn't get enabled every time I boot Ubuntu. The wireless details don't even show up in the network manager at this stage. 
The problem gets solved most of the time by a reboot, but there should be a solution to this. 
Can anyone help?

[email]dope.smugglaz@gmail.com[/email]

---

### Post by airbornemist6 on 2008-01-14
Hmmm did you try completely uninstalling ndiswrapper and reinstalling it?

---

### Post by dope.smugglaz on 2008-01-15
I did that, the problem persists. That was one of the first things i tried.

[email]dope.smugglaz@gmail.com[/email]

---

### Post by Dark_Stang on 2008-01-15
Hmm... your laptop has bluetooth. Post the output of "lspci" for us. According to HP the drivers should still be the same, but I still wonder if there is some conflict going on.

---

### Post by dope.smugglaz on 2008-01-17
Thanks for taking time out for helping me in this. The problem is persistent. I have to reboot laptop to get the Wireless working.

The results are as follows:
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

Thanks again.

---

### Post by Dark_Stang on 2008-01-19
You have a different wireless card. I'm not sure why it isn't working as you'd be using broadcom's drivers for it, but maybe you should try the bcm43xx native drivers. According to the 43xx website your card has native support. Here's something to check out.
[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

Sorry for the late response, I just moved into an apartment and things are pretty crazy right now.

---

### Post by dope.smugglaz on 2008-01-20
Many thanks for that! 

How's the new place? 

On the other note, im what forums call 'n00b', I would really appreciate if u could just help me what are the steps i need to take now to get it done? Do i un-install the ndiswrapper, or just change the drivers, if so how. I would have no clue. :(
Please take you time, i can understand how it goes. :D

I can be reached at *dope.smugglaz@gmail.com*

---

### Post by Specter043 on 2008-01-21
I used your install method and it all worked on my dv6646, except for the wireless.  I followed your  instructions, but they wouldn't work, so I installed ndisgtk.  I found it in the repositories and it says it's just a GTK frontend for ndiswrapper.  I used your drivers and it worked fine, but I have to install the driver every reboot.  Any idead how to stop that.

---

### Post by Dark_Stang on 2008-01-21
The new apartment is awsome. I have to go to St. Louis to get the rest of my furniture from my parents this week. Just uninstall ndiswrapper to get rid of it, and remove it from the modules list.

The dv6646us has the N card, I wonder if it's a broadcom card... Post the output of lspci for me and we'll go from there.

---

### Post by Specter043 on 2008-01-21
Congrats on the new place.  
here's the output.


00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by sergiom99 on 2008-01-22
as you might have seen, I have the 6646us and got it working fine, just following dark_stang's directions.
One issue I have is that I connect to my wi-fi network and open firefox and then I got disconnected. I reconnect and the I keep on-line without problems.

Is there a way to make it auto-connect to my network?

---

### Post by Specter043 on 2008-01-22
Well I tried dark_stang's instructions a second time and they worked.  Must have been user error on my part. :/  Thanks for the great guide.

---

### Post by airbornemist6 on 2008-01-23
I have a 6646us, mine's working fine. Your network card is actually still the same one. The previous broadcom card was exactly the same, although I heard it might have N disabled, which would explain some things, but it works fine without N so it's working in my book.

---

### Post by Dark_Stang on 2008-01-29
Good to see that you've got it working. I'm also hearing now that wpa2 personal encryption might not be working with these cards. Can anybody else confirm this?

Also, I've setup my laptop to output stuff to my TV as an external monitor. I'll make an update whenever I get that all lined out. It isn't "plug and play" yet. You have to restart X when you plug in the tv/monitor with svideo (havne't tried vga). I'll make an update when I'm more comfortable with how this is working out as it is far from unbuggy at the moment.

---

### Post by EXCiD3 on 2008-01-29
I have been using Hardy and it worked with plug and play on my external monitor. No configuration of it like i needed to do in Gutsy or Feisty. You might check the alpha out. Its quite stable.

---

### Post by airbornemist6 on 2008-01-29
> **EXCiD3 said:**
> I have been using Hardy and it worked with plug and play on my external monitor. No configuration of it like i needed to do in Gutsy or Feisty. You might check the alpha out. Its quite stable.

Is it able to use the newest compiz fusion release?

---

### Post by EXCiD3 on 2008-01-29
It should be. It like Gutsy has Compiz built in. You should always be able to compile Compiz from source anyways.

---

### Post by airbornemist6 on 2008-01-30
I wanted to compile compiz from source on gutsy but could never find a good how to. I know linux a lot better than I used to, but I'm still not that great with it. I tried using a guide that got compiz from Git, but it messed up gutsy. When I upgraded to hardy, it stayed messed up, but I've noticed, hardy does not like the idea of fast boot. But I also haven't had time to attempt fixing anything yet.

---

### Post by EXCiD3 on 2008-01-30
I noticed that after updates that were added recently there has been a dramatic drop in speed for hardy.

As for Compiz, try using Git4CF Automator. It downloads and compiles Compiz Fusion from Git for you. It has always been my favorite way to install CF from git as the tutorials ive found are hard to understand and follow. [http://elemongw.exofire.net/projects/linux-section/git4cf-automator/](http://elemongw.exofire.net/projects/linux-section/git4cf-automator/)

---

### Post by airbornemist6 on 2008-01-30
wow... that might have just revolutionized my life. thanks!

---

### Post by EXCiD3 on 2008-01-30
haha, your welcome. glad i could help ;)

---

### Post by airbornemist6 on 2008-01-30
when you installed hardy did it break your wireless?

---

### Post by EXCiD3 on 2008-01-30
Nope, of course I have a dv9000t though running intel 3945 wireless. Which do you have?

---

### Post by airbornemist6 on 2008-01-30
I have the broadcom 43xx, I saw some threads on it, so I'll be able to fix it, I think. However, my current problem is with it overheating. I'm not used to my fan sounding like a hurricane.

---

### Post by EXCiD3 on 2008-01-30
My laptop has been overheating and shutting off too. If i prop it up it gets plenty of airflow but if im gaming or anything it overheats and turns off :( I think the heatsink has gotten too much dust on it.

---

### Post by airbornemist6 on 2008-01-31
Mine might have too, the day before I had to run across campus during a dust storm and had just finished downloading all the packages to upgrade, and I left the computer on so that the installation wouldn't stop. I have a bad feeling it might have gotten a lot of dust in it during that time.

---

### Post by duartemolha on 2008-02-06
The problem of the microphone can be resolved...
In my case i use audigy to record my songs and I was having the same problem with the microphone but then went to the preferences page and on IN/OUT setting I changed from OSS to alsa and the microphone captured perfectlly without any problems.

---

### Post by EXCiD3 on 2008-02-06
> **duartemolha said:**
> The problem of the microphone can be resolved...
In my case i use audigy to record my songs and I was having the same problem with the microphone but then went to the preferences page and on IN/OUT setting I changed from OSS to alsa and the microphone captured perfectlly without any problems.

Yeah, if at all possible make sure your apps use alsa, oss is not in major use anymore, and alsa has much better compaitibility.

---

### Post by airbornemist6 on 2008-02-07
Ah, thanks! I'll try that. Unfortunately, pretty much no matter what I do in hardy the sound sucks, so fixing the mic probably won't help much.

---

### Post by EXCiD3 on 2008-02-07
I just found out that audio in gutsy is actually being amplified if PCM is set to higher than 47%. In the volume settings turn it down to less than 47% and everything should not sound distorted anymore. I'm not sure if you are experiencing the same problems but it definitely fixed my sound quality.

---

### Post by airbornemist6 on 2008-02-07
Ah yeah, there's that too. But, I think it's different for every latop. Like on mine, it isn't amplifying until about 90%.

---

### Post by sergiom99 on 2008-02-09
Dark, I had it working fine and today I got some header updates, rebooted and now the quickplay buttons (media keys) dont work at all!!

Any ideas of where should I look to fix that??
thanks dude!

---

### Post by ahorriblemess on 2008-02-10
I just wanted to note that I used this guide for my dv6704dr and it worked great. I haven't tested the remote control yet though, otherwise, this thread helped me out a lot.

**edit**

Actually, I tried the sound card configuration, it just stops Ubuntu from recognizing that I have a sound card. I had to reinstall Ubuntu. I tried another method that included making a backup of my configuration, but recovering didn't work at all. 

Are a lot of HP laptop owners having a lot of sound problems? My sound is just a little weak and my headphones don't cut off the speakers. I'm trying to find a way to backup my system including my driver configuration, files, settings etc. and I'll try some more.

But, the remote does work!

---

### Post by airbornemist6 on 2008-02-11
> **sergiom99 said:**
> Dark, I had it working fine and today I got some header updates, rebooted and now the quickplay buttons (media keys) dont work at all!!

Any ideas of where should I look to fix that??
thanks dude!
You'll need to ask in a general help thread for that. When updates break stuff, that tends to go somewhere else, because honestly, I don't know what to tell you. But then again, I'm also not using gutsy anymore.

> **ahorriblemess said:**
> I just wanted to note that I used this guide for my dv6704dr and it worked great. I haven't tested the remote control yet though, otherwise, this thread helped me out a lot.
The remote works almost completely, by default. It's amazing.

---

### Post by sergiom99 on 2008-02-11
I know what happened: I also enabled the Xkb options in system settings to enable the Compose key to get my spanish characters, and that disabled the laptop hotkeys.
Reversed that, I got my media keys back.
gonna start a thread about this to see if someone knows.

Thanks!

---

### Post by Dark_Stang on 2008-02-11
Okay, so here is my xorg.conf file I have for my tv. Again, you have to restart X for this to work and it isn't plug and play. I'll try hoary when I have time.

```
# xorg.conf (xorg X Window System server configuration file)

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Boardname	"nv"
	Busid		"PCI:0:18:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:0:18:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-85
EndSection
Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection
```

I apologize for being gone so much. Between 35 hours at my job, 17 credit hours in college, and my spare web design job I have no time for hardly anything.

---

### Post by ahorriblemess on 2008-02-15
AH! I did it! I posted earlier saying that the procedure to get the headphone switch working just killed my sound card, well I got it working.

Laptop is HP Pavilian dv6704nr
My sound card is nVidia HDA MCP67 

I pretty much combined the instructions on this thread with the instructions on [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

 So here is what I did step-by-step if it's any help to anyone else:

First, I had to check if I had the soundcore module, so in the terminal I entered:

modinfo soundcore

It turns out I have, it, and according to the Alsa Project site, which meant I didn't have to recompille a kernal, which is great because I have no idea how to do that.

**Step 1:**

I opened the Terminal and entered: 

sudo gedit /etc/modprobe.d/alsa-base 

Then added "options snd-hda-intel model=laptop" to a new line (as instructed on this thread)

**Step 2:**

Then I went back to the terminal and entered:

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install linux-headers-`uname -r`

(as instructed on this thread)

**Step 3:**

I downloaded alsa-driver-1.0.16, then extraced it and moved it to my home folder

**Step 4:**

I opened the terminal and entered: cd /home/myuserloginname/alsa-driver-1.0.16
then entered: (as instructed on the Alsa Project website for HDA cards)

./configure --with-cards=hda-intel --with-sequencer=yes
make
sudo make install

**Step 5**

The Alsa Project instructions say to enter 

chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi 

in the terminal, but that didn't seem to do anything, it said something like "no such directory" so I just ignored it and moved on (but I'm a newb, for all I know something might have happened)

Anyway, so downloaded the alsa-lib package next, extracted into my home folder
in the terminal:

cd /home/myuserloginname/alsa-lib-1.0.16
./configure
make
sudo make install

**Step 6**

Download and installed alsa-utils package, extracted into home folder
in the terminal:

cd /home/myuserloginname/alsa-utils-1.0.16
./configure
make 
sudo make install


**Step 7**

I followed this from the Alsa Project site:

"Now insert the modules into the kernel:"
(in the terminal. I assumed I should cd back to home, so I entered:)

cd

then

modprobe snd-hda-intel (this did not work at first, i got an error message, but after "set up modprobe" [see below] I tried again and it worked)
modprobe snd-pcm-oss
modprobe snd-mixer-oss
modprobe snd-seq-oss

(hitting enter after each one of course)

**Step 8**

opened alsamixer in the terminal (by typing, alsamixer) and made sure the volume was up (I hear it gets muted? It wasn't, but I checked anyway)

**Step 9**

Alsa-Project says to 

"Set up modprobe and kmod support" 
'Note:  	
Debian GNU/Linux users need to save this information into a file in the /etc/&#8203;modutils/ directory (eg. /etc/&#8203;modutils/&#8203;alsa) and run update-modules. so, as instructed, in the terminal I entered"

sudo gedit /etc/modules/alsa

I got a blank page. On the Alsa Project site, it says to add the following to the bottom, but there was no "bottom" so I just put this on the blank page:

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-hda-intel
# module options should go here
       
# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
       
# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

**Step 10:** 

I immediately shut down and started up again... and that's it. It worked. System sounds (like the bongos at login, and pidgin sounds) seemed to initiate a little late, but it does mute the speakers.

---

### Post by sergiom99 on 2008-02-15
great you figured it out. nice instructions!

---

### Post by ahorriblemess on 2008-02-15
Well... looks I got too excited. I tried recording today and nothing is happening, all levels are up, when I try to test the input, I get this:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Resource busy or not available


***OK, I just used the microphone jack, it works fine through there, but my built in mics don't work, not a big deal really, they sound like butt anyway.

---

### Post by airbornemist6 on 2008-02-18
Oddly enough it seems I posted exactly how to do this earlier.... you don't actually need to sequencer, and that may actually be what killed your internal mics. All you need to do is make sure you do 
```
./configure --with-cards=hda-intel
make
sudo make install
```
for the first step.
Also, one tip, you can execute global commands from any location, being in your home folder is not necessary.

As far as editing your modules.conf... you SHOULD have something in there. If you don't X shouldn't even be able to start. Perhaps the reason why the code didn't work would be that you accidentally pointed gedit to a different file due to a mispelling. That's happened to me. Either way, go into nautilus and navigate to that folder and check if you have a modules.conf. Seriously, it's quite important.

---

### Post by wallgod on 2008-02-20
This has been absolutely helpful. Thank you very much for sharing this. I had failed initially while trying this but it was because Kubuntu's Adept Manager's database was locked. Now everything is fine. Thanks once again.

---

### Post by rocky909 on 2008-02-23
[ATTACH]60482[/ATTACH]

[ATTACH]60483[/ATTACH]

[ATTACH]60484[/ATTACH]I am stucked here in my laptop..(AMD turion 64x2 TL-60,nvidia GeForce 7150M)

My laptop is Amd-TL-60,(64bit)(thts why tring 64 bit ubuntu),nvidia 7150m
I also tried by pressing F6 & giving the command in boot like this--
noacpi nolacpi
then pressed enter
but again ubuntu hangs the photos i provided here..All the photos are from the same window where I was hanged for starting the ubuntu..i added top and bottom view for your better understanding.
Advance thank you for your comments and suggession.

Rocky
NY

---

### Post by sergiom99 on 2008-02-23
Is your laptop a DV6646us? same thing happened to me. video drivers are not working. read the WHOLE thread as this is explained along this thread and  we've solved this.

On the other hand, i managed to install Kubuntu64 but then removed it b/c there is no flash for 64bits OS and lost most of the web's contents.

---

### Post by rocky909 on 2008-02-23
> **sergiom99 said:**
> Is your laptop a DV6646us? same thing happened to me. video drivers are not working. read the WHOLE thread as this is explained along this thread and  we've solved this.

On the other hand, i managed to install Kubuntu64 but then removed it b/c there is no flash for 64bits OS and lost most of the web's contents.

Hi Sergiom99
My laptop is dv 6700 series(amd turion-TL 60,nvida 7150m) exact model is 6736nr..
the thread was good for 6000 to 66xx series..as it said..but if u find anything imp, let me know dude..

---

### Post by rocky909 on 2008-02-23
hello there
Can u pls check my thread regardin dv 6736nr..? I saw ur comments abt this series ? do u have any solution for me?
thank you very mush in advance
Rocky

---

### Post by ahorriblemess on 2008-02-23
> **airbornemist6 said:**
> Oddly enough it seems I posted exactly how to do this earlier.... you don't actually need to sequencer, and that may actually be what killed your internal mics. All you need to do is make sure you do 
```
./configure --with-cards=hda-intel
make
sudo make install
```
for the first step.
Also, one tip, you can execute global commands from any location, being in your home folder is not necessary.

As far as editing your modules.conf... you SHOULD have something in there. If you don't X shouldn't even be able to start. Perhaps the reason why the code didn't work would be that you accidentally pointed gedit to a different file due to a mispelling. That's happened to me. Either way, go into nautilus and navigate to that folder and check if you have a modules.conf. Seriously, it's quite important.


I have "modules" and "modules.conf" in /etc. Should I have added that to "modules" rather then creating it?

---

### Post by ahorriblemess on 2008-02-23
well... I had to do a clean install of ubuntu again (failed attempt at dual booting...) and I came back and followed my own instructions... now i have no sound! WTF?

This wonderful message popped up:

[B]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.
[/B]

Oh, and I tried to stop then start alsa-utils... when I started it, it said "no sound cards found"


UPDATE

ok, well I did apt-get install linux-backports-modules, and I got my sound back after a restart. Still no headphone/speaker mute though, after all I did.

---

### Post by airbornemist6 on 2008-02-25
ugh i had that problem the first time i tried reinstalling. I don't know what caused it, but I never got it fixed and ended up reinstalling.

---

### Post by rocky909 on 2008-02-25
I am no longer installing ubuntu in my laptop dv 6736nr.i will do it in my desktop...i had to change my laptop to get the vista again as I was not getting the drivers for my laptop even for XP...Microsoft made such a deal that I had no other way without going to vista for using my options..I tried to dual boot with vista...if u want to dual boot with vista, be very carefull with one thing....if u have a OEM disk,you are fine...you can do all the changes anytime you want..otherwise make sure you know what you are doing...I knew later that I need to shrink the Vista from disk management and free some unallocated space..later on, I need to use that for installing Ubuntu...from my little exp, I think, You need to install the Ubuntu from low graphics mode,I failed to install it from the first option..I also tried with noapci or those commands from one of the link I got from one of the thread here..But I didnt try the alternate cd option, you can try that too if low graphics mode does not work...
Cheers for Linus...
Rocky

---

### Post by sergiom99 on 2008-02-26
rocky909, if you still want to use XP and have no drivers, dont worry, same happened with my laptop. But the folks at HP forums pointed me to the right drivers for my specs and now I have a nice dual-booting Kubuntu/XP HP laptop, working like a charm. You can start searching for your model there and see if someone else already asked for XP drivers.
(I still keep the rescue CD i made when I got my laptop though, maybe vista sometime could be needed)
As of how I installed Kubuntu from alternate CD in text mode, all my adventures are posted here. I am no pro, but managed to do so. You can do it w/o problems too!

---

### Post by EXCiD3 on 2008-02-26
> **rocky909 said:**
> I am no longer installing ubuntu in my laptop dv 6736nr.i will do it in my desktop...i had to change my laptop to get the vista again as I was not getting the drivers for my laptop even for XP...Microsoft made such a deal that I had no other way without going to vista for using my options..I tried to dual boot with vista...if u want to dual boot with vista, be very carefull with one thing....if u have a OEM disk,you are fine...you can do all the changes anytime you want..otherwise make sure you know what you are doing...I knew later that I need to shrink the Vista from disk management and free some unallocated space..later on, I need to use that for installing Ubuntu...from my little exp, I think, You need to install the Ubuntu from low graphics mode,I failed to install it from the first option..I also tried with noapci or those commands from one of the link I got from one of the thread here..But I didnt try the alternate cd option, you can try that too if low graphics mode does not work...
Cheers for Linus...
Rocky

Here is the driver page for your HP 6736nr. All of these are drivers for XP. Download them and install them right after your windows install and everything should be back to normal. :)
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&lang=en&dlc=en&product=3646946](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&lang=en&dlc=en&product=3646946)

---

### Post by rocky909 on 2008-02-27
> **EXCiD3 said:**
> Here is the driver page for your HP 6736nr. All of these are drivers for XP. Download them and install them right after your windows install and everything should be back to normal. :)
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&lang=en&dlc=en&product=3646946](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&lang=en&dlc=en&product=3646946)

Thanks dude..I tried tht link b4..but I cant find the audio and video driver...I tried to go with Vista 32 bit driver..but f....cen  microsoft is not giving those drivers...I am sorry for this odd word..but i find the imperialist Microsft forcing me to keep the vista..even I tried to go by nvidia and my respective audio drivers..nvidia's  driver number and my driver model number is different..Cant locate the exact one...here also microsoft didnt give me the exact model number..and the coxent audio driver has no option from company's own site to download...
One day Linux will rule bro...one day...I am gonna install linux in my desktop soon..
cheers

---

### Post by EXCiD3 on 2008-02-27
> **rocky909 said:**
> Thanks dude..I tried tht link b4..but I cant find the audio and video driver...I tried to go with Vista 32 bit driver..but f....cen  microsoft is not giving those drivers...I am sorry for this odd word..but i find the imperialist Microsft forcing me to keep the vista..even I tried to go by nvidia and my respective audio drivers..nvidia's  driver number and my driver model number is different..Cant locate the exact one...here also microsoft didnt give me the exact model number..and the coxent audio driver has no option from company's own site to download...
One day Linux will rule bro...one day...I am gonna install linux in my desktop soon..
cheers

Huh thats odd i just noticed taht they dont have all the drivers either...have you tried using windows update to install drivers? that sometimes can get you the correct drivers for you.

---

### Post by rocky909 on 2008-02-27
> **EXCiD3 said:**
> Huh thats odd i just noticed taht they dont have all the drivers either...have you tried using windows update to install drivers? that sometimes can get you the correct drivers for you.

I cant..caz I broke the code of xp as an experiment and using it just to have a os..I dont wanna use it and get caught..ha ha ..later on,when I went to best buy ,they said they cant change it as I did modification in the vista...I had warranty for 1 month and my recovary disk to restore the system  even wasnt working..so crazy microsoft to keep me in vista any how....later I uniinstalled the xp..b4 uninstalling I made sure tht I made 2 partion ..one for vista(as it was) and the other one for vista recovary..then I went again to different store and just changed it..never mentioned about linux or xp..ha ha..I tried to be honest with them first time..but the way they behaved with me just after 3 days of my buying that laptop, I eneded up doing as they behaved with me..they said -just to reinstall the os I will be charged 129 dollar..Isnt tht crazy for a student? Honest has it rewards...i doubt now a days man..
make sure watever u do with any pc with vista or XP that you have a OEM disk..
take care man
cheers

---

### Post by EXCiD3 on 2008-02-27
Glad you got it fixed up but sorry you had to go through all that trouble :(

---

### Post by airbornemist6 on 2008-02-27
Email HP and ask them for a XP rollback disc. Lately HP has finally gotten enough pressure to bring back support for XP. If you use the cd it will downgrade to xp and install all your drivers for you.

---

### Post by rocky909 on 2008-02-27
> **EXCiD3 said:**
> Glad you got it fixed up but sorry you had to go through all that trouble :(

I love gutsy watever trouble I went through even..i will try again when I know all the loop holes of her..
thanks man..

---

### Post by HitRefresh on 2008-02-27
A few weeks ago I bought an HP DV6704nr laptop. Long story short, I don't like Vista and I've dabbled a bit with Ubuntu (Fawn) before using virtualization, and I came to like it. I came to like it so much that I now want to make it my OS.

I've heard of the woes with installing Gibbon on an HP laptop, and so I'm a bit hesitant - but determined. Is there a well-explained how-to guide for a *complete* install of Gibbon on a HP dv6704nr (TK-57) laptop ? 

There seem to be bits and pieces, but for a noob like myself it could be a bit challenging. I've done the first steps (backup data, create recov disks, and also tested a Live CD of Gibbon on it, and it worked yay!). What are my next steps for successful installation ? 

Oh, and I need to keep Vista around for my wife. I hope to convert her soon once I'm done.

---

### Post by airbornemist6 on 2008-02-28
This guide should work for you. If you don't mess with bleeding-edge, barely functioning software like I do, you'll be fine. If you do, then you'd be in a mess regardless of your OS.

---

### Post by rocky909 on 2008-02-28
> **airbornemist6 said:**
> This guide should work for you. If you don't mess with bleeding-edge, barely functioning software like I do, you'll be fine. If you do, then you'd be in a mess regardless of your OS.

wat guide you are talking about? Can you pls let me know if you have any detail guide for it?

---

### Post by Taino on 2008-02-28
> **rocky909 said:**
> wat guide you are talking about? Can you pls let me know if you have any detail guide for it?

The first post of this thread is the guide he refers to -[link]("http://ubuntuforums.org/showthread.php?t=575750")- to the beginning. :)

---

### Post by airbornemist6 on 2008-03-03
Thank you.

---

### Post by HitRefresh on 2008-03-14
I'm trying out the instructions provided by Dark_Stang to intall Gutsy on a HP DV6704nr. 

I'm using the  x86 live cd, boot in safe mode, and then try to change my resolution as the instructions says, so that the entire install screen can appear. But I cannot change the resolution at all, it gives me an error. I'm not able to install directly from the live CD because it says "Cannot find screen or graphics card" and I'm not advanced enough to know how to install using the alt CD, yet. 

What do I do ? Thanks for any help.


-Bhavesh

---

### Post by mohamedafattah on 2008-03-15
Invoking this thread to life again :)

First of all, thanks to the detailed instructions that helped me when I followed it blindly on my laptop. The reason is simply having a dv6636nr (What an exact match).

The laptop works at its best with this configuration steps mentioned in the beginning of this thread. I just did not do the ALSA step, because I am comfortable with the sound card as is (not a big deal anyway), and I usually refrain from manipulating kernel modules because they have strange results when updating the kernel itself from the repositories.

Anyway, only one thing annoyed me and was always there at the back of my head: power saving. C'mon guys, I can not believe that Windows Vista lives 3 hrs on battery with full processor usage and a zillion hard disk invocation per second, given that Ubuntu with no real hard disk access or very hard processing lived under 2 hrs. That was *clearly* because hardware producers do their best writing the windows drivers, while most of them don't give any consideration to Linux users. I guess the propriety device drivers did not make any control of power, and began investigating this in details. Most of the processor wakeups was due to the USB controllers and the NVidia graphics card. None of the packages succeeded to force the dynamic processor frequency. Not any single useful search result told me how to deal with the graphics card, and the wireless seemed irrelevant (not much difference as I noticed). But, I was decided that Linux should win this war (at least on my laptop). And here is my shot:

As a KDE little fan, I had Kubuntu 8.04 alpha 6 KDE 3.5 (you will be amazed how stable it is after the updates, IMHO it is better than Kubuntu 7.04 release version). Installed Kubuntu 8.04, under 800X600 resolution. I decided not to install the binary nvidia driver and work on the VESA graphics card (I dual boot it with Ubuntu 7.10 to have a distro that takes care of full performance). Then K -> System Settings -> Monitor and Display -> Administrator Mode -> Hardware tab -> Choose the LCD 1024X768 Generic monitor for Monitor #1. Then, Apply, And choose 1024X768 in the Size, Orientation tab.

Tried to install the wifi in the same way mentioned by the beginning of this thread by ndiswrapper, but I did that after trying the binary driver, so It didn't work, but I will update after retrying. It didn't require any more configuration, the headphones works out of the box. Still, two things are annoying me, and I will update as soon as I solve them:
1) The resolution is 1024 X 768 not 1280 X 800 and the aspect ratio is not correct whenever trying the VESA driver.
2) The wifi still didn't work (I will work it out soon, but did anybody try madwifi on a similar card?).

I was happy that the processor frequency is dynamically changed, and that the NVidia was not invoked. Instead of resolving the previous issues I went to test the battery life. And **YES**. It lived 3.5 hrs on Kubuntu with the screen turned on and showing the blue desktop background. Yes, I finally did it. But for me it is not an end, I still have to fix the two issues, and there is a newer target: 4.5 hrs.

Anyway, I appreciate any suggestion.

---

### Post by Dark_Stang on 2008-03-15
> **HitRefresh said:**
> I'm trying out the instructions provided by Dark_Stang to intall Gutsy on a HP DV6704nr. 

I'm using the  x86 live cd, boot in safe mode, and then try to change my resolution as the instructions says, so that the entire install screen can appear. But I cannot change the resolution at all, it gives me an error. I'm not able to install directly from the live CD because it says "Cannot find screen or graphics card" and I'm not advanced enough to know how to install using the alt CD, yet. 

What do I do ? Thanks for any help.
-Bhavesh
You're attempting to start in safe graphics mode with a 7.10 or newer disk, right? The 6704nr has the same gpu as the 6636nr so I wouldn't think there would be any problems. You might have to try to install with the screen set at 800x600... which will suck but if you can't change your resolution not much else can be done except for an alternate install.

> **mohamedafattah said:**
> Invoking this thread to life again :)

First of all, thanks to the detailed instructions that helped me when I followed it blindly on my laptop. The reason is simply having a dv6636nr (What an exact match).
Yeah... I work at best buy so that's how I ended up with it. I have to assume that's where you got yours since they're the only retailer I've seen carrying the nr's.

> **mohamedafattah said:**
> The laptop works at its best with this configuration steps mentioned in the beginning of this thread. I just did not do the ALSA step, because I am comfortable with the sound card as is (not a big deal anyway), and I usually refrain from manipulating kernel modules because they have strange results when updating the kernel itself from the repositories.
You'd have to re-compile alsa every time you get a new kernel. I made a little script to do it for me. ;)

> **mohamedafattah said:**
> Anyway, only one thing annoyed me and was always there at the back of my head: power saving. C'mon guys, I can not believe that Windows Vista lives 3 hrs on battery with full processor usage and a zillion hard disk invocation per second, given that Ubuntu with no real hard disk access or very hard processing lived under 2 hrs. That was *clearly* because hardware producers do their best writing the windows drivers, while most of them don't give any consideration to Linux users. I guess the propriety device drivers did not make any control of power, and began investigating this in details. Most of the processor wakeups was due to the USB controllers and the NVidia graphics card. None of the packages succeeded to force the dynamic processor frequency. Not any single useful search result told me how to deal with the graphics card, and the wireless seemed irrelevant (not much difference as I noticed). But, I was decided that Linux should win this war (at least on my laptop). And here is my shot:
I can get 3.5 to 4 hours of battery life on constant use with my laptop. Actually, I'm on it now and it's pretty much been unplugged the whole time I've been home (almost 3 hours) and it still has 46% charge left. Granted I'm using it off and on at the moment, but still that's pretty good.

> **mohamedafattah said:**
> As a KDE little fan, I had Kubuntu 8.04 alpha 6 KDE 3.5 (you will be amazed how stable it is after the updates, IMHO it is better than Kubuntu 7.04 release version). Installed Kubuntu 8.04, under 800X600 resolution. I decided not to install the binary nvidia driver and work on the VESA graphics card (I dual boot it with Ubuntu 7.10 to have a distro that takes care of full performance). Then K -> System Settings -> Monitor and Display -> Administrator Mode -> Hardware tab -> Choose the LCD 1024X768 Generic monitor for Monitor #1. Then, Apply, And choose 1024X768 in the Size, Orientation tab.

Tried to install the wifi in the same way mentioned by the beginning of this thread by ndiswrapper, but I did that after trying the binary driver, so It didn't work, but I will update after retrying. It didn't require any more configuration, the headphones works out of the box. Still, two things are annoying me, and I will update as soon as I solve them:
1) The resolution is 1024 X 768 not 1280 X 800 and the aspect ratio is not correct whenever trying the VESA driver.
2) The wifi still didn't work (I will work it out soon, but did anybody try madwifi on a similar card?).
Yeah, just use the nvidia driver you get through the restricted drivers manager. The vesa drivers don't have 3d acceleration. To reconfigure your settings use the method described under the graphics card section rather than using Ubuntu's built in tool.

And as for the wireless you have to use ndiswrapper with this card. Using the guide and drivers I have posted under the wireless card section should work for you. Be sure to blacklist the kernel driver.

> **mohamedafattah said:**
> I was happy that the processor frequency is dynamically changed, and that the NVidia was not invoked. Instead of resolving the previous issues I went to test the battery life. And **YES**. It lived 3.5 hrs on Kubuntu with the screen turned on and showing the blue desktop background. Yes, I finally did it. But for me it is not an end, I still have to fix the two issues, and there is a newer target: 4.5 hrs.

Anyway, I appreciate any suggestion.
My best suggestion, play with it. Start learning how to compile your own software and kernels. Speaking of compiling a kernel, that's something I really need to do for this laptop... The generic kernel is fine but, a custom kernel would give it a nice boost.

Edit: Oh, and for kernel compilation here is a good guide to use for Ubuntu.
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by Bigrjsuto on 2008-03-29
Good tutorial.

I have a HP dv2516nr laptop
I tried a couple months ago trying to get my wireless to work in 7.10 with no luck.

But I decided to give it another go.

Your tutorial got my wireless working the first time I tried it!

Thanks a lot.

---

### Post by sergiom99 on 2008-04-09
Dark, I want to use aircrack but it wont work with ndiswrapper.
do you know if I can easily and securely use another driver for our wireless chipset??
Thanks!

---

### Post by Dark_Stang on 2008-04-09
Good luck finding a driver that works for these cards, I don't know of any. Broadcom seems to keep their code and specs locked up tight. Unfortunately aircrack and airsnort does not work with ndiswrapper. Here is a quote taken from ndiswrapper's webstite.
>  No! NDIS doesn&#8217;t support Master/Repeater/Monitor modes. The only modes supported are Ad-Hoc and Managed. Note that some drivers may support features that are not in NDIS e.g., showing signal noise and possibly Master mode, but they are proprietary and no documentation available for them, so such features won&#8217;t be supported by ndiswrapper.

Do let me know if you find anything though.

---

### Post by smallville_bz on 2008-04-10
your wireless card driver instruction is working on my dv9068eu too, thanks!!!

---

### Post by smallville_bz on 2008-04-13
when i start up ubuntu i don't have the nvidia logo, but on restricted drivers it's green (in use), i have geforce 8400gs grafic card

---

### Post by sergiom99 on 2008-04-13
> **Dark_Stang said:**
> 
Do let me know if you find anything though.

I will try the backtrack2 Live CD and tell u how it goes.

---

### Post by Dark_Stang on 2008-04-13
> **smallville_bz said:**
> when i start up ubuntu i don't have the nvidia logo, but on restricted drivers it's green (in use), i have geforce 8400gs grafic card

The nvidia logo should appear on startup... Run glxgears. As long as it's running smoothly you're using the nvida drivers and not the vesa drivers. If it isn't running smoothly reconfigure you're xserver again, making sure you select the nvidia driver and not the "nv" driver.

---

### Post by smallville_bz on 2008-04-14
i installed ubuntu 5 days ago for the first time, so it´s new for me, and i don´t know exactly how to reconifgure this, but i can say that compiz fusion is working great, if that has to do something with the nvidia card

---

### Post by smallville_bz on 2008-04-14
i want to ask you if i can use this configuration for my geforce 8400gs, or is this just for 7150
thanks


Configuring the Nvidia 7150 Card and Screen
Lets get this thing going. Go to System > Administration > Restricted Drivers Manager. Check the box to enable the restricted driver for your Nvidia card, but do not enable the wifi card as it is not supported even though it says it is. Now Ubuntu will setup your nvidia card.
Now, lets setup your screen. The method I use may seem to overwhelm you at first, but it really is easy. Press Ctrl+alt+F1 to get to terminal. Login. Run
Code:

sudo /etc/init.d/gdm stop

It will ask for your password. We just shut down the x-server so we can reconfigure it. Now run
Code:

sudo dpkg-reconfigure xserver-xorg

1.Select no to auto detect our setup.
2.If the nvidia driver isn't already selected, select it with the arrow keys, hit tab and then enter to continue.
3.Continue with default options until you are asked if it should use a kernel frame buffer. Select no and continue.
4.Go ahead and click yes to have it detect the keyboard.
5.For the mouse use the PS/2 and to emulate the 3 button mouse.
6.Click yes to writing default files section to configuration file.
7.Click no for attempting monitor detection.
8.Go ahead and give your monitor a name.
9.Now we're at the important part. Scroll down the left side with the arrow keys until you see “1280x800”. Hit the space bar to check that box, a little asterisk will appear. Now uncheck all the other boxes, hit tab and enter to continue.
10.Select medium for setting the monitor up, we're not entirely dumb.
11.Scroll down to “1280x960 @ 60 Hz”, hit tab and enter. (i know it isn't 100% right, but it works just fine)
12.Select yes for writing monitor ranges.
13.For desired color I chose 24. If you feel like you're getting slow performance you can come back and choose 16 later, however 24 feels great to me.

Now that we're all done enter
Code:

sudo /etc/init.d/gdm start

Your login screen will come right back up. Did you like that nvidia logo? Sexy, isn't it?

---

### Post by Dark_Stang on 2008-04-14
> **smallville_bz said:**
> i want to ask you if i can use this configuration for my geforce 8400gs, or is this just for 7150
thanks


Configuring the Nvidia 7150 Card and Screen
Lets get this thing going. Go to System > Administration > Restricted Drivers Manager. Check the box to enable the restricted driver for your Nvidia card, but do not enable the wifi card as it is not supported even though it says it is. Now Ubuntu will setup your nvidia card.
Now, lets setup your screen. The method I use may seem to overwhelm you at first, but it really is easy. Press Ctrl+alt+F1 to get to terminal. Login. Run
Code:

sudo /etc/init.d/gdm stop

It will ask for your password. We just shut down the x-server so we can reconfigure it. Now run
Code:

sudo dpkg-reconfigure xserver-xorg

1.Select no to auto detect our setup.
2.If the nvidia driver isn't already selected, select it with the arrow keys, hit tab and then enter to continue.
3.Continue with default options until you are asked if it should use a kernel frame buffer. Select no and continue.
4.Go ahead and click yes to have it detect the keyboard.
5.For the mouse use the PS/2 and to emulate the 3 button mouse.
6.Click yes to writing default files section to configuration file.
7.Click no for attempting monitor detection.
8.Go ahead and give your monitor a name.
9.Now we're at the important part. Scroll down the left side with the arrow keys until you see “1280x800”. Hit the space bar to check that box, a little asterisk will appear. Now uncheck all the other boxes, hit tab and enter to continue.
10.Select medium for setting the monitor up, we're not entirely dumb.
11.Scroll down to “1280x960 @ 60 Hz”, hit tab and enter. (i know it isn't 100% right, but it works just fine)
12.Select yes for writing monitor ranges.
13.For desired color I chose 24. If you feel like you're getting slow performance you can come back and choose 16 later, however 24 feels great to me.

Now that we're all done enter
Code:

sudo /etc/init.d/gdm start

Your login screen will come right back up. Did you like that nvidia logo? Sexy, isn't it?
That will work for any nvidia card that the nvidia glx drivers support. If compiz works it's probably working though.

---

### Post by rgaino on 2008-04-25
It worked perfectly on my HP Pavillion dv6000. I tried a lot of other things until I made a fresh install of Hardy Heron and applied your tutorial. I am posting this using the wireless connection. Thanks a LOT.

---

### Post by saveferris7872 on 2008-04-27
the wireless card setup isnt working for me. i downloaded the file but when i try and run sudo ndiswrapper -i bcmwl5.inf, it says 

couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by airbornemist6 on 2008-04-28
Are you in the wifi driver directory? you have to be sitting in it, or it won't work. I believe you also have to run as root... don't remember for sure.

---

### Post by saveferris7872 on 2008-04-28
do you mean the files i downloaded have to be in the wireless driver directory? and if so, how do i get them there.

sorry but i am completely new to all of this and thanks for the help

---

### Post by mohamedafattah on 2008-05-01
8.04 has been released. I am so happy of the stability of this release. :)
The following applies to Ubuntu 8.04 amd64, Kubuntu 8.04 amd64, and Kubuntu/KDE4 8.04 amd64, unless stated otherwise:

Firstly, replying my post here: After I have benchmarked a little bit, I found that it is not the nVidia graphics card that absorbs the power. Most of the power consumption is due to two components: the processor, and the screen. The nVidia graphics card drew a lot of battery probably because I used to run Ubuntu with too much effects from compiz-fusion :) all the time.

The processor consumption is low if the CPU frequency scaling is set to dynamic (In which the case is that the processor levels at 800 MHz at 99.9 % of your work time, unless there is a process that just consumes too much processing, and then suspect a broken process and wait for updates). This dynamic scaling is enabled by default in any 8.04 I stated above. In KDE 4, you may install kde-guidance-powermanager from Adept in order to track the CPU frequency and policy easily. Command line backends are:
cpufreq-info
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
kde-guidance-powermanager doesn't work by default on KDE4, its command is guidance-power-manager

The screen: I am not really sure of that, but I believe that darker backgrounds draw less power than brighter ones.

Nvidia graphics card: Since 8.04, once you choose the graphics card from the restricted drivers manager, you will find the screen adjusted at 1280X800, and all of the other resolutions will be available. It just works out of the box.

Sound card: Yay, All of the 8.04s listed above are the only Linux distros nowadays that is operating my sound card out of the box without glitches. This is just amazing how the hardware support is so leading in Ubuntu.

Hotkeys work out of the box except for KDE4, you have to configure them yourself.

Since anything but the wifi works out of the box, I will borrow Dark_Stang's wifi installation steps (from the very first post in this thread):

Wireless Card Setup
Download and extract the files I have [here]("http://www.darkstang.com/wifi.tar.bz2").
If that link doesn't work, go to this one [here]("http://www.gotode.com/wifi.tar.bz2"). - (one of my client's sites, temporary fix)
Now go to System > Administration > Synaptic Package Manager (Adept if you are KDE).
While we're here we're going to unlock all our repositories. Go Settings > Repositories (Adept -> Manage repositories if you are KDE). Check all the boxes on the first page except for the CD, and hit close. A window will pop up telling you that you need to reload your packages. Go ahead and close that window, and click reload at the top.
Once that is finished click in the main window and start typing “ndiswrapper”. It will automatically scroll down and find it. Click the box next to “ndiswrapper-utils” and click “Mark for Installation”. Now go ahead and click Apply at the top.
After that is installed open a terminal window. Applications > Accessories > Terminal. Navigate to where you saved the drivers I had you download and extract. Now run the following

```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m

```

**At least in dv6636nr, this step is not needed, bcm43xx is blacklisted automatically in my laptop, you may want to look up in the following file yourself:**

Our wireless driver is now installed but not working just yet. It's currently being blocked by another driver that is trying to run, so we need to block this other driver. Run

```
sudo gedit /etc/modprobe.d/blacklist
```

A text editor will pop up with the blacklist. Go to the end, start a new line, and enter “blacklist bcm43xx” without quotes. Save the file.


**Now, this step is needed though is not yet working in 8.04:**
Now for some reason ndiswrapper doesn't load automatically when it starts up. So now let's add it to the modules list.

```
sudo gedit /etc/modules
```

Make a new line and add "ndiswrapper".

Well, Dark_Stang is fixing the 8.04 wifi behavior in a different way that automatically operates the wifi card on startup. Me, waiting for updates is using the same shell script but after start up. Both of them are the same and I think it really doesn't matter, but this is the way I tried it (just for the record):

Make a new file, wifiFix.sh:
```

#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

```
Then:
chmod a+x wifiFix.sh

This file, when run, you will find your wireless led glowing blue, i.e.: functional. So, make a desktop launcher to this file, make it to be run by a different user "root", and put the launcher in your desktop.

One comment: This thread is archived and is no longer available in the forums search, that is why I suggest to really archive this thread, copy the important stuff needed for 8.04 in a new clean thread, and put a huge link to the 8.04 configurations in the first post of this thread (as this thread is a google-first-hit).

One issue that I could not resolve in the early alpha6 release (I was using the 32 bit) is some programs using sound. For instance, Skype. It just did not read anything from the microphone. Now as I use 64-bit, I am searching for an alternative anyway :), but if anybody found out some solution just post it, because somebody may need that feature.

---

### Post by mohamedafattah on 2008-05-01
> **saveferris7872 said:**
> the wireless card setup isnt working for me. i downloaded the file but when i try and run sudo ndiswrapper -i bcmwl5.inf, it says 

couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.


Download that file: [http://www.darkstang.com/wifi.tar.bz2](http://www.darkstang.com/wifi.tar.bz2)
Extract it:

Open a terminal, navigate to the extracted directory.

Once you have that:
```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
```

Did that run for you? If not, put all output messages here.

---

### Post by mohamedafattah on 2008-05-01
> **saveferris7872 said:**
> do you mean the files i downloaded have to be in the wireless driver directory? and if so, how do i get them there.

sorry but i am completely new to all of this and thanks for the help

Oh, I missed those couple of posts. Here is how it goes:

Download the files, I assume by using Firefox, they are now on your desktop. Right Click -> Extract here

Open a terminal:

cd Desktop
cd wifi

-- cd (change directory) is the command to get into a directory in the command line.
then

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m

---

### Post by mohamedafattah on 2008-05-01
> **mohamedafattah said:**
> Now as I use 64-bit, I am searching for an alternative anyway :), but if anybody found out some solution just post it, because somebody may need that feature.

Oh, I didn't search about how to solve it. It has a clear solution from [http://forum.skype.com/lofiversion/index.php/t96497.html](http://forum.skype.com/lofiversion/index.php/t96497.html) :
sudo dpkg -i --force-architecture packagename_i386.deb

The point is that it works now, but without sensing any microphone input.

---

### Post by lutzik on 2008-05-14
When i first got my hp dv2610, this was the only tutorial that made everything work on my ubuntu 7.10, and when i upgrated to 8.04 it worked perfectly. but then i tried to set up a manual configuration for a wireless access since it wasn't broadcasts, and everything went to hell. Even after i switched back i can't select wireless network, my only option now is wired netword. I tried uninstalling the driver by ndiswrapper -r bcmwl5 and reverting all the settings back, and installing everything from scratch, but it didn't work. Can anyone help me or suggest what to do?

---

### Post by EXCiD3 on 2008-05-14
> **lutzik said:**
> When i first got my hp dv2610, this was the only tutorial that made everything work on my ubuntu 7.10, and when i upgrated to 8.04 it worked perfectly. but then i tried to set up a manual configuration for a wireless access since it wasn't broadcasts, and everything went to hell. Even after i switched back i can't select wireless network, my only option now is wired netword. I tried uninstalling the driver by ndiswrapper -r bcmwl5 and reverting all the settings back, and installing everything from scratch, but it didn't work. Can anyone help me or suggest what to do?

You should try the tutorial here: [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

---

### Post by Dark_Stang on 2008-05-14
lutzik

Make sure ndiswrapper is using bcmwl5. Then check your network configuration and make sure roaming mode is enabled. Give it a reboot. Then right click the network manager icon and make sure Enable Wireless is checked. If this doesn't work and you have your hard drive partitioned so /home is separated from /, I'd suggest a fresh install. It's hard for me to diagnose this problem without the machine sitting in front of me.

---

### Post by sergiom99 on 2008-06-05
Hey darkstang,
I want to hear some feedback from you about this laptop killing HDD bug in linux:
[http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

My pavilion has a TOSHIBA MK1637GSX HDD and the output from diag tool:
```
ue Jun  3 21:13:23 ART 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       16607
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Lifetime Min/Max 13/51)
sergio@kubuntu:~$ date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
Tue Jun  3 22:24:28 ART 2008
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       16725
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Lifetime Min/Max 13/51)
```
Almost 100-110 mounts /hour.

```
My system:
Kubuntu HH
2.6.24-17-generic i686 kernel
KDE 3.5.9
Qt 3.3.8b
```

Do you think we should fix something? Thanks for your thoughts.

---

### Post by EXCiD3 on 2008-06-05
Ouch!!! 100 load cycles an hour!! Just run this to turn down the power management settings on the affected drive(s):

```
sudo hdparm -B 254 /dev/sda
```

This turns the power management settings down so that drive will not gain load cycles except on boot up and shutdown/suspend/hibernate. Thats the least amount you can get but also maximizes your drive lifetime. Your laptop may be slightly hotter but its better than having your drives go out on you.

---

### Post by sergiom99 on 2008-06-05
thanks EXCiD3,
I will try that.
Does that persist for every session? Or do I have to do it everytime I log in?

---

### Post by EXCiD3 on 2008-06-05
Yes it should. You can query the setting through one of the parameters in hdparm...i think its -I /dev/sda to get the current value.

---

### Post by Dark_Stang on 2008-06-05
Hm... 83 per hour. Do we know for sure that this is killing the drives? I'm half tempted to use my laptop as an experiment... There's a 200g 7200rpm drive at work that screams my name every time I walk past it...

---

### Post by EXCiD3 on 2008-06-05
Yes its the power management causing the problems. I've done monitoring of the load cycles on my laptop. Had it for little over a year and ive already had 127,000 load cycles. Friend of mine with the same laptop has 400,000 load cycles because he uses linux a lot more before i got started using it.

---

### Post by Dark_Stang on 2008-06-05
Hm... well, I set mine to 254, it was at 127 before. I'll check on the temp every now and then but, I've probably only heard 20 clicks out of it the entire time I've owned it.

---

### Post by EXCiD3 on 2008-06-05
255 isnt good to set it on as it turns management completely off but with 254 you should see only a load cycle every time you do something with shutdown/startup. It takes it very easy on the drive because it does not actually turn off the drive. When you have power management on it turns off the drive after amounts of inactivity and this keeps it cooler but increases load cycles quite a bit.

---

### Post by Fasian on 2008-06-12
Hi, ive tried to use ndis wrapper on my bcmwl5.inf but i get the error message cant find bcmwl5.inf at ndiswrapper line 219. why is this happening. Btw is the broadcom 4312 rev 2 chipset supported?

---

### Post by Dark_Stang on 2008-06-12
> **Fasian said:**
> Hi, ive tried to use ndis wrapper on my bcmwl5.inf but i get the error message cant find bcmwl5.inf at ndiswrapper line 219. why is this happening. Btw is the broadcom 4312 rev 2 chipset supported?
When you're running the ndiswrapper commands you need to run them in the same directory the drivers that you extracted are in. So if you saved them to, let's say, /home/Fasian/wifiDrivers you will need to use the commands "cd" to navigate to that.
cd /home/Fasian/wifiDrivers

Then run your ndiswrapper stuff.


Edit: 21,000 views. I'd like to think that 1/50 views on this thread helped somebody. That's 400 woots for the open source community.

---

### Post by bolha on 2008-07-06
Thanks for that Dark, my wireless is working now.

I'm running Ubuntu 8.04 64 bits on a HP dv6000 laptop. The Ubuntu installer configured everything but wireless. I have a Broadcom 4321. 

Following Dark's tips in the first post in this thread, I just downloaded [http://www.darkstang.com/wifi.tar.bz2](http://www.darkstang.com/wifi.tar.bz2)  unpacked it, installed ndisgtk via synaptic, in the ndisgtk screen I selected the bcmwl5.inf and configured my wireless connection.

[],
Bolha.

---

