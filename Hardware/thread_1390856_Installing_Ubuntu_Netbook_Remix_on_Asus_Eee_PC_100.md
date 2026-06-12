---
title: "Installing Ubuntu Netbook Remix on Asus Eee PC 1005P"
date: 2010-01-26
forum: Hardware
---

### Post by gregpritchard on 2010-01-26
I recently purchased an Asus Eee PC 1005P with Windows 7. I wanted to completely replace Windows with Ubuntu Netbook Remix 9.10 Karmic Koala, as Ubuntu as its my distro of choice. This is how I did it, as a very simple guide, for those who are contemplating the same. The ubuntuforums have saved my bacon more times than I can count; so this is my way of giving back (plus a handy repository if I want to do this again and forget how!).

In all in all, everything works great, with wireless being the biggest challenge during installation.

Pre-requisites:

[LIST=1]
[*]Another computer (I was running Ubuntu 9.04)
[*]Ethernet connection with internet
[*]Spare/empty USB drive with at least 1 Gb of space
[*]Asus Eee PC 1005P
[/LIST]

**Get Ubuntu for the Netbook**

Firstly, you're going to need to download the CD Image for Ubuntu Netbook Remix (UNR) from Ubuntu. From the other computer, navigate to the following location from your browser of choice:
[URL="http://www.ubuntu.com/GetUbuntu/download-netbook"]
http://www.ubuntu.com/GetUbuntu/download-netbook[/URL]

Click the Download Ubuntu CD Image link and save the ISO image (e.g. ubuntu-9.10-netbook-remix-i386.iso) to the other computer.

**Prepare USB Stick**

The 1005P netbook doesn't come with a CD/DVD drive; so you're going to need to do the installation from the USB key on the netbook. To do this; we'll convert the ISO (that would normally be burnt to a DVD) to the USB file structure.

Once the ISO has finished downloading; you're going to need the usb-creator utility. Follow the instructions from this page:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Follow the instructions, but the short end of it is, from the other computer, type/paste in the following command into a Terminal to install usb-creator:

```
sudo apt-get install usb-creator
```Once this has installed; plug your USB stick into the other computer and run the usb-creator by typing the following command into a Terminal:

```
usb-creator
```Careful: the next step will erase everything from the USB stick; so make sure you've backed up whatever was on there.

As per the instructions at the previous link; simply select the ISO just downloaded in the top box, and select the USB stick in the bottom box. Click "Make Startup Disk" and you're on you're way. Once finished; your USB stick is ready to be used as the install source for the netbook.

**Prepare the Netbook to boot from the USB Stick**

Start up the netbook using the Power button on the right-hand-side (the Windows one, not the Express Gate one on the left-hand-side). In the nanoseconds after you press the Power button; click once or many times; Ctrl+ESC to stop the default loading of Windows. Then click F2 to access the boot setup.

When you get to the BIOS setup options; scroll right to Boot from the top menu tabs. Then select Boot Priority Order. You want the first item to say "Removable Dev" (or similar). Once you've done this; click F10 to save your changes.

I've read that there is a way to change the boot order from within Windows, but I never booted into Windows on the netbook and I've never used Windows Vista or 7; so best to follow those instructions if you find them.

**Installation**

Plug in the ethernet cable connected to your modem/router/switch to the netbook.

In addition, plug in the USB stick with the UNR installation files into the netbook. Reboot/Start the netbook; clicking Ctrl+ESC to give you the boot choices. Select the USB key from the options provided. This should bring up the Ubuntu installation choices; selecting Install Ubuntu to get started.

Follow all standard questions (username, computer name, passwords, languages, locales, etc.). Let the system finish the installation as normal. Up to you whether you want to retain the Windows partition; I didn't, and there are gurus in the Ubuntu community better placed to advise on the best way to do this.

**Post-Installation**

I know a lot of people have had issues with the Ethernet connection on the 1000HA, but I didn't experience any issues on the 1005P.

Once the system is installed; you'll want to update your system. From the main menu; navigate to System -> Administration -> Update Manager. Click Install Updates to get your system up-to-date.

More instructions here:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

**Wireless**

Now, you probably find that wireless isn't working. The problem is, UNR doesn't seem to recognise the hardware at all. So commands like iwconfig, etc. return no recognition of the wireless card. This was driving me nuts. I'd tried installing the Karmic backports, building from source the drivers into the kernel, and a whole lot of other things; but the one thing that appeared to work was isidoro's post on this thread:

[http://ubuntuforums.org/showthread.php?p=8700392](http://ubuntuforums.org/showthread.php?p=8700392)

This is the Windows XP drivers for the Atheros AR2427 wireless card. The file you're going to need is: xp3264-7.7.0.329-whql.zip from the following location:

[http://www.atheros.cz/download.php?atheros=AR5007EG&system=1](http://www.atheros.cz/download.php?atheros=AR5007EG&system=1)

I've also saved a copy of this zip on my company's website if the above link expires:

[http://www.dedicationgroup.com/files/xp3264-7.7.0.329-whql.zip](http://www.dedicationgroup.com/files/xp3264-7.7.0.329-whql.zip)

Save the zip file down to the netbook. Extract from the zip the netathw.inf file. Now that you have this; you're going to need ndiswrapper; which is a Linux wrapper around Windows drivers. To install ndiswrapper and the ndiswrapper graphical client; type the following commands into your Terminal:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```Once these have been installed; run the ndisgtk tool from the Terminal:

```
sudo ndisgtk
```This is will bring up the Wireless Network Drivers screen. Click on "Install New Driver". Browse for the netathw.inf file just extracted from the zip file, and click "Install". You should see in the Currently Installed Windows Drivers box "netathw Hardware present: Yes". Now, go to System -> Preferences -> Network Connections -> Wireless (tab) and click "Add" to setup your wireless connection.

**That's It**

I've found pretty everything else to work that I've tried. The (blue) function keys work fine. Have not yet had an issue Suspending and Hibernating. Battery life is a dream. Now that UNR is running successfully; this netbook is just an awesome piece of kit. 

Corrections, updates and better explanations welcome. Best of luck!

---

### Post by zeroK on 2010-01-26
I hope you don't mind me asking some questions about your setup here :-) I'm currently contemplating really hard getting a 1005P but the NM10 graphics chip worries me a little bit. Did the netbook work out of the box in 1024x600?

---

### Post by gregpritchard on 2010-01-26
@zeroK

I actually originally tried Jaunty 9.04 on the Asus 1005P and that was not very good in my opinion. There were just to many parts of the system which assumed a standard monitor. The Netbook Remix is perfect though, and assumes the 1024x600 screen, so font and window sizes have the right relative sizes. Everything is crystal clear too. 

Let me know if there is some specific info you'd like to know.

---

### Post by zeroK on 2010-01-26
> **gregpritchard said:**
> @zeroK

I actually originally tried Jaunty 9.04 on the Asus 1005P and that was not very good in my opinion. There were just to many parts of the system which assumed a standard monitor. The Netbook Remix is perfect though, and assumes the 1024x600 screen, so font and window sizes have the right relative sizes. Everything is crystal clear too. 

Let me know if there is some specific info you'd like to know.

I was refering to driver issues with the NM10 graphics chip, but if this now works out of the box with 9.10 UNR I'm more than happy, thank you :-) What specific model of the 1005P do you have? The P or the PE?

Thanks you very much for the information so far :-)

---

### Post by gregpritchard on 2010-01-26
Have had absolutely no issues with the drivers for the graphics chip. Model is specifically 1005P.

All good

---

### Post by zeroK on 2010-01-26
Great, thank you very much :-) If uncle Steve doesn't announce anything useful and available tomorrow, I will perhaps get myself the same machine tomorrow :-)

---

### Post by a_rojilla on 2010-01-28
Congratulations.

All I can say is that I tried installing Ubuntu on a 1005P with no success: no keyboard, no touchpad... Nothing. I tried 9.04, 9.10, UNR... Only 8.04 barelly works (no wireless of course, 800x600 screen...).

Going back to Windows 7.

Regards.

---

### Post by zeroK on 2010-01-29
From what I've found so far on the net, you have to install a bios upgrade to get the keyboard and touchpad to work.

---

### Post by a_rojilla on 2010-01-29
Thanks for your reply zeroK, it brought me some hope.

Now I have to decide: spent more time trying to make Ubuntu work or just go back to Windows 7 and wait a few months?

Well, I don't like Windows at all (I've been using OpenSUSE and Ubuntu for years now), but the Asus 1005P I'm talking here is not mine (it's my 5 years old daughter's first computer -yes, I know, an expesive present, but it will be used by the whole family), and I don't really care if she has to use Windows for now... as long as everything works.

BTW I also tried installing Linux Mint (really nice, but still prefer Ubuntu) and Moblin (seems too underdeveloped, but very promising) with similar results...

The think is... sometimes the keyboard works, sometimes not (and it's hard to update anything without keyboard, if it weren't thanks to the onscreen keyboard). Same for the touchpad. And it won't restart or shut down...

So... gregpritchard, did you upgraded the BIOS? It is strange that you got everything working being the same machine. Thanks in advance.

Regards.

---

### Post by zeroK on 2010-01-29
There might be a chance that Asus already ships units with the new BIOS pre-installed. That's the only explanation I can think of for people who didn't need to do the update and who really installed Ubuntu instead of just using the live disc.

---

### Post by a_rojilla on 2010-01-29
You may be right zeroK. I think I was one of the first persons to get the 1005P, :) (it was bought as a Christmas present), but when I got it I had been a few weeks without Internet and wasn't aware of new launches. The Atom N450 chip sticker was a hint though.

I'm going to upgrade the BIOS and see what happens.

Regards.

---

### Post by erdalronahi on 2010-01-29
I have the same issues as a_rojilla on the laptop of a friend. No sound, no keyboard, basically nothing works.

I would like to do the BIOS update if that helps. Can anybody give me a hint how to do that?

---

### Post by Hansmc on 2010-01-29
According to chadraytay here [http://newyork.ubuntuforums.org/showthread.php?p=8699560]("http://newyork.ubuntuforums.org/showthread.php?p=8699560"):

> Ok, figured out exactly how to make the keyboard and mouse work...

unplug the computer. :-/

You can plug it in after it starts. But not before. And everything but sound works fine. If its plugged in completely during the entire startup process (I was plugging it in as it started the first time it worked) then keyboard and mouse are disabled...

very strange

So make sure it is off external power, during boot. Does that work for you? Let us know if a bios upgrade helps. Thanks

---

### Post by erdalronahi on 2010-01-29
The BIOS upgrade was actually very simple, since there is a tool for that. It is started with ALT+F2 from the start screen after the power on.

Now keyboard, sound and camera work. The remaining problems are:
[LIST]
[*]no WLAN
[*]no microphone works, neither internal nor external
[/LIST]
The ndiswrapper solution for the WLAN (Atheros 168c:002c) did not work for me at all. Ndiswrapper finds all drivers to be "invalid".

---

### Post by incade on 2010-01-29
So I just have a few questions.. I too have been fighting with this thing for a few days now trying to get everything to work. I installed Ubuntu 9.10 and was able to get most of my stuff working, but it seemed that my battery life was terrible (roughly 4-5 hours). You did say you're seeing improved battery life with the Ubuntu UNR?

Also, was anyone able to resolve the issue where the brightness adjustment would seem to adjust brighter, dimmer, brighter, and so on?

I also noticed when I had Ubuntu on there, the screen would seem to flicker at times. I'm assuming this was the APCI trying to dim the screen and Linux not knowing how to react with it?

You guys are doing great at documenting this stuff way early! Keep it up!

Edit: I too was having the intermittent keyboard and touchpad issues, I'll post back with what I find this time around. (I have done the BIOS update now). I'm really hoping that I don't have to leave the computer unplugged every time I start it up. But, if so that's a small price to pay to not be stuck in Windows 7.

---

### Post by Hansmc on 2010-01-29
> **erdalronahi said:**
> The remaining problems are:
[LIST]
[*]no WLAN
[*]no microphone works, neither internal nor external
[/LIST]
The ndiswrapper solution for the WLAN (Atheros 168c:002c) did not work for me at all. Ndiswrapper finds all drivers to be "invalid".

Both wireless LAN and microphone are talked about here: [Asus Eee PC 1005PE]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005PE"). Also check out the notes on [1005ha]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA"). The microphone fix for the 1005he might work for the 1005pe. Let us know if any of these work for you. Have a good day.

---

### Post by erdalronahi on 2010-01-29
> **Hansmc said:**
> The microphone fix for the 1005he might work for the 1005pe. Let us know if any of these work for you.

The 1005pe is a different model than the 1005p. None of these fixes work on the new 1005p.

---

### Post by Hansmc on 2010-01-29
> **erdalronahi said:**
> The 1005pe is a different model than the 1005p. None of these fixes work on the new 1005p.

Ok, I am sorry. According to most of the reviews I was reading it seemed like the only difference was 1005pe has a little bigger hard drive and battery, and wireless N. One other thing is the glossy vs matte screen. So I was assuming all the internals (cpu, chip set, etc) was the same.

---

### Post by erdalronahi on 2010-01-30
> **Hansmc said:**
> According to most of the reviews I was reading it seemed like the only difference was 1005pe has a little bigger hard drive and battery, and wireless N.

Well, yes, the wireless N is exactly the problem. The chipset is too new, even ath9k does not recognize it. I am really desperate. Netbook without wireless is a bit like car without wheels.

---

### Post by Hansmc on 2010-01-30
I did a little more checking around [and found this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507507"):

> Hi again,

following link in

    [http://ubuntuforums.org/showthread.php?p=8740712](http://ubuntuforums.org/showthread.php?p=8740712)

wifi is working too.

Alberto.

But that just links back to here. I am not sure what they did, but maybe you could ask them. [See post nine.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507507")

---

### Post by mudguts on 2010-02-01
i run 9.04 on the Asus eee PC 1000HD.

I also get the flicker though I think that it's something to do with compiz as once I turned that off and went to the basics, the screen flicker stopped.

Other then that, the 1000HD worked out of the box on 9.04
though 9.10 was a disaster...  no Wi-Fi, blank screens etc. etc.

---

### Post by suaveviento on 2010-02-01
Just a bit of feedback. I bought my ASUS 1005PE two weeks ago and had much of the same issues that were reported--WIFI crapped out periodically, keyboard and mouse didn't work (had to use USB ones) and kernel errors would pop up. Upgrading to a newer BIOS fixed almost all of these problems--the wireless NIC didn't work as well as it should have (fixed by using the old driver), the system flickers sometimes, and the battery doesn't last as long as it does with Windows 7. The keyboard, trackpad, and kernel errors disappeared after the BIOS upgrade. I can live with the flickering and battery life for now. I am confident that a solution will be found for these little annoyances.

---

### Post by a_rojilla on 2010-02-04
Well, I can't upgrade the BIOS (it doesn't find my UBS memory, maybe it is bad formated -tried lots of different options: fat16, 32, ntfs- or I don't know how to rename the file -1005P.ROM?-), any idea?

Anyway, it seems the new BIOS will not solve all of the problems, specially wireless. I guess I'll reinstall W7 and wait until everything works (let's see what Lucid brings).

Still, where is the OP? He got everything working... how? :-?

Regards.

---

### Post by zeroK on 2010-02-04
I also got about everything working right now except for the unstable wifi driver. If you have W7 installed, you can use ASUS' own BIOS update tool, which makes the whole update process reeeeeaaallly easy :-) Basically it is about 3 clicks ;-)

---

### Post by mmaas70 on 2010-02-04
Updated the BIOS on the 1005p, but no succes with the Wlan. #1's suggestions don't work. Netathw-driver is invalid. Drives me crazy, because lan and mobile broadband works.
Everything else works too btw. On Karmic and Mint Helena. No problems with screen or sound. I hate to move back to win7, because it crashes several times a day.

Maybe we should remove [solved] from this posts header?

Edit: SOLVED! thx to the excellent Ubuntu wiki

[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005P]("https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005P")

I loaded the wrong driver for ndiswrapper. So the drivers mentioned by OP are not correct.

---

### Post by a_rojilla on 2010-02-05
> **mmaas70 said:**
> Edit: SOLVED! thx to the excellent Ubuntu wiki

[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005P]("https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005P")

Well, I already reinstaled W7 yesterday, but what you found in the Wiki is new (I believe it wasn't there when this thread started), so I'm going to give it a try (what goes to show you how little I like Windows -even my wife and my 5 years old daughter are used to gnome now-).

Regards.

---

### Post by a_rojilla on 2010-02-08
Everything working now! :D

I updated the BIOS in W7 and then installed 9.10. As reported by others, everything fine except wireless, but like mmaas70 pointed out the wiki now has the answer.

Great! I had to use W7 for a few days a what a pain in the... :p

Regards.

---

### Post by anaconda on 2010-02-22
Thanks to the OP. I have also (almost) everything working. Including wlan.

haven't tried the mic yet, and the touchpad doesn't recognize multituouch.

Have any of you got the multitouch functions  of the touch pad working???

Oh. I installed ubuntu 9.10. (I have tried UNR before, and don't like it.)

---

### Post by chaoszcat on 2010-02-24
Hey!

I have just installed it onto my 1005P and everything just work out charmingly

Thanks for the great guide. Will back to this topic often to get updates & tips :)

Cheers
Lionel

---

### Post by erdalronahi on 2010-02-24
Everything? Including the internal microphone? I have installed the alsa-backport modules on two computers of the same type - no success.

---

### Post by kmiernik on 2010-03-01
I'm another happy user of Eee 1005P. I have first upgraded BIOS and then moved to UNR. Everything works fine. Function buttons - suspend, volume control, brightness control (after adding acpi_osi=linux option in grub), wireless is doing very well (running on atk9k module), camera, external monitor and so on.

Of course there are no special touchpad gestures (I have tried little bit of them in Win and not crying after them), however scrolling with touchpad works - which is the only thing I need.

The only last thing I couldn't get to work is a build-in microphone. It is not even detected anyway.

---

### Post by CanyonDrifter on 2010-03-01
Fyi... My Asus eeepc, model 1001p, works great with 9.10, thanks to ndiswrapper (ndisgtk) and the pervious few posts right here!  The Asus download page for my model did NOT give me the correct inf file that works, since I clicked on the Windows 7 hardware link, but when I clicked on the XP operating system downloads selection and got the XP available downloads, then downloaded and unzipped them, I did run into another problem...  the correct inf file to load with ndisgtk is the 'netathwx' NOT the other one, which apparently worked for others but not for my model.  I actually tried the other one, as listed in other posts, but had no sign of life, even though it did report to have 'seen installed hardware' in existence, NOT seeing any networks available, and nothing on the little icon in my screen's panel. But then..
  Here's what I did:  Got Asus downloads off the model recomended page, having chosen XP as operating system, not 7 or Linux, I unzipped them to a convenient location, opened ndisgtk with   sudo ndisgtk   using a terminal, then using ndisgtk I browsed and located the   netathwx    (the correct inf file for mine) and clicked install, waited a couple minutes, and my panel icon kicked into life, found the wireless signals and put this HUGE smile on my face!  It had been a two or three week nightmare for me to get this working.  Thanks to everyone here...  :D :D :D :D :popcorn:

---

### Post by RadeRad on 2010-03-05
I had **no** issues installing Ubuntu 9.10 Netbook Remix on my ASUS Eee 4G PC.  The standard 9.10 was eating up my DOC, the remix left me with 1/3 of the DOC free!  I built the installation CD from a WinXP platform.


[LIST=1]
[*]Downloaded UNR
[*]Downloaded and installed the CD burner from: [http://infrarecorder.org/](http://infrarecorder.org/)
[*]Burned the CD with UNR
[*]Installed UNR on my ASUS Eee Surf
[*]Added my wireless definitions, and the network kicked right up.
[/LIST]

Overall, pleased!   I was getting concerned that the 4G had run its course.  

Rade

:popcorn:

---

### Post by Fakil on 2010-04-08
Hi, this is my first post here!

I have the same computer as you, an Asus EEE 1005P, and I've followed all your instructions, in fact, I'm writing this post from Ubuntu Netbook-remix OS with an ethernet-cable connected to my PC and I am getting connection to the Internet perfectly fine like this. I've downloaded and installed all the updates, so my system is up to date, but my problem is that I can't get the driver that you recommended for the computers network-card to work when using ndiswrapper. ndiswrapper just keep telling me the driver (netathw) is invalid when I have installed it and I can't get my wireless network to work. Please help me! Any suggestion of other drivers I may try?

EDIT: Haha, solved it thanks to the Wiki, and I almost started dancing on the floor of sheer happiness! :P. Thx anyways!

---

### Post by dionblundell on 2010-04-18
I have a AR2427 on 1005PE that does not work.
This WILL get it working using GNU drivers. I think that the kernel uses  an old wireless build? Not sure why? Anyway, the following works. And appears to be much simpler, better and faster than the hack to get the windows drivers working.

Go here:
[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)
and download the latest drivers, for example:
[URL="http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-16.tar.bz2"]http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-16.tar.bz2
[/URL]
Now extract these files
Open a SHELL, and change into the directory created with the archive,  it's probably something like:
```
cd ~/Downloads/compat-wireless-2010-04-16

```now select the driver
```
./scripts/driver-select ath9k
```You now need to build the  drivers
```
make
```Now install them with this
```
sudo make install
sudo make unload
sudo modprobe ath9k

```You will need to do ALL the above EACH TIME the kernel is  updated.
Networking works perfectly for me on my ASUS 1005PE now

---

### Post by robertfullarton on 2010-06-11
The built in microphone doesn't seem to work but if you install the pulseaudio device chooser and adjust either the left or right mic levels to minimum it does indeed work. It's as if one of the mic channels is inverted and cancels out the other.

---

### Post by attilab on 2010-06-11
interestingly, I've installed the netbook remix (currently 10.04) to a dual boot on my Asus Netbook EEE 1005P (purchased about May 2010), and all functioned well out of the box. OK, the screen is flickering sometimes (not allways) but my ubuntu knowledge is not there that I will start troubleshooting, 
before installing ubuntu, I've loaded the W7 first, update the BIOS,  update all the drivers, cut all from W7 what I wouldn't need at all, repartitioned the HDD, than finally installed the UNR. since I didn't even opened the W7.
One thing, the blue FN key for sound + or - is not working, but that is not my concern at all.

---

### Post by james_fried on 2010-06-26
Thanks to gregpritchard for the excellent guide!

@robertfullarton, @attilab

does this mean that you guys got 10.4 running on your 1005P and are happy with it?

---

### Post by dionblundell on 2010-06-30
Yes, I do have Ubuntu 10.04 working fine on my 1005PE.
Two things to get it working are:
1) acpi_osi=Linux   (this makes brightness work)
2) compiled wireless drivers so that wireless works
I should be noted: That it works so well that this is my only computer, I use it every day. The battery life is amazing. For long term work, I plug a LCD screen, keyboard and mouse.

That said, the netbook version constantly crashes for me. The programme that has all of the icons becomes unresponsive. I've given up on the Netbook launcher. Instead at the login screen I tell it to login as Gnome, rather that Netbook. Incidentally, the 2D version still crashes... sigh.

At the moment, my favourite version is Ubuntu Mint
[http://www.linuxmint.com](http://www.linuxmint.com)

---

### Post by th13teen on 2010-07-05
Hey guys,

I installed 10.04 onto my eee pc 1005p, but I've been unable to get the wireless to start working.

I've tried all the solutions in this thread (the nethatw.inf and nethatwx.inf - both were invalid drivers when i tried installing them using the ndiswrapper)

I also tried using the the compat-wireless solution i found on a number of forums. I went through the entire process, was able to see the wireless option (disabled). I was unable to enable it, and the option would disappear after a reboot.

I'm pretty much a noob when it comes to this stuff, and I'd really appreciate any help...

Thanks...

---

### Post by th13teen on 2010-07-05
Bump

---

### Post by hoover67 on 2010-07-06
which bios version are you running?

---

### Post by hoover67 on 2010-07-06
Hi folks,

here's another hint: In order to get the "disable touchpad" function key working, you need to disable the "disable touchpad while typing" setting in the gnome control center-> mouse input settings. 

Once this setting has been disabled, the Fn-F3 key works perfectly. 

Now the only fn-key left to get working properly on the 1005p for me is the "switch off screen" key (fn-f7). 

HTH, Uwe

---

### Post by james_fried on 2010-07-16
@dionblundell - cheers for the info, hopefully I'll be able to pick one up soon and try it out.

J

---

### Post by Silveri on 2010-07-30
I managed to solve my WLAN problem on 1005P (10.4 netbook remix). Yes, I had to install ndiswrapper, and before I even started I upgraded the BIOS (luckily for me it's rather easy on the Win7 part - it's a dual-boot system)

BUT the ndiswrapper drivers kept me from connecting due to the simple "fact" that they had problems with 128 bit WEP passphrase encryption. Didn't help if I put the passphrase in HEX. What helped me there was change the main WLAN security settings to WAP2, which works like a dream (as I'm currently typing this on the 1005P on WLAN).

---

### Post by tommyolofsson on 2010-09-01
This is weird.  I updated to bios revision 1202 and installed 10.04.1 and the previously shaky function of the brightness-keys was gone. To be expected. But now the "killTheMouse"-key and the volumekeys are dead. Does anyone recognize this?

Edit: Turns out the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"** in /etc/default/grub was necessary for those functions too. The more you know. ;)

---

### Post by armanbf on 2010-10-20
> **erdalronahi said:**
> The 1005pe is a different model than the 1005p. None of these fixes work on the new 1005p.
the mic fix worked on my eee 10005pe
sweet! 
but low quality and noisy... haven't played with it much yet

---

