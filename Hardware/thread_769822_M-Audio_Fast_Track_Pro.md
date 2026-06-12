---
title: "M-Audio Fast Track Pro"
date: 2008-04-26
forum: Hardware
---

### Post by thetechguyz on 2008-04-26
I'm using Ubuntu 8.04 with a USB M-Audio Fast Track Pro. I have been looking to find the software to install the firmware to this device and hopefully getting this to work with my notebook PC. So, if you have any information I would be most appreciative.

---

### Post by fareastside on 2008-05-11
Sorry I can't help you, but I feel your pain. I've been googling all over the place to try and get my M-Audio Transit USB to work with Ubuntu 8.04. I found these sets of instructions, neither of which works..

[http://www.head-fi.org/forums/f46/how-make-m-audio-transit-worn-ubuntu-243027/](http://www.head-fi.org/forums/f46/how-make-m-audio-transit-worn-ubuntu-243027/)
[http://www.head-fi.org/forums/f46/m-audio-transit-ubuntu-7-04-feisty-fawn-241650/](http://www.head-fi.org/forums/f46/m-audio-transit-ubuntu-7-04-feisty-fawn-241650/)

Seems to be something with this madfu software.. which seems it has not been updated in a while. Has anyone gotten madfu to work with any M-Audio device on Ubuntu 8.04?

---

### Post by mcphargus on 2008-05-19
[http://ubuntuforums.org/showthread.php?t=447744&highlight=qjackctl+m-audio+usb]("http://ubuntuforums.org/showthread.php?t=447744&highlight=qjackctl+m-audio+usb")

Got a Fast Track USB and was up till 4 AM banging my head against the table, but this post helped me lots. Hope it helps you.

---

### Post by thetechguyz on 2008-05-23
Thanks! I'm going to download Ubuntu Studio 8.04 and try this out... :)

---

### Post by trriss on 2008-07-23
> **thetechguyz said:**
> I'm using Ubuntu 8.04 with a USB M-Audio Fast Track Pro. I have been looking to find the software to install the firmware to this device 

Don't know if you're still looking for solutions, but this device doesn't need firmware to be uploaded, it's usb audio class-compliant....

alsa might need to be patched in order to get 24 bit instead of 16 though, haven't worked that out yet...

[http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro)

---

### Post by overdrank on 2008-07-23
I realize it may be a little late but moving this thread out of the Hardware team forum.  :)

---

### Post by mulperi on 2008-08-06
I found a simple tip to get my Fast Track Pro work in Ubuntu 8.04:

Use System->Preferences->Sound to configure USB Audio as default for all playback.

open a console and type
$ asoundconf list

choose USB card from list, in my case Pro so I type
$ asoundconf set-default-card Pro

reboot, done!

---

### Post by rosegarden78 on 2008-08-11
II. Ubuntu Studio and Linux - install on 3rd partition last

A. Sources - LiveCD or alternate CD for modern distros

	1.  Use download managers or torrents to get large files
	2.  Always burn OS discs at slowest possible speed
	3.  Glossary
		a. "/" is the root directory for Linux partition #3
		b. ext2 or ext3 are the filesystems for Linux
		c. swap is used on the tiny 4th partition
		d. 1st and 2nd partitions are NTFS
		e. "/home" is reserved for 5th partition as ext2
	4.  Follow simple installation instructions for LiveCD or Alternate CD
5. plugin Ethernet cable to configure DHCP
	6.  Okay to skip automatic dhcp

B.  UbuntuStudio - First run

	1.  Install NVIDIA graphics card driver for Linux
	2.  Add gnome-network-manager for wireless internet
	3.  Add ubuntu-restricted-modules
	4.  Update packages

C. Ubuntu Studio setup 

	1.  Streaming audio - See [**_PulseAudio wiki_**]("https://wiki.ubuntu.com/PulseAudio")
		a.  In PulseAudio Volume Control click the last tab and enable virtual simultaneous outputs.
		b.  [**_Tweak PulseAudio_**]("http://ubuntuforums.org/showthread.php?t=789578") to remove clicks
		c.  Run '*padsp zynaddsubfx*' to test clicks
	2. [**_M-Audio Fast Track_**]("http://ubuntuforums.org/archive/index.php/t-447744.html") - class-compliant
	a.  Choose device in qjackctl setup
	b.  Select device #1 in System/Sound
	3.  Compile ALSA from source
		a. Require build-essential
		b. Require RT kernel headers
		c. See links for details
	4.  Streaming or stereo mix recording is enabled by 		calling a program with *padsp* command prefix.
		a.  First launch your audio program with padsp
		b.  Launch Audacity with '*padsp audacity*'
	5.  PulseAudio cannot co-exist with qjackctl, so you 		can't record streams and instruments at once.	
	6.  JACK displays *PortAudio* when Audacity is 		recording with JACK drivers so:
		a.  Record then pause with Audacity
		b.  Go to JACK dialog box - click connect
		c.  Patch your audio app into PortAudio
	
**7.   To get audio feedback from mic:**
		a.  Open qjackctl
		b.  Click setup
		c.  Select USB Audio #1 for all interfaces
		d.  128 buffers / 2-4 periods
		e.  Start JACK server
		f.  Connect 'sytstem in' to 'system out'
		g.  Push Fast-Track A/B switch in B setting
		h.  Connect monitors to 3/4 and headphones
                i.  Launch karaoke program

**8. To get simultaneous playback on computer and USB speakers**
a.  Install PulseAudio as instructed
b.  Select simultaneous outputs/inputs in PulseAudio Volume Control
c.  Launch VLC or your favorite audio p:layer in padsp mode.
d.  The sound output should come from both sources and record too.
[B]
9. UPDATE: Get system wide stereo mix with instruments[/B]
a. Go to System - Preferences - Sound
b. Under audio devices select "Usb Audio" for all playback
c. Select "USB Audio #1" for recording
d. Reboot
e. Turn A/B mixer knob to middle position
f. Plug in a microphone
g. Plug in computer speakers to 1/2 out
i. See [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
j. Use the PulseAudio Jack plugins
k. Patch System and PulseAudio into PortAudio when using Audacity.

10. Edit PulseAudio daemon.conf 
a. [http://www.pulseaudio.org/attachment/ticket/326/daemon.conf](http://www.pulseaudio.org/attachment/ticket/326/daemon.conf)
b. Run "killall pulseaudio" from a terminal
c. Run "pulseaudio -D" to restart

Note: Using 48000 Hz causes tuning problems 
My daemon.conf settings:

high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 1
default-fragments = 10
default-fragment-size-msec = 1
resample-method = speex-float-3
default-sample-format = s32le
default-sample-rate = 44100			
default-sample-channels = 2
no-cpu-limit = yes
;disable-remixing = yes

**UPDATE: August 14, 2008 - Flash 10 with PulseAudio**
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by nadalex on 2008-11-29
I'm using the Fast Track Pro and it detected automatically. I'm using it with Ardour/Jack... (It works in Audacity, but Audacty crash often when I run it through a USB device.) 

Still, I can't get 4-outs through the RCAs (which is the appeal of the Fast Track Pro, no?) I'm sure there's something I need to do in Jack but tutorials aren't helping me to figure it out.

Has anyone been able to get their Fast Track to run 4-outs through their Fast Track?

---

### Post by JDPP on 2009-07-04
> **nadalex said:**
> I'm using the Fast Track Pro and it detected automatically. I'm using it with Ardour/Jack... (It works in Audacity, but Audacty crash often when I run it through a USB device.) 

Still, I can't get 4-outs through the RCAs (which is the appeal of the Fast Track Pro, no?) I'm sure there's something I need to do in Jack but tutorials aren't helping me to figure it out.

Has anyone been able to get their Fast Track to run 4-outs through their Fast Track?

I tried to read and understand this thread, but in the end, looks like I have the same issue as the last post.  I tried the M-audio Fast track Pro, it is recognised, but in the connections Jack only shows 2 outs (1 stereo), instead of 4.

I tried to mannualy put 4 outputs channel in the setup, but then it does'nt start.

Is there a way to see the 4 outs in JAck ?

(using jackdmp .71 jaunty package)

---

### Post by raboofje on 2009-09-12
See also: [http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro)

According to this page, there is a patch available that enables a couple of extra options, including 0x02 'enable digital output (channels 3,4)'.

I took a quick look at the official kernel tree, unfortunately it looks like this patch hasn't been applied upstream yet.

---

### Post by japboy on 2009-10-05
does anyone know when this patch will b merged in the upstream...?

the original patch source seems that was posted approximately 2 years ago. such a long time ago...

> **raboofje said:**
> See also: [http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro](http://alsa.opensrc.org/index.php/M-Audio_FastTrack_Pro)

According to this page, there is a patch available that enables a couple of extra options, including 0x02 'enable digital output (channels 3,4)'.

I took a quick look at the official kernel tree, unfortunately it looks like this patch hasn't been applied upstream yet.

---

### Post by rosegarden78 on 2010-08-04
I think Joe has the answer.  I'm using the Ubuntu Studio 64-bit Lucid version.  The new kernel is compiling. I can't wait to have 24-bit audio support.  If you can't get Ardour and Jack working, try disabling D-BUS support in Jack options.  Then, Jack was able to seize control of the USB audio...just check Messages to be sure it did.

[http://www.joegiampaoli.com/blog/?p=462](http://www.joegiampaoli.com/blog/?p=462)

---

### Post by joegiampaoli on 2011-09-23
Just for those still looking for support on the FTP on linux I updated my blog, no longer for ubuntu, I explain why there...

[http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html](http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html)

---

