---
title: "No sound in Ubuntu 10.04 RC"
date: 2010-04-29
forum: Hardware
---

### Post by anomajaya on 2010-04-29
Hi,

I'm very new to Linux. I installed Ubuntu 10.04 RC in HP Compaq CQ62-111TU ( C=Intel Core i5 430m + 4GB DDR III + Intel HD audio) It works fine except for no sound from 2 speakers. But I can listen to sounds through head phone jack. External mic is also working fine but internal mic do not. I went through a one of the threads in this forum on sound problems but it didn't resolve my problem. Some of the information regarding my heardware generated with the Terminal are given below.


noma@anoma-laptop:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



anoma@anoma-laptop:~$ lspci -v

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Hewlett-Packard Company Device 1425
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

( When boot with win 7 it shows that there are two audio drivers 1.) Intel HD audio
2.) Realtek audio )

Can any one help me to get my laptop's sound properly?

Looking for an early reply,

Thanks,

---

### Post by proxess on 2010-04-29
Change the volume directly with alsamixer or sudo alsamixer. Worked for my USB headset.

---

### Post by anomajaya on 2010-04-29
Volume is already increased to Max using Alsa mixer. But still not working..!!

---

### Post by simon_w on 2010-04-29
I'm having the same problem with the same HDA device :(

I notice that 10.04RC is using alsa 1.0.21 (cat /proc/asound/version), and that the final release should have 1.0.22 ([http://packages.ubuntu.com/lucid/alsa-base](http://packages.ubuntu.com/lucid/alsa-base)) so I'll try that tomorrow before I investigate further.

:(:(

---

### Post by lidex on 2010-04-29
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by simon_w on 2010-04-29
Hi lidex, thanks for your interest in helping with this.  I'm away from my shiny new problem machine for the time being, but will post the information you ask for when I get back to it, in the hope that it might generate some suggestions.

The laptop in question a Dell Studio 1458, and the output from `lspci` is identical to anomajaya's (except, of course, that it reports a dell subsystem, instead of a HP one).  My symptoms are also identical.

For now, my plan of attack when I get home is to install the release version of Lucid, and then begin editing `/etc/modprobe.d/alsa-base.conf` and trying out all the various model options that I can pass to the `snd-hda-intel` module.  Do you know where I can find a definitive and current list of these?

[Edit:  here it is - `/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz`]

(FYI, a quick test last night on 10.04RC1 using `model=dell-m6` and `model=dell-bios` didn't help at all :()

If I still have no success, then I guess I'll compile the latest ALSA drivers from source (or would you recommend the `ubuntu-audio-dev` PPA?) and see if that helps.  Then I'm on to posting debug info at alsa-project.org, I suppose :(

I'm beginning to wonder if this new laptop was a mistake - I've already had to solve driver problems with the WLAN and graphics chipset, and I haven't even looked at things like HDMI or the webcam yet....  Ah well, "once more unto the breach", eh?

:)

---

### Post by simon_w on 2010-04-30
Well I finally got a chance to look at this, and I believe I've solved my issue.  It seems I have an audio chipset that uses a very new codec - Realtek ALC665.

```
cat /proc/asound/card*/codec#* | grep Codec
```

The solution was to compile a special version of the alsa driver (1.0.22) provided by Realtek which includes the necessary driver.  I obtained the driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false").

I only actually needed to compile and install the alsa-driver itself - the libraries and utils from the Lucid install are compatible.

```

tar xf LinuxPkg_5.14rc6.tar.bz2
cd realtek-linux-audiopack-5.14/
tar xf alsa-driver-1.0.22-5.14rc6.tar.bz2
cd alsa-driver-1.0.22
./configure --with-cards=hda-intel
make
sudo make install

```

after a restart, I have everything working perfectly (touch wood!) - speakers, headphone jacks (both of them), internal mic...

Hope it works for you too!

simon

---

### Post by jakslev on 2010-04-30
> **proxess said:**
> Change the volume directly with alsamixer or sudo alsamixer. Worked for my USB headset.

Proxess is your USB headset working flawlessly? Under 10.04 I never sure what applications will send the sound to the headset and which will send the sound to the speakers. You experienced this too?

jakslev

---

### Post by kr651129 on 2010-05-02
Okay, so none of the above worked for me.  But then I remembered that I upgraded from 9.10 to 10.04 by command line and I was getting audio.  But I wanted a fresh install and that's when I had no audio.  So I think I've got a really out of the way workaround.  I'm going to do a clean install of 9.10 then upgrade by command line to 10.04.  I'll let everyone know how it goes.  By the way here are my system details

```

> aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> uname -r
2.6.32-21-generic

```

Intel Chip
Dell
64 bit

---

### Post by jakslev on 2010-05-02
I got the sound in USB to work in one application (SecondLife) by forcing it to use the alsamixer. i suppose something is messed upi somewhere in the new 10.04 - and I hope that enough people use USB headphones and notices the problem so it ca be fixed...

looking forwards to hearing how the update thing goes - and to see what the config file reads then!

---

### Post by Joe on 2010-05-02
Hey you guys may want to try the solutions posted here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I'm running a desktop with a Core i3 with Intel HD audio as well and couldn't get audio outputted via HDMI (although analog out worked ok) until I took the steps listed under Alsa Driver Compilation.  However, I'm still not able to get sound out of the web browser and I'm unsure why but you may have better luck than me.

---

### Post by claytontlewis on 2010-05-02
I also have no sound from 10.04. I'm using an Asus G51VX.

```
Linux clayton-ubuntu-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Advanced Linux Sound Architecture Driver Version 1.0.21.

Codec: Realtek ALC663
```

I've been using netbook remix on my Eee PC for a while and love it, but now that I've finally put the full version on my laptop it is biting me in the *** :(

---

### Post by lidex on 2010-05-02
> **claytontlewis said:**
> I also have no sound from 10.04. I'm using an Asus G51VX.

```
Linux clayton-ubuntu-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Advanced Linux Sound Architecture Driver Version 1.0.21.

Codec: Realtek ALC663
```

I've been using netbook remix on my Eee PC for a while and love it, but now that I've finally put the full version on my laptop it is biting me in the *** :(

You've tried all the basic defaults, levels, etc? Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.
Still no sound? Install the alsa-backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` and reboot.

---

### Post by claytontlewis on 2010-05-02
> **lidex said:**
> You've tried all the basic defaults, levels, etc? Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3  
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.
Still no sound? Install the alsa-backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` and reboot.


I've done all that except for installing the backports. I'm installing those now.

---

### Post by claytontlewis on 2010-05-02
Installed backports and rebooted.

Now it recognizes no sound cards at all.

:(

---

### Post by lidex on 2010-05-02
So aplay - l says no soundcards detected?

---

### Post by claytontlewis on 2010-05-02
> **lidex said:**
> So aplay - l says no soundcards detected?

Yes.

---

### Post by simon_w on 2010-05-02
@claytonlewis

The ALC663 codec that your Asus is using is very new, and the drivers aren't bundled in ALSA yet (not even in the backports repo, it seems).  You *need* to use the version from Realtek that has the driver included, which I linked to in my post.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")

[Edit: - you will probably need to remove the backports version and the line in your alsabase.conf]

You shouldn't need the whole installation process if you're running Lucid - here again are the only steps I needed:

[http://ubuntuforums.org/showpost.php?p=9203173&postcount=7]("http://ubuntuforums.org/showpost.php?p=9203173&postcount=7")

Here, for the record, are a list of the codecs supported in this package (from the readme):

====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC259
ALC269
ALC270
ALC272
ALC273
ALC275
ALC660
ALC660VD
ALC661
ALC662
ALC663
ALC665
ALC670
ALC680
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A
ALC892


@jackslev - to get more control over which audio sources are played on which output devices, try installing the PulseAudio Device chooser.  You should have complete control:

```

sudo apt-get install padevchooser

```

Good luck!

simon

---

### Post by claytontlewis on 2010-05-02
@simon_w OK, I followed through with all of that and I've somehow made my problem worse. There was no .22 in the package I downloaded but there was a .23 so I continued on with it assuming it was a newer version. Now I can't launch alsamixer (not found) and I still have no driver showing up.

---

### Post by simon_w on 2010-05-02
okay - no problem.  if you've installed .23, the plugins, libs and tools from Lucid (.22) probably won't play nice, so you'll need to install those three from the Realtek package as well, so that they're all compatible.

There are a few ways you can go about this, since these three packages in the Realtek bundle are not different from the standard distribution.  However, I would simply compile the source in the same bundle and be done with it, if it were me.

The order doesn't matter, but you must install all three (additional) packages, and then reboot.

so that's: 1) unpack the archive;  2) cd to the newly-created folder;  3) ./configure;  4) make;  5) sudo make install


Let us know how you get on :)

simon

---

### Post by claytontlewis on 2010-05-02
OK, I'm going to try that. In my haste I've attempted to apt-get remove --purge all of alsa and then apt-get install --reinstall it all. On the reinstall I can't fine the alsa-module that I removed. So who knows what I've done now.

---

### Post by claytontlewis on 2010-05-02
I can't get the alsa-utils directory to work. When I run ./configure it isn't creating the Makefile. There is the configure.in, Makefile.am, and Makefile.in. So I have no idea why the Makefile isn't being created. 
<rant>
I've been telling everyone all week how great the new Ubuntu is and now I can't even make simple sound to work! Created by programmers for programmers I guess.
</rant>

Awaiting the next suggestions.

---

### Post by claytontlewis on 2010-05-03
Noticed an Install file in that RealTek tar. I ran it. Who knows if that was a good idea or not, but it reported the following

```
./install: 109: alsaconf: not found

```

---

### Post by kr651129 on 2010-05-03
I'm pleased to say I've found the workaround.  Clean install 9.10 32 or 64 bit do all your upgrades.  Then from the upgrade manager go to 10.04, works perfectly now!

---

### Post by simon_w on 2010-05-03
@claytonlewis -

don't despair!  The audio controller you've got is very new, that's all (the datasheet is dated Dec. 2009).  You'd have the same difficulty (probably worse) with any OS if the drivers weren't provided pre-installed.  Realtek have done a great job providing the support, but if the laptop vendors don't care enough to support linux, even to give a link to realtek on their product pages, then it's tough to find what you need.  (i've already written a letter to Dell to this effect - the problem is that they're deeply beholden to MS, especially with the Windows 7 -style licensing system.  But now I'm starting to rant....).

okay, first things first:  the install script in the archive is for RedHat/Fedora only.  It does explicitly say in the readme *not* to run it on Ubuntu....  however, it shouldn't have done any harm.

when you say "all of alsa", what do you mean?

If you install the alsa packages from the Realtek bundle, I think you'll be okay.

First install the plugins and libs packages, then extract and cd to the utils package.

Create some symlinks:

```

sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so

```

and then ./configure etc.

(I've just done a test with the .23 files - although admittedly on the Karmic machine that I'm currently sat at - and everything's gone fine).

(Note:  you basically should follow the instructions [here]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/"), but using the Realtek bundle)

[Edit:]
note especially that you may need some extra packages to complete this process successfully.  (If you've already successfully compiled the drivers, you're probably okay, but it's worth checking.)  As per the link above, use:

```

sudo apt-get install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get install linux-headers-`uname -r` libncursesw5-dev

```


Keep going - you'll get there!

simon

---

### Post by simon_w on 2010-05-03
@kr651129

> **kr651129 said:**
> I'm pleased to say I've found the workaround.  Clean install 9.10 32 or 64 bit do all your upgrades.  Then from the upgrade manager go to 10.04, works perfectly now!

What issue is this a workaround for?

If you really had perfect audio on Karmic and it's broken on a clean Lucid install, then this sounds like it could be a genuine regression bug, and you really should report it if you can.

[http://www.ubuntu.com/community/reportproblem]("http://www.ubuntu.com/community/reportproblem")

---

### Post by kr651129 on 2010-05-03
> **simon_w said:**
> @kr651129



What issue is this a workaround for?

If you really had perfect audio on Karmic and it's broken on a clean Lucid install, then this sounds like it could be a genuine regression bug, and you really should report it if you can.

[http://www.ubuntu.com/community/reportproblem]("http://www.ubuntu.com/community/reportproblem")

I had no problems with audio on karmic at all outside of my flashplugin wich was simple enough to fix.  The only way for me to fix this issue was a clean install of Karmic with and Upgrade to Lucid.  I'll report it now, but I'm interested to know if this solution can be confirmed by anyone else, that is to say it will take around 4+ hours of work so don't just jump into this "workaround" unless no other solutions have worked for you.

---

### Post by lidex on 2010-05-03
You can download the linux realtek driver here:
[http://152.104.125.41/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false]("http://152.104.125.41/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")
BTW, the datasheet for the ALC663 is dated May of 2008. 
Bug report with workarounds:
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65752]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65752")

---

### Post by simon_w on 2010-05-03
@lidex -
> BTW, the datasheet for the ALC663 is dated May of 2008. 
my apologies, thanks for the correction (I was looking at the wrong one).  Any insight, then, on why the driver isn't supported out-of-the-box with ALSA?

(ps. - the driver link you supplied seems to be broken.  Is it the same one I supplied above?)

---

### Post by lidex on 2010-05-03
> **simon_w said:**
> @lidex -

my apologies, thanks for the correction (I was looking at the wrong one).  Any insight, then, on why the driver isn't supported out-of-the-box with ALSA?

(ps. - the driver link you supplied seems to be broken.  Is it the same one I supplied above?)

There have been some support at least since 1.0.20. It's not so much the individual codec but how the hardware pin assignments are implemented. Realtek ships a specific driver for windows. ALSA has to implement all the configurations under one umbrella, so to speak, and has to read bios information to autoselect and the bios is frequently inaccurate. That's where all these switches come into play - to tell alsa to reconfigure to the hardware.

Probably the same driver. I hadn't noticed your link. Way too many hours online today. US site not redirecting properly for some reason.

---

### Post by simon_w on 2010-05-03
> **lidex said:**
> There have been some support at least since 1.0.20. It's not so much the individual codec but how the hardware pin assignments are implemented. Realtek ships a specific driver for windows. ALSA has to implement all the configurations under one umbrella, so to speak, and has to read bios information to autoselect and the bios is frequently inaccurate. That's where all these switches come into play - to tell alsa to reconfigure to the hardware.

Thanks, that makes good sense.  Thankfully the detection sequence is successful on my new laptop, and additional configuration switches are not required.  I assume this result is a combination of helpful information in the PCI configuration registers, and using a driver package which knows how to configure the other parts of ALSA on the basis of that information.

Cheers :)

simon

---

### Post by claytontlewis on 2010-05-03
WOW! It is finally fixed. I had to install those extra packages you mentioned to get it to work, but it is working now.

Thank you so much for your help.

---

### Post by simon_w on 2010-05-03
Cool :)  Hopefully support for these codecs will be available out-of-the-box in future versions of ALSA and Ubuntu.

With newer hardware, especially on laptops, we will occasionally run into these kinds of issues, but it's soooo worth it :)

---

### Post by metro2005 on 2010-05-03
what did the trick for me was removing pulseaudio. 

```

sudo apt-get remove pulseaudio

```

I then installed gnome-alsa mixer for controlling volume and everything worked again. I had the same issue in 9.10 but when i did the upgrade ubuntu re-installed the pulseaudio horror. 

I also edited /etc/modprobe.d/alsa-base.conf with this line at the end:

options snd_hda_intel model=acer-aspire



These are the codecs i have: 

Codec: Motorola Si3054
Codec: Realtek ALC883



Hope that also helps!

---

### Post by jakslev on 2010-05-03
> **simon_w said:**
> @kr651129



What issue is this a workaround for?

If you really had perfect audio on Karmic and it's broken on a clean Lucid install, then this sounds like it could be a genuine regression bug, and you really should report it if you can.

[http://www.ubuntu.com/community/reportproblem]("http://www.ubuntu.com/community/reportproblem")

I agree - this is a regression. Works fine in 9.10 and is not working on clean install with 10.04

---

### Post by jakslev on 2010-05-03
> **kr651129 said:**
> I had no problems with audio on karmic at all outside of my flashplugin wich was simple enough to fix.  The only way for me to fix this issue was a clean install of Karmic with and Upgrade to Lucid.  I'll report it now, but I'm interested to know if this solution can be confirmed by anyone else, that is to say it will take around 4+ hours of work so don't just jump into this "workaround" unless no other solutions have worked for you.

I confirm worked for me too. but not a "nice" solution! and i have now gone back to a defunctioning clean install

---

### Post by kawabago on 2010-05-04
I have an Audigy sound card and had to open a terminal window and type alsamixer then press enter.  A text mixer opens, use the right arrow key to scroll right until you get to Audigy Analog/Digital Output Jack.  Press M to toggle it On then press ESC and close the terminal.  Sound should be working.

---

### Post by anomajaya on 2010-05-04
> **simon_w said:**
> Well I finally got a chance to look at this, and I believe I've solved my issue.  It seems I have an audio chipset that uses a very new codec - Realtek ALC665.

```
cat /proc/asound/card*/codec#* | grep Codec
```

The solution was to compile a special version of the alsa driver (1.0.22) provided by Realtek which includes the necessary driver.  I obtained the driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false").

I only actually needed to compile and install the alsa-driver itself - the libraries and utils from the Lucid install are compatible.

```

tar xf LinuxPkg_5.14rc6.tar.bz2
cd realtek-linux-audiopack-5.14/
tar xf alsa-driver-1.0.22-5.14rc6.tar.bz2
cd alsa-driver-1.0.22
./configure --with-cards=hda-intel
make
sudo make install

```

after a restart, I have everything working perfectly (touch wood!) - speakers, headphone jacks (both of them), internal mic...

Hope it works for you too!

simon


Dear Simon,

I did what u have mentioned above. But it did not work.

I found that my sound card is : Codec: Realtek ID 270
Codec: Intel G45 DEVIBX
( Using " cat /proc/asound/card*/codec#* | grep Codec" )

And the driver available at the link u have given above is LinuxPkg-5.15rc1.tar.bz2 ,and NOT  LinuxPkg_5.14rc6.tar.bz2.( they have upgraded it).

But It gave an Error at Command " make". It was,
 
anoma@anoma-laptop:~/realtek-linux-audiopack-5.15/alsa-driver-1.0.23$ make
make dep
make[1]: Entering directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23'
make[2]: Entering directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include'
make -C sound prepare
make[3]: Entering directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound'
make prepare2
make[4]: Entering directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound'
ln -s ../../alsa-kernel/include/aci.h
ln -s ../../alsa-kernel/include/ad1816a.h
ln -s ../../alsa-kernel/include/ad1843.h
ln -s ../../alsa-kernel/include/ak4113.h
ln -s ../../alsa-kernel/include/ak4114.h
ln -s ../../alsa-kernel/include/ak4117.h
ln -s ../../alsa-kernel/include/ak4531_codec.h
ln -s ../../alsa-kernel/include/ak4xxx-adda.h
ln -s ../../alsa-kernel/include/asequencer.h
ln -s ../../alsa-kernel/include/asound.h
ln -s ../../alsa-kernel/include/asound_fm.h
ln -s ../../alsa-kernel/include/asoundef.h
ln -s ../../alsa-kernel/include/atmel-abdac.h
ln -s ../../alsa-kernel/include/atmel-ac97c.h
ln -s ../../alsa-kernel/include/control.h
cp ../../alsa-kernel/include/core.h .
patch -p0 -i core.patch core.h
make[4]: patch: Command not found
make[4]: *** [core.h] Error 127
make[4]: Leaving directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound'
make[3]: *** [prepare] Error 2
make[3]: Leaving directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23'
make: *** [include/sndversions.h] Error 2
anoma@anoma-laptop:~/realtek-linux-audiopack-5.15/alsa-driver-1.0.23$ 

AND once I RUN "sudo make install", It gave this,

anoma@anoma-laptop:~/realtek-linux-audiopack-5.15/alsa-driver-1.0.23$ sudo make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.32-21-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include'
make[1]: Nothing to be done for `modules_install'.
make[1]: Leaving directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/include'
make[1]: Entering directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore'
mkdir -p /lib/modules/2.6.32-21-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.32-21-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/anoma/realtek-linux-audiopack-5.15/alsa-driver-1.0.23/acore'
make: *** [install-modules] Error 1
anoma@anoma-laptop:~/realtek-linux-audiopack-5.15/alsa-driver-1.0.23$ 

OnCE I restarted nothing was happened!

What can I do?

Looking for an early reply.

Thanks

Anoma

---

### Post by simon_w on 2010-05-04
Anoma,

Your error is because you are missing some software which you need to compile the drivers.

You can use the excellent instructions [here]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/") as a guide, but use the Realtek download instead of the ones linked on this page.

To summarize:

Begin by making sure you have what you need.

```
sudo apt-get install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get install linux-headers-`uname -r` libncursesw5-dev
```

Then untar and compile each package in turn.  Using the .23 drivers, you'll need to install all four packages (drivers, libs, plugins and utils, in that order).  (I was able to get away with only installing the .22 drivers, since Lucid already has the .22 libs, plugins and utils - but they should all be the same version, to avoid any potential weirdness).

Also, when configuring the drivers package, I added the "--with-cards=hda-intel" flag.  This is not mentioned in the blog-post linked above, but is mentioned in the documentation that comes with the Realtek package.  I don't think it's necessary, but I'd add it if I were you - i.e.

```

cd alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

```

Then restart, not forgetting to keep your fingers crossed the whole time ;)

good luck!

---

### Post by claytontlewis on 2010-05-04
The sound demons (get it? demons daemons. ok I suck at linux jokes) are haunting me again. Sound has been working fine, but then I put the machine into hibernate last night and now today there is no sound.I've rebooted. I've made sure all the realtek drivers are still installed. Removed pulseaudio. Nothing is working.

What command, that there is no possible way a beginner could know, should I run now?

PS Yes, I did make sure it isn't muted.

---

### Post by claytontlewis on 2010-05-04
If you go to Synaptic Packet Manager and do a search on pulse then it is a very bad idea to right click on the installed things and choose mark for complete removal. System no longer will boot correctly. I think I have bigger problems than sound now.

---

### Post by simon_w on 2010-05-04
> **claytontlewis said:**
> If you go to Synaptic Packet Manager and do a search on pulse then it is a very bad idea to right click on the installed things and choose mark for complete removal. System no longer will boot correctly. I think I have bigger problems than sound now.

I think you probably do, I'm sorry to say.

(at risk of coming off as patronizing, here is a link to an [excellent article about reporting and dealing with bugs]("http://www.chiark.greenend.org.uk/~sgtatham/bugs.html").  It's well-written and bang on the money.  Your last post put me in mind of the part ["So then I tried..."]("http://www.chiark.greenend.org.uk/~sgtatham/bugs.html#antelope"))

fwiw, imo, removing PulseAudio should really be an option of desperate last-resort only.  PulseAudio is an important component in Ubuntu's sound architecture, and unistalling it will surely lead to lots of reconfiguring of other parts of the system, at minimum.  I've not needed to remove it at any stage (well, not since the first distro which included it as default - was it Hardy?  I still feel that it wasn't nearly ready at that time, but I think it's great now).

If you want to try to recover your system, try to use the recovery console or a live cd (usb, preferably) to reinstall PulseAudio in the first instance.  Failing that, perhaps post some more info on what's going wrong.

However, I suspect if it was me I'd be beginning a clean install at this point.  Do you have a separate home partition?  If so, it's pretty trivial - if not, you should use a live cd to backup your home folder first, and seriously think about creating one ([here's a guide I found]("http://ubuntuforums.org/showthread.php?t=1457542")).

---

### Post by claytontlewis on 2010-05-04
LOL

Yeah I have already done a reinstall. Working on getting the sound going again. Starting from square one.

---

### Post by anomajaya on 2010-05-04
Hi Simon,

Thanks a lot to U for giving me instructions. It worked well. But driver downloaded from the Realtex site did not work. I followed all the steps in the page u suggested.( [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)) 

Those .23 drivers working well.

Thank U once again.

Dr. Anoma

---

### Post by anomajaya on 2010-05-05
Hi I got it done with the help of Mr Simon_W. Please follow the steps in [http://monespaceperso.org/blog-en/20...id-lynx-10-04/](http://monespaceperso.org/blog-en/20...id-lynx-10-04/)

Thank you

Dr. Anoma

---

### Post by Vtechie on 2010-05-05
Install gnome- alsamixer by:

sudo apt-get install gnome-alsamixer.

open alsamixer in terminal and change the setting for speakers.

---

### Post by dino99 on 2010-05-05
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by deadite66 on 2010-05-05
just hit the same problem when i rebooted my xbmc machine, livecd works fine.

[B]UPDATE: i restored karmic from a fsarchiver backup and that's the same, i fitted a new pci gfx card yesterday and ubuntu seems unable to cope with the change.
seems i'll have to fresh reinstall :/[/B]

```
uname -a
Linux sakura 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

```

```

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 14 2010 for kernel 2.6.32-21-generic (SMP).

```

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Device 414c:4760
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e000 [size=256]
	I/O ports at eb00 [size=64]
	Memory at ec081000 (32-bit, non-prefetchable) [size=512]
	Memory at ec082000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

```

```
lee@sakura:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
lee@sakura:~$ head -n 1 /proc/asound/card0/
codec97#0/ intel8x0   pcm0c/     pcm1c/     pcm3c/     
id         oss_mixer  pcm0p/     pcm2c/     pcm4p/   
```

---

### Post by deadite66 on 2010-05-06
another update, did a fresh install.
audio works until i install the nvidia drivers, uninstall them and the audio works again.

---

### Post by Harab on 2010-05-07
I had a similar problem after doing a clean install of Ubuntu 10.04 after successfully using Ubuntu 9.10.  I traced the problem to the mute setting being on.  Go to System>Control Center>Sound (in Hardware group) and you have a Sound Preferences dialog box come up.  At the top right of the box make sure that the Mute box is not ticked.

---

### Post by deadite66 on 2010-05-08
i have sound again yay
problem was using a dvi-to-hdmi cable, the tv was expecting audio over hdmi so no sound.
i had to create a custom edid with the audio bit disabled.
[http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI](http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI)

---

### Post by claytontlewis on 2010-05-11
So I've been fighting with my sound card more. I've been having sporadic sound. Sometimes I reboot or let the machine hibernate and then I have sound, other times there is no sound at all. I tried to do an alsa force-reload today and got:

```
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
```

Any ideas?

---

### Post by simon_w on 2010-05-11
> **claytontlewis said:**
> So I've been fighting with my sound card more. I've been having sporadic sound. Sometimes I reboot or let the machine hibernate and then I have sound, other times there is no sound at all. I tried to do an alsa force-reload today and got:

```
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
```

Any ideas?

This is just telling you that the file ``/etc/modprobe.d/sound`` should be named ``/etc/modprobe.d/sound.conf`` (ALSA is still reading the file, but is warning that future versions will ignore file which do not finish with .conf)

I'm not having any difficulty with my sound at all, any more.  I had to recompile the drivers after the recent kernel upgrade, but other than that it's been plain-sailing all the way since I found the Realtek drivers.

---

### Post by Incystar on 2010-05-30
I have recently installed 10.04 netbook edition on my nec versa s5200 notebook. I don't get any sound. I have tried to get realtek drivers for my realtek hd 262 sound card, but they won't install. have also tried ```
sudo alsa force-reload
``` but with no result.

Any Ideas?

---

### Post by yts2421 on 2010-05-30
> **deadite66 said:**
> another update, did a fresh install.
audio works until i install the nvidia drivers, uninstall them and the audio works again.

just installed 10.04 installed nvidia drivers no sound uninstalled drivers have sound again, go figure also had a problem with powering down. it would bring me to a login window. had to go to terminal and use the shutdown command. once i uninstalled  the drivers it worked fine.

---

### Post by yts2421 on 2010-05-30
just installed 10.04 installed nvidia drivers  no sound uninstalled drivers have sound again, go figure also had a  problem with powering down. it would bring me to a login window. had to  go to terminal and use the shutdown command. once i uninstalled  the  drivers it worked fine.

---

### Post by Saghaulor on 2010-05-31
> **simon_w said:**
> Well I finally got a chance to look at this, and I believe I've solved my issue.  It seems I have an audio chipset that uses a very new codec - Realtek ALC665.

```
cat /proc/asound/card*/codec#* | grep Codec
```

The solution was to compile a special version of the alsa driver (1.0.22) provided by Realtek which includes the necessary driver.  I obtained the driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false").

I only actually needed to compile and install the alsa-driver itself - the libraries and utils from the Lucid install are compatible.

```

tar xf LinuxPkg_5.14rc6.tar.bz2
cd realtek-linux-audiopack-5.14/
tar xf alsa-driver-1.0.22-5.14rc6.tar.bz2
cd alsa-driver-1.0.22
./configure --with-cards=hda-intel
make
sudo make install

```

after a restart, I have everything working perfectly (touch wood!) - speakers, headphone jacks (both of them), internal mic...

Hope it works for you too!

simon

Did you have to specify the kernel version? I'm trying to follow your steps, and I'm hanging on the ./configure.

I get the following error:
> $ ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/stephenaghaulor/Desktop/realtek-linux-audiopack-5.15/alsa-driver-1.0.23
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


---

### Post by Saghaulor on 2010-05-31
I've been messing around with kernels from the ppa, trying to get my intel integrated graphics to work properly. Apparently I hadn't installed the kernel properly, because after install kernel 2.6.34 I was able to properly ./configure.

---

### Post by Saghaulor on 2010-05-31
Fantastic, I have working speakers and a working headphone jack.

However, they both work at the same time, the headphones don't cancel the speakers.

It would be nice if that worked, but I can always play with the level in alsamixer.

---

### Post by Saghaulor on 2010-05-31
Btw, I sent Realtek tech support an email thanking them. I figure we should let them know that we appreciate their support for the Linux community.

---

### Post by Firefox15 on 2010-06-09
Hey for those of you who have tried alsamixer but doesn't seem to work go back and make sure that you raised every volume in there. I mean everything, using the right arrow key move through alsamixer and raise the volume of everything you can all the way up and see what happens. You can leave the shared thing alone though. Hope this helps.

---

### Post by lidex on 2010-06-09
It was mentioned previously in this thread to run sudo alsamixer. I would advise against that as you may end up with permissions problems. For alsamixer, in a terminal simply enter:
```
alsamixer
```
Gnome-alsamixer is the gui version and has some advantages.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by greecesking on 2010-06-11
I fixed the sound problem in my vaio vpc-eb17fb installing alsa-drivers from this ppa.

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-2.6.32-22-generic

More info here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442)

---

### Post by avatardvr@gmail.com on 2010-06-22
Hey all.  Had this same problem; fresh install of 10.04 and no sound.  solved it by installing gnome-alsamixer then running and checking the box that says analog/digital audio jack.  then i had to turn the the center left/right channel volume up and then the master volume.  dunno if it will help any of you.  good luck.

---

### Post by Bravehart on 2010-06-27
> **greecesking said:**
> I fixed the sound problem in my vaio vpc-eb17fb installing alsa-drivers from this ppa.

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-2.6.32-22-generic

More info here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442)

Thanks "greecesking"
Perfect! ... This worked for my Sony Vaio VPC - EB11FX/WI laptop and this is the easiest & quickest fix I'hav found after 3 weeks of research on this issue. I have sound on my laptop.

---

### Post by Anilix on 2010-07-01
> **simon_w said:**
> Well I finally got a chance to look at this, and I believe I've solved my issue.  It seems I have an audio chipset that uses a very new codec - Realtek ALC665.

```
cat /proc/asound/card*/codec#* | grep Codec
```The solution was to compile a special version of the alsa driver (1.0.22) provided by Realtek which includes the necessary driver.  I obtained the driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false").

I only actually needed to compile and install the alsa-driver itself - the libraries and utils from the Lucid install are compatible.

```

tar xf LinuxPkg_5.14rc6.tar.bz2
cd realtek-linux-audiopack-5.14/
tar xf alsa-driver-1.0.22-5.14rc6.tar.bz2
cd alsa-driver-1.0.22
./configure --with-cards=hda-intel
make
sudo make install

```after a restart, I have everything working perfectly (touch wood!) - speakers, headphone jacks (both of them), internal mic...

Hope it works for you too!

simon



Worked for me on toshiba Sattelite A660-11M!!!! thanks a ton!

---

### Post by don_engtech on 2010-07-12
> **greecesking said:**
> I fixed the sound problem in my vaio vpc-eb17fb installing alsa-drivers from this ppa.

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-2.6.32-22-generic

More info here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442)
Thank you 'greecesking'!  Your method also worked for me. Fresh install of Mythbuntu 10.04LTS w/ no audio at all. Older Ensoniq PCI audio card on modern server mobo w/o onboard audio.

Don

---

### Post by commandnotfound on 2010-07-26
> **greecesking said:**
> I fixed the sound problem in my vaio vpc-eb17fb installing alsa-drivers from this ppa.

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-2.6.32-22-generic

More info here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442)

omg, no sound on my hp slimline with alsa for a while after i removed PA. finally found the solution, many thanks :D

---

### Post by vishaluc on 2010-07-27
I faced this problem when i changed the 'Connector' option in the  'Output' tab in sound preferences to 'Analog Headphones'. After i  changed the 'Connector' option back to 'Analog Output' everything seems  fine. Try it. :D

---

### Post by alagiriruban on 2010-08-01
Hi
I am new to Linux. I recently bought Compaq Presario 620. I have installed Ubuntu 10.04. The audio is not working. Please find the info requested by you... Please help me resolving this issue.

alagiri@alagiri-laptop:~$  uname -r
2.6.32-24-generic
alagiri@alagiri-laptop:~$ uname -a
Linux alagiri-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
alagiri@alagiri-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
alagiri@alagiri-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
alagiri@alagiri-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT ID 7666

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG

---

### Post by lidex on 2010-08-01
> **alagiriruban said:**
> Hi
I am new to Linux. I recently bought Compaq Presario 620. I have installed Ubuntu 10.04. The audio is not working. Please find the info requested by you... Please help me resolving this issue.

alagiri@alagiri-laptop:~$  uname -r
2.6.32-24-generic
alagiri@alagiri-laptop:~$ uname -a
Linux alagiri-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
alagiri@alagiri-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
alagiri@alagiri-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
alagiri@alagiri-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT ID 7666

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG

You should upgrade your alsa install. Use the alsa-upgrade link in my sig. When that's finished, post these outputs:
```

aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by jango_0072003 on 2010-08-02
> **lidex said:**
> You should upgrade your alsa install. Use the alsa-upgrade link in my sig. When that's finished, post these outputs:
```

aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```

This is bug in ubuntu 10.04. There is a work around for this. It worked for me the work around is very simple. If you find that your sound card are rest of the audio hardware are configured properly and the sound still doesn't work do this:

[LEFT]1) Go to **System > Preferences > Startup Applications**
2) Press the **Add** Button
             Name:         **Pulseaudio daemon**
             Command:  **/usr/bin/pulseaudio**
             Comment:   **Start the sound daemon**
3) Now press the **Add** Button
4) Now Press the **Close** Button
5) Restart.

Your audio should be working now.


[/LEFT]

---

### Post by alagiriruban on 2010-08-02
i am getting the below error when try to run the command 
sudo ./AlsaUpgrade-1.0.23-2.sh -c

Hacking autoconf.h...
make dep
make[1]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23'
make[2]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
make -C sound prepare
make[3]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound'
make .includes.tmp
make[4]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound'
make[4]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound'
make prepare2
make[4]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound'
cp ../../alsa-kernel/include/ac97_codec.h .
patch -p0 -i ac97_codec.patch ac97_codec.h
make[4]: patch: Command not found
make[4]: *** [ac97_codec.h] Error 127
make[4]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound'
make[3]: *** [prepare] Error 2
make[3]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23'
make: *** [include/sndversions.h] Error 2

***************************************************************************
*  alsa-driver-1.0.23 make failed
***************************************************************************

---

### Post by lidex on 2010-08-02
Make sure build-essential is installed and start over. Check the posts on that thread as well. Others have had similar issues.
```
sudo aptitude install build-essential
```

---

### Post by alagiriruban on 2010-08-03
Hey i am able to hear sound in my laptop. But the volume is very low. I have set the sound preference Output Volume to the maximum. Please help me to resolve this too... I have attached snapshots of my Sound Preferences. 

Please find below the output of
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#*

alagiri@alagiri-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
alagiri@alagiri-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                       1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                           1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                        1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                     1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                      1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                                  1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                      1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                      4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                 0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                              0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-alsa-driver-modules-2.6.32-22-generic     2.6.32-22.201007050500                          Ubuntu-supplied Linux modules for version 2.
ii  linux-headers-alsa-driver-2.6.32-24-generic-pae 2.6.32-24.201007270500                          Header files related to linux-alsa-driver-mo
alagiri@alagiri-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD88B3

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG

---

### Post by alagiriruban on 2010-08-04
Even my Mic is not working. can u help me fix this ? check the output of alsamixer in the attached document

---

### Post by lidex on 2010-08-04
That's your digital soundcard. Try selecting the other one in 'Sound Preferences' on the hardware tab.

---

### Post by Vinas on 2010-08-05
> **simon_w said:**
> Well I finally got a chance to look at this, and I believe I've solved my issue.  It seems I have an audio chipset that uses a very new codec - Realtek ALC665.

```
cat /proc/asound/card*/codec#* | grep Codec
```

The solution was to compile a special version of the alsa driver (1.0.22) provided by Realtek which includes the necessary driver.  I obtained the driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false").

I only actually needed to compile and install the alsa-driver itself - the libraries and utils from the Lucid install are compatible.

```

tar xf LinuxPkg_5.14rc6.tar.bz2
cd realtek-linux-audiopack-5.14/
tar xf alsa-driver-1.0.22-5.14rc6.tar.bz2
cd alsa-driver-1.0.22
./configure --with-cards=hda-intel
make
sudo make install

```

after a restart, I have everything working perfectly (touch wood!) - speakers, headphone jacks (both of them), internal mic...

Hope it works for you too!

simon

I can confirm that the above worked for me. :p I used the newer driver (realtek-linux-audiopack-5.15).

System specs:

Dell Optiplex 980
Intel core i7 860
8GB RAM
Codec: Realtek ALC259
Linux workstation-pc 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

---

### Post by boroborolama on 2010-08-17
> **greecesking said:**
> I fixed the sound problem in my vaio vpc-eb17fb installing alsa-drivers from this ppa.

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-2.6.32-22-generic

More info here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/464442)
This worked on my Sony VAIO VPCEB11FX.  After installing some updates the laptop went silent again.  Here's what finally brought the sound back (replacing the third command):

> sudo apt-get install linux-alsa-driver-modules-$(uname -r)

---

### Post by g2d on 2010-09-06
Hi users,

 These step it's ok for HP G62

Code:
 	tar xf LinuxPkg_5.14rc6.tar.bz2
cd realtek-linux-audiopack-5.14/
tar xf alsa-driver-1.0.22-5.14rc6.tar.bz2
cd alsa-driver-1.0.22
./configure --with-cards=hda-intel
make
sudo make install

---

### Post by Me4oKyX on 2010-09-25
> **simon_w said:**
> Well I finally got a chance to look at this, and I believe I've solved my issue.  It seems I have an audio chipset that uses a very new codec - Realtek ALC665.

```
cat /proc/asound/card*/codec#* | grep Codec
```The solution was to compile a special version of the alsa driver (1.0.22) provided by Realtek which includes the necessary driver.  I obtained the driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false").

I only actually needed to compile and install the alsa-driver itself - the libraries and utils from the Lucid install are compatible.

```

tar xf LinuxPkg_5.14rc6.tar.bz2
cd realtek-linux-audiopack-5.14/
tar xf alsa-driver-1.0.22-5.14rc6.tar.bz2
cd alsa-driver-1.0.22
./configure --with-cards=hda-intel
make
sudo make install

```after a restart, I have everything working perfectly (touch wood!) - speakers, headphone jacks (both of them), internal mic...

Hope it works for you too!

simon


THANK YOU!!! This worked out for me! There's a new version of the drivers but with lil change in the names, eveyrthing else worked PERFECT :)  Now my Ubuntu is better than Win7 in all the ways possible for my needs :P Thank YOU! Will stay tuned to the forum so I could help some day to newbies like me :KS

---

### Post by simon_w on 2010-09-28
@Me4oKyX - welcome to Ubuntu and GNU/Linux :)

---

### Post by OnZy on 2010-10-04
Hello guys,

So I installed alsa-driver-1.0.23

with the following config: sudo ./configure --with-cards=hda-intel

and after reboot I get the following:

```

$ uname -a
2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux
$ aplay -l
aplay: device_list:223: no soundcards found...
$ cat /proc/asound/card*/codec#* | grep Codec
Codec: Realtek ALC887
Codec: Nvidia ID b
Codec: Nvidia ID b
Codec: Nvidia ID b
Codec: Nvidia ID b

```

Before reboot and running aplay -l i was getting two entries, one for analog and the other for digital 

I am running trying to get the HDMI or Digital to run on the following board: At5iont-i
[http://www.asus.com/product.aspx?P_ID=iIZKMXSj0jZKiebE](http://www.asus.com/product.aspx?P_ID=iIZKMXSj0jZKiebE)

I have been following all of the forms and instructions but no luck :(

Please help!!
Thanks
OnZy

---

### Post by lidex on 2010-10-05
> **OnZy said:**
> Hello guys,

So I installed alsa-driver-1.0.23

with the following config: sudo ./configure --with-cards=hda-intel

and after reboot I get the following:

```

$ uname -a
2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux
$ aplay -l
aplay: device_list:223: no soundcards found...
$ cat /proc/asound/card*/codec#* | grep Codec
Codec: Realtek ALC887
Codec: Nvidia ID b
Codec: Nvidia ID b
Codec: Nvidia ID b
Codec: Nvidia ID b

```

Before reboot and running aplay -l i was getting two entries, one for analog and the other for digital 

I am running trying to get the HDMI or Digital to run on the following board: At5iont-i
[http://www.asus.com/product.aspx?P_ID=iIZKMXSj0jZKiebE](http://www.asus.com/product.aspx?P_ID=iIZKMXSj0jZKiebE)

I have been following all of the forms and instructions but no luck :(

Please help!!
Thanks
OnZy

Yeah, it didn't take. Probably the easiest way to upgrade alsa is using the script linked to in my sig. Give that a go.
Remember to first remove alsa backports, if installed, as it will interfere.

---

### Post by OnZy on 2010-10-06
> **lidex said:**
> Yeah, it didn't take. Probably the easiest way to upgrade alsa is using the script linked to in my sig. Give that a go.
Remember to first remove alsa backports, if installed, as it will interfere.

Very cool it worked great =) Now the Intal digital and analog work great!  Do you have any ideas as to how i can get sound to work over the HDMI???

I also had to make the following to get the script to work with out errors:
```

sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so

```

---

### Post by lidex on 2010-10-06
> **OnZy said:**
> Very cool it worked great =) Now the Intal digital and analog work great!  Do you have any ideas as to how i can get sound to work over the HDMI???

I also had to make the following to get the script to work with out errors:
```

sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so

```

This may be different hardware, but good generic information on hdmi. The OP did awesome job documenting his fix.
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

More:
[http://ubuntuforums.org/showthread.php?t=1466111](http://ubuntuforums.org/showthread.php?t=1466111)
[http://ubuntuforums.org/showthread.php?t=1532355](http://ubuntuforums.org/showthread.php?t=1532355)
[http://ubuntuforums.org/showthread.php?t=1542401](http://ubuntuforums.org/showthread.php?t=1542401)
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by Izodn on 2010-10-08
@[simon_w]("http://ubuntuforums.org/member.php?u=393749") I just wanted to thank you! Your method got me up and running my beats again!

---

### Post by AppleBonker on 2010-10-17
Well, I guess it's time to post my problem in this thread.  If anyone can help it would be greatly appreciated.


First, a little bit of info.  Output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Output of lspci -v:

Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 812a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at dc00 [size=256]
	I/O ports at e000 [size=256]
	Memory at dc003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0


And for good measure, cat /proc/asound/cards:

 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10


So, I've downloaded the realtek driver from their website (posted by simon).  It was compiled and installed.  I then upgraded to the latest version of alsa.  At this point, I am able to get audio out of the digital (optical) output.  But I do not have anything from the analog outputs.  I've messed with every possible setting in alsamixer, but nothing seems to work.  I'm fairly certain I've got the proper driver, but yet no audio from the analog outs.  For reference, this is onboard sound from an Asus A8N-SLI Deluxe mobo.  Anything I should try that I might have missed?

---

### Post by AppleBonker on 2010-10-17
Actually, I figured out there was a hardware issue with the front audio ports on my case.  When they are connected correctly, I do get audio out of the rear analog jacks.  Unfortunately, it is ridiculously distorted.  I can hear enough to tell that it is playing the correct audio, but it takes a lot of straining.  What could cause the output to be so distorted?

---

### Post by lidex on 2010-10-17
> **AppleBonker said:**
> Actually, I figured out there was a hardware issue with the front audio ports on my case.  When they are connected correctly, I do get audio out of the rear analog jacks.  Unfortunately, it is ridiculously distorted.  I can hear enough to tell that it is playing the correct audio, but it takes a lot of straining.  What could cause the output to be so distorted?

Check that your levels are not too high, especially pcm.

---

### Post by AppleBonker on 2010-10-17
> **lidex said:**
> Check that your levels are not too high, especially pcm.

I've messed with the levels of everything and tried changing all settings in alsamixer.  I still get audio out of the analog outs even when PCM is set to 0, but not when it is muted.

---

### Post by lidex on 2010-10-17
> **AppleBonker said:**
> I've messed with the levels of everything and tried changing all settings in alsamixer.  I still get audio out of the analog outs even when PCM is set to 0, but not when it is muted.

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by AppleBonker on 2010-10-17
lidex, I've been trying to mess with it both in 10.04 (my old mythbuntu install) as well as 10,10 thinking I can try a couple different methods without completely borking an entire install.  They both have the same functionality right now - digital out works fine and analog is painfully distorted.  The Lucid install is running the realtek driver downloaded from their site.  The Maverick install is running the stock alsa configuration.  This is from the Maverick install:

[http://www.alsa-project.org/db/?f=36da71c3e1a5e64567c74e7a6cb2a859e25d386e](http://www.alsa-project.org/db/?f=36da71c3e1a5e64567c74e7a6cb2a859e25d386e)

I'm slightly capable of tinkering around at the command line, but the information above is a bit above my head when it comes to diagnosing this issue.  If you have any insight I would appreciate it.  Thanks in advance.

---

### Post by lidex on 2010-10-17
> **AppleBonker said:**
> lidex, I've been trying to mess with it both in 10.04 (my old mythbuntu install) as well as 10,10 thinking I can try a couple different methods without completely borking an entire install.  They both have the same functionality right now - digital out works fine and analog is painfully distorted.  The Lucid install is running the realtek driver downloaded from their site.  The Maverick install is running the stock alsa configuration.  This is from the Maverick install:

[http://www.alsa-project.org/db/?f=36da71c3e1a5e64567c74e7a6cb2a859e25d386e](http://www.alsa-project.org/db/?f=36da71c3e1a5e64567c74e7a6cb2a859e25d386e)

I'm slightly capable of tinkering around at the command line, but the information above is a bit above my head when it comes to diagnosing this issue.  If you have any insight I would appreciate it.  Thanks in advance.

Make sure this is installed:
```
sudo apt-get install alsa-oss
```
Reboot.

---

### Post by AppleBonker on 2010-10-17
Oddly enough it wasn't installed.  I installed it, but no change.  The volume is also much lower out of the analog outputs than the digital.  I have to turn the volume up a ton on my AVR to hear anything.  Not sure if that has something to do with the distortion as well.

Also, the 10.04 install definitely has alsa-oss installed on it as well.  I upgraded to alsa version 1.0.23 using the update script floating around here somewhere (albeit with some modifications to adjust for using the realtek driver and not the driver from alsa-project.org).

---

### Post by lidex on 2010-10-17
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by AppleBonker on 2010-10-17
No change.  For what it's worth, the audio sounds just as bad out of the front headphone port on the case.  I almost wish I had the space on a drive to install windows and see if the problem persists.  The analog audio was fine in windows when I used to run it, but this PC hasn't seen a windows install in close to two years.

And, by the way, thanks for taking a look.  I've honestly tested all possible combinations of volume and settings in alsamixer, so I don't think it's anything there.  I've also tried two different drivers, so I ran out of ideas on my end.

---

### Post by lidex on 2010-10-17
> **AppleBonker said:**
> No change.  For what it's worth, the audio sounds just as bad out of the front headphone port on the case.  I almost wish I had the space on a drive to install windows and see if the problem persists.  The analog audio was fine in windows when I used to run it, but this PC hasn't seen a windows install in close to two years.

And, by the way, thanks for taking a look.  I've honestly tested all possible combinations of volume and settings in alsamixer, so I don't think it's anything there.  I've also tried two different drivers, so I ran out of ideas on my end.

Most of the info I can dig up is pretty old and the biggest problem with this chipset is getting digital audio whereas most say analog works out-of-the-box. You are exactly the opposite. Have you made config changes - ie. asound.conf? And can you post these outputs please: ```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by AppleBonker on 2010-10-18
The motherboard is old, especially for me.  I generally upgrade computers every couple of years.  This was my old desktop that I decided to convert to a HTPC.

I haven't made any adjustments.  In fact, the 10.10 install is completely fresh.  I just reinstalled Ubuntu on it earlier today.  A big part of me is wondering if the chipset is somehow damaged, or if the front panel audio connectors are causing the issue.  There are two pins each for the left and right channels for the front panel audio, and if they aren't jumpered together there is no output from the analog ports (seems strange to me too, and there isn't anything in the owner's manual that explains this).  I'm planning on just trying to jumper them together and see what happens there.

It's not a huge issue, as I am hoping to upgrade to a smaller PC in the semi-near future (I want to go mATX or ITX so it will fit in my tv stand).  I was just hoping to be able to use it in the meantime.

---

### Post by AppleBonker on 2010-10-18
bios:

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: ASUS A8N-SLI Premium ACPI BIOS Revision 1303
    Release Date: 08/10/2006
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported

Handle 0x0042, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1
```

baseboard:

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: ASUSTeK Computer INC.
    Product Name: A8N-SLI Premium
    Version: 1.02    
    Serial Number: 123456789000
```

---

### Post by lidex on 2010-10-18
In any case, I'd think a bios update is a good thing. 
Right now I'd like you to try this. First remove the entry I asked you to make to alsa-base.conf. Now insert these lines there:
```
options snd cards_limit=1
alias snd-card-0 snd-intel8x0
options snd slots=snd-intel8x0
alias sound-slot-0 snd-intel8x0
```
**Reboot**

---

### Post by AppleBonker on 2010-10-18
While the date makes it look old, that is the most current version of the bios available on the Asus website.  That particular alsa-base.conf edit didn't change anything either.

---

### Post by lidex on 2010-10-19
> **AppleBonker said:**
> While the date makes it look old, that is the most current version of the bios available on the Asus website.  That particular alsa-base.conf edit didn't change anything either.

OK, try this. First open alsa-base.conf for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Now remove the entries you added previously and insert this line:```
options snd-intel8x0 ac97_quirk=3
```
Reboot.

---

### Post by AppleBonker on 2010-10-19
No dice there either...

---

### Post by physicsloph on 2010-11-16
It really works :))

---

### Post by physicsloph on 2010-11-16
> **g2d said:**
> Hi users,

 These step it's ok for HP G62

Code:
     tar xf LinuxPkg_5.14rc6.tar.bz2
cd realtek-linux-audiopack-5.14/
tar xf alsa-driver-1.0.22-5.14rc6.tar.bz2
cd alsa-driver-1.0.22
./configure --with-cards=hda-intel
make
sudo make install


It really works :) By the way is there any way to delete wrong all not well replies??

---

