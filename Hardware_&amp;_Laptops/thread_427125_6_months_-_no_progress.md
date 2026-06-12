---
title: "6 months - no progress"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by jrz on 2007-04-29
**Wireless Problem is solved further in this thread.**

As an ex-ATT employee who had used unix since it first became an OS, I had recommended that a friend who had never used a computer install a Linux OS rather than MS Windows, based on his needs which were primarily stability, working in a rain forest. Having retired and being away from computers for a number of years I had not kept up with the changes which appear to have occurred, many of which appear irrational to me. It appears that today most hardware is designed for compatibility with MS OS's, and lacking the information available to allow it to be used with any other OS's easily. 
As a result we looked for a notebook computer which would fit his needs based on features and price and settled on a Compaq Presario 3000 series, (V3042AU), requesting it come with a Linux OS rather than Win-XP.
It was built and delivered with Ubuntu 6.06 LTS and appeared to have applications for every need pre-installed.
Initially he was very happy with it as was I. As he became more familiar with it we began to implement more and more of the features that could be useful to him, and began to find areas that required attention, most of which were quickly and easily solved. We quickly encountered several things which we could not easily solve, listed here:

1. Cannot record from the microphone - Desired for recording notes quickly while in the field that can later be expanded in written textually.
2. Wireless connection does not work - Often an internet connection is available only via a wireless connect as the building housing the router is unoccupied, and locked for security purposes.
3. Many video formats cannot be played - Video information  being shared by others is received in many different formats which we have no control over, and as most others are using a Win-XP OS formats are a choice of those providing them.

We have spent the last 6 months reading FAQ's, emailing Compaq, NVidia, and Broadcom, searching the Ubuntu forums, and other websites, following the "Try this" offerings to no avail. We have also tried the IRC channels related to the OS, hardware, and software involved in the problems encountered, also to no avail. We have even gone so far as to format and re-install the OS from scratch, after receiving some IRC help which left the system unusable, as the one providing help quietly disappeared providing no assistance on how to undo what he had suggested would fix our problems. The greatest difficulty is trying to discern the competency of the one who claims to have the solutions to the problems you are seeking help to solve. Many, it appears feel a need to provide help when they should not. Questions often result in the same answers received numerous times previously, leaving one to believe they are just going around in circles. 

I still remain convinced that Ubuntu, or Linux is much preferred to Win-XP as an OS, but am at a loss as to where reliable assistance is to be found when difficulties arise. Six months is not what I feel to be a reasonable time to be working on the same problems. I still maintain that the problems are solvable, but am at a loss as to where to find the solutions. If someone has knowledge of where to go next please inform us. 

Thank you, from the forests of Thailand.

---

### Post by sharke on 2007-04-29
Well you are definetly in the right to recieve the answers you need.
Please supply a list of specific problems you have startig with the most urgent also as much info as possible about the system.
Regards
Sharke

---

### Post by josephus on 2007-04-29
i looked through your old posts about your wireless connection.  

which drivers did you use in conjunction with the ndiswrapper?  i would make sure that you are using the ones that came with your computer, or better yet use the latest ones online - 

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-41607-1&lc=en&cc=us&dlc=&product=3246149&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-41607-1&lc=en&cc=us&dlc=&product=3246149&os=228)

you can unpack the drivers using the cabextract utility.

the information you posted is from many months ago, so i'm not sure what has changed on your system, so let us know so we can help you better.  but going on the limited info that i have the next step is to remove any existing drivers attached to ndiswrapper

```
sudo ndiswrapper -l
```

if it lists any drivers then remove them using

```
sudo ndiswrapper -e <driver_name>
```

then go into the directory that has the driver and load it into ndiswrapper

```
sudo ndiswrapper -i bcmwl15.inf
sudo ndiswrapper -l
```

if it worked then it should say driver installed, hardware present (or something to that effect)

after this load up the ndiswrapper module

```
sudo modprobe ndiswrapper
```

From there can you post

```
lshw -C network
dmesg
```

i just need the last couple of lines of dmesg to see if there are any errors.

------

you also asked the question about lspci

```

lspci
0000:01:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
```

 The fact that it is unknown doesn't necessarily mean anything.  If you used 'lspci -n'  you will get a 8 digit code xxxx:yyyy which identifies the device.  The number is translated into a human readable identifier based on the information in /usr/share/misc/pci.ids .  The first 4 digits identifies company (broadcom), and the last four digits the specific device.  All it means is that your device was not in the database.  It's continually updated so a more recent version might include your card.

---

### Post by jrz on 2007-04-29
Thank you for such a quick response, and I hope I didn't appear irate or angry in my post, as in reality I am only frustrated. I will try to provide as much as I can, but if I miss something it is only because I am unaware of what it might be or where to find the info, so if that occurs please notify me as where to obtain such info.

System: Compaq Presario V3018AU
OS: Ubuntu 6.06 LTS with all updates recommended by the package manager applied
Sound Card: HDA NVidia Chip: Generic 14f11 ID 5045
lspci shows: 0000:00:10:1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
Wireless: Broadcom 4311
lspci shows: 0000:01:00.0 Network Controller: Broadcom Corporation: Unknown Device 4311 (rev 01)

Items with problems in order of importance are:

1. Microphone both internal (stereo) and external do not record. Right clicking on the speaker and opening the volume control displays Volume Control: HDA NVidia (Alsa mixer) with 2 tabs, Playback and Capture. The Capture tab shows 2 sliders maxed out and beneath a Mute and Microphone, neither are disabled, or contain a red X. On the Playback tab both sliders for Master and Playback are at Maximum and are enabled, no red X's applied to the icons below them. We are trying to record using the Applications, Sound and Video, Sound Recorder which opens a GUI labeled Untitled-Sound Recorder, Record from Capture, Record as Voice, Lossless (WAV Audio), and have tried using both the internal and external microphones, but capture no sound. 

2. The wireless connection has been attempted using every possible driver we have found from Compaq, Dell, and other sites but none appear to work. Not being very familiar with wireless troubleshooting I am really not sure where to begin but it appears that no matter which driver we have tried to use we have never got to the point that the system recognizes a wireless device is available, no WLAN0 or ETH1 appears.

3. We have installed VLC Player and also have Totem, as some video formats work with one but not the other, while other video formats work with neither. Ideally we would like to have but one player work with all video formats, but would be satisfied using two or more players as a last resort. I seem to have misplaced the notes on video formats that do not play at all, and which do play in one, the other or both players, but this is the least important of the problems.

If you can aid, or point us to where best to find aid in solving any of the above problems we would be very appreciative. If the info provided is lacking, please advise as to what additional is necessary and from where it should be obtained if it is the output of a command.

Thank you once again, from Thailand.

---

### Post by josephus on 2007-04-29
ok.  you might need to download a new version of ndiswrapper (you are using 6.04 right? which by default includes a pretty old version) 

ndiswrapper -v

the current version 1.42

have you looked at this, it gives pretty specific instructions for your specific card

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

### Post by sharke on 2007-04-29
Okay looks lije josephs is trying to get wireless sorted for multimedia go here [https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)   
and install the repos fo your distribution.
Do you have synaptic packet manager installed if not in a terminal sudo apt-get install synaptic.
now we uodate your sources with sudo apt-get update
now we get the latest updates for your distro sudo apt-get dist-upgrade
now we will install totem-zine and libdvdcss2
Totem-xine works a lot netter than totem
Ina terminal synaptic this will open synaptic package manager search fo r above packages and install
Sorry i have to leave it here for now as i have visitors
Regards
Sharke

---

### Post by jrz on 2007-04-29
I just finished following you initial instructions, and dmesg output is quite large, but appears that the following is relevant:

[17238473.652000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17238473.676000] ndiswrapper (check_nt_hdr:155): Windows driver is not 32-bit; bad magic: 020B
[17238473.676000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[17238473.676000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
[17238669.416000] hdc: tray open
[17238669.416000] end_request: I/O error, dev hdc, sector 0
[17238669.416000] Buffer I/O error on device hdc, logical block 0
[17238669.420000] hdc: tray open
[17238669.420000] end_request: I/O error, dev hdc, sector 4
[17238669.420000] Buffer I/O error on device hdc, logical block 1
[17238669.420000] hdc: tray open
[17238669.420000] end_request: I/O error, dev hdc, sector 8
[17238669.420000] Buffer I/O error on device hdc, logical block 2
[17238669.424000] hdc: tray open
[17238669.424000] end_request: I/O error, dev hdc, sector 12
[17238669.424000] Buffer I/O error on device hdc, logical block 3
[17238669.424000] hdc: tray open
[17238669.424000] end_request: I/O error, dev hdc, sector 16
[17238669.424000] Buffer I/O error on device hdc, logical block 4
[17238669.428000] hdc: tray open
[17238669.428000] end_request: I/O error, dev hdc, sector 20
[17238669.428000] Buffer I/O error on device hdc, logical block 5
[17238669.428000] hdc: tray open
[17238669.428000] end_request: I/O error, dev hdc, sector 24
[17238669.428000] Buffer I/O error on device hdc, logical block 6
[17238669.432000] hdc: tray open
[17238669.432000] end_request: I/O error, dev hdc, sector 28
[17238669.432000] Buffer I/O error on device hdc, logical block 7
[17238669.432000] hdc: tray open
[17238669.432000] end_request: I/O error, dev hdc, sector 32
[17238669.432000] Buffer I/O error on device hdc, logical block 8
[17238669.436000] hdc: tray open
[17238669.436000] end_request: I/O error, dev hdc, sector 36
[17238669.436000] Buffer I/O error on device hdc, logical block 9
[17238669.436000] hdc: tray open
[17238669.436000] end_request: I/O error, dev hdc, sector 40
[17238669.440000] hdc: tray open
[17238669.440000] end_request: I/O error, dev hdc, sector 44
[17238669.440000] hdc: tray open
[17238669.440000] end_request: I/O error, dev hdc, sector 48
[17238669.444000] hdc: tray open
[17238669.444000] end_request: I/O error, dev hdc, sector 52
[17238669.444000] hdc: tray open
[17238669.444000] end_request: I/O error, dev hdc, sector 56
[17238669.448000] hdc: tray open
[17238669.448000] end_request: I/O error, dev hdc, sector 60
[17238669.448000] hdc: tray open
[17238669.448000] end_request: I/O error, dev hdc, sector 0
[17238669.452000] hdc: tray open
[17238669.452000] end_request: I/O error, dev hdc, sector 4
[17238669.452000] hdc: tray open
[17238669.452000] end_request: I/O error, dev hdc, sector 0
[17238669.456000] hdc: tray open
[17238669.456000] end_request: I/O error, dev hdc, sector 4
[17238669.456000] hdc: tray open
[17238669.456000] end_request: I/O error, dev hdc, sector 0
[17238669.460000] hdc: tray open
[17238669.460000] end_request: I/O error, dev hdc, sector 4


We are running Ubuntu 6.06 LTS 32bit version, and I am wondering if the wireless drivers installed by ndiswrapper are for the 64 bit version? If so is there a way to denote that 32 bit is desired? Also the version of ndiswrapper installed is 1.8-0ubuntu2 per the Synaptic Pkg Mgr

---

### Post by eggdeng on 2007-04-29
> **jrz said:**
> 

1. Cannot record from the microphone - Desired for recording notes quickly while in the field that can later be expanded in written textually.
2. Wireless connection does not work - Often an internet connection is available only via a wireless connect as the building housing the router is unoccupied, and locked for security purposes.
3. Many video formats cannot be played - Video information  being shared by others is received in many different formats which we have no control over, and as most others are using a Win-XP OS formats are a choice of those providing them.


Microphone problem: See post by stami in
[http://ubuntuforums.org/showthread.php?t=342681](http://ubuntuforums.org/showthread.php?t=342681)

Wireless (Drastic solution):
Instead of struggling with unsupported wireless adapters & ndiswrapper, you might consider getting hold of a wireless access point, which can be configured as bridge, repeater or client. You just connect it to the ethernet card with a cable, configure it as client and you're picking up your wireless connection via your ethernet card. It's a neat, totally reliable solution from about 50 euros, the only problem being that you need somewhere to plug it in. For the record, mine is an ecom EW54AP.

Video formats:
It depends on which formats but the codecs installed by Automatix2 seem to do the job for most people. Alternatively, Just tick gxine and gxine-plugins in Synaptic to install a very versatile player.

---

### Post by jrz on 2007-04-29
Eggdeng: My settings match those given for the microphone problem, and we're running Ubuntu 6.06 not 6.10 if that makes a difference.

I'm getting spread a little thin trying to work on 3 problems simultaneously, so as it seems the wireless began first I would like to see if we can make progress on that now, especialy as it appears that something may have been discovered in that although the driver and hardware show present, it states that a 64 bit driver has been installed and we're running 32 bit ubuntu.

---

### Post by josephus on 2007-04-29
the ndiswrapper in repository for dapper are out of date, you'll have to recompile ndiswrapper yourself based on the link that i sent you earlier.

just to confirm the drivers you are loading are from the link the first link that i sent?

---

### Post by jrz on 2007-04-29
Josephus: Will an updated ndiswrapper install the 32 bit drivers or will something need be done to ensure the appropriate version is installed?

---

### Post by josephus on 2007-04-29
not positive, but i think that that is something worth doing - i've read a number of posts where people had trouble with ndiswrappers until they upgraded versions.  but if you are indeed trying to load 64bit drivers then i don't think will ever load up properly.  

just to confirm again, which model are you running in a recent post you stated V3018AU while in a the first post you have V3042AU.  i'm not sure if there is a difference in drivers, but it might be something to consider.

---

### Post by jrz on 2007-04-29
rik@compaq:~$ ndiswrapper -v
utils version: 1.7
driver version:        1.8
rik@compaq:~$


Are you saying that ndiswrapper 1.42 is later than what I show installed?

The System shows Compaq Presario V3000 on the LCD bezel, but the sticker on the bottom shows V3042AU. I may have made a typo if I show something different in one of my previous posts.

Also I note that there bcmwls32.exe and bcmwls64.exe in the driver folder making me think drivers for both 32 bit and 64 bit are there but the .inf file used by ndiswrapper is accessing info telling it that I am using a 64 bit CPU and therefore installing the 64 bit drivers?? The .inf file is over 12,000 lines long so I pause about thinking of making mods to it.

---

### Post by josephus on 2007-04-29
yup. 1.42 > 1.8

just made a quick check and the model numbers  doesn't make a difference either way as they both use the same drivers

---

### Post by josephus on 2007-04-29
just trying to understand why it's trying load up a 64bit driver, is it an AMD64bit processor ?

---

### Post by jrz on 2007-04-29
I retrieved the drivers fro the location you referred me, and a quick look at the ndiswrapper location you gave appears to state that it has been tested for 32 bit so I may find success following those instructions. As it's past 1am here, in Thailand and I have to get up early in the morning I will try and follow those instructions when I return home and will post the results here, hoping they will confirm success. Thank you very much for your help.

---

### Post by jrz on 2007-04-29
Josephus:
Thank you kindly, your instructions appear to be just what was needed. I am now on the wireless connection for the first time, and it is working great. Oh, and yes we have an AMD Turion64 CPU, but are using the 32 bit version of Ubuntu.
Thanks for both your time and your kindness, I didn't think we were going to make progress so quickly.

Joe (Thailand)

edit:
Perhaps I should add for anyone else that may follow this same procedure using [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)
which worked with one minor difficulty. Ndiswrapper was installed on our system using the Synaptic Package Manager, not with make, but trying to remove it with sudo apt-get remove ndiswrapper did not work. I did an ndiswrapper -v after running the remove command and it showed ndiswrapper still installed, so I simply went to the Synaptic Package Manager and marked it for complete removal which did remove it and I was able to proceed with no further difficulty. I have since restarted the system several times, powered off and started from power on, closed the lid for a period and each time the wireless came right up working. The link you provided and you help in general was all it took. If anyone else with the same OS and HW as me is having problems this appears to be the fix. I'm using a Compaq Presario V3042AU, and running Ubuntu 6.06 LTS, with a Broadcom 4311 wireless card, removed the ndiswrapper V1.8 and installed ndiswrapper v1.42, and retrieved the drivers from the site as recommended by the howto, and only had to install cabextract to get the contents of the sp33008.exe driver file. Perhaps it would be helpful in step 1, removing ndiswrapper, to do a ndiswrapper -v to verify that it has been removed and if not to use the Synaptic package manager to do so.

---

### Post by sharke on 2007-04-30
Well done Joe well done josephus.
Joe which problem would you like to be sorted next.
Regards
Sharke

---

### Post by jrz on 2007-04-30
eggdeng: It looks like josephus had just what I needed to get the 4311 wireless card working, so that's one problem solved. Now I'm getting ready to take a look at your advice on the microphone and if I can get that working we will have solved the 2 most important problems, and my friend and I both will be elated. Well, here goes, and I post the results encountered. Thanks for the help.

---

### Post by jrz on 2007-04-30
Sharke:
Hello again, this time from a much happier Ubuntu user. The most important of the remaining problems is the microphone. The Video isn't necessary in the field and I can convert formats on another computer when necessary. I had just went through the thread that eggdeng suggested and didn't seem to find anything that helped. Everything matched the suggested changes until I reached the System-Preferences-Sound and find I have no Tab labeled Devices. Perhaps that only exists in Ubuntu 6.10? The sound card works fine with the internal speaker and even the headset jack, but neither of the built in microphones, nor the microphone jack are able to record anything. Looking at the Pkg Mgr I believe we have ALSA v1.0.10 installed, and am not sure what commands might give more useful information as to what is installed. If you know what command outputs are important I will run them. I first thought it might just be a config file that required editing, but have not got anywhere on that.
BTW, we are only trying to record voice, using the Sound Recorder, and not use SKYPE or anything complicated. Any ideas? Pass them on and we'll give them a shot.

---

### Post by josephus on 2007-04-30
i don't really know what i'm doing here, but do mind posting

```
more /proc/asound/*
```

my only suggestion right now is to try recompiling alsa (dev version 1.0.14.rc3)

---

### Post by jrz on 2007-04-30
Thanks again for getting the wireless to work, I'm on it now.

rik@compaq:~$ more /proc/asound/*

*** /proc/asound/card0: directory ***

::::::::::::::
/proc/asound/cards
::::::::::::::
0 [NVidia         ]: HDA-Intel - HDA NVidia
                     HDA NVidia at 0xc0000000 irq 50
::::::::::::::
/proc/asound/devices
::::::::::::::
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
::::::::::::::
/proc/asound/modules
::::::::::::::
0 snd_hda_intel

*** /proc/asound/NVidia: directory ***


*** /proc/asound/oss: directory ***

::::::::::::::
/proc/asound/pcm
::::::::::::::
00-00: HDA Generic : HDA Generic : playback 1 : capture 1

*** /proc/asound/seq: directory ***

::::::::::::::
/proc/asound/timers
::::::::::::::
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
::::::::::::::
/proc/asound/version
::::::::::::::
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21
2005 UTC).

If the version of Alsa needs to be updated other than using the package manager, is there a good how to, as this is an area where we received help on IRC previously and ended up having to re-install the OS from scratch. But  I feel like we're on a roll today. I thought the wireless was going to be a lost cause.

---

### Post by josephus on 2007-04-30
i haven't seen any how-to's on this yet.  what happened the last time you tried compiling alsa.  did your system crash or did you just lose sound altogether?

---

### Post by jrz on 2007-04-30
Last time the system crashed and we had no idea what had to be undone or how to in order to get it to boot up again. I have a second system and the original helper disappeared and the only other help we could find suggested to reinstall the OS, which we did. That was help from the ALSA IRC channel.
Searching through the forums, it appears that many say their microphones can be heard through the speakers, but don't record or do so at a low volume, or hear only static. In our case there is no sound at all recorded, not even static. I'm a little afraid of trying to install a new version of ALSA without some good written instructions based on a Ubuntu OS, as the last time the helper wasn't familiar with Ubuntu, which may have been why we crashed the OS.

---

### Post by sharke on 2007-04-30
Perhaps this may be off some assistance [http://ubuntuforums.org/showthread.php?t=418396&highlight=microphone](http://ubuntuforums.org/showthread.php?t=418396&highlight=microphone)
Regards
Sharke

---

### Post by jrz on 2007-04-30
rik@compaq:~$ amixer set 'Capture' cap
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 23
  Front Left: Capture 23 [100%] [on]
  Front Right: Capture 23 [100%] [on]
I'm assuming that front left and front right capture refers to the microphones, everything shows unmuted and max volume, but no sound recorded or from the speakers when speaking into the microphones. On my notebook running MS OS, I get feedback if I enable the mikes with the volume maxed. Once looking at a post with a screen capture of the mixer I saw a set of volume controls labeled microphone, but ours are just labeled capture, with an icon of a microphone underneath the sliders. Also looked at the other thread referred to but found no "Microphone', 'Microphone Capture', 'Mic Boost (+20dB)', and 'Mic Select" to check. So no progress yet.

---

### Post by josephus on 2007-04-30
are you looking for something like this.  try gnome-alsamixer (you might have to add it from the repository)

---

### Post by josephus on 2007-04-30
forgot the attachment

---

### Post by josephus on 2007-04-30
i've been researching your problem, and i think that latest release of alsa is your best bet to getting your mic to work.  i've looked through some of the change logs, and they do make reference to your particular sound card.  however, given your previous bad experience with compiling/installing alsa it doesn't seem like a good decision to proceed without first understand what went wrong.

can you give a list of steps that you took the first time around.

---

### Post by jrz on 2007-05-01
sharke & josephus:
I had to take a friend to the airport yesterday and got home in the wee hours of the morning, so apologize for being slow to reply.

I added the gnome alsa mixer using the pkg mgr, and it only displays sliders for Master, PCM, and Capture. Looking at File-Preferences, displays the Mixer checked as Generic 14f1 ID 5045, and no option to change it to HDA NVidia (Alsa Mixer), which is what I believe it should be showing. I tried unchecking the check box and entering the HDA NVidia which then gave me an empty box where the slider previously appeared, so I changed it back. Perhaps this is where I need to make a change though?

The time before when we tried IRC help in updating ALSA, we went through so many things I didn't have time to make notes, and can't remember exactly what we did at the time the system crashed. We had just compiled something we were told to download, and after going through numerous commands from a terminal screen we were told to reboot the system which it would no longer do. 

The gnome-alsamixer png is what we would love to see, and what we thought we would see. Possibly a config file that needs manual changes? or something we need to run for it to see what we actually have installed?

And thanks to both of you for your patience.

Edit:
Just for the record, we've never had any problems with sound output, only with the built in microphones and the microphone jack. We've never been able to record sound.

---

### Post by josephus on 2007-05-01
i think it's supposed to say generic 14f1 5045, that refers to the chip that does the actual conversion from digital to analog/analog to digital.  if it is just a problem of a setting in a configuration file, i'm not sure what else to suggest.

---

### Post by sharke on 2007-05-01
jrz
Do you have alsamixer installed ina terminal alsamixer.
The reason i ask is i hooked a mike up on my ubuntu feisty system and it did not work opened alsamixer the only o volume was line adjusted same mike now works 
Regards
Sharke

---

### Post by josephus on 2007-05-01
in case you do decide to compile alsa here's how i would go about it:

download ver 1.0.14rc3 of alsa-driver, utilities, and library from [www.alsa-project.org/](www.alsa-project.org/)
unpack them 
go into the alsa driver directory
```
./configure --with-cards=hda-intel --with-oss=yes
make
sudo make install
```

in the first step if you run into errors then you need make sure you have whatever missing libraries before proceeding.  you might need to get the linux header files, but i think you already have it from compiling the ndiswrapper,  if not just go into synaptic and install it.

for the utilities and library go inside each of those directories and 
```
./configure
make
sudo make install
```

finally sudo pico /etc/modprobe.d/alsa-base 
and add to the end of the file
```
options snd-hda-intel model=laptop
```

i think it's pretty safe, but no guarantees.

---

### Post by sharke on 2007-05-01
I seem to remember having to install sox when i was runing debian before i could get sound recording to work cant hurt.
in terminal sudo apt-get install sox
Regards
Sharke

---

### Post by jrz on 2007-05-01
I open alsamixer from a terminal screen, and all 3 sets of sliders are at 100 and nothing muted.
The Gnome Alsa mixer comes up under Applications, Sound & Video, GNOME ALSA Mixer, and displays the same sliders, Master, PCM, and Capture, all maxed and nothing muted.

I would prefer to persue a fix not requiring me to compile a later version of ALSA, "If possible", but if it appears that will be necessary, I will give it a try as I'm not getting any further elsewise.
I've been looking through other posts as well to see if anything new has appeared, but have found nothing that helps. And it appears that most others have problems that are not quite the same as mine, as I have no problems with audio out, and many of those having microphone problems have low audio output, while I have none at all. I'm curious as what the difference between capture and microphone is as some have mixer screens showing both. I've also been on the ALSA site to see if I could find help there, but have had no success yet.

I installed 'sox' and tried to see if anything changed but still cannot record.

Edit:
I found the following on the NVidia website, and am uncertain if this helps as it only adds confusion to me, is it possible I am using the wrong drivers for the hardware installed?:

	
Linux nForce Drivers

All of the following drivers are open-source and are included in most popular Linux distributions. In most cases, the Linux installer will select the appropriate driver for the detected nForce hardware.
Component 	Platform 	             Use this driver
Audio (AC97) 	nForce-1 &#8211; nForce-4 	intel8x0.c
Audio (HDA) 	nForce-430 and later 	hda_intel.c

---

### Post by josephus on 2007-05-01
i'm pretty sure you are using the right driver.

the module that is being loaded up is snd_hda_intel which i'm pretty sure corresponds to the hda_intel.c that's mentioned in the note below.

---

### Post by jrz on 2007-05-01
Looking at your earlier post on ALSA, I looked at /etc/modprobe.d/alsa-base and am wondering if there is something there related to the problem? If you or anyone else is familiar with how this file is used and sees something that needs be changed please inform me.

rik@compaq:/etc/modprobe.d$ cat alsa-base
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
rik@compaq:/etc/modprobe.d$

---

### Post by colonelk on 2007-05-01
Hi Joe,

I'm not able to help with your problem but may I suggest that if you cannot solve it using Ubuntu 6.06 that you try installing Ubuntu 7.04 Feisty Fawn.  

I find its a much better distribution and  with respect to networking in particular it is miles better than 6.06 was as Network Manager (for configuring wireless networks) works out of the box on my rig with no issues at all.

Regards 

CK

---

### Post by jrz on 2007-05-01
colonelk:

The computer belongs to a friend and he is out of the country presently and expressed a desire to keep 6.06LTS so I'd have to first get his permission to change to 7.04 which I thought was not yet final. We're down to just 2 problems left to solve, and with no guarantee that 7.04 would solve all the problems, I'd prefer to stay with 6.06 also.

Edit:

Something I just tried is I found that the package mgr showed an 'alsamixergui' which I just installed to see what it would show, and it also displays 3 sets of sliders, Master, PCM, and Capture, but I notice that the sliders for Capture will not move, although they are showing maxed. Also the mute function does not work on PCM or Capture in the alsamixergui.

---

### Post by jrz on 2007-05-01
Josephus:

I have just come from the ALSA irc channel, where they claim I will have to install the latest alsa version, and just directed me to the wiki to find out how. I've downloaded the 3 packages you recommended, and opened them up. 

I may not have looked in the correct location on their wiki, but am debating if it is necessary to remove the existing alsa before trying to install a later version or not. Any suggestions there?

---

### Post by sharke on 2007-05-01
take a look at this post may help.
[http://ubuntuforums.org/showthread.php?t=102377&highlight=sound+record+dapper](http://ubuntuforums.org/showthread.php?t=102377&highlight=sound+record+dapper)
regarda
Sharke

---

### Post by josephus on 2007-05-01
i don't think you need to uninstall the existing packages, just overwrite them.

---

### Post by jrz on 2007-05-01
sharke: Well at least I'm in the majority group.
josephus: I went ahead and asked for some help on the alsa irc channel but they referred me to the wiki which left me with some more questions, so I just followed your instructions but found I needed a curses package, and later found someone else who was trying to get help with alsa who told me it was libncurses5-dev that I needed and that got alsa to install. I seem to have made a little progress as I now have sliders for internal and external microphones, but I have 2 sets of left and right external mics, and 3 sets of internal mics. I get some static and noise when I try to record now from the internal mics, but no voice, and using the external mic I can faintly hear voice. Not really great improvement, but headway anyway. 
I've been up all night and it's past 6 am so I'm going to try and catch a few winks and see what else I might be able to do. If either of you have any ideas I'll check and give them a try in a few hours. And thanks for both of you helping. The wireless is doing great at least.

---

### Post by josephus on 2007-05-01
that sounds like significant progress to me! just for future reference when you are compiling something and they ask for a missing package, just go into synaptic and search for the package name.  usually you it'll turn up something even if it not the exact package name.  you'll have to make an educated guess from there, and also usually they are looking the dev files for the package as well.

---

### Post by josephus on 2007-05-01
can you post a screenshot of your gnome-alsamixer? and output of amixer. also which program are using to record sounds  (not sure if it makes a difference, but at least we'll be on the same page).

edit:  try using audacity for recording sounds, at least while you try to debug this.  you'll be able to see the graphical waveform of the recorded sounds . this will help you when you are playing with the controls and will allow you to see in real-time the effects of moving up/down controls

---

### Post by jrz on 2007-05-02
I tried to get help on the alsa IRC to see if I could improve on the progress made, and ended up unable to boot the system except to a Failsafe terminal, and spent the remainder of the day trying to get the system back to normal, which required nearly rebuilding from scratch. I'm back to no mic, but the wireless continued to work even when everything else was broke. I think I'll take a break for a while before trying anything with the mic again. I didn't get a chance to get a snapshot of the mixer, but believe it was a fluke.
I think I'll read their wiki and try to get a better understanding of what needs to be done, as I sure don't want to go through that again.

---

### Post by josephus on 2007-05-02
what type of advice are they giving you on the alsa irc?  i'm interested in knowing what it takes to break the system that badly.

---

### Post by sharke on 2007-05-02
Sorry to hear you had a system break maybe thats a good reason to take time off just post back on this thread when ready to continue on.
Regards
Sharke

---

### Post by siiib on 2007-05-02
alternatively instead of messing around with ndiswrapper (i've never got it working either).. simply junk your wireless mini pci card and get another one off ebay for about ten quid that actually works with linux.. the intel ones are pretty good.. compile in the kernel and work out of the box.

---

### Post by jrz on 2007-05-03
siiib: Thanks, but if you read back previously in this thread you will see that the advice given by josephus has cleared my wireless problem quite well, and even during the major system problem I still retained a wireless internet connection and was able to acquire needed packages to restore the system to normal. I am very satisfied with both the advice given and the results it obtained. I would recommend anyone else having wireless problems look at the advice given earlier in this thread, and follow it exactly.

---

### Post by jrz on 2007-05-03
josephus & sharke:
I'm back after some hours of sleep. Getting up in age and can't put in the hours I used to.
On the alsa IRC most helpers there seem to feel the person with a question has just failed to read the wiki, or faqs and just direct you to the wiki telling you to follow the instructions exactly. In my case I was told that Ubuntu 6.06 contained very old alsa packages and the only solution was to install the Release Candidate version. I read the wiki before proceeding, and had several questions which I could not obtain an answer to from the alsa IRC, as no one available seemed to know the answers. 
The advice given was similar to that given here, and the questions I tried to ask were should I D/L and install the OSS Compat. Library, or was it not required with the 1.0.14rc3 version, no one knew, so I proceeded installing only 3 packages, the Driver, Library, and Utilities. I initially asked prior to installing if I should remove the old alsa, and like here it was said to be unnecessary, so I proceeded, and upon completion got the results I posted here. Later I opened the Synaptic Package Manager and it showed that the that alsa 1.0.10-4ubuntu4 was installed. That was when I questioned if perhaps I had a conflict which was causing so many microphone controls. This is when the problems began, when advice of how to remove the newly installed alsa packages to return to normal and try to find out what changes need be used in the installation process. The command given to uninstall I believe was "sudo make uninstall" done from each of the 3 directories that were used to perform the "make install". After completing this a reboot was done and the system would no longer boot, telling me that my session only lasted 10 seconds, and I should try coming up in a Failsafe mode and correcting the problem. I finally found the only mode that would come up was the Failsafe terminal mode, and from that point I had no idea what needed to be done to proceed and things only got worse following numerous attempts of various commands given by others, one of which appears to have deleted over 300 MB of packages and later required downloading for several hours from the repositories, which probably could have been done from the Ubuntu CD I have, but I didn't think of that at the time. The Failsafe terminal screen is a very tiny box in the lower left corner of the screen barrely readable due to my poor eyesight, and after many hours we were able to achieve a full screen terminal screen but no Desktop. Several attempts to reinstall the Desktop failed, and the alsa IRC said I should seek help from ubuntu IRC as it was a distro problem. No one was found there able to give help, and I finally found some help at the ubuntu-au IRC from someone who patiently worked with me for many hours until we got the system back to normal. the last typed commands to get back the Desktop were "sudo"
apt-get update
apt-get install gdm
apt-get install ubuntu-desktop
/etc/init.d/gdm restart
all done from the failsafe desktop login. Sorry for the lengthy post, but wanted to try and relate as much as possible in case it might be useful.
Right now I wish to try and acquire enough knowledge to try and install the latest alsa where it will not have both the old and the new versions installed for certain. I'm a little gun shy at the moment as I'm not certain I could recover from a similar event without help still.

Edit:
I nearly forgot, another reason for wanting to remove and try re-installing alsa was an additional problem also cropped up that didn't exist previously that I thought had to be related, and that was when I closed the laptop lid and later opened it the screen was unreadable, colors changed and icons were not recognizable, nor were the fonts readable until a reboot was done. That may be of importance, possibly due to NVidia being the hardware used both for video and sound?

---

### Post by josephus on 2007-05-03
it's really too bad that this has been such a difficult process.

i'll try to explain what happened to your system.  when we installed alsa by compiling from source we overwrote the asla files that were originally on your system.  unfortunately, the way that packaging system (apt/synaptic) works there is no way for it to have known that you've updated the alsa, that is why it continued to say that 1.0.10-ubuntu4 was installed.  in order for the packaging system to actually know of changes, you have to install things through the packaging system  this requires that you create .deb file from the compiled files (doing this could be another thread).

if you ever recompile alsa again and wanted to revert back to the original version, i think the easiest way would be to go into synaptic and reinstall the old alsa packages.  this will just overwrite the new version with the old version and therefore restore you back to your previous state.

anyway, i'm pretty sure there was no conflict between two versions of alsa as the previous version was replaced when the new version was installed.

it might be possible that the new alsa components were doing something with the video.  if it is an issue it might be related to acpi since it happens after you close your monitor (but i'm beginning to talk about things i know even less about).  you'll probably have to file a bug report to get that fixed.

i'm not sure having too many controls was an indication of anything bad happening with your system.  even on my system, i'm pretty sure i have knobs that don't actually do anything.

for the brief time that the new version of alsa was running, did you have a chance to fiddle with the controls to see if they had any affect on the mic?

at this point i'm not sure what advice to give you, but  if you have specific questions please feel free to continue to ask.

---

### Post by jrz on 2007-05-03
Josephus:
Hi, you mentioned acpi, and someone at the alsa irc mentioned something about a possible bug related to acpi, but didn't elaborate further. As this computer is my friends, and his first ever, the Pkg Mgr was probably the most appreciated thing he has noticed as it eliminates the need to look for dependencies and makes installation of packages much simpler.
About all I did while the new alsa was installed was try to record something, and I found the internal mics still did not work, but an external mic was able to produce a very weak voice recording. In both cases the recording attempts has a lot of noise when played back, but it was not background noise coming from the room.
I'm still a little confused as to what really needs to be installed as the alsa site shows 7 packages listed under the development release, and the OSS package shows ---, which I wasn't sure if that meant not required or that you should use the one listed under the stable release. I downloaded all of them just in case they might be needed, but only installed the three mentioned by you. The wiki didn't make clear which were needed and said to use the same command for other packages as  needed.
Is there any possibility of Ubuntu providing an update for alsa using the Pkg Mgr? It appears that many others are experiencing sound problems that an alsa update might improve if not fix.
It appears that although the system looks normal again, I am still missing something related to the audio which needs to be installed. If I click on the microphone to open the volume control it says "No volume control GStreamer plugins and/or devices found." The Pkg Mgr shows Gstreamer plugin for alsa installed. And aplay -l says "no sound cards found", but lspci -v still shows the Nvidia MCP51 High Definition Audio in it's output.
Perhaps some config file got corrupted in all the activity getting the system to boot and the Desktop restored?

---

### Post by josephus on 2007-05-03
you can request that certain packages be backported, which basically means that a newer version is compiled and added to the backport repository.  from my understanding they will only backport things that are either in the edgy,feisty, so it is unclear which new version of alsa they would be willing to provide.  but it might be worth a try nonetheless.

i think that the only thing that is really need is the alsa-drivers. but i think alsa-tools and alsa-library are up there in the priority of things used.  the oss compatibility layer is only needed if you want oss applications to be piped through alsa. looking at my own installation this package is not enabled by default.

----

right now can you get any sounds to play?  maybe the driver is no longer being loaded up at boot.  post 'more /proc/asounds/*'.  the other thing that i would try is to use synaptic to reinstall the packages related to alsa.  just search by name for alsa, and an reinstall the packages (Package->Mark for reinstallation).

---

### Post by jrz on 2007-05-03
Josephus:

First /proc has no asounds directory in it. Not sure where it comes from, and do you think reinstalling alsa might create it?
The Pkg Mgr displays the following pkgs installed and up to date when I search on alsa:
alsa-base
alsa-utils
gstreamer0.10-alsa
libasound2
libesd-alsa0
libpt-plugins-alsa
libsdl1.2debian-alsa
linux-sound-base
If I were to do a reinstall, should I mark each and every one of those?
I just tried to play an audio file and there is no sound

Perhaps my friend, and I have misunderstood what ubuntu 6.06 LTS meant. His departing statement was he didn't want me to install a new version as he wished to keep the LTS version, for "Long Term Support." I think both of us have/had the feeling that this version would be kept up to date an most stable in comparison to the other versions, and he remarked about reading of problems with feisty so he wished to avoid that.

---

### Post by josephus on 2007-05-03
try

more /proc/asound/*

/proc is not an actual file on your hard drive.  it refers to a memory location.

---

### Post by jrz on 2007-05-03
That returns /proc/asound/*: No such file or directory

---

### Post by josephus on 2007-05-03
i'm pretty sure your sound module isn't being loaded up.  post 
```

lsmod | grep snd
```

you should probably have the entry : snd_hda_intel

if not try loading it up
```

sudo modprobe snd_hda_intel
```

---

### Post by jrz on 2007-05-03
Having access problems to ubuntu forums. Hopefully this time will send


rik@compaq:~$ sudo modprobe snd_hda_intel
WARNING: Could not open '/lib/modules/2.6.15-28-386/kernel/sound/acore/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-28-386/kernel/sound/acore/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-28-386/kernel/sound/acore/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-28-386/kernel/sound/acore/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-28-386/kernel/sound/pci/hda/snd-hda-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.15-28-386/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
rik@compaq:~$

---

### Post by josephus on 2007-05-03
can you check if those files are on your system somewhere not being referenced properly?

```
cd /lib/modules/2.6.15-28-386
find -iname 'snd-page-alloc.ko'
```

my guess they were deleted after issuing the 'sudo make uninstall'  command for alsa-drivers.

i think to get them back you need to reinstall the linux image file.  just go into synaptic and look for linux-image and find the current version and mark it for reinstallation.

---

### Post by jrz on 2007-05-03
josephus:

The find command returns nothing, and when I look for linux-image in the Pkg Mgr, and check it for reinstall it said it could not be authenticated, but appears that a reload cleared that and it installed and upon reboot said two additional pkgs needed to be updated which I did also, libsnmp-base and libsnmp9. The volume control is now working and I can play the recording I made while the latest alsa was installed, using Totem and with VLC.
I guess that has everything back to normal again?

---

### Post by jrz on 2007-05-03
I did a little further testing and the sound recorder still does not record, but the file I created and saved with the new alsa installed will play back using it. I also notice that now the headphone jack does not work but it did previously. My friend doesn't have a headset so he doesn't use it, although we found it worked using my headset previously. Other than that everything looks like previously.

---

### Post by josephus on 2007-05-03
looks like it.   i'm going offline for a couple of hours so won't be able to answer your questions until tonight.  i'm not sure your next move should be.  it looks like you might be able to get your mic working with the new ver of alsa, but that results in the bug with your video.  i guess you have to decide which one is more important.  the other option is to look for an external usb mic -  it wouldn't hurt to make another post to see if there are usb mics which work right of the box with dapper.

---

### Post by jrz on 2007-05-03
That sounds fine, I'm still a little worn out myself and it's 10pm here so I may just hit the sack and see if I can get some more energy before proceeding further. I think I will try and read some more at the alsa wiki site and see if there might be something helpful there as well before trying to install alsa again. I appreciate all the time and help you've given, and am still tickled to death that you got our wireless problem solved.
Thanks again.

---

### Post by pinkertime on 2007-05-03
Hi,
I had a similar problem with my mic on a compaq notebook with a conexant audio chip (ICH7), but i have solved it. The only solution is to compile the latest alsa driver (the rc3  and if this is not enough add the latest daily snapshot of the alsa-driver from [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver")).
Install it using these step by step instructions: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") 
The problem is that the intel-hda driver is under heavy development by the alsa team.

Please give it a try it is very simple and may solve the problem!

---

### Post by jrz on 2007-05-03
pinkertime:
 Thank you for that info. I will look into it but after the problems I just had after installing  the alsa rc3 following the alsa wiki, I think I will take some time reading over what has to be done first. I'm very unfamiliar with linux and hate to get into problems requiring me to burden others for an enormous amount of help. I've received from very good help here and don't wish to become someone to avoid. I still feel Linux is the best OS, but due to the proprietary restraints it is difficult to produce software that works immediately for every system configuration. Being a unix user all my working life I thought that would make things easier, but there appears to be many differences to contend with, and I haven't seen a unix system for about 10 years now.
I'm going to read the How To now, and if I get up the nerve to use it I'll post any results to let you know the outcome. Thanks again.

---

### Post by jrz on 2007-05-04
Josephus:

Was that you on the alsa IRC minutes ago? I tried to respond but it appears you disconnected before I could. I've been having difficulty using the internet here today as we've had a monsoon rain, and the cloud cover is really thick, causing me dropouts. I've spent all day reading everything I can find on the alsa website and was trying to get answers to some questions before I attempt to try anything with a new version of alsa again. The more I read the more questions I come up with, perhaps I've become paranoid about doing anything related to alsa after 2 major mishaps. One question I wanted to see if I could get answered is "can you determine prior to trying to do the install if there are any needed dependencies that are missing", and I'm not sure if I have need for OSS or not so I wanted to know if there was someplace to look to see if it was needed. I've run across some conversations that mentioned running alsaconf, but I don't seem to have that on my system. Someone else made comment that 2 different alsa kernel modules cannot exist, and left me thinking the driver package contained another kernel module that would cause conflict. And the wiki mentioned something about the 2.6.xx linux kernel having alsa built in. Nearly each line I read left me with questions.

---

### Post by josephus on 2007-05-04
yeah that was me, but my connection dropped briefly.   i just wanted to see what it was like after your comments.  it's not a very active channel.

i'm pretty sure you had it right the last time you installed alsa.  the support for you card is still underdevelopment, so each new version will bring more functionality to your mic.  i looked at the change log, and rc4 has some new changes over rc3.  

i think you shouldn't worry about oss, just try to get alsa working by itself first.

---

### Post by jrz on 2007-05-04
What about dependencies? Can that be checked prior to installing? I had briefly installed CentOS on my notebook once before and it used to inform you of dependencies needed in advance, but I forget what you had to type. But trying to find the proper ones was so difficult that I quickly gave up on it.
And I believe it was you that mentioned something about making a package that could be installed from the package manager ?  Would that be worth the effort?

---

### Post by josephus on 2007-05-04
dependencies for alsa?  you have everything you need for alsa to work.  when you are compiling, the ./configure script will let you know if you are missing anything.  

dependencies among packages in general is handled automatically by apt/synaptic.  if you click on any package in synaptic and look at the properties it tells you the packages that they depend on.

i'm not sure what would be gained by packaging alsa, at least it won't get it to work any better.

at this point i'm still unclear why you think things went wrong last time.

---

### Post by jrz on 2007-05-04
Last time I received an error of a missing curses package, which I forgot the name of and am uncertain if it is still installed after losing so many packages. I'm not sure what went wrong and why the video was affected, which was probably the most major problem, but the mixer was a little confusing having so many sliders and the internal mics didn't work at all even with all 5 sets of sliders at maximum. The wiki has some additional commands  all of which are sudo modprobe ..., and I don't understand if they are required or not, as I don't know what the words following modprobe relate to. If you feel pretty certain that a recovery can be accomplished if problems appear I am willing to give it another shot. I just wouldn't like to go through the same recovery procedure as previously if at all possible.

---

### Post by josephus on 2007-05-04
just check in synaptic, but i'm pretty sure libncurses is still on your system.

there is no guarantee that the problem with video will be fixed this time around.  i'm pretty sure it wasn't an installation issue.

if install the new version and want to revert back to the old version, i think the right method is to go into synaptic and reinstall alsa-base, alsa-utils and the linux-image file.

the modprobe stuff isn't really necessary, only if you wanted to insert the modules right away instead of waiting for a reboot.

---

### Post by jrz on 2007-05-04
I remembered the Pkg Mgr had a history record, and I found the curses pkg that was installed there and it is showing installed still.
The wiki makes mention of Debian users running the following 1st:
> apt-get install libasound2 alsa-utils alsa-oss
But I'm sure if that applies to Ubuntu or not. I'm just trying to assure that my problems were not due to skipping over something as the alsa IRC just told me to go to the wiki and follow it exactly, and I skipped that step before.

> Kernel 2.6.XXX users:

If you have a kernel from the 2.6.xxx series, ALSA is already included, so it's not necessary to do all these steps.

I have 2.6.15-28-386 

> Make sure you have a kernel source tree that you've already compiled from. This should be in /usr/src/linux 

I don't have that directory.
From that point I have already downloaded each of the packages and they have been un-tar'd into /usr/src/alsa waiting to be compiled and installed.

 >   cd alsa-driver-xxx
   ./configure --with-sequencer=yes && make
   make install

The wiki gives this command, but the command you gave originally sounds more reasonable, if sequencer relate to MIDI.

These are about the only questions I have before proceeding if you see nothing there important I guess it would be appropriate to begin with the alsa-driver pkg  followed by the libraries and utilities .
I'm assuming the driver options you gave would in fact be preferred?

---

### Post by josephus on 2007-05-04
with regards to 
> 
apt-get install libasound2 alsa-utils alsa-oss 

the wiki is saying that you don't need to compile everything from source if all you want are the latest drivers.   so rather than compiling the latest version of alsa-lib you can just install libasound2 from the repo, and likewise for alsa-utils and alsa-oss.


> 
Kernel 2.6.XXX users:

If you have a kernel from the 2.6.xxx series, ALSA is already included, so it's not necessary to do all these steps.


this just means that alsa was included in the kernel.  however, we want the latest version of alsa so it is still necessary to compile.

> Make sure you have a kernel source tree that you've already compiled from. This should be in /usr/src/linux

basically telling you it needs to have the linux kernel header files somewhere on your computer which you have or else you wouldn't have been able to compile stuff earlier.

i think the compiler options that i gave were ok.  i don't know if the if the oss option that i had was necessary.  maybe you can omit it this time around.

---

### Post by jrz on 2007-05-04
OK, I'll begin now, and post the results when finished. It may take a little while so if you have something else to take care of I'll post the results and when ever you get time you can take a look. Thank you for being so patient.

---

### Post by josephus on 2007-05-04
sure, all these posts are emailed to me so i'm notified nearly immediately even when i'm not on the forums.

---

### Post by jrz on 2007-05-04
Josephus: 
I'm on the last pkg, the utils and happened to look back at my other computer and noticed that they have just made a change to alsa today and now it is rc4. Is it possible to just download the new packages and without removing the drivers and libraries, create the new packages and install them instead over top of what I have just done? 
I wasn't expecting any changes to take place so quickly. OR should I just go ahead an finish what I'm doing now?

---

### Post by josephus on 2007-05-04
yeah, that's probably the best thing to do.

---

### Post by jrz on 2007-05-04
OK, I'm downloading them now, I hope they don't come out with rc5 tomorrow. I'll post a message when completed.

---

### Post by jrz on 2007-05-04
Josephus:
I just finished and rebooted. The volume control now shows Master, PCM, and 2 dual slider Ext Mics, and 2 dual slider Int Mics. I tried to record from the internal mics and they work, but are not associated with any of the volume controls. In fact I set all 6 sliders to 0 and muted all 6 items and still was able to record with no change in volume. The only controls that have effect are Master and PCM which affect the audio output. The external mic is just faintly audible if you put your ear on top of the built in speakers. It appears that the headphone jack disconnects the speakers as no audio is heard at all when they are plugged in so they don't appear to work at all.  I even tried to see if the mic and headphone jacks were crossed in wiring which also didn't work. I saw something called JACKS in a post, but don't know if if relates to physical jacks or just the name of an application.  Maybe there is something left for me to do? I just closed the lid and will wait a moment or two and see if the video display is corrupted or not. Nope, the video came up fine. So it looks like real progress this time, the noise that persisted is gone and the internal mics appear to have fairly good output if you are close, there's no feedback, so I assume they are not really set to full volume as the speakers are only 8 inches below them and I even tried placing a reflector to force feedback but none occurred. It might be necessary to try and find out why the external jacks are not working as that would probably be the only way one could work in the field.
But you've done it again, we seem to have a working mic finally.

---

### Post by josephus on 2007-05-04
is there a mic boost option?  sometimes not all the options on the mixer are listed until you go into the preferences menu and make them visible.  i think to get full functionality from your mic you'll have to check alsa from time to time and update to the latest release.

---

### Post by jrz on 2007-05-04
There's no changeable options on the mixer, which is Volume Applet 2.14.3, Volume control for you Gnome Panel, using gstreamer 0.10.
Maybe I need an alsa mixer? I think I had installed alsamixergui previously and it may have more controls? If that be the case would there be a conflict by having 2 mixer controls?

---

### Post by josephus on 2007-05-04
you might have the gnome-alsamixer installed and definitely should have alsamixer installed.  

there is no harm in having more than one mixer installed as they are just provide different user interfaces to the same controls.  but even with the volume applet you should be able to access all the controls.  it's more likely that the mic boost is currently not supported.  remember alsa drivers are under heavy development and your card is only starting to be supported in this latest release.  only time will make things better.

-----

just looking at the options available when loading up the module you can edit the /etc/modprobe.d/alsa-base

change the last line from
```
options snd-hda-intel model=laptop
```
to
```
options snd-hda-intel model=test
```

this will provide with more controls (i don't know if they actually do anything - they probably don't).  but for this to work you have to recompile the drivers with an extra option

```
./configure <whatever you had before> --with-debug=basic
```
or possibly
```
./configure <whatever you had before> --with-debug=full
```

and then 
```
make
sudo make install
```

again i don't know if having the extra controls actually will do anything but if you want to give it a shot, go right ahead.

---

### Post by jrz on 2007-05-04
I found that I have alsamixer, and it has to be opened from a terminal screen.
It shows sliders for: 
 Master, PCM, IEC958, ExtMic, IntMic
while the alsamixergui shows controls for:
Master, PCM, LineIn, IEC958, ExtMic, ExtMic, IntMic, IntMic, IntMic
Perhaps I should persue this on the alsa IRC channel?
Oh, and after I installed the alsamixergui a test recording was made and there is background noise that didn't exist prior to installing it.

---

### Post by josephus on 2007-05-04
alsamixergui likely changed some setting.  you'll have to play with it until you get an acceptable result.

---

### Post by jrz on 2007-05-04
Josephus:

I'll try playing around some and see what I can find, and in addition to your getting us to make great headway on our most major problems you've done much to build my confidence in trying out things. I do think I might ask a question on the alsa IRC mainly to see if someone knows where the 20db boost comes from as I believe I should be able to get feedback between the mikes and the speakers.
I think you've done enough for today, and I hope I haven't put you to too much trouble. I really appreciate all your help, and my friend will also when he sees he now has a working wireless, and can record for the first time. If I can make further progress I will post it here for your info as well as anyone else who may be having a similar problem that might find it useful.
Thanks very much.

---

### Post by jrz on 2007-05-04
Josephus:

I just got off the alsa IRC and gnubien looked at my problems and asked me to dump a couple of files, below is the content of what was said:

I finally got the alsa update installed, after nearly completing and finding that a new rc4 had cropped up today. I have rc4 installed and it has cleared some audio problems, and created some new ones, plus I have some questions which I have not found answers to. Anyone wish to try and provide some assistance and some answers?
z9999:ill attempt..heh

wishie: Thank you. Running ubuntu 6.06 I had good audio out both at the speakers and the headset, but no microphone. RC4 seems to have got the internal mikes working, although low level, but the headphone jack no longer works. I have several other items but am unsure if it would be better to give them one by one.

--- At that point wishie had company, and gnubien came on to give help

z9999: alsamixer have a 'mic boost" control? set it to ON
gnubien: I don't find one, and that was going to be another question as I don't know what it is that makes it appear.
z9999: alsamixer -V all #some cards have no Mic Boost control 
z9999: ok, no Mic Boost for your card yet; card name change with alsa upgrade happens sometimes

gnubien: the chip now shows Conextant CX20549 (Venice) - I believe it used to show Generic 14f1 ID 5045. Is that normal?
z9999: probably, Conextant alsa support is fairly new, change from generic to Conextant is normal with alsa upgrade

gnubien: One more oddity is 2 external and 2 internal mike volume controls in alsa mixer, and alsamixergui shows 2 external and 3 internal each with a L and R channel.
z9999 amixer >> amixer.txt use the upload link at pastebin.ca for the .txt file, no pasting needed
gnubien: Sorry if I'm not proficient at this, [http://pastebin.ca/470875](http://pastebin.ca/470875)

z9999: amixer scontrols >> amixer.controls.txt use the upload link at pastebin.ca for the amixer.controls.txt file, no pasting needed
gnubien: that's [http://pastebin.ca/470882](http://pastebin.ca/470882)

gnubien: I should also let you know that the int mic records, but none of the mixer controls have any effect even if I mute all of them.
z9999: you have alsamixer control 'Ext Mic','Int Mic' and 'IntMic'; 'IntMic' is set to ON now, you using the internal or an external mic to test recording?
gnubien: I've tried both but only the internal mic records audibly. The external mic is barely audible if you place your ear on the speaker, and the headphone jack doesn't output anything although it worked prior to installing rc4.
z9999: no fix known except wait for the next version of alsa cvs to be released

gnubien: OK, well thanks for you time and help. I'll keep an eye open for it.


I thought I'd pass this along as you have been involved more than anyone and wanted you to know where alsa stands at the moment. I guess they're making many changes so maybe the one I have will be cleared soon.
So I guess I'll just have to keep looking for a new update and give it a try. 

Joe (Thailand)

---

### Post by anirban.sam on 2007-05-05
Type alsamixer and press enter in a console to launch alsamixer. Disable all ICE devices in alsamixer and unmute all muted. Save settings by typing "sudo alsactl store".

---

### Post by jrz on 2007-05-05
anirban.sam:

Looking at alsamixer, I see something labeled IEC958 with no control above it. Is that what you mean? I can't do anything to it when I highlight it though. And nothing is muted.

---

### Post by jrz on 2007-05-06
josephus:

I feel like a complete idiot, but feel it necessary to make this post even if it confirms such.
I had just about given up on the previous posted alsa problem, when I wanted to listen to an audio book on my computer while my daughter was watching a cartoon on another computer next to me. Having to plug in the headset earphones, I recognized that the plug color I was plugging in happened to be the same as I have been plugging in to the mic jack on my friends computer. I quickly went to my friends computer and tried the other plug colored red in the mic jack and found I could record from the external jack, I also tried inserting the blue plug into the earphone jack and found that I had audio in the headset. It appears that the alsa rc4 packages has cleared all my audio problems and the only remaining problem was found to be the user, ME.
Thanks for all your help and it appears that you had also fixed my audio problem and the only remaining problem was me.

---

### Post by josephus on 2007-05-06
well it sounds like it wasn't really your fault, and definitely would have been a mistake i would have made were i in your place.  glad everything worked out.

---

