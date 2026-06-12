---
title: "[SOLVED] Sound used to work..not now"
date: 2008-08-18
forum: Hardware
---

### Post by Banny706 on 2008-08-18
On my Toshiba P10, the sound used to work flawlessly.  After installing Ubuntu a few times, the sound no longer works.  (I was experimenting) What happens when I log on is the opening sound file for logging on will play momentarily then just cut out before the sound clip is done.  Then the sound does not work no more in Ubuntu.  The sound works fine with XP.  I think the sound hardware is Realtek.  I even tried to install Gutsy thinking that it may be the Pulseaudio server in Hardy crapping out but I get the same issue with ALSA in Gutsy.  Anybody run into problems like this?  Any help would be appreciated.  Thanks.

---

### Post by markbuntu on 2008-08-18
Have you tried making a new user in System/Administration/Users and Groups and logging in with that?

---

### Post by Banny706 on 2008-08-18
No I didn't, my user is the super user.  What would that have to do with the sound?

---

### Post by markbuntu on 2008-08-19
Well, it will set up the new user with the system defaults. If that works then you just have some configuration problem in your own ~/. files, most likely ~/.asoundrc.asoundconf. You can then compare the files and fix the one that is not working.

It is an easy way to figure out if you have a system wide problem or just a user configuration issue.

---

### Post by Banny706 on 2008-08-20
Thanks for the help.  I didn't try your solution yet because I installed XP back on a few weeks ago to see if it was a hardware problem.  I haven't yet got around to putting my fave OS back on.  Last night, I played around with LiveCD versions of Kubuntu, Xubuntu, PCLinuxOS 2007, and PCLinuxOS 2008 Gnome Version.  The sound works fine for those distros but not with Ubuntu.  When I get the time this weekend, I am going to install Ubuntu back on the laptop and try out what you suggested.  I hope the LiveCDs helped in troubleshooting the problem.

---

### Post by Banny706 on 2008-08-28
Further update to trying to figure out this problem.  When I first bought this laptop in early July, I installed Ubuntu on it and everything worked out of the box excluding the SD card reader.  Not a big deal.  After doing a couple of reinstalls, the sound doesn't work properly anymore.  I re-installed XP to see if it was a hardware problem in the sound device and it works fine.  The sound also works OutOfTheBox with these OS's:  Kubuntu, Xubuntu, PCLinuxOS 2007, Mandriva 2008, Sabayon 3.5, openSuse 11 KDE4 and Gnome.  Frankly, its ticking me off because I like Gnome and dislike KDE.  When in LiveCD of Ubuntu, the sound only works momentarily when it boots in.  Meaning the nice little African logging on sound plays and I hear it but the sound stops before the log on clip is finished.  When I go into System>Preferences>Sound, these results are what I get from the sound tests.  When Sound Playback is set on Autodetect and PulseAudioServer, it tests but no sound is heard.  When ATI IXP 97, ALSA and OSS are tested, I get this error message:

"audiotestsrc wave=sine frq=512 ! audioconvert ! audioresample ! gconfaudiosink:  Could not open audio device for playback.  Device is being used by another application."

I have included the screenshots:

[ATTACH]83185[/ATTACH]

[ATTACH]83186[/ATTACH]

[ATTACH]83187[/ATTACH]

[ATTACH]83188[/ATTACH]

[ATTACH]83189[/ATTACH]

I really need some help and appreciate it.

---

### Post by Banny706 on 2008-08-28
Oh BTW for markbuntu, I could not find the ~/.asoundrc.asoundconf file.  As far as the file search is concerned, it doesn't exist.  I did create another user using the LiveCd which works but the sound problem remains.  Looks to be Ubuntu wide problem.  Strange considering it used to work fine before.  Thanks for the help markbuntu.

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > lspci

---

### Post by Banny706 on 2008-08-28
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 1)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller

---

### Post by Banny706 on 2008-09-10
For now, I am going to call this one solved.  I installed Intrepid Ibex Alpha 5 last night and the sound worked fine.  Looking forward to the next release.

---

