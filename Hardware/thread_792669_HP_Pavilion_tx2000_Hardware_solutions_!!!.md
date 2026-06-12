---
title: "HP Pavilion tx2000 Hardware solutions !!!"
date: 2008-05-13
forum: Hardware
---

### Post by G_man on 2008-05-13
I have been using Ubuntu for 2 years and I have installed it in many laptops and desktops including: HP, IBM, Dell, Acer, Toshiba & many assembled PC's

I have never find problems with drivers as much as what I had with the HP Pavilion tx2000

OS: Ubuntu Hardy (8.04) AMD64


I wanted to tell people how I managed to get through all of them (YES ALL)

1.VGA
Problem: Not Working Perfectly (Driver Problem)
Solution:Go to synaptic and install the "nvidia-glx-new" package. It will work fine after you restart the laptop.

2-Audio:
Problem: Not Working (LED indicate that it is mute)
Solution: in Terminal write the code
[PHP]sudo gedit /etc/modprobe.d/alsa-base[/PHP]
Write at the end of the file in new line:
[PHP]options snd-hda-intel model=hp[/PHP]
Save the file and the sound will work after reboot

3.Lightscribe:
Problem: Not Working (Need Driver and Application)
Solution: Download the following packages and install them:
Driver: [lightscribe-1.12.37.1-linux-2.6-intel.deb]("http://download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb")
Software: [lightscribeApplications-1.10.19.1-linux-2.6-intel.deb]("http://download.lightscribe.com/ls/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb")
Additional Links:
[Template Label Gallery]("http://www.lightscribe.com/ideas/index.aspx?id=1540")
[Label Gallery]("http://www.lightscribe.com/ideas/labelgallery.aspx?id=219")


4.Fingerprint:
Problem: Not Working (Detected but does not work when you log in)
Solution: You need three packages & since one or two of them are not available in Synaptic you can get them here: [http://legacy.madman2k.net/comments/105](http://legacy.madman2k.net/comments/105)
The packages are: libfprint, pam_fprint and fprint_demo.
Then Write in the Terminal:
[PHP]tar -xjf libfprint-0.0.4.tar.bz2
cd libfprint-0.0.4
./configure --prefix=/usr
make
sudo make install
[/PHP]
and repeat it again for pam_fprint and fprint_demo.

5-Wireless:
Problem: Detected but not working at all
Solution:
A.install ndiswrapper packages:
[PHP]sudo apt-get install ndiswrapper-utils
sudo apt-get install ndiswrapper-common[/PHP]
B.[Download this driver]("http://h18000.www1.hp.com/support/files/hpcpqnk/us/download/24001.html")
C.Open the Terminal and write:
[PHP]sudo cabextract SP34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
sudo gedit /etc/modules[/PHP]
Write at end of that file: "ndiswrapper" and It should be working without reboot


6.WACON "Touch Screen"
This is very new & I worked very hard to find it BUT after finding it and fighting to install it I found that neko18 wrote a new Thread all about it and it was the first topic in front if me when I came to post mine.
Link: [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)
"Thanks & I wish I have found your topic an hour ago."

7.Monitor Rotation:
Problem: Not working
Solution:I need more time to check it fully
I Found this helpful link: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Thank you

---

### Post by cespinal on 2008-05-13
does the tx has integrated mic? dos your solution helped to enable it? 

aaaand... what about suspend and hibernate? :D 

last question, I would like to get lightscribe software! would you please tell me the exact codes for installing all that from terminal? Im a total noob a that :lolflag:

Thank you very much in advance for your help.

---

### Post by rebshalom on 2008-05-13
Will your audio solution also make my headphones work?
I just installed Hardy on my tx1320 and the speakers work at VERY low volume, but the headset(and attached mic) do not

---

### Post by cespinal on 2008-05-13
yeah that is a total pain in the A... dont get me wrong.. for me, the advantages Ubuntu offers far surpass the disadvantages...so in keeping myself happy despite the eventual frustrations...

---

### Post by G_man on 2008-05-14
For the records these are not my solutions, I went through many websites and did lots of searches. Then, I brought to you what worked with me

As for the sound check the Audio section in this page:
[http://www.codepencil.com/index.php/installing-ubuntu-gutsy-gibbon-on-my-hp-tx1003au-laptop/](http://www.codepencil.com/index.php/installing-ubuntu-gutsy-gibbon-on-my-hp-tx1003au-laptop/)

This will get the front jacks to work "If they are not already working"

Sorry guys the Mic works by default

cespinal: These are Debian packages = double click on them, press install & That's it

rebshalom: I am not sure

cespinal: I installed Ubuntu in 5 HP's, 4 Toshiba's, 2 acer's, 3 IBM's, 5 Dell's (This was the first one I had driver problems with. Unlike Windows, Ubuntu usually do the dirty job for me.)

I do not own this laptop, I just installed it and tried to get everything to work. The device is gone now and I can't test anything anymore

I noticed that the Wacom solution may not work, I will look for what I used and post it here as well.

Thank you

---

### Post by Zólhos on 2008-05-27
> **G_man said:**
> I have been using Ubuntu for 2 years and I have installed it in many laptops and desktops including: HP, IBM, Dell, Acer, Toshiba & many assembled PC's

I have never find problems with drivers as much as what I had with the HP Pavilion tx2000

OS: Ubuntu Hardy (8.04) AMD64

I'm using Ubuntu Hardy 32 bits

> 
I wanted to tell people how I managed to get through all of them (YES ALL)

1.VGA
Problem: Not Working Perfectly (Driver Problem)
Solution:Go to synaptic and install the "nvidia-glx-new" package. It will work fine after you restart the laptop.

For this driver, ctrl+alt+f1 doesn't work with me. Also, when the screen turns off (power saving), to go back I have to move the mouse AND press ctrl+alt+f1 and then ctrl+alt+f7.

The nv driver doesn't have these bugs, but it has even MORE bugs.

Haven't tried the nouveau driver yet.

> 
2-Audio:
Problem: Not Working (LED indicate that it is mute)
Solution: in Terminal write the code
[PHP]sudo gedit /etc/modprobe.d/alsa-base[/PHP]
Write at the end of the file in new line:
[PHP]options snd-hda-intel model=hp[/PHP]
Save the file and the sound will work after reboot

I also had to go to the alsamixer and increase the volume!

Did you make the microphone work?

> 
4.Fingerprint:
Problem: Not Working (Detected but does not work when you log in)
Solution: You need three packages & since one or two of them are not available in Synaptic you can get them here: [http://legacy.madman2k.net/comments/105](http://legacy.madman2k.net/comments/105)
The packages are: libfprint, pam_fprint and fprint_demo.
Then Write in the Terminal:
[PHP]tar -xjf libfprint-0.0.4.tar.bz2
cd libfprint-0.0.4
./configure --prefix=/usr
make
sudo make install
[/PHP]
and repeat it again for pam_fprint and fprint_demo.

The last time I tried it, gksu and some other applications were not working because of bugs on them (gksu and others, not the fprint package)

> 
5-Wireless:
Problem: Detected but not working at all
Solution:
A.install ndiswrapper packages:
[PHP]sudo apt-get install ndiswrapper-utils
sudo apt-get install ndiswrapper-common[/PHP]
B.[Download this driver]("http://h18000.www1.hp.com/support/files/hpcpqnk/us/download/24001.html")
C.Open the Terminal and write:
[PHP]sudo cabextract SP34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
sudo gedit /etc/modules[/PHP]
Write at end of that file: "ndiswrapper" and It should be working without reboot

I read somewhere that our wireless driver should be working natively on linux now. Haven't tried. Ndiswrapper driver works fine.

> 
6.WACON "Touch Screen"
This is very new & I worked very hard to find it BUT after finding it and fighting to install it I found that neko18 wrote a new Thread all about it and it was the first topic in front if me when I came to post mine.
Link: [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)
"Thanks & I wish I have found your topic an hour ago."

Is there any application to do the handwriting like in Windows? =P

> 
7.Monitor Rotation:
Problem: Not working
Solution:I need more time to check it fully
I Found this helpful link: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Thank you

This is my driver section in xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
        Option          "RandRRotation" "On"
        #Driver         "nv"
EndSection

to rotate the screen do something like this:
$ xrandr --output default --rotate inverted

One thing that I noted:
Every time that I press the button to disable the touchpad, when I press it again to enable, gnome help window opens (as if I pressed f1). Do you guys see this too?

And... How much time does the battery works with you guys? Mine is 2:30 with ndiswrapper + compiz

What do you think about the screen? I didn't like the screen quality, specially when I'm reading black text on a white background (like this forum). Black as background with white text is fine.

---

### Post by danai on 2008-06-05
For Wireless Driver after the command ::: sudo ndiswrapper -m
I found "module configurution already contain alias directive" what it meaning. Please suggest me.

---

### Post by Trivia89 on 2008-06-06
G_man can you post your solution for the touchscreen?
I did as suggested in the other topic but, in the end, i got no /dev/input/wacom device and nothing was working.
So i took a look on the net and discovered the touch screen should be serial, so i launched a script wich would "expose" the screen to ttyS2 and then configured xorg.conf to look on that device, but i've also got errors in xorg.0.log...

How did you do? Thanks for the useful post

---

### Post by mirosol on 2008-06-24
Here's howto that i've made for ubuntu and this machine.
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)
It's just extended translation of my thread in finnish ubuntu forums, but i think there's everything.

---

### Post by TheeWasp on 2008-07-02
> **mirosol said:**
> Here's howto that i've made for ubuntu and this machine.
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)
It's just extended translation of my thread in finnish ubuntu forums, but i think there's everything.

thank you a lot even I managed to fix most problems with your help

---

### Post by nameGoesHere on 2008-07-11
> **mirosol said:**
> Here's howto that i've made for ubuntu and this machine.
[http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm)
It's just extended translation of my thread in finnish ubuntu forums, but i think there's everything.

Thanks, following your guide I was able to get 99% of my precious tx2000 up and running.

The last 1% that still bugs me is:

When I add the "noapic nolapic irqfixup" parameters to the kernel, suspend and resume works like a charm, but now the processor scaling is acting up. The Ondemand governor just jumps straight to the highest frequency and stays there and the Conservative governor just climbs down to 800MHz no matter what the load.

Any one else noticed this behavior?

---

### Post by vishalrao on 2008-07-12
Can anyone post what is the fingerprint reader model on the tx2000 series? Is it supported by latest fprint code? My older tx1000 series tablet has the AuthenTec AES 1610 fingerprint reader...

---

### Post by dharivs on 2008-07-13
> **vishalrao said:**
> Can anyone post what is the fingerprint reader model on the tx2000 series? Is it supported by latest fprint code? My older tx1000 series tablet has the AuthenTec AES 1610 fingerprint reader...
Hi vishalrao,

I have one tx2000es and its fingerprint reader is AuthenTec AES1610, as your tx1000 series.

It works quite well, but there is no way to get a valid print which validates against the enrolled one.

Now I'm looking for two things:
  - Lower load cycle count: it was at 200!! With hdparm -B 255 it works well, but the hdd gets a little hotter than usual.
  - Life battery: I cannot get more than one hour and half of battery life.

I installed powertop from Intel and I get that the 50% of consumption comes from ehci_hcd:usb2, which is this: "Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7c65640 USB-2.0 "Tetrahub"".

---

### Post by Robotex on 2008-07-14
Hi! I use AuthenTec AES1610 fingerprint scanner, but it's doesn't work in Ubuntu.

---

### Post by kjamo36 on 2008-07-27
kjam@kjam:~$ sudo apt-get install ndiswrapper-utils
[sudo] password for kjam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
-------------------------------------------------------------------------------------
im trying to enable wireless but i keep getting this and im stuck here....help!

---

### Post by gali98 on 2008-07-27
I have written a short tutorial on how to get the stylus and touchscreen working with a new version of linuxwacom made for Usb tablets.
This way you don't have to apply patches....
go here to see
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
Kory

---

### Post by the_wayfarer_2000 on 2008-09-01
> **kjamo36 said:**
> kjam@kjam:~$ sudo apt-get install ndiswrapper-utils
[sudo] password for kjam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
-------------------------------------------------------------------------------------
im trying to enable wireless but i keep getting this and im stuck here....help!

I had a similar issue.  Here's how I got around it.  I'm new to Linux, so hopefully this solution works.

1) Make sure you have an internet connection.  I actually did not realize I needed this (I was going to use a USB thumb drive to transfer over install files).  The ethernet port should work out of the box with Ubuntu.

2) Update your repository list.  You can follow these instructions or do some research on repositories, if you need to.
[INDENT]A. Open Synaptic Package Manager.  Go to Settings -> Repositories.  On "Third-Party Software" tab check all of those boxes to include those repositories.  Ubuntu may require you to update at this point; I forgot.
[/INDENT]
[INDENT]B. Also, I just added a bunch of repositories to my computer thru the instructions provided _[here]("http://mathpages.blogspot.com/2008/04/ubuntu-hardy-repositories-list.html")_.  The instructions includes repositories that are not official, so use at your own risk.  One of the commands on that page didn't work for me.  I needed to add a hyphen at the end of the command, so this line:
[PHP]sudo gpg --export --armor KEY | sudo apt-key add[/PHP]
became:
[PHP]sudo gpg --export --armor KEY | sudo apt-key add -[/PHP]
[/INDENT]
Some of the GPG keys didn't work for me, but that didn't affect my system detrimentally.

3) Update your computer.  This should, amongst many other things, automatically add cabextract to your computer.

3.5) I think that these updates might update your kernel.  Because of this, in my case, I had to reinstall my nvidia drivers.

4) At this point, I still could not install the ndiswrapper pacakges through the command line.  However, I *was* able to install them through synaptic (Applications -> System -> Synaptic Package Manager).  Search for ndiswrapper, and install them.

I also found a more complete guide to install ubuntu on the HP tx2000 series _[here]("http://mirosol.kapsi.fi/tx2020/tx2000howto.htm")_.

---

### Post by Goldford on 2008-09-17
Hello All, 

I am just getting to know this new laptop and want to wipe off Vista ASAP.  The CPU load jumps to 80 - 90% with three tabs open and viewing one youtube video in Firefox! shameful. 

However, I do not know what I am doing whatsoever with Ubuntu. I would hit a wall every 5 minutes and I know what they say: "If you don't know what you're doing, don't do it." Is there any way all these hardware fixes could be put together into some kind of patch/installer program?  I wouldn't mind contributing a reasonable amount ($) if it were possible.  I know this sounds lazy but, as I said, by reading through these forums I have a snowball's chance of getting this up and running.

---

### Post by i messed up on 2008-09-17
thanks this help some :popcorn:

---

### Post by gali98 on 2008-09-17
> **Goldford said:**
> Hello All, 

I am just getting to know this new laptop and want to wipe off Vista ASAP.  The CPU load jumps to 80 - 90% with three tabs open and viewing one youtube video in Firefox! shameful. 

However, I do not know what I am doing whatsoever with Ubuntu. I would hit a wall every 5 minutes and I know what they say: "If you don't know what you're doing, don't do it." Is there any way all these hardware fixes could be put together into some kind of patch/installer program?  I wouldn't mind contributing a reasonable amount ($) if it were possible.  I know this sounds lazy but, as I said, by reading through these forums I have a snowball's chance of getting this up and running.

I suppose it would be possible, but it would be quite an undertaking, and it would change as updates come out. It would be difficult to maintain and hardware differences would pose a problem....
I have thought about it myself, but I do not have enough time, and wouldn't have time to troubleshoot all the problems that would arise from it.
It really doesn't take a whole lot of time to get most of it working.
Mainly plug into an ethernet jack and update everything.
Then use hardware drivers to get graphics and wireless.
Then put the line 

options snd-hda-intel model=hp

into /etc/modprobe.d/alsa-base

to get sound working.
to get the tablet working follow my tutorial:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

and that gets most everything working....
When Intrepid comes out, I may undertake such a task if I have time, but I doubt I will...

Kory

---

### Post by Goldford on 2008-09-18
> **gali98 said:**
> I suppose it would be possible, but it would be quite an undertaking, and it would change as updates come out. It would be difficult to maintain and hardware differences would pose a problem....
I have thought about it myself, but I do not have enough time, and wouldn't have time to troubleshoot all the problems that would arise from it.
It really doesn't take a whole lot of time to get most of it working.
Mainly plug into an ethernet jack and update everything.
Then use hardware drivers to get graphics and wireless.
Then put the line 

options snd-hda-intel model=hp

into /etc/modprobe.d/alsa-base

to get sound working.
to get the tablet working follow my tutorial:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

and that gets most everything working....
When Intrepid comes out, I may undertake such a task if I have time, but I doubt I will...

Kory

Thanks Kory, 

I will give it a try sometime soon.  

Greig

---

### Post by getifax on 2008-10-03
> **nameGoesHere said:**
> Thanks, following your guide I was able to get 99% of my precious tx2000 up and running.

The last 1% that still bugs me is:

When I add the "noapic nolapic irqfixup" parameters to the kernel, suspend and resume works like a charm, but now the processor scaling is acting up. The Ondemand governor just jumps straight to the highest frequency and stays there and the Conservative governor just climbs down to 800MHz no matter what the load.

Any one else noticed this behavior?

Well i guess nobody else is helping us out here bud.  i got the same problem, and yeah it's pretty much the last thing i'm still losing swimming time over.  i tried removing some of the parameters... the one that seemed to fix the suspend issue was irqfixup, i used just that one and i could suspend no problem.  unfortunately the processor was also churning when I used just that one.
i've uninstalled powernowd and installed cpufreqd and tweaked the parameters... the same thing is happening, with the progression that when the cpu overheats every couple seconds (default was 55 celsius, i upped it to 64) it drops it down to 800 for a little while.  i might just need to fix the settings, or i might just need to do something way more elegant to make my laptop stop behaving like a candyraver.  the other thing you can do is set the cpu frequency manually with cpufreq-set.  which feels kind of like knocking out & then building a wall a few times a day instead of just using the door.
does anybody else here know what to do about this?  We're tryin to save the planet here.
i limited it to 1.80 rather than its default 2.2 GHz using $ cpufreq-set -u 1800000.  so now it just uses that speed as much as possible, even though cpufreq-info says
```
$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, powersave, userspace, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.80 GHz.
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.20 GHz
  available frequency steps: 2.20 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, powersave, userspace, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.80 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.80 GHz.

```


Also to the guy having trouble installing ndiswrapper... while it is certainly invigorating to wade steeltoe-first into the exciting world of installing pgp keys, you may alternately be interested to learn that i'm using the package "ndiswrapper-utils-1.9" without having had to do that.  you might just need to specify that name.  or maybe it's just the time factor of the now version of everything being better than the then version.  in any case $ apt-cache search ndis   will tell you what related packages are available.

in general here's a summary of my success at the intersection of hp pavilion tx2110ca and ubuntu "hardy heron" 8.10 x86_64:
details: 2.2GHz Turion 64 processor, 3GB RAM.
broadcom bcm4328 a/b/n/g wireless: works with ndiswrapper and [this driver]("http://ubuntuforums.org/attachment.php?attachmentid=50636&d=1195424847").
wacom touchscreen: haven't touched it.
webcam: haven't looked at it.
fingerprint scanner: what?
nvidia MCP51 sound: sudo echo "options snd-hda-intel model=hp" >>/etc/modprobe.d/alsa-base
geForce 6150 Go: using the proprietary driver 'cause the mouse cursor disappeared one time after i hibernated and then user switched.  i think there's another fix but what ev.
suspend/hibernate: add "noapic nolapic irqfixup" to the boot options like [the man says]("http://mirosol.kapsi.fi/tx2020/tx2000howto.htm").
in general: mostly working except the cpu frequency governor is on crystal meth ever since i changed the boot options. Anyone got a fix?

-getifax

---

### Post by Obituaryfreak on 2009-04-11
Hi I tried not to post a new thread but I couldn't find my answer in the SOMEHOW RELATED posts ,so I`m posting this..
I have an HP 2070ee Tablet with the Interpid installed on it which has been running smoothly for 4 month using its internal wireless card. Its not even listed under the connection list in Network Settings and yet not connected in the lspci with the following result:
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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
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
---------
Here is my uname -a output : 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
---------
and iwconfig output:
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.
---------
The funny thing is it doesn't even exit when I left click on the two monitors.
I checked the HP web site for the Broadcom drivers and the featured ones were:Broadcom 802.11 a/b/g WLAN Broadcom 802.11 b/g WLAN Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter Broadcom 4322AG 802.11a/b/g/draft-n Wi-Fi Adapter
which are supported on my laptop.
---------
Besides I must say that I tried the ndisgtk to install the drivers (bcmwl6.inf),but was of no success it still says Hardware present:No).
Theres even no log in the dmesg output which mentions the ord WIRELESS.

2 more things which may help
he output of my lshw is :
 *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:21:be:e6:5b:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
1st thing is it doesn't show any thing about the wireless card and only shows the Ethernet card
and the 2nd thing is that the ethenet card as you can see is featured in Disabled status which is really freaking me out cuz I`m using my Ethernet connection right now sending you this thread!
please leave me a note because I`m completely nuts at the moment.

---

### Post by Obituaryfreak on 2009-04-13
> **G_man said:**
> I have been using Ubuntu for 2 years and I have installed it in many laptops and desktops including: HP, IBM, Dell, Acer, Toshiba & many assembled PC's

I have never find problems with drivers as much as what I had with the HP Pavilion tx2000

OS: Ubuntu Hardy (8.04) AMD64


I wanted to tell people how I managed to get through all of them (YES ALL)

1.VGA
Problem: Not Working Perfectly (Driver Problem)
Solution:Go to synaptic and install the "nvidia-glx-new" package. It will work fine after you restart the laptop.

2-Audio:
Problem: Not Working (LED indicate that it is mute)
Solution: in Terminal write the code
[PHP]sudo gedit /etc/modprobe.d/alsa-base[/PHP]
Write at the end of the file in new line:
[PHP]options snd-hda-intel model=hp[/PHP]
Save the file and the sound will work after reboot

3.Lightscribe:
Problem: Not Working (Need Driver and Application)
Solution: Download the following packages and install them:
Driver: [lightscribe-1.12.37.1-linux-2.6-intel.deb]("http://download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb")
Software: [lightscribeApplications-1.10.19.1-linux-2.6-intel.deb]("http://download.lightscribe.com/ls/lightscribeApplications-1.10.19.1-linux-2.6-intel.deb")
Additional Links:
[Template Label Gallery]("http://www.lightscribe.com/ideas/index.aspx?id=1540")
[Label Gallery]("http://www.lightscribe.com/ideas/labelgallery.aspx?id=219")


4.Fingerprint:
Problem: Not Working (Detected but does not work when you log in)
Solution: You need three packages & since one or two of them are not available in Synaptic you can get them here: [http://legacy.madman2k.net/comments/105](http://legacy.madman2k.net/comments/105)
The packages are: libfprint, pam_fprint and fprint_demo.
Then Write in the Terminal:
[PHP]tar -xjf libfprint-0.0.4.tar.bz2
cd libfprint-0.0.4
./configure --prefix=/usr
make
sudo make install
[/PHP]
and repeat it again for pam_fprint and fprint_demo.

5-Wireless:
Problem: Detected but not working at all
Solution:
A.install ndiswrapper packages:
[PHP]sudo apt-get install ndiswrapper-utils
sudo apt-get install ndiswrapper-common[/PHP]
B.[Download this driver]("http://h18000.www1.hp.com/support/files/hpcpqnk/us/download/24001.html")
C.Open the Terminal and write:
[PHP]sudo cabextract SP34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper
sudo gedit /etc/modules[/PHP]
Write at end of that file: "ndiswrapper" and It should be working without reboot


6.WACON "Touch Screen"
This is very new & I worked very hard to find it BUT after finding it and fighting to install it I found that neko18 wrote a new Thread all about it and it was the first topic in front if me when I came to post mine.
Link: [http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)
"Thanks & I wish I have found your topic an hour ago."

7.Monitor Rotation:
Problem: Not working
Solution:I need more time to check it fully
I Found this helpful link: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Thank you

dude your wireless solution doesnt work for me :mad:
its been 3 days with no wireless and only ethernet cable(stuck in ma room)
and its too frustrating...
My laptop is hp tx 2070 ee tablet pc...
and I`m nuts..

---

### Post by brainsqueezer on 2009-05-12
Nobody had overheat problems?

If so please tell. I have created a discussion group on this topic at [http://groups.google.com/group/tx2000-overheat](http://groups.google.com/group/tx2000-overheat).

---

### Post by correaa on 2009-05-19
> **brainsqueezer said:**
> Nobody had overheat problems?

If so please tell. I have created a discussion group on this topic at [http://groups.google.com/group/tx2000-overheat](http://groups.google.com/group/tx2000-overheat).

Yes, I had when I switched to Jaunty. But later I realized that it was a combination of Jaunty power management AND a dusty fan. 
Initially I tried to open the laptop case to clean the fan but I couldn't. Later I tried blowing very hard through it and everything solved. It used to reach 92 Celsius and Ubuntu shuting down. Now after cleaning it is (at most) ~80 Celsius.

---

### Post by Favux on 2009-05-19
Hi brainsqueezer and correaa,

Some TX2500 users said installing guidance-power-manager through Synaptics helped.

And marranzano went to the extreme of changing his dsdt on post #554 here:  [http://ubuntuforums.org/showthread.php?t=845911&page=56](http://ubuntuforums.org/showthread.php?t=845911&page=56)  This may apply to our TX2000's.

---

### Post by Favux on 2009-08-07
Hi everyone,

We figured out how to get auto-magic rotation (swivel hinge) for the TX2000 (works for TX2500 and TX2z too).  See HOW TO on post #225 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=23](http://ubuntuforums.org/showthread.php?t=996830&page=23)  And a little more info. on the first page HOW TO.

---

### Post by brainsqueezer on 2009-08-23
Anybody had problems with latest nvidia drivers (185.18.31)?

[http://www.nvnews.net/vbulletin/showthread.php?t=137772](http://www.nvnews.net/vbulletin/showthread.php?t=137772)

---

### Post by themattbeballin on 2009-09-25
I'm kinda resurrecting an older thread here.. But my sister has a HP Pavilion TX2000 machine... 

She ended up taking her first Linux class as part of her PC Operating Systems class and when she gets home says, "You're putting Linux on my PC."

Well. I gotten to the part about the fingerprint reader... The link that is provided does not work.. is anyone able to provide an alternative so I can get her computer back to her sometime in the near future.. She used this fingerprint reader CONSTANTLY in Vista and I'd hate to deprive her of it.

-Matt

EDIT: FRIDAY SEPTEMBER 25, 03:00:45 CDT

I also could not seem to get through with the Wacom touchscreen either... This laptop is a true pain in the ***. lol.

---

### Post by Favux on 2009-09-25
Hi themattbeballin,

To get the TX2000 working in Jaunty use gali98's Jaunty HOW TO.  See Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)  And follow the link in 1) to post #104 (the HOW TO).

I think the link was indirect to the fprint site.  Here's the fprint site directly:

[http://reactivated.net/fprint/wiki/Main_Page](http://reactivated.net/fprint/wiki/Main_Page)

And a couple other fingerprint links:

[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

[http://www.pdfserver.net/fingerprint/index.php](http://www.pdfserver.net/fingerprint/index.php)

Hope this is helpful.

---

### Post by themattbeballin on 2009-09-25
Apparently I'm not that good at compiling and installing source... or following HOWTOs for that matter.

I was still unable to get either one of these to work... Turns out this is a TX2500 and not a TX2000.. It says TX2000 on the screens so I figured thats what it was... until I decided to look at the bottom.

---

### Post by Favux on 2009-09-25
Hi themattbeballin,

That's OK.  It works for the TX2500 too.

---

### Post by themattbeballin on 2009-09-25
I realized that but here's the thing...

I am still unable to get the Wacom touchscreen or the fingerprint reader to work.. I don't know what I am doing wrong..


i might be able to get the fingerprint reader to work if I knew what kinda of fingerprint reader that it is.. Is there a way that i can figure that out?

---

### Post by Favux on 2009-09-26
Hi themattbeballin,

Enter in a terminal:
```
lsusb
```
I think it's an "AuthenTec, Inc. AES1600".  Then you can search with that.  This thread is good:  [http://ubuntuforums.org/showthread.php?t=845911](http://ubuntuforums.org/showthread.php?t=845911)   Then use the Search Thread tool top right.  You'll see posts, for example post #339 here:  [http://ubuntuforums.org/showthread.php?p=6095114&highlight=fingerprint#post6095114](http://ubuntuforums.org/showthread.php?p=6095114&highlight=fingerprint#post6095114)

I'm not sure why you aren't getting the tablet working.  You haven't provided any details.  Gali98's HOW TO seems fairly straightforward to me.  And in Jaunty it's likely that it least the stylus should have worked on boot or at least after installing the wacom.ko in Section 1.

---

### Post by themattbeballin on 2009-09-26
I went through gali98's HOWTO and I rebooted and the graphics got all funky so I had to restore the old xorg.conf file. 

The laptop seems to have ATi graphics compared to this and nVidia which I keep seeing everywhere.

---

### Post by Favux on 2009-09-26
Hi themattbeballin,

Gali98's HOW TO shouldn't affect graphics.  Did you do something with your xorg.conf?  You don't need to change the xorg.conf for linuxwacom in Jaunty.  That's handled by HAL/.fdi.

Are you using the ATI proprietary driver "fglrx"?  For rotation you need to run the aticonfig command in Appendix 1 here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

---

### Post by themattbeballin on 2009-09-26
Wait... It wasn't the gali98 tutorial that did that.. I did go through gali98's tutorial but I rebooted.. and nothing happened.

---

### Post by Favux on 2009-09-26
Hi themattbeballin,

You're not telling me enough to figure out what's going on.

When you did gali98's Jaunty HOW TO were there any problems?  Or did everything go smoothly without error messages?

In Synaptics Package Manager are both 0.8.2-2 linuxwacom packages installed?:  wacom-tools & xserver-xorg-input-wacom  If not install whichever is missing and reboot.

Try entering in a terminal:
```
dmesg | grep [Ww]acom
```
You should see several lines with wacom stuff in the output.  If so post the output.

---

### Post by themattbeballin on 2009-09-26
Yes, on gali98s tutorial everything went smoothly but the touchscreen still didn't work..

```
shaunna@shaunna-laptop:~$ dmesg | grep [Ww]acom
[   14.734958] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input8
[   14.750912] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input9
[   14.756654] usbcore: registered new interface driver wacom
[   14.756677] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver
shaunna@shaunna-laptop:~$ 

```That's the output I got via her SSH terminal since she is not home and I can not access her laptop.

---

### Post by Favux on 2009-09-26
Hi themattbeballin,

Well usb communication is established to the Wacom tablet so you should at least have the stylus working.

So next you need to establish that both the default Jaunty 0.8.2-2 linuxwacom packages are installed.  If it says they are tell Synaptic to reinstall them and reboot.  This assumes you haven't tried to compile and install another version of linuxwacom or put any wacom stuff in xorg.conf, and the only wacom.fdi you've installed is the one gali98 showed you in his HOW TO.

You can use Places (Nautilus) to navigate to the 10-wacom.fdi and right click on it and select Text Editor (gedit) to establish that you've installed it correctly.  If so then in a terminal:
```
xsetwacom
```
should return stylus, eraser, and touch.  If not enter:
```
xinput --list
```
to see what HAL/dBus is calling your wacom devices.

---

### Post by themattbeballin on 2009-09-27
Well this is what I got from her "xinput --list" command

```
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=5    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1

```


This might actually say something to you.. but this is just words to me.

---

### Post by Favux on 2009-09-27
Hi themattbeballin,

It's saying that your tablet is not showing to Xinput/Xserver.  So there is usb connection but then things are broken somewhere.

Please review my last post and answer the questions.

---

### Post by themattbeballin on 2009-10-10
Okay, so I have now gotten ahold of her PC and and I did I search in Nautilus for the 10-wacom.fdi and found it... 


It gave me the following output in Firefox when I opened it. 

```
<!-- -*- SGML -*- -->
&#8722;
<deviceinfo version="0.2">
&#8722;
<device>
&#8722;
<match key="input.originating_device" contains="if0">
&#8722;
<match key="info.product" contains="Wacom">
<merge key="input.x11_driver" type="string">wacom</merge>
<merge key="input.x11_options.Type" type="string">stylus</merge>
<merge key="info.product" type="string">stylus</merge>
<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
<append key="wacom.types" type="strlist">eraser</append>
</match>
</match>
</device>
&#8722;
<device>
&#8722;
<match key="input.originating_device" contains="if1">
&#8722;
<match key="info.product" contains="Wacom">
<merge key="input.x11_driver" type="string">wacom</merge>
<merge key="input.x11_options.Type" type="string">touch</merge>
<merge key="info.product" type="string">touch</merge>
</match>
</match>
</device>
&#8722;
<device>
&#8722;
<match key="input.x11_options.Type" contains="eraser">
<merge key="info.product" type="string">eraser</merge>
</match>
</device>
</deviceinfo>
```What else do I need to do?

-Matt

---

### Post by Favux on 2009-10-10
Hi themattbeballin,

Well that looks like the right wacom.fdi.  Is that at "/usr/share/hal/fdi/policy/20thirdparty/"?  If so then "xsetwacom list" in a terminal should be returning stylus, eraser, and touch.  Is it?

---

### Post by themattbeballin on 2009-10-14
> **Favux said:**
> Hi themattbeballin,

Well that looks like the right wacom.fdi.  Is that at "/usr/share/hal/fdi/policy/20thirdparty/"?  If so then "xsetwacom list" in a terminal should be returning stylus, eraser, and touch.  Is it?

Okay so I made sure the files were in the 20thirdparty folder and then ran xsetwacom list and got the following.

```
shaunna@shaunna-laptop:/usr/share/hal/fdi/policy/20thirdparty$ ls
10-wacom.fdi   11-x11-synaptics.fdi             20-podsleuth.fdi
10-wacom.fdi~  20-libgpod-sysinfo-extended.fdi
shaunna@shaunna-laptop:/usr/share/hal/fdi/policy/20thirdparty$ xsetwacom list
Failed to open display ()

```

Now I'm thinking the ```
Failed to open display ()
``` might be because I was running this from an SSH terminal? or should it give me the same response either way?

---

### Post by themattbeballin on 2009-10-15
Okay I ran it locally from the actually machine, not over an SSH Terminal.. and I got the following... 

```
shaunna@shaunna-laptop:~$ xsetwacom list
shaunna@shaunna-laptop:~$
```

Something tells me it's missing something.. Like what you said it should return.

---

### Post by Favux on 2009-10-15
Hi themattbeballin,

'xsetwacom list' will stay blank until 'xinput --list' is returning stylus, eraser, and touch.  Check on the .fdi again and make sure it's in the right place with the correct contents.  I'm wondering if you don't have a permission problem and it (the modified one) hasn't been installed.  Remember if you remove or reinstall the linuxwacom packages (wacom-tools) the modified .fdi will be overwritten.  You have to either reboot or restart HAL after changing the .fdi.

---

### Post by djchandler on 2009-10-17
Big thank you to G_man for getting this thread going. Seldom do you read the first post in a thread and find exactly what you're looking for. Great job.

Thought I was going to need to pull my Lightscribe  capable HP dvd740 and give it to my wife to use on her Windows 7 box. She hardly ever burns DVDs/CDs let alone having the patience to use the Lightscribe function.

Mine is one of the first offered by HP. Have they gotten any faster?

---

### Post by themattbeballin on 2009-10-21
> **Favux said:**
> Hi themattbeballin,

'xsetwacom list' will stay blank until 'xinput --list' is returning stylus, eraser, and touch.  Check on the .fdi again and make sure it's in the right place with the correct contents.  I'm wondering if you don't have a permission problem and it (the modified one) hasn't been installed.  Remember if you remove or reinstall the linuxwacom packages (wacom-tools) the modified .fdi will be overwritten.  You have to either reboot or restart HAL after changing the .fdi.

Okay, so I went through the tutorial on her computer again..

'xinput --list 'is still coming up with nothing.

---

### Post by Favux on 2009-10-21
Hi themattbeballin,

Not making much sense.  Wacom showed up in dmesg back a few posts.  So we don't need to add 'wacom' to the modules file in "/etc/modules".

What you could try is the following.  Go into Synaptic Package Manager and right click on wacom-tools and telling it to reinstall it.  For good measure you might as well do that with xserver-xorg-input-wacom also.  Reboot.

That will over write the modified wacom.fdi with the default one.  It will may replace the wacom.ko too.  Probably not since it is linux-image, but.  So you'll need to redo gali98's tutuorial again.  Compile 0.8.4-3 to get the wacom.ko and copy it into place and replace the default .fdi with the modified one.  See if after a reboot that straightens things out.  If you want to try it that is.

---

