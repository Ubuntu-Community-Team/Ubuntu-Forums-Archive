---
title: "Ubuntu on Acer Aspire 5315-052G12Mi"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by sanone on 2007-11-12
[COLOR="Red"][SIZE=3]**Last Update:** 03-03-2008[/SIZE]
- Updated Wifi (ndiswrapper) section. We now have a new driver which fixes bugs and enables the Wifi LEDS!!! (Marlo_nl keeps me busy ;))

**21-02-2008**
- Added gstreamer-properties section. (thanks ryphix)
- Fixed some commands that gave 'permission denied errors' and changed ndiswrapper packages. (thanks guykes and Marlo_nl)
- Added reference to ibiltari post about madwifi_ng patch instead of ndiswrapper.[/COLOR]


Here I'll share my experiences with installing and configuring this neat little notebook. If you happen to own this notebook as well or have information to make this guide a bit better please let me know...

Specs: 
&#8226; Celeron-M 530 1.73GHz 
&#8226; 2048MB (2x 1024MB) 
&#8226; 120GB 
&#8226; DVD+/-RW DL 
&#8226; Intel GMA X3100 onboard. Max.358MB shared memory 
&#8226; USB 2.0/Modem/LAN/WLAN 802.11bg 
&#8226; 15.4" WXGA TFT (1280x800) 
&#8226; Li-Ionen-Akku (6 Cells) 
&#8226; 2.80kg


[SIZE=5]**INSTALLATION**[/SIZE]

The Ubuntu 7.10 Gutsy Gibbon LiveCD booted up without problems altho no wireless network was found. When I started the installer gParted (the partition manager) only gave me the option to install to the entire disk or manual installation.

Since I wanted to leave Vista on the disk (and 50GB is enough for now) I had to chose manual. I removed the third partition (sda3) which was the empty D:\ partition in Vista. 

No further issues.


[SIZE=5]**CONFIGURATION**[/SIZE]

After installation I logged into ubuntu and most of the stuff worked out of the box. There were only a few issues with the items below.

1) Compiz
2) Wifi
3) Sound
4) Webcam
5) Gstreamer-properties

Below you'll find solutions I found for these problems. If someone has better solutions / workarounds / knowledge feel free to comment as I will update this page.


**1) Compiz**
For such a powerfull 3D card with opensource drivers one would expect compiz to be working. According to [this compiz fusion wiki page]("http://wiki.compiz-fusion.org/Hardware/Blacklist") it is blacklisted.

Please note that this card is blacklisted for a reason. The drivers still don't support Xv which means that Totem (the default movie player) crashes when you play a movie and so does some other stuff (i.e. the visualization on rhythmbox). There is a pretty good work around for this. See section 5) Gstreamer-properties for more info.

If you want compiz fusion added the option "SKIP_CHECKS=yes" to the  ~/.config/compiz/compiz-manager file.
```
echo "SKIP_CHECKS=yes" > ~/.config/compiz/compiz-manager
```

**2) Wifi**
[COLOR="Red"][Update][/COLOR] ibiltari has posted a possible solution to use the madwifi_ng driver (true linux driver) instead of the ndiswrapper (windows driver). Check it [here]("http://ubuntuforums.org/showpost.php?p=4246472&postcount=17"). I haven't tested it myself but if you do please reply with the results!!
[COLOR="Red"][Update2][/COLOR] [This post]("http://ubuntuforums.org/showpost.php?p=4279390&postcount=303") suggests a newer XP driver which enables the wifi indicator LED and fix some issues.

Ubuntu detects the wifi card on this notebook as an Atheros AR5006EG. This is **NOT** correct and kept me busy for quite some time. When I booted back to Vista to dubble check on this I noticed that it was the Atheros AR500**[COLOR="Red"]7[/COLOR]**EG. This card doesn't work with any of the restricted drivers nor with [madwifi]("http://www.madwifi.org"). 

I used [this]("http://ubuntuforums.org/showthread.php?t=554531") thread, [this]("http://ivangarcia.org/blog/?p=13") website and this [post]("http://ubuntuforums.org/showpost.php?p=4279390&postcount=303") as my guidance for installation and basically came down to this.

&#8226; Install ndiswrapper (use windows network drivers in linux)
&#8226; Download windows drivers and unpack ( I used these: [http://www.atheros.cz/download/drivers/ar5008/xp32-6.0.3.85.zip]("http://www.atheros.cz/download/drivers/ar5008/xp32-6.0.3.85.zip") from [http://www.atheros.cz/]("http://www.atheros.cz/"))
&#8226; Install the driver with ndiswrapper
&#8226; Blacklist the device so Ubuntu doesn't try to load drivers for it itself.
&#8226; Save the ndiswrapper module configuration.

```
cd ~
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://www.atheros.cz/download/drivers/ar5008/xp32-6.0.3.85.zip
unzip xp32-6.0.3.85.zip
cd xp32-6.0.3.85
sudo ndiswrapper -i net5416.inf
gksudo gedit /etc/modprobe.d/blacklist

```

The last command starts gedit as superuser so we have the right to modify this system configurationfile. Add the following at the end of the file.
> #Atheros AR5007EG (Ubuntu detects it as AR5006EG so we use ndiswrapper...)"
blacklist ath_pci

Save the file and close gedit.

Now all we need to do is save the ndiswrapper config.
```
sudo ndiswrapper -ma && sudo ndiswrapper -mi && sudo ndiswrapper -m
cd ~
```


**3) Sound**
There are a lot of threads about Acer and sound on this forum. However most of them are old and require a lot of work (recompilation of also for instance). Luckily I found [this]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") official ubuntu wiki page. It shows this notebook and two simple instructions work perfectly. 

&#8226; installed linux-backports-modules-generic
&#8226; added options line to /etc/modprobe.d/alsa-base: options snd-hda-intel model=acer

```
sudo apt-get install linux-backports-modules-generic
gksudo gedit /etc/modprobe.d/alsa-base
```

The last command starts gedit as superuser so we have the right to modify this system configurationfile. Add the following at the end of the file.
> options snd-hda-intel model=acer

Save the file and close gedit.


**4) Webcam**
[COLOR="Red"][Update][/COLOR] It is possible to use the webcam pretty straightforward. The section below is kept for historical reasons and perhaps someone might find the tools provided there useful. See section 5) Gstreamer-properties how to set this up the 'best' way. 

Wow.. during the writing of this article I did got some videofeed from my webcam.. but this doesn't mean that it's working in applications yet.. Both Ekiga and Camorama fail to connect to the webcam. I believe this is because it's supported by the video 4 Linux 2 drivers which aren't supported by those apps yet. 

The command I used to get some video footage:
```
gst-launch v4l2src queue-size=2 !  ffmpegcolorspace ! ximagesink
```I found another tool which shows webcam footage and can make screenshots / movies and allows you to alter stuff like gamma / sharpness etc. It's called luvcview and it's not in the repositories. The code below downloads, builds and starts luvcview.

```
cd ~
wget http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz
tar zxvf luvcview-20070512.tar.gz
cd luvcview-20070512
echo "INSTALLING THE REQUIRED PACKAGES TO BUILD THIS SOFTWARE"
sudo apt-get install libsdl1.2-dev build-essential
make
./luvcview -w -f yuv -i 30
```*Update:* Ekiga can see this camera if you configure it to use the v4l2 driver but it seems that it can't send the data over.. 

If someone has some recommendations about good webcam software (capture sound/video) or a good MSN/ICQ client which supports this webcam please let me know


**5) Gstreamer-properties**
Gstreamer-properties is a configuration tool to setup devices for gstreamer (most gnome applications use this). It allows us configure gstreamer so we can playback video while compiz-fusion is enabled and allows gstreamer applications to use the webcam. The usage is pretty straightforward.

1) Start gstreamer-properties from the console by typing: *gstreamer-properties*
2) Goto the Video tab and select as *Default Output* the plugin *X Window System (No Xv)*. This should enable all gnome applications to play video and visualizations while compiz-fusion is enabled.
3) Select at the *Default Input* section the plugin *Video for Linux 2 (v4l2)*. This allows programs as cheese to use the webcam. 

Please note while compiz is enabled and the *Default Output* plugin is set as in step 2 cheese (very nice webcam software) performs poorly. This is because they heavily depend on Xv for performance.


[SIZE=5]**CONCLUSION**[/SIZE]
After these steps this notebook rocks your boxers like any other ubuntu machine. There are still some issues but it's for 95% usable.

The issues are mostly with the X3100 driver since it has some 3D related crashes, rendering bugs (try the 3d chess screensaver to see some ugly z buffering issues) and Xv. But since this is an open source driver I suspect these will be fixed soon,

The issues with the microphone are harder but I have good faith. 

I hope some people find this information useful.

Cheers,
Sander


PS.
Thanks for all the replies with tips and bug fixes. Please continue to report errors / typos etc!!

---

### Post by JoeTarrant on 2007-11-18
Hi.

This post was very helpful. I wanted to get sound working. I installed the Linux modules and added the options line to alsa-base as suggested and rebooted. A whole new PC started up...   Soundjuicer was playing a CD earlier and even recognised the tracknames.  

For info - I've tried two old (10 years old) SVGA screens on this laptop and neither works. I set the Acer to 640x480 and they still don't work. Newer screens might work, of course, but at least one of these old screens was working in the last week. It's also impossible to screw the cable from an external screen into the laptop. So if you have an old connector, it just hangs there unsecured, which isn't the best for external screens. 

I can also vouch that Fn+F7 turns off the trackpad. Gave me a bad 5 minutes before I worked that out! I connected a USB mouse to the laptop which worked immediately and checked around. So if anybody was wondering about USB.... It really works. 

One problem I have is that the laptop whines a bit. I've begun noticing that over the last few days. Apart from that and a generally plasticky feeling (this isn't Apple quality hardware), it was a very good deal (£299 at Comet, in England). 

I'm very new to Ubuntu. It seems light on the hardware - I have two Firefox windows running and the OS is using only 270MB of the gigabyte of ram. I have really fallen in love with Gnome. Extremely simple interface. Brilliant. 

Thanks for the help with the sound. I'd never have worked that out. I'll keep an eye here for news of screen updates. If I'm in the mood later, I might try printing on it. 

Joe

---

### Post by sanone on 2007-11-18
I'm glad this helped you out.. I haven't tested external monitors myself but if I do I'll update this page. 

I also created [a LaptopTestingTeam wiki page]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5315") which informs you about all diffrent parts tested on this notebook. 

San

---

### Post by ryphix on 2007-11-19
A note on compiz:

I was able to get visualizations in rhythmbox by typing

gstreamer-properties

into the terminal and under the video tab, selecting

X Window System (No Xv)      for the plugin option.

I'm running on an Aspire 5315-2153.  It's basically the same hardware.

---

### Post by sanone on 2007-11-19
> **ryphix said:**
> A note on compiz:

I was able to get visualizations in rhythmbox by typing

gstreamer-properties

into the terminal and under the video tab, selecting

X Window System (No Xv)      for the plugin option.

I'm running on an Aspire 5315-2153.  It's basically the same hardware.

Thanks a lot ryphix!! I dind't know about this configuration tool. 

This tool also allows me to change the default driver used by gstreamer for the webcam. Now cheese (webcam software) works. It's slow but according to [their FAQ]("http://live.gnome.org/Cheese/FAQ#head-fb51597a3f48dfc21f2d288bf07cf78ce00b2802") this is because of selecting "X Window System (No Xv)" in the gstreamer-properties configuration tool. 

Well for now this tradeoff is good enough for me.. at least every video application using gstreamer (including watching movies in totem) now seems to work!

Cheers,
San

---

### Post by JoeTarrant on 2007-11-24
I've been having a problem with screen brightness. Fn+Left/Right arrow turns the screen brightness down/up. Pressing the key combination shows a little slider. Sometimes this works fine. Sometimes the slider shows nothing. It's there but has nothing to slide, as it were. Sometimes the slider shows full brightness and can't be altered. I feel there's a pattern to this, but haven't been using the machine enough to spot it. Anybody else having this and if so, what did you do to fix it? I don't like screens that are too bright and the default setting on the Acer is too bright for me. So it's one I'm keen to fix. 

Thanks,

Joe

PS: just remembered. The Euro key (for the currency), next to the arrow keys, doesn't seem to work either. However, pressing AltGr+4 (as on Windows) works fine.

---

### Post by sanone on 2007-11-26
The brightness worked out of the box here... On all occasions so I'm curious what makes it not work on your machine.

And the eurosign indeed doesn't work.. neither does the dollar sign (the one near the arrows) btw. As far as I can tell they aren't supported by the selected 'keyboard layout' I use and therefore X11 doesn't detect any keypresses etc. 

Perhaps some other 'keyboard layout' exists that has theses buttons on them... but then there is the issue that gnome doesn't have an option to bind a random key to the eurosign. There are only three predefined options which are all based on existing keys.

Even though I live in The Netherlands I do never use this sign so I'm not really looking further into this. If someone finds a fix for this please let us know in here!

Cheers,
San

---

### Post by apez on 2007-11-28
I'm going to buy this same model, and I would want to know if it's WLAN works fine with linux (not only Ubuntu/Kubuntu), for example, would it work with OpenSUSE or PCLOS?

---

### Post by sanone on 2007-11-30
> **apez said:**
> I'm going to buy this same model, and I would want to know if it's WLAN works fine with linux (not only Ubuntu/Kubuntu), for example, would it work with OpenSUSE or PCLOS?

Like I explained in my starters post I got WLAN / Wifi working with ndiswrapper. So the use of windows network drivers in Linux. Ndiswrapper is availible on almost every linux distribution so OpenSUSE / PCLOS should not have any problem with it. 

I don't know about any specific tricks on other distros but there are certainly people on their forums / irc / mailinglists who can describe the procedure...

---

### Post by mjwhitfield on 2007-12-02
Your guide has saved my a*s. I'd never have figured all this out by myself.  I'm getting this laptop of Christmas and I was super worried that I'd have a hell of a time getting it all working.  Come to England one day and I'll buy you a beer - you've made my Christmas!

---

### Post by sanone on 2007-12-04
Hahaha ... I spent quite some time in figuring things out and writing it all down. But responses like yours make it worth the trouble :)

Cheers and a happy xmas!
[IMG]http://forum.gamer.nl/images/smilies/bier.gif[/IMG]

---

### Post by persisto on 2007-12-04
Excellent Sanone!

It took me a second or tow to realise what the hell I was looking at when the webcam output showed. LOL (I entered the webcam related command s an after thought on for the Sound problem)

Now, would you not also have a solution for the modem which does not work. (Im working on a 5710Z of a friend who only has dial up. The WIFI, sound and Webcam solution you propose worked perfectly.)

Thanks 
Pete

---

### Post by sanone on 2007-12-05
:lolflag:

Well I haven't looked at the modem even for a second..  I have wired or wireless broadband at all the places I visit so no need for that now.. but I encourage you to look at this yourself!

I'm rather busy atm with my Master Thesis for the uni and can't spend as much time hacking ubuntu as I would like. So don't expect me to figure this out in the next couple of weeks... perhaps that I'll look into this later but it's hard to test a modem without even having a telephone line :D

Cheers,
San

---

### Post by persisto on 2007-12-05
OK thanks for that. Should you ever come accros hints as to how to resolve the modem prob, I would much appriciate a post. Alvast bedankt

Pete

---

### Post by gatoz on 2007-12-10
i tried using the sound codes but i got an permission denied any help with that.
I am using an Acer 5315-2153 so its basically the same

---

### Post by sanone on 2007-12-12
> **gatoz said:**
> i tried using the sound codes but i got an permission denied any help with that.
I am using an Acer 5315-2153 so its basically the same

Your comment is kinda vague and I have not really a clue on what to say...
Well the problem with the sound was in my case not codec related. But is was the way Ubuntu identified the hardware. 

If you want some help make sure you give us some more info.. what did you try? On what command did you get the "permission denied"? Etc. etc.

San.

---

### Post by ibiltari on 2008-01-31
Hi, if someone is interested i have the madwifi_ng driver runing in a 5315_051g12Mi with the atheros wifi card reported as "Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)"
I used madwifi-ng-r2756-20071018 with this [patch]("http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw") 

Also there is a small patch to the kernel to make processor stepping work on my model, if interested look for a patch to  p4-clockmod to make it recognise newer celeron 530 found on this computer.

Hope it helps.
Ion

---

### Post by guykes on 2008-02-16
> **sanone said:**
> Your comment is kinda vague and I have not really a clue on what to say...
Well the problem with the sound was in my case not codec related. But is was the way Ubuntu identified the hardware. 

If you want some help make sure you give us some more info.. what did you try? On what command did you get the "permission denied"? Etc. etc.

San.



Hi

first of all san, thanks for all your tips!

Perhaps I found a solution for the problem gatoz is facing.

I also got 'permission denied' after this command:
sudo echo "" >> /etc/modprobe.d/alsa-base

I suppose this means that acces was denied to the 'alsa-base' file. 

Entering this command in terminal got me into the alsa base file 
 sudo gedit /etc/modprobe.d/alsa-base

(I found this in another forumthread)

Then I just entered this line at the end:
options snd-hda-intel model=acer

Then I saved and rebooted and my sound works!

I guess the problem just was getting access to the alsa file (im not an expert at all, so just guessing)

good luck

guykes

---

### Post by Marlo_nl on 2008-02-16
Hi,

I tried to enable Wifi using the code provided by Sanone on an Acer Aspire 5315-052G12Mi with Ubuntu 7.10 (Gutsy Gibbon) installed.

Unfortunately I've been unsuccessful with the 10 lines of code provided in the original thread.

I already got stuck with the first line: sudo apt-get install ndiswrapper.

m@laptop:~/wireless$ sudo apt-get install ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper

I took my quite some time to figure out that the first line of Sanone's procedure will not work if Ubuntu was installed without (wired) internet connection.

apt makes use of the file sources.list in directory /etc/apt. If the file sources.list contains the following text "#Line commented out by installer because it failed to verify:" this is probably because Ubuntu was installed without (or bad) wired internet connection.

You'll first need to edit the sources.list file (undo the commented out operations by the installer) using sudo gedit sources.list.

However, after this modification I still was not able to successfully apply the first line of the procedure provided by Sanone:  sudo apt-get install ndiswrapper

I don't understand why, but by checking available packages using the Synaptic Package Manager I found that there is no package available with the name "ndiswrapper". 
Maybe it was in November 2007, but no longer in February 2008.

So I decided to use the Synaptic Package Manager to install ndiswrapper-common and ndiswrapper-utils-1.9.

This allowed me to execute the following line of Sanone's procedure:
sudo ndiswrapper -i net5211.inf

But at the next line I got stuck again:
sudo echo "" >> /etc/modprobe.d/blacklist

Ubuntu does not allow me to do this. So I decided to do a sudo gedit /etc/modprobe.d/backlist to add the lines of text to the backlist file.

Finally did a sudo ndiswrapper -ma && sudo ndiswrapper -mi and a reboot of the system.

But still no wireless access. I don't know how I can see the effects of what I've did in the Ubuntu environment. If I do System->Administration->Network I don't see any Wireless Connection, if I do an iwconfig I get eth0 no wireless extensions.

So I'm puzzled why with the same hardware and the same OS version results are so different.

I don't know how to continue. 
Did anyone encounter similar problems trying to enable Wifi using Sanone's procedure?


Regards,

Marlo

---

### Post by tvcrabo on 2008-02-16
Hi,

i had some dificulties in getting my wifi card working. Fortunatly now it does (after 4 hours of tries and rechearch).
At the moment the sound is still not working and i dont give a damm about the webcam.
using the line in the console for the sound it says i dont have access to do so...

any other way to do so?

---

### Post by sanone on 2008-02-21
I updated this thread with the comments posted here. It should work now with the guide in the first post.

Thanks for all the replies. If you notice some errors / typos or have additional information please post it here.


Have phun!
San

---

### Post by Marlo_nl on 2008-02-24
Hi,

Let me start by saying thanks to San for keeping the thread up to date.

I managed to get sound working following the procedure on the first page of this thread.
Just one additional note to the procedure: for sound to work a system restart is needed.

I also managed to get Wifi operational on my machine and hence I can now confirm that Sanone's Wifi procedure also works for me.

I now have some better understanding why the procedure did not work for me initially. 
I want to share my learnings here as it might be useful to others.

Before I came across this thread I followed instructions on some other threads trying to get my Wifi operational. In doing so, at some moment in time, I removed the file ndiswrapper.ko from my filesystem. Without this file you can not get Wifi to work.

So for me the question was how to reinstall ndiswrapper.ko?
By searching the internet I learned that I was not the only one who ended up removing the file ndiswrapper.ko. 
But I did not find much information on how to reinstall this file.

By using the Synaptic Package Manager I found that the ndiswrapper.ko file is part of the package "linux-ubuntu-modules-2.6.22-1 2.6.22-14-37".
By checking the properties of this package (tab Installed Files) I could find the entry:
/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

So i decided to mark this package for reinstallation within the Synaptic Package Manager.
Note: for some reason Synaptic Package Manager only allows me to reinstall this package when having a working (wired) internet connection. I could not select "Mark for Reinstallation" with only the Ubuntu CD-ROM (and no internet connection).

After restoring ndiswrapper.ko my Wifi finally became "alive".

To conclude: if you cannot get your Wife operational by following the instructions on the first page of this thread check that you have the file ndiswrapper.ko available. For Ubuntu 7.10 this file should be in the directory: /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/


Regards, Marlo

---

### Post by Marlo_nl on 2008-02-29
Hi San,

I have two short questions related to Wifi behavior on your Acer machine.

1) Is your Wife LED indicator operational?

My LED indicator does not work. 

I found that the net5211.inf file I had in use was an older version than the one you refer to in your procedure.
Hence, I did an uninstall of this older version (ndiswrapper -r net5211), downloaded the files from the Acer ftp site and reinstalled the newer version.
But unfortunately this did not help to get my Wifi LED indicator to work.


2) Does your Wifi connection always initialize correctly at startup?

My Wifi connection did not always initialize correctly (no IP address, no internet connection).
In another thread I found someone's suggestion to do a sudo ndiswrapper -m.
This to add "alias wlan0 ndiswrapper" to the /etc/modprobe.d/ndiswrapper file.
My experience (up to now) is that adding this alias did help to "guarantee" proper Wifi initialization at startup.
Maybe it is a good idea to include the "sudo ndiswrapper -m" to your procedure as well.


Regards, Marlo

---

### Post by sanone on 2008-02-29
> **Marlo_nl said:**
> Hi San,

I have two short questions related to Wifi behavior on your Acer machine.

1) Is your Wife LED indicator operational?

I've never seen any Wifi LED blinking. I'm not even sure there is such a LED ;)

> **Marlo_nl said:**
> 2) Does your Wifi connection always initialize correctly at startup?
....
Maybe it is a good idea to include the "sudo ndiswrapper -m" to your procedure as well.

Unfortunately I can not say it **always** connects to my wifi router... but in most cases it does. If there is no connection I can simply select the ESSID from the list (in the Network Manager Applet). 
In my tutorial I used the command "sudo ndiswrapper -ma". This is, according to the help, also a way to save the configuration. 

```
sander@sander-acer:~$ ndiswrapper --help
....
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
```

In a reaction to your earlier post:
Note that it is never smart to remove any .ko file. Especially if you do not know exactly what you're doing! These are kernel modules and removing those can lead to serious issues. 
I understand that issues with Wifi make you try anything anyone suggests but solutions like this are very tricky!

Succes,
Sander

---

### Post by Marlo_nl on 2008-03-01
Hi Sander,

Thanks a lot for your reply. Some more feedback from me.

> **sanone said:**
> I've never seen any Wifi LED blinking. I'm not even sure there is such a LED ;)


Yes, for sure the Acer Aspire 5315-052G12Mi is equipped with a Wifi LED. It is located just beneath the Wireless On/Off button. 
How can I be so sure?
I've configured my Acer such that I can multiboot into Windows Vista, WindowsXP and Ubuntu 7.10. The Wifi Led is operational in both Windows Vista and in WindowsXP, not in Ubuntu. Or better said, it **was** not operational in Ubuntu.

By doing some further investigations on the internet I found two hints on how to enable the Wifi LED.

[LIST=1]
[*][http://luke.no-ip.org/x60tablet/]("http://luke.no-ip.org/x60tablet/")
Hint: To get the wireless power LED working, edit /etc/ndiswrapper/net5211/168C:1014.5.conf and replace the line "gpioPinFunc1|0" with "gpioPinFunc1|1"

Result: I tried this hint on my Acer Aspire5315 (no X60tablet) but found that it does not activate the Wifi LED. 


[*][http://ubuntuforums.org/showthread.php?t=512828&page=31]("http://ubuntuforums.org/showthread.php?t=512828&page=31")
Hint in post #303 by Mackum: Driver net5211 is not good at all!!! It is 5416 driver.
Download windows driver version xp32-6.0.3.85.zip
From here lets' say. [http://www.atheros.cz/download.php?a...R5008&system=1](http://www.atheros.cz/download.php?a...R5008&system=1)
Then it will work perfectly even with the working LED. With normal MAC address and etc.
PS:TO EVERYBODY: DO NOT USE net5211 DRIVER ON AR5007EG CARDS, IT DOESN'T WORK AS IT SHOULD!!!

Result: Using driver net5416 does the trick, it activates the Wifi LED on my Acer Aspire 5315-052G12Mi.
This is really nice: having a visual Wifi LED indicator telling me the status of the Wife On/Off button.
There might be one disadvantage: reduced battery life ;)
[/LIST]

Maybe you can try hint 2 on your machine as well. In case it also activates your Wifi LED it might be good idea to update your procedure and suggest the use of net5416.inf instead of net5211.inf.

 
> **sanone said:**
> 
Unfortunately I can not say it **always** connects to my wifi router... but in most cases it does. If there is no connection I can simply select the ESSID from the list (in the Network Manager Applet). 
In my tutorial I used the command "sudo ndiswrapper -ma". This is, according to the help, also a way to save the configuration. 

```
sander@sander-acer:~$ ndiswrapper --help
....
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
```


I'm not sure ndiswrapper -m and ndiswrapper -ma are doing exactly the same.
I checked the contents of the /etc/modprobe.d/ndiswrapper file before and after executing ndiswrapper -m.
I found that ndiswrapper -m modified the /etc/modprobe.d/ndiswrapper file. The following line was added: "alias wlan0 ndiswrapper".

Can you please check the contents of your /etc/modprobe.d/ndiswrapper file?
If you don't see the line "alias wlan0 ndiswrapper" in your file then executing ndiswrapper -m will add it.

My experience is still that adding this alias "helps to guarantee" proper Wifi initialization at startup.
And therefore I still think it is a good idea to include the "sudo ndiswrapper -m" to your procedure as well.

> **sanone said:**
> 
In a reaction to your earlier post:
Note that it is never smart to remove any .ko file. Especially if you do not know exactly what you're doing! These are kernel modules and removing those can lead to serious issues. 
I understand that issues with Wifi make you try anything anyone suggests but solutions like this are very tricky!


I fully agree (now) that it isn't smart to remove .ko files. 
Just part of the learning curve.
Internet is a great source of information. On the other hand, there are a lot of suggestions and hints that tell you to do "things" without explaining why or without warning for the consequences of certain actions.
This is what makes it difficult to distinguish "the good and the bad".

In my opinion your procedure is "the good" and I hope my contribution is useful for others as well.

Regards, Marlo

---

### Post by sanone on 2008-03-03
Marlo_nl: Nice find mate!!

I tested this new driver and wow.. I can see the light ;)
Also I checked the alias in the modprobe section. I had it there but perhaps I did the -m option after all. After the installation of the updated drivers the alias was gone. I used the -m option and now it's back. 

So I updated the first post with the new driver and added the -m option as well.

Thank you very much for your feedback!!
San

---

### Post by dmunc on 2008-03-05
I just installed the latest wireless driver over the previous one, and I can confirm that it is working like a charm! The orange light is on steady when the wireless radio is on, blinks intermittently when data is being transmitted, and is off entirely when the wireless radio is deactivated.

Sincere thanks to all of those in this forum who have put so much effort into this project. Your work is appreciated!

Cheers,
Dan

---

### Post by Flymo on 2008-03-06
Thanks, San!  :guitar:

Some very helpful stuff has been posted  here - hope this helps if you have a go using an external monitor or TV.

We needed TV-Out to view EPGs on the TV screen - a main reason for buying an Acer 4315 (almost identical hardware - no camera, less RAM, small screen & CD not DVD-RW), and all it seemingly takes to enable it is:  
[B]
Have the S-Video output connected by cable to the TV when you boot Ubuntu..... [/B]

 That's it - but it took me *such* a long time to discover. :confused:

Hope that helps & all the best,  Ben

---

### Post by sanone on 2008-03-07
> **Flymo said:**
> Thanks, San!  :guitar:

Some very helpful stuff has been posted  here - hope this helps if you have a go using an external monitor or TV.

We needed TV-Out to view EPGs on the TV screen - a main reason for buying an Acer 4315 (almost identical hardware - no camera, less RAM, small screen & CD not DVD-RW), and all it seemingly takes to enable it is:  
[B]
Have the S-Video output connected by cable to the TV when you boot Ubuntu..... [/B]

 That's it - but it took me *such* a long time to discover. :confused:

Hope that helps & all the best,  Ben

Hi Ben,

Hav you tried xrandr? 

Sometimes I use xrandr to connect to an external VGA monitor using this command:
```
xrandr --output VGA
```

You can query what devices are connected using:
```
xrandr -q
```

For me this gives the following output (nothing connected right now)
```
sander@sander-acer:~/School/MasterThesis/Code/bin/debug/linux$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2048 x 2048
VGA disconnected (normal left inverted right)
LVDS connected 1280x800+0+0 (normal left inverted right) 331mm x 207mm
   1280x800       59.9*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)
```

You notice the TV disconnected at the bottom. Perhaps this changes when you add the device. At least that is the idea behind xrandr.. plug and play.

Try the following when you have you tv cable connected:
```
xrandr --output TV
```

More info can be found here: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

Goodluck,
San

PS. Your post is the first that counted as a 'Thanks' on this forum.. Thank you for that ;)

---

### Post by netroy on 2008-03-07
i tried what you said about wifi configuration on my kubuntu laptop (acer 5315), no error message, but nothing happen. 
would you please tell me, how can i get wifi connection on kubuntu?
thank.

---

### Post by sanone on 2008-03-08
> **netroy said:**
> i tried what you said about wifi configuration on my kubuntu laptop (acer 5315), no error message, but nothing happen. 
would you please tell me, how can i get wifi connection on kubuntu?
thank.

Netroy,

Well this howto is the way I and many other people got wifi working. When you reply by saying that it does not work without any additional information we can't do much. 

Can you check the list below:
1) Is ndiswapper is installed?
2) Is the windows driver installed?
```
ndiswrapper -l
```
3) Wireless configuration
```
iwconfig
```
If you get a wlan0 device out there do a scan for availible wireless networks:
```
iwlist wlan0 scan
```

Goodluck,
San

---

### Post by Marlo_nl on 2008-03-09
Hi Sander,

Thanks for checking the net5416 Wifi driver.

Good to know that it also works on your machine. 
This raises confidence level a lot; we're on the right track with Ubuntu 7.10 Wifi on the Acer Aspire 5315.

What about your Wifi initialization at startup, did you encounter any connection problems since issuing ndiswrapper -m?

I didn't encounter any connection problems up to now. 


Regards, Marlo

---

### Post by scottro on 2008-03-09
My own experience, on an Acer4720z, with the same wireless card, is that while the 5416 and ndiswrapper will get my LED working, it's unreliable.  That is, sometimes it will connect normally and at other times it won't. 

I've had a great deal more success with the MadWifi driver.  It seems quite consistant.  Unfortunately, it doesn't work with 64 bit, and no one seems to know when, or if, such support will be coming.

---

### Post by sanone on 2008-03-10
> **scottro said:**
> My own experience, on an Acer4720z, with the same wireless card, is that while the 5416 and ndiswrapper will get my LED working, it's unreliable.  That is, sometimes it will connect normally and at other times it won't. 

I've had a great deal more success with the MadWifi driver.  It seems quite consistant.  Unfortunately, it doesn't work with 64 bit, and no one seems to know when, or if, such support will be coming.

As Ubuntu does not even detect the device correctly I assume this should be done by hand. I linked to a patch for the madwifi drivers which should work. But I do not prefer to compile my drivers by hand. Is there a repo with the lastest and perhaps a howto?

[QUOTE=Marlo_nl]What about your Wifi initialization at startup, did you encounter any connection problems since issuing ndiswrapper -m?[/QUOTE]

This is still not reliable. I sometimes still have to configure the device by hand.

Cheers,
San

---

### Post by MrGreen on 2008-03-12
I have just installed 8.04 on my laptop... and using ndiswrapper got wifi working, sound was an issue in 7.10 but I have got sound and internal microphone now so more than happy :-)

MrG

---

### Post by mjwhitfield on 2008-03-12
Not wanting to go too OT, however the laptop fits perfectly in the ubuntu bag that you can get from the store :)

Back on topic, is the sound issue fixed with 8.04 yet?  I'm happy enough using ndiswrapper, but the sound thing bugs me.

---

### Post by sanone on 2008-03-13
> **mjwhitfield said:**
> Not wanting to go too OT, however the laptop fits perfectly in the ubuntu bag that you can get from the store :)
72 Euro for a bag? I'll continue carrying it in my normal rucksack!

> **mjwhitfield said:**
> Back on topic, is the sound issue fixed with 8.04 yet?  I'm happy enough using ndiswrapper, but the sound thing bugs me.
I'm not aware of any issues with the sound on 8.04. I'm still using 7.10 and the provided solution works fine. Have you tried those suggestions? What is exactly the problem and what did you try? 
And did you notice that MrGreen could use sound and microphone with 8.10 ( [http://ubuntuforums.org/showpost.php?p=4499756&postcount=35](http://ubuntuforums.org/showpost.php?p=4499756&postcount=35) )

San.

---

### Post by mjwhitfield on 2008-03-13
Yeah I noticed he said that, which is why I was wondering if it was fixed completely.

The solution provided in the OP worked for me, it just seems rather unusual that such a common sound card has issues.

---

### Post by sanone on 2008-03-16
> **mjwhitfield said:**
> Yeah I noticed he said that, which is why I was wondering if it was fixed completely.

The solution provided in the OP worked for me, it just seems rather unusual that such a common sound card has issues.

Perhaps posting a bug report on launchpad will fix this for the final version of 8.10

---

### Post by Malekish on 2008-03-17
Does the 5315-052G12Mi have the same heat problems that the 5315-2153?

If you search the forums you'll see we have a problem with the fan not working after suspend or hibernate, also problems with the CPU temp not updating properly.

Running windows it has no heat problem at all but while in Ubuntu we all have problems with it shutting down from heat.

Almost the same laptop, slight downgrade.

---

### Post by mjwhitfield on 2008-03-18
I've never used suspend or hibernate, so I can't comment.

---

### Post by Malekish on 2008-03-18
How's about your CPU temp, can you run a monitor and see if it changes?  On mine the CPU temp doesn't update which is why the fan never kicks in to cool it off, causing it to eventually shutdown from heat.

---

### Post by mjwhitfield on 2008-03-18
As far as I've read, the problem with overheating only occurs after a suspend or a hibernate because the fan doesn't kick back in.  The reason, so far as I can tell, is that the fan isn't controlled by the BIOS, but by a win32 exe, which doesn't work under WINE.

if the laptop is popular enough, someone will make a fix.

---

### Post by dca on 2008-03-18
Don't know if this has been brought up but has anyone used the 'acer_acpi' package to see if it resolves any of these issues?
 
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

---

### Post by sanone on 2008-03-22
I tried hibernate once and it was no success so I never used it ever since. 

@ dca
I never used that but the site states that the Ubuntu packages are not maintained anymore, are beta and may contain bugs. Well to be honest I don't like stuff like that at a kernel level in my system. If someone tried it please let me know how it went. I'm quite curious!

Perhaps we should post this on launchpad to inform the devs of the existence of this software.

Thanks for sharing.

San

---

### Post by alucardromero on 2008-03-24
I followed San's instructions for Kubuntu 7.10 and it worked without a hitch.  However, I've upgraded to Kubuntu 8.04 Beta (KDE3.5.9) and the guide doesn't seem to work with the wireless technique.  I haven't tried sound yet but I suppose I could work on that.

Any clue what the difference is?  Here's what's going on so far...

1. Newest XP drivers are loaded and are reported to be present
2. Blacklisted said incompatible driver and disabled it in Hardware Drivers Manager
3. Restarted, and LED light is working and makes a subtle blink now and then.
4. Installed wicd for WPA1/2 support, attempted connection to network, and it's successful.
**5. wicd reports that it's connected, yet I can't access the network or the internet.  At times wicd will switch ESSID between the real ID and "None". Percentage of range stays the same.**

I feel I've made the smallest error, but I check back twice, and I can't find the error.

EDIT: It seems like the sound works out of the box which is really cool.
wicd doesn't want to load at all.

Meh, I've given up and reverted back 7.10.  Everything was fine back then. :P  But yeah, 8.04 is just gonna have to wait until things get cleared.

---

### Post by sanone on 2008-03-27
It's a shame that it did not work out well for you alucardromero. I haven't updated yet myself (working on my master thesis and don't want to risk braking things during an upgrade) but when I do I let you know how it went.

Are you sure it's not related to wicd?

Cheers,
Sander

---

### Post by DemonBob on 2008-03-29
> **ibiltari said:**
> Hi, if someone is interested i have the madwifi_ng driver runing in a 5315_051g12Mi with the atheros wifi card reported as "Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)"
I used madwifi-ng-r2756-20071018 with this [patch]("http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw") 

Also there is a small patch to the kernel to make processor stepping work on my model, if interested look for a patch to  p4-clockmod to make it recognise newer celeron 530 found on this computer.

Hope it helps.
Ion

This driver works good. Been using it since the first day it was released. They also have a 2.6.24 release for Hardy.

---

### Post by sanone on 2008-03-31
> **DemonBob said:**
> This driver works good. Been using it since the first day it was released. They also have a 2.6.24 release for Hardy.

Hi DemonBob,

I was wondering if the patch ibiltari referred to was already merged in the madwifi project. 
I'm also hoping that you could describe (in a few steps) how you get the driver working on ubuntu?

Thanks,
Sander

---

### Post by peterleder on 2008-03-31
thanks for this nice thread.

i do have an acer2920z that inhabits an ar5007eg as well. i made it working with the madwifi modules i downloaded from madwifi.org easily.

```
make 
make install
reboot
```

```
apt-get update 
apt-get install network-manager network-manager-kde
reboot
```

and everything worked easily. the sound worked correctly after i edited as you said before. I do know that madwifi is able to work my wifi device. I do not want to use ndis - never got the picture :-\

why cant i use the same madwifi driver for ubuntu? is this really a HAL problem?
thanks guys! will try to use ndis after i found this thread after all... :(

---

### Post by Giuliano on 2008-03-31
I'm planning to install the new version of Ubuntu when its released, there will be total support to Aspire 5315? Atm i'm using Windows XP and dont have any problem, but i want to use Ubuntu once again. Can i start making backups? x)

Thanks

Ps.: Sry about my english

---

### Post by sanone on 2008-04-01
> **Giuliano said:**
> I'm planning to install the new version of Ubuntu when its released, there will be total support to Aspire 5315? Atm i'm using Windows XP and dont have any problem, but i want to use Ubuntu once again. Can i start making backups? x)

Thanks

Ps.: Sry about my english

If you don't play many games it is time to start making backups ;)
The biggest issue I have with this notebook is related to 3d. The intel drivers simply suck at opengl. So don't think that you can play games like urban terror with a lot of FPS or even without a crash :(

Compiz, sound, wifi all work well with my guide (or tips from other users in this thread).

So the choice is yours.. 
San

---

### Post by Giuliano on 2008-04-01
I dont use it for games, then i will just start my backups. Can't wait for the new version.
One last question, the fan works fine now? I never use hibernate, so this wont be a problem i guess.

---

### Post by sanone on 2008-04-01
> **Giuliano said:**
> I dont use it for games, then i will just start my backups. Can't wait for the new version.
One last question, the fan works fine now? I never use hibernate, so this wont be a problem i guess.

I never had any problem with the fan to start with. I leave my notebook on for 12 hours to compute some stuff but never had any issue with that. Nor does it feel warm. If you have the same version I doubt you will have any.

---

### Post by Simon Bridge on 2008-04-03
> **Marlo_nl said:**
> Hi,
To conclude: if you cannot get your **Wife** operational by following the instructions on the first page of this threadYou could try dinner and flowers - admitting you are "wrong" has been known to help. :)

See man pages, apologise(1) and woman(2224) - though the second one is out of date and incomplete.

--- now I've got that out of my system ---------------

I've come to this thread with an aspire 4315 which has Ubuntu *pre-installed* by Acer. (Offer seems to be Australasia only.) So most of the issues here don't apply. I just wish Acer had chosen different hardware for their linux experiment.

Inside the box, they list four "disabled" function. The empower (e) button, the wifi button, the onboard modem and the microphone.

They say all these are disabled due to "limitations of linux".

Wifi works out of the box - but it doesn't seem to speak WPA2. Acer should have mentioned that suspend, hibernate and restart don't work either. (restart?) And the boot process is hobbled by poor settings.

I submit for discussion that;
1. Acers windows only "empowering software" not running in linux is a limitation with Acer, not linux.
2. Linux not needing "empowering" in this way is not a *limitation* in linux
3. The inclusion of a connexant chipset (modem) in an intel soundcard was an acer decision - this is a combination which requires additional "empowering" to work in windows, and that linuxant do not support. This limitation exists in windows too, but is more of a limitation in linuxant support. (Lets all notify them.)
4. Nobody knows what is wrong with the mic. Likely culprit is the inclusion of conflicting non-intel subsytems in an intel board. Possibly representing budget limitations imposed by acer more than any limitation in linux.

For future releases, acer need to treat their customers with a bit more (i.e. any) respect than this. Including full explanations of missing functions would be useful, as would actually *disclosing them* outside the box, where customers can see them before parting with money.

OTOH: FOSS has some political clout (here) in NZ, Once the national LUG and NZOSS became aware of the problems, the local acer reps have been taking steps to adress these problems. While I doubt they are 100% solveable for this hardware, the next linux box should be better appointed. We can only hope.

Whatever - it seems acer are serious about pre-installing linux.

I understand that the 5315 has been similarly offered to Canadians?

---

### Post by sanone on 2008-04-07
> **Simon Bridge said:**
> You could try dinner and flowers - admitting you are "wrong" has been known to help. :)

See man pages, apologise(1) and woman(2224) - though the second one is out of date and incomplete.

--- now I've got that out of my system ---------------

lol.. I did not notice that spelling mistake :)

> **Simon Bridge said:**
> 
Wifi works out of the box - but it doesn't seem to speak WPA2. Acer should have mentioned that suspend, hibernate and restart don't work either. (restart?) And the boot process is hobbled by poor settings.
Try the madwifi drivers or the latest ndiswrapper onces. As for hybernating... yeah that simply does not work well :(

> **Simon Bridge said:**
> I submit for discussion that;
1. Acers windows only "empowering software" not running in linux is a limitation with Acer, not linux.
2. Linux not needing "empowering" in this way is not a *limitation* in linux
3. The inclusion of a connexant chipset (modem) in an intel soundcard was an acer decision - this is a combination which requires additional "empowering" to work in windows, and that linuxant do not support. This limitation exists in windows too, but is more of a limitation in linuxant support. (Lets all notify them.)
4. Nobody knows what is wrong with the mic. Likely culprit is the inclusion of conflicting non-intel subsytems in an intel board. Possibly representing budget limitations imposed by acer more than any limitation in linux.

1&2. I've seen this "empowering software" on vista and had a lot of trouble disabling / deinstalling that piece of crap. Really you don't want that! Perhaps that button can be mapped to something cool like gnome-do or something in the (near) future.

3. Did you notify them? In the netherlands the need for dial in modems is gone as almost everyone has a broadband connection to the internet. I personally have little need here.

4. Well actually I used it with skype the other day. Although I do not know exactly what I changed to get it working.
gstreamer-plugins -> Audio -> Default Input -> Plugin: Alsa
gstreamer-plugins -> Audio -> Default Input -> Device: ALC268 Analog
System -> Preferences -> Sound -> Devices -> Audio Conferencing -> Sound capture: ALSA (Custom)
System -> Preferences -> Sound -> Devices -> Default Mixer Tracks -> Device: Alsa Intel (Alsa mixer)

> **Simon Bridge said:**
> For future releases, acer need to treat their customers with a bit more (i.e. any) respect than this. Including full explanations of missing functions would be useful, as would actually *disclosing them* outside the box, where customers can see them before parting with money.

OTOH: FOSS has some political clout (here) in NZ, Once the national LUG and NZOSS became aware of the problems, the local acer reps have been taking steps to adress these problems. While I doubt they are 100% solveable for this hardware, the next linux box should be better appointed. We can only hope.

Whatever - it seems acer are serious about pre-installing linux.

We can only hope that the situation will be better in the future. Altough I'm a bit skeptical as acer tends to chose for the cheapest and not the best hardware/solutions in many cases. 

Cheers,
Sander

---

### Post by Simon Bridge on 2008-04-07
I stand corrected on the modem:
I contacted Linuxant about the problem and they insist that their madwifi driver works in this configuration. They say that the backports update to alsa is at fault - something about not updating the headers.

Wifi is good enough for public hotspots.

I have a web page dedicated to what I've found out so far.
[http://www.hbclinux.net.nz/acer4315.html](http://www.hbclinux.net.nz/acer4315.html)

At the moment I am stuck on ACPI (there is a package just for this in the 2.6.25 kernel!) and mapping the special buttons. The e-button is trivial, but the wifi, euro, and dollar keys do not produce xev events. I can get the scancodes (see link) and xmodmap is installed... so I'm studying.

The plan now is to get everything going, then use the OEM tools to create a new install CD: offer it to Acer (and make it available online.)

---

### Post by Simon Bridge on 2008-04-15
> **sanone said:**
> 
4. Well actually I used it with skype the other day. Although I do not know exactly what I changed to get it working.
gstreamer-plugins -> Audio -> Default Input -> Plugin: Alsa
gstreamer-plugins -> Audio -> Default Input -> Device: ALC268 Analog
System -> Preferences -> Sound -> Devices -> Audio Conferencing -> Sound capture: ALSA (Custom)
System -> Preferences -> Sound -> Devices -> Default Mixer Tracks -> Device: Alsa Intel (Alsa mixer)

The penultimate line dosn't exist for me. I have Sound Capture on "Default (Custom)". The test button responds with "unable to establish pipeline".

In the volume control options tab, which did you use for the input device?

When I attempt to start the sound recorder, it announces that the sound settings are invalid. I have to change the gstreamer-plugins device entry back to "default". Any recording from there produces a lot of clicks.

---

### Post by lazydesi on 2008-04-15
Hi, 
I am new to Ubuntu and I want to support the opensource

can somebody tell me running Ubuntu on this machine is faster than running XP sp2?

is this thread tells me Step by step procedure to run Ubuntu on Acer 5315?

---

### Post by lazydesi on 2008-04-15
> **Simon Bridge said:**
> I stand corrected on the modem:
I contacted Linuxant about the problem and they insist that their madwifi driver works in this configuration. They say that the backports update to alsa is at fault - something about not updating the headers.

Wifi is good enough for public hotspots.

I have a web page dedicated to what I've found out so far.
[http://www.hbclinux.net.nz/acer4315.html](http://www.hbclinux.net.nz/acer4315.html)

At the moment I am stuck on ACPI (there is a package just for this in the 2.6.25 kernel!) and mapping the special buttons. The e-button is trivial, but the wifi, euro, and dollar keys do not produce xev events. I can get the scancodes (see link) and xmodmap is installed... so I'm studying.

The plan now is to get everything going, then use the OEM tools to create a new install CD: offer it to Acer (and make it available online.)

Hi Simon,

yesterday I brought the Aspire 5315 from DSE tooo for $500

can you tell me step by step procedure to install ubuntu (including the drivers)?

---

### Post by mjwhitfield on 2008-04-16
> **lazydesi said:**
> is this thread tells me Step by step procedure to run Ubuntu on Acer 5315?Read the first post and follow it carefully.

---

### Post by Simon Bridge on 2008-04-16
> **lazydesi said:**
> Hi, 
I am new to Ubuntu and I want to support the opensource

can somebody tell me running Ubuntu on this machine is faster than running XP sp2?
If you are keen to support FOSS then it doesn't matter.

However - I have had the opportunity to run an XP and an Ubuntu version side by side.
Ubuntu boots about 10s faster than a minimum-install XP SP2. From login, the Ubuntu desktop is useable sooner by about 5s.

However, if I install enough additional apps to XP to match Ubuntu's basic functionality, the boot-time and login time for XP increases considerably. The difference can be as much as 1min depending on what is installed.

You get the same effect with useability. I can see the XP windows draw - but not the gnome windows, and gnome is not known for it's speed. MS-Word is quicker on the draw than OOo-Writer, but slows down sooner for large documents.

MS plays DVDs more smoothly, with less CPU overhead. OTOH: it doesn't have to brute-force the encryption. Similarly, MS plays (supported) DRMd media, Ubuntu simply doesn't.

Paradigms differ between the two OSs - so different functions make differing demands on the hardware.

If you disable the advanced desktop effects in Ubuntu, the interface becomes twitchy fast.

Basically, full-featured XP runs at a similar pace to the Ubuntu live-desktop session (which is constrained by the optical-drive speed). It is possible to get either OS to go slow with the "right" combination of running apps. The combination is different for each though.

Oh yeah - leave XP online for a day or so and experience how slow it gets. Ubuntu maintains it's speed because it isn't picking up malware. I took my XP machine online for just long enough to install a firewall and AV... (about 10 mins) the first scan picked up 4 items of malware. One was a keylogger, and another was a bot. The other two were for advertising.

> is this thread tells me Step by step procedure to run Ubuntu on Acer 5315?
Nope - my machine is a 4315. This thread has a lot of information, read through it carefully and take note of the things that ubuntu will not provide out of the box. Decide which of those you need.

Installing Ubuntu is as simple as booting from the CD and clicking "install" (follow the instructions - where you don't understand something, use the defaults.) Best option is to use the whole disk: less to learn about. From this thread, ubuntu will run enough of your hardware for you to have a functional computer - internet would be through the ethernet port, which means the rest is easy (easier than no internet at all).

Allow about three days for the learning curve - ask questions. Most of us can install to your kind of system in less than a day with everything going. You'll get that way too, but the first time always takes longer.

If you are nervouse - look up a Linux Users Group close to you - attend an installfest, or just ask for help in their mailing list.

Above all - have fun.

---

### Post by Simon Bridge on 2008-04-25
I can announce that Hardy Heron solves all outstanding issues except Suspend.

Suspend (to ram) will still reboot - I'll do some research.
Anybody with this working, please let me know.

A gotcha - the supplied aetheros drivers do not work.
I installed madwifi-ng from source, a la Ubuntu-Geek, but there must be a way of handling this Ubuntu style.

New page:
[http://www.hbclinux.net.nz/acer4315-804.html](http://www.hbclinux.net.nz/acer4315-804.html)

---

### Post by alucardromero on 2008-04-25
> **Simon Bridge said:**
> I can announce that Hardy Heron solves all outstanding issues except Suspend.

Suspend (to ram) will still reboot - I'll do some research.
Anybody with this working, please let me know.

A gotcha - the supplied aetheros drivers do not work.
I installed madwifi-ng from source, a la Ubuntu-Geek, but there must be a way of handling this Ubuntu style.

New page:
[http://www.hbclinux.net.nz/acer4315-804.html](http://www.hbclinux.net.nz/acer4315-804.html)

Awesome.  Wish I could say that for 5315.

> **sanone said:**
> It's a shame that it did not work out well for you alucardromero. I haven't updated yet myself (working on my master thesis and don't want to risk braking things during an upgrade) but when I do I let you know how it went.

Are you sure it's not related to wicd?

Cheers,
Sander

Okay, so I did a fresh install of 8.04 Final.

Sound works out of the box.  Wifi still needs ndiswrapper but there's something funky going on with the wireless methods...
Wifi did not work with WPA security.  I haven't thoroughly tested WEP but I will do that when I get home (I'm at school). But it did work **without any security at all**, which of course isn't quite desirable unless you're running a hotspot.  I have a Belkin router, and the manufacturers clearly bealieve that everybody and their grandma speaks Information Technology so I have no idea how/what to do with the WEP settings in my router.

Other than that, I'm satisfied with 8.04 so far, but... I won't be happy with wifi unless I can at least get WEP going.

I'll tinker with it a bit to get it up and share with you all how I did.  Don't expect me to mess with WPA or wpa-supplicant at all.  That's a whole other dedication of time, much less a whole other ball game.

But I'll keep everybody posted.

:)

---

### Post by mjwhitfield on 2008-04-26
Hi guys!

Thought I'd check in with you all.  I've been running 8.04 on my 5315 for 24 hours now and I figured I'd say what is and isn't working for me.

* The sound how works out the box, which is great news.

* Compiz-Fusion also works without messing around, no more issues with video playback while it's enabled either.

* Wifi still thinks it's working, but doesn't.  I had to blacklist the module as per the OP's instructions & reboot. Then use ndiswrapper as follows:
```
ndiswrapper -i net5416.inf
ndiswrapper -ma
ndiswrapper -mi
sudo modprobe ndiswrapper
```
Not sure if all those steps were needed, but my wifi kicked in right away.

* The screen auto dim now works as it did in 7.10, but in 8.04 the moment I start typing it brightens back up again (didn't happen for me in 7.10).

* The mic on the lid doesn't appear to be working, I've not tried the port on the front yet.

* The headphone jack on the front does work.

That's all that springs to mind right now, I'm very pleased with 8.04 for my Acer 5315.

---

### Post by lostfawords on 2008-04-27
madwifi works just fine, you just need a patched version. 

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

---

### Post by mjwhitfield on 2008-04-27
> **lostfawords said:**
> madwifi works just fine, you just need a patched version. 

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)And the benefits of using madwifi over ndiswrapper are?

---

### Post by sanone on 2008-05-05
> **mjwhitfield said:**
> And the benefits of using madwifi over ndiswrapper are?

Well perhaps they are more stable and you don't have to connect manually everytime?
And I think you can use aircrack-ng ([http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)) to gain access to 'protected' wireless networks.. just don't do anything illegal ;)

Cheers,
San

---

### Post by mjwhitfield on 2008-05-05
I don't have to connect manually everytime... being able to use aircrack is handy though.

---

### Post by KevinD_Atl on 2008-06-01
Didn't see the last page~

---

