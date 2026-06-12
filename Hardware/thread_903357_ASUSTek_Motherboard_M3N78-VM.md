---
title: "ASUSTek Motherboard M3N78-VM"
date: 2008-08-28
forum: Hardware
---

### Post by dburnett77 on 2008-08-28
Anyone have experience with Ubuntu/Linux on this motherboard:

[http://www.asus.com/products.aspx?l1=3&l2=149&l3=643&l4=0&model=2268&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=149&l3=643&l4=0&model=2268&modelmenu=1)

I would like to know how effective the Asus Express Gate is (Linux boot for simple tasks in 5 seconds) and if this board has any issues with the latest kernel.
Also, the built-in video is Nvidia 8200, and I was curious if nvidia-glx supported this chipset.

Thanks.

P.S.  Any offers of opinion on getting the AMD Athlon X2 6000+ as opposed to saving cash and going with a 5000+ for half the price.  Is the performance increase really worth it?

Thanks again.

---

### Post by phidia on 2008-08-28
That's a interesting motherboard (with hybrid tech) there are some reviews, not linux specific, at newegg [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318&Tpk=M3N78-VM"). 
I didn't read all the reviews but I would want to know more about the bios and how that will effect performance as well as linux compatibilty.
I think it's sort of new to have a lot of feed back from the linux community.
The onboard nvidia gpu should be recognized 8 & 9 series cards work-sometimes they need a little extra work to get the nvidia driver correctly enabled.

---

### Post by Onyxblack on 2008-08-28
Not to sure on your board - but the m3n-ht (which is kinda like yours) is working fine - I have actually disabled my express gate - its not all that its cracked up to be. I didn't have any problems with the board in installation

---

### Post by dburnett77 on 2008-08-28
I've been searching the Inet, and hear problems with the ethernet, and also audio a couple of times.  Ubuntu 8.04 doesn't seem to correctly identify them for these users.  One guy can't even get Ubuntu to install.  One other complained of 'tearing' video with the 8200 graphics.

But, for the most part (about 4 others), they indicate no problem.
I guess I'll just have to try it myself to see.

---

### Post by jasonfiset on 2008-08-29
After spending more than a few hours working through the issues.  It seems that the magic in installing Ubuntu 8.04 is using the "pci=nomsi" option to the kernel.  Some users have reported that you have to change your SATA configuration to ACHI but I've left mine on SATA mode (not sure if RAID mode will work) and pass the kernel option pci=nomsi and the SATA drives are found and the networking works no problem.  I'm not entirely sure what nomsi does but it appears that other distros are having similar issues with msi turned on.

I'm using M3N78-VM motherboard but I'm sure that any M3N78 or boards based on the nForce 780 chipset will work with this setting.  Without that option turned on, the networking didn't appear to work right and I got a "No disks found" error when trying to install Ubuntu.

I picked up a 5000+ X2 processor myself today simply to save cost.  I would research the 6000+ CPU a bit more and make sure you don't run into compatibility problems.  I saw one odd incompatibility regarding the Video performance with the 6000+.

-Jason

---

### Post by Onyxblack on 2008-08-29
I had a whole bunch of problems with the sata drive - i gave up and pluged in a 200gig ide to install it on hah.... it detects the sata drive just fine now but meh...

---

### Post by dburnett77 on 2008-08-29
> **jasonfiset said:**
> After spending more than a few hours working through the issues.  It seems that the magic in installing Ubuntu 8.04 is using the "pci=nomsi" option to the kernel.  Some users have reported that you have to change your SATA configuration to ACHI but I've left mine on SATA mode (not sure if RAID mode will work) and pass the kernel option pci=nomsi and the SATA drives are found and the networking works no problem.  I'm not entirely sure what nomsi does but it appears that other distros are having similar issues with msi turned on.

I'm using M3N78-VM motherboard but I'm sure that any M3N78 or boards based on the nForce 780 chipset will work with this setting.  Without that option turned on, the networking didn't appear to work right and I got a "No disks found" error when trying to install Ubuntu.

I picked up a 5000+ X2 processor myself today simply to save cost.  I would research the 6000+ CPU a bit more and make sure you don't run into compatibility problems.  I saw one odd incompatibility regarding the Video performance with the 6000+.

-Jason

I appreciate the info.  I got curious as to what msi was, and found:

[http://en.wikipedia.org/wiki/Message_Signaled_Interrupts](http://en.wikipedia.org/wiki/Message_Signaled_Interrupts)

[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)
"Common problems switching to AHCI under Linux

    * AHCI controller does not work on AMD/ATI RS400-200 and RS480 HBA when MSI is enabled due to a hardware error. In order for AHCI to work users must provide the "pci=nomsi" kernel boot parameter. With MSI disabled in this way, the PCIe bus can only act as a faster PCI bus with hotplug capabilities. This is also true of the Nvidia nForce 560 chipset.[citation needed]
    * AHCI controller on AMD/ATI SB600 HBA can't do 64-bit DMA transfers. 64-bit addressing is optional in AHCI 1.1 and the chip claims it can do them, but in reality it can't, so it is disabled. After that it will be forced to do 32-bit DMA transfers. Thus DMA transfers will occur in the lower 4 GiB region of the memory, and bounce buffers must be used sometimes if there is more than 4 GiB of RAM.[5]"

Hopefully, future versions of the kernel will adapt to the new chip set.  Guess it'll depend on their popularity, or someone's willingness to fix the issue.

Thanks again for the info.

---

### Post by PeonDevelopments on 2008-09-24
I own this board and am currently running Kubuntu 8.04.
After installing envy and selecting the nVidia drivers, everything installed and worked perfectly regarding video.

My issue is that the onboard sound occassionally gives random bouts of static when playing files. (especially anything lower than 48000 hz)
I may have that solved soon...

---

### Post by Piraga on 2008-09-26
> **PeonDevelopments said:**
> I own this board and am currently running Kubuntu 8.04.
After installing envy and selecting the nVidia drivers, everything installed and worked perfectly regarding video.

My issue is that the onboard sound occassionally gives random bouts of static when playing files. (especially anything lower than 48000 hz)
I may have that solved soon...

When you solve the static issue, let us know. I have this board and I've been running it for about a month now but the onboard sound has been pissing me off to no end, and nothing I can think of will fix it.

Thats really the only issue I can think of with this board and its a pretty large flaw. :/

---

### Post by mnorton on 2008-11-03
I'm thinking of buying this one myself and want to dual boot. Has anyone tried this with 8.10?

---

### Post by spoc on 2008-11-10
OS: Ubuntu 8.10 64 (today updated from 8.04)
MB: Asus M3N78-CM - X2 6000+

The onboard hd audio doesn't work. I had to use a pci audio card.
Next issue is the 8200 graphics chip.
- nv-driver works
- nvidia 169 doesn't work
- nvidia 173 works best
- nvidia 177 works very slow

Now the 173 is installed, because it got less problems. It doesn't work with desktop effects. See: [http://ge.ubuntuforums.com/showthread.php?t=959344&highlight=nvidia+8200]("http://ge.ubuntuforums.com/showthread.php?t=959344&highlight=nvidia+8200")

the 8200 does well for me in games. It runs Spring at 1024x768 with some shader (not too many) at around 40fps. See: [http://spring.clan-sy.com/]("http://spring.clan-sy.com/")
I thought to upgrade to 9xxx pcie, but there is no need for me now.

My system got 2GB of ram. Thats NOT enough. The 8200 uses 512MB for graphics. With just Firefox open, 55% of mem is used + another 33% as cache. Running some other programs and it becomes slow.

Also I am using AHCI without any kerneloption. Ubuntu 8.04 didn't find the /dev/sda with SATA. But with AHCI being a open standard it's even better.

```
sudo hdparm -tT /dev/sda
[sudo] password for spoc: 

/dev/sda:
 Timing cached reads:   1190 MB in  2.00 seconds = 594.94 MB/sec
 Timing buffered disk reads:  286 MB in  3.00 seconds =  95.26 MB/sec

```

Didn't test the express gate, it looks like you have to setup it in Windows.
All in all I am satisfied to get this much computer with a free/open os.
Nvidia could do better though.
Probably the soundproblem is just a matter of time until drivers are available.

---

### Post by coolercooler on 2008-11-11
Can you get audio through hdmi with this board?  Or does it need extra set of speakers for sound to go with picture?

---

### Post by spoc on 2008-11-12
Can't test this. I've got no hdmi device. Doesn't look so though. Most probably you will have to connect via phone plugs (front/rear/center...8-channel/4 plugs). But as I said, audio doesn't work for me.

---

### Post by coolercooler on 2008-11-12
Thanks for the reply, I can't even get it to work with just the hdmi, let alone sound.  And thats under windows Xp.

Does it work if you just install all the drivers or is there a special way to make it work?

It works on bios startup, but when windows load it just shows no sync.  And even then only one display shows up even though it's calming to have mulitiple displays, I can only have monitor or tv but not both.

I think this board is going back, very disappointing upon closer look.

---

### Post by spongebobp2m on 2008-12-09
Hi,..

I have this MoBo and I can't get analog audio.
I'm using Ubuntu 8.10 for AMD64.

Has anyone got the same problem?

---

### Post by DJ Exprice on 2008-12-30
I would like to know of a way to fix the audio on this board for my Ubuntu system; I'll be on the lookout for any fixes.

Mobo: Asus M3N78-VM
CPU: AMD Athlon 64 X2 5000+
Memory: 1.8GiB DDR2

Video (Geforce 8200M NVIDIA 173 drivers) and audio (VT1708B - ALSA) are onboard; I've been resorting to a Griffin iMic instead.

Thanks!

-e

---

### Post by nandoc on 2009-01-07
Hola,
Some notes on this board:
Audio: Works great using my Creative 5.1 analogue speakers, but I had to make sure to double click the speaker icon on the top panel and moving the bar up to increase volume and under preferences activate the center and surround speakers.
Sata: Using standard SATA, no Raid nor AHCI, it works without problems.
ExpressGate: It works. I have dual boot (vista) and after installing the provided CD under Windongs (uses some files in (ntfs/Fat) partition.
Video: On of the advantages on this MB, is that it comes with the 8200 video card and a PCIe slot to place a second video card (nvidia 9800GT in my case) I have some issues to solve: 1) Using the main board video card (8200)ONLY, works but after installing the private nvidia drivers it just doesn't work! or is it related to the PCIe video card (9600 GT in my case).
2) The only way to get the PCIe to work is under BIOS making the PCIe card as the primary Graphics adapter but the second screen on the 8200 card doesn't work. Maybe is due to what is stated ahead!!!)
Hope this help,
Fernando
Oh, I updated the BIOS to the latest

---

### Post by jdeslip on 2009-02-13
I also have this board.  I haven't had any audio issues (but I think intrepid cleared this up at some point before I bought the board).

However, I do have some issues that all seem to be related to the 8200 video card:

1.  I am using it with mythbuntu 8.10 - hdmi works to my vizio 1280 x 720 tv fine with the nvidia 173 driver but not with anything greater.  With drivers higher than 173, the picture doesn't quite fit in the screen and the colors are completely wonky.  VGA works fine with 173 and 180.29  (ones in between have slow 2D).  

2.  I can't get the nvidia driver to load at all unless I add the vmalloc=256MB to my kernel boot line.  

3.  I am using the patched version 0.21 mythtv vesion with vdpau.  When VDPAU plays a movie, it is awesome.  But, it often "fails to initialize" giving errors about insufficent resources to initialize vdpau buffers.

Does anyone else have these problems?

---

### Post by barwin on 2009-03-25
I also am using this board with mythbuntu 8.10.

System specs:
M3N78-VM
Athlon 64 X2 5050e @ 2.6Ghz
2x2GB G-skill RAM

Currently I'm using HDMI for video at 1920x1080 on a Sceptre 42" 1080p LCD television.  Originally I was hooked up via VGA (since the TV has a VGA input) but I just switched to HDMI last night and it worked without my having to change any settings at all.  I did reboot though.

As for audio, I'm currently using onboard audio (but would like to eventually use audio over HDMI).  To get the onboard audio to work, you have to rmmod and modprobe the sound driver at the end of the boot up sequence.  To accomplish this, add the following two lines to /etc/rc.local per this thread:  [http://ubuntuforums.org/showthread.php?t=881363&page=2](http://ubuntuforums.org/showthread.php?t=881363&page=2)
```

rmmod snd_hda_intel
modprobe snd_hda_intel

```
See that thread for more info..

I was running nvidia's 177 driver but I upgraded to 180 because I intend to take advantage of VDPAU and as I understand it, 180 is required for that.  You can easily update to 180 with ```
sudo apt-get install nvidia-glx-180
``` I'm *hoping* that version includes the necessary VDPAU functionality but haven't confirmed yet.

Anyway, with both versions (177 and 180) of the nvidia driver, I had no problems whatsoever and I did not need to add vmalloc=256 to the kernel options as some have reported. But I did play with the BIOS options and allocated 512MB to video there..


My Questions:

[LIST=1]
[*]My last big hurdle with my mythtv system before I can really consider it "done" is to get sound over HDMI working.  Has anybody written a HOWTO on getting HDMI audio to work with this board, M3N78-VM, or boards like it at least?  I've managed to find a few tips here and there scattered about, but nothing recent / cohesive / definitive as of yet. Maybe I'm looking in the wrong places... Or perhaps it's easier than I think and I'm just missing something?


[*]I'm currently using mythbuntu's weekly build repository to get 0.21-fixes. Does anyone know if there's a way to get VDPAU support to work without compiling mythtv from source?

I really wish we could just use XvMC but that's not supported in the geforce 8000's and higher.
[/LIST]

Thanks!
-Ben

---

### Post by jdeslip on 2009-03-25
jyavenard has made patched 0.21-fixes mythbuntu packages with vdpau.  It works great.  [http://www.mythtv.org/wiki/VDPAU#MythTV_0.21-fixes_and_Ubuntu_repository](http://www.mythtv.org/wiki/VDPAU#MythTV_0.21-fixes_and_Ubuntu_repository)

You should disable the weekly builds repo and enable his instead.

I have been using it with this board with great success.  CPU usage is down below 5% when playing HD video!

---

### Post by barwin on 2009-03-26
wow!  You were right about VDPAU - CPU usage dropped while playing 1080p content from 100% to under 5%!

Thanks a bunch for the tip about the patched 0.21-fixes repo. Much nicer than having to compile from source :)  

The only trick (for anyone else switching from the mythbuntu 0.21-fixes repo to the VDPAU one) is I had to manually *remove* all the mythtv packages and then re-install because the versions in the VDPAU repo are a bit older.  It kept all my settings/config though, so it wasn't a big deal.

@jdeslip - I'm curious about your playback profile, did you find any good settings for deinterlacing?  I tried a few options with VDPAU + various deinterlacing options but I get choppy playback (still low CPU usage though, interestingly enough).

I ended up setting up a playback profile where VDPAU only kicks in for 1080p content with none/none for deinterlacers, and then just regular ol' ffmpeg+xvlib for 720p and lower w/some modest deinterlacing settings.

Cheers,
-Ben

> **jdeslip said:**
> jyavenard has made patched 0.21-fixes mythbuntu packages with vdpau.  It works great.  [http://www.mythtv.org/wiki/VDPAU#MythTV_0.21-fixes_and_Ubuntu_repository](http://www.mythtv.org/wiki/VDPAU#MythTV_0.21-fixes_and_Ubuntu_repository)

You should disable the weekly builds repo and enable his instead.

I have been using it with this board with great success.  CPU usage is down below 5% when playing HD video!

---

### Post by jdeslip on 2009-03-26
I have been using vdpau for basically all my video playback.  I can't quite remember what deinterlacer I am using (will check when get back home), but it is one of the less intensive ones.  The advanced deinterlacers caused problems for me as well but my tv is only 720p.  I have heard others say vdpau + deinterlacing can be slow for 1080p.

---

### Post by barwin on 2009-03-28
I got HDMI audio to work with the M3N78-VM and MythBuntu 8.10!

In theory this should work for S/PDIF (SPDIF) as well.. but I don't have a s/pdif cable so I'm unable to confirm.

So, with mythbuntu 8.10, the included version of alsa is 1.0.17.  Evidently you need the latest version which is currently 1.0.19.

There is a very easy to use script that someone wrote, available here: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810) - that will upgrade you to the latest version (it simply overwrites the installed version, but it's 100% reversible if you decide to uninstall and go back to the official .deb pkgs.  There are also some other handy utilities troubleshoot sound issues. See that thread for more info.

I ran it, rebooted, and aplay -l FINALLY began showing a real HDMI output. Here's my output for 'aplay -l':
```

myth:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Card 0, Device 3 is the HDMI. (It's important to note that it's device 3 for the .asoundrc config later on).  In the BIOS, I have the audio codec set to both internal+external.  If I only select internal, then the first device disappears and I'm left with only HDMI.  BTW, if you're not running BIOS version 0907, you should upgrade.

After upgrading alsa and confirming that your HDMI device shows up in 'aplay -l', you MUST run 'alsamixer' in a terminal and unmute the iec958 channel. That is the digital channel and it WILL be muted by default. Don't waste hours futzing with other settings until you've confirmed that channel is unmuted :)  (Future Alsa upgrades will likely re-mute the channel as well)

After that, confirm that you can hear sound over the digital channel with the following command:
```

speaker-test -twav -c6 -Dplug:hdmi 

```

If you can hear sound, you're ready to set up your alsa config so that MythTV will happily use HDMI.  For that, use the alsa config file on MythTV's site: [http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly](http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly)

(side note: Even though the instructions are written for S/PDIF, for this mobo at least, the terms "S/PDIF" and "HDMI" are interchangeable when it comes to the audio config)

The two changes you must make to the .asoundrc file they give you are as follows:

1. in the pcm.!default section near the top, make 'dmix-digital' the default device
```

pcm.!default {
  type plug
## Uncomment the following to use (unmixed) "analog" by default
#  slave.pcm "analog-hw"
## Uncomment the following to use "mixed-analog" by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
#  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
  slave.pcm "dmix-digital"
}

```
(You should only have ONE slave.pcm line that is uncommented)


2. in the pcm.digital-hw section, you must have a 'device' line that matches the output from aplay -l.  For me (and likely anyone else with a M3N78-VM board), the HDMI output is card 0, device 3
```

# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {
  type hw
  card 0
# barwin: removed 'device 1' and added 'device 3'
  device 3
}

```


The last step is to make sure Mythfrontend has the appropriate configuration for audio output. Goto Utilities/Setup->Setup and then the 3rd screen has the audio settings. My config is as follows:
Audio output device: ALSA:default
Passthrough output device: Default
Max Audio channels: 5.1  Upmix: Passive
Enable AC3 passthru: unchecked
Enable DTS passthru: unchecked
Aggressive Sound card buffering: unchecked
Use internal volume controls: unchecked

There's a lot of room for customization here ... if you'd rather use the analog channel as the default, go with 'dmix-analog' in the 1st .asoundrc customization above, keep MythTV's default output to 'Default' but set the passthrough device as ASLA:dmix-digital (case sensitive) and then enable the two passthrough checkboxes. Play around and see what works best for your particular setup... for me, the above settings work so I wanted to post them in case anyone else is having a hard time getting HDMI audio to work.

A couple notes (re: Troubleshooting):

[LIST]
[*]At certain points during my journey to functional HDMI audio, a couple test videos in MythTV would have terribly distorted audio (recorded TV episodes, but not downloaded movie files). That has to do with the audio sampling rate not being exactly what S/PDIF and HDMI want it to be.  The dmix-digital virtual device is key - it will make sure the sampling rate is as it should be -- see the MythTV article (above) for more info on that...
[*]make sure you can hear sound from the cmd line utils before moving on to Mythfrontend's configuration.  'aplay', 'speaker-test' and 'alsamixer' are the three commands that you'll want to play around with.
[*]sometimes rebooting or just logging out and back in to X windows will help squash certain issues.
[*]/etc/init.d/alsa-utils restart is handy ..
[*]Right after booting up, I tend to get white-noise audio until I play something in Myth. The article on MythTV's site mentions something similar which they worked around by playing a quick test with speaker-test. See this section: [http://www.mythtv.org/wiki/Configuring_Digital_Sound#Quick_Check_of_Sound_System](http://www.mythtv.org/wiki/Configuring_Digital_Sound#Quick_Check_of_Sound_System) ("Quick Check of Sound System").  Anyway, don't be scared if you get some white noise initially... it's "normal" ;)
[/LIST]


Alright, that's all I can think of for now. Hopefully this post is helpful to those of you who have been struggling with getting sound over HDMI to work.  This should, in theory, work for S/PDIF as well, since the M3N78-VM seems to treat them as the same device from what I can tell.


-Ben


------------------------------------------------------------------
[http://www.ecosnap.com/](http://www.ecosnap.com/) - Hosting a Greener Web
LAMP hosting from $5.55/mo
PHP 5, MySQL 5, cPanel 11, Fantastico De Luxe
8% donated to Environmental Causes

---

### Post by Chemical Imbalance on 2009-03-28
> **spongebobp2m said:**
> Hi,..

I have this MoBo and I can't get analog audio.
I'm using Ubuntu 8.10 for AMD64.

Has anyone got the same problem?

First, try uninstalling pulse-audio then set your audio devices all to Alsa, then

Try:  sudo alsa force-reload

This worked for me in Intrepid.  I have the M3N78-PRO version.

Updating to Jaunty fixes all problems--everything works flawlessly in the Jaunty beta with the 180.xx series Nvidia drivers.

---

### Post by barwin on 2009-03-28
For me getting analog audio to work in the m3n78-vm involved unloading and reloading the module at the *END* of the bootup process.

sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel

Stick those two lines in /etc/rc.local and it will do it for you automatically upon boot.  If you execute the lines manually, you'll get sound but no volume control so you'll need to log out and back in to X real quick...

Cheers,
-Ben

> **Chemical Imbalance said:**
> First, try uninstalling pulse-audio then set your audio devices all to Alsa, then

Try:  sudo alsa force-reload

This worked for me in Intrepid.  I have the M3N78-PRO version.

Updating to Jaunty fixes all problems--everything works flawlessly in the Jaunty beta with the 180.xx series Nvidia drivers.

---

### Post by Chemical Imbalance on 2009-03-28
> **barwin said:**
> For me getting analog audio to work in the m3n78-vm involved unloading and reloading the module at the *END* of the bootup process.

sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel

Stick those two lines in /etc/rc.local and it will do it for you automatically upon boot.  If you execute the lines manually, you'll get sound but no volume control so you'll need to log out and back in to X real quick...

Cheers,
-Ben

It isn't an issue for me now because I'm running the Jaunty beta (which is amazing btw).  Everything works great and pulseaudio sounds perfectly crisp.

---

### Post by barwin on 2009-03-28
> **Chemical Imbalance said:**
> It isn't an issue for me now because I'm running the Jaunty beta (which is amazing btw).  Everything works great and pulseaudio sounds perfectly crisp.

Nice .. I love pulseaudio and use it on my primary desktop (ubuntu 8.10).  Just downloaded the jaunty beta but haven't tried it yet.  I don't generally like to run beta OS's though, so I may just wait a while longer.

btw I meant the advice to be for spongebobp2m as a supplement to your advice, but I quoted your reply instead of his.

---

### Post by Chemical Imbalance on 2009-03-28
> **barwin said:**
> Nice .. I love pulseaudio and use it on my primary desktop (ubuntu 8.10).  Just downloaded the jaunty beta but haven't tried it yet.  I don't generally like to run beta OS's though, so I may just wait a while longer.

btw I meant the advice to be for spongebobp2m as a supplement to your advice, but I quoted your reply instead of his.

I have Jaunty installed next to Intrepid, just in case.

Oh, and I could still put that to use on my Intrepid install :)

---

### Post by notz on 2009-03-28
i recently have bought this mobo for my media center because it supports vdpau. but i'm struggling with the performance in mythtv. 

720p works mostly but stutters sometimes (arte hd). 
1080p apple trailers always stutters. 
1080i from astra promo channel also stutters 

always without interlacer. 


with mplayer i have no troubles to play the 720p and apple trailers.
  
in my mythfrontend log i get following:
2009-03-25 21:55:48.931 NVP(4): Video is 5.81385 frames behind audio (too slow), dropping frame to catch up.
2009-03-25 21:55:48.931 NVP(4): prebuffering pause
2009-03-25 21:55:48.931 NVP(4): Waiting for prebuffer..  0 AAAAAAaAAaAALAAAA
2009-03-25 21:55:48.988 NVP(4): Video is 4.82285 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '22921.12', std. dev. = '17735.73', fps = '43.63'
2009-03-25 21:55:50.862 NVP(4): Video is 3.20055 frames behind audio (too slow), dropping frame to catch up.


do you have same problems ? which formats works for you? (i have latest bios, 512 mb video ram, no gpu overclocking) 

thx,
notz

---

### Post by barwin on 2009-03-30
> **notz said:**
> i recently have bought this mobo for my media center because it supports vdpau. but i'm struggling with the performance in mythtv. 

720p works mostly but stutters sometimes (arte hd). 
1080p apple trailers always stutters. 
1080i from astra promo channel also stutters 

always without interlacer. 


with mplayer i have no troubles to play the 720p and apple trailers.
  
in my mythfrontend log i get following:
2009-03-25 21:55:48.931 NVP(4): Video is 5.81385 frames behind audio (too slow), dropping frame to catch up.
2009-03-25 21:55:48.931 NVP(4): prebuffering pause
2009-03-25 21:55:48.931 NVP(4): Waiting for prebuffer..  0 AAAAAAaAAaAALAAAA
2009-03-25 21:55:48.988 NVP(4): Video is 4.82285 frames behind audio (too slow), dropping frame to catch up.
'video_output' mean = '22921.12', std. dev. = '17735.73', fps = '43.63'
2009-03-25 21:55:50.862 NVP(4): Video is 3.20055 frames behind audio (too slow), dropping frame to catch up.


do you have same problems ? which formats works for you? (i have latest bios, 512 mb video ram, no gpu overclocking) 

thx,
notz


Maybe a stupid question, but are you sure that your installation of mythtv has VDPAU enabled?  And if so, is your playback profile set up to use it?  It won't use it by default .. 

Also, try running 'top' in a terminal window while you're doing your various playback tests and see if the CPU is being taxed. If not ... could be something else going on.

For example, I get stuttering playback sometimes depending on what deinterlacer I choose, but even so, the CPU never goes higher than 11%.

-Ben

---

### Post by notz on 2009-03-31
> **barwin said:**
> Maybe a stupid question, but are you sure that your installation of mythtv has VDPAU enabled?  And if so, is your playback profile set up to use it?  It won't use it by default .. 


for sure, i tried nearly all possible settings (opengl video sync, audio puffer, alsa settings, vdpau interlacers)

> **barwin said:**
> Also, try running 'top' in a terminal window while you're doing your various playback tests and see if the CPU is being taxed. If not ... could be something else going on.


yeah, my cpu runs hat ~ 10 % with cpufreq at 1000 Mhz

> **barwin said:**
> For example, I get stuttering playback sometimes depending on what deinterlacer I choose, but even so, the CPU never goes higher than 11%.
-Ben

yesterday, i discovered what solves my problem. i need to set cpufreq at a minimum to 1800Mhz. that solves all my glitches. i don't know exactly why, but seems hat the memory speed also increases and so make it run smoothly or alsa have some troubles at 1000Mhz.

mplayer runs at 1000 Mhz only smooth if i use alsa without a mixer (alsa:device=hw=0.3). with your asound.conf it has more glitches than mythtv. don't know really why.

i also tried to overclock the gpu but that doesn't change anything. so i have to wright a script that parses mythfrontend log and set's cpufreq to 1800 Mhz on hdtv livetv.

notz

---

### Post by nkrumm on 2009-04-17
Hello Everyone,

new member here. I am about to pull the trigger on the M3N78-VM, for use as an HTPC-- so hdmi+audio and spdif audio (2 channel only) are crucial. I could also go with the M2N68-VM board, which is a bit older and has more success marked down, but i like the idea of the n8200 graphics and a better amd processor upgrade path with the m3n78.

I don't yet care to know* how* to get this to work-- but what i'd like to hear is whether this board is currently thought to work using:
1) HDMI + audio
2) SPDIF (pcm-- for 2-channel music, i'll be running it into a separate DAC)
3) VDPAU?
* these can be yes/no answers, along with your build * :-)

Barwin and Chemical Imbalance, I'd be especially interested to hear what you both have to say regarding JAUNTY, which i'll likely be using. From what i've seen so far, jaunty and the latest nvidia drivers seems to clear up the problems?

THANKS!
~Nik

ps, i am sorry to ask such a self-involved question. the last time i tried to build a computer was in 2001, and boy have things changed. what was wrong with AGP? that stuff was the rage! ;-)

---

### Post by barwin on 2009-04-17
Hi nkrumm,

To answer your questions:

[LIST=1]
[*]HDMI+Audio - **Yes**: I have HDMI+audio working. I have only tested 2-channel audio so far though. The trick here is to run Alsa 1.0.19. Alsa version 1.0.17, which comes with Ubuntu 8.10, does not recognize the HDMI audio output. Upgrading Alsa magically solved all audio issues. As I understand it, Jaunty comes with a version of Alsa that will work out of the box, but I have not tried it yet.
[*]SPDIF - **Probably**: Although I have not tested this yet, my understanding is that this board (M3N78-VM) sends the same ouput to the S/PDIF as it does the HDMI audio ... so, it *should* work, but until I get an S/PDIF cable I can't test.
[*]VDPAU - **Yes**: Definitely works. The trick is getting the VDPAU support built into your MythTV front-end. There is a great MythTV repository set up with binary builds of version 0.21-fixes with VDPAU support back-ported in.  The other alternative is to build MythTV version 0.22 from source, since VDPAU was introduced in that version. Since most of the work here involves getting *MythTV* to have VDPAU enabled, running Jaunty will not make a difference.  I did have to install nvidia-glx-180 from  Jean-Yves' repo (same repo mentioned above for vdpau enabled mythtv) which possibly may not be necessary with Jaunty?
[/LIST]

**My System:**
M3N78-VM
Athlon 64 X2 5050e @ 2.6Ghz
4GB G-Skill RAM (2x2GB)
Distro: Mythbuntu 8.10
Repo: Jean-Yves Avanard's 0.21-fixes w/VDPAU repo: [_Click here for info_]("http://www.mythtv.org/wiki/Vdpau#MythTV_0.21-fixes_and_Ubuntu_repository")

**Conclusion**: I'm very happy with Asus M3N78-VM and MythTV as my HTPC. The only major problems I encountered during the setup were due to the outdated version of Alsa that ships with Intrepid. Jaunty more than likely solves that, but if not, upgrading to alsa 1.0.19 is not hard at all. Paired with MythTV 0.21 w/VDPAU patch, it performs amazingly well (VDPAU drops the CPU usage down below 5% for a 1080p video)

**References:**
[LIST]
[*][_MythTV with VDPAU patch - Click here_]("http://www.mythtv.org/wiki/Vdpau#MythTV_0.21-fixes_and_Ubuntu_repository")
[*][_Upgrading to Alsa 1.0.19 - Click here_]("http://ubuntuforums.org/showthread.php?p=6589810")
[*][_Setting up digital audio (HDMI or S/PDIF) - Click here_]("http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly")
[*][_My previous post on HDMI audio config_]("http://ubuntuforums.org/showpost.php?p=6972353&postcount=23")
[/LIST]

> **nkrumm said:**
> Hello Everyone,

new member here. I am about to pull the trigger on the M3N78-VM, for use as an HTPC-- so hdmi+audio and spdif audio (2 channel only) are crucial. I could also go with the M2N68-VM board, which is a bit older and has more success marked down, but i like the idea of the n8200 graphics and a better amd processor upgrade path with the m3n78.

I don't yet care to know* how* to get this to work-- but what i'd like to hear is whether this board is currently thought to work using:
1) HDMI + audio
2) SPDIF (pcm-- for 2-channel music, i'll be running it into a separate DAC)
3) VDPAU?
* these can be yes/no answers, along with your build * :-)

Barwin and Chemical Imbalance, I'd be especially interested to hear what you both have to say regarding JAUNTY, which i'll likely be using. From what i've seen so far, jaunty and the latest nvidia drivers seems to clear up the problems?

THANKS!
~Nik

ps, i am sorry to ask such a self-involved question. the last time i tried to build a computer was in 2001, and boy have things changed. what was wrong with AGP? that stuff was the rage! ;-)

---

### Post by Chemical Imbalance on 2009-04-17
I have no experience with a Myth box, but everything works great on Jaunty, including the latest stable Nvidia drivers and Pulseaudio.

---

### Post by jms-ubuntu-en on 2009-04-18
Anyone having problems (freezing) with combination: Jaunty, nvidia 180.* drivers, desktop effects and integrated GF8200?   For me this is guaranteed route to crash X session, so at the moment desktop effects are disabled. Mythtv from Jaunty's standard repositories runs just fine.

---

### Post by nkrumm on 2009-04-18
Thanks Chemical Imbalance and Barwin. I'm going to give this puppy a shot! I'll post back with progress...

---

### Post by dburnett77 on 2009-04-19
> **nkrumm said:**
> Hello Everyone,

new member here. I am about to pull the trigger on the M3N78-VM, for use as an HTPC-- so hdmi+audio and spdif audio (2 channel only) are crucial. I could also go with the M2N68-VM board, which is a bit older and has more success marked down, but i like the idea of the n8200 graphics and a better amd processor upgrade path with the m3n78.

I don't yet care to know* how* to get this to work-- but what i'd like to hear is whether this board is currently thought to work using:
1) HDMI + audio
2) SPDIF (pcm-- for 2-channel music, i'll be running it into a separate DAC)
3) VDPAU?
* these can be yes/no answers, along with your build * :-)

Barwin and Chemical Imbalance, I'd be especially interested to hear what you both have to say regarding JAUNTY, which i'll likely be using. From what i've seen so far, jaunty and the latest nvidia drivers seems to clear up the problems?

THANKS!
~Nik

ps, i am sorry to ask such a self-involved question. the last time i tried to build a computer was in 2001, and boy have things changed. what was wrong with AGP? that stuff was the rage! ;-)

Yes, audio is not Hight Big Dummies In;lepex.

---

### Post by nkrumm on 2009-04-19
> **dburnett77 said:**
> Yes, audio is not Hight Big Dummies In;lepex.

wait... what? could you try again please? :)

---

### Post by indianolajohn on 2009-04-20
> **nkrumm said:**
> wait... what? could you try again please? :)


full guide here 

[http://xbmc.org/forum/showthread.php?t=49072](http://xbmc.org/forum/showthread.php?t=49072)

this is for setting up a htpc but you could install 

video and audio drivers the same way

---

### Post by ffaker on 2009-04-20
> **nkrumm said:**
> Thanks Chemical Imbalance and Barwin. I'm going to give this puppy a shot! I'll post back with progress...

Spookily enough, I too am about to order this motherboard for use in a Jaunty-based MythTV box! So I'll look for your progress updates, and post mine in a week or two once the parts have arrived and the box is built.

This thread has been very helpful: especially the detailed stuff about audio over HDMI and VDPAU. Thanks!

---

### Post by barwin on 2009-04-21
So my latest hurdle is getting my universal remote setup to work with lirc and MythTV. Right now I'm using a wireless full keyboard which works great, but is a little clunky and the [Woman Acceptance Factor (WAF)]("http://en.wikipedia.org/wiki/Woman_acceptance_factor") is still a bit low due to that ;)

I had an old IR receiver laying around (X10) that plugs in via serial port that I'm going to be using.  As those of you with the m3n78-vm already know, there is no external serial port on this board - only the internal connector.  I searched high and low for the best deal on an IDC->db9 connector with a low-profile bracket and finally went with this one here: [http://www.techgeardirect.com/ssproduct.asp?pf_id=1012029082]("http://www.techgeardirect.com/ssproduct.asp?pf_id=1012029082")

It was only $2.10 but shipping was about $6.

Just wanted to post that link in case anyone else is searching for a low profile solution for idc->db9 serial port adapter.  If you don't need low-profile, you will probably have way more options.

More modern IR receivers seem to be USB these days? I guess that's probably easier, but since I already had this serial port one laying around, I figured why not...

---

### Post by jdeslip on 2009-04-22
On my M3N78-VM board, I have actually not been able to get audio out of my PC case front audio jacks connected to the board either with HD Audio or AC'97  (And changing the bios settings).  I am on 8.10 with alsa 1.0.17.  Does anyone have audio out of the front of their case?

---

### Post by barwin on 2009-04-22
> **jdeslip said:**
> On my M3N78-VM board, I have actually not been able to get audio out of my PC case front audio jacks connected to the board either with HD Audio or AC'97  (And changing the bios settings).  I am on 8.10 with alsa 1.0.17.  Does anyone have audio out of the front of their case?

No luck here either with the front audio port with 8.10 and alsa 1.0.19.  Upgrading to Jaunty today though, will let you know if results are any different there...

One thing though, I noticed that it automatically mutes the 'front' channel when you unplug your headphone jack.  Run alsamixer *frequently* and make sure the front output is not muted.

---

### Post by jdeslip on 2009-04-22
I have another problem with this board that I thought I'd share.  It may be specific to my TV, but I hope maybe someone here can help. 

I have a Vizio VO22L  HDTV whose native resolution 720p (1280x720) over HDMI.  I have mythbox built on a M3N78-VM motherboard with an integrated 8200 nvidia card.  Using HDMI out on the board worked on the 173 driver, but hasn't worked on any other driver since then (including 180.51).  On any driver > 173, the hdmi output looks like it has dropped to about 256 colors and the resolution that is output is slightly too big (I forget the exact number but maybe 1400x900).  1280X720 isn't even an option in nvidia-settings.  I have also tried with a DVI->HDMI cable using the DVI-OUT on the board, but the same problem exists.  

Fortunately, the TV also has a VGA input and the VGA out on the board works good, at a native 1680x1050 resolution.  So, I am not totally screwed, but I'd like to get the HDMI to work; partly because I may switch TVs and partly because I think 1280x720 may have better performance with fullscreen flash videos.  

I am not sure if the  problem is with card or with the drivers recognition of the TV (nvidia-settings does recognize the TV model but still gives wrong resolution).  

Has anyone had a similar problem with this board?  Is it unique to my TV?  Any idea how to fix it?

---

### Post by barwin on 2009-04-23
> **jdeslip said:**
> On my M3N78-VM board, I have actually not been able to get audio out of my PC case front audio jacks connected to the board either with HD Audio or AC'97  (And changing the bios settings).  I am on 8.10 with alsa 1.0.17.  Does anyone have audio out of the front of their case?

Running Jaunty now (which ships Alsa ver 1.0.18) and still no luck with the front jack.  However, HDMI audio worked without any fuss - no need to manually [upgrade alsa]("http://ubuntuforums.org/showthread.php?p=6589810") anymore. Yay :)   (note: still had to [configure my ~/.asoundrc]("http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly") to make HDMI the default)


> I have a Vizio VO22L HDTV whose native resolution 720p (1280x720) over HDMI. I have mythbox built on a M3N78-VM motherboard with an integrated 8200 nvidia card. Using HDMI out on the board worked on the 173 driver, but hasn't worked on any other driver since then (including 180.51). On any driver > 173, the hdmi output looks like it has dropped to about 256 colors and the resolution that is output is slightly too big (I forget the exact number but maybe 1400x900). 1280X720 isn't even an option in nvidia-settings. I have also tried with a DVI->HDMI cable using the DVI-OUT on the board, but the same problem exists.

Hrmm, I'd suggest trying the nvidia-glx-180 deb that [jean-yves avenard has in his custom repo]("http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html"). That's what I'm using ... I've tried both 1280x720 and 1920x1080 and both work well, but I keep it on 1080

repo: [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by jdeslip on 2009-04-23
> **barwin said:**
> 

Hrmm, I'd suggest trying the nvidia-glx-180 deb that [jean-yves avenard has in his custom repo]("http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html"). That's what I'm using ... I've tried both 1280x720 and 1920x1080 and both work well, but I keep it on 1080

repo: [http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

Actually, I am using the drivers from jean-yves' repo.  Still, no luck.  I think it might be particular to my TV.  Not sure.

---

### Post by barwin on 2009-04-23
> **jdeslip said:**
> Actually, I am using the drivers from jean-yves' repo.  Still, no luck.  I think it might be particular to my TV.  Not sure.

Damn ... that was the only thing that came to mind.  Guess we need someone with the same TV to pipe in.

---

### Post by jdeslip on 2009-04-25
Actually, the nvidia settings correctly shows resolution of 1280x720 on 180.51 driver with hdmi but the output is slightly too big for the screen.... and the colors are still wonky.  

The odd thing is that it sometimes randomly displays correctly after reboot but develops the problemonce the screensaver (turning off the screen) comes and off.  

It seems like a problem with my TV, but it works fine with the 173.x driver.  Any advice, help?

---

### Post by dburnett77 on 2009-04-25
Decided to order from Directron.com:

Thermaltake WingsRS 201
Logisys 550W PSU
ASUS M3N78-VM
AMD Athlon X2 7750
WD Caviar SE16 320 GB HD
Kingston HyperX 4GB/2X2GB 800 MHz RAM
LG LightScribe SATA DVD-RW

Total Expenditure, as of now: $337.18

Set and Final, barring major blowout deal.

---

### Post by barwin on 2009-04-26
> **jdeslip said:**
> Actually, the nvidia settings correctly shows resolution of 1280x720 on 180.51 driver with hdmi but the output is slightly too big for the screen.... and the colors are still wonky.  

The odd thing is that it sometimes randomly displays correctly after reboot but develops the problemonce the screensaver (turning off the screen) comes and off.  

It seems like a problem with my TV, but it works fine with the 173.x driver.  Any advice, help?

Come to think of it, every now and then my TV (brand=Sceptre) does what you described where the output is too big for the screen. It happens after watching certain videos but I haven't picked up a definite pattern yet. Usually if I turn the TV off and back on, it corrects itself.  Restarting X does not seem to help, at least not consistently.  When this happens the colors still look fine though.  I'm actually a little relieved to hear I'm not the only one with the weird resolution-screensize mismatch. I thought my TV was dying or something.  That all said though, since the colors are fine it really hasn't been that big of an issue.  What's happening in your situation sounds like it makes it pretty un-watchable.

It almost sounds like a loose cable though. But sounds like you've tried a few different connection types at this point so that probably rules out that idea...

Wish I could be more helpful .. good luck

-Ben

---

### Post by jdeslip on 2009-04-26
Well, the color isn't completely off.  It just looks like dropped from millions of colors to thousands.  Like the menu shadows and stuff look off.

---

### Post by nkrumm on 2009-04-28
update:

after reading too many posts about fullscreen XBMC troubles with the 8200IGP, i'm nearly to the point of choosing the gigabyte GA-E7AUM-DS2H intel board with 9400 graphics built-in. which costs 50-70 dollars more, and i cannot use the low-power AMD 5050e :(

barwin-- have you tried fullscreen 1080p playback in XBMC? you seemed to have great success with mythTV, and hdmi/1080p in general.  I'd be interested to hear what happens...

thanks
nik

---

### Post by barwin on 2009-04-28
> **nkrumm said:**
> update:

after reading too many posts about fullscreen XBMC troubles with the 8200IGP, i'm nearly to the point of choosing the gigabyte GA-E7AUM-DS2H intel board with 9400 graphics built-in. which costs 50-70 dollars more, and i cannot use the low-power AMD 5050e :(

barwin-- have you tried fullscreen 1080p playback in XBMC? you seemed to have great success with mythTV, and hdmi/1080p in general.  I'd be interested to hear what happens...

thanks
nik

I'll try it out tonight - I have tinkered with XBMC a little. It works as a frontend for MythTV actually ... I LOVE the interface but as a mythtv frontend it was lacking some important features like automatic commercial skipping.  I don't recall testing 1080p content. I'm a bit curious myself about how it'll perform. Will let you know!

Btw, that Gigabyte board looks awesome. But that is indeed a bummer that you can't pair it up with one of the low wattage processors, and a further bummer that it costs so much more than the m3n78-vm.  I'm liking AMD at the moment but if I were doing Intel I'd certainly consider that board.

Also, there seem to be a few boards out there with the nvidia 9300 that are a tad cheaper than the 9400 ones.  If those are also rumored to have good performance with the particular setup you're shooting for, might be a good way to shave $15-30 off.  [This thread]("http://www.gossamer-threads.com/lists/mythtv/users/361401?do=post_view_flat#361401") that had a couple recommendations.

Cheers,
-Ben

---

### Post by nkrumm on 2009-04-28
> **barwin said:**
> ... But that is indeed a bummer that you can't pair it up with one of the low wattage processors, and a further bummer that it costs so much more than the m3n78-vm.  I'm liking AMD at the moment but if I were doing Intel I'd certainly consider that board.

Also, there seem to be a few boards out there with the nvidia 9300 that are a tad cheaper than the 9400 ones.  If those are also rumored to have good performance with the particular setup you're shooting for, might be a good way to shave $15-30 off.  [This thread]("http://www.gossamer-threads.com/lists/mythtv/users/361401?do=post_view_flat#361401") that had a couple recommendations.

Cheers,
-Ben

did some more research:
Regarding the power consumption: the E5200 Wolfsdale core-- although rated 65W-- is actually a 45nm chip, and has some of the lowest idle/peak power consumption scores out there. So that is enouraging. see here: [http://www.xbitlabs.com/articles/cpu/display/core2duo-e7300-pdc-e5200_12.html#sect0](http://www.xbitlabs.com/articles/cpu/display/core2duo-e7300-pdc-e5200_12.html#sect0) (granted, no 4050/5050e in the mix) and here [http://www.tomshardware.com/reviews/athlon-64-power,2259-7.html](http://www.tomshardware.com/reviews/athlon-64-power,2259-7.html) (5050e vs. E7200)

Another option does seem to be the asus p5n7a. about 15 dollars cheaper, as you mentioned. the 9300 IGP is fine, im sure, but check out the last graph here: [http://www.trustedreviews.com/motherboards/review/2008/11/27/Gigabyte-GA-E7AUM-DS2H/p4](http://www.trustedreviews.com/motherboards/review/2008/11/27/Gigabyte-GA-E7AUM-DS2H/p4) not sure how legit their review is, but 55W (gigabyte) vs. 70W (asus) is a huge difference.  Another comparison (no methodology) here [http://www.avsforum.com/avs-vb/showthread.php?p=15356946#post15356946](http://www.avsforum.com/avs-vb/showthread.php?p=15356946#post15356946). Also, the p5n7a northbridge gets quite hot and some people have had overheating issues. The last thing i want to do is add additional fans to keep some integrated graphics chip cool!

so many considerations!

ps
sorry to hijack the thread :-\

---

### Post by barwin on 2009-04-28
> **nkrumm said:**
> did some more research:
Regarding the power consumption: the E5200 Wolfsdale core-- although rated 65W-- is actually a 45nm chip, and has some of the lowest idle/peak power consumption scores out there. So that is enouraging. see here: [http://www.xbitlabs.com/articles/cpu/display/core2duo-e7300-pdc-e5200_12.html#sect0](http://www.xbitlabs.com/articles/cpu/display/core2duo-e7300-pdc-e5200_12.html#sect0) (granted, no 4050/5050e in the mix) and here [http://www.tomshardware.com/reviews/athlon-64-power,2259-7.html](http://www.tomshardware.com/reviews/athlon-64-power,2259-7.html) (5050e vs. E7200)

Another option does seem to be the asus p5n7a. about 15 dollars cheaper, as you mentioned. the 9300 IGP is fine, im sure, but check out the last graph here: [http://www.trustedreviews.com/motherboards/review/2008/11/27/Gigabyte-GA-E7AUM-DS2H/p4](http://www.trustedreviews.com/motherboards/review/2008/11/27/Gigabyte-GA-E7AUM-DS2H/p4) not sure how legit their review is, but 55W (gigabyte) vs. 70W (asus) is a huge difference.  Another comparison (no methodology) here [http://www.avsforum.com/avs-vb/showthread.php?p=15356946#post15356946](http://www.avsforum.com/avs-vb/showthread.php?p=15356946#post15356946). Also, the p5n7a northbridge gets quite hot and some people have had overheating issues. The last thing i want to do is add additional fans to keep some integrated graphics chip cool!

so many considerations!

ps
sorry to hijack the thread :-\

So I tried XBMC w/full screen 1920x1080 and the results were pretty bad, unfortunately.  Now, I'm a newb when it comes to xbmc so who knows if I'm using the most optimal settings, but I did go in and select VDPAU for video playback (which works great on the same machine w/MythTV) and 1080p playback was non-watchable.  Picture was there, but slow/delayed/choppy, sound was messed up, etc.

I tried watching some SD content as well, and the picture was completely jumbled, though audio seemed to work just fine.

If I were to spend a few hours with it, I'm sure I could figure out more. I don't think I will though since MythTV does the trick. If there is a particular combo of settings you want me to try tho, I'd be happy to give it a shot.

BTW those comparisons on the processors and boards is quite interesting.  Good finds!  Going with the low power consumpion / low heat is definitely the way to go especially if the price hike is only $15ish - you'll make that back in saved energy costs in no time :)

---

### Post by nkrumm on 2009-04-28
as i expected :(

you could try the patch from motd2k (xbmc dev for vdpau) [http://xbmc.org/forum/showpost.php?p=323942&postcount=966](http://xbmc.org/forum/showpost.php?p=323942&postcount=966) (also more info in that thread, it seems to be a driver issue).

OR per [http://www.nvnews.net/vbulletin/showpost.php?p=1988966&postcount=31](http://www.nvnews.net/vbulletin/showpost.php?p=1988966&postcount=31) start in windowed mode and then fullscreen the program.

and some info that is over my head right now here: [http://www.nvnews.net/vbulletin/showthread.php?t=131715&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=131715&page=3)

anyways, thanks for all your help and testing!
~Nik

---

### Post by jdeslip on 2009-04-30
So, has anyone out there been able to get front audio to work on this board?

---

### Post by jt_04 on 2009-04-30
> **barwin said:**
> I got HDMI audio to work with the M3N78-VM and MythBuntu 8.10!


wow it works! thanks for the directions!  all i had to do was upgrade my alsa driver.  i'm using Jaunty with M3N78-EM with a Nvidia 9400 GT.  

now i just have to figure out the right modeline for my sony bravia 40".

---

### Post by yzf600 on 2009-05-02
I got the analog audio to work on this board with Intrepid using alsa instead of pulseaudio. 

So yesterday I upgraded from Intrepid to Jaunty. I also upgraded the nvidia drivers to 180. Now my sound is broken. It seems as though the upgrade installed pulse again. All I get is some crackly sound out of the speakers. I tried to remove pulse and go back to alsa (esound), but that resulted in no sound at all. It seems as though everyone here has gotten pulse to work with this board on Jaunty just fine.  

Can anyone with this board who runs Jaunty (9.04) post their contents of /etc/pulse or ~/.pulse directory? 

I'm really frustrated as this is my HTPC. I can't watch jack squat without sound!

---

### Post by yzf600 on 2009-05-02
I ended up installing the 9.04 from scratch on a new drive. Audio worked perfect.

---

### Post by jdeslip on 2009-05-02
> **yzf600 said:**
> I ended up installing the 9.04 from scratch on a new drive. Audio worked perfect.

Does that mean front audio as well?

---

### Post by Original_Name on 2009-05-05
> **jdeslip said:**
> I have another problem with this board that I thought I'd share.  It may be specific to my TV, but I hope maybe someone here can help. 

I have a Vizio VO22L  HDTV whose native resolution 720p (1280x720) over HDMI.  I have mythbox built on a M3N78-VM motherboard with an integrated 8200 nvidia card.  Using HDMI out on the board worked on the 173 driver, but hasn't worked on any other driver since then (including 180.51).  On any driver > 173, the hdmi output looks like it has dropped to about 256 colors and the resolution that is output is slightly too big (I forget the exact number but maybe 1400x900).  1280X720 isn't even an option in nvidia-settings.  I have also tried with a DVI->HDMI cable using the DVI-OUT on the board, but the same problem exists.  

Fortunately, the TV also has a VGA input and the VGA out on the board works good, at a native 1680x1050 resolution.  So, I am not totally screwed, but I'd like to get the HDMI to work; partly because I may switch TVs and partly because I think 1280x720 may have better performance with fullscreen flash videos.  

I am not sure if the  problem is with card or with the drivers recognition of the TV (nvidia-settings does recognize the TV model but still gives wrong resolution).  

Has anyone had a similar problem with this board?  Is it unique to my TV?  Any idea how to fix it?

I have a Samsung 2333HD that was producing a very similar issue.  According to the NVidia Display Utility (v180) it was outputting at my monitor's 1080p native resolution 1920x1080, and according to the info display button on the TV, it was receiving the same 1920x1080 1080p resolution.  I finally gave in ](*,) and used the "Auto-scale" feature to scale the image to my display 16:9 (Which actually looked pretty good).  That's when I noticed in the settings on the actual TV that you could define from a drop-down menu what sort of device was on the HDMI input.  As soon as I set it to PC , **WHAM** 1920x1080 1080p wonderfulness was presented to my sleep deprived eyes!  It was like that moment when the sky opens up, the choir sings, and the beam of light strikes you in the face.  It was that good :D

---

### Post by Original_Name on 2009-05-06
Alright, this is driving me crazy...  ](*,) ](*,) ](*,)
So I followed all of the instructions at [http://ubuntuforums.org/showpost.php?p=6972353&postcount=23](http://ubuntuforums.org/showpost.php?p=6972353&postcount=23) and I get audio over my HDMI via the command

```
speaker-test -twav -c6 -Dplug:hdmi
```However I get no audio out of Mythbuntu whether it be in a video or mp3.

Here is my aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```and my aplay -L

```
default:CARD=NVidia
    HDA NVidia, VT1708B Analog
    Default Audio Device
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

```Attached is a copy of my asound.conf file (renamed asound.txt for upload requirements)

Any help is greatly appreciated.
Thanks!

---

### Post by barwin on 2009-05-06
> **Original_Name said:**
> 
Attached is a copy of my asound.conf file (renamed asound.txt for upload requirements)

Any help is greatly appreciated.
Thanks!

weird, everything looks as it should - I diff'd your asound.conf with my ~/.asoundrc and there were no differences 

My only thought would be to save the asound.conf as ~/.asoundrc instead of /etc/asound.conf (make sure it's saved in the home directory for whatever user you're logged in as when mythfrontend is running)

Then delete /etc/asound.conf (or move it out of the way).  Then log out and back in to X.  Or run ```
sudo alsa force-reload
``` (or reboot)

When the .asoundrc file is properly in-use, it should send all sound from any app over the HDMI channel.  So try some other tests before trying again in Myth ... that will help you determine if it's an ALSA config problem or just a MythTV config problem.  For example, try playing something in VLC or mplayer and see if that works.

The only other thing I can think is to make sure pulseaudio isn't screwing stuff up? Remove pulseaudio if it's installed..

Hopefully that helps,
-Ben

---

### Post by Original_Name on 2009-05-06
I am at work now, so I will have to try your suggestions when I get home.

I ran across this post that might lend some help, but it's for the M3N78-EM **[COLOR=Red]*NOT*[/COLOR]** the M3N78-VM

[http://ubuntuforums.org/showpost.php?p=7152783&postcount=9](http://ubuntuforums.org/showpost.php?p=7152783&postcount=9)

---

### Post by barwin on 2009-05-06
> **Original_Name said:**
> I am at work now, so I will have to try your suggestions when I get home.

I ran across this post that might lend some help, but it's for the M3N78-EM **[COLOR=Red]*NOT*[/COLOR]** the M3N78-VM

[http://ubuntuforums.org/showpost.php?p=7152783&postcount=9](http://ubuntuforums.org/showpost.php?p=7152783&postcount=9)

Actually, with Jaunty, you don't need to upgrade alsa.  When I wrote the guide, I was running Intrepid (8.10). After upgrading to jaunty, I didn't need to touch alsa.  Even though it's only alsa version 1.0.18, it still seems to detect and use the HDMI output just fine (still had to customize the .asoundrc though).

With either version, though, if you can hear sound w/speaker-test, then alsa's good to go.  It *should* just be a configuration thing from then on, not a version thing.

Cheers,

-Ben

---

### Post by Original_Name on 2009-05-07
Well, wouldn't you know it...

I decided to reinstall Mythbuntu Jaunty, and all I had to do was un-mute the IEC958 channel in Alsamixer, and import my asound.conf file.  Worked like charm \\:D/ \\:D/ \\:D/ HDMI AUDIO!!! :guitar:

I definitely did those steps many times before, so I am pretty certain it had something to do with the following things...

[LIST=1]
[*]I am very new to Linux
[*]I tried about 30 different things/tricks/hints/tips
[*]I installed a bunch of crud trying to get it to work
[*]I was going insane trying to get this to work
[/LIST]
 
Clearly something got screwed up along the way with all of these changes I was making.
Was it the install of the 1.0.19 ALSA? I dunno, could have been...  I'll have to test it out and see.

Thanks again for the help!

---

### Post by barwin on 2009-05-07
> **Original_Name said:**
> 
I was going insane trying to get this to work


Welcome to the club 

:)

---

### Post by Original_Name on 2009-05-07
So just for the record, in case anyone else is looking for advise on what system to buy, my system functions perfectly at playing 1080p video/audio over HDMI, and capturing OTA HDTV signals.  Here are it's parts, and except for the HDHomerun it only cost me $307 with shipping from Newegg!
    
[LIST=1]
[*][Mythbuntu 9.04 Jaunty Jackalope running the mixed back/front-end setup]("http://www.mythbuntu.org/")
[*]NVidia Driver 180.44
[*][HDHomerun]("http://www.silicondust.com/products/hdhomerun")
[*][IN WIN BL641.300TBL Black Steel MicroATX Slim Case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811108106&Tpk=11-108-106")
[*][(MOBO) M3N78-VM NVIDIA GeForce 8200 (1006 BIOS) Chipset with 1080p HDMI out]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318&Tpk=13-131-318")
[*][(CPU) AMD Athlon 64 X2 7750 Kuma 2.7GHz AM2+ 95Watts]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103300&Tpk=19-103-300")
[*][(RAM) OCZ2N1066SR2GK (2 x 1GB)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227181&Tpk=20-227-181")
[*][(Hard Drive) Western Digital Caviar SE16 WD6400AAKS 640GB 7200RPM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136218&Tpk=22-136-218")
[/LIST]
  The only tweaking I had to do with Mythbuntu was to follow the directions provided by the following post
[http://ubuntuforums.org/showpost.php?p=6972353&postcount=23](http://ubuntuforums.org/showpost.php?p=6972353&postcount=23)



The Motherboard has a ton of features in the BIOS for overclocking, but I have not messed with them yet.  The motherboard did not automatically select the best timings from the RAM's SPD table, I had to manually enter them.  But that is probably a good thing, because you want the computer to be able to boot.  I am currently running at the advertised 5-5-5-19 setup with the voltage on auto.  I plan on tweaking the timings/frequency more in the future, but I ran memtest overnight on it and it appears that I am stable for now.  I had to install WinXP on a seperate partition so that I could run CPU-Z to confirm my timings etc...

As of the most recent BIOS the 533MHz (1066) is only available to AM2+ CPU's and only supported for the first two DIMM slots, with a maximum of 1GB per slot.  So basically if you want the 533MHz (1066) Dual-Channel RAM then you have to go with the 2 x 1GB.  Also depending upon how much ram you dedicate to the video (64, 128, 256, 512), you lose that off the top of your avaiable RAM as well.

I suggest setting the memory to unganged mode if you are running the Dual-Channel setup, because my understanding is that the on-die (CPU) memory controller(s?) map each core to it's own DIMM of memory.  I don't know how that would be affected if you're running a 3-core design, but if you google "ganged vs unganged" you should get more than enough info regarding it.  For my 2-core setup though, I believe that this unganged arrangment will be the best configuration.

The Southbridge has a big copper heatsink slapped on it, and for good reason, it gets hot.  Some of this may have had to do with the fact that the case lid was off, and this interupted the airflow of the case.  However I slapped a small fan on the heatsink just to be sure.

The board also supports a "Hybrid" SLI design, so that will be good if I ever wanted to do more with it.

My only complaints about the board are the following

[LIST=1]
[*]The ATX power connector is directly in the way of where the DVD drive would be.  It's going to take some creative engineering on my part to make room for it.
[*]The IDE port comes off the side of the board in the very front making it very inaccessable, but everything i am running is SATA anyway so it's not much of a deal breaker for me.
[*]The aluminum cover for the back of the case where all of the ports come out seems like it could have been made to some closer tolerances, or maybe the ports be placed a little more outward on the board it's self, as many of the ports seem quite recessed.  Again not a deal breaker because they all still work.
[/LIST]
Overall I am quite happy, and I would recommend this setup to anyone.

---

### Post by barwin on 2009-05-07
> **Original_Name said:**
> 
As of the most recent BIOS the 533MHz (1066) is only available to AM2+ CPU's and only supported for the first two DIMM slots, with a maximum of 1GB per slot.  So basically if you want the 533MHz (1066) Dual-Channel RAM then you have to go with the 2 x 1GB.  Also depending upon how much ram you dedicate to the video (64, 128, 256, 512), you lose that off the top of your avaiable RAM as well.


Damn ... I went with 2 x 2GB, didn't catch that when I bought the parts.

Lots of good info in that post, thanks!

---

### Post by Original_Name on 2009-05-07
> **Original_Name said:**
> 

As of the most recent BIOS the 533MHz (1066) is only available to AM2+ CPU's and only supported for the first two DIMM slots, with a maximum of 1GB per slot.  So basically if you want the 533MHz (1066) Dual-Channel RAM then you have to go with the 2 x 1GB.  Also depending upon how much ram you dedicate to the video (64, 128, 256, 512), you lose that off the top of your available RAM as well.

Well... I think I might have to partially redact that statement.... #-o

The QVL for the 1066 memory did not list any modules larger than 1GB, but quoting from the manual,

> Due to the chipset's limitations, the 1066 memory modules run at 1066
MHz only when:

[LIST]
[*]two 1066 MHz memory modules installed in the same colored-slots
(either in the yellow slots or black slots); and
[*]one 1066 MHz memory module installed in any of the slots.
[/LIST]
In other cases, the 1066 MHz memory modules can only run at 800MHz.
So I apologize for the misinformation I was confused.  :) 
Out of curiosity what memory are you running then, and are you sure it's running at 533MHz?  I wouldn't mind upgrading to the 2x2GB :D

---

### Post by Chemical Imbalance on 2009-05-07
I have the M3N78-PRO version of this motherboard with the onboard 8300 nvidia graphics.

Is anybody else experiencing lockups in Jaunty with the latest nvidia drivers?  It worked great in Intrepid.

Does the VM motherboard version have this same gpu?

---

### Post by Original_Name on 2009-05-07
> **Chemical Imbalance said:**
> I have the M3N78-PRO version of this motherboard with the onboard 8300 nvidia graphics.

Is anybody else experiencing lockups in Jaunty with the latest nvidia drivers?  It worked great in Intrepid.

Does the VM motherboard version have this same gpu?

I have the M3N78-VM, and it's Northbridge chipset (integrated video) is the        NVIDIA GeForce 8200

According to [Wikipedia]("http://en.wikipedia.org/wiki/GeForce_8200_Chipset"), the        NVIDIA GeForce 8[SIZE=4]**3**[/SIZE]00 is the Intel version of the chipset, whereas the 8[SIZE=4]**2**[/SIZE]00 is the AMD chipset.  So they're the same.

I am running Jaunty and have experienced no issues with the video locking up, but I have only been running for about 2 days.   Is it happening when you are doing intensive stuff like playing content, or just at seemingly random intervals?

---

### Post by Chemical Imbalance on 2009-05-08
> **Original_Name said:**
> I have the M3N78-VM, and it's Northbridge chipset (integrated video) is the        NVIDIA GeForce 8200

According to [Wikipedia]("http://en.wikipedia.org/wiki/GeForce_8200_Chipset"), the        NVIDIA GeForce 8[SIZE=4]**3**[/SIZE]00 is the Intel version of the chipset, whereas the 8[SIZE=4]**2**[/SIZE]00 is the AMD chipset.  So they're the same.

I am running Jaunty and have experienced no issues with the video locking up, but I have only been running for about 2 days.   Is it happening when you are doing intensive stuff like playing content, or just at seemingly random intervals?

The 8300 is also for AMD chipsets.  I custom built mine with AMD Phenom X4.
I've already filed a bug report and there is a thread with dozens of people with the same problem.
It turns out that the nvidia proprietary drivers seem to be the culprit.  
I've uninstalled them and no more lockups so far.  
The odd thing is that it worked fine with nvidia drivers in Intrepid.  
I've tried downgrading to the same nvidia driver I used in Intrepid within Jaunty and no luck.  
I'm guessing it is a bug in combination with the jaunty kernel + nvidia drivers.

I'll try an upstream kernel later + nvidia drivers.

---

### Post by Original_Name on 2009-05-08
Well damn, I am just on a roll with the misinformation...  :oops:

I misread the article where it said [SIZE=4]**9**[/SIZE]300 instead of [SIZE=4]**8**[/SIZE]300
[http://en.wikipedia.org/wiki/GeForce_8200_Chipset#cite_note-0](http://en.wikipedia.org/wiki/GeForce_8200_Chipset#cite_note-0)

I did some better research this time though, FTA
> The GeForce 8300 probably was a reaction to AMD’s graphics performance with the 780G chipset, as the 8200 and 8300 are identical except for the clock speed of their 16 stream processors: the GeForce 8200 runs at 1.2 GHz, while the GeForce 8300 is clocked at a 1.5 GHz speed, providing improved 3D graphics performance.[http://www.tomshardware.com/reviews/amd-nvidia-chipset,1972-9.html](http://www.tomshardware.com/reviews/amd-nvidia-chipset,1972-9.html)

Hopefully I got it right this time  :D

---

### Post by Chemical Imbalance on 2009-05-08
> **Original_Name said:**
> Well damn, I am just on a roll with the misinformation...  :oops:

I misread the article where it said [SIZE=4]**9**[/SIZE]300 instead of [SIZE=4]**8**[/SIZE]300
[http://en.wikipedia.org/wiki/GeForce_8200_Chipset#cite_note-0](http://en.wikipedia.org/wiki/GeForce_8200_Chipset#cite_note-0)

I did some better research this time though, FTA
[http://www.tomshardware.com/reviews/amd-nvidia-chipset,1972-9.html](http://www.tomshardware.com/reviews/amd-nvidia-chipset,1972-9.html)

Hopefully I got it right this time  :D

Yep that's the one :)

It works fine without the nvidia drivers in Jaunty I have found.

It's probably a kernel issue though.  I hope the .29 or .30 kernel fixes the problem.

---

### Post by barwin on 2009-05-08
> **Original_Name said:**
> 
Out of curiosity what memory are you running then, and are you sure it's running at 533MHz?  I wouldn't mind upgrading to the 2x2GB :D

Here's the RAM I'm using, bought from newegg:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122")

The description is: G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory

So I guess it's somewhat of a moot point afterall (for me at least) ... I forget why I went with the ddr2-800 over 1066 .. maybe price? Ooohh, I went with an AM2 socket CPU, not an AM2+, so I wouldn't have been able to take advantage of the 1066 unless I went with a more expensive CPU as well.  I think that was train of thought when I was choosing parts.

Here's my frontend system:

**mboard**: [Asus M3N78-VM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131318")
**CPU**: [AMD Athlon 64 X2 5050e Brisbane 2.6GHz Socket AM2 45W Dual-Core Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103298")
**Mem**: [G.SKILL 4GB (2 x 2GB) DDR2 800 (PC2 6400) ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122")
**Case**: [Rosewill R379-SM Black/ Silver 0.8mm SGCC Steel MicroATX Slim Case Computer Case PSU ATX12V Flex 300W Power Supply]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811147098")

The total was only about $230 .. possibly cheaper by now.  I used a spare drive that was laying around, though eventually I'd like to try a diskless frontend to cut the noise/power consumption down.  The tuner card is a pcHDTV 5500 ([http://www.pchdtv.com/](http://www.pchdtv.com/)) and I have that in my everyday desktop which is doubling as the backend.

Cheers,
-Ben

---

### Post by jdeslip on 2009-05-08
It looks like a new version of alsa 1.0.20 was released this week.  Changelog shows a bunch of fixes to hda codec.  Anyone braver than me running this?  Can you check if front audio works?

---

### Post by dburnett77 on 2009-05-16
> **jdeslip said:**
> It looks like a new version of alsa 1.0.20 was released this week.  Changelog shows a bunch of fixes to hda codec.  Anyone braver than me running this?  Can you check if front audio works?

Need the cable, as it runs different bandwidth.

Nice board...works well.

---

### Post by jdeslip on 2009-05-16
Huh?  What does that mean?  Do you have frontaudio working?

---

### Post by dburnett77 on 2009-05-16
> **jdeslip said:**
> Huh?  What does that mean?  Do you have frontaudio working?

Yes and no.  Listen here pix, tricks are 4 kids.

If you can't stand up to the box ur in front of, stand aside and give it up...

---

### Post by ffaker on 2009-06-15
> **Chemical Imbalance said:**
> I have the M3N78-PRO version of this motherboard with the onboard 8300 nvidia graphics.

Is anybody else experiencing lockups in Jaunty with the latest nvidia drivers?  It worked great in Intrepid.

Yes I get these really hard lockups when doing things like adjusting the power savings settings. I have turned off desktop effects though, and that seems to have solved it.

Anyone know what is behind this? (desktop effects would be nice)

---

### Post by rjb308 on 2009-07-08
Hi All!
I am fairly new to all of this.. I have read the thread and it has helped emmensley.
I do have one problem. Every time I try to install the nvidia drivers my system will 
not boot into ubuntu.. I will get the ubuntu and loading line in the bottom once it is complete
there are several skips.. then it says the nvidia was found but not working.. I do not know if
it is something in the xorg I have to put it back to generic to get a screen at all. I currently have
m3n78-vm
ubuntu 9.04
the driver I tried last was from the 3 rd party guy as well as the myth tv I installed.
any help would be great. Thanks.

---

### Post by barwin on 2009-07-08
> **rjb308 said:**
> Hi All!
I am fairly new to all of this.. I have read the thread and it has helped emmensley.
I do have one problem. Every time I try to install the nvidia drivers my system will 
not boot into ubuntu.. I will get the ubuntu and loading line in the bottom once it is complete
there are several skips.. then it says the nvidia was found but not working.. I do not know if
it is something in the xorg I have to put it back to generic to get a screen at all. I currently have
m3n78-vm
ubuntu 9.04
the driver I tried last was from the 3 rd party guy as well as the myth tv I installed.
any help would be great. Thanks.


I reinstalled 9.04 just the other day and had a similar problem when installing the vdpau patched nvidia driver from avenard's repository. The issue, in my case, was that certain packages were being held back because I didn't have the repo key installed.. The way to verify whether or not this is the problem is to open up a terminal / konsole window and run
```

sudo apt-get upgrade

```
And if it indicates that certain packages are being "held back" (namely, nvidia-glx-180), then you need to import the repo key stuff and then try again.

First step on this page indicates how to get the key imported:
[http://avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

Add the signing GPG key
```

    wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key

```

After that, do:
```

sudo apt-get update && sudo apt-get upgrade

```
and, if necessary
```

sudo apt-get dist-upgrade

```
and if nvidia-glx-180 still isn't installed, do:
```

sudo apt-get install nvidia-glx-180

```

Hopefully it's the same issue I ran into and that will help.

Cheers,
-Ben

---

### Post by spoc on 2009-07-09
> **rjb308 said:**
> I do not know if
it is something in the xorg I have to put it back to generic to get a screen at all.

Change nvidia to **nv** in /etc/X11/xorg.conf:
```
Section "Device"
    Identifier  "GF8200"
    Driver      "nvidia"

```

You should now be able to graphically browse the web again.

---

### Post by zobcat on 2009-08-24
I have this same board. I've added Avenard's repo and GPG. I upgraded all the myth packages and the nvidia 180. I created my profiles according to this:
[INDENT]If you have a nVidia < 8600GT or < 9500GT, use the following profile:

<      W: 1920 H: 720, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Advanced 2X

>=    W: 0 H: 720, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Temporal 2X[/INDENT]

Yet, I still get ~80% CPU when playing video. What am I doing wrong?

---

### Post by zobcat on 2009-08-24
Here is my playback output:

```
hal@hal:~$ mythfrontend.real -v playback
2009-08-24 14:19:46.518 Using runtime prefix = /usr
2009-08-24 14:19:46.528 XScreenSaver support enabled
2009-08-24 14:19:46.528 DPMS is active.
2009-08-24 14:19:46.528 Empty LocalHostName.
2009-08-24 14:19:46.528 Using localhost value of hal
2009-08-24 14:19:46.532 New DB connection, total: 1
2009-08-24 14:19:46.541 Connected to database 'mythconverg' at host: localhost
2009-08-24 14:19:46.542 Closing DB connection named 'DBManager0'
2009-08-24 14:19:46.545 Primary screen 0.
2009-08-24 14:19:46.546 Connected to database 'mythconverg' at host: localhost
2009-08-24 14:19:46.547 Using screen 0, 1680x1050 at 0,0
2009-08-24 14:19:46.570 user: 1000 effective user: 1000 before privileged thread
2009-08-24 14:19:46.571 user: 1000 effective user: 1000 after privileged thread
2009-08-24 14:19:46.571 user: 1000 effective user: 1000 run_priv_thread
2009-08-24 14:19:46.590 New DB connection, total: 2
2009-08-24 14:19:46.590 Connected to database 'mythconverg' at host: localhost
2009-08-24 14:19:46.592 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-08-24 14:19:46.592 Enabled verbose msgs:  important general playback
2009-08-24 14:19:46.759 The theme (Pear-odyTV-wide) is missing a themeinfo.xml file
2009-08-24 14:19:46.890 The theme (Pear-odyTV-wide) is missing a themeinfo.xml file
2009-08-24 14:19:46.934 max_width: 1680 max_height: 1050
2009-08-24 14:19:46.966 No theme dir: /home/hal/.mythtv/themes/Pear-odyTV-wide
2009-08-24 14:19:46.968 Primary screen 0.
2009-08-24 14:19:46.968 Using screen 0, 1680x1050 at 0,0
2009-08-24 14:19:46.968 No theme dir: /home/hal/.mythtv/themes/Pear-odyTV-wide
2009-08-24 14:19:46.968 The theme (Pear-odyTV-wide) is missing a themeinfo.xml file
2009-08-24 14:19:46.968 Switching to wide mode (Pear-odyTV-wide)
[COLOR="Red"]Error: API mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 180.60.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.[/COLOR]
2009-08-24 14:19:47.019 Using the Qt painter
2009-08-24 14:19:47.020 lirc init success using configuration file: /home/hal/.mythtv/lircrc
2009-08-24 14:19:47.021 JoystickMenuClient Error: Joystick disabled - Failed to read /home/hal/.mythtv/joystickmenurc
2009-08-24 14:19:47.892 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-24 14:19:48.117 Registering Internal as a media playback plugin.
2009-08-24 14:19:48.171 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-24 14:19:48.204 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-24 14:19:48.234 No theme dir: /home/hal/.mythtv/themes/Pear-odyTV-wide
2009-08-24 14:19:48.239 MythThemedMenuPrivate: Unknown tag image in background
2009-08-24 14:19:48.359 Unable to find image file: /usr/share/mythtv/themes/Pear-odyTV-wide/title/netflix.png
mount: block device /dev/sr0 is write-protected, mounting read-only
2009-08-24 14:19:50.777 Detected MediaType MEDIATYPE_DVD
2009-08-24 14:19:50.779 Found a handler
2009-08-24 14:19:50.795 MythThemedMenuPrivate: Unknown tag image in background
2009-08-24 14:19:50.982 Unable to find image file: /usr/share/mythtv/themes/Pear-odyTV-wide//title/netflix.png
2009-08-24 14:20:03.977 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-08-24 14:20:03.978 Using protocol version 40
2009-08-24 14:20:03.995 TV: Attempting to change from None to WatchingLiveTV
2009-08-24 14:20:03.996 Using protocol version 40
2009-08-24 14:20:05.104 LiveTVChain(live-hal-2009-08-24T14:20:03): ReloadAll(): Added new recording
2009-08-24 14:20:05.112 TV: StartRecorder(): took 1 ms to start recorder.
2009-08-24 14:20:05.115 DPMS Deactivated 
2009-08-24 14:20:05.144 New DB connection, total: 3
2009-08-24 14:20:05.144 Connected to database 'mythconverg' at host: localhost
2009-08-24 14:20:05.149 detectInterlace(Ignore Scan, Interlaced Scan, 25, 576) ->Interlaced Scan
2009-08-24 14:20:05.149 NVP: Disabling Audio, params(-1,2,44100)
[COLOR="Red"]Error: API mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 180.60.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.[/COLOR]
2009-08-24 14:20:05.206 [COLOR="Red"]VDPAU Error: Error at util-vdpau.cpp:197 (#1, Unknown)[/COLOR]
2009-08-24 14:20:05.206 [COLOR="Red"]VDPAU Error: Failed to create VDP Device.[/COLOR]
2009-08-24 14:20:05.206 VideoOutput: Allowed renderers: directfb,xv-blit,xshm,opengl,xlib
2009-08-24 14:20:05.207 VideoOutput: Allowed renderers (filt: dummy): xlib,xshm,directfb,xv-blit,opengl
2009-08-24 14:20:05.208 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-24 14:20:05.208 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-24 14:20:05.208 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-24 14:20:05.208 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-24 14:20:05.208 VDP: LoadBestPreferences(720x576, 60)
2009-08-24 14:20:05.208 VideoOutput: Trying video renderer: xv-blit
2009-08-24 14:20:05.208 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-24 14:20:05.208 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-24 14:20:05.208 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-24 14:20:05.208 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-24 14:20:05.212 VideoOutputXv: ctor
2009-08-24 14:20:05.213 XOff: 0, YOff: 0
2009-08-24 14:20:05.213 VDP: LoadBestPreferences(720x576, 60)
2009-08-24 14:20:05.213 Display Rect  left: -280, top: 0, width: 2240, height: 1050, aspect: 1.33333
2009-08-24 14:20:05.213 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-24 14:20:05.214 VideoOutputXv: Pixel dimensions: Screen 1680x1050, window 1680x1050
2009-08-24 14:20:05.214 VideoOutputXv: Estimated display dimensions: 427x267 mm  Aspect: 1.59925
2009-08-24 14:20:05.214 VideoOutputXv: Estimated window dimensions: 427x267 mm  Aspect: 1.59925
[COLOR="Red"]Error: API mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 180.60.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.[/COLOR]
2009-08-24 14:20:05.215 [COLOR="Red"]VDPAU Error: Error at util-vdpau.cpp:197 (#1, Unknown)[/COLOR]
2009-08-24 14:20:05.215 [COLOR="Red"]VDPAU Error: Failed to create VDP Device.[/COLOR]
2009-08-24 14:20:05.215 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: xv-blit,xshm,opengl,xlib
2009-08-24 14:20:05.215 VideoOutputXv: Desired video renderer 'vdpau' not available.
			codec 'None' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-08-24 14:20:05.215 VDP: SetVideoRenderer(xv-blit)
2009-08-24 14:20:05.215 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpauadvanceddoublerate,none) filt()
2009-08-24 14:20:05.215 VDP: New preferences: rend(xv-blit) osd(softblend) deint(linearblend,none) filt()
2009-08-24 14:20:05.216 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-24 14:20:05.216 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-24 14:20:05.216 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-24 14:20:05.216 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-24 14:20:05.216 VDP: LoadBestPreferences(720x576, 60)
2009-08-24 14:20:05.222 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  10
2009-08-24 14:20:05.222 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-08-24 14:20:05.222 VideoOutputXv: Has XVideo flags...
2009-08-24 14:20:05.222 VideoOutputXv: Has XV_BRIGHTNESS...
2009-08-24 14:20:05.222 VideoOutputXv: Here...
2009-08-24 14:20:05.222 VideoOutputXv: Grabbed xv port 283
2009-08-24 14:20:05.222 VideoOutputXv: XVideo surface found on port 283
2009-08-24 14:20:05.222 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-08-24 14:20:05.222 VideoOutputXv: XVideo Format #0 is 'YUY2'
2009-08-24 14:20:05.223 VideoOutputXv: XVideo Format #1 is 'YV12'
2009-08-24 14:20:05.223 VideoOutputXv: XVideo Format #2 is 'UYVY'
2009-08-24 14:20:05.223 VideoOutputXv: XVideo Format #3 is 'I420'
2009-08-24 14:20:05.223 VideoOutputXv: Using XVideo Format 'YV12'
2009-08-24 14:20:05.223 VideoOutputXv: CreateShmImages(32): video_dim: 720x576
2009-08-24 14:20:05.291 VDP: SetVideoRenderer(xv-blit)
2009-08-24 14:20:05.291 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2009-08-24 14:20:05.291 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-08-24 14:20:05.291 Display Rect  left: -280, top: -104, width: 2240, height: 1259, aspect: 1.59925
2009-08-24 14:20:05.291 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-24 14:20:05.293 Over/underscan. V: 0, H: 0
2009-08-24 14:20:05.293 Display Rect  left: -280, top: -104, width: 2240, height: 1259, aspect: 1.59925
2009-08-24 14:20:05.294 Video Rect    left: 0, top: 0, width: 720, height: 576, aspect: 1.33333
2009-08-24 14:20:05.294 VDP: LoadBestPreferences(720x576, 25)
2009-08-24 14:20:05.295 NVP: LoadFilters(''..) -> 0
2009-08-24 14:20:05.296 OSD Theme Dimensions W: 1280 H: 720
2009-08-24 14:20:05.557 TV: StartPlayer(): took 407 ms to start player.
2009-08-24 14:20:05.557 TV: Changing from None to WatchingLiveTV
2009-08-24 14:20:05.557 NVP: ClearAfterSeek(1)
2009-08-24 14:20:05.557 VideoOutputXv: ClearAfterSeek()
2009-08-24 14:20:05.557 VideoOutputXv: DiscardFrames(0)
2009-08-24 14:20:05.557 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:05.558 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-08-24 14:20:05.558 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:05.561 VDP: GetFilteredDeint() : xv-blit -> 'vdpauadvanceddoublerate'
2009-08-24 14:20:05.562 Failed to approve 'vdpauadvanceddoublerate' deinterlacer
2009-08-24 14:20:05.562 Couldn't load deinterlace filter 
2009-08-24 14:20:05.562 Using deinterlace method 
2009-08-24 14:20:05.562 Realtime priority would require SUID as root.
2009-08-24 14:20:05.563 rate: 25 speed: 1 skip: 1 = interval 40000
2009-08-24 14:20:05.662 nVidiaVideoSync: VBlank ioctl did not work, unimplemented in this driver?
2009-08-24 14:20:05.662 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2009-08-24 14:20:05.662 RTCVideoSync: Could not open /dev/rtc, Permission denied.
2009-08-24 14:20:05.663 Using audio as timebase
2009-08-24 14:20:05.663 Video timing method: USleep with busy wait
2009-08-24 14:20:05.663 Refresh rate: 16699, frame interval: 40000
2009-08-24 14:20:05.703 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.079 LiveTVChain(live-hal-2009-08-24T14:20:03): ReloadAll(): Added new recording
2009-08-24 14:20:07.081 LiveTVChain(live-hal-2009-08-24T14:20:03): SwitchTo(1)
2009-08-24 14:20:07.081 LiveTVChain(live-hal-2009-08-24T14:20:03): Entry@1: '1391_20090824142005'
2009-08-24 14:20:07.081 JumpToProgram(void)
2009-08-24 14:20:07.087 RingBuf(/var/lib/mythtv/recordings/1391_20090824142004.mpg): OpenFile(/var/lib/mythtv/recordings/1391_20090824142005.mpg, 12)
2009-08-24 14:20:07.087 RingBuf(/var/lib/mythtv/recordings/1391_20090824142005.mpg): CalcReadAheadThresh(2893047224 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-24 14:20:07.137 NVP: Waiting for prebuffer..  0 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.337 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.341 NVP: Waiting for prebuffer..  1 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.542 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.543 NVP: Waiting for prebuffer..  2 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.744 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.746 NVP: Waiting for prebuffer..  3 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.946 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:07.949 NVP: Waiting for prebuffer..  4 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.149 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.154 NVP: Waiting for prebuffer..  5 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.354 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.358 NVP: Waiting for prebuffer..  6 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.491 AFD: Stream #0, has id 0x49 codec id MPEG2VIDEO, type Video, bitrate 19392800 at 0x0xaf5a5c60
2009-08-24 14:20:08.493 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-24 14:20:08.493 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-24 14:20:08.493 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-24 14:20:08.493 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-24 14:20:08.494 VDP: LoadBestPreferences(1920x1088, 60)
[COLOR="Red"]Error: API mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 180.60.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.[/COLOR]
2009-08-24 14:20:08.497 [COLOR="Red"]VDPAU Error: Error at util-vdpau.cpp:1691 (#1, Unknown)[/COLOR]
2009-08-24 14:20:08.500 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-24 14:20:08.500 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-24 14:20:08.501 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-24 14:20:08.501 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-24 14:20:08.501 VDP: LoadBestPreferences(1920x1088, 60)
2009-08-24 14:20:08.501 Using 0 CPUs for decoding
2009-08-24 14:20:08.502 AFD: InitVideoCodec() 0xac7061e0 id(MPEG2VIDEO) type (Video).
2009-08-24 14:20:08.502 VideoOutputXv: InputChanged(1920,1088,1.77778) 'None'->'MPEG2'
2009-08-24 14:20:08.502 VDP: LoadBestPreferences(1920x1088, 25)
2009-08-24 14:20:08.502 VDP: GetFilteredDeint() : xv-blit -> 'vdpaubasicdoublerate'
2009-08-24 14:20:08.504 [COLOR="Red"]Failed to approve 'vdpaubasicdoublerate' deinterlacer[/COLOR]
2009-08-24 14:20:08.508 [COLOR="Red"]Couldn't load deinterlace filter [/COLOR]
2009-08-24 14:20:08.508 Using deinterlace method 
2009-08-24 14:20:08.508 VideoOutputXv: DiscardFrames(1)
2009-08-24 14:20:08.508 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.508 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:08.508 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-08-24 14:20:08.509 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:08.509 VideoOutputXv: DiscardFrames(1)
2009-08-24 14:20:08.509 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.509 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:08.509 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-08-24 14:20:08.509 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:08.509 VideoOutputXv: DiscardFrames(1)
2009-08-24 14:20:08.509 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.509 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:08.509 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-08-24 14:20:08.509 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:08.510 VideoOutputXv: Closing XVideo port 283
[COLOR="Red"]Error: API mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 180.60.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.[/COLOR]
2009-08-24 14:20:08.589 [COLOR="Red"]VDPAU Error: Error at util-vdpau.cpp:197 (#1, Unknown)[/COLOR]
2009-08-24 14:20:08.589 [COLOR="Red"]VDPAU Error: Failed to create VDP Device.[/COLOR]
2009-08-24 14:20:08.589 VideoOutputXv: InitSetupBuffers() render: vdpau, allowed: xv-blit,xshm,opengl,xlib
2009-08-24 14:20:08.590 VideoOutputXv: Desired video renderer 'vdpau' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2009-08-24 14:20:08.590 VDP: SetVideoRenderer(xv-blit)
2009-08-24 14:20:08.590 VDP: Old preferences: rend(vdpau) osd(vdpau) deint(vdpaubasicdoublerate,none) filt()
2009-08-24 14:20:08.590 VDP: New preferences: rend(xv-blit) osd(softblend) deint(linearblend,none) filt()
2009-08-24 14:20:08.590 VDP: Accepting: cmp(< 1920 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpauadvanceddoublerate,none) filt()
2009-08-24 14:20:08.590 VDP: Accepting: cmp(>= 0 720) dec(vdpau) cpus(0) skiploop(enabled) rend(vdpau) osd(vdpau) osdfade(enabled) deint(vdpaubasicdoublerate,none) filt()
2009-08-24 14:20:08.590 VDP: LoadBestPreferences(2048x2048, 0)
2009-08-24 14:20:08.590 VDP: LoadBestPreferences(2048x2048, 60)
2009-08-24 14:20:08.590 VDP: LoadBestPreferences(1920x1088, 60)
2009-08-24 14:20:08.591 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  10
2009-08-24 14:20:08.591 VideoOutputXv: Adaptor#0: NV17 Video Texture has flag[s]: XvInputMask XvImageMask 
2009-08-24 14:20:08.591 VideoOutputXv: Has XVideo flags...
2009-08-24 14:20:08.591 VideoOutputXv: Has XV_BRIGHTNESS...
2009-08-24 14:20:08.591 VideoOutputXv: Here...
2009-08-24 14:20:08.591 VideoOutputXv: Grabbed xv port 283
2009-08-24 14:20:08.591 VideoOutputXv: XVideo surface found on port 283
2009-08-24 14:20:08.591 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-08-24 14:20:08.591 VideoOutputXv: XVideo Format #0 is 'YUY2'
2009-08-24 14:20:08.591 VideoOutputXv: XVideo Format #1 is 'YV12'
2009-08-24 14:20:08.591 VideoOutputXv: XVideo Format #2 is 'UYVY'
2009-08-24 14:20:08.591 VideoOutputXv: XVideo Format #3 is 'I420'
2009-08-24 14:20:08.591 VideoOutputXv: Using XVideo Format 'YV12'
2009-08-24 14:20:08.591 VideoOutputXv: CreateShmImages(32): video_dim: 1920x1088
2009-08-24 14:20:08.728 VDP: SetVideoRenderer(xv-blit)
2009-08-24 14:20:08.729 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2009-08-24 14:20:08.772 VideoOutputXv: Chromakeying not possible with this XVideo port.
2009-08-24 14:20:08.772 Display Rect  left: -280, top: -104, width: 2240, height: 1259, aspect: 1.59925
2009-08-24 14:20:08.772 Video Rect    left: 0, top: 0, width: 1920, height: 1080, aspect: 1.33333
2009-08-24 14:20:08.772 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.774 VDP: LoadBestPreferences(1920x1088, 29.97)
2009-08-24 14:20:08.863 NVP: ClearAfterSeek(1)
2009-08-24 14:20:08.863 VideoOutputXv: ClearAfterSeek()
2009-08-24 14:20:08.863 VideoOutputXv: DiscardFrames(0)
2009-08-24 14:20:08.863 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:08.863 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-08-24 14:20:08.863 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:08.863 NVP: LoadFilters(''..) -> 0
2009-08-24 14:20:08.863 detectInterlace(Detect Scan, Interlaced Scan, 29.97, 1088) ->Interlaced Scan
2009-08-24 14:20:08.864 AFD: EIA-608 caption 1 is in the English language.
2009-08-24 14:20:08.864 AFD: EIA-708 caption service #1 is in the English language.
2009-08-24 14:20:08.864 AFD: Using ffmpeg for video decoding
2009-08-24 14:20:08.864 AFD: Looking for decoder for MPEG2VIDEO
2009-08-24 14:20:08.864 AFD: Opened codec 0xac7061e0, id(MPEG2VIDEO) type(Video)
2009-08-24 14:20:08.864 AFD: Stream #1, has id 0x52 codec id AC3, type Audio, bitrate 384000 at 0x0xac701770
2009-08-24 14:20:08.864 AFD: codec AC3 has 6 channels
2009-08-24 14:20:08.864 AFD: Looking for decoder for AC3
2009-08-24 14:20:08.864 AFD: Opened codec 0xaf5a42c0, id(AC3) type(Audio)
2009-08-24 14:20:08.864 AFD: Stream #2, has id 0x53 codec id AC3, type Audio, bitrate 192000 at 0x0xaf5ae2f0
2009-08-24 14:20:08.864 AFD: codec AC3 has 1 channels
2009-08-24 14:20:08.864 AFD: Looking for decoder for AC3
2009-08-24 14:20:08.865 AFD: Opened codec 0xac707490, id(AC3) type(Audio)
2009-08-24 14:20:08.877 NVP: Waiting for prebuffer..  7 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:09.044 VideoOutputXv: UpdatePauseFrame() AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:09.056 NVP: Waiting for prebuffer..  8 AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:09.151 RingBuf(/var/lib/mythtv/recordings/1391_20090824142005.mpg): CalcReadAheadThresh(3047934861 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-24 14:20:09.158 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-24 14:20:09.158 Opening ALSA audio device 'default'.
2009-08-24 14:20:09.185 Mixer unable to find control Master
2009-08-24 14:20:09.185 Mixer unable to find control Master
2009-08-24 14:20:09.188 NVP: Enabling Audio
2009-08-24 14:20:09.188 Dec: Selected track #1 in the English language(6647399)
2009-08-24 14:20:09.188 Dec: Selected track #1 in the English language(6647399)
2009-08-24 14:20:09.188 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-08-24 14:20:09.190 SyncPositionMap watchingrecording, from DB: 0 entries
2009-08-24 14:20:09.191 Filling position map from 0 to 53
2009-08-24 14:20:09.192 Position map filled from Encoder to: 45
2009-08-24 14:20:09.192 SyncPositionMap watchingrecording total: 4 entries
2009-08-24 14:20:09.192 SyncPositionMap, new totframes: 45, new length: 1, posMap size: 4
2009-08-24 14:20:09.192 AFD: Partial position map found
2009-08-24 14:20:09.192 AFD: Successfully opened decoder for file: "/var/lib/mythtv/recordings/1391_20090824142005.mpg". novideo(0)
2009-08-24 14:20:09.195 NVP: DoPlay: rate: 29.97 speed: 1 skip: 1 => new interval 33366
2009-08-24 14:20:09.195 Set video sync frame interval to 33366
2009-08-24 14:20:09.195 NVP: Stretch Factor 1, allow passthru 
2009-08-24 14:20:09.213 RingBuf(/var/lib/mythtv/recordings/1391_20090824142005.mpg): CalcReadAheadThresh(0 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2009-08-24 14:20:09.213 Resyncing position map. posmapStarted = 0 livetv(1) watchingRec(1)
2009-08-24 14:20:09.215 SyncPositionMap watchingrecording, from DB: 4 entries
2009-08-24 14:20:09.215 Filling position map from 46 to 54
2009-08-24 14:20:09.216 Position map filled from Encoder to: 45
2009-08-24 14:20:09.216 SyncPositionMap watchingrecording total: 4 entries
2009-08-24 14:20:09.222 VideoOutputXv: UpdatePauseFrame() LAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:09.229 NVP: Waiting for prebuffer..  9 LAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:09.363 NVP: Prebuffer wait timed out 10 times.
2009-08-24 14:20:09.363 NVP: Waiting for prebuffer.. 10 uLULAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:09.496 NVP: Waiting for prebuffer.. 11 UUUUuUULULAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:11.013 TV: CommitQueuedInput() livetv(1) qchannum() qchanid(0)
'video_output' mean = '32958.65', std. dev. = '4372.49', fps = '30.34'
2009-08-24 14:20:13.432 NVP: Changing speed to 0
2009-08-24 14:20:13.432 rate: 29.97 speed: 1 skip: 1 = interval 33366
2009-08-24 14:20:13.432 Set video sync frame interval to 33366
2009-08-24 14:20:13.475 VideoOutputXv: UpdatePauseFrame() UUUUUUUUUUuUULUUUUUUUUUUUUuAUUU
2009-08-24 14:20:13.618 DPMS Reactivated.
2009-08-24 14:20:22.653 TV: Attempting to change from WatchingLiveTV to None
2009-08-24 14:20:22.653 TV: StopStuff() -- begin
2009-08-24 14:20:22.653 TV: StopStuff(): stopping ring buffer[s]
2009-08-24 14:20:22.653 TV: StopStuff(): stopping player[s] (1/2)
2009-08-24 14:20:22.653 TV: StopStuff(): stopping recorder[s]
2009-08-24 14:20:22.653 NVP: Exited decoder loop.
2009-08-24 14:20:22.665 VideoOutputXv: dtor
2009-08-24 14:20:22.665 VideoOutputXv: DiscardFrames(1)
2009-08-24 14:20:22.665 VideoBuffers::DiscardFrames(1): UUUUUUUUUUuUULUUUUUUUUUUUUuAUUU
2009-08-24 14:20:22.665 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:22.665 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-08-24 14:20:22.665 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:22.666 VideoOutputXv: DiscardFrames(1)
2009-08-24 14:20:22.666 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2009-08-24 14:20:22.666 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:22.666 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2009-08-24 14:20:22.666 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2009-08-24 14:20:22.678 VideoOutputXv: Closing XVideo port 283
2009-08-24 14:20:23.123 TV: StopStuff(): stopping player[s] (2/2)
2009-08-24 14:20:23.160 TV: StopStuff() -- end
2009-08-24 14:20:23.161 TV: Changing from WatchingLiveTV to None
```

So I checked everything installed to do with nvidia, there is no 180.44. The kernel is definitely version 180.60. What can I do?

---

### Post by Twizzle on 2009-09-06
I recently bought this board for my HTPC and have just installed a minimal version of 9.04 and XBMC (following the guide on the XBMC forum). Part of that install is to upgrade the alsa drivers so I am running 1.0.20.

No matter what I try, I still cannot get the sound to work. I am trying for video and sound over hdmi to my TV and the only thing I can see that is different in my setup compared to the posts here is the content of my aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I seem to have an extra 'card 0' bit with VT1708B Digital.

Now I know that the sound works as I have installed Windows 7 on a partition (the RC) and sound works fine (although I had to select the Nvidia HDMI as opposed to another HDMI option (I forget which at the moment and am not logged in with it)

I wonder if this extra line is causing some sort of conflict.

I really want to get this working as I hate using Windows!

---

### Post by Cuppa-Chino on 2009-09-06
Twizzle which version of alsa have you got? you might want to consider the alsa-upgrade script.

couple of things that have caught me out in the past are:

various iec958/digital channels being muted in alsa conf / gnome sound properties, note that these might not be shown unless you "open them up" via the properties tab

---

### Post by strange. on 2009-09-26
hey guys i have a problem with my asus M3N78-EM board the usb ports seem unstable my ir receiver (mceusb2) keeps dying after an x amount of minutes and recently my usb keyboard and mouse stop after a while as well unplugging them and putting them back in dont change anything after reboot all works fine.

any ideas would be greatly appreciated if i need to add any dmesg/syslog stuff just post here and i'll put it up

all the usb stuff work in the same version of ubuntu (jaunty 32bit)
on my laptop without any problems

---

### Post by feh on 2009-10-08
To the folks running Myth successfully on this board, I have one question - do you use hibernate/sleep?

I have the same board, and was able to get everything to work properly (this was back in April/May) except hibernate/sleep. Given that my machine is a dedicated PVR, this was a deal breaker, and I resorted to Windows 7 beta.

I'd like to go back to Myth, but only if I can get hibernate to work. 

Thanks.

---

### Post by gradinaruvasile on 2009-11-30
> **zobcat said:**
> I have this same board. I've added Avenard's repo and GPG. I upgraded all the myth packages and the nvidia 180. I created my profiles according to this:
[INDENT]If you have a nVidia < 8600GT or < 9500GT, use the following profile:

<      W: 1920 H: 720, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Advanced 2X

>=    W: 0 H: 720, decoder: VDPAU, renderer: VDPAU, Deinterlacer: Temporal 2X[/INDENT]

Yet, I still get ~80% CPU when playing video. What am I doing wrong?

I have this motherboard (M3N78-VM) too. And VDPAU rocks! I played 1080p videos on a Athlon 3200+/AM2 (ancient) single core processor. Max utilisation vas 30 % (spikes), but generally about 15-20.

Ubuntu 9.04 (ALSA only)
Nvidia driver from the site (not deb) version 195.22

I tested xine and mplayer; 
Conclusions:
The Mplayer command-line version is the best. You can give it options from the command line and you will see if they are in fact applied/working/etc.
So:

Mplayer from command line with the "-vo vdpau -vc [COLOR="Red"]ffh264vdpau[/COLOR] -ao alsa" options.

The ffh264vdpau option is the key here. It forces the use of hardware accelerated decoding -the video card decodes + displays, not the CPU. Otherwise you might end up (with only the -vo vdpau option) using software decoding/hardware accelerated display. But the software decoding is a killer for CPUs. Not even an Intel Core2Duo E6550 / 2.33 GHZ / 1333 FSB with Nvidia Quadro NVS 285 (software decoding) i have at work could match the decoding speed of the IGP 8200/VDPAU/Athlon 3200+ (hardware decoding).

Also it seems you need vdpau set B to work properly (the 8200, 8300 IGPs are set B).
 

A bit off topic:The Quadro NVS 285 for some reason doesnt support hardware decoding VDPAU, despite the fact it is on the list on wikipedia. Same with NVS 135M (on DellD630). These 2 NVS models have the video out vdpau option, but dont work with ffh264vdpau. The NVS 135M seems to support it, (but it loops every about 3 seconds worth of frames while the sound plays normally - on one specific movie) - it works with another. The NVS 285 works only with xine, but it uses software decoding only.

The 8200 IGP on the other hand just rocks.

PS. I started the comp to try Karmic from live cd and the nv opensource/default driver wouldnt work with the 8200 (it was some beta or rc, the problem probably is corrected). I had to install the restricted drivers in order to see the GDM.

---

