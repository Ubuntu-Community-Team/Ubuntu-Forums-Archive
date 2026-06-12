---
title: "nVidia 8200 HDMI Sound support"
date: 2008-10-24
forum: Hardware
---

### Post by phowells on 2008-10-24
Hello Forum,

I do not know if this is the appropriate forum for this inquiry so please forgive my ignorance if it is not.

I have an ASUS motherboard with the nVidia 8200 chipset and I am running Hardy.  I have noticed that Ubuntu is recognising the onboard sound but does not recognize a seperate sound device for the HDMI output.  I assume that this is the root reason why there is no HDMI sound support for the 8200 in Ubuntu.

My questions:

Is there any effort underway to add the support for the HDMI sound device on the 8200?

Is the device detected but not recognized as a sound device?

Any information or comments regarding this lack of hardware support would be appreciated.

Thanks
Paul

---

### Post by shawnrgr on 2008-10-25
whats the output of...

```
aplay --list-devices
```
Also, this may be related: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/148097](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/148097)

---

### Post by Tidder on 2008-11-14
I have read of success under Gentoo using nvidia 177.80 drivers and alsa-driver 1.0.18a.  So far under ubuntu I have been unsuccessful in getting it to work.

---

### Post by cszikszoy on 2008-11-14
Intrepid has the latest kernel, have you tried to load up the latest Live CD and see if your hardware is detected then?  It's worth a shot.

---

### Post by Tidder on 2008-11-14
Closest I have got to getting it working is compiling the newest ALSA from source.  The HDMI audio interface shows up after upgrading ALSA, but still no audio can be routed thru it.  That's with intrepid.

I've also tried the ALSA driver from realtek, which had no difference what so ever.

---

### Post by zim2dive on 2008-12-11
Just got a new Acer AX1200 with nvidia 8200 graphics.  I am running the latest nvidia driver I see in the custom driver menu (177).

I've got graphics via HDMI, but no sound.. and the AX1200 doesn't have any other digital sound output other than the HDMI port.  Audio does work under windows.

I am completely new to Ubuntu, tho a daily user of *nix for 15+ years, still mostly as an end-user and perl hacker, not as an admin... so forgive me if I have to ask for help with small words :)

> ubuntu:~> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

from what I've read it sound like no digital output is being seen?  I've seen other output that lists a Device 1 that is Digital?

alsamixer shows me only 1 column of volume.

I've tried to follow the steps at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) (the comprehenisive sound problem thread), but short of installing things from scratch, no dice.

I did see reference to a newer nvidia driver (180), but that does not show up in the custom driver menu (how do they get added?).. will look further into how to install that tomorrow (I've done an nvidia install by hand on a linux box at a previous job 2 years ago, but the memory is very fuzzy)

---

### Post by zim2dive on 2008-12-14
Installing ALSA 1.0.18a I now get

> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but still no sound.

---

### Post by dvhart on 2008-12-14
I'm currently working with the same system and having the same trouble.  I've rebuilt and installed the 1.0.18a drivers and the 1.0.18 libs, utils, tools, and plugins from debian experimental (I still had to overwrite the libasound plugins for 32 bit stuff which ubuntu puts in the ia32libs (or similar)... I digress.  After the upgrade I see the same devices as above.  I looked at /proc/asound/card0/codec#0 and saw that there is a section in there which identifies the digital out of Node 0x11 (17) to be an internal HDMI connection:

Node 0x11 [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18566140: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Orange
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x10


Mapping this to the output of /proc/asound/devices:

  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 26: [ 0- 2]: digital audio capture
 33:        : timer

Says to me that Node 17, device 0,1, is the HDMI output.  Is that correct?

I've ensured that in my mixer IEC958 is not muted (set to 00) and IEC958 Default PCM is not muted (set to 00).  Using mplayer with "-ao alsa:device=plughw=0.1" or "alsa:device=hw=0.1" doesn't output any sound to my receiver, and using the similar options in MythTV results in the same problem.

I've confirmed that this does work with Windows Vista.  I'm using version 177 of the nvidia driver.  I haven't see any kind of configuration specific for the nvidia driver - does anyone know if there is something we need to do there? (modinfo nvidia doesn't list any obvious parameters).

---

### Post by zim2dive on 2008-12-15
I downloaded and installed the 180.16 beta driver from nvidia, but no improvement.

I then went into BIOS, under Integrated Peripipherals I see

Onboard HD Audio
Onboard HDMI Audio

with both being either Auto or Disabled.. Both were Auto.

Just b/c nothing else is as expected, what I found was that I had to have 'HD Audio' enabled in order to get HDMI audio under Windows.. the "HDMI Audio" setting did not seem to matter.

Under Ubuntu, aplay -l comes up empty unless HD Audio is enabled, and does not care if HDMI audio is enabled... quite a curious naming situation...

---

### Post by zim2dive on 2008-12-16
I finally got this working.

I needed alsa 1.0.18a [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2) , compiled with ./configure --with-cards=all and --with-card-options=all

after that I see

> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
Subdevices: 0/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0 

and while I already it installed (so I can't say for sure), I also am using the latest nvidia beta driver (180.16), installed by following directions at [http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/](http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/)

I found this page very useful for debug: [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

I did NOT seem to need to make any edits to /etc/modprobe.d/alsa-base

Get these installed and unmute things in alsamixer.
Go to the System->Pref->Sound and pick the nVidia HDMI mixer

for mplayer I was able to 

mplayer -ao alsa:device=hw=0.3 movie.avi

---

### Post by zim2dive on 2008-12-18
My system got unstable.. which I blamed on the nvidia beta driver.. so since I was only 1 week into my ubuntu install. I trashed it and am trying to start over.. but having less success...

I was able to get VLC and mplayer to play DD5.1 files, but my rcvr is only reporting DPL... I'm loathe to upgrade the nvidia driver again to see if that is the magic sauce for that...

Also I have install flash for Firefox, and can _see_ things (like The Daily Show), but I get NO sound for that... how do I get that path set up? in mplayer and VLC I can direct the sound output, but here I think I need to direct the overall system output...

I think I heard the ubuntu satartup sound for the 1st time (is there a startup sound?) (which I didn't even hear on my previous install that had DD 5.1 abilities)

thanks,
Mike

---

### Post by Tidder on 2008-12-28
I will have to try and compile with the options you have shown for the new alsa driver.  It wouldn't surprise me to see that the beta driver has something to do with HDMI sound output... hopefully my success is a little better than what you reported. :)

---

### Post by Cuppa-Chino on 2008-12-28
hi I am having similar problems.

current setup is asus geforce 8300 (same difference) board the spdif port to the receiver works right off the bat, although I have not tried to play 5.1 over it yet.

aplay -l does not bring up the device 0:3 that seems to be the hdmi audio output.

I have tried both the alsa script (as per [here]("http://ubuntuforums.org/showthread.php?t=962695")) and from the ppa ( [https://launchpad.net/~pgquiles/+archive/]("https://launchpad.net/~pgquiles/+archive/")) to install alsa 1.0.18a but
the install kills my mythbuntu/xcfe all I get is display corrupted mumble jumble, restarting gdm does not do anything to aid the situation, even when I replace xorg.conf with a failsafe with vesa no dice.

I have yet to do it the old fashioned way.

similarly I have failed on the grand scale to install any nvidia 180.xx driver with the run packages from their site either, all I get is "safe" mode and 640x480 and the usual driver not loaded mumbo.

any pointers?

---

### Post by zim2dive on 2008-12-28
> **Cuppa-Chino said:**
> hi I am having similar problems.

current setup is asus geforce 8300 (same difference) board the spdif port to the receiver works right off the bat, although I have not tried to play 5.1 over it yet.

aplay -l does not bring up the device 0:3 that seems to be the hdmi audio output.

I have tried both the alsa script (as per [here]("http://ubuntuforums.org/showthread.php?t=962695")) and from the ppa ( [https://launchpad.net/~pgquiles/+archive/]("https://launchpad.net/~pgquiles/+archive/")) to install alsa 1.0.18a but
the install kills my mythbuntu/xcfe all I get is display corrupted mumble jumble, restarting gdm does not do anything to aid the situation, even when I replace xorg.conf with a failsafe with vesa no dice.

I have yet to do it the old fashioned way.

similarly I have failed on the grand scale to install any nvidia 180.xx driver with the run packages from their site either, all I get is "safe" mode and 640x480 and the usual driver not loaded mumbo.

any pointers?

This is my install script ```
sudo aptitude -y install build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r`

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2
sudo wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.18.tar.bz2
sudo wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18.tar.bz2
sudo wget ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.18.tar.bz2

sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
sudo tar xjf alsa-plugins*.tar.bz2

cd alsa-driver*
sudo ./configure --with-cards=all --with-card-options=all
sudo make
sudo make install
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
cd ../alsa-plugins*
sudo ./configure
sudo make
sudo make install

sudo reboot
cat /proc/asound/devices
aplay -l

alsamixer
# sudo alsactl store 0

cat > /etc/asound.conf << DELIM
defaults.pcm.device 3
DELIM
```

Note that the steps after the reboot are mostly done by hand... aplay -l should show you the HDMI device..

I also used this link heavily for debug assistance  [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

I can get 180.11 and .16 to load, but I get VERY unstable results, so I am sticking with 177.  177.80 (the Intrepid default) does NOT give me 5.1, I seem to need 177.82 for that.

---

### Post by Cuppa-Chino on 2008-12-29
thanks, I think I am half way now...

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

alsamixer every output unmuted including 3* IEC

but still when I try to play sound via hdmi I get nowhere..

```
$ aplay -D hw:0,3 -f cd SURROUNDTEST_DD_640.wav 
Playing WAVE 'SURROUNDTEST_DD_640.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Warning: rate is not accurate (requested = 44100Hz, got = 48000Hz)
         please, try the plug plugin 
Aborted by signal Terminated...


$ aplay -D hw:0,3 -r=48000 Norrlanda.wav 
aplay: main:496: bad speed value 0

```

I cannot seem to find a setup in which it will play them via hdmi to the tv (samsung)
both those pay right of the bat via my spdif optical to the digital receiver, in stereo and 5.1.

any help would be appreciated. (I am still using 177.80, will try and upgrade to 180.xx now)

---

### Post by zim2dive on 2008-12-29
> **Cuppa-Chino said:**
> thanks, I think I am half way now...


Did you go to the sound pref panel and

a) switch everything to nVidia HDMI
b) do the "TEST" buttons there

?

Also you have to restart alsa or reboot after upgrading.

Personally I used the mplayer example to get sound (from the alsa digital page).

EDIT: I realize the above is mostly grasping at straws...

---

### Post by speed32219 on 2008-12-31
After much research and this thread I finally have sound working through HDMI.  At least I can hear the test tones from the sound panel under preferences.  After installing the new 1.0.18a alsa drivers, I had to set everything up to Nvidia HDMI as zim2dive pointed out.  I also found that IEC958 1 had to be selected in the Alsa mixer panel. But in the preferences (Right click on the speakers top panel) IEC958 2 needed to be selected.  In fact, if you select that in the sound panel it would auto select the IEC958 1 in the alsamixer screen.

Now I have to install the new Nvidia 1.80 display drivers, since I am having problems with Video tearing and high CPU utilization. (Gigabyte MB with the new 45nm AMD 2.5Ghz dual core CPU) I have the Nvidia drivers, now I need to find out how to install them.

---

### Post by zim2dive on 2008-12-31
> **speed32219 said:**
> After much research and this thread I finally have sound working through HDMI.  At least I can hear the test tones from the sound panel under preferences.  After installing the new 1.0.18a alsa drivers, I had to set everything up to Nvidia HDMI as zim2dive pointed out.  I also found that IEC958 1 had to be selected in the Alsa mixer panel. But in the preferences (Right click on the speakers top panel) IEC958 2 needed to be selected.  In fact, if you select that in the sound panel it would auto select the IEC958 1 in the alsamixer screen.

Now I have to install the new Nvidia 1.80 display drivers, since I am having problems with Video tearing and high CPU utilization. (Gigabyte MB with the new 45nm AMD 2.5Ghz dual core CPU) I have the Nvidia drivers, now I need to find out how to install them.

Actually with the 8200, you may want to read [http://ubuntuforums.org/showthread.php?t=1015407](http://ubuntuforums.org/showthread.php?t=1015407) .. I actually rolled BACK to 173 in order to get acceptable Flash performance.. I had lots of instability with 180.x and they did not help Flash at all for me.  Guess it all depends on your usage model... as Murphy's Law would have it, 173 killed my HDMI audio..

---

### Post by speed32219 on 2008-12-31
Oh no, that is really bad news!  It is Nvidia's chip set, why release it if it doesn't work.  Oh, I forgot, doze probably does and that's there first target.  Dang.

How is the Video playback using 1.73?

I thought you needed 1.77 for the HDMI output, although I have a Geforce 6200 working great using the 1.73 and DVI output with a Turtle Bch spidf optical card for 5.1 sound. 

 I wanted the new IGA with sound (HDMI) combo coupled with a dual Core CPU for 1080P, but I guess we are a little to early.  I hope a solution comes along soon.  By the way, this is the first AMD based Mobo and  dual core AMD CPU that I  ever used.  I wonder if the Intel CPU based Bds. are having the same issues using the 1.80 drivers.

---

### Post by zim2dive on 2008-12-31
> **speed32219 said:**
> Oh no, that is really bad news!  It is Nvidia's chip set, why release it if it doesn't work.  Oh, I forgot, doze probably does and that's there first target.  Dang.

How is the Video playback using 1.73?

I thought you needed 1.77 for the HDMI output, although I have a Geforce 6200 working great using the 1.73 and DVI output with a Turtle Bch spidf optical card for 5.1 sound. 

 I wanted the new IGA with sound (HDMI) combo coupled with a dual Core CPU for 1080P, but I guess we are a little to early.  I hope a solution comes along soon.  By the way, this is the first AMD based Mobo and  dual core AMD CPU that I  ever used.  I wonder if the Intel CPU based Bds. are having the same issues..

I lose audio with 173 over HDMI.. I am using the 6 analog audio jacks in the short term b/c I'd rather have good video than hdmi audio.  The video with 173 behaves as one would expect.. ie. it works.. I can even watch hulu HD... with 177 and 180, video slows to a very few FPS.

---

### Post by speed32219 on 2008-12-31
Well that is good news as far as the video.  But I have to have good audio 5.1 to go with it.  I am going to roll back to 1.73 and install that turtle beach sound card with optical out to AVR for now until they get averything worked out. Thank you  for the heads up, I know it takes a lot of bleeding to get it just right.  I not only need smooth 1080i/p playback but I also want low CPU utilization and that is not the case right now. I'll move to 1.73 and monitor this thread

---

### Post by DinoPower on 2008-12-31
Hey Guys, 

Great Thread on topic.  I'm in the same boat with a nvidia MB with HDMI and audio trying to get HDMI audio to work with mythbuntu 8.10.  Here is the rub that kills me.  My sony TV (wega 50) has an HDMI input and RCA audio paired to the input port.  With the older version of Mythbuntu, my HDMI port was happy to take video with HDMI, and audio through the RCA ports, but with 8.10, my Sony "senses" HDMI audio and mutes the RCA ports (per sony tech support), yet I have no audio ether way (HDMI or RCA). I do know that audio is coming out of my RCA/analog ports.   

I'm running the nvidia 177.80 driver and .10a alsa driver (per the install here).  

my aplay -l shows the digital device, but not HDMI.  aplay -L USED to show an HDMI input before the alsa driver upgrade, but now does not.  

Gnome sound control does NOT show an HDMI device.  

Please keep this thread updated with anything new to try and I'll gladly post results.  At this point, it's looking like I need to have a seperate audio channel (amp/speakers) rather than my TV.

---

### Post by zim2dive on 2009-01-01
> **DinoPower said:**
> Hey Guys, 

Great Thread on topic.  I'm in the same boat with a nvidia MB with HDMI and audio trying to get HDMI audio to work with mythbuntu 8.10.  Here is the rub that kills me.  My sony TV (wega 50) has an HDMI input and RCA audio paired to the input port.  With the older version of Mythbuntu, my HDMI port was happy to take video with HDMI, and audio through the RCA ports, but with 8.10, my Sony "senses" HDMI audio and mutes the RCA ports (per sony tech support), yet I have no audio ether way (HDMI or RCA). I do know that audio is coming out of my RCA/analog ports.   

I'm running the nvidia 177.80 driver and .10a alsa driver (per the install here).  

my aplay -l shows the digital device, but not HDMI.  aplay -L USED to show an HDMI input before the alsa driver upgrade, but now does not.  

Gnome sound control does NOT show an HDMI device.  

Please keep this thread updated with anything new to try and I'll gladly post results.  At this point, it's looking like I need to have a seperate audio channel (amp/speakers) rather than my TV.

If you roll back to 173 you _might_ not have any HDMI audio to get detected.. not sure but since its just a few clicks in Synaptic and a reboot, its a low effort to try.

And yeah, I was thinking of going the Turtle Beach USB route as well.

---

### Post by Cuppa-Chino on 2009-01-01
> **DinoPower said:**
> Hey Guys, 

Great Thread on topic.  I'm in the same boat with a nvidia MB with HDMI and audio trying to get HDMI audio to work with mythbuntu 8.10.  Here is the rub that kills me.  My sony TV (wega 50) has an HDMI input and RCA audio paired to the input port.  With the older version of Mythbuntu, my HDMI port was happy to take video with HDMI, and audio through the RCA ports, but with 8.10, my Sony "senses" HDMI audio and mutes the RCA ports (per sony tech support), yet I have no audio ether way (HDMI or RCA). I do know that audio is coming out of my RCA/analog ports.   

I'm running the nvidia 177.80 driver and .10a alsa driver (per the install here).  

my aplay -l shows the digital device, but not HDMI.  aplay -L USED to show an HDMI input before the alsa driver upgrade, but now does not.  

Gnome sound control does NOT show an HDMI device.  

Please keep this thread updated with anything new to try and I'll gladly post results.  At this point, it's looking like I need to have a seperate audio channel (amp/speakers) rather than my TV.

odd question maybe but have you tried to roll back alsa? 
I had a fresh install of mythbuntu 8.10 and ran into all kinds of nonsense, plus some general corrupted install files (bad install cd maybe) in the end:
*I installed regular 8.10 (gnome) and then ran the script here. aplay -l found my hdmi audio on hw=0,3. 
*I then install 180.18 (make sure that before installing 180.18 you uninstall (even better purge) the 177.80 per synaptic)

now in gnome I can play the test sounds etc and also get output audio output on hdmi via mplayer file.extension -ao alsa=hw=0.3 (note the dot for mplayer), I am still struggling to have simultaneous playback via my spdif and hdmi. 
The other bit that is generally more difficult apears to be xfce, in gnome the sound properties seem to work off the bat (well kind of :D ).
I cannot get mythtv to give me sound anywhere at the moment..... but that will be setting there somewhere

maybe try this
* (make backup, if needed)
* (install ubuntu desktop package and check if it helps)
* purge 177.80
* reinstall alsa 1.1.18a
* install nvidia beta drivee

just a set of sugestions

---

### Post by zim2dive on 2009-01-01
> **Cuppa-Chino said:**
> odd question maybe but have you tried to roll back alsa? 
I had a fresh install of mythbuntu 8.10 and ran into all kinds of nonsense, plus some general corrupted install files (bad install cd maybe) in the end:
*I installed regular 8.10 (gnome) and then ran the script here. aplay -l found my hdmi audio on hw=0,3. 
*I then install 180.18 (make sure that before installing 180.18 you uninstall (even better purge) the 177.80 per synaptic)

now in gnome I can play the test sounds etc and also get output audio output on hdmi via mplayer file.extension -ao alsa=hw=0.3 (note the dot for mplayer), I am still struggling to have simultaneous playback via my spdif and hdmi. 
The other bit that is generally more difficult apears to be xfce, in gnome the sound properties seem to work off the bat (well kind of :D ).
I cannot get mythtv to give me sound anywhere at the moment..... but that will be setting there somewhere

maybe try this
* (make backup, if needed)
* (install ubuntu desktop package and check if it helps)
* purge 177.80
* reinstall alsa 1.1.18a
* install nvidia beta drivee

just a set of sugestions

I started with 8.10 via Wubi.. 

- tried video before nvidia drivers at 1280x800(?).. it was better than 
- intalled nvidia 177.80 (Intrepid recommended).. video is bad
- then installed alsa 18a to get sound

so I haven't rolled alsa BACK, but I did try before I upgraded, so that is why I don't suspect alsa.

I've been thru ~10 fresh installs of Intrepid, trying different combinations, and sometimes just getting to a hosed state.  Rolling back to 173 was the only thing I found to make video work well, and between here and the nvidia forums, it seems to be coming to a consensus amongst us poor saps using the 8200.

---

### Post by speed32219 on 2009-01-07
Just an udate. I installed the newer beta 1.80 drivers from Nvidia and CPU usage dropped by 75%.  It was a major improvement in the GPU area, but had some instability problems. (ie freuquent pc video lockups) 

I had it running pretty good though (Sound across hdmi, hdmi video, low cpu useage, soundgraph LCD/Volume knob & remote) with most all of my HW working.  Then I started on the BD (1080P, I had some unencrypted videos and I was trying to get them to play to see how it would handle 1080p as far as GPU/CPU utilization.

I screwed up and loaded the kernel updates (What was I thinking, and I didn't even save a backup copy)  and all my work up to that point was forever wiped out.  Back to square one.  So I am moving to VirtualBox with xp and ibex on there to see if I can get everything working concurrently including wireless  Then as Ibex modules are released I can slowly migrate back over. I just want to get a working system with seamless 1080p playback for now.  Dang bleeding edge HW has been killed me. 

PS.  If they update Hardy to support the newer Nvidia 8000/9000 chipsets I am using that.  That new applet driven NM in 8.1 is for the birds.

---

### Post by Torquewrench on 2009-01-07
Hi,

Just found this thread and it's great to know there're others out there struggling with this too.

Running mythbuntu 8.10 (intrepid)
Asus M3N78-EM motherboard (nvidia 8300 chipset, realtek 1200 audio)
nVidia 177 video driver

With a fresh install here's what i got from aplay -l and -L
```
dorkbot@DB5K01:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dorkbot@DB5K01:~$ aplay -L
default:CARD=NVidia
    HDA NVidia, ALC888 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

With that I tried playing a .wav file with the following results:

aplay -D hw:0,0 test.wav plays sound through line out 3.5mm jack
aplay -D hw:0,1 test.wav plays in terminal but no sound is heard from any jacks

aplay -D plughw:0,0 test.wav plays sound through line out 3.5mm jack
aplay -D plughw:0,0 test.wav reports "underrun!!! (at least 11111...ms long) and no sound is heard

Just to make sure that my receiver was working I tried my HDMI DVD player through the same HDMI port and got sound.

I didn't find .asoundrc or asound.conf where they're supposed to be so I created asound.conf and added the following:

```
pcm.!default {
        type hw
        card 0
        device 1
}
```

That didn't help so next I installed ALSA 1.0.18a:

installed ALSA 1.0.18a driver with --with-cards=all --with-card-options=all
installed ALSA 1.0.18 library
installed ALSA 1.0.18 utils

After rebooting aplay gives the following device info:

```
dorkbot@DB5K01:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dorkbot@DB5K01:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
```

It now report ALC1200 which is the correct sound chip, but there's no longer an HDMI device in aplay -L.

And yes, I did unmute alsamixer:D

What am I missing? Is there some way to get that hdmi device back under aplay -L? Though when I tried to play directly to the device before upgrading to .18a fit wouldn't work. Thanks in advance for the help.

Phil/TW

---

### Post by zim2dive on 2009-01-07
> **Torquewrench said:**
> Hi,

Just found this thread and it's great to know there're others out there struggling with this too.

Running mythbuntu 8.10 (intrepid)
Asus M3N78-EM motherboard (nvidia 8300 chipset, realtek 1200 audio)
nVidia 177 video driver

With a fresh install here's what i got from aplay -l and -L
```
dorkbot@DB5K01:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dorkbot@DB5K01:~$ aplay -L
default:CARD=NVidia
    HDA NVidia, ALC888 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

With that I tried playing a .wav file with the following results:

aplay -D hw:0,0 test.wav plays sound through line out 3.5mm jack
aplay -D hw:0,1 test.wav plays in terminal but no sound is heard from any jacks

aplay -D plughw:0,0 test.wav plays sound through line out 3.5mm jack
aplay -D plughw:0,0 test.wav reports "underrun!!! (at least 11111...ms long) and no sound is heard

Just to make sure that my receiver was working I tried my HDMI DVD player through the same HDMI port and got sound.

I didn't find .asoundrc or asound.conf where they're supposed to be so I created asound.conf and added the following:

```
pcm.!default {
        type hw
        card 0
        device 1
}
```

That didn't help so next I installed ALSA 1.0.18a:

installed ALSA 1.0.18a driver with --with-cards=all --with-card-options=all
installed ALSA 1.0.18 library
installed ALSA 1.0.18 utils

After rebooting aplay gives the following device info:

```
dorkbot@DB5K01:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dorkbot@DB5K01:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
```

It now report ALC1200 which is the correct sound chip, but there's no longer an HDMI device in aplay -L.

And yes, I did unmute alsamixer:D

What am I missing? Is there some way to get that hdmi device back under aplay -L? Though when I tried to play directly to the device before upgrading to .18a fit wouldn't work. Thanks in advance for the help.

Phil/TW

I have the 8200.. oddly I never got HDMI listed under aplay -L but do have it with aplay -l

I don't think it should be causing your problem, but you should also install alsa-plugins, else you will not have HDMI sound via firefox, etc (once you have the other issues solved).

With 177.80 (default in 8.10) you should be able to get 2-channel sound over HDMI.

Have you tried ```
speaker-test -c 6 -twav
``` also what is the output of ```
cat /proc/asound/devices
```.  I found this link [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) very useful in my debug efforts.

---

### Post by jayman8547 on 2009-01-07
I struggled with this for about a month but have got it running with much success.  I have an Myth frontend rig w /ASUS M3N78-VM and to get the HDMI audio and video to work I followed these links in order:

[http://xbmc.org/forum/showthread.php?t=42183](http://xbmc.org/forum/showthread.php?t=42183)

I know it was for a xbmc setup but follow precisely then stop at "go into settings-system-audio and change the passthrough device to hdmi..." and switch to: 

[http://www.nvnews.net/vbulletin/showthread.php?t=116286&highlight=myth&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=116286&highlight=myth&page=3)

and copied the asource.conf file into /etc/

then I went to terminal and ran "alsamixer" and hit m to unmute the sound. (box on bottom of screen changed from 2 red XX's to a green box with 2 00's)

Also, disabled SP/DIF in BIOS.

Sound works great.  Not quite sure on navigation sound because I don't really use it but Myth (Stereo and 5.1), VLC and Firefox all have sound.

I know it is very frustrating and I was ready to give up but in the end I got the comp to do what _I_ wanted it to do!

---

### Post by xJoo Unitx on 2009-01-07
I've done some research on this topic... and I've failed. I updated the Alsa sound drivers and installed the Nvidia 180.17 graphics driver. Video is fine on my samsung tv, perfect 1080p resolution on my HDMI cable, but still no sound.  nvidia 8400m gs graphics card

aplay -l still shows now HDMI output

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0

aplay -L

front:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output


any ideas? I'm pretty new to linux in general, and upgrading the two drivers is really as far as I've gotten... and HDMI as audio output is in the aplay -L list... how do I get it to run?

---

### Post by xJoo Unitx on 2009-01-07
I've done some research on this topic... and I've failed. I updated the Alsa sound drivers and installed the Nvidia 180.17 graphics driver. Video is fine on my samsung tv, perfect 1080p resolution on my HDMI cable, but still no sound.  nvidia 8400m gs graphics card

aplay -l still shows now HDMI output

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0

aplay -L

front:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output


any ideas? I'm pretty new to linux in general, and upgrading the two drivers is really as far as I've gotten... and HDMI as audio output is in the aplay -L list... how do I get it to run?

---

### Post by Torquewrench on 2009-01-07
> **zim2dive said:**
> I have the 8200.. oddly I never got HDMI listed under aplay -L but do have it with aplay -l

I don't think it should be causing your problem, but you should also install alsa-plugins, else you will not have HDMI sound via firefox, etc (once you have the other issues solved).

With 177.80 (default in 8.10) you should be able to get 2-channel sound over HDMI.

Have you tried ```
speaker-test -c 6 -twav
``` also what is the output of ```
cat /proc/asound/devices
```.  I found this link [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) very useful in my debug efforts.

Ok, did my very best to follow what you asked above:

With NVidia 177.80 I ran speaker-test as above with the following results:

```
dorkbot@DB5K01:~$ speaker-test -c 6 -twav

speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 4096
Period size range from 1024 to 1024
Using max buffer size 4096
Periods = 4
was set period_size = 1024
was set buffer_size = 4096
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.564163

```

Where "default" is set in asound.conf as hw:0,1

cat /proc/asound/devices gives the following:

```
dorkbot@DB5K01:~$ cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 26: [ 0- 2]: digital audio capture
 33:        : timer
```

Been following the [http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut) also, just not sure where to go...

And following jayman's directions:
> I struggled with this for about a month but have got it running with much success. I have an Myth frontend rig w /ASUS M3N78-VM and to get the HDMI audio and video to work I followed these links in order:

[http://xbmc.org/forum/showthread.php?t=42183](http://xbmc.org/forum/showthread.php?t=42183)

I know it was for a xbmc setup but follow precisely then stop at "go into settings-system-audio and change the passthrough device to hdmi..." and switch to: 

[http://www.nvnews.net/vbulletin/show...ht=myth&page=3](http://www.nvnews.net/vbulletin/show...ht=myth&page=3)

and copied the asource.conf file into /etc/

then I went to terminal and ran "alsamixer" and hit m to unmute the sound. (box on bottom of screen changed from 2 red XX's to a green box with 2 00's)

Also, disabled SP/DIF in BIOS.

Sound works great. Not quite sure on navigation sound because I don't really use it but Myth (Stereo and 5.1), VLC and Firefox all have sound.

I know it is very frustrating and I was ready to give up but in the end I got the comp to do what I wanted it to do! 

Checked the BIOS and SPDIF output is directed to HDMI.

Followed the XBMC instructions and am now running NVidia 180.17 and the latest ALSA snapshot on top of 1.0.18a.

I had also found the NVNEWS thread and loaded the asound.conf.

alsamixer unmuted and reports: 
CARD: HDA NVidia
Chip: Realtek ALC888dorkbot@DB5K01:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -l gives:

dorkbot@DB5K01:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L gives:
dorkbot@DB5K01:~$ aplay -L
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

speaker-test -c 6 -twav produces no sound
aplay test.wav produces no sound over HDMI
aplay -D hw:0,0 test.wav produces sound out of the analog line out port

It bothers me that I'm not seeing the word HDMI anywhere in aplay -l or aplay -L. Also, it seems unusual that alsamixer is reporting ALC888 and aplay is reporting ALC1200. Any other configuration files I should check or other ideas?

Thanks so much,

Phil/TW

---

### Post by Torquewrench on 2009-01-07
Ok,

Progress!

Based on [HTML]http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg23969.html[/HTML] I decided to go into the BIOS and check whether changing from External CODEC to Internal + External would help under the Southbridge Setup area. It did.

I now get the following output from aplay -l:

```
dorkbot@DB5K01:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and aplay -L remains unchanged:

```
dorkbot@DB5K01:~$ aplay -L
default:CARD=NVidia
    HDA NVidia, ALC1200 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

```

I ran through the instructions on [HTML]http://xbmc.org/forum/showthread.php?t=42183[/HTML] from "now do these steps on your XBMC machine via putty or on the console" to the end and rebooted.

Opening alsamixer gave me a bunch more IEC options and displayed:

CARD: HDA NVidia
Chip Generic 10de NVIDIA MCP78 HDMI

I unmuted all the IEC958 options and then tried playing something.

aplay test.wav still did nothing
aplay -D hw:0,3 test.wav did play something! Woohoo!!!

This is a little puzzling because my asound.conf from the NVNews post has the following: 
pcm.digital-hw {
type hw
card 0
device 3
}

Thanks so much,

Phil/TW

---

### Post by zim2dive on 2009-01-08
Post this just in case it helps someone else...

I ran alsaconf.. and I swear I got a new item on my alsamixer options.. the channel mixer that let me select 2,4,6 channels.. which finally enabled my 6-channel output on the 3 stereo jacks on the rear of the machine (I am using these until there is a fix to the nvidia drivers for full-screen flash since I am stuck at 173 driver)

I can't really explain this, other than saying I've run alsamixer a good 40 times and very deliberately shifted to the right side every time and never saw the channels config....

---

### Post by jayman8547 on 2009-01-08
> **Torquewrench said:**
> Ok,

Progress!

Based on [HTML]http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg23969.html[/HTML] I decided to go into the BIOS and check whether changing from External CODEC to Internal + External would help under the Southbridge Setup area. It did.

I now get the following output from aplay -l:

```
dorkbot@DB5K01:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and aplay -L remains unchanged:

```
dorkbot@DB5K01:~$ aplay -L
default:CARD=NVidia
    HDA NVidia, ALC1200 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

```

I ran through the instructions on [HTML]http://xbmc.org/forum/showthread.php?t=42183[/HTML] from "now do these steps on your XBMC machine via putty or on the console" to the end and rebooted.

Opening alsamixer gave me a bunch more IEC options and displayed:

CARD: HDA NVidia
Chip Generic 10de NVIDIA MCP78 HDMI

I unmuted all the IEC958 options and then tried playing something.

aplay test.wav still did nothing
aplay -D hw:0,3 test.wav did play something! Woohoo!!!

This is a little puzzling because my asound.conf from the NVNews post has the following: 
pcm.digital-hw {
type hw
card 0
device 3
}

Thanks so much,

Phil/TW

Based on the path I have traveled, it seems you are very close....
I have the ASUS M3N78-VM mb and in the BIOS I changed the southbridge setting to whichever one was HDMI only (at work right now and don't remember off the top of my head).  Then when I ran alsamixer there were NO volume controls, only the card info.  Make sure it is unmuted by pressing M (Green box with two 00 in it).  Sorry I'm not more specific about the details but like I said I am at work and don't quite remember.

When I ran aplay -l, the output was only: 

card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

then I ran
```
#speaker-test -c 2 -D plughw:0,3
```
The 2 signifies 2 channel stereo since I only had it hooked up to my tv; plughw:0,3 means test card 0, device 3 as found out from the above aplay -l.

Output was:
speaker-test 1.0.18

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.632769

Once I had white noise I knew the system was using the HDMI audio output so the next step was forcing the system to use it - that's why you disabled analog in the BIOS, so the system had no choice but to use the HDMI.  Then by inserting the asource.conf file the default digital output device is set.  I used the asource.conf from pmosinskis in the previous link since it was for my board.  As you look at the asource.conf it can specify 4 different types of audio output - analog, mixed-analog, digital, mixed-digital which will create the devices analog-hw, dmix-analog, digital-hw, dmix-digital.

For HDMI you want to use digital-hw

Further on down the asource.conf file you will find the line > Uncomment the following to use (unmixed) "digital" by default
  slave.pcm "digital-hw"
This sets the default audio output to "digital-hw"; Then later on you specify the "digital-hw" to be 

pcm.digital-hw {
type hw
card 0
device 3
}

This is what worked for me and hopefully it helps anyone else to save them the hours and hours I spent getting this to work. I pulled info from many sources and made some educated guesses in between but I can tell you it does work!

---

### Post by juicedM3 on 2009-01-09
> **jayman8547 said:**
> I struggled with this for about a month but have got it running with much success.  I have an Myth frontend rig w /ASUS M3N78-VM and to get the HDMI audio and video to work I followed these links in order:

[http://xbmc.org/forum/showthread.php?t=42183](http://xbmc.org/forum/showthread.php?t=42183)

I know it was for a xbmc setup but follow precisely then stop at "go into settings-system-audio and change the passthrough device to hdmi..." and switch to: 

[http://www.nvnews.net/vbulletin/showthread.php?t=116286&highlight=myth&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=116286&highlight=myth&page=3)

and copied the asource.conf file into /etc/

then I went to terminal and ran "alsamixer" and hit m to unmute the sound. (box on bottom of screen changed from 2 red XX's to a green box with 2 00's)

Also, disabled SP/DIF in BIOS.

Sound works great.  Not quite sure on navigation sound because I don't really use it but Myth (Stereo and 5.1), VLC and Firefox all have sound.

I know it is very frustrating and I was ready to give up but in the end I got the comp to do what _I_ wanted it to do!

I would like to thank jayman8547 and others that have posted on to this thread.  I followed jayman's procedures.  After a lot less pain then what others have gone through, I am able to get audio and video through my HDMI cable!!

I figure I'd post some things I found that may be helpful for other people.

Setup (just important stuff):
Asus M3N78 PRO motherboard (nVidia 8300 chipset w/ Realtek ALC1200 audio)
Integra DTC-9.8 pre-processor (made sure the video & audio options are set to HDMI for whatever input you're using)
Sony KDL-46XBR5

OS:
Mythbuntu 8.10

Drivers:
nVidia 810.11.02
ALSA 1.0.18

nVidia drivers installed w/o any problems.  However, when I went to compile the ALSA drivers, it complained that SW_VIDEOOUT_INSERT was undefined and would exit with an error.  This is reported during the make.  When AlsaUpgrade compiles it, you'd never know there was an error unless you looked at the logs.  I searched the web and came across this link:

[http://article.gmane.org/gmane.linux.alsa.devel/58924](http://article.gmane.org/gmane.linux.alsa.devel/58924)

Then I searched the source code for SW_JACK_PHYSICAL_INSERT.  I found that it was defined in ./acore/jack.c.  That and other definitions matched what was posted on the link I found.  There was also a SW_VIDEO_INSERT parameter which equaled the value of the "missing" SW_VIDEOOUT_INSERT.  So I searched the code for SW_VIDEO_INSERT.  No results.  I modified ./acore/jack.c by changing SW_VIDEO_INSERT to SW_VIDEOOUT_INSERT and did a make clean && ./configure && make && make install.

It worked.  I wasn't going to complain.  I don't know too much about those definitions but replacing one that isn't needed w/ one that is needed, seems like a no brainer.

Now the important thing to remember: keep it simple.  I kept playing around w/ my MythTV settings to get the audio working and couldn't.  I kept rebooting and looking in the BIOS on how to disable my S/PDIF out.  And couldn't find anything!  Apparently that isn't an option w/ my mobo and a complete waste of time.  I was getting tired and frustrated and exited out of MythTV and tried youtube for S&G.  It worked!  Sound & video through HDMI!

I went back to MythTV and changed my audio settings to the following:

-> Utilities/Setup
 -> Setup
  -> General
    -> Hit next until you're on the Audio page

     Audio output device: ALSA:mixed-digital
     Passthrough output device: Default
     Max Audio Channels: 5.1 (I only have a 5.1 system)
     Upmix: Passive
     Enable AC3 to SPDIF passthrough: Off
     Enable DTS to SPDIF passthrough: Off
     Aggressive Sound card Buffering: Off
     Use internal volume controls: On
     Mixer Device: ALSA:default
     Mixer Controls: PCM

Audio and video now work through MythTV over HDMI.

Thanks again!

---

### Post by Cuppa-Chino on 2009-01-09
> **speed32219 said:**
> PS.  If they update Hardy to support the newer Nvidia 8000/9000 chipsets I am using that.  That new applet driven NM in 8.1 is for the birds.

NM is a dog, install wicd and you will be pleasantly surprised. [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

on a very different note: you can get both spdif and hdmi to work simulatneously, keep the internal & external setting in the bios and then an **/etc/asound.conf** (for all users, alternatively .asoundrc file in home) to setup up a new default device like below.
* select default device in mythsetup
* you can enable spdif pass through for both ac3 and dts
and both spdif and hdmi will continuously pass the sound info out, if you want to watch with your (old) home cinema just turn volumme on tv to zero and up on the spdif receiver and vice versa, obviously if you got switching/passthrough hdmi equipment that might not be necessary.

I am trying to see if I can get away from the bit rate conversion, maybe by only forcing it into the hdmi device rather than both....

```
# cat /etc/asound.conf
# Aforin konffi
# http://www.netholic.com/viewtopic.php?t=3050

pcm.!default {
        type plug
        slave {
                pcm multi
                rate 48000
        }
        ttable.0.0 1.0
        ttable.1.1 1.0
        ttable.0.2 1.0
        ttable.1.3 1.0
}

#ctl.!default hdmiout

pcm.optically {
        type hw
        card 0
        device 1
}

ctl.optically {
        type hw
        card 0
        device 1
}

pcm.hdmiout {
        type hw
        card 0
        device 3
}

ctl.hdmiout {
        type hw
        card 0
        device 3
}

pcm.multi {
        type multi
        slaves.a.pcm "hdmiout"
        slaves.a.channels 2
        slaves.b.pcm "optically"
        slaves.b.channels 2

        bindings.0.slave a
        bindings.0.channel 0
        bindings.1.slave a
        bindings.1.channel 1

        bindings.2.slave b
        bindings.2.channel 0
        bindings.3.slave b
        bindings.3.channel 1
}

ctl.multi {
        type hw
        card 0
}
```

for some reason after upgrading to 1.0.19 it did not work anymore I had to do the following:
I think I have found a regression either in the script or alsa 1.0.19 

my geforce 8300 (same as 8200) chipset did not go to spdif anymore when I had to use the script after an update, I changed from 1.0.18 to 1.0.19 during this

it took some time to figure out but I needed to add
> options snd-hda-intel model=6stack-dig to:
/etc/modprobe.d/sound 
found it here [link]("http://www.gossamer-threads.com/lists/mythtv/users/369044")

---

### Post by pools on 2009-02-20
Hi Everyone!

I make my XFX 8200 HDA nvidia sound through HDMI works.

I've compiled Alsa 1.0.19 and in HDA nvidia mixer appears an option: 
"IEC958 2", and only if I check this option the sound works.

Changing the asound.conf file now I've sound entire on my ubuntu system (Before only in the players like Totem, mplayer - setting hw=0,3 )

But an odd thing is the mixer, the volume control - I can't change the volume sound.

On the Totem and mplayer I can control the volume, but in the system (Flash, system sounds) all of them are in the max volume and I cannot change. No one mixer works. all is unmuted.

May I put something in the asound.state?

Thanks in advance!

---

### Post by felizcortez on 2009-04-19
I am having an issue getting my 8200 based graphics card to output 5.1 signals over HDMI.  I have installed Alsa 1.0.19 and 180.11 Nvidia drivers.  WHen playing a DVD using VLC it plays in stereo, if i try to switch it to 5.1 then it goes blank.  My end goal is to get this into myth and have it send the 5.1 channel audio to my tv which can then send it to my receiver.

I am outputing 2 channel (stereo) via HDMI to my TV, but I would like to get 5.1 output from DVD's or HD TV.

Here are a few of my outputs.

aplay -l outputs the following

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



aplay -L outputs the following

front:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


my /proc/asound/devices is as follows

cat /proc/asound/devices 
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  7: [ 0- 3]: hardware dependent
 16: [ 0- 0]: digital audio playback
 19: [ 0- 3]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer


```

# ~/.asoundrc or /etc/asound.conf
# ALSA configuration file

##### USAGE #####
# Save this file as "~/.asoundrc" (for user-specific sound configuration) or
# "/etc/asound.conf" (for system-wide sound configuration) and specify ALSA
# device names ad described in the next section.


##### DEVICE NAMES #####
# This configuration file defines four devices for use by the user.  Those
# devices are "analog", "mixed-analog", "digital", and "mixed-digital".  The
# user may also re-define "default" to be identical to one of the above-named
# devices (i.e. to send all sound output to the digital output unless otherwise
# specified).  Use the device names as described below:
#  - "analog" outputs to the analog output directly and (at least on software
#  sound cards) blocks other audio output.  After playback completes, "queued"
#  sounds are output in sequence.
#  - "mixed-analog" mixes audio output from multiple programs into the analog
#  output (so you can hear beeps, alerts, and other noises while playing back
#  an audio stream).
#  - "digital" outputs to the digital output directly.  Since most (all?)
#  digital outputs expect 48kHz PCM audio, this may not work for some playback
#  (i.e. CD's--which are 44.1kHz PCM audio--or 32kHz audio streams from TV
#  recordings, etc.).
#  - "mixed-digital"

# All other devices created within this file are used only by the configuration
# file itself and should /not/ be used directly.  In other words, do not use
# the devices "analog-hw", "dmix-analog", "digital-hw", or "dmix-digital".


##### IMPORTANT #####
# To make this ALSA configuration file work with your sound card, you will need
# to define the appropriate card and device information for the "analog-hw" and
# "digital-hw" devices below.  You can find the card and device information
# using "aplay -l".


##### Configuration File #####

# Override the default output used by ALSA.  If you do not override the
# default, your default device is identical to the (unmixed) "analog" device
# shown below.  If you prefer mixed and/or digital output, uncomment the
# appropriate four lines below (only one slave.pcm line).
#
# Note, also, that as of ALSA 1.0.9, "software" sound cards have been modified
# such that their default "default" device is identical to the "mixed-analog"
# device.  Whether using an ALSA version before or after 1.0.9, it does no harm
# and has no affect on performance to redefine the device (even if the
# redefinition does not change anything).  Also, by using this ALSA
# configuration file, you once again have access to unmixed analog output using
# the "analog" device.
pcm.!default {
  type plug
## Uncomment the following to use (unmixed) "analog" by default
#  slave.pcm "analog-hw"
## Uncomment the following to use "mixed-analog" by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
#  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.!default {
  type hw
  card 0
}

# Alias for (converted) analog output on the card
# - This is identical to the device named "default"--which always exists and
# refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog" to access analog
# output on the card
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is different from "default" and
# allows playback while blocking other sound sources (until playback
# completes).
pcm.analog {
  type plug
  slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the card
ctl.analog {
  type hw
  card 0
}

# Alias for (converted) mixed analog output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the dmix plugin (in this case 48000Hz)
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is identical to "default" for
# "software" sound cards.
pcm.mixed-analog {
  type plug
  slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the card
ctl.mixed-analog {
  type hw
  card 0
}

# Alias for (converted) digital (S/PDIF) output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the S/PDIF hardware (in this case 48000Hz)
pcm.digital {
  type plug
  slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the card
ctl.digital {
  type hw
  card 0
}

# Alias for mixed (converted) digital (S/PDIF) output on the card
#  - This will accept audio input--regardless of rate--and convert to the rate
#  required for the S/PDIF hardware (in this case 48000Hz)
pcm.mixed-digital {
  type plug
  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.mixed-digital {
  type hw
  card 0
}

# The following devices are not useful by themselves.  They require specific
# rates, channels, and formats.  Therefore, you probably do not want to use
# them directly.  Instead use of of the devices defined above.

# Alias for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.analog-hw {
  type hw
  card 0
  # The default value for device is 0, so no need to specify
#  - Uncomment one of the below or create a new "device N" line as appropriate
#    for your sound card or 
#  device 1
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.analog-hw {
  type hw
  card 0
}

# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {
  type hw
  card 0
  device 3
#  - Comment out "device 1" above and uncomment one of the below or create a
#    new "device N" line as appropriate for your sound card or 
#  device 2
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.digital-hw {
  type hw
  card 0
}

# Direct software mixing plugin for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-analog {
  type dmix
  ipc_key 1234
  slave {
    pcm "analog-hw"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}

# Control device (mixer, etc.) for the card
ctl.dmix-analog {
  type hw
  card 0
}

# Direct software mixing plugin for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.dmix-digital {
  type dmix
  ipc_key 1235
  slave {
    pcm "digital-hw"
    period_time 0
    period_size 1024
    buffer_size 4096
    rate 48000
  } 
}

# Control device (mixer, etc.) for the card
ctl.dmix-digital {
  type hw
  card 0
}


```

When i try to run a speaker test using the following, I only get sound on the front left and right speakers, no sound on any of the others.


david@david-desktop:~$ speaker-test -c 6 -D plughw:0,3

speaker-test 1.0.19

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 17.579562


Any help would be greatly appreciated, I have been working on this a few days and trying to follow the forum advice.  Thanks.

---

### Post by Cuppa-Chino on 2009-04-19
> **felizcortez said:**
> I am having an issue getting my 8200 based graphics card to output 5.1 signals over HDMI...

Any help would be greatly appreciated, I have been working on this a few days and trying to follow the forum advice.  Thanks.

can you get 5.1 via spdif, if your board has that?

---

### Post by felizcortez on 2009-04-20
I'm not sure that will work.  My board has a SPDIF output on it.  Aplay-l outputs the following and I don't 'see the digital output for SPDIF. 

How would i enable the SPDIF?

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
Subdevices: 2/2
Subdevice #0: subdevice #0
Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by galaxsat on 2009-07-18
Cuppa-Chino:

I'm so close to reaching my goal of simultaneous audio via spdif and hdmi. In mythtv, I can get 5.1 over spdif, and I can get simultaneous 2-channel audio over both (thanks to the netholic asound.conf), but I cannot seem to unlock the secret of getting 5.1 over spdif without losing hdmi audio in mythtv. I can get audio if I run a speaker test on the hdmi while watching mythtv in 5.1 over spdif, so I am sure it's my mythtv configuration (or a mythtv limitation). If you have what I want from your mythtv setup, please share your mythtv audio settings.

---

### Post by galaxsat on 2009-07-19
I figured out mythtv audio settings to get 5.1 out via spdif without losing hdmi audio. For others that might be searching for the solution:
-Audio output device: ALSA:default
-Passthrough output device: Default
-Max Audio Channels: 5.1
-Upmix: Passive
-Enable AC3/DTS to SPDIF passthrough: Check
-Use internal volume controls: Uncheck

Other pertinent info:
-I did use the ALSA update script. My ALSA version is 1.0.20. I had to do this to light up my homemade toslink connected to the external header of my Asus M3N78-VM.
-NVIDIA Driver Version: 180.44

---

### Post by galaxsat on 2009-08-01
Well, I'm not sure what I did other than a reboot, but I am back to where I was. I can't seem to get 5.1 through SPDIF without losing HDMI audio, so suggestions are welcome. I can get 5.1 via SPDIF with no HDMI audio, but all I get with both enabled is an initial pop, snap, or click out of the SPDIF. I can still get audio out out both outputs, but the SPDIF is not 5.1 when I do.

MB is an ASUS M3N78-VM, SPDIF attached to the external header and using the netholic asound.conf with 'type multi' parameter.

---

