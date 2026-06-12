---
title: "Acer Aspire 5310 problems with Ubuntu"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by cumbulak on 2007-08-23
I have installed Ubuntu 7.04 on Acer Aspire 5310, most things seem to work, but several devices are unavailable:
- no sound from the soundcard
- wifi not working
- web camera not working (but this is not crucial, I can live without it :-) )
- card reader not working
- not sure if S-Video is working (what is the way to test it?)
- acer buttons do nothing (but this is also not too harming :-) ))

Has anybody succesfully installed Unbuntu on this Acer and solved the issues?

Thanks in advance for any advice.

cumbulak

---

### Post by E_K on 2007-08-23
i have the acer extensa 5210, which i can find minimal info about, not even on the acer website, i bought the laptop at the start of the month, and started with the same problems as you, most of which i have solved, still working on the bluetooth and the s-video, not tested the card reader yet, PM your MSN addy if you have one, maybe we can chat there

---

### Post by cumbulak on 2007-08-23
We may compare the HW:

this is what I found in the Aspire 5310 after installing testing win-vista:

- things not working with linux:
Wifi: Broadcom 802.11 - BCM43xx
Sound: Realtek HD Audio(nothing more specified), but linux seems to detect it as intel something.
WebCam: Acer Crystal Eye - some Sonix with drivers of SuyinNBCam on CD, it works wit this
Modem: Winmodem (driver AcrZUn32) - not tested
Card Reader: ENE MR510 - not detected by linux
Acer HotKeys: I may have messed something with acerhk, but it did not do anything

- things working with linux:
Gigabit NIC, HDD, DVD (with sucessful burning), video (915 resolution necessary for 1280x800), mouse, touchpad, battery.

- things not tested:
S-Video, hmmmm I somehow forgot to test USB, I will have to do it.

---

### Post by E_K on 2007-08-23
i have a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card , type in lspci in a terminal and it will tell you if you have that one i can tell you how to get it working

---

### Post by cumbulak on 2007-08-23
lspc says that I have the same Wifi card. (Dell Wireless 1390 WLAN)

I have tried disabling bcm43xx driver and installing ndiswrapper + some downloaded windows driver, but without success (with bmc43xx a wifi card was displayed, but unusable, with ndiswrapper no wifi device was even displayed)

How did you succeed with your sound card? And how does feel your card-reader?

---

### Post by E_K on 2007-08-23
My Sound card works to an extent, the external ports do NOT work, which is a pain in the *** when your watching a movie with a low volume 
My card reader i have no idea i do not have anything to test it with....

but any way onto the issue

if u have a Dell 1390 this should be no probs u should have a switch for it on the front of your laptop, i have one for the bluetooth and one for wireless unltil i did this it wouldnt light up
 
If you have tried to get your wirless card working before this, this will probably not work, depending on what you have done, best to start from a clean install, if you have nothing really worth keeping on the system reinstall, i reinstalled alot when i first started using ubuntu, you got to get things wrong to learn right?

i dont know why but it seems that things worked better from the original disk, like the cube worked for starters, but the copied disk i have no idea where it came from or how it was burnt(a friend downloaded and burned it for me in work)..... just a point, but the wireless always worked,so that shouldnt be a problem.

Less of the rambling.... (should prob have less of the drinking to haha)

first do this to remove any versions of ndiswrapper you may have installed

> sudo rmmod ndiswrapper
sudo ndiswrapper -e bcmwl5
sudo apt-get remove ndiswrapper-utils

next we need compiling tools, the latest kernal headers if you dont have them already, and the source code for ndiswrapper

> 
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)

next get the latest ndiswrapper from sourceforge

> 
wget [http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz](http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz)

or [http://sourceforge.net/project/showf...group_id=93482](http://sourceforge.net/project/showf...group_id=93482)

time to untar that big ball of tarey goodness

> tar -xzvf ndiswrapper-1.47.tar.gz

now black list the useless bcm43xx firmware drivers that they try to load in the default ubuntu install

> sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist

if that gives you a permission denied give it some what for and try:

> sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit

[B][U][COLOR="Red"]
REBOOT, time to REBOOT, do not forget to REBOOT!!!!!!!!!!!!!!!!!!!!!!!![/COLOR][/U][/B]

Ok now we need to compile ndiswrapper go to the directory where you extracted it (probably home if you followed the instructions, or destructions HAHAHA only joking)

> sudo make uninstall

keep doing the above until it says some thing like no files or directories found.

then

> sudo make
sudo make install

i hope that worked without any errors, go to the directory where you have the R151517.EXE file and type

> unzip -a R151517.EXE

now go to the DRIVER directory

> sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

now if we see driver present hardware detected, we are onto a winner

next type

> sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules

you may have to reboot here i did not, ur wireless light should be on i had to press the switch on the front of mine for a couple of seconds before it lit up, and hopefully now yours works as goos as mine

try:

> sudo iwlist scanning

if it still not workingpost back with any errors you got, any any extra info you can, i will do my best to help you

---

### Post by cumbulak on 2007-08-24
Thank you for your advice. I have followed your instructions to run wifi. Now it seems to work, at least the laptop button started to react on pushing and iwlist is able to start scanning (althoug it found nothing, but it can be real situation). So I will try it somewhere elsewhere. :-)

As for sound, I tried to follow [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto), but with no success, just in the step:
options snd-hda-intel model=3stack

I could not find relevant model in the documentation, so just tried "auto" and "3stack".

Thank you for anything else you advice to test. :-)

cumbulak

---

### Post by cumbulak on 2007-08-25
I have just tested kernel 2.6.22.5... and no difference...

---

### Post by indie56 on 2007-08-25
Hello
I bought a Acer 3680. My sound card did not work. So I tried something from these forums. Go to Terminal and type in alsamixer. If a window opens then you are in luck. Then just make the selections.
Hope this helps.

---

### Post by E_K on 2007-08-26
im glad you got it working cumbulak, as for my audio i thought id give that a bash today, im working on it now so ill let you know if i get it going, id apreciate it if you could do the same :D 

My sound works, just not the mic and the jack plugs, im meant to have these options in the mixer Master, PCM, LineIn, IEC958, Digital, Ext Mic, Int Mic, Int Mic, but i only have Master and PCM

I think maybe this should be in another thread... if someone makes another one please let me know

oh and cumbulak when i tried the how to, i lost all sound, fiesty didnt even know i had a sound card :P ill let you know if i get somewhere anyways

---

### Post by cumbulak on 2007-08-27
> **indie56 said:**
> Hello
I bought a Acer 3680. My sound card did not work. So I tried something from these forums. Go to Terminal and type in alsamixer. If a window opens then you are in luck. Then just make the selections.
Hope this helps.

Everythings show fine, but there is no sound at all.... :-(

BTW: Wifi really works! :-) (with the ndiswrapper)

---

### Post by Vermind on 2007-08-27
Hello,
If anyone is still interested in the Aspire 5100 series solutions for Linux, I just wrote a HOWTO for Ubuntu Feisty on Acer Aspire 5101AWLMi and added it to TuxMobil. Check this for the solution to the integrated microphone noisiness and recording stopping between 5 to 10 minutes of starting (Very annoying in the middle of a Skype call).
[Acer Aspire 5101AWLMi HOWTO]("http://www.cs.helsinki.fi/u/lagerspe/Linux/Laptop-report.html").
Comments to me here or to my email, thanks.

--
Vermind

---

### Post by cumbulak on 2007-08-28
Thanks for advice, I will test it next week.

---

### Post by ronny_d on 2007-09-24
Hi,


About the acer aspire 5310 with Ubuntu Feisty:

what happens when you type in a terminal:


 gksudo asoundconf list

(you will be prompted for your password)

so what soundcard do you get?


And is this soundcard filled out too in the 'soundpreferences'  when you look under  'system' and then 'preferences' and then 'sound'?


Have you done this and does your sound work now? Or...?

---

### Post by ronny_d on 2007-09-24
Else...: what about this that i found on the Internet?



Bug description

I can't activate sound and wlan on my acer 5310.
This may be a result of non-disclosure contract
between acer, intel and ms.

ProblemType: Bug
Architecture: i386
Date: Sun Sep 23 14:43:15 2007
DistroRelease: Ubuntu 7.04
ExecutablePath: /usr/bin/gnome-panel
Package: gnome-panel 1:2.18.1-0ubuntu3.1
PackageArchitecture: i386
ProcCmdline: gnome-panel --sm-client-id default1
ProcCwd: /home/uwe
ProcEnviron:
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage: gnome-panel
Uname: Linux lama 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux


Hm..., i wanted to buy this "cheap" laptop and install Ubuntu Feisty Fawn, Ubuntu 7.04, on it, but now i am not so sure about that anymore... 


However: did you make the sound work or didn't you?

All the best...

---

### Post by cumbulak on 2007-09-25
Finally I had to stop tests and give the laptop to the final recipient. Last state was: at least no sound (important), wifi with ndiswrapper, no card reader (very important), no webcamera (would not bother :-) ), not fully working Acer Keys. I did not catch to test S-video output.

---

### Post by archimedes1 on 2007-09-25
Hello, i was able to install both WiFi and Sound for Aspire 5310

Wifi:

  I downloaded latest version of ndiswrapper:

[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243&release_id=541594]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243&release_id=541594")

installed it with 
  ```
make
``` 
   ```
 make install
```

then I downloaded windows xp driver for wi-fi from acer page

unziped and install with   ndiswrapper -i net5211.inf

you will need to blacklist ath_pci in /etc/modprobe.d/blacklist
```
blacklist ath_pci 
```

also add ndiswrapper to ```
/etc/modules
``` so it will start on boot

reboot linux and try ```
iwconfig 
```
wlan0 should appear,  however the signal light for wi-fi is allways turned off.



sound:
```
lspci | grep Audio
```
[HTML]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/HTML]

1. I downloaded latest alsa driver,lib and util and installed them :

```
sudo /usr/src
sudo mkdir alsa
cd alsa 
sudo cp /home/downloads/alsa-* .

 bunzip2 alsa-driver-1.0.15rc2.tar.bz2 
 sudo tar -xvf alsa-driver-1.0.15rc2.tar
 cd alsa-driver-1.0.15rc2/
 sudo ./configure --with-cards=hda-intel --with-sequencer=yes
  sudo make
 sudo make install
 chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi

 cd ..
 sudo bunzip2 alsa-lib-1.0.15rc2.tar.bz2
 sudo tar -xvf alsa-lib-1.0.15rc2.tar 
 cd alsa-lib-1.0.15rc2/
 sudo ./configure sudo make sudo make install

 cd ..
 sudo bunzip2 alsa-utils-1.0.15rc1.tar.bz2
 sudo tar -xvf alsa-utils-1.0.15rc1.tar
 cd alsa-utils-1.0.15rc1/
 sudo ./configure sudo make sudo make install
 modprobe snd-hda-intel
 modprobe snd-pcm-oss
 modprobe snd-mixer-oss
 modprobe snd-seq-oss
```

the sound didnt work so i looked deeper:

  >  cat /proc/asound/card0/codec#* | grep Codec

output:
   [HTML]Codec: Realtek ALC268
Codec: Conexant ID 2c06
[/HTML]

by looking into [HTML]cd /usr/src/alsa/alsa-driver-1.0.15rc2/alsa-kernel/Documentation/ALSA-Configuration.txt[/HTML]

i found out that ALC0268 was not supported yet.

so i looked at mercurial project at found in change log patch for ALC0268 so:
```

sudo apt-get install mercurial
sudo hg clone http://hg-mirror.alsa-project.org/alsa-driver alsa-driver

```
then I **rebuild alsa sources** again, and after reboot the sound worked for me!!!

[/HTML]

---

### Post by cumbulak on 2007-09-27
You seem to have solved it. I tried mercurial few weeks ago, but probably mismanaged something, so it did not work. Unfortunately now I don have the laptop at my disposal, so I am not able to reproduce your  advice. :-(
BTW: did you manager to connect the S-video to a TV?

---

### Post by westdam on 2007-10-07
hi, i've got the same laptop. ( acer aspire 5310 )  anyone was able to install 
a) wifi card succesfully. ( cant find the XP drivers.. acer doesnt provide it on ftp site ) 
b) sound card 

( i try to set up the 2 things above just reading better the post above ) 

anyone was able to setup

c) card reader
d) set correct video resolution ( continue to use 1024x768 ).

anyone can help me?? 

thanks!

---

### Post by westdam on 2007-10-07
> **ronny_d said:**
> Else...: what about this that i found on the Internet?



Bug description

I can't activate sound and wlan on my acer 5310.
This may be a result of non-disclosure contract
between acer, intel and ms.

ProblemType: Bug
Architecture: i386
Date: Sun Sep 23 14:43:15 2007
DistroRelease: Ubuntu 7.04
ExecutablePath: /usr/bin/gnome-panel
Package: gnome-panel 1:2.18.1-0ubuntu3.1
PackageArchitecture: i386
ProcCmdline: gnome-panel --sm-client-id default1
ProcCwd: /home/uwe
ProcEnviron:
 PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 LANG=en_US.UTF-8
 SHELL=/bin/bash
SourcePackage: gnome-panel
Uname: Linux lama 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux


Hm..., i wanted to buy this "cheap" laptop and install Ubuntu Feisty Fawn, Ubuntu 7.04, on it, but now i am not so sure about that anymore... 


However: did you make the sound work or didn't you?

All the best...

hi ronny

i think acer have done this for sure..
a cheap 389€ laptop,with ubuntu it's a GREAT laptop so i think in acer have choose the correct ;) device to grant a hard-way installation of ubuntu

---

### Post by westdam on 2007-10-07
mmm

my vga chipset is intel 945 gm

xorg.conf has 1280x800 res. on it but the screen is still on 1024..

any help?

---

### Post by cumbulak on 2007-10-08
I can advice you just the VGA: try using 915resultion. This should work well.
 I have downloaded XP Wifi driver for brm43xx somewhere, but I really cannot recall where from. :-(
As for sound, some guys wrote nice avice in this thread, but I was unable to test it.
Card reader - somehow nothing.

You may try the newest Ubuntu 7.10 (now still beta) or just for a test OpenSuSE 10.3. Just for your info OpenSuSE 10.3 Beta had the same problems as Ubuntu 7.04, but something may have improved.

---

### Post by archimedes1 on 2007-10-12
Hi there,

I dont needed to configure or setup card reeder or vga, it worked as default well.
I still have problem with touchpad. On battery touchpad is still crazy :) jumping and tapping lol

---

### Post by cumbulak on 2007-10-12
Did your card reader on Acer Aspire (not Travelmate) 5310 really work with Ubuntu 7.04 out of box??

---

### Post by dominik_ap on 2007-12-15
> **westdam said:**
> hi, i've got the same laptop. ( acer aspire 5310 )  anyone was able to install 
a) wifi card succesfully. ( cant find the XP drivers.. acer doesnt provide it on ftp site ) 
b) sound card 
thanks!

Hi i used for wifi this tutorial 
[http://ubuntuforums.org/showthread.php?p=3523715&mode=linear#post3523715](http://ubuntuforums.org/showthread.php?p=3523715&mode=linear#post3523715)

and driver for my Atheros 5006EG wifi
[http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)

But now i have problem, when i do "cat /sys/class/net/wlan0/power/state" it turns 0... so i suppose it is turned off and i dont know how to turn it on (echo 1> /sys/cl... doesnt work)

about Audio on this notebook try this tutorial:
[http://ubuntuforums.org/showthread.php?p=3237983&mode=linear#post3241735](http://ubuntuforums.org/showthread.php?p=3237983&mode=linear#post3241735)

when you will try it, please inform me, i dont have time to try it actually :)

Dominik Franek

---

### Post by Pixman on 2007-12-16
Just for the records:

I have an 5310 model, too. With gutsy gibbon and I'm using the kernel 2.6.22-14-generic, everything works perfect!

The only problem I had, was the sound in the beginning, but this changed with the kernel change. And as far as I remember, you have to load snd-hda-intel with the options model=acer.

I used NDISWRAPPER and the fitting drivers for Windows and everything went well, too. Actually, I'm right now using it.

BUT there is one thing I have to complain.. the volume is kind of low.
Does anybody with the 5310 have Windows and is the volume there low, too?
Is the machine just not able to produce a higher volume?
All my controls are up to the limit... it's acceptable but somtimes it's just too quiet for some movies or music.

Every help is appreciated, thanks in advance. :)

Greets,
Michael

P.s. Are you peeps also extremely happy with the 5310? ;) It's such a cheap but still powerful notebook. Looks fine and isn't too heavy either... Real catch. :)

---

### Post by Flix83 on 2008-01-03
Hello,
I bought myself an Acer Aspire 5310, too. The Installation of Ubuntu was quite inspiring. ;-)
I got sound and wifi working following the tutorials in this thread. Even the little wheel on the side can be used to control the volume. Wifi is allways on until I touch the Wifi switch, which seems to turn it off, but I can live with that.
The only problem which remains is the behaving of the touchpad when operating on battery. Anyone got solutions for that?

I haven't tested the S-Video and the Card Reader yet so I can say nothing about that.

---

### Post by roto6 on 2008-01-03
Congratulations! Was the card reader working right out of the box? If not, how did you get it doing so? What special modules do you have? External drivers? Kernel version? I tried it with two different MemoryStick cards without any response. With Win they work whence I am keeping that system for now. I somewhere found a kernel patch for 2.6.20, but that is not working in my case 2.6.22.14.

Regarding the sound I followed the instructions at the end of (maybe the same as your method):
[http://ubuntuforums.org/showthread.php?t=545318](http://ubuntuforums.org/showthread.php?t=545318)
I compared with winvista output (especially for you ;)). Result: same volume, which is actuaklly quite loud if I turn it up, at the earphones as well as on the internal speakers.

My touchpad works without problems, I have changed nothing.

---

### Post by sheleztt on 2008-01-07
Hi, folks :) Same laptop.
I had success with sound.
My webcam works - i know it. I can see myself in kopete device configurations, but when i try to use camorama the "cannot connect to /dev/video0" error appears. And i also know i have the /dev/video0 file:)
WiFi: Has anybody tried something like enabling firmware drivers in System  Settings? (kubuntu) 
I have been thinking my wifi will work, but still had no chance to test it.

---

### Post by Mister 4 on 2008-01-07
Hi there, first post and so forth.

I got an Acer 53**15** recently, and ran into the same two main problems that everyone else in this thread seems to have (and have solved).  It's worth keeping in mind that I was only running the Live CD to check if it would all work first.

Now, my question is:  Is the hardware similar enough between the two models that I can just use the same method to fix it?

---

### Post by sheleztt on 2008-01-10
> **Mister 4 said:**
> Hi there, first post and so forth.

I got an Acer 53**15** recently, and ran into the same two main problems that everyone else in this thread seems to have (and have solved).  It's worth keeping in mind that I was only running the Live CD to check if it would all work first.

Now, my question is:  Is the hardware similar enough between the two models that I can just use the same method to fix it?
I think it's definatelly worth trying.

+ [http://hsnewman.freeshell.org/acr5315.htm](http://hsnewman.freeshell.org/acr5315.htm)

---

### Post by Flix83 on 2008-01-26
Hello,
the next chapter of the fascinating ubuntu on the acer laptop story:
I tried the Card Reader today but it is far from working, lspci shows that it is there but when I plug something in there nothing happens. Even dmesg shows nothing but I discovered the following line which brings some light into the touchpad problem:
> [ 2663.652000] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.
[ 2665.128000] psmouse.c: GlidePoint at isa0060/serio1/input0 lost sync at byte 1
[ 2665.136000] psmouse.c: GlidePoint at isa0060/serio1/input0 - driver resynched.

This SEEMS to happen only when operating on battery, today I've got no time to test this (it's my brothers birthday) but I'll keep this one in mind.

Has anybody a similar dmesg output or am I the only one?

---

### Post by Flix83 on 2008-01-28
Okay, I don't know if anybody helps this if anybody is reading this post regularly please post something or I will stop either.

So far there is all quiet on the touch pad front but I found another reproducible quite annoying error:
If I started windows and then restart to ubuntu i often have a kernel panic after I log on, where can I get an error log for things like this?

---

### Post by dominik_ap on 2008-02-08
Hi about TOUCHPAD try this:

```

 sudo rmmod psmouse
 sudo modprobe psmouse

```

It will reinstall your drivers for touchpad and then its working better (but i dont know how to automatize this command, so help me, i dont want to use it each time working on battery)

And CARDREADER... I have just tried it because i got new Camera :) so I inserted the SD card of it and in Krusader when I pressed ctrl + M (Mount devices) there was this card, so I opened it and downloaded photos from SD card.
So it works and i didnt install it

But I have problems with WiFi and Audio.
I have installed the driver for Wifi by NDISWRAPPER, but i dont know how to connect or how to test if the wifi is properly installed.

and audio, there i have no succes in anything :)

---

### Post by dominik_ap on 2008-02-11
> **archimedes1 said:**
> Hi there,
I dont needed to configure or setup card reeder or vga, it worked as default well.
I still have problem with touchpad. On battery touchpad is still crazy :) jumping and tapping lol

Hey archimedes, i have found the solution for the touchpad problem.

I have written it here: [http://ubuntuforums.org/showthread.php?p=4308913](http://ubuntuforums.org/showthread.php?p=4308913)
For the others, the process is this:
Edit file **/etc/X11/xorg.conf** 

change the Synaptics Touchpad section with this one:
```

Section "InputDevice"
        Identifier      "Alps Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/input/event4"
        Option          "Protocol"              "event"
        Option          "HorizEdgeScroll"       "0"
        Option          "MinSpeed"              "0.50"
        Option          "MaxSpeed"              "0.80"
        Option          "AccelFactor"           "0.030"
        Option          "SHMConfig"             "on"
EndSection

```
And don't forget that you have to change also section "ServerLayout":
```

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Alps Touchpad"
EndSection

```

this help i found on
[http://ubuntu.wordpress.com/2005/11/...aptics-driver/](http://ubuntu.wordpress.com/2005/11/...aptics-driver/)
other help is here:
[http://ubuntuforums.org/showpost.php...3&postcount=50](http://ubuntuforums.org/showpost.php...3&postcount=50)

But i have modified it a little bit.
I am now writing an advice how to get working Linux Kubuntu/Ubuntu on Acer ASpire 5310 here
[http://www.franek.name/index.php/Acer_Aspire_5310_on_Kubuntu](http://www.franek.name/index.php/Acer_Aspire_5310_on_Kubuntu)

---

### Post by E_K on 2008-02-14
I do have my card reader working, ive not checked back here in a while, i just googled it, followed something and tada it works

i realised thats not to helpful so i searched for you and i think it was this
[http://ubuntuforums.org/showthread.php?t=420721](http://ubuntuforums.org/showthread.php?t=420721)

hope it works for you

EDIT: That is definitely what i used to get it working :D

---

