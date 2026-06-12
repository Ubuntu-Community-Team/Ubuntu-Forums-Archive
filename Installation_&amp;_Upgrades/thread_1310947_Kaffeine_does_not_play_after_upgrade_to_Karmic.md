---
title: "Kaffeine does not play after upgrade to Karmic"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Donnw on 2009-11-02
I had Kaffeine installed on 9.04 and was working perfectly, but after upgrading to Karmic it starts up and will not play anything at all. If it is started from the terminal I get the following output

Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableSubtitlesChanged()
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableAudioChannelsChanged()
Object::connect: No such signal Phonon::Gstreamer::MediaObject::titleChanged(int)
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableTitlesChanged(int)
Object::connect: No such signal Phonon::Gstreamer::MediaObject::chapterChanged(int)
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableChaptersChanged(int)
Object::connect: No such signal Phonon::Gstreamer::MediaObject::angleChanged(int)
Object::connect: No such signal Phonon::Gstreamer::MediaObject::availableAnglesChanged(int)


when kaffeine is started from the menu I get the message -

the audio playback device ICH6 with ACL655(Intel ICH6) does not work falling back to default.

Other Apps such as Totem and mplayer seem to work ok so far.

My lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

---

### Post by fjpos on 2009-11-04
Exact same problem for me two. Have to find out what is missing

---

### Post by realzippy on 2009-11-04
Talking about the "new" kaffeine?(version?)

---

### Post by Donnw on 2009-11-04
Sorry its version 4.3.2. Looks like a newer version than what I already had installed.

---

### Post by realzippy on 2009-11-04
Found a ppa to downgrade to good old kaffeine that works;completely remove Kaffeine 1.0-pre2 before.

wget [https://launchpad.net/~pkern/+archiv...~ppa0_i386.deb](https://launchpad.net/~pkern/+archiv...~ppa0_i386.deb)
sudo dpkg -i kaffeine_0.8.7-1ubuntu6~ppa0_i386.deb

64bit:
wget [https://launchpad.net/~pkern/+archiv...ppa0_amd64.deb](https://launchpad.net/~pkern/+archiv...ppa0_amd64.deb)
sudo dpkg -i kaffeine_0.8.7-1ubuntu6~ppa0_amd64.deb

---

### Post by howefield on 2009-11-04
> **Donnw said:**
> I had Kaffeine installed on 9.04 and was working perfectly, but after upgrading to Karmic it starts up and will not play anything at all.

Have you checked launchpad ? there are a few threads that look very much like yours - with solutions, eg.

[https://bugs.launchpad.net/kaffeine/+bug/453916](https://bugs.launchpad.net/kaffeine/+bug/453916)

---

### Post by Donnw on 2009-11-05
Thanks for that help. I have fixed it by simply installing 
phonon-backend-xine as suggested in the launchpad bug.

Thanks again

---

### Post by absalom on 2009-12-25
> **realzippy said:**
> Found a ppa to downgrade to good old kaffeine that works;completely remove Kaffeine 1.0-pre2 before.

wget [https://launchpad.net/~pkern/+archiv...~ppa0_i386.deb](https://launchpad.net/~pkern/+archiv...~ppa0_i386.deb)
sudo dpkg -i kaffeine_0.8.7-1ubuntu6~ppa0_i386.deb

64bit:
wget [https://launchpad.net/~pkern/+archiv...ppa0_amd64.deb](https://launchpad.net/~pkern/+archiv...ppa0_amd64.deb)
sudo dpkg -i kaffeine_0.8.7-1ubuntu6~ppa0_amd64.deb


Too bad this no longer works.

I have a different problem with karmic/kaffeine and dvb-c, but it all worked so nicely in 0.8.7.

Anyone else know of another downgrade url?

---

### Post by Col-1023 on 2009-12-26
I upgraded to karmic and now have a problem with kaffeine and scheduled recordings.

If I record a SD channel (Australia) with mp3 (MP2) audio it seems to record both audio and video ok, and I can demux and re-encode the clip.

If I try to record a HD channel such as ABC-Hd with AC3 448 Kbps sound, I get the video no problems, but NO AUDIO.

When I use projectx to demux the HD stream, there is literally no audio stream detected, just the video.

My USB DVB-T stick worked well with kaffeine and jaunty, so what happened during the upgrade, and is there a fix for my problem.

I get no errors from kaffeine when I set it to record the HD channel.

I can play previously recorded videos with AC3 448 Kbps sound, so I assume the AC3 codec is installed.

Any help appreciated.

---

### Post by Gorlist on 2009-12-28
Try here instead:

[https://launchpad.net/~pkern/+archive/ppa/+sourcepub/652996/+listing-archive-extra](https://launchpad.net/~pkern/+archive/ppa/+sourcepub/652996/+listing-archive-extra)

---

### Post by Col-1023 on 2009-12-31
I've installed the phonon-backend package and libxine1-ffmpeg was already installed,  and still no luck getting my pinacle usb dvb-t nanostick to capture the ac-3 channel of the australian abc-hd channel.

If I download the amd64 deb from the link provided by gorlist, how do I install that old version of kaffein, and should it solve my problem.

I Assume I would have to use synaptic package manager to uninstall the current version of kaffein, but are there any other steps besides clicking on the deb package that I need to take.

I don't want to bork my setup, since I can still capture all SD channels, since they don't have ac3 audio.

TIA.

---

### Post by Col-1023 on 2010-01-05
Does uninstalling the current karmic version of kaffeine and installing the older version from Gorlist's link fix all the problems?

The upgrade from jaunty to karmic went smoothly, so I have no idea whey when I do a scheduled recording of a dvb tv stream, the ac3 sound component is not captured.

Any help appreciated.

---

### Post by Col-1023 on 2010-01-06
bump

---

### Post by Col-1023 on 2010-01-07
any help with this, I don't want to do any unnecessary damage to my system, so will using the older kaffeine deb from the launchpad link cause problems in karmic?

Has anyone else tried it?

TIA

---

### Post by sergius248 on 2010-04-02
From [https://bugs.launchpad.net/kaffeine/+bug/453916?comments=all](https://bugs.launchpad.net/kaffeine/+bug/453916?comments=all)
Fred61 wrote on 2009-10-31 wrote:
-----------------------------------------------
Problem fixed!

Adding package phonon-backend-xine removed the above error messages but lead to a new error:

demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.

Then I added
 - libxine1-plugins
 - libxine1-all-plugins

Now kaffeine is able to select and display the DVB channels!

I hope this will help.
---------------------------------------------

I have tried and it works!!
Still I have not the "preference option" displayed.

---

