---
title: "ubuntu 10.04 thinkpad x100e mic doesn't work"
date: 2010-05-20
forum: Hardware
---

### Post by bdutzz on 2010-05-20
did anyone experience same thing as me?
thinkpad x100e with ubuntu 10.04 amd64 mic doesn't work, either with sound recorder or skype, actually skype is the reason why i need mic.

---

### Post by bdutzz on 2010-05-22
could anyone tell me which package control mic and how to tell if it works well or not with the mic?

---

### Post by lidex on 2010-05-23
Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.

Then use pulseaudio volume control (pavucontrol), input devices tab, to select mic.

Install:
Terminal="Applications->Accessories->Terminal"
```
sudo apt-get install gnome-alsamixer pavucontrol
```

---

### Post by bdutzz on 2010-05-24
thx, i'll try it now

btw no on use thinkpad x100e?
i want to know whether your mic works or not... or it's only me who this issue

edit:
this is alsamixer **Edit -> Sound Card Properties**, dunno why there's so much mic there.... i dunno which one is mine but by default all of them is enabled, and still cant get my mic to work

[IMG]http://i45.tinypic.com/64j7me.png[/IMG]

---

### Post by lidex on 2010-05-25
What are your vitals? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by bdutzz on 2010-05-26
thx lidex for your update and support ^^
it's thinkpad x100e here's the [spec]("http://i40.tinypic.com/34hw1g7.png") from wedoz, hope it might give you some information

i really hope i can use skype on my ubuntu

```
bdutzz@bdutzz-laptop:~$ uname -a
Linux bdutzz-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
bdutzz@bdutzz-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bdutzz@bdutzz-laptop:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May 20 2010 for kernel 2.6.32-22-generic (SMP).
bdutzz@bdutzz-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20582 (Pebble)
```

---

### Post by lidex on 2010-05-26
These conextant codecs usually respond well to an alsa upgrade. Follow the alsa-upgrade link in my sig.

---

### Post by bdutzz on 2010-05-26
i've done it once before,still not working, revert the kernel back to original alsa.

but i'll give it another try after office today, for the advice, i'll report tonight

oh.. and actually the playback works well :) it's just about the mic that doesn't work

---

### Post by lidex on 2010-05-26
Your best shot is with latest alsa, so don't downgrade it if it alone doesn't work.

---

### Post by bdutzz on 2010-05-27
installed alsa upgrade... and the mic still not working :(

---

### Post by dino99 on 2010-05-27
have you set your prefs with gnome-alsamixer ?
(apps sound gnome-alsamixer)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by lidex on 2010-05-29
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=lenovo-101e 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

If that doesn't work, here are more options to try (after the '='):
```
laptop
lenovo
thinkpad
```

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

---

### Post by JackxLonsdale on 2010-06-04
I found using a combination of google translate on the japanese forums and general installation that if you use the ubuntu-audio-dev ppa 
(sudo add-apt-repository  ppa:ubuntu-audio-dev/ppa)
and the update and install the kernel appropriate linux-alsa-driver-modules (linux-alsa-driver-modules-2..6.32.xx) and NOT the container package (backports-modules) it works.

For some reason the backports-modules never worked

---

### Post by dirkvs on 2010-06-04
I have exactly the same problem - Ubuntu 10.04 on a Lenovo Thinkpad x100e. Note that the hardware is AMD based and not Intel. Also, there is only one audio jack that does both mic in and headphone out.

bdutzz - did any of the above work for you?

lidex - gnome-alsamixer is not installed by default on Ubuntu 10.04. If I install it, will it interfere with PulseAudio?

---

### Post by lidex on 2010-06-04
> **dirkvs said:**
> I have exactly the same problem - Ubuntu 10.04 on a Lenovo Thinkpad x100e. Note that the hardware is AMD based and not Intel. Also, there is only one audio jack that does both mic in and headphone out.

bdutzz - did any of the above work for you?

lidex - gnome-alsamixer is not installed by default on Ubuntu 10.04. If I install it, will it interfere with PulseAudio?

No.

---

### Post by the_master on 2010-06-05
> **JackxLonsdale said:**
> I found using a combination of google translate on the japanese forums and general installation that if you use the ubuntu-audio-dev ppa 
(sudo add-apt-repository  ppa:ubuntu-audio-dev/ppa)
and the update and install the kernel appropriate linux-alsa-driver-modules (linux-alsa-driver-modules-2..6.32.xx) and NOT the container package (backports-modules) it works.

For some reason the backports-modules never worked

Just to elaborate after you install the repository you will want to search for "linux-alsa-driver-modules-2.6.32-xx-generic" and install the package that is the same as your kernel(mine was 2.6.32.21)

I also had to reboot before it would find those packages for some reason.

Edit: however, this didn't work for me at all, it actually broke sound all together so i am lost.  Anyone know how to revert back to the stock kernel?

---

### Post by dirkvs on 2010-06-14
I still haven't managed to get a microphone working with Ubuntu 10.04 on the thinkpad x100e. 

Anyone else have better luck?

---

### Post by dirkvs on 2010-07-01
Bump. This is still a problem.

I am now running the 2.6.32.23 kernel (upgraded through Update Manager).
I also upgraded the x100e BIOS to the latest version, v1.25.

Has anyone managed to get the microphone working on the x100e yet? I don't want to dual-boot just to make voice calls. :(

---

### Post by xenzero on 2010-07-05
Bump.  Mic not working for me either.  I'm unclear where the software problem lies - if someone can provide clarity on that, I'm happy to raise a bug with the appropriate group.

---

### Post by juliobahar on 2010-07-07
The mic is not working for me either. 
I've tried upgrading the kernel to the mainline 2.6.34 version, according to one review - [here]("http://www.thinkwiki.org/wiki/Category:X100e") - but the problem was that computer freezes at the LOGIN screen, error reporting turned out to be a conflict with the ATI proprietary driver.

For which I had to revert back to kernel 2.6.32 & restore the xorg.conf file.

Other issues: Bluetooth can't be enabled on ubuntu. Some function keys aren't working. 

We all need guidance!!! thanks

---

### Post by spfldadm on 2010-07-07
I had to revert back to Skype 2.1.0.47, I couldn't get 2.1.0.81 to work. There is a discussion on the Skype forum about this problem.

---

### Post by lidex on 2010-07-07
I would suggest upgrading your alsa install to version 1.0.23 using the alsa-upgrade link in my sig. If no help there, try the alsa-base.conf edit I posted previously. Still no help? Need more info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by battybiologist on 2010-07-13
same problem, x100e (model 3508CTO) from lenovo.
I did a little digging and found [http://www.thinkwiki.org/wiki/CX20582](http://www.thinkwiki.org/wiki/CX20582) from the output of the commands previously mentioned; looking on the alsa wiki, "ALSA: hda - Add CX20582 and OLPC XO-1.5 suppor" is in the changes to 1.0.21. I've tried lenovo, lenovo-101e, olpc-xo-1_5, laptop, thinkpad, lenovo-100e, and lenovo-x100e (all appended to options snd-hda-intel model=), and these have all not gotten the mic to work. system info is below.

```
henry@soundwave:~$ uname -a
Linux soundwave 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
henry@soundwave:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
henry@soundwave:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                  1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                           0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
henry@soundwave:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20582 (Pebble)

```

any help is greatly appreciated! I run a pen-and-paper RPG over skype, and rebooting is a pain.

---

### Post by lidex on 2010-07-13
Need to solve this thing already. Try this for me please.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by battybiologist on 2010-07-13
[IMG]http://i468.photobucket.com/albums/rr49/truthiness1/forum%20stuff/micwork.png[/IMG]

Still doesn't seem to work :???:

---

### Post by lidex on 2010-07-13
OK. Now try pulseaudio volume control (pavucontrol). Unlink the sliders and turn one all the way down and the other one up and see if it works. See below.

---

### Post by battybiologist on 2010-07-14
nope, no dice. according to [http://http://thinkpad-x100e.blogspot.com/2010/05/how-to-activate-thinkpad-x100es-built.html]("http://http//thinkpad-x100e.blogspot.com/2010/05/how-to-activate-thinkpad-x100es-built.html"), installing device chooser did it in karmic, though it has no effect on my lucid install.[URL="http://http//thinkpad-x100e.blogspot.com/2010/05/how-to-activate-thinkpad-x100es-built.html"]
[/URL]

---

### Post by lidex on 2010-07-14
You do have the conexant chip. There are drivers on this page that very well may solve your problems. Make sure to get the right version.
[http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

---

### Post by battybiologist on 2010-07-14
huzzah! success :D

---

### Post by juliobahar on 2010-07-14
> **lidex said:**
> You do have the conexant chip. There are drivers on this page that very well may solve your problems. Make sure to get the right version.
[http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

Finally someone has come out with the solution. I must say this thread should be tagged SOLVED!!!

Well I've downloaded the .deb.zip file from the above link. Installed it it really took a while building the source against my kernel.

Now I can use my mic (which turned out to be on a conexant chipset). 

Good Job.

---

### Post by juliobahar on 2010-08-11
I have to reinstall the linuxant HDA driver every time I want to use the mic. besides most of the time the mic. doesn't turn on. 

I was eluded by the fact that it worked for the first time, hence my last comment.

I need help with this silly x100e

---

### Post by jeffmings on 2010-09-17
I have been trying to get the microphone to truly work on my ThinkPad x100e for some time.  I purchased the Thinkpad solely to run Ubuntu, and have only booted into Win7 a few times, so I was very frustrated with the microphone not working.  I ended up buying a SoundBlaster X-Fi USB sound card.  This works perfectly with Ubuntu, but plugging it in everytime I want to make a voip call is a pain.
    This thread showed me how to solve the problem, but it's a bit scattered.  Here is the winning combination for me in a step-by-step listing:

-Alsa driver upgrade- add the repository for the ALSA PPA using the command   sudo add-apt-repository ppa:ubuntu-audio-dev/ppa ,  then open up Synaptic, hit reload, and get the new Alsa for your kernel. I used   linux-alsa-driver-modules-2.6.32-24-generic.

-Chipset driver- The good folks at Linuxant have made new toys for us at: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) .  I grabbed:
[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip) , unzipped it, and ran it.  It takes a while to compile itself against your kernel.

-Modprobe entries-  I tried a few combinations, and ended using this at the bottom of /etc/modprobe.d/alsa-base.conf:

# per Ubuntu forum suggestion to fix mic after alsa upgrade
options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes

(Guys, remember to make a copy of alsa-base.conf BEFORE you change it)

After a few reboots, the built-in mic and the mic via the combo jack still work, so it seems to be good!

I am using the headphone/mic combo that came with my Android phone, but am hoping to find a better combo. Anyone tried the iPhone headphone/mic units with their X100e?

Aloha,
-Jeff Mings

---

### Post by lidex on 2010-09-17
> **jeffmings said:**
> I have been trying to get the microphone to truly work on my ThinkPad x100e for some time.  I purchased the Thinkpad solely to run Ubuntu, and have only booted into Win7 a few times, so I was very frustrated with the microphone not working.  I ended up buying a SoundBlaster X-Fi USB sound card.  This works perfectly with Ubuntu, but plugging it in everytime I want to make a voip call is a pain.
    This thread showed me how to solve the problem, but it's a bit scattered.  Here is the winning combination for me in a step-by-step listing:

-Alsa driver upgrade- add the repository for the ALSA PPA using the command   sudo add-apt-repository ppa:ubuntu-audio-dev/ppa ,  then open up Synaptic, hit reload, and get the new Alsa for your kernel. I used   linux-alsa-driver-modules-2.6.32-24-generic.

-Chipset driver- The good folks at Linuxant have made new toys for us at: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) .  I grabbed:
[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip) , unzipped it, and ran it.  It takes a while to compile itself against your kernel.

-Modprobe entries-  I tried a few combinations, and ended using this at the bottom of /etc/modprobe.d/alsa-base.conf:

# per Ubuntu forum suggestion to fix mic after alsa upgrade
options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes

(Guys, remember to make a copy of alsa-base.conf BEFORE you change it)

After a few reboots, the built-in mic and the mic via the combo jack still work, so it seems to be good!

I am using the headphone/mic combo that came with my Android phone, but am hoping to find a better combo. Anyone tried the iPhone headphone/mic units with their X100e?

Aloha,
-Jeff Mings

It would seem that 3 different alsa versions is overkill since the linuxant driver - if I am not mistaken - is basically alsa with conexant patch. In other words, there shouldn't be a reason to upgrade alsa just to overwrite it with linuxant. Next time try just installing linuxant and see how that fares. Could save you some trouble. ;)

---

### Post by battybiologist on 2010-09-17
> **lidex said:**
> It would seem that 3 different alsa versions is overkill since the linuxant driver - if I am not mistaken - is basically alsa with conexant patch. In other words, there shouldn't be a reason to upgrade alsa just to overwrite it with linuxant. Next time try just installing linuxant and see how that fares. Could save you some trouble. ;)

 Agreed.  I had a similar problem with skype only where it would lock me out of microphone input once skype booted up or when I began calling, but I found a simple solution - either give yourself audio and video via the route System -> Administration -> Users and Groups -> Manage Groups -> user name -> User Privileges -> Use audio devices and use video devices, or by using gksudo skype.  It should be noted that sometimes linuxant worked and sometimes it didn't until I tried this.

---

### Post by robfuller on 2010-09-24
Jeff, thank you! Your two lines of options to add to alsa-base.conf have been the breakthrough which has made my microphone and headphone socket work after hours of puzzling over this.

Just to note, I didn't install the linuxant driver - but I am running the Ubuntu 10.10 beta (kernel 2.6.35), so maybe that's the difference. Still I didn't have a working mike or headphone socket until I used your modifications to alsa-base.conf.

---

### Post by zacbri on 2010-10-06
Those alsa options worked for me too without installing new packages on 10.10-rc.

Thanks!

---

### Post by juliobahar on 2010-10-06
> **zacbri said:**
> Those alsa options worked for me too without installing new packages on 10.10-rc.

Thanks!

What options are those you just mentioned?

I still can't get my mic to work without the modded 1.0.23 Linuxant driver

---

### Post by rewbs on 2010-10-22
Thanks guys! Found this thread within minutes of noticing that audio played on the built-in speakers even when I had headphones plugged in. On 10.10 with kernel 2.6.35-22-generic-pae, just adding these options to /etc/modprobe.d/alsa-base.conf and rebooting sorted the issue.

```
# per Ubuntu forum suggestion to fix mic after alsa upgrade
options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes
```

Thanks again!

---

### Post by Dis89 on 2010-10-26
Thanks, editing the .conf helps

---

### Post by Gouzi001 on 2010-10-27
Hi guys, I have also x100e, with conexant driver everything works fine. After update to 10.10 microphone stop working, and after instalation of conexant driver, who fail, after reboot sound&bluetooth stop work at all. After some elaboration I decide to reinstall (anyway I need more space for ubuntu:-) ).

After pure instalation 10.10 sound works, microphone still. K.O. So i have added 2 lines:: "options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes".
Result ? Sound does not work at all.(even after return changes).

But problem is not in ALSA.. it seems some problem with .gvfs.,
cause now virtual link (same as before reinstallation), in home directory
is RED and ?.gvfs (in mc).

Anyone, let me know how to solve that.. I have try to reinstall (before reinstall :-D )  dpkg-reconfigure,.. reinstall alsa.. also all common files with gvfs, libs...  result ? > no sound at all.. :-(

---

### Post by juliobahar on 2010-10-27
> **Gouzi001 said:**
> Anyone, let me know how to solve that.. I have try to reinstall (before reinstall :-D )  dpkg-reconfigure,.. reinstall alsa.. also all common files with gvfs, libs...  result ? > no sound at all.. :-(

My Advice - since this worked for me - 
1- Use ubuntu 10,10 64-bit
2- Don't download the modded ALSA driver
3- Edit your /etc/modprobe.d/alsa-base.conf as per this thread.

Enjoy your fast Lenovo Thinkpad X100e. You will have other issues then to worry about. Btw what is .gvfs?

---

### Post by lidex on 2010-10-27
> **Gouzi001 said:**
> Hi guys, I have also x100e, with conexant driver everything works fine. After update to 10.10 microphone stop working, and after instalation of conexant driver, who fail, after reboot sound&bluetooth stop work at all. After some elaboration I decide to reinstall (anyway I need more space for ubuntu:-) ).

After pure instalation 10.10 sound works, microphone still. K.O. So i have added 2 lines:: "options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes".
Result ? Sound does not work at all.(even after return changes).

But problem is not in ALSA.. it seems some problem with .gvfs.,
cause now virtual link (same as before reinstallation), in home directory
is RED and ?.gvfs (in mc).

Anyone, let me know how to solve that.. I have try to reinstall (before reinstall :-D )  dpkg-reconfigure,.. reinstall alsa.. also all common files with gvfs, libs...  result ? > no sound at all.. :-(

Have a look here:
[http://ubuntuforums.org/showthread.php?t=1327560](http://ubuntuforums.org/showthread.php?t=1327560)
Once you fix that problem run the alsa-info script. 
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Gouzi001 on 2010-10-29
Output::
 [http://www.alsa-project.org/db/?f=55c0e36d0ee0b9ca95637c6125688c533d850e8d](http://www.alsa-project.org/db/?f=55c0e36d0ee0b9ca95637c6125688c533d850e8d)

PS: better to use ALT+F2 than drain menu :-)

---

### Post by Gouzi001 on 2010-10-29
If you read my post well...
1.I didnt d.load any additional/reinstall ALSA..
2.After edit alsabase...gvfs from unknow reasons die..
GVFS(gnome virtual file system) if i understood well is layer who "comunicate" between core,Libs & user. Same as you can see devices in /dev/.. thanks to GVFS you can acess serivces such sound, bluetooth &&... and you can see layer service as .gvfs in your home folder. If this Linkage is broken,.. you can see it in MC red = my case.

---

### Post by juliobahar on 2010-10-30
I'm really not getting it. what is this whole thing about?!

why should there be a problem is this gvfs thing? 

Do we really need to fix it, if it really was a problem?

Is it related to our microphone not working bit?

btw I tried the thread mentioned by lidex and I wasn't able to get anywhere.

---

### Post by juliobahar on 2010-10-30
> **rewbs said:**
> Thanks guys! Found this thread within minutes of noticing that audio played on the built-in speakers even when I had headphones plugged in. On 10.10 with kernel 2.6.35-22-generic-pae, just adding these options to /etc/modprobe.d/alsa-base.conf and rebooting sorted the issue.

```
# per Ubuntu forum suggestion to fix mic after alsa upgrade
options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes
```

Thanks again!

I must say this also worked for me, keeping fingers crossed for it to remain in this way. I'm running 
Ubuntu Kernel 2.6.35-22-generic #35-Ubuntu SMP x86_64 GNU/Linux

---

### Post by lidex on 2010-10-30
> **Gouzi001 said:**
> Output::
 [http://www.alsa-project.org/db/?f=55c0e36d0ee0b9ca95637c6125688c533d850e8d](http://www.alsa-project.org/db/?f=55c0e36d0ee0b9ca95637c6125688c533d850e8d)

PS: better to use ALT+F2 than drain menu :-)

Wow. Post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by Gouzi001 on 2010-10-30
cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

---

### Post by lidex on 2010-11-03
> **Gouzi001 said:**
> cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-hda-intel model=lenovo-101e
options snd-hda-intel position_fix=1 enable=yes
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

You have onboard sound card as well as a PCI device. ALSA recognizes the onboard but not the other. Do this for me please:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
Now post this output please:
```
sudo lshw -C multimedia
```

---

### Post by Gouzi001 on 2010-11-04
xxx@GT:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
rm: nelze odstranit „/home/gouzi/.asound*“: No such file or directory
xxx@GT:~$ sudo rm /etc/asound.conf
[sudo] password for gouzi: 
rm: nelze odstranit „/etc/asound.conf“: No such file or directory
xxx@GT:~$ sudo lshw -C multimedia
  *-multimedia UNCLAIMED  
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:d0600000-d0603fff

---

### Post by lidex on 2010-11-04
This is whacked. Try removing this line from alsa-base.conf
```
options snd-hda-intel position_fix=1 enable=yes
```
Change the model on the other line from:
```
lenovo-101e
to
thinkpad
```
Reboot.

---

### Post by Gouzi001 on 2010-11-06
I had applied changes as you wrote and no changes.

root@GT:~# alsamixer
nemohu otev&#345;ít sm&#283;&#353;ova&#269;: No such file or directory
root@GT:~# alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/gouzi/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/gouzi/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hwdep snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hwdep snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
root@GT:

---

### Post by Smarty341 on 2010-12-05
It seems that the issue isn't resolved and I couldn't find the solution anywhere on the net. 

I would like to raise the question again. 

I had a 2.6.35-22 kernel and simply modifying the alsa-base.conf worked for me perfectly fine. However, yesterday I've upgraded to 2.6.35.23 and the mic doesn't work again and that annoys me a lot, I have to admit. 

Solutions of above - further editing alsa-base.conf, commenting the lines doesn't work. Booting the old kernel doesn't work either. 

I would be grateful for any help.

THanks.

---

### Post by lidex on 2010-12-05
@Smarty341
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

