---
title: "Sound through hdmi with nvidia GTX460"
date: 2010-08-24
forum: Hardware
---

### Post by niiklas on 2010-08-24
Im trying to get my nvidia gtx 460 to send the audio through hdmi. Got it working on my w7 install but not with ubuntu.

I tried to install & compile the latest alsa driver without success, this is how my alsa mixer looks like:
[IMG]http://lasias.com/download/nhogblom/Skrmbild-GNOME_ALSA-mixer.png[/IMG]

Aplay -l shows this:
> niklas@niklas-desktop:~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: DX [Xonar DX], enhet 0: Multichannel [Multichannel]
  Underordnade enheter: 0/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: DX [Xonar DX], enhet 1: Digital [Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: Intel [HDA Intel], enhet 0: ALC889A Analog [ALC889A Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: Intel [HDA Intel], enhet 1: ALC889A Digital [ALC889A Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
niklas@niklas-desktop:~$


Anyone that has sound through hdmi with a discrete nvidia graphics card? How did you do it? :)

---

### Post by Groucho Marxist on 2010-08-24
I typed ```
alsamixer
``` in Terminal and scrolled over to "S/PDIF" and pressed m. This un-muted my HDMI audio and caused jolly good times to commence. I hope this solves your problem :)

---

### Post by niiklas on 2010-08-24
> **Groucho Marxist said:**
> I typed ```
alsamixer
``` in Terminal and scrolled over to "S/PDIF" and pressed m. This un-muted my HDMI audio and caused jolly good times to commence. I hope this solves your problem :)

Couldnt find any S/PDIF in my nvidia tab, but unmuted on the other soundcards without any luck...

[IMG]http://lasias.com/download/nhogblom/Skrmbild-niklasniklas-desktop_.png[/IMG]
No controls for the nvidia soundcard~

---

### Post by niiklas on 2010-08-25
anyone?

---

### Post by Serdar on 2010-08-26
I do have exactly the same problem. 

I do get the sound from HDMI with Windows 7 64 but no sound with Ubuntu 10.04 64.
 I tried alsamixer on Terminal and S/PDIF outputs are un-muted. But still no sound. Do I have to change anything in BIOS settings. Such as; HDMI settings from HDMI output to S/PDIF? If I do, do I have to change any cable config on motherboard?

My System;
Ubuntu 10.04 64
Asus P5Q-EM Motherboard
Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz
8002 MB Memory
Nvidia GTX 460

---

### Post by Maletor on 2010-08-28
Same error as you guys. I should be able to select HDMI as a source from System=>Preferences=>Sound

Maybe this will be fixed in later drivers? Is this a problem with Ubuntu or nvidia? 

I thought *maybe* BIOS but I'm pretty sure this is a software problem.

---

### Post by dmaxwell81 on 2010-09-09
Any one have any luck? I have the exact same card, with the exact same problem.  I've updated Alsamixer and get the same 'this device has no controls'.

Its frustrating...I just built my new machine and now I might actually have to revert to Windows :(

---

### Post by Tavis on 2010-09-10
> **Groucho Marxist said:**
> I typed ```
alsamixer
``` in Terminal and scrolled over to "S/PDIF" and pressed m. This un-muted my HDMI audio and caused jolly good times to commence. I hope this solves your problem :)

Groucho, could you tell us what package versions you have installed (alsa-base, alsa-utils, linux-headers-alsa-driver, linux-alsa-driver-modules)?  Did you compile anything yourself?  Clearly you're able to access a bunch of controls that the rest of us can't find using the same hardware, which makes me think that there's a package or two the rest of us are missing.

Thanks,
Tavis

---

### Post by gcbzzzz on 2010-09-10
are all nvidia GTX 460 the same? there's like 20 different boards for those.

---

### Post by dmaxwell81 on 2010-09-13
> **gcbzzzz said:**
> are all nvidia GTX 460 the same? there's like 20 different boards for those.
Mine is a EVGA, but I have seen several threads with the exact same problem for the exact same card.  It seems to stretch across all brands.  I agree with the earlier poster that it may be a software issue, as true video card only HDMI sound is still pretty young. 

I would also like to know Groucho's setup/card brand.

---

### Post by Tavis on 2010-09-13
By the way, there seem to be some kernel issues involved; it appears that a custom kernel is required.  See this thread on the Nvidia linux driver forums:

[http://www.nvnews.net/vbulletin/showthread.php?t=154755&highlight=hdmi+audio]("http://www.nvnews.net/vbulletin/showthread.php?t=154755&highlight=hdmi+audio")

Also, this Ubuntu bug report and the discussion:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/611810]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/611810")

It's not clear to me which compilations of ALSA or kernel backports (if any) do contain the right patches.

---

### Post by Maletor on 2010-09-15
Ellis,
 
The bug tracker in question is internal to NVIDIA, so I&#8217;m afraid I can&#8217;t give you a link.
 
However, once we&#8217;ve determined what the problem is, we will certainly email you and let you know.
 
Thanks.
 
From: Ellis
Sent: Thursday, September 02, 2010 12:02 PM
To: Stephen Warren
Cc: linux-bugs
Subject: Re: GTX 460 HDMI Sound
 
Thank you, can you link me to the bug or otherwise keep me updated?
 
On Sep 2, 2010, at 1:02 PM, Stephen Warren wrote:


Ellis,
 
I don&#8217;t currently have the hardware set up to repro your current issue. I&#8217;ve filed a bug and will work on getting somebody to repro this.
 
From: Ellis 
Sent: Wednesday, September 01, 2010 8:12 PM
To: Stephen Warren
Cc: Linux-Devel
Subject: Re: GTX 460 HDMI Sound
 
Do you think you could tell me how you have it set up to work?
 
On Sep 1, 2010, at 11:55 AM, Stephen Warren wrote:



Ellis,
 
Can you provide details on how you&#8217;re attempting to play DTS streams over HDMI; which application you&#8217;re using, what version of the application, the complete command-line you&#8217;re using, etc. Also, it&#8217;d be useful if you could give us  a sample of the audio so we can try to reproduce the issue in exactly the same way you are. For upload details, see [http://www.nvnews.net/vbulletin/showthread.php?t=123819](http://www.nvnews.net/vbulletin/showthread.php?t=123819).
 
Thanks.
 
From: Ellis
Sent: Tuesday, August 31, 2010 2:38 PM
To: Stephen Warren
Subject: Re: GTX 460 HDMI Sound
 
Stephen,
 
Setting /etc/modprobe.d/alsa-base.conf to have
options snd-hda-intel probe_mask=0x102 and then running sudo alsa force-reload works for analog streams.
 
However, for any digital stream (DTS or DTS HD) it does not work.
 
Ellis
 
On Tue, Aug 31, 2010 at 1:31 PM, Ellis wrote:
Stephen, 
I think Ubuntu distros keep alsa configuration in /etc/modprobe.d/alsa-base.conf.
I will try adding options snd-hda-intel probe_mask=0x101/2/4/8 to that file then rebuilding the initrd and restarting later on today.
 
When do you think these patches will show up in a release or distro, just out of curiosity?
 
I have no idea if this information might be useful to you but here is the output from dmesg | grep -i alsa 
[http://gist.github.com/559390](http://gist.github.com/559390)
 
Ellis
 
On Aug 31, 2010, at 12:25 PM, Stephen Warren wrote:




Ellis,
 
I remembered one other thing that needs updating:
 
NVIDIA GPUs support multiple audio codecs, since multiple video streams can be active at once. The ALSA driver correctly supports the 4 codecs on your card. However, the ALSA library currently has a bug that exposes only the first of these codecs to applications. This has been fixed in the latest ALSA library code, but not yet made it into any official release or distro. Pulseaudio has a similar issue, which has not been fixed as far as I know.
 
The easiest way to work around this is to use a &#8220;probe_mask&#8221;.
 
Edit /etc/modprobe.d/sound.conf, edit  (or add) a line for snd-hda-intel. Try each of the following:
 
probe_mask=0x101
probe_mask=0x102
probe_mask=0x104
probe_mask=0x108
 
a complete line in sound.conf might look like:
 
options snd-hda-intel probe_mask=0x101
 
After each edit, you will probably need to rebuild your initrd/ramdisk to incorporate this change, and then reboot.
 
Note that the probe_mask value you need depends on which video connector you&#8217;re using on your graphics board, so if you switch to a different connector, you&#8217;ll need to search for a different probe_mask value.
 
 
From: Ellis
Sent: Monday, August 30, 2010 10:13 PM
To: Stephen Warren
Subject: Re: GTX 460 HDMI Sound
 
Just got home and tried this out.
 
It looks like the drivers from the PPA you linked me to works at first glance.
>> cat /proc/asound/cards shows
0 [NVidia ]: HDA_Intel - HDA NVidia
                           HDA NVidia at 0xfbfc000 irq 10
 
>> cat /proc/asound/version
ALSA 1.0.23
for kernel 2.6.32-24
 
Do I need to upgrade my kernel as well?
 
HDMI is selected from System=>Preferences=>Sound as the output and I disabled HD Audio in my BIOS so that I could have the nvidia card as the only device.
 
When I play a song, alsamixer shows S/PDIF 1 OO (as opposed to MM -- mute) but when not playing it reverts to MM. There is no red light from my integrated VIA soundcard.
 
Does the PPA not include the latest patch you mentioned?
 
On Aug 30, 2010, at 10:42 AM, Stephen Warren wrote:
 

Ellis wrote:

ALSA can find the NVIDIA card but I can't choose it as a hardware interface
and it doesn't have any  controls in alsamixer. I have tried disabling
S/PDIF.
 
Is this a NVIDIA or ALSA problem? How can I listen to audio through HDMI
with my GTX 460?

Ellis,

The ALSA driver needs to be updated to support newer NVIDIA GPUs.

If you're up to building your own drivers, you can download an ALSA driver
snapshot from:

[http://www.kernel.org/pub/linux/kernel/people/tiwai/snapshot/](http://www.kernel.org/pub/linux/kernel/people/tiwai/snapshot/)

Otherwise, you'll have to wait until your distribution includes the updated
code that is required. For Ubuntu, please see the following bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/611810](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/611810)

In particular, comment #3 includes a link that shows how to install the very
latest ALSA drivers for Ubuntu. I believe these should solve your problem.


-----------------------------------------------------------------------------------
This email message is for the sole use of the intended recipient(s) and may contain
confidential information.  Any unauthorized review, use, disclosure or distribution
is prohibited.  If you are not the intended recipient, please contact the sender by
reply email and destroy all copies of the original message.
-----------------------------------------------------------------------------------

---

### Post by Maletor on 2010-09-15
So basically what I did to get it to work was update the kernel to most recent. Update ALSA to 23 and add that line in sound.conf with probe_mask. Who knows why we are selecting those bits.

So with that configuration it worked but not for digital streams. Apparently, NVIDIA doesn't have the equipment to reproduce the error - whatever that means.

---

### Post by Tavis on 2010-09-15
> **Maletor said:**
> So basically what I did to get it to work was update the kernel to most recent. Update ALSA to 23 and add that line in sound.conf with probe_mask. Who knows why we are selecting those bits.

So with that configuration it worked but not for digital streams. Apparently, NVIDIA doesn't have the equipment to reproduce the error - whatever that means.


Did you just use the version 23 from the PPA?  No patches required?  Also, when you say the most recent kernel, do you just mean the 2.6.32-23 Ubuntu kernel, or did you have to build your own?

Also, what do you mean by "analog streams"?  What does work?

Thanks,
Tavis

---

### Post by Maletor on 2010-09-15
No. I just decided to upgrade to Maverick because it has the 2.6.35 kernel and the 1.0.23 versions of ALSA. If you can get that to go in Lucid then distro should be inconsequential.

I added [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

sudo -i
apt-add-repository ppa:ubuntu-audio-dev/ppa
apt-get install linux-alsa-driver-modules-2.6.35
vim /etc/modprobe.d/sound.conf
options snd-hda-intel probe_mask=0x102
:wq
alsa force-reload
alsamixer

What I mean by analog streams are those that are not PCM. Digital streams are passed through the GTX460 which is one of it's major selling points if you ask me. Some examples are DTS, AC3, DTSHD MA. 

Optical can play PCM and analog however, it cannot play lossless digital streams like DTS HD.

---

### Post by marcuskj on 2010-10-26
Hi!
I have the exact same problem. I have followed the instructions as best i can, and I have updated to latest kernel, along with latest alsa drivers. I am currently trying to set the probe mask, but there is one thing I am unable to figure out (just starting out with linux), and that is how to rebuild the ramdisk. Is this a complicated task? I tried to google it, but mostly i get hits on recompiling the kernel (admittedly I can't claim to know the difference...).

Everyting else seems to be in order, I find the soundcard unmuted in the alsamixer, as well as in the sound properties, but when I test the sound there is nothing. Coming from years and years in a Windows environment, I find it all very daunting, but I am slowly making progress :)

If there are any simple commands i can run in terminal to rebuild the ramdisk, as suggested in post#12 I would love to learn them.

Regards,
Marcus

---

### Post by Holmyara on 2010-11-12
So what the final solution? I'm confused with multiple threads on  forums. I have Gainward NVidia GTX460 and I can't setup audio through HDMI as many others. My kernel version is 2.6.35-22-generic and alsa version is 1.0.23. I have the same situation as described in the beggining of this thread.
Any chances to get updates for OS through update manager to get it working? 
What the correct steps to setup audio through HDMI for my configuration?

---

### Post by Maletor on 2010-11-12
The solution is to upgrade the kernel by adding the maverick proposed repositories or by using the kernel mainline builds. (google).Then create a file called /etc/modules/sound.conf and add

options snd-hda-intel probe_mask=0x102

Then do reboot or sudo alsa force reload
It should be selected in system preferences sound. 
I have yet to get DTS HD working though so let me know if you figure that one out.

---

### Post by lidex on 2010-11-12
Your best source for info is the nvnews forums and xbmc forums. This thread should get you started:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
(Different hardware but same process)

---

### Post by Holmyara on 2010-11-13
I could get sound through HDMI on my TV:
1) I've updated my Ubuntu using Update Manager with option 'maverick-proposed'. So kernel is 2.6.35-23-generic.
2) Then I've created /etc/modules/sound.conf as you proposed in your post
3) And last one I've uninstalled pulse audio lib in my installation to use alsa mixer anywhere.

So finally I have TV display through HDMI including sound through HDMI and I have Skype through analog onboard sound device.
Thank you for your solution.
P.S.: The last remaining unresolved problem is display cut (cropped) (top and bottom of screen) on TV through HDMI. I have no such problem on Win7.

---

### Post by Maletor on 2010-11-13
Run nvidia-settings & from terminal. 

Change overscan compensation. 
Different receivers and tvs handle the input differntly.

---

### Post by Holmyara on 2010-11-14
Fortunately I found 'overscan' option in my Panasonic TV. NVidia driver has no option to drive overscan option. Thank you!

---

