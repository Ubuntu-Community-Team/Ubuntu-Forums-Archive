---
title: "Acer Aspire Mic Fix?"
date: 2008-09-22
forum: Hardware
---

### Post by ArrrghJ on 2008-09-22
My integrated mic doesn't work. Am I just stupid or is there a driver I need to install.
I'm using an Acer Aspire 5720z laptop.

---

### Post by calraith on 2008-09-22
> **ArrrghJ said:**
> My integrated mic doesn't work. Am I just stupid or is there a driver I need to install.
I'm using an Acer Aspire 5720z laptop.

I'm on an Acer Aspire 4520 and have the same issue.  I believe the integrated mic is a USB device, although I can't remember what I saw that gave me that idea.  I've also been unable to get the mic / line in / headphone jacks on the front to work.

The only solution I've come up with is to use a Creative X-Fi Xmod USB sound card I picked up on red dot from Circuit City several months ago.  As luck would have it, I just bought it because it was a good deal, but had no idea why I'd need it.  Now I have a use for it.  :)  Anyway, the Creative device has better quality audio than my integrated audio, so I don't really miss the functionality I don't have.

However, if someone does have a solution to get my on-board crap to work, I certainly wouldn't scoff at it.

---

### Post by Fanless_Puppy_Fan on 2008-09-24
Basically, the AA1 works great except for the choice between no sound on resume from suspend and no internal mic. Check out my post and screen shot on the wubi board:

[http://ubuntuforums.org/showthread.php?t=905983](http://ubuntuforums.org/showthread.php?t=905983)

---

### Post by johnsky on 2009-05-27
Yes, we wouldn't be here if we hadn't already installed Ubuntu on an Aspire One, Fanless_Puppy_Fan.
We don't need a guide to general installation, or to be reminded what our problem is.


What we need is a fix to this internal mic issue everyone is experiencing on Acer Aspire Netbooks loaded with Ubuntu.

I've seen some people on other forums claim they have figured it out... but they were ignorant enough to forget there's still hundreds of us who haven't, and need to know how.


So, if anyone has figured out how to get the internal mic on the Acer Aspire One units working with Ubuntu (9.04 for me), please chime in.

I'd like to use the onboard mic for conference calls... I don't want to have to be stuck using windows on such a light comp.


Someone on another forum hinted that the issue lays in ALSA... but that doesn't really help me.

---

### Post by josekym on 2009-07-04
I've been stuck with the same issue on my Aspire 4736z using Jaunty since a couple of months ago.  I've done most of the workarounds, including updating to Alsa 1.0.20, but still don't have a working front mic.

Good thing though is that my external speaker and mic ports are working by default on Jaunty, so I'm restricted to using a headset for conferencing in the meantime.

I've read on other forums that this is a regression problem with the latest kernels.  No solution in sight yet. :(

---

### Post by ideathproof on 2009-07-10
I too have a problem with my accer aspire 5520, everything is working except internal mic, on [https://bugs.launchpad.net/linux/+bug/269294](https://bugs.launchpad.net/linux/+bug/269294) there is a fix posted which apparently works according to some of the users, but i could not figure it out yet, below is the fix which was posted, but I get stuck at sudo dpkg -i --force-overwrite alsa-driver_1.0.20-1_i386.deb (i asume i need to ajust this command as i am using amd64 Ubuntu 9.04 - the Jaunty Jackalope)

> I fixed this problem on my Acer Aspire 5520 Notebook. I had the exact same problems above, but can now record audio just fine with the internal microphone from the Acer CrystalEye Camera and Microphone combo.
 NOTE: This problem was experienced in Ubuntu 9.04 and Linux Mint 7. The fix was performed and tested in Linux Mint 7, which uses Ubuntu 9.04 as its base.
 Step 1:
Download <a href="[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)">Alsa drivers v10.0.20</a>
 Step 2:
extract the contents.
 <b>
tar -vxf alsa-driver-1.0.20.tar.gz
</b>
 Step 3:
Compile the driver
 <b>
./configure
make
sudo make install
</b>
 NOTE: I actually used a program called CheckInstall which creates a debian package that I can later install or remove at my leisure. If you choose this option be sure to install CheckInstall first, and also it may be necessary to install the finished package in this manner:
 <b>
sudo dpkg -i --force-overwrite alsa-driver_1.0.20-1_i386.deb
</b>
 Step 4:
Configure alsa-base.conf
 Add the following line to the end of /etc/modprobe.d/alsa-base.conf
 <b>
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer
</b>
 Step 5:
Reboot
 Sound recording should now work correctly on the Acer 5520. I experienced this problem with Ubuntu 9.04 and Linux Mint 7. The Fix works in Linux Mint 7, and should therefore work in Ubuntu 9.04, as they are essentially the same under the hood.

        


---

### Post by ideathproof on 2009-07-10
Hurray I got it to work, thanks to [marcosbelancon]("https://bugs.launchpad.net/%7Embelancon") from the bug report.

Below is what I did

Step 1: Download [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
 

Step 2:extract the contents.
 Open terminal and cd (change directory) to where you downloaded the driver e.g usr@usr-laptop:~$cd Desktop Note: remember its case sensitive once in the correct directory untar the driver using the command tar -vxf alsa-driver-1.0.20.tar.gz


 Step 3:Compile the driver (note you need Check install if you don't have it use apt-get install to get it e.g sudo apt-get install checkinstall) then run the commands bellow takes a little while to do its thing

 
./configure
make
sudo make install


 Step 4:
Configure alsa-base.conf
 Add the following line to the end of /etc/modprobe.d/alsa-base.conf file I did this by using the command 

sudo gedit /etc/modprobe.d/alsa-base.conf
 

I added these two lines at the end of the conf file then saved it
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer


 Step 5:
Reboot and for me it worked hope this helps someone

---

### Post by josekym on 2009-07-25
> **ideathproof said:**
> Hurray I got it to work, thanks to [marcosbelancon]("https://bugs.launchpad.net/%7Embelancon") from the bug report.

Below is what I did

Step 1: Download [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2)
 

Step 2:extract the contents.
 Open terminal and cd (change directory) to where you downloaded the driver e.g usr@usr-laptop:~$cd Desktop Note: remember its case sensitive once in the correct directory untar the driver using the command tar -vxf alsa-driver-1.0.20.tar.gz


 Step 3:Compile the driver (note you need Check install if you don't have it use apt-get install to get it e.g sudo apt-get install checkinstall) then run the commands bellow takes a little while to do its thing

 
./configure
make
sudo make install


 Step 4:
Configure alsa-base.conf
 Add the following line to the end of /etc/modprobe.d/alsa-base.conf file I did this by using the command 

sudo gedit /etc/modprobe.d/alsa-base.conf
 

I added these two lines at the end of the conf file then saved it
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer


 Step 5:
Reboot and for me it worked hope this helps someone

Hello there,

I did the same procedure on my Aspire 4736z, but sadly the built-in mic still doesn't work.  Audio works fine and so does the external mic jack.  I also used model=3stack-6ch-dig but still no go.

---

### Post by raletando on 2009-10-08
This is my first post so hello to everyone

I had the same problem with acer 5520
I followed [ideathproof]("http://ubuntuforums.org/member.php?u=872044")'s advice just until step 3 
The mic seems to work but has many cracks and pops and echo and the sound seem to come out 
of a tunnel. 

So my question is "how do I configure alsa" ?
and where is the file  /etc/modprobe.d/alsa-base.conf ?

Thanks

---

### Post by raletando on 2009-10-14
it was jsut a matter of adjusting the mixer after all :D

thanks

---

### Post by ArrrghJ on 2009-10-28
Thanks so much ideathproof! 
I finally got my mic to work!

---

### Post by leorolla on 2009-11-09
Worked for me!!!

Acer Aspire One D150

I installed Ubuntu 9.10

```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.

```that means I have ALSA 1.0.20 already installed. If you don't, stop right here and go get ALSA 1.0.20 before proceeding.

```
sudo gedit /etc/modprobe.d/alsa-base.conf

```and added the following lines to the end of the file:
```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer
```Rebooted.

Sound Preferences -> Hardware ... there is only "Internal Audio 1 Input 1 Output Analog stereo duplex"
Sound Preferences -> Input -> Device : Internal Audio Analog Stereo
Sound Preferences -> Input -> Connector : Microphone 1

Edit: change to Microphone 2, than to Microphone 1 again, then Mute, then Unmute.

It works!

Don't know if it's the "right" solution to my machine, but it works.

---

### Post by noletolucas on 2009-11-09
> **leorolla said:**
> Worked for me!!!

**_Acer Aspire One D150_**

I installed Ubuntu 9.10

```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.

```that means I have ALSA 1.0.20 already installed. If you don't, stop right here and go get ALSA 1.0.20 before proceeding.

```
sudo gedit /etc/modprobe.d/alsa-base.conf

```and added the following lines to the end of the file:
```
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer
```Rebooted.

Sound Preferences -> Hardware ... there is only "Internal Audio 1 Input 1 Output Analog stereo duplex"
Sound Preferences -> Input -> Device : Internal Audio Analog Stereo
Sound Preferences -> Input -> Connector : Microphone 1

It works!

Don't know if it's the "right" solution to my machine, but it works.

It didn't work for me on **_Aspire 4736Z_**, Ubuntu 9.10.
It actually  behaved very weird:
1- mic still didn't work
2- speaker and headphones were active at the same time

---

### Post by EveryWhere on 2009-11-22
Same here.. Acer 5520 with Ubuntu 9.10 x64.
Internal and External (with jack), both aren't working.
What can we do?

---

### Post by ideathproof on 2009-11-23
the conf file is a hidden file but i did the entirety of the above fix in terminal afterwars you need to play with the volume mixer a bit to get it working smooth its perfect for me now, i am not sure if the fix is still in affect as i upgraded to Karmic, but all is still well

---

### Post by EveryWhere on 2009-11-23
I did your steps (using the new version of alsa *.21) with Ubuntu 9.10 x64.. only cracks from my internal/external microphone. I've  tried removing pulseaudio and rebooting also.. still the same. Suggestions?

---

### Post by marcelopaz on 2009-11-28
Hello ppl!

I'm using Karmic Koala 64-bit on an Acer Aspire 6930-6154. Everthing that I have tested (webcam, sound, HDMI sound/video out, wi-fi, power management) worked perfectly, with the exepction of the built-in microphone. I have tried all steps listed here to fix (upgrading ALSA and installing realtek drivers). The realtek drive didnt work and messed up all sound, and I reverted it to the native drivers to get the sound back to work. 
The internal mic doenst work at all and using the mic on the external jacks works, but the input is too low, I almost cannot hear. I need the mic to use with skype, anybody has and idea to fix it? 

Thanks in advance!!!!

---

### Post by beren.olvar on 2009-11-28
The problem with acer microphones is weird.
I had the following experience: After never being able to use it under ubuntu, I switched to archlinux (for other reasons). Making my own install of alsa, I realised that it will not work unless you choose an specific volume configuration for the capture devices. Although I could use it for a while, it stopped working out of nothing, I was using skype and is suddenly died.

There are a lot of bugs reports around, but non of them seems to fix it, at least in my case.

my advice, buy a cheap external usb sound card, I don't think it will get solved soon.

---

### Post by marcelopaz on 2009-11-29
I have tried a wierd thing here, writing these lines on alsa-base.conf

```

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer-aspire
```I don´t remeber where I did read about this "acer-aspire" (instead of "acer" suggested in this topic). And with this, the mic on the external jack WORKS with a good volume. But the internal mic still don´t work. But with this config, the internal speakers don't work, only if a headphone/speaker is plugged in the external jack. 

This is nonsense. More complicated stuff in the notebook, like webcam and hdmi, works perfectly, and this stupid mic doens't. 

I will try to "mix" the two solutions (with the external mic working AND the internal speakers too), but I don't know how to do it.

---

### Post by Danwhelan on 2010-01-16
**ALSA / Sound help** 			
 			 			 		   		 		 		Hi there 

I'm using - Karmic 9.10

Basically I've tried to update my ALSA driver set to get my microphone working... I used the instructions found here 

[http://ubuntuforums.org/showthread.php?t=927270](http://ubuntuforums.org/showthread.php?t=927270)

Now I've no sound at all, I've tried trying to diagnose the problem however can't seem to find anything specific to this issue. 

My sound settings page is just blank on the hardware tab

Various tests have shown that the sound card is detected... but no joy 

Can any one help with this? 

Many thanks 

Dan

---

### Post by omair on 2010-01-25
install kmix, enable all channels, check capture, set 'input source' to Int Mic :) I have tried many mixer apps with my 6930 but kmix is the only one that provides the option. Hope this helps.

---

### Post by Antecursor on 2010-03-04
I've had a similar experience using an Acer Aspire 5810TZ.

There is an excellent post on this that can be found at:

[http://ubuntuforums.org/showthread.php?t=1341325&highlight=acer+5810tz]("http://ubuntuforums.org/showthread.php?t=1341325&highlight=acer+5810tz")

Fot the 5810TZ the problem was resolved by installing the linux-backports-modules-alsa-karmic-generic packages.  They are easily found in synaptic or apt-get.

I had tried a new installation of alsa, but it did not solve the issue permanently.  It seems that between those two fixes, the majority of the intel integrated mic issues can be resolved.  Thanks to PatrickVogeli, the power saving tips also brought my battery life much closer to the 8 hours it is advertised as running.

---

### Post by jason_n89 on 2010-03-12
> **EveryWhere said:**
> I did your steps (using the new version of alsa *.21) with Ubuntu 9.10 x64.. only cracks from my internal/external microphone. I've  tried removing pulseaudio and rebooting also.. still the same. Suggestions?

this is something extremely simple and as such easy to overlook but over amplification can result in either little or no audible recording, or in very staticy sounding garbled illegible recording. if you lower the input/capture volume to approximately one eighth to one quarter volume and then work your way up you may find that your problem is fixed. also thank you ideathproof for posting those step by step instructions they are very useful

---

### Post by leorolla on 2010-03-12
The following worked for me.

Now the system even switches from internal to external mic depending on whether the latter is plugged.

I use Ubuntu. Anything starting with "K" might conflict with this solution.

My device:
```
$ sudo lshw -C multimedia
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:56340000-56343fff
$
```1. Install padevchooser

2. Reboot

3. When adjusting the sound levels of the mic, unlock the channels and adjust left to 90% and right to 5%.

Without Step 3 I had it working well except on Skype. Now it always work.

Source:
[http://ubuntuforums.org/showthread.php?t=1391884](http://ubuntuforums.org/showthread.php?t=1391884)

---

### Post by alex_baraker on 2010-11-15
Acer 4736z internal mic issue solved: 

[http://forums.gentoo.org/viewtopic-t-852766.html](http://forums.gentoo.org/viewtopic-t-852766.html)

---

### Post by alex_baraker on 2010-11-15
internal mic solved:

[http://forums.gentoo.org/viewtopic-t-852766.html](http://forums.gentoo.org/viewtopic-t-852766.html)

---

### Post by islandBilly on 2010-11-18
This (ie post #21) is the most hopeful solution I've seen in this thread - but I'm reluctant to install kmix: it looks like it needs me to install the whole basic KDE stuff, and I don't want to do that - I like the standard Ubuntu interface much better (I've got an Aspire 532h w Ubuntu 10.4 installed, and this dead internal mic is STILL going on!

anyway, if I install kmix through Synaptic, and all its dependencies, will the rest of Ubuntu stay the same, or will I find myself in KDE land?

[update] I checked and I already am running alsa v1.0.21, so no point in loading an older version I think. Also, trying to use Ubuntu facilities first, I did a system test and found that the internal mic seemed to work fine! Then I tried it with th sound recording app in the System ->Sound menu, and that too works just fine. It seems that all I really have here is a compatibility problem with Skype, the most important thing I want that mic for. Skype simply does not recognize it at all. And this is Skyp v2.1.0.81, installed via Synaptic.

At least this should be easier to pursue than a general dead microphone.

---

### Post by jazzman on 2010-11-22
I don't know if this will work for you but 
1. I installed  pavucontrol 
2. then opened Applications-> Sound & Video-> PulseAudio Volume Control.
3. I then clicked on the "input devices" tab. 
4. I unlocked the sliders by clicking on the little lock icon.
5. I moved the right slider all the way to the left (muted) and the left slider I adjusted as needed. Works perfect without tweaking the system.

---

### Post by islandBilly on 2010-11-23
> **jazzman said:**
> I don't know if this will work for you but 
1. I installed  pavucontrol 
2. then opened Applications-> Sound & Video-> PulseAudio Volume Control.
3. I then clicked on the "input devices" tab. 
4. I unlocked the sliders by clicking on the little lock icon.
5. I moved the right slider all the way to the left (muted) and the left slider I adjusted as needed. Works perfect without tweaking the system.

Thanks, jazzman, it worked exactly as you said, and being able to download a relatively small package like that was very encouraging. I wanted to stay within the Ubuntu way if you know what I mean.

I fussed a bit with the sliders for the mic, wondering if maybe using some of the right side would work out, and in fact the internal stereo mic works fine with both channels up and even - with anything except Skype. Only when I mute the right channel and then adjust the left  does Skype work - AND I had to shut off Skype's automatic level setting to keep it working right, or it adjusts the level downward until you can't hear anything. So Skype is the bad actor here, but this work-around is great, thanks again!

love to hear your bass work some time ;)

---

### Post by HipHopBlond on 2011-06-05
> **jazzman said:**
> I don't know if this will work for you but 
1. I installed  pavucontrol 
2. then opened Applications-> Sound & Video-> PulseAudio Volume Control.
3. I then clicked on the "input devices" tab. 
4. I unlocked the sliders by clicking on the little lock icon.
5. I moved the right slider all the way to the left (muted) and the left slider I adjusted as needed. Works perfect without tweaking the system.

Just wanted to say thank you too, worked like a charm... an Ubuntu friend referred me to this topic after trying almost everything... Now I can make skype calls from my netbook ^^

/Acer Aspire One D260-Bkk running Ubuntu Linux 11.04/

---

### Post by sxfield on 2011-06-05
I have an Acer Aspire One AO255E Netbook and was having a problem with the internal microphone being 'muted' or 'turned off' while running both UNR 10.10 and Joli OS 1.2. I stumbled upon the answer and here it is: The Juli OS help files have you:

sudo apt-get update
sudo apt-get install pavucontrol
Alt+F2
(enter) pavucontrol

When the control box pops up, click on the 'Input' tab. You will see two sliders for input marked Front Left and Front Right. The problem is, the external 'input' jack (or line in) is STEREO, while the internal microphone is obviously MONO. If you use an external microphone, which I did, which had a stereo plug on it (which implies that the microphone was a stereo microphone, or had one microphone connected to both left and right channels) and it worked fine, while the internal microphone did not. Now, if you click the little 'lock' icon (which unlocks the sliders) and move one of the sliders (doesn't matter which one) to zero, all of a sudden, the internal microphone works! Then, click the little 'lock' icon again, to lock the sliders where they are. Later, if you do want to input some two channel stereo stuff, you have to run pavucontrol again, unlock the sliders, adjust them both for whatever gain you want, and away you go. This behavior is apparently completely undocumented (or not). Anyway, it worked for me!

d

---

### Post by wjamoore on 2011-06-27
doesn't work on acer 3820TZ

WJAM

---

### Post by insaner on 2011-07-23
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/775788](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/775788)

```

sudo gedit /etc/modprobe. d/alsa-base.conf

```and add the line:
```
options snd-hda-intel model=laptop,dell-vostro position_fix=0,1"

```this should fix most problems, i can get hdmi audio yet, not sure why

ps, this is for ao522-bz623, hope that helps you guys out too..

-- 
insaner
[www.insaner.com](www.insaner.com)

---

### Post by littledonnyfund on 2012-09-05
Hi all i have a Acer Aspire 5810TZ & i am running the latest build of ubuntu 12.04 & when i go too sound settings & go to input there is nothing available under record sound from & i was reading the posts in here on this thread & someone suggested going to old repositories & i don't know how to do this any help is greatly appreciated thanks again :)

---

