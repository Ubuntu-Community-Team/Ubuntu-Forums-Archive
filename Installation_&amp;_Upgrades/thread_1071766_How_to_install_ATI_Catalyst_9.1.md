---
title: "How to install ATI Catalyst 9.1?"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by sticker_happie on 2009-02-16
[FONT="Georgia"][SIZE="2"]+ Can someone please give me step by step directions on how to install the ATI Catalyst 9.1 in Ubuntu 8.10. And please don't direct me to the ATI installation manual that ATI has in their website because the manual is in Linux language & I'm still speaking Windows...

[RIGHT]~THANKS[/RIGHT][/SIZE][/FONT]

---

### Post by Saija on 2009-02-16
just one question: why do you need that application, only for curiosity... ;)

Edit: by Catalyst you are meaning the privative-closed-source drivers, or the control center or whatever it calls?

Edit2: [Look here]("http://ubuntuforums.org/showthread.php?t=587372") and [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)")

---

### Post by sticker_happie on 2009-02-16
[FONT="Georgia"][SIZE="2"]+ I need it to play my videos without any flickering & record my desktop without my computer slowing down significantly. Read my first thread: [http://ubuntuforums.org/showthread.php?t=1071449](http://ubuntuforums.org/showthread.php?t=1071449)[/SIZE][/FONT]

---

### Post by Saija on 2009-02-16
open up a terminal, in gnome alt-f2 then write **gnome-terminal**, in the kde enviroment again alt-f2 then write **konsole**, there wrote this:

> fglrxinfo

then write the output of that program here to try to help you

---

### Post by sticker_happie on 2009-02-16
> **Saija said:**
> open up a terminal, in gnome alt-f2 then write **gnome-terminal**, in the kde enviroment again alt-f2 then write **konsole**, there wrote this:



then write the output of that program here to try to help you

[FONT="Georgia"][SIZE="2"]+ You guys are not getting it. You guys are talking in a totally different language. Please! I'm very new to Linux!! Lay it down in English please! Or at least in Windows terminologies. I don't know what KDE is, I don't know what KONSOLE is. Give me step by step directions on how to install the ATI CATALYST 9.1 FOR UBUNTU 8.10 INTREPID. The links that "Saija" gave was not helpful at all. Step-By-Step...[/SIZE][/FONT]

---

### Post by Saija on 2009-02-16
ok, my bad, sorry

tell me what version of ubuntu, or better, how do you installed? where do you grab the installer?

sorry buddy, for my instructions being so linux-centric, just give me some info so i could actually can try to help you

can you describe what you see in your desktop? the little buttons are on top or bottom of the desktop? what text is placed there? there's some "system", "places" text on top of the desktop? there's some letter "k" on the left bottom corner of your desktop? what looks the wallpaper?

**Gnome**: a desktop enviroment, it places the windows in the right position, places the maximize, close and restore buttons on the top of every window in your desktop, this Gnome, also includes some software: office suite, games, etc

**Kde**: do the same as gnome, but using different ways, it also includes an office suite, games, utilities, etc

**gnome-terminal** its a utility of the gnome environment, it let you input commands through a command line interface, something similar to the cmd.exe program from windows xp

**konsole**: the utility of the kde environment which, as gnome-terminal, lets you input command through a command line interface

**fglrxinfo**: its a program included in the ati propietary drivers(the drivers made by the ATI people) which display some useful information about the configuration of your graphics card, this fglrxinfo must be executed by some command line utility, thats why i give you some instructions to run it through gnome-terminal or konsole, depending on which environment you are

---

### Post by sticker_happie on 2009-02-16
[FONT="Georgia"][SIZE="3"]+ Ok this is starting to get ridiculous. This is one of the reasons why people are NOT switching OS from Windows. Installing a simple driver in Linux literally takes days when in Windows it takes less than a minute! I woke up at 7:00 in the morning & it's now 5:25pm. This is what I was afraid of in the first place. I registered in this forum to get help from the so called "Ubuntu Community" but so far no one has responded & given me step-by-step directions. Please don't talk to me in Linux terminologies because I don't know Linux. I just started! Can someone please level with me? And instead of giving me links, just write down in your replies in a way that it would be understood by a 7 yr old. Please.

[RIGHT]~THANKS[/RIGHT][/SIZE][/FONT]

---

### Post by sticker_happie on 2009-02-16
> **Saija said:**
> ok, my bad, sorry

tell me what version of ubuntu, or better, how do you installed? where do you grab the installer?

sorry buddy, for my instructions being so linux-centric, just give me some info so i could actually can try to help you

can you describe what you see in your desktop? the little buttons are on top or bottom of the desktop? what text is placed there? there's some "system", "places" text on top of the desktop? there's some letter "k" on the left bottom corner of your desktop? what looks the wallpaper?

[FONT="Georgia"][SIZE="2"]+ I am using Ubuntu 8.10 sir & I haven't done anything to change the interface. It's the same interface as the newly installed Ubuntu 8.10 would look like in a computer. I have the Applications, Places & Systems on the top panel & I have the windows tabs on the bottom panel.[/SIZE][/FONT]

---

### Post by sticker_happie on 2009-02-16
> **Saija said:**
> ok, my bad, sorry

tell me what version of ubuntu, or better, how do you installed? where do you grab the installer?

sorry buddy, for my instructions being so linux-centric, just give me some info so i could actually can try to help you

can you describe what you see in your desktop? the little buttons are on top or bottom of the desktop? what text is placed there? there's some "system", "places" text on top of the desktop? there's some letter "k" on the left bottom corner of your desktop? what looks the wallpaper?

**Gnome**: a desktop enviroment, it places the windows in the right position, places the maximize, close and restore buttons on the top of every window in your desktop, this Gnome, also includes some software: office suite, games, etc

**Kde**: do the same as gnome, but using different ways, it also includes an office suite, games, utilities, etc

**gnome-terminal** its a utility of the gnome environment, it let you input commands through a command line interface, something similar to the cmd.exe program from windows xp

**konsole**: the utility of the kde environment which, as gnome-terminal, lets you input command through a command line interface

**fglrxinfo**: its a program included in the ati propietary drivers(the drivers made by the ATI people) which display some useful information about the configuration of your graphics card, this fglrxinfo must be executed by some command line utility, thats why i give you some instructions to run it through gnome-terminal or konsole, depending on which environment you are

[FONT="Georgia"][SIZE="2"]+ I download the ATI Catalyst 9.1 from their website exactly as how I would do it in Windows which is clicking on the dowload link. That's it. Then I see the file in my desktop but I have no idea what to do from their. I'm not sure if I'm supposed to use ADD/REMOVE, SOFTWARE SOURCES, SYNAPTIC PACKAGE MANAGER, TERMINAL or UPDATE MANAGER.[/SIZE][/FONT]

---

### Post by Saija on 2009-02-16
please take a look in the "system" option placed in the top of your desktop, there is a option called "administration", in there is a option called "hardware controllers", this option has a icon of an computer chip, please click it, it ask for your password...

---

### Post by Saija on 2009-02-16
> hen I see the file in my desktop but I have no idea what to do from their. I'm not sure if I'm supposed to use ADD/REMOVE, SOFTWARE SOURCES, SYNAPTIC PACKAGE MANAGER, TERMINAL or UPDATE MANAGER.

what's the name of that file?

---

### Post by sticker_happie on 2009-02-16
> **Saija said:**
> please take a look in the "system" option placed in the top of your desktop, there is a option called "administration", in there is a option called "hardware controllers", this option has a icon of an computer chip, please click it, it ask for your password...

[FONT="Georgia"][SIZE="2"]+ I don't have HARDWARE CONTROLLERS in my SYSTEM> ADMINISTRATION. I have HARDWARE DRIVERS. The the proprietary drvier their by ATi & that is what I'm trying to replace because that's the one that came with the Ubuntu 8.10 install. The name of the file is: ati-driver-installer-9-1-x86_x64.run[/SIZE][/FONT]

---

### Post by Saija on 2009-02-16
ok, now i just figure some things, you right now have the open source driver for ati cards but want the propietary, to make this happen you need to take a look at [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)")

just read that link and tell me what steps you don't undertand so i can try to help you, some hints:

[LIST=1]
[*]Open up a terminal: press the keys ALT and then F2, a little window appears, then write gnome-terminal, then enter

[*]The terminal appears: once you make step 1 a window appears, in there you can see your user name, the @ symbol, the name you choose for your computer and a $ symbol

[*]Install requerides software: once step 2 is verified copy & paste this text: > sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot 
[/LIST]

please do that 3 steps and let me know any issue you have, then i'll try to help you with the remaining steps so you can install the driver you just download from the ati website...

---

### Post by sticker_happie on 2009-02-16
> **Saija said:**
> ok, now i just figure some things, you right now have the open source driver for ati cards but want the propietary, to make this happen you need to take a look at [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)")

just read that link and tell me what steps you don't undertand so i can try to help you, some hints:

[LIST=1]
[*]Open up a terminal: press the keys ALT and then F2, a little window appears, then write gnome-terminal, then enter

[*]The terminal appears: once you make step 1 a window appears, in there you can see your user name, the @ symbol, the name you choose for your computer and a $ symbol

[*]Install requerides software: once step 2 is verified copy & paste this text:  
[/LIST]

please do that 3 steps and let me know any issue you have, then i'll try to help you with the remaining steps so you can install the driver you just download from the ati website...

[FONT="Georgia"][SIZE="2"]Ok. I did that & this is what popped up:

carlo@carlo-desktop:~$ sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot 
[sudo] password for carlo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg-dev is already the newest version.
debhelper is already the newest version.
libstdc++5 is already the newest version.
dkms is already the newest version.
build-essential is already the newest version.
cdbs is already the newest version.
fakeroot is already the newest version.
The following packages were automatically installed and are no longer required:
  evolution-common libimlib2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
carlo@carlo-desktop:~$ 
[/SIZE][/FONT]

---

### Post by sticker_happie on 2009-02-16
> **Saija said:**
> ok, now i just figure some things, you right now have the open source driver for ati cards but want the propietary, to make this happen you need to take a look at [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)")

just read that link and tell me what steps you don't undertand so i can try to help you, some hints:

[LIST=1]
[*]Open up a terminal: press the keys ALT and then F2, a little window appears, then write gnome-terminal, then enter

[*]The terminal appears: once you make step 1 a window appears, in there you can see your user name, the @ symbol, the name you choose for your computer and a $ symbol

[*]Install requerides software: once step 2 is verified copy & paste this text:  
[/LIST]

please do that 3 steps and let me know any issue you have, then i'll try to help you with the remaining steps so you can install the driver you just download from the ati website...

[FONT="Lucida Sans Unicode"][SIZE="2"]+ On the link that you've given me, the 2nd step I don't understad. It says: You will then need to build the installation packages with the downloaded ATi drivers (ensure the ATi drivers have the execute flag set first)

+ I don't know what the line in the parenthesis mean. Execute flag set first?[/SIZE][/FONT]

---

### Post by sticker_happie on 2009-02-17
[FONT="Arial"][SIZE="2"]+ Anyways, I think I've resolved the issue sir. I went to the "Unofficial ATI Linux Driver Wiki". Here's the URL: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

+ I tried my best to understand what it was saying & followed all the steps. Now I'm not 100% sure that it worked because I have no way of knowing if I have the right version which is the Catalyst 9.1. But what I did was I turned on Compiz & played videos & movies in .mpg, .wma, .avi format & all the flickering is gone. But if you know a way to check what driver version is installed then please let me know.

[RIGHT]~THANK YOU MUCH[/RIGHT][/SIZE][/FONT]

---

### Post by dashaund on 2009-02-17
Have you tried EnvyNG yet?  It work perfectly on my system.  I'm able to install ATI drivers and enable Desktop Effects in minutes, even faster than on Windows.  You can check it out at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (yes, ATI is supported even though it says nvidia).  Tip: just choose the text version.  It's quicker and faster to setup and very easy to use even though it's not as "pretty."

---

### Post by sticker_happie on 2009-02-17
> **dashaund said:**
> Have you tried EnvyNG yet?  It work perfectly on my system.  I'm able to install ATI drivers and enable Desktop Effects in minutes, even faster than on Windows.  You can check it out at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (yes, ATI is supported even though it says nvidia).  Tip: just choose the text version.  It's quicker and faster to setup and very easy to use even though it's not as "pretty."

[FONT="Arial"][SIZE="2"]+ I'd love to try it but I looked at the link that you wrote & it looks like that doesn't support Ubuntu Intrepid Ibex.[/SIZE][/FONT]

---

### Post by tenmoi on 2009-02-17
> **sticker_happie said:**
> [FONT="Arial"][SIZE="2"]+ Anyways, I think I've resolved the issue sir. I went to the "Unofficial ATI Linux Driver Wiki". Here's the URL: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

+ I tried my best to understand what it was saying & followed all the steps. Now I'm not 100% sure that it worked because I have no way of knowing if I have the right version which is the Catalyst 9.1. But what I did was I turned on Compiz & played videos & movies in .mpg, .wma, .avi format & all the flickering is gone. But if you know a way to check what driver version is installed then please let me know.

[RIGHT]~THANK YOU MUCH[/RIGHT][/SIZE][/FONT]

So you want to do it the Windows way, huh? 
- Alt + F2 -> gksu nautilus
- Browse to where your ati. run is located.
- Right-click on it -> Properties -> permissions -> check/tick "ALlow executing as program" (If this should not work, open a terminal (look below if not knowing how!) sudo chmod +x /pathtowhereatidriveris)
- Double click the .run file -> run in terminal
- OK AND ACCEPT AND OK DOO .. DUH 
- and there you go!
then
- Applications -> Accessories -> Terminal and enter: sudo aticonfig --initial -f
REboot to enjoy!:D

---

### Post by Saija on 2009-02-17
well at least it seems it worked for you, bravo!

anyways i'm also a noob and jut tried to be the most helpful as possible, anyways if you do the alt-f2 then gnome-terminal then fglrxinfo thing it should give you some advice about what graphics driver you're using now

---

### Post by chmbrs on 2009-02-18
ok i get you. linux is harder, a lil, but its definetly worth it. winblows doesnt compare to linux in any way. if you wanna use crappy os no one is stopping you. if youre willing to give some time and patience, you wont regret it, trust us. i just made the switch. took me 6 months to fully switch. i wont ever use windows again. you should watch "Revolution OS" to find out what linux is about. Now back to your problem.

ive had trouble with ati and wasted many hours trying to get it work with compiz, i ended up buying a nvidia card for 30 bucks to solve my problem for good. which ati chipset do you have?

go to System>Administration>Restriced drivers.

there should be an Ati driver there. just click Enable or activate or whatever then restart pc. everything should work fine. now if you have rc410 radeon xpress 200 it WONT work. to find this out you can: 
System>Administration>Packagemanager

then search device manager

install package gnome-device-manager

after install it should be in applications>systemtools if not just find it.
open it and scroll down to VGA when you click on it itll show you the device and stuff. if it's rc410 radeon xpress 200 i wouldnt bother. just get a nvidia card. either way after you enable the restriced driver and reboot, if the screen says, out of resolution, or is blank just reboot
then boot ubuntu [recovery mode] and pick fix x server. i hope i helped you at least a bit as this is my first post trying to help someone. im new to linux too and am mostly looking for help.;)

post back what happened.

---

### Post by sticker_happie on 2009-02-18
> **chmbrs said:**
> ok i get you. linux is harder, a lil, but its definetly worth it. winblows doesnt compare to linux in any way. if you wanna use crappy os no one is stopping you. if youre willing to give some time and patience, you wont regret it, trust us. i just made the switch. took me 6 months to fully switch. i wont ever use windows again. you should watch "Revolution OS" to find out what linux is about. Now back to your problem.

ive had trouble with ati and wasted many hours trying to get it work with compiz, i ended up buying a nvidia card for 30 bucks to solve my problem for good. which ati chipset do you have?

go to System>Administration>Restriced drivers.

there should be an Ati driver there. just click Enable or activate or whatever then restart pc. everything should work fine. now if you have rc410 radeon xpress 200 it WONT work. to find this out you can: 
System>Administration>Packagemanager

then search device manager

install package gnome-device-manager

after install it should be in applications>systemtools if not just find it.
open it and scroll down to VGA when you click on it itll show you the device and stuff. if it's rc410 radeon xpress 200 i wouldnt bother. just get a nvidia card. either way after you enable the restriced driver and reboot, if the screen says, out of resolution, or is blank just reboot
then boot ubuntu [recovery mode] and pick fix x server. i hope i helped you at least a bit as this is my first post trying to help someone. im new to linux too and am mostly looking for help.;)

post back what happened.

[FONT="Arial"][SIZE="2"]+ What are you talking about? Why would I switch back to Windows? I don't wanna deal with anything Microsoft. I was just frustrated about how I couldn't figure out how to install a simple driver. You know how it is. Haha! I even bought a book called "How to Do Everything Ubuntu". Very helpful. Ubuntu is my primary OS from now on. No other distros for me & definitely no Microsoft. Not sure about Mac OS. If they lower their freaking prices, maybe. But I'm very content with Ubuntu.

+ But yeah, on the Catalyst thing I followed the instructions on this site: [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide). And I think that resolved the issue.

[RIGHT]~THANKS ALL[/RIGHT][/SIZE][/FONT]

---

### Post by chmbrs on 2009-02-18
GREAT!!!!!!!!!!!!!!!!

this forum is what's unique about linux. you cant get support like this for winblows. its pretty rough to make the switch and theres a lot of differences and some things are harder to do but after using it for a week theres no way, anyone would go back to winblows. it gets easier and funner everyday. if youre new to linux deffinetly check out Revolution Os. either google video or torrent. its a really interesting documentary about linux and how it differs from winblows. its really good. i watched it like 3 times.

---

### Post by sticker_happie on 2009-02-18
> **chmbrs said:**
> GREAT!!!!!!!!!!!!!!!!

this forum is what's unique about linux. you cant get support like this for winblows. its pretty rough to make the switch and theres a lot of differences and some things are harder to do but after using it for a week theres no way, anyone would go back to winblows. it gets easier and funner everyday. if youre new to linux deffinetly check out Revolution Os. either google video or torrent. its a really interesting documentary about linux and how it differs from winblows. its really good. i watched it like 3 times.

[FONT="Arial"][SIZE="2"]+ Word!... I mean, OPENOFFICE! LoL! I'll definitely watch that. I work at a computer department at Best Buy here in California & I'm seeing more & more computers with Ubuntu in them instead of Windhoes especially on the laptops & netbooks. HPs, Dells & Gateways mostly. I love it![/SIZE][/FONT]

---

### Post by thefish123 on 2009-05-26
..deleted...

---

