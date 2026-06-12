---
title: "HP Compaq 2133 Mini-Note PC"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by R_U_Q_R_U on 2008-04-08
Do you think Ubuntu will run on this new mini-notebook?


[http://www.hp.com/hpinfo/newsroom/press_kits/2008/mobility/](http://www.hp.com/hpinfo/newsroom/press_kits/2008/mobility/)

[http://www.hp.com/hpinfo/newsroom/press_kits/2008/mobility/ds_HP2133Mini-NotePC.pdf](http://www.hp.com/hpinfo/newsroom/press_kits/2008/mobility/ds_HP2133Mini-NotePC.pdf)

[http://www.hp.com/hpinfo/newsroom/press_kits/2008/mobility/images/HP7872.jpg](http://www.hp.com/hpinfo/newsroom/press_kits/2008/mobility/images/HP7872.jpg)

---

### Post by kerry_s on 2008-04-08
wow, that's pretty.

it says it can run linux in the pdf, so you should be fine with any linux.

---

### Post by sriram.venkataramani on 2008-04-09
The press release mentions a 64 GB SSD. I don't see that as any of the storage options when I try to buy the laptop.

---

### Post by steelisreal on 2008-04-10
i am ordering mine tonight so after I get it I will be more than happy to let you know how the ubuntu install goes.

---

### Post by rimiko on 2008-04-17
The livecd works!  You must use the xforcevesa option with the 8.04 beta and a USB stick of the livecd.

---

### Post by rimiko on 2008-04-22
A follow-up note for mini-note owners who want to run Ubuntu:

The blank screen apparently is a known bug in Via Chrome laptops.  Use the xforcevesa kernel option to get the livecd working and boot into X.  If you switch to openchrome after installing, set Option "ForcePanel" in your xorg.conf to force X to drive the LCD panel first.  Acceleration (if there is any) seems slower than in the original Suse installation, but my memory is hazy.   

Wireless.  b43, in its current state, is a waste of your time.  Get an XP (not Vista) Broadcom driver off hp.com and use ndiswrapper instead.  Don't forget to add modprobe -r ssb and modprobe ndiswrapper to your /etc/rc.local file.

---

### Post by bmccann on 2008-04-23
Thanks, Rimiko, for the advice about 'xforcevesa'. It was a lifesaver.

I successfully used the Ubuntu Hardy 8.04 live CD to resize the existing Suse partition and add a couple more partitions for Ubuntu and /home. The installation went well until the mini-note hung during "Detecting Hardware" at 90%. (Note, I'm actually using Xubuntu but I doubt that matters. Its the same Ubuntu installer, right?).

I have left it that way for maybe 10 minutes and then gave up and turned the box off. (It was completely unresponsive to the touch pad and keyboard).

Do you have any suggestions on what I might do to fix this?

Or, given my Xubuntu partition has all the files now, is there an easy way to manually complete the installation? I'm considering manually editing the GRUB menu on my Suse partition to point to the vzImage and initrd files on the Ubuntu partition. I'll keep the existing Suse entries too so I can dual boot either Suse 10 or Ubuntu.

---

### Post by bmccann on 2008-04-23
The GRUB menu.lst supplied with the Suse Enterprise 10 on the Mini-note included:

  ide0=noprobe ide1=noprobe ide2=noprobe ide3=noprobe

as kernel parameters. So, I added those, plus xforcevesa, to the kernel options of the Xubuntu 8.04 Live CD kernel options. (I don't think the HP-2133 has any IDE interfaces. Its disk drive uses a SCSI driver).

The install then completed successfully. 

Its possible the first failure was a glitch, and that these extra options were irrelevant, but you can try them if you also have problems with the install hanging during 'Detecting Hardware'.

Now, to go get that wireless interface working...

---

### Post by redhed on 2008-04-23
I was able to install from the 8.04 LiveCD just by adding the xforcevesa kernel parameter. (I did not try without that parameter)

Currently my system is doing an update to get the latest packages.

I am still using vesa for video, but plan to switch to openchrome after the updates finish. I plan to use the openchrome.sh script which automates the install. It seems like it does the same things I would do manually, so I am going to give it a try. I will just need to make the change to xorg.conf after it is done to force it to use the laptop panel as default.

Then I will get to work on wireless.

I also need to get a large SDHC or maybe an ExpressCard flash drive (or CF in Expresscard adapter), so I can move my home directory there.

I have the least expensive 2133. It came with 512MB of RAM and the 4GB SSD. I have not cracked it open to look at the insides yet, but will as soon as the 2GB RAM chip I ordered comes in. I ordered the cheapest model since I figured it would be fun to upgrade and I wanted to see what the SUSE install and 4GB SSD would be like. I also figure the battery will last longer since it does not have a mechanical hard disk.

My wife really likes it and wants me to get her one. The only issue is she will probably have to use some form of windows. Her goal is to videochat using MS Messenger. Perhaps I can get her to switch to skype video chat (assuming it works on the mini-note in Ubuntu).

---

### Post by redhed on 2008-04-23
I used ndiswrapper for wireless. Here is a tutorial if you need it: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

The webcam works with skype and amsn. Maybe my wife could use this laptop.

The webcam is very smooth and looks great. Overall the laptop is a little slow, but not terrible. Basically the issue is with disk access. so for web surfing it works great. Installations and opening apps takes a little longer than I would like, but once they are open they run well.

---

### Post by warder on 2008-04-23
n00b question...how do I add that flag?

---

### Post by redhed on 2008-04-24
Insert the LiveCD and get to the menu with the splash screen. Choose "Try Ubuntu without any change to your computer" and click f6. Clicking F6 will bring up the Boot Options. Add the word xforcevesa to the end of the line and hit enter to start the LiveCD boot process.

Optionally, I think you can also press f4 and choose to start in Safe Graphics mode, that may accomplish the same thing.

---

### Post by redhed on 2008-04-24
I upgraded the RAM to 2GB today. It was a rather painless process. I had to remove three phillips head screws from under the battery compartment, so I could lift off the keyboard. This revealed the memory slot and ssd. I popped oout the 512MB chip and replaced it with a 2GB (DDR2 667MHz) chip.

The SSD is somewhat funny. The board looks as if it is the same one that would be used for a 32GB SSD, but it only has two flash chips attached to the board (as opposed to 16). There are 7 empty spots on either side of the board where the additional flash chips would reside. It takes up the same space as a normal 2.5" HD or SSD although it is mostly a blank circuit board.

Since I now have 2GB of RAM, I decided to get rid of my swap partition and see if it causes any problems. I also moved /home to an SDHC card that will always be in the built-in SD slot. If I determine that SWAP is necessary I will make some space for it on the SDHC card, but at this point the system runs fine without it.

I have a standard install of Ubuntu 8.04 on the SSD. The SSD is formatted to 3.73GB and 2.44GB are free.

I do have some remaining issues with power save features, but that seems to be the case on every laptop I have installed linux on. Basically suspend mode is inconsistent, a few times when I woke the system up the video was hung requiring s shutdown and reboot (although a restart of X sometimes works). Hibernate also hangs (even before I removed swap). Luckily it boots up and shuts down relatively quick, so this is not a major issue. On the good side, the screen brightness does lower properly when I am on battery power and the system is idle. I'm not exactly impressed by battery life, but I haven't tested it much. The system has only been unplugged for about an hour at this point. Since I have a few HP laptops, there always seems to be a power cord around.

---

### Post by rdrandal on 2008-04-24
Using the 8.04 Live Disk and xforcevesa kernel option I had my Mini-Note running Ubuntu. I plan to use the install from the Ubuntu desktop to install the OS onto my HDD. Do I need to do anything special concerning the graphic driver during the actual install? After I have the system running of HDD I will install openchrome. Have you encountered any special problems with using openchrome or problems with WiFi? Anything you care to share is appreciated.

---

### Post by sthoms on 2008-04-25
OpenChrome script worked very well. However, the problem remains that I am not able to make the external screen run. Any suggestions?

Also, sound capture via internal mic is not working in the mixer and in Skype ...

---

### Post by redhed on 2008-04-25
> **rdrandal said:**
> Using the 8.04 Live Disk and xforcevesa kernel option I had my Mini-Note running Ubuntu. I plan to use the install from the Ubuntu desktop to install the OS onto my HDD. Do I need to do anything special concerning the graphic driver during the actual install? After I have the system running of HDD I will install openchrome. Have you encountered any special problems with using openchrome or problems with WiFi? Anything you care to share is appreciated.
I did not have to do anything special during the install, since the installer knows to use VESA for video.

I used openchrome for video, but you could also try via.

My problems with openchrome are with suspend/hibernate. I have not tried to troubleshoot it yet. It may have something to do with the SD card that I have mounted as my /home partition.

WiFi works well, but it also has some problems with suspend/hibernate. I cannot get WPA to work after I wake the system up. WEP works fine after I wake the system though.

---

### Post by redhed on 2008-04-25
> **sthoms said:**
> OpenChrome script worked very well. However, the problem remains that I am not able to make the external screen run. Any suggestions?

Also, sound capture via internal mic is not working in the mixer and in Skype ...
I have not tested an external monitor yet, but may get a chance this afternoon.

I tried the video in amsn and skype, which worked, but did not try the audio.

---

### Post by bmccann on 2008-04-26
Two questions:
[LIST]
[*]How much faster is OpenChrome versus the VESA Video Driver?
[*]How do we get CPU frequency scaling to work?
[/LIST]
I'm curious about the first because I'm lazy. :)

The second is more annoying. I've tried to modprobe acpi-cpufreq and longhaul and both return with an 'No such device' error from modprobe. Dmesg doesn't provide any output from the module and Google hasn't helped.

I installed Ubuntu to dual-boot with the SUSE Enterprise Linux that came from the factory so I booted to that and poked around. It **does** have the acpi_cpufreq module installed and it is successfully uses the cpufreq_ondemand frequency govenor. (It runs at 800 MHz by default and jumps to 1200 MHz under load). The SUSE kernel is 2.6.16.54-0.2.5-default.

Any ideas how to get CPU scaling to work with the HP-2133 and (X)Ubuntu?

I'd like to have it to stretch the battery life a bit.

(Update) There may be an issue using acpi-cpufreq with the Hardy kernel. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201890/comments/12](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201890/comments/12).

---

### Post by sthoms on 2008-04-26
I experienced subjectively better performance using OpenChrome. Most notably, video playback in VLC of MPEG4 was finally smooth, though there seems to be a bug when going full screen that leaves a small area around the position of the mouse pointer black.

---

### Post by sthoms on 2008-04-27
to fix the CPU scaling bug:

go to your grub menu file in boot/grub/menu.lst

Edit the file, and towards the bottom of it, and add  argument

acpi_osi="!Windows 2006" 

to the kernel line (right after "ro quiet splash"

Here is more information: 

[https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/177076](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/177076)

---

### Post by wieman01 on 2008-04-27
Is this laptop available in Europe yet?

---

### Post by mivo on 2008-04-27
> **wieman01 said:**
> Is this laptop available in Europe yet?

Not in Germany at least. I checked the other day and couldn't find out anything about it.

---

### Post by Troyzino on 2008-04-27
Thanks to all the good tips here I've managed to get my mini-note mostly working with Ubuntu.

I have the cheapest mini-note with 1GHZ, 4GB SSD, but I upgraded the memory from 512MB to 1GB.

+ Wifi works with NDISWrapper (and the light on the front even works which didn't work with SUSE).

+ Laptop screen is working with openChrome at 1280x768 and looks good.

+ CPU Scaling works now

- External monitor doesn't work, but I can live with that.

- Sound still isn't fully working. I get sound output from the speakers and from the headphone jack, but it doesn't mute the external speakers when I plug in the headphones. I don't think the microphones are working either.

I think the answer to the sound problem might be something like here:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)
Except my chip isn't listed:

:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices ID 194a

I've tried so far a few random choices for:
options snd-hda-intel model=???
Negative for hp, laptop. It sucks that each change requires a lengthy reboot.

I blew away SUSE. I'm wondering if the right one might have been set in the /etc/modprobe.d/alsa-base file. Can someone check?

Anybody else figured out how to get sound completely working? As it is, it won't do. I need the externals to be muted when using headphones (so as not to disturb others), and I need the mic to work for conferencing. I don't have a plugin mic, but maybe that works. If so, I can live with that.

Thanks for all the guidance so far provided here. I'm new to linux and Ubuntu so I've been struggling nonstop since I got this thing.

---

### Post by wieman01 on 2008-04-27
> **mivo said:**
> Not in Germany at least. I checked the other day and couldn't find out anything about it.
Schade. I was looking forward to it.

---

### Post by makkus on 2008-04-28
A quick questions for those of you who have one of these neat little toys:

Are video skype calls really working all right on the 1.2 Ghz version? Or is the video/audio rather choppy?

You guys reckon the 1.6 Ghz version is notably better performing?

Also, how well does it play normal xvid videos?

Cheers,
Makkus

---

### Post by bmccann on 2008-04-28
The headphone mute problem is getting annoying. I set up my HP2133 to dual boot between the original Suse install and Xubuntu Hardy Heron. The Suse install properly mutes the speakers when headphones are plugged in. Xubuntu doesn't.

I booted the Suse code to see if I could identify a critical difference between the two. I haven't found anything useful (and I still have the problem) but I thought I'd document what I found:

**lsmod | egrep "snd|sound|alsa"**
snd_pcm_oss            43008  0 
snd_mixer_oss          16256  1 snd_pcm_oss
snd_seq                46832  0 
snd_seq_device          7948  1 snd_seq
snd_hda_intel          19864  3 
snd_hda_codec         217344  1 snd_hda_intel
snd_pcm                79752  4 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_timer              20868  3 snd_seq,snd_pcm
snd                    50948  12 snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
soundcore               8672  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm

**cat /proc/asound/card0/codec#0 | grep Codec**
Codec: Analog Devices AD1984A

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**find . -type f -print | xargs grep -i snd-hda-intel**
./sysconfig/hardware/hwcfg-vpid-1106-3288-103c-3030:MODULE='snd-hda-intel'
./modprobe.d/sound:options snd-hda-intel enable=1 index=0
./modprobe.d/sound:alias snd-card-0 snd-hda-intel
./modprobe.d/sound:alias sound-slot-0 snd-hda-intel
./modprobe.d/blacklist:blacklist snd-hda-intel

**strings snd-hda-intel.ko | grep -i verm**
vermagic=2.6.16.54-0.2.5-default 586 REGPARM gcc-4.1


When I run with Xubuntu, I see a couple of interesting differences. First, the codec model number is different:

**cat /proc/asound/card0/codec#0 | grep Codec**
Codec: Analog Devices ID 194a

and second, the HDA driver is in a 'generic' mode instead of recognizing a specific Analog Devices codec:

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I also tried a bunch of different snd-hda-intel options, none of which worked:

# BEM 04/27/08 (failures so far)
# options snd-hda-intel position_fix=1 model=laptop 
# options snd-hda-intel model=laptop 
# options snd-hda-intel enable=1 index=0

# BEM 04/28/08
# options snd-hda-intel model=laptop-automute
# options snd-hda-intel probe_mask=8 model=lenovo
# options snd-hda-intel model=lenovo
# options snd-hda-intel model=hp
# options snd-hda-intel model=auto
# options snd-hda-intel model=6stack

Note that the 'enable=1 index=0' options mirrors my Suse configuration. No joy.

I saw, but didn't record the URL, a post saying the snd-hda-intel driver is busted in 2.6.24. That may be worth pursuing if anyone has time.

Post to here if there is other useful data I can pull from the Suse environment. As I said, it works fine. I just don't want use KDE on this little laptop. Too slow...

---

### Post by wieman01 on 2008-04-28
> **makkus said:**
> A quick questions for those of you who have one of these neat little toys:

Are video skype calls really working all right on the 1.2 Ghz version? Or is the video/audio rather choppy?

You guys reckon the 1.6 Ghz version is notably better performing?

Also, how well does it play normal xvid videos?

Cheers,
Makkus
Skype video works great on my Sony Vaio with 1.2 Ghz, even when it is in power saving mode running at 0.6 Ghz. No problem I reckon.

---

### Post by rdrandal on 2008-04-28
" am still using vesa for video, but plan to switch to openchrome after the updates finish. I plan to use the openchrome.sh script which automates the install. It seems like it does the same things I would do manually, so I am going to give it a try. I will just need to make the change to xorg.conf after it is done to force it to use the laptop panel as default."

I'm about to install OpenChrome and am wondering if the openchrome.sh script worked for you or if you needed to manually install. Thanks

---

### Post by sthoms on 2008-04-28
From what I remember, the openchrome script worked for me.

I also had to set Virtual 1280 768 in Xorg.conf under SubSection Display in addition to ForcePanel or else the Ubuntu Start login screen would not display correctly.

---

### Post by bmccann on 2008-04-29
Thanks, that had puzzled me too.

> **sthoms said:**
> From what I remember, the openchrome script worked for me.

I also had to set Virtual 1280 768 in Xorg.conf under SubSection Display in addition to ForcePanel or else the Ubuntu Start login screen would not display correctly.

I'm running Hardy Heron and I found that the openchrome driver was installed by APT. (I forgot if I did so manually or if it was automatic during the Xubuntu install). I wonder whether your 'openChrome.sh' driver version is the same as mine? I have version 1:0.2.901-0Ubuntu4 from Hardy.

I ran two very informal benchmarks and I've decided to keep the Vesa driver instead of openChrome.

[LIST]
[*]Glxgears runs 150 FPS with VESA buit only 100 FPS with openChrome (OC). OC was also very inconsistent.
[*]xengine ran almost SEVEN times faster with VESA (10000 FPS instead of 1500 FPS).
[/LIST]

Could someone who is using the 'openChrome.sh' version of OpenChrome install and run 'xengine' and report your results. I doubt I'll change my mind but it would be useful data to report here. (I had openChrome lock up my laptop after running xengine so I'm not too impressed so far...)

FWIW, YMMV...

---

### Post by allinurl on 2008-04-29
for those who are trying to setup their video card on the Mini HP-2133, there is good news, **VIA **has joined the open source world and now is proving the drivers for it, you can **download** the driver [here]("http://linux.via.com.tw/support/downloadFiles.action"), to install it just follow the instructions, the only thing is that I had to use the same xorg.conf that it came with suse, besides that everything is working fine. (direct rendering yes).

---

### Post by sthoms on 2008-04-29
Can you post your Suse xorg.conf here, please? I am getting screen test loops with colors changing etc upon reboot, so it is seemingly about the way the Via installer modifies the xorg.conf. Thanks a bunch

---

### Post by allinurl on 2008-04-29
attached the xorg.conf. With this should work

---

### Post by sthoms on 2008-04-30
Thank you, this worked very nicely. 

I have an external monitor hooked up, but it only displays at the laptop widescreen resolution. 

I have added new Monitor and Screen sections. However, the external monitor keeps defaulting to 1280x768 instead of 1280x1024, as I want it to. Do I need to change settings in the Device section?

Also, how can I make the configuration more graphical, via Preferences - Screen Resolution?

---

### Post by Tavorisch on 2008-05-02
Whoazuh! hows the sound issue coming along, also, so for the record, that driver a couple posts above works? i saw direct rendering, so,?desktop effects? i've been really thinking about getting one of these, but ubuntu is a must have.. the fact that it comes with linux it really dissapoints me that there is this much trouble. would think they would ahve put an atheros wifi card, etc etc.

---

### Post by catdriver97 on 2008-05-03
First off, I want to thank everybody who posted advice in this thread.  I never would have got my Mini-Note going without your help.

To pass that along to others, I've compiled the wisdom of this thread and the little bit of Hardy testing I've done into a Wiki page on the Ubuntu LaptopTestingTeam site.

You can find it [here]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133").  

I'll do my best to keep it up to date as we get more info on the headphone jack bug.

Thanks again.

---

### Post by sthoms on 2008-05-04
It is not only the headphone jack issue ... also the microphone is not recognized properly. 

Meanwhile, when using Skype and video-in-video there (my own plus the main video), I get flickering picture with the Via Driver. No documentation at all from Via, which makes me question their commitment to Linux.

---

### Post by bmccann on 2008-05-04
I've made some progress on the headphone jack issue. 

If you make the patch I show below, and follow the installation directions, you'll end up with NO (I repeat NO) sound coming out of your speakers but the headphones will work. I haven't figured out why the auto-mute doesn't work but I've burned too much time looking so I've wimped out and just disabled the speakers instead. This suffices for me because I will never use sound w/o headphones anyway.

To start, you need to get the source package and install a number of other packages to support compilation of the source code. I put the source code under my home directory in ~/src/Hardy, installed a missing package required to download the source, got the source, and then installed all the other packages required to build the source.

In a console terminal window, enter:
[INDENT]
mkdir -p ~/src/Hardy
cd ~/src/Hardy

sudo apt-get install dpkg-dev
apt-get source linux-sound-base

sudo apt-get build-dep linux-sound-base
[/INDENT]

Now configure and build the sound system:
[INDENT]
cd alsa-driver-1.0.16
./configure
make
[/INDENT]

This verifies your build environment is OK.  There should be no errors and the last message coming out of 'make' will be:
[INDENT]
ALSA modules were successfully compiled.
[/INDENT]

At this point you should have a sound driver that is identical to the one already installed. Install the driver you just built to verify it works. Note you should back up the old driver in case this all blows up:
[INDENT]
sudo mv /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko.save

sudo cp pci/hda/snd-hda-intel.ko /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
[/INDENT]

At this point, you can reboot and double check your sound still works. It should. If not, just put the old driver back and stop. The remaining steps won't work if the driver's not working (with speakers and headphone). To restore the old driver:
[INDENT]
sudo cp /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko.save /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
[/INDENT]

Finally, to actually disable the speakers, 'cd' to the directory where you installed the source (i.e. ~/src/Hardy) and edit (using your favorite editor) the file alsa-kernel/pci/hda/hda_generic.c:

[INDENT]
cd ~/src/Hardy/alsa-driver-1.0.16/
vi alsa-kernel/pci/hda/hda_generic.c
[/INDENT]

Down around line 414, you need to change:

[INDENT]
        /*
         * Look for the output PIN widget
         */
        /* first, look for the line-out pin */
        node = parse_output_jack(codec, spec, AC_JACK_LINE_OUT);
        if (node) /* found, remember the PIN node */
[INDENT]
                spec->out_pin_node[0] = node;
[/INDENT]
        else {
[INDENT]
                /* if no line-out is found, try speaker out */
                node = parse_output_jack(codec, spec, AC_JACK_SPEAKER);
                if (node)
[INDENT]
                        spec->out_pin_node[0] = node;
[/INDENT]
[/INDENT]
        }
[/INDENT]

to the following (bold face shows inserted text):
[INDENT]
        /*
         * Look for the output PIN widget
         */
        /* first, look for the line-out pin */
        node = parse_output_jack(codec, spec, AC_JACK_LINE_OUT);
        if (node) /* found, remember the PIN node */
[INDENT]
                spec->out_pin_node[0] = node;
[/INDENT]
        else {
[INDENT]
[B]#if 0
/* DISABLE SPEAKERS ON HP-2133 */[/B]
                /* if no line-out is found, try speaker out */
                node = parse_output_jack(codec, spec, AC_JACK_SPEAKER);
                if (node)
[INDENT]
                        spec->out_pin_node[0] = node;
[/INDENT]
**#endif**
[/INDENT]
        }
[/INDENT]

Now build and install the modified driver
[INDENT]
cd ~/src/Hardy/alsa-driver-1.0.16
make
sudo cp pci/hda/snd-hda-intel.ko /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
[/INDENT]

Now **reboot**. If everything worked, then you'll have no speakers but your headphones will work correctly.


For the record, I tried to fix this correctly by addressing one obvious difference between the Suse boot and Ubuntu. The Suse Linux detects the sound codec as an Analog Devices 1986A. The Ubuntu kernel doesn't, and instead tries to use a 'generic' driver. All of the postings about speaker auto-mute relied on passing a 'model=' selector in the /etc/modprobe.d/alsa-base file line for 'options snd-hda-intel'. I don't think any of those experiments will work unless the driver knows the codec is an 1986A.

Unfortunately, the codec reported by Ubuntu is "Analog Devices ID 194a". This isn't known to the sound driver so it falls back to 'generic'. I tried adding an entry mapping the 194a device type to 1986a by inserting the following in alsa-kernel/pci/hda/patch_analog.c:

[INDENT]
/*
 * patch entries
 */
struct hda_codec_preset snd_hda_preset_analog[] = {
[INDENT]
        { .id = 0x11d41882, .name = "AD1882", .patch = patch_ad1882 },
        { .id = 0x11d41884, .name = "AD1884", .patch = patch_ad1884 },
        { .id = 0x11d41981, .name = "AD1981", .patch = patch_ad1981 },
        { .id = 0x11d41983, .name = "AD1983", .patch = patch_ad1983 },
        { .id = 0x11d41984, .name = "AD1984", .patch = patch_ad1984 },
**        { .id = 0x11d4194a, .name = "AD1986A", .patch = patch_ad1986a },**
        { .id = 0x11d41986, .name = "AD1986A", .patch = patch_ad1986a },
        { .id = 0x11d41988, .name = "AD1988", .patch = patch_ad1988 },
        { .id = 0x11d4198b, .name = "AD1988B", .patch = patch_ad1988 },
        {} /* terminator */
[/INDENT]
};
[/INDENT]

I couldn't get this to work with several attempts of 'model=' using models of hp, laptop, and 3stack. (The driver kept reporting there were zero volume steps for various volume controls).

If someone wants to investigate this for ubuntu or alsa then that's probably a cleaner fix because then auto-mute will work.

---

### Post by catdriver97 on 2008-05-04
The [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") has been updated to reflect the video flicker on Skype (confirmed locally with my 2133) the microphone issues (also confirmed locally) and to reference the above speaker workaround.

For whatever it's worth, here's Analog's Official Site for the AD1986A codec:

[http://www.analog.com/en/prod/0,2877,AD1986A,00.html]("http://www.analog.com/en/prod/0,2877,AD1986A,00.html")

Interestingly the title reads:  AD1986A AC97 2.3 and HD Audio SoundMAX audio codec **w/jack sensing**

CORRECTION:  It's actually the AD1984A according to the [HP Driver Site]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687084&prodNameId=3687085&swEnvOID=2094&swLang=8&mode=2&swItem=ob-59522-1")

---

### Post by Ender_chan on 2008-05-05
I have looks for an openchrome.sh file for a while and I don't think I have found the one that works for the mini note. I found a openchrome-stable.sh but not a openchrome.sh. After running the openchrome-stable.sh my vidoe didn't work and had to go back to my last good xorg.conf file.  Can someone post a link of where they got their openchrome.sh file and a copy of the xorg.conf that they got to successfully work. Thank you for your time.

---

### Post by ldrn on 2008-05-05
I used this one:
[http://linux.via.com.tw/support/beginDownload.action?eleid=2&fid=2]("http://linux.via.com.tw/support/beginDownload.action?eleid=2&fid=2")

From this page:
[http://linux.via.com.tw/support/downloadFiles.action]("http://linux.via.com.tw/support/downloadFiles.action")

Make sure to select "Ubuntu 8.04 LTS" rather than Suse 10.0 SP1 if you use the second link.


After installing, my screen cycled through multiple colors and did not work until I replaced my xorg.conf file with the one posted by allinurl in this thread:
[http://ubuntuforums.org/showpost.php?p=4837833&postcount=33]("http://ubuntuforums.org/showpost.php?p=4837833&postcount=33")

I just replaced xorg.conf completely with that one and it worked. (I tweaked a few settings later for my personal preferences.)



I've been trying to follow in bmccann's footsteps this weekend... geeze. x_x  It has been very frustrating. I tried three different versions recompiling, tried all the tweaks he did except the disabling speakers one in hopes it'd be different on the head code... my best luck came when I downloaded the source for the debian Lenny version (since I have a Lenny machine) and recompiled/packaged for Hardy then installed those and edited modules.dep; I still had no sound, but kmix -- after throwing an error I wasn't quick enough to catch -- "fell back" to the Analog Devices 1986A.  Unfortunately, no sound with Alsa (nothing ran, same errors as earlier) or with artsd. Sigh... it's very frustrating.

---

### Post by allinurl on 2008-05-05
I've found this wiki under Gentoo, he seems that he got to work the sound under the 2133

[http://gentoo-wiki.com/HARDWARE_HP_2133_Mini-Note_PC](http://gentoo-wiki.com/HARDWARE_HP_2133_Mini-Note_PC)

If it's really working we could take some hints from there.

---

### Post by ldrn on 2008-05-05
I saw that, too -- I'm not entirely familiar with Gentoo, but it looks like he's just building new Alsa drivers from the development versions.

I've tried that a few times, too... no luck yet. I think I must be doing something wrong with the error messages alsamixer gives me when I try to run it; I forget exactly what it said, but when I looked it up on google people thought it was the result of a version mismatch between parts of alsa.

I'll write it down when my latest attempt finishes compiling. ;)

Edit: 
Ah, there it is:
function snd_ctl_open failed for default: No such file or directory

Module assistant didn't do the trick, either.

---

### Post by munkymac on 2008-05-06
> **rimiko said:**
> A follow-up note for mini-note owners who want to run Ubuntu:

Wireless.  b43, in its current state, is a waste of your time.  Get an XP (not Vista) Broadcom driver off hp.com and use ndiswrapper instead.  Don't forget to add modprobe -r ssb and modprobe ndiswrapper to your /etc/rc.local file.
Regarding Ndiswrapper--While i'm not running on a mininote, I have been using an HP the whole time I've been using linux, and i have found that even with ndiswrapper, sometimes it just doesn't work. In the end, any time i upgrade, i've just said "screw it" and installed WICD straight off the bat, replacing network-manager. On Ubuntu Feisty, Ubuntu Gutsy, and now Xubuntu Hardy, this has done the trick with no muss and no fuss. I'm betting it's at least worth a shot on the Mininote.

---

### Post by symbiat on 2008-05-07
Ive managed to get Xubuntu up and running on my Mini-Note. The VIA Chrome driver install was flawless once the right xorg.conf was installed.

Im having a very frustrating time with wireless and ndiswrapper. I followed the how-to, meticulously, twice, and its still not working. Network Manager shows the heading 'Wireless Networks' but shows no access points underneath (Im surround by at least 10 access points so that's not right. And my Nokia N810 web tablet works just fine so I know its not the access point that's the problem).

I tried telling Network manager to manually connect to my access point - after entering all the network details the animation 'spins' for a few minutes before disappearing and Im still not connected.

Would be grateful for any troubleshooting ideas...

---

### Post by stormbreaker on 2008-05-07
Hey guys, im thinking of buying a HP2133 when they come out in australia. What i would be interested in knowing is has anyone installed ubuntu on one of the vista 2133's? I was thinking of getting the AT model I think it is and downgrading it to XP Pro, from there I would either be installing ubuntu on it or even dual booting XP and ubuntu. Anyone tried this?

---

### Post by bmccann on 2008-05-08
I tried building ALSA from scratch as well and I had some undefined symbol reported when I tried to load the driver. (I forgot which). That's when I decided to download the linux-sound source for Hardy directly from ubuntu. They may have patched it to work with their kernel.

This limits our options unless someone wants to apply the patches in the package source to the latest ALSA driver.

> **ldrn said:**
> I saw that, too -- I'm not entirely familiar with Gentoo, but it looks like he's just building new Alsa drivers from the development versions.

I've tried that a few times, too... no luck yet. I think I must be doing something wrong with the error messages alsamixer gives me when I try to run it; I forget exactly what it said, but when I looked it up on google people thought it was the result of a version mismatch between parts of alsa.

I'll write it down when my latest attempt finishes compiling. ;)

Edit: 
Ah, there it is:
function snd_ctl_open failed for default: No such file or directory

Module assistant didn't do the trick, either.

---

### Post by symbiat on 2008-05-08
> **Ender_chan said:**
> I have looks for an openchrome.sh file for a while and I don't think I have found the one that works for the mini note. I found a openchrome-stable.sh but not a openchrome.sh. After running the openchrome-stable.sh my vidoe didn't work and had to go back to my last good xorg.conf file.  Can someone post a link of where they got their openchrome.sh file and a copy of the xorg.conf that they got to successfully work. Thank you for your time.

Just wondering why you're using openchrome instead of the VIA driver? AFAIK, openchrome doesn't support any 3D or compositing but the VIA driver does. Ive been using the VIA driver without any problems.

---

### Post by symbiat on 2008-05-08
I have a backup of the SuSE partition before I wiped it and installed Xubuntu. Just wondering if anyone can help me get WiFi working? Maybe the SuSe files would be useful to look at, but I dont know where to start.

---

### Post by symbiat on 2008-05-08
I made note of the device list, modules, kernel config and processes under SuSE too. They are available online:

[Devices & Module List]("http://docs.google.com/Doc?id=dfrs48gm_8cc8jmqfc")

[Kernel Configuration]("http://docs.google.com/Doc?id=dfrs48gm_10hmchv4fh")

[Process List]("http://docs.google.com/Doc?id=dfrs48gm_118pngnffv")

---

### Post by allinurl on 2008-05-08
This is what I did to get my wireless:

```
cd Desktop/
mkdir wireless/
sudo apt-get update
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
sudo nano /etc/modprobe.d/blacklist
add this -> blacklist b43
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.52.tar.gz
cd ndiswrapper-1.52/
make distclean
make
sudo make install
cd ..
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

I think that should work for you. Let me know!

---

### Post by ldrn on 2008-05-08
I don't think it was patched by the Ubuntu packagers; I was able to download, recompile and repackage, and use the Debian version.  It functions the same way, despite being 1.0.16 instead of 1.0.15.  

I tried your suggested fix as well (modifying alsa-kernel/pci/hda/patch_analog.c) and it failed differently than it did when modifying the same file with the Ubuntu source; Alsamixer will not work and there is no sound, but kmix reports the correct analog devices AD1986A, with the correct volume sliders (I believe.) Still no sound, though.

I am wondering if perhaps the Hardy audio problem is separate from the one Gentoo has;. I would switch distros on the Mini Note after all this work, but Via has only posted drivers for a very old version of SuSE and Hardy. 

> **bmccann said:**
> I tried building ALSA from scratch as well and I had some undefined symbol reported when I tried to load the driver. (I forgot which). That's when I decided to download the linux-sound source for Hardy directly from ubuntu. They may have patched it to work with their kernel.

This limits our options unless someone wants to apply the patches in the package source to the latest ALSA driver.

---

### Post by bmccann on 2008-05-08
Ldrn, if you decide to try my sound driver fix again, and it fails, then post what you're seeing. I'll try to help troubleshoot it. I want my 'recipe' to be accurate so it works for others including the noobies.

---

### Post by ldrn on 2008-05-08
Thank you! I appreciate it... I meant not the actual fix but the one you thought would be a more correct way, though; I haven't taken the plunge and gone for the headphone fix yet. I want speakers AND headphones; I'm pretty greedy. ;)

I am seriously considering applying the fix, then trying to make a script to switch modules on the fly in order to manually switch between headphones and speakers; while I want microphone support, I don't really need it -- I probably wouldn't use it anyway.

> **bmccann said:**
> Ldrn, if you decide to try my sound driver fix again, and it fails, then post what you're seeing. I'll try to help troubleshoot it. I want my 'recipe' to be accurate so it works for others including the noobies.

---

### Post by catdriver97 on 2008-05-10
Interestingly, [HP's official driver site]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687084&prodNameId=3687085&swEnvOID=2094&swLang=8&mode=2&swItem=ob-59522-1") lists the audio as an ADI SoundMAX AD**1984**A.

---

### Post by ldrn on 2008-05-11
I gave up. I installed OpenSuSE 10.3 to get sound working.

It doesn't. :confused:  The version of SuSE that ships with the mini note seems dated; is this a bug introduced with newer versions of Alsa or the kernel? If so, why can Gentoo avoid them?

---

### Post by bmccann on 2008-05-11
> **catdriver97 said:**
> Interestingly, [HP's official driver site]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687084&prodNameId=3687085&swEnvOID=2094&swLang=8&mode=2&swItem=ob-59522-1") lists the audio as an ADI SoundMAX AD**1984**A.

I googled 'alsa ad1984a driver' and eventually found the following patch:

[http://patches.ubuntu.com/a/alsa-driver/extracted/post_16_20080307.patch]("http://patches.ubuntu.com/a/alsa-driver/extracted/post_16_20080307.patch")

This looks promising because it adds code for a new AD1884A driver which is apparently compatible with the AD1984A used on the Mini-note. Most importantly, the set of preset devices now includes the 0x11d4194a device type reported on the HP2133:

```

 struct hda_codec_preset snd_hda_preset_analog[] = {
+	{ .id = 0x11d4184a, .name = "AD1884A", .patch = patch_ad1884a },
 	{ .id = 0x11d41882, .name = "AD1882", .patch = patch_ad1882 },
+	{ .id = 0x11d41883, .name = "AD1883", .patch = patch_ad1884a },
 	{ .id = 0x11d41884, .name = "AD1884", .patch = patch_ad1884 },
**+	{ .id = 0x11d4194a, .name = "AD1984A", .patch = patch_ad1884a },**
+	{ .id = 0x11d4194b, .name = "AD1984B", .patch = patch_ad1884a },
 	{ .id = 0x11d41981, .name = "AD1981", .patch = patch_ad1981 },
 	{ .id = 0x11d41983, .name = "AD1983", .patch = patch_ad1983 },
 	{ .id = 0x11d41984, .name = "AD1984", .patch = patch_ad1984 },

```

It looks like this patch just needs to be applied to ALSA 1.0.16 and then built. I'll try this sometime this week but if someone wants to try it sooner then hopefully this posting will get you started.

---

### Post by ldrn on 2008-05-11
YES! :)  That is *wonderful*, awesome find, thanks Bmccann & Catdriver; I tried this and can confirm that this works as far as adding more options to alsamixer and the like, and detecting when the headphones are unplugged. I was unable to get the built in microphone to work. 

I know there are things very wrong with this way of doing it -- but I don't care that much because it worked. ;) This is what I did
* Downloaded the source package for alsa-driver:
```
sudo apt-get source alsa driver

```* Downloaded the latest bazaar patches:
```
sudo apt-get install bzr
bzr branch http://bazaar.launchpad.net/~ubuntu-core-dev/alsa-driver/ubuntu.new
sudo cp -r * ubuntu.new/* alsa-driver-1.0.16/debian/

```Tried to make packages:
```
cd alsa-driver-1.0.16
sudo debuild -us -uc
```
Found the packages did not contain the new drivers. Researched how to make them with kpkg, tried it, failed, did ```
this:
sudo ./configure
sudo make
sudo install checkinstall 
sudo checkinstall
```
After poking around after a reboot:```

sudo mv /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver /lib/modules/2.6.24-16-generic.ubuntu.sound.alsa-driver.bak
sudo ln -s /lib/modules/2.6.24-16-generic/kernel/sound/ /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver
```


While again I know this is *not* the debian way or even smart, here's a package if anyone wants to do the same and doesn't care:
[download & install this]("rickybrent.com/mininote/deb/alsa-driver-1.0.16_linux-headers-2.6.24-16-generic-1_i386.deb").
After installing it, you need to also do the following:
```

sudo mv /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver /lib/modules/2.6.24-16-generic.ubuntu.sound.alsa-driver.bak
sudo ln -s /lib/modules/2.6.24-16-generic/kernel/sound/ /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver
```


> **bmccann said:**
> I googled 'alsa ad1984a driver' and eventually found the following patch:
<SNIP>
It looks like this patch just needs to be applied to ALSA 1.0.16 and then built. I'll try this sometime this week but if someone wants to try it sooner then hopefully this posting will get you started.

Man! I'm so happy to finally have the headphone detection working.

---

### Post by catdriver97 on 2008-05-12
Nice work **ldrn**!  I haven't had a chance to try it out yet, but I can't wait to get headphone detection working.

---

### Post by ldrn on 2008-05-15
Glad to help! :) Thank you for bringing up that it's actually a different card... all that fiddling and I never thought to make sure it was actually the card I was forcing alsa to treat it as. 8-[

I switched from KDE4 to XFCE and ran into an issue where the screen was blank, but the mouse appeared whenever a key was pressed or the mouse was moved; the solution was to kill gnome-screensaver -- posting it here in case anyone else runs into the same problem. I ended up just removing it for good.

---

### Post by catdriver97 on 2008-05-15
My hacking skills are not strong, but for those who can take advantage of it HP has released the source code disk for their SLED 10.1 installation on the HP 2133.

Perhaps someone with a deeper understanding of Linux internals can make good use of this.

[HP 2133 Mini-Note PC - Linux Source RPMs]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687084&swItem=ob-60382-1&prodNameId=3687085&swEnvOID=2020&swLang=8&taskId=135&mode=4&idx=0")

---

### Post by aeshanw on 2008-05-17
Hi ,
I've just got my HP2133 and I installed ubuntu via WUBI installer , coz the laptop came with vista installed.problem is thta keep getting a white screen coz of the gfx drivers.but when i enter safe mode , the system hangs on the installation state and keeps prompring me "uninstall exisiting instance of root in ubuntu/disks/".im quite confused about all this.can anyone explain to me whats going on here?
Thanks!

---

### Post by paintba||er on 2008-05-17
Has anybody tried putting FreeBSD on one of these?  I plan on getting one to take to school and other places where I would be worried that my MacBook would be stolen/damaged, and I'd really like to use FreeBSD on it.

---

### Post by aeshanw on 2008-05-18
has anyonw tried installing via the WUBI installer?if so could u guys share ur secret.coz im bogged down with the gfx issue & a white screen :(

---

### Post by aeshanw on 2008-05-18
How exactly do u enter the command-line mode of ubuntu , if ur gfx isnt installed yet?do i hit a key a few times on ubuntu bootup?
I need to enter command-line ststae so I can install the VIA GFX drivers.
Cheers!

---

### Post by allinurl on 2008-05-18
Does anyone is having problems with their USB mouse? I'm having a strange behavior that when I plug in my usb mouse then everything with a single mouse click assumes it's a double click. Perhaps someone can help me with this. Thanks Here it is my xorg for the mouse part: 

```
Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[0]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Emulate3Buttons" "on"
  Option       "InputFashion" "Mouse"
  Option       "Name" "Synaptics;Touchpad"
  Option       "Protocol" "explorerps/2"
  Option       "SHMConfig" "on"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[1]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "PS/2 Generic Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection
```

---

### Post by catdriver97 on 2008-05-18
**aeshanw**

I haven't used WUBI, but you might be able to get the vesa video drivers working.  That might give you a good enough desktop to install the VIA drivers.

Try booting into Windows.  Edit c:\ubuntu\disks\boot\grub\menu.lst and append the word "xforcevesa" (without the quotes) to the end of the "kernel" line under the "Ubuntu 8.04, kernel 2.6.24-16-generic" section.

Then boot into Ubuntu and give it a shot.  More WUBI info can be found [here]("https://wiki.ubuntu.com/WubiGuide").

If you need help installing the video drivers, the [LaptopTestingTeam HP2133 Wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133#preview") might also prove helpful.

Good luck!

---

### Post by catdriver97 on 2008-05-18
**allinurl**

I had similar problems before installing [this xorg.conf]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133?action=AttachFile&do=get&target=xorg.conf") file, which fixed it on my Logitech VX Revolution.  

Note that the sections you quoted are identical to the sections in that file.  Maybe there's a problem in another section, like "ServerLayout"?

---

### Post by catdriver97 on 2008-05-18
I've extensively updated the [HP 2133 Wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133").  Below are a few of the changes.

[LIST]
[*]Added **ldrn**'s sound driver fix.  Also put a mirror of the file up (hosted by wiki.ubuntu.com), so the whole world doesn't use up his bandwidth.  
**ldrn:**  If you'd rather have the traffic, I can redirect those downloads back to your site.  Let me know.
[*]Spelled out the whole ndiswrapper installation process, saving a trip to the original site, which had a more complicated install process aimed at a broad range of platforms.
[*]Removed Feisty and Gutsy hardware testing from the tables.  If anyone really wants me to put it back I can, but I haven't heard of many people installing earlier versions on their 2133s.
[/LIST]
If you've got any suggestions, or if I've really messed something up, please let me know.

---

### Post by bethanyboo on 2008-05-18
> **symbiat said:**
> Im having a very frustrating time with wireless and ndiswrapper. I followed the how-to, meticulously, twice, and its still not working. Network Manager shows the heading 'Wireless Networks' but shows no access points underneath (Im surround by at least 10 access points so that's not right. And my Nokia N810 web tablet works just fine so I know its not the access point that's the problem).

I tried telling Network manager to manually connect to my access point - after entering all the network details the animation 'spins' for a few minutes before disappearing and Im still not connected.

Would be grateful for any troubleshooting ideas...
I am having the same issue.  I have tried on 2 different wireless networks with no success.  Anyone have any ideas?

(Side note:  wireless didn't work under SUSE for me either. Same issue! :( )

---

### Post by allinurl on 2008-05-18
Have you guys tried the post I put before?

[http://ubuntuforums.org/showpost.php?p=4913259&postcount=51](http://ubuntuforums.org/showpost.php?p=4913259&postcount=51)



> **bethanyboo said:**
> I am having the same issue.  I have tried on 2 different wireless networks with no success.  Anyone have any ideas?

(Side note:  wireless didn't work under SUSE for me either. Same issue! :( )

---

### Post by catdriver97 on 2008-05-18
**symbiat**, **bethanyboo**,

A quick question for the both of you:

Which version of the HP2133 do you own?  

If you got the one with the solid-state-drive (4GB) then you've got a different wifi card than the rest.  That might explain why wireless isn't working for you.

If so, go [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") (if you haven't already) and follow the instructions closely.  If you succeed, then please tell me what worked (and what didn't) and I'll update the wiki.

---

### Post by aeshanw on 2008-05-18
Thanks for the advice catdriver97 , im in the folder , but cant see a menu.lst.do u think i can just create my own menu.lst n add the xforcevesa ?

> **catdriver97 said:**
> **aeshanw**

I haven't used WUBI, but you might be able to get the vesa video drivers working.  That might give you a good enough desktop to install the VIA drivers.

Try booting into Windows.  Edit c:\ubuntu\disks\boot\grub\menu.lst and append the word "xforcevesa" (without the quotes) to the end of the "kernel" line under the "Ubuntu 8.04, kernel 2.6.24-16-generic" section.

Then boot into Ubuntu and give it a shot.  More WUBI info can be found [here]("https://wiki.ubuntu.com/WubiGuide").

If you need help installing the video drivers, the [LaptopTestingTeam HP2133 Wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133#preview") might also prove helpful.

Good luck!

---

### Post by catdriver97 on 2008-05-18
> **aeshanw said:**
> Thanks for the advice catdriver97 , im in the folder , but cant see a menu.lst.do u think i can just create my own menu.lst n add the xforcevesa ?

Probably not.  Unfortunately, I'm not an expert at WUBI, so I might not me of much more use.  

Looking at the WUBI support link it seems that the file *should* be there, so that *could* mean you have an incomplete install.  I might be mistaken though.

Sorry I couldn't be of any more help.  Good luck!

---

### Post by allinurl on 2008-05-18
[FIXED]...

Low Volume under ubuntu.

---

### Post by allinurl on 2008-05-18
Thanks, that worked perfectly..

> **catdriver97 said:**
> **allinurl**

I had similar problems before installing [this xorg.conf]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133?action=AttachFile&do=get&target=xorg.conf") file, which fixed it on my Logitech VX Revolution.  

Note that the sections you quoted are identical to the sections in that file.  Maybe there's a problem in another section, like "ServerLayout"?

---

### Post by Nuno Abreu on 2008-05-19
Hi. I'm having a problem installing the wireless card. When I use the step 2a in the guide I see the access points in Network Manager but cant connect to them. If I use step 2b ubuntu crashes when Im doing the "Hardy bug fix" and doesnt boot until I remove ndiswrapper...

The strangest thing is that my wireless card seems different from what you have:

lspci gives me:  BCM4312,  14e4:4312 (rev **ff**)


ff??? I dont find a reference to this anywhere, its exclusive to me :).

Maybe I have to use a different version of ndiswrapper. Please give me some ideas so I can solve my problem. 

PS: I have the 2133 1.6 GHz version

Thanks

---

### Post by bethanyboo on 2008-05-19
> **catdriver97 said:**
> **symbiat**, **bethanyboo**,

A quick question for the both of you:

Which version of the HP2133 do you own?  

If you got the one with the solid-state-drive (4GB) then you've got a different wifi card than the rest.  That might explain why wireless isn't working for you.

If so, go [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") (if you haven't already) and follow the instructions closely.  If you succeed, then please tell me what worked (and what didn't) and I'll update the wiki.
Aha, that would explain it.  I do have the $500 model with the 4gb drive. I did follow those instructions at one point, using step 2a.  I took a look at the HP drivers site, which has a separate wireless driver for the models without bluetooth.  This driver is sp38766.exe, and from what I can tell from my work computer, it appears to support model 4321AG.  (I will try doing lspci  on my mini-note when I can to see what model I actually have)  I will go ahead and try 2a with the sp38766.exe driver.  

When I had my wireless halfway working (wireless capability was there, but wouldn't connect) I used the ndiswrapper GUI to add the .inf file from the sp38766.exe driver.  Perhaps things will work through the command line. 

**allinurl** - yes, I tried your instructions, as well as about 3 other sets of steps I found online, with no luck.

---

### Post by xjgnsdof on 2008-05-20
Between the video drivers, Skype issue, LiveCD quirks, CPU scaling problem, and wireless obstacles, it sounds like nightmare to install Ubuntu on this machine. Is it really that incompatible?

---

### Post by ldrn on 2008-05-20
Well, when you are done, it works much better than it did with the old version of SuSE it shipped with. :)

Lee over at the mini-note users forum has made a special version of the Ubuntu installer that should make the install easy; I haven't tried it, though:
[http://forums.mininoteuser.com/viewtopic.php?f=11&t=258&start=60&st=0&sk=t&sd=a]("http://forums.mininoteuser.com/viewtopic.php?f=11&t=258&start=60&st=0&sk=t&sd=a")

Some people have had skype issues, but for me, skype worked with video right out of the box -- very smoothly, too. It may have been because of the packages I installed, however.

---

### Post by catdriver97 on 2008-05-20
> **elgilicious said:**
> Between the video drivers, Skype issue, LiveCD quirks, CPU scaling problem, and wireless obstacles, it sounds like nightmare to install Ubuntu on this machine. Is it really that incompatible?

Admittedly, it's been a few years since I used Linux regularly (the distro I used was still called Mandrake at the time) but I was actually impressed at how *easy* it was.

I toyed with a dual-boot of Windows XP on my 2133, and a reinstall of Ubuntu (following the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") and fixing all the quirks) took all of 45 minutes.  

We've still got a little ways to go, but I can't imagine that the few remaining hardware issues won't be ironed out by the end of the summer.

Considering the hardware has been on the market for less than a month, I was surprised that it was so well supported.  No doubt this is due to the low-end nature of the Mini-Note's design, but it's still impressive.

---

### Post by xjgnsdof on 2008-05-20
> **catdriver97 said:**
> Admittedly, it's been a few years since I used Linux regularly (the distro I used was still called Mandrake at the time) but I was actually impressed at how *easy* it was.

I toyed with a dual-boot of Windows XP on my 2133, and a reinstall of Ubuntu (following the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") and fixing all the quirks) took all of 45 minutes.  

We've still got a little ways to go, but I can't imagine that the few remaining hardware issues won't be ironed out by the end of the summer.

Considering the hardware has been on the market for less than a month, I was surprised that it was so well supported.  No doubt this is due to the low-end nature of the Mini-Note's design, but it's still impressive.

I just got my Mini-Note in the mail this evening. I don't have an external CD drive, and I'm having trouble installing Linux Mint onto it. I'll see just how easy it is to set up and report back.

---

### Post by catdriver97 on 2008-05-20
> **bethanyboo said:**
> Aha, that would explain it.  I do have the $500 model with the 4gb drive. I did follow those instructions at one point, using step 2a.  I took a look at the HP drivers site, which has a separate wireless driver for the models without bluetooth.  This driver is sp38766.exe, and from what I can tell from my work computer, it appears to support model 4321AG.  (I will try doing lspci  on my mini-note when I can to see what model I actually have)  I will go ahead and try 2a with the sp38766.exe driver.  

When I had my wireless halfway working (wireless capability was there, but wouldn't connect) I used the ndiswrapper GUI to add the .inf file from the sp38766.exe driver.  Perhaps things will work through the command line. 

**bethanyboo**

The wiki has been updated to reflect the problems people have been having with the SSD version of the 2133.  

Did the alternate driver end up working for you?  If so, I can add a separate WiFi driver path to the How-To.

**elgilicious**

I did hear from another user that USB Kubuntu 8.04 install was successful.  If the USB setup works will you e-mail me or update the wiki with any quirks you find?  Good luck!

---

### Post by catdriver97 on 2008-05-20
> **Nuno Abreu said:**
> Hi. I'm having a problem installing the wireless card. When I use the step 2a in the guide I see the access points in Network Manager but cant connect to them. If I use step 2b ubuntu crashes when Im doing the "Hardy bug fix" and doesnt boot until I remove ndiswrapper...

The strangest thing is that my wireless card seems different from what you have:

lspci gives me:  BCM4312,  14e4:4312 (rev **ff**)


ff??? I dont find a reference to this anywhere, its exclusive to me :).

Maybe I have to use a different version of ndiswrapper. Please give me some ideas so I can solve my problem. 

PS: I have the 2133 1.6 GHz version

Thanks

**Nuno**, 

I've heard from another user that the KX875AA (1.6GHz, 2GB RAM, 160GB HDD, Bluetooth) was having similar issues in Kubuntu.  

The latest version of the HP wireless driver on the [support site]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687084&prodNameId=3687085&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-58949-1") is sp38766, vice the sp34152 in the How-To.  Maybe it will work better?  It's certainly worth a try.  You should be able to substitute the proper driver number in step 2a.

---

### Post by xjgnsdof on 2008-05-21
I am running Linux Mint Elyssa (beta) on my Mini-Note!

I will configure the wireless card and enable Compiz later today.

---

### Post by earlycj5 on 2008-05-21
> **catdriver97 said:**
> 
**elgilicious**

I did hear from another user that USB Kubuntu 8.04 install was successful.  If the USB setup works will you e-mail me or update the wiki with any quirks you find?  Good luck!

I'm not elgilicous but I did install OzOs from my USB stick on my mininote.

The only thing that worked differently for me was once I had everything installed my fstab file thought that /dev/sda1 was a CDROM drive so I couldn't mount the internal card reader or a USB drive if inserted.  I've not seen anyone else make a note of that anywhere.  Dunno if I'm unique or not.

I've the 1.6ghz, bluetooth model.  Wireless works flawlessly with Ndiswrapper and the network-manager.

---

### Post by catdriver97 on 2008-05-21
**earlycj5**,

A quick question for you.  

If you remember from your install, which HP driver pack did you use with ndiswrapper?  We're trying to track down which ones work and which don't.

Thanks!

---

### Post by earlycj5 on 2008-05-21
> **catdriver97 said:**
> **earlycj5**,

A quick question for you.  

If you remember from your install, which HP driver pack did you use with ndiswrapper?  We're trying to track down which ones work and which don't.

Thanks!

Got it!

[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)


From [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

```

lspci -n | grep '14e4:43'

```
Returns

```

02:00.0 0280: 14e4:4312 (rev 02)

```

---

### Post by catdriver97 on 2008-05-21
> **earlycj5 said:**
> Got it!

[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)


Good.  That's the same one we've been asking people to use on the Wiki.
  
Has anyone had success with HP's recommended driver [sp38766]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=3687084&prodNameId=3687085&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-58949-1") under ndiswrapper?

---

### Post by xjgnsdof on 2008-05-21
> **earlycj5 said:**
> I'm not elgilicous but I did install OzOs from my USB stick on my mininote.

The only thing that worked differently for me was once I had everything installed my fstab file thought that /dev/sda1 was a CDROM drive so I couldn't mount the internal card reader or a USB drive if inserted.  I've not seen anyone else make a note of that anywhere.  Dunno if I'm unique or not.

I've the 1.6ghz, bluetooth model.  Wireless works flawlessly with Ndiswrapper and the network-manager.

As for your fstab issue, all you have to do is comment out the /dev/sda1 line. I solved that same problem earlier today...

---

### Post by earlycj5 on 2008-05-22
> **elgilicious said:**
> As for your fstab issue, all you have to do is comment out the /dev/sda1 line. I solved that same problem earlier today...

I know, that's what I did when I found out what the problem was.  :)

---

### Post by allinurl on 2008-05-22
Any news or hope about the microphone?

---

### Post by rdrandal on 2008-05-23
> **catdriver97 said:**
> **allinurl**

I had similar problems before installing [this xorg.conf]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133?action=AttachFile&do=get&target=xorg.conf") file, which fixed it on my Logitech VX Revolution.  

Note that the sections you quoted are identical to the sections in that file.  Maybe there's a problem in another section, like "ServerLayout"?

Adding this xorg.conf with the "CorePointer" Option in the third Input Section resolved my issue with my USB mouse. Thank you very much.

---

### Post by earlycj5 on 2008-05-23
I don't know if anyone else is using e17 like I am, I'm using OzOS on mine.  But after I install the Via driver and the corresponding Xorg.conf file my dpi settings were off.  It borked my GTK font sizes.

I added this line to the Monitor section and it corrected the problem:
```

  DisplaySize 338 203 # 1280x768 96dpi

```

While searching for the solution I found that XFCE uses its own file and overrides the xorg settings and probably Gnome and KDE too?  But for Fluxbox and e17 it fixes the fonts in GTK aps as far as I can tell.

---

### Post by earlycj5 on 2008-05-23
.

---

### Post by bringar on 2008-05-25
well, after fussing about and following along here i've got my mininote working as much as it sounds like anyone else does.

i noticed that i can get choppy distorted sound in through the mic jack, no response from the built in mic's tho.

is it possible that the snd_hda_intel is not exactly the right module as it is a Via device, or we're missing something else?

```
# lsmod | egrep 'snd|sound'
snd_hda_intel         359320  4 
snd_pcm_oss            42528  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78980  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd_seq_dummy           4996  0 
snd_seq_oss            35712  0 
snd_seq_midi            9504  0 
snd_rawmidi            25888  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54352  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    57252  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

cheers and thanx for all the hard work guys.

---

### Post by catdriver97 on 2008-05-26
Heads up everybody!  The latest Ubuntu update includes the 2.6.24-17 kernel, which breaks the headphone-jack fix posted by **ldrn** in [this post]("http://ubuntuforums.org/showpost.php?p=4937154&postcount=58").

If you care about headphone-jack recognition, you should probably hold off on the update for now.

---

### Post by earlycj5 on 2008-05-26
> **catdriver97 said:**
> Heads up everybody!  The latest Ubuntu update includes the 2.6.24-17 kernel, which breaks the headphone-jack fix posted by **ldrn** in [this post]("http://ubuntuforums.org/showpost.php?p=4937154&postcount=58").

If you care about headphone-jack recognition, you should probably hold off on the update for now.

Swell.  Thanks, now I know why I can't get it to work where previously it had.  I thought I'd screwed something up somewhere as I've been tweaking, installing, reinstalling trying different file systems for optimal battery life etc.  Then all the sudden this quit working.  Now I know...

---

### Post by catdriver97 on 2008-05-26
**earlycj5,**

Yeah, I got the ugly surprise too.  Maybe **ldrn** will save us with another fix, although I'm thinking this will get a little old after a few kernel updates.  

What we really need is a functional audio driver.

---

### Post by bringar on 2008-05-26
ouch... sorry you guys got bit by that

everyone who hasn't should pin their kernel and headers like so:
find what packages you have installed that pertain by:
aptitude search 2.6.24 | egrep -i '^i'
then aptitude show *packagename* look for the version

add to /etc/apt/preferences your own versions/ whatever:
```


     Package: linux-image-2.6.24-generic
     Pin: version 2.6.24-16.30
     Pin-Priority: 1000

     Package: linux-headers-2.6.24-16-generic
     Pin: version 2.6.24-16.30
     Pin-Priority: 1000

     Package: linux-restricted-modules-2.6.24-16-generic
     Pin: version 2.6.24-12-16.34
     Pin-Priority: 1000

     Package: linux-ubuntu-modules-2.6.24-16-generic
     Pin: version 2.6.24-16.23
     Pin-Priority: 1000

     Package: linux-restricted-modules-common
     Pin: version 2.6.24.12-16.34
     Pin-Priority: 1000



```

this will keep your package manager from updating over all your hard labor.
if you want to know more about pining..
[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

cheers

---

### Post by catdriver97 on 2008-05-26
**bringar**,

I've never heard of pinning before.  Thanks for the informative links.  

I'm torn right now between pinning those packages or holding out for a permanent fix.  It seems like pinning this problem is just putting a bandage over a bandage.

Still, "it works" is a powerful argument.

---

### Post by bringar on 2008-05-26
woops i missed linux-restricted-modules-common...

yes pinning can create long term issues but i fully expect the kernel dev team or the ubuntu kernel maintainers will get themselves a mininote before long or someone with enough clout and experience will send them a good patch for inclusion.

in other news i tried modprobing the snd-via8c2xx module and got about the same results as with snd_hda_intel..

---

### Post by fourseason7444 on 2008-05-26
Thank you everyone for posting this valuable info, and to Catdriver in particular for assembling it all into a step-by-step installation guide!

My Mini is the second-cheapest one which shipped with SuSE and a 120G hard drive. I bought one of those no-name SATA/IDE->USB cables for about $35 and was able to boot from the Kubuntu installer CD without a problem (an earlier attempt to boot the installer from a SATA drive with this cable failed; must be missing a critical driver). I've updated firmware to v0.2 and have applied all updates to Kubuntu (I did so before reading about headphone jack issues, oh well).

Wireless was working pretty good, but KNetworkManager won't remember any settings if the WAP has a private SSID. I didn't see any solution to this other than making the SSID visible, and it worked fine thereafter.

It also seemed to be hit-or-miss whether wireless still worked after waking the computer from a suspended or hibernating state. In most cases, I could restore things with:

> sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

Taking a cue from a SUSE document on Pm-utils:
[http://en.opensuse.org/Pm-utils]("http://en.opensuse.org/Pm-utils")

I created the file
/etc/pm/sleep.d/45ndiswrapper

Containing:

> #!/bin/bash
case $1 in
	hibernate)
		modprobe -r ndiswrapper
		;;
	suspend)
		modprobe -r ndiswrapper
		;;
	thaw)
	modprobe ndiswrapper
		;;
	resume)
	modprobe ndiswrapper
		;;
	*) echo "A fault occurred with /etc/pm/sleep.d/45ndiswrapper"
		;;
esac

followed by

> sudo chmod +x /etc/pm/config.d/45ndiswrapper

This seems to have mostly fixed my wireless issues upon waking the computer.

Unresolved strangeness:

Upon waking from hibernation or suspend, the cooling fan will sometimes run at full speed and stay there, and

Sometimes i'll be scrolling a page using the touchpad, and will get a loud howling noise from the speakers. So far I've always been using Konqueror when it happens, and it seems to go away if I switch the touchpad off for a moment.

---

### Post by catdriver97 on 2008-05-26
Somehow (by futzing around too much with ALSA and config files, I'm sure) I seem to have completely tubed my sound.  Not a big deal, since I'm not using the audio on my Mini-Note for much anyway.

Interestingly, I've dug up [this link]("http://www.linuxhq.com/kernel/v2.6/25-git7/Documentation/sound/alsa/ALSA-Configuration.txt"), which seems to imply that AD1984A support will be built into the 2.6.25 kernel.

No idea when that will be making its way into Ubuntu, but help may be on the (distant) horizon.

EDIT:  Answered my own question... looks like [Intrepid]("http://www.nabble.com/Ubuntu-Intrepid-kernel-open-for-business-(almost)-td16811704.html").

---

### Post by catdriver97 on 2008-05-31
Just for kicks (since my audio was already messed up) I gave Fedora Core 9 a shot, since it's based on the update 2.6.25 kernel that *might* have working audio for the AD1984A.  Bad idea.  I couldn't even get a desktop.

The good news is the full reinstall of Ubuntu that followed let me audit the install [how-to]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133").  It has now been updated.

It looks like the -17 kernel update broke the 3D acceleration in VIA video driver in addition to our audio fix.  Every time I tried to add the "via" line to the /usr/bin/compiz whitelist, I'd crash the window manager on login.

Has anyone had any luck getting the audio-jack sensing to work post-update?

---

### Post by ldrn on 2008-05-31
I've been holding off on updating since the video driver wouldn't work anyway; I think just using the older kernel is a better solution for now, but the audio should be pretty easy to recompile for the new kernel.

---

### Post by catdriver97 on 2008-05-31
> **ldrn said:**
> I've been holding off on updating since the video driver wouldn't work anyway; I think just using the older kernel is a better solution for now, but the audio should be pretty easy to recompile for the new kernel.

If I really needed the headphone sensing or the 3D I'd be holding off myself.  I'm sure that just as soon as you recompiled the audio, they'd come out with another kernel patch and you'd have to do it all over again!

I'm pretty sure that when 2.6.25 comes out it will all work OK.  Like most new hardware in Linux, it just takes a bit of time.

---

### Post by ldrn on 2008-05-31
Yep! Intrepid is far away, though...

For kernel 2.6.24-17:
[alsa-driver-1.0.16_linux-headers-2.6.24-17-generic-1-1_i386.deb]("http://rickybrent.com/mini-note/deb/alsa-driver-1.0.16_linux-headers-2.6.24-17-generic-1-1_i386.deb")
Followed by:
```

sudo mv /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver /lib/modules/2.6.24-17-generic.ubuntu.sound.alsa-driver.bak
sudo ln -s /lib/modules/2.6.24-17-generic/kernel/sound/ /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver

```

I'd automate all that inside the deb, but it's a pretty odd hack anyway. :)

---

### Post by earlycj5 on 2008-05-31
> **ldrn said:**
> Yep! Intrepid is far away, though...

For kernel 2.6.24-17:
[alsa-driver-1.0.16_linux-headers-2.6.24-17-generic-1-1_i386.deb]("http://rickybrent.com/mini-note/deb/alsa-driver-1.0.16_linux-headers-2.6.24-17-generic-1-1_i386.deb")
Followed by:
```

sudo mv /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver /lib/modules/2.6.24-17-generic.ubuntu.sound.alsa-driver.bak
sudo ln -s /lib/modules/2.6.24-17-generic/kernel/sound/ /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver

```

I'd automate all that inside the deb, but it's a pretty odd hack anyway. :)

Thanks for the update!

---

### Post by catdriver97 on 2008-06-01
> **ldrn said:**
> Yep! Intrepid is far away, though...



Once again **ldrn** saves the day.  

The new file has been posted to the [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") with the instructions.

Thanks!

---

### Post by rdrandal on 2008-06-03
I have an HP 2133 KX870AT running 2.6.24.16 generic with Via's Via-Chrome beta driver and 3D enabled in compiz w/CPU scaling. Most everything is working fine with the exception of the mic as with everyone else. I do not seem to have a working screen-saver. If I click on a particular screen-saver to view, it usually will display in full-screen although the notebook will appear to lock-up on some SS. I scheduled the SS to execute with random SS after 5 minutes but the screen only goes to a blank display. Pressing any key brings the desktop back. Anyone else having this issue?

---

### Post by earlycj5 on 2008-06-03
I spent a bit of time yesterday with the bluetooth on mine.  I installed Blueman, [http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/) and used that to transfer files between my Mini-Note and my desktop computer with a bluetooth dongle.  It works quite nicely.

Biggest problem I had was that I'd forgotten I turned off the bluetooth device in the BIOS.  :oops:

---

### Post by catdriver97 on 2008-06-03
> **rdrandal said:**
> I have an HP 2133 KX870AT running 2.6.24.16 generic with Via's Via-Chrome beta driver and 3D enabled in compiz w/CPU scaling. Most everything is working fine with the exception of the mic as with everyone else. I do not seem to have a working screen-saver. If I click on a particular screen-saver to view, it usually will display in full-screen although the notebook will appear to lock-up on some SS. I scheduled the SS to execute with random SS after 5 minutes but the screen only goes to a blank display. Pressing any key brings the desktop back. Anyone else having this issue?

I had a similar experience with my KX869AT when running in that configuration.  I attributed it to some of the screen savers being extremely (for the Mini-Note) graphics intensive on top of Compiz's already heavy load.  Usually I ended up crashing the X-session, or at least Compiz.

If you've got to have something other than a blank screen, I'd pick one screen saver that runs well and stick with it.  3D accelerated screen savers are probably too much to ask of this video card.

---

### Post by earlycj5 on 2008-06-03
> **catdriver97 said:**
> I had a similar experience with my KX869AT when running in that configuration.  I attributed it to some of the screen savers being extremely (for the Mini-Note) graphics intensive on top of Compiz's already heavy load.  Usually I ended up crashing the X-session, or at least Compiz.

If you've got to have something other than a blank screen, I'd pick one screen saver that runs well and stick with it.  3D accelerated screen savers are probably too much to ask of this video card.

I use the OpenGL screensavers on mine, Flurry and Flying Toasters work fine.  It warms up a good bit, but not as much as compiling a kernel will do to it.

Screensaver isn't on very long usually anyway.  But I digress.  The OpenGL SSs work fine for me it seems.

---

### Post by rdrandal on 2008-06-04
Thank you both (catdriver97 & earlycj5) If I can get my system back after updating to 2.6.24.18 I'll have to try your suggestion. Now my system continues to boot and re-boot after entering my password. I'll need to get into a safe terminal and see what's going on. I knew I shouldn't have loaded the new kernel but then I wouldn't have the experience in trying to figure out what broke.

---

### Post by dltebojr on 2008-06-04
So, it looks like the -18 Kernel busted the audio/headphones fix AGAIN! ;-/ Any suggestions on the table??? 

Thanks to all in advance!

---

### Post by Rui Pais on 2008-06-04
> **earlycj5 said:**
> I use the OpenGL screensavers on mine, Flurry and Flying Toasters work fine.  It warms up a good bit, but not as much as compiling a kernel will do to it.

Screensaver isn't on very long usually anyway.  But I digress.  The OpenGL SSs work fine for me it seems.

Btw, a nice screensaver that may be lighter (and avoid extra hot) it's xlockmore, with basic screensaver, or xlockmore-gl for an extra eye-candy.

Use it's simple, run a launcher at session start with for xlock, instead of gnome-screensaver or Xscreensaver.

---

### Post by earlycj5 on 2008-06-04
> **Rui Pais said:**
> Btw, a nice screensaver that may be lighter (and avoid extra hot) it's xlockmore, with basic screensaver, or xlockmore-gl for an extra eye-candy.

Use it's simple, run a launcher at session start with for xlock, instead of gnome-screensaver or Xscreensaver.


Thanks Rui, I'm not really concerned about it though.  It only warms up to the mid-60s and like I said the SS isn't activated that long before the screen blanks.

---

### Post by earlycj5 on 2008-06-04
> **catdriver97 said:**
> Somehow (by futzing around too much with ALSA and config files, I'm sure) I seem to have completely tubed my sound.  Not a big deal, since I'm not using the audio on my Mini-Note for much anyway.

Interestingly, I've dug up [this link]("http://www.linuxhq.com/kernel/v2.6/25-git7/Documentation/sound/alsa/ALSA-Configuration.txt"), which seems to imply that AD1984A support will be built into the 2.6.25 kernel.

No idea when that will be making its way into Ubuntu, but help may be on the (distant) horizon.

EDIT:  Answered my own question... looks like [Intrepid]("http://www.nabble.com/Ubuntu-Intrepid-kernel-open-for-business-(almost)-td16811704.html").

Interesting, I've compiled a vanilla 2.6.25 kernel and have no sound.  :(

Not sure what I've done wrong.  I might fiddle with it more later.

---

### Post by veruus on 2008-06-04
Getting one of these next week.  Did anyone mention if the camera is working?  Gotta pay this thing off somehow... wait, what?  ;)

---

### Post by catdriver97 on 2008-06-05
> **dltebojr said:**
> So, it looks like the -18 Kernel busted the audio/headphones fix AGAIN! ;-/ Any suggestions on the table??? 

**ldrn **is our resident audio patch deity.  I suggest prayer and/or food offerings.  

> **veruus said:**
> Getting one of these next week.  Did anyone mention if the camera is working?  Gotta pay this thing off somehow... wait, what?  ;)

I've had good success with the 1.2GHz model in Skype, but I had to turn off preview or it would cause artifacts.  Without microphone input it might not do you much good though.

---

### Post by earlycj5 on 2008-06-06
Arrgghh, this sound thing is driving me nuts!

I've tried compiling a .deb myself, I managed to get the patch incorporated (edit the series file in /debian/patches).  But even after that and installation of the patched .deb or installation of the 2.6.25 kernel (should have support) I still have no sound.  :mad:

---

### Post by rdrandal on 2008-06-06
> **rdrandal said:**
> Thank you both (catdriver97 & earlycj5) If I can get my system back after updating to 2.6.24.18 I'll have to try your suggestion. Now my system continues to boot and re-boot after entering my password. I'll need to get into a safe terminal and see what's going on. I knew I shouldn't have loaded the new kernel but then I wouldn't have the experience in trying to figure out what broke.

Make sure you disable 3D effects in Compiz before moving to 2.6.24.18 as well as 2.6.24.17

---

### Post by Blademaster on 2008-06-07
Hello,

I have used wubi and installed 8.04 within Vista business
I have downloaded the new drivers, changed the xorg file, and updated the compiz file, but when I try to enable 3d effects - my screen flashes and reboots. Any ideas?

---

### Post by bmccann on 2008-06-07
The ALSA team has released RC1 of ALSA-1.0.17. See:

[http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17rc1](http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17rc1)

Among many other changes, this includes:

hda - Add support of AD1989A/AD1989B
hda-codec - Fix automute of AD1981HD hp model 
hda - Fix mic input on HP2133

I don't know if this driver can compile/build against 2.6.24 but it might be worth a shot for anying anxious to get the microphone working.

---

### Post by earlycj5 on 2008-06-09
> **bmccann said:**
> The ALSA team has released RC1 of ALSA-1.0.17. See:

[http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17rc1](http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17rc1)

Among many other changes, this includes:

hda - Add support of AD1989A/AD1989B
hda-codec - Fix automute of AD1981HD hp model 
hda - Fix mic input on HP2133

I don't know if this driver can compile/build against 2.6.24 but it might be worth a shot for anying anxious to get the microphone working.

electronic_s from Mininoteuser.com did this against 2.6.24 and posted that it worked there.

I can happily say I'm listening to music on my Mininote now.  I compiled the 2.6.25 kernel with the Via C7 optimizations enabled and then compiled ALSA RC1 1.0.17 and installed.  Reboot.  Voila, sound!

Headphone detection works as well.

---

### Post by allinurl on 2008-06-09
earlycj5, is the microphone working too?

---

### Post by earlycj5 on 2008-06-10
> **allinurl said:**
> earlycj5, is the microphone working too?

electronic_s says it sorta works.  I didn't see any controls for it in ALSAmixer though.

I'm gonna give it a try later and I'll report back.

I had problems with my custom kernel, the computer would freeze up.  Going to try not enabling the C7 CPU scaling and just use generic and see if that's it (hopefully).

---

### Post by lordwalsh on 2008-06-15
I installed Ubuntu on my new HP Compaq 2133 Mini-Note but I have had trouble with the video driver there are distortions like strings of red blots on the desktop, and websites, and all over videos, and images. I already decided to followed the instructions closely on the wiki/ubuntu.com/Laptoptestingteam/hp2133 site to reinstall my video driver to the one they recommended but after that I saw no improvement. I have also tried playing with the screen resolution to no effect. does anyone have any suggestions? thanks

---

### Post by heretik_85 on 2008-06-21
> **lordwalsh said:**
> I installed Ubuntu on my new HP Compaq 2133 Mini-Note but I have had trouble with the video driver there are distortions like strings of red blots on the desktop, and websites, and all over videos, and images. I already decided to followed the instructions closely on the wiki/ubuntu.com/Laptoptestingteam/hp2133 site to reinstall my video driver to the one they recommended but after that I saw no improvement. I have also tried playing with the screen resolution to no effect. does anyone have any suggestions? thanks

This probably isn't going to make it any better lordwalsh, but exactly the same thing has happened on mine... it sorta looks like when your video card has overheated and you start getting artifacts. Not really OS-breaking but it's pretty annoying on my beautiful desktop.

---

### Post by cenwesi on 2008-06-23
> **earlycj5 said:**
> electronic_s from Mininoteuser.com did this against 2.6.24 and posted that it worked there.

I can happily say I'm listening to music on my Mininote now.  I compiled the 2.6.25 kernel with the Via C7 optimizations enabled and then compiled ALSA RC1 1.0.17 and installed.  Reboot.  Voila, sound!

Headphone detection works as well.

I can confirm that Kernel 2.6.25 with the ALSA RC1 1.0.17 and installed worked. Finally i think i have everything working the way i want. I even have wireless working using the "compat-wireless" library. Now i can retire the other laptop to the wife still running XP.

---

### Post by lordwalsh on 2008-06-23
> **heretik_85 said:**
> This probably isn't going to make it any better lordwalsh, but exactly the same thing has happened on mine... it sorta looks like when your video card has overheated and you start getting artifacts. Not really OS-breaking but it's pretty annoying on my beautiful desktop.

yea I reinstalled the orgional video driver and that restored my computer back to normal, its not the best quility but it works fine now, thanks

---

### Post by volt4ire on 2008-06-26
Im trying to figure out the video-driver issues so I can get compiz running. I'm using the 120GB SLED version of the mininote running Kubuntu 8.04 and the latest kernel versions, which i believe is the problem. I tried installing the CN896+VT8237S ubuntu stable glx driver from [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action) and used the xorg.conf file found in this forum. Whenever i tried to login it would apparently crash X, so i had to replace it with the xorg.conf.viabak file, so now i think im using the Vesa driver. was the CN896+VT8237S the right driver? From what i understand from the previous posts, the VIA drivers wont work b/c they're not compatible with the new kernel versions. so, *how can i run compiz on this machine*? Should i use that custom Minbuntu and just install kde on top of it? Does it have that "pegging" thing mentioned in previous posts built-in so it still updates the packages but keeps the kernel version which supports the VIA drivers? What about the "openchrome" drivers i hear about? Will they support compiz, and if so, how do i install them? If it doesn't, does it have better video playback then the vesa drivers, which play flash-videos realy slowly online when in full-screen mode? (it plays-back DVD-quality vids just fine from the harddrive). Thanks for your help!!!!!!!!

---

### Post by allinurl on 2008-07-01
> **cenwesi said:**
> I can confirm that Kernel 2.6.25 with the ALSA RC1 1.0.17 and installed worked. Finally i think i have everything working the way i want. I even have wireless working using the "compat-wireless" library. Now i can retire the other laptop to the wife still running XP.

Can you go through on how did you make your sound work plz? If you could do a step by step will be appreciate it. Also does the microphone works?

---

### Post by pulpo88 on 2008-07-06
I can confirm that all playback/record features work well on my 2133 with the latest Alsa RC and just the standard Ubuntu Hardy kernel 2.6.24-19.

Here's what I did:

[LIST=1]
[*] Download alsa-driver-1.0.17rc3 from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
[*] **./configure; make; sudo make install**
[*] Unfortunately it installs to the wrong place.  Not surprising since we don't have any of the Ubuntu patches in this tarball.  Probably can be fixed with configure, but I just worked around it with:
[LIST=a]
[*] **cd /lib/modules/2.6.24-19-generic** (or whatever kernel you have)
[*] **sudo cp -a kernel/sound/* ubuntu/sound/alsa-driver/**
[/LIST]
[*] **sudo vi /etc/modprobe.d/alsa-base** and add the following to the bottom of the file: **options snd-hda-intel model=laptop**
[*] Reboot.  Sound playback should work, and plugging in headphones will mute the speaker.
[*] Run alsamixer.  You should see the following devices:
[LIST=a]
[*] Playback: Master, PCM, Mic, Mic Boost, Beep, Dock, Dock Mic (x2), Internal (x2)
[*] Capture: Mic Boost, Capture (x2), Digital, Dock Mic Boost, Input Source x2, Internal Mic Boost
[/LIST]
[*] Adjust the settings using the attached screen shot as a guide.  Use M to toggle mute and SPACE to toggle the recording mode for the two Capture channels.
[/LIST]

At this point as long as the Playback:Mic level is unmuted, you can plug in a microphone and hear yourself in the speakers.

You can record through either the built-in mic or a plugged in mic using:

**arecord -vv -c 2 -d 5 -f cd -t wav test.wav**

---

### Post by dsurber on 2008-07-06
I'm running Kubuntu 8.04 fully updated. I downloaded Google Earth from earth.google.com and did the default install. When I start it, the splash screen comes up for a bit then nothing. I started it from a console and get a stack dump. Any one else seen this behavior? Anyone else able to run Google Earth on a similar config?

Douglas

---

### Post by catdriver97 on 2008-07-07
> **pulpo88 said:**
> I can confirm that all playback/record features work well on my 2133 with the latest Alsa RC and just the standard Ubuntu Hardy kernel 2.6.24-19.

Here's what I did:


Thanks **pulpo88**, that did the trick!  

The [wiki]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") has been updated for Hardy 8.04.1 and **pulpo88**'s ALSA fix is now included.

Additionally, a compatibility column has been added for Intrepid Ibex.  

My brief experience with it was encouraging, but it will take some diligent bug reporting to ensure our Mini-Notes work "out-of-the-box" on this next release.  I encourage anyone brave and experienced enough to try Alpha 1 out and report as many bugs as you can.  Good hunting!

Also, for those waiting, you can now [order 6-cell batteries]("http://h10010.www1.hp.com/wwpc/us/en/sm/WF06c/A10-51210-329223-329260-329223-3678641-3678642-3678644.html") online at the HP store.

---

### Post by violajack on 2008-07-08
I'm running intrepid.  I got tired of fighting with ndiswrapper so I took the plunge.  I ran update-manager -d to do the upgrade and it worked.  I now have native wifi.  I also tested suspend and it works just fine.  As far as I can tell, everything resumed successfully.  It's currently listed as untested on the wiki.  Should I update that?  Does my experience count as enough to say that it works?  Also, the same fix for CPU frequency scaling works for intrepid.  All the function keys are working for me also.  

The one thing I miss is the graphics drivers.  Youtube runs like a slideshow.  I don't know how to go about playing with the openchrome drivers.  If I change the "via" to "openchrome" in the xorg, I get the greeter crash referenced here: [http://ubuntuforums.org/showthread.php?t=847977](http://ubuntuforums.org/showthread.php?t=847977), but I haven't had time to go about trying anything to fix it.  

It also runs quite a bit slower than Hardy did, but I think that's just because it's alpha and full of debug code and stuff.

---

### Post by catdriver97 on 2008-07-08
**violajack**, if you've used Intrepid on your Mini-Note, you're as qualified as anyone to update the wiki.  I only used it for about fifteen minutes before jumping back into Hardy, and I ran into the greeter crash myself.

Did you have to do much else besides running *update-manager -d* to get everything to work?  I'm impressed that you got CPU scaling working.  For some reason it never worked for me.

I'll probably give Intrepid another shot when they come out with the next Alpha.

**dsurber**

I haven't tried Google Earth on my Mini-Note, but that sounds an awful lot like a video card issue.  Are you using openchrome or the VIA drivers?

---

### Post by Monstroxus on 2008-07-08
I followed the wiki, but it seems cpu scaling is still not working properly as the battery runs out fast. (1 hour or so)

More importantly, I installed the VIA video driver and it shows up in the hardware drivers section. However it says:

enabled (but) not in use.

I tried to disable it, reboot, enable, reboot... but no luck. Perhaps I need to reinstall this driver, but I don't know how to uninstall it in the first place (newbie) anyone can help me? Thanks.

---

### Post by violajack on 2008-07-08
I was running an up to date hardy with the original -16 kernel for the graphics drivers.  I just ran update-manager -d and crossed my fingers.  It downloaded and installed over 900 packages.  I had to click agree on a few things, I think it was mostly the update of Java.  About 2 hours later, when it rebooted I got a bright red screen, but the hard drive light was still flickering so I just let it go to see if it would do anything.  Then, white blocks started scolling as if it was the kernel messages.  Turns out, the red screen is another interesting error others are getting and it's a problem with usplash.  It only happens after I make major changes or big updates.  If it's just a normal reboot, I get the usual usplash.  

I think I have frequency scaling.  I keep the frequency monitor applet in my top panel, just cause I like to know those things, and on my first reboot it complained that frequnecy scaling was not enabled on this machine.  I checked the grub menu.lst and sure enough, the option was gone.  I just added acpi_osi="!Windows 2006" to the kernel options and rebooted.  Now my frequency monitor says I'm at 800 most of the time and 1200 under load.  I also have the little system monitor up there to know when the system is working hard and when its not.  I have not run the battery all the way down from a full charge to know if it's really saving me the battery life.  I'll try to do that sometime later today.  Is there another check I can do to verify the CPU frequency?

I was using the xorg.conf provided by the wiki for the via drivers.  I've also used the one by mikez posted on the mininoteuser forums, which also references the via driver.  Those two work normally.  Any attempt at using "openchrome" or even going back to "vesa" results in the greeter crash.  

Intrepid would be perfect if only I could get the 3D graphics and better video performance.  I used to get close to 400 fps in glxgeaers with the via provided drivers.  I only get around 180 now and all the videos I get from miro that played fine in hardy are slideshows in intrepid.

---

### Post by WillyLinux on 2008-07-12
> **pulpo88 said:**
> I can confirm that all playback/record features work well on my 2133 with the latest Alsa RC and just the standard Ubuntu Hardy kernel 2.6.24-19.

Here's what I did:

[LIST=1]
[*] Download alsa-driver-1.0.17rc3 from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
[*] **./configure; make; sudo make install**
[*] Unfortunately it installs to the wrong place.  Not surprising since we don't have any of the Ubuntu patches in this tarball.  Probably can be fixed with configure, but I just worked around it with:
[LIST=a]
[*] **cd /lib/modules/2.6.24-19-generic** (or whatever kernel you have)
[*] **sudo cp -a kernel/sound/* ubuntu/sound/alsa-driver/**
[/LIST]
[*] **sudo vi /etc/modprobe.d/alsa-base** and add the following to the bottom of the file: **options snd-hda-intel model=laptop**
[*] Reboot.  Sound playback should work, and plugging in headphones will mute the speaker.
[*] Run alsamixer.  You should see the following devices:
[LIST=a]
[*] Playback: Master, PCM, Mic, Mic Boost, Beep, Dock, Dock Mic (x2), Internal (x2)
[*] Capture: Mic Boost, Capture (x2), Digital, Dock Mic Boost, Input Source x2, Internal Mic Boost
[/LIST]
[*] Adjust the settings using the attached screen shot as a guide.  Use M to toggle mute and SPACE to toggle the recording mode for the two Capture channels.
[/LIST]

At this point as long as the Playback:Mic level is unmuted, you can plug in a microphone and hear yourself in the speakers.

You can record through either the built-in mic or a plugged in mic using:

**arecord -vv -c 2 -d 5 -f cd -t wav test.wav**

Thanks Pulpo88!!
I've tried this solution and worked great. I've bought a new Packard Bell EasyNote BG45-025 notebook and had no sound until I've found your post.

Just to help others:
Notebook: Packard Bell EasyNote BG45-025A
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
With Ubuntu 8.04 Desktop Edition 64bit AMD and Intel computers
Kernel 2.6.24-19-generic

Thanks!

---

### Post by jtappin on 2008-07-14
Just a quick note to let folks know that ALSA 1.0.17 final has been released (so should probably be preferred to rc3).

[Expecting my 2133 around the end of the week:-) ]

---

### Post by allinurl on 2008-07-14
Were you able to get to work your internal microphone? cause I just got to work the external microphone.

> **WillyLinux said:**
> Thanks Pulpo88!!
I've tried this solution and worked great. I've bought a new Packard Bell EasyNote BG45-025 notebook and had no sound until I've found your post.

Thanks!

---

### Post by WillyLinux on 2008-07-15
Yes, internal microphone works too. I've just made the tests adjusting properly alsamixergui.

Just a note: I could never make work the sound recorder (not in 8.04, nor in 7.1).

I use Skype (phone talks), I can hear MP3, see and hear YouTube (with Opera 9.5 for 64 bits). These activities with internal or external audio/microphone.

Now I'm testing Ekiga.

Regards.

---

### Post by andif62 on 2008-07-16
@WillyLinux: how did you adjust alsamixer? Still having problems with the built-in microphone :(

---

### Post by WillyLinux on 2008-07-17
hi andif62,
I had to modify volume leves until I found which one was affecting the right device. I'll try to attach an image with the ones I modified. Also it is very important to watch the "capture" column that is to the right because it tells you the sound volume that the device is capturing (it moves up and down as it receives more or less sound, so it is a hint if you are doing it right).

[IMG]http://picasaweb.google.es/info2111/Linux?authkey=ZmL8LugTcrU[/IMG]


[http://picasaweb.google.es/info2111/Linux/photo?authkey=ZmL8LugTcrU#5223863647333696818]("http://picasaweb.google.es/info2111/Linux/photo?authkey=ZmL8LugTcrU#5223863647333696818")
Here is an image: [http://picasaweb.google.es/info2111/Linux/photo?authkey=ZmL8LugTcrU#5223863647333696818](http://picasaweb.google.es/info2111/Linux/photo?authkey=ZmL8LugTcrU#5223863647333696818)

---

### Post by earlycj5 on 2008-07-18
Interestingly enough I can't get the 1.0.17 to compile with the 2.6.24-16 kernel (desireable since Via drivers currently only suport it).

However 1.0.17RC3 will compile properly.

---

### Post by jtappin on 2008-07-18
A couple of questions:

1) Is there any way (other than finding someone with a Windows box) to read the documentation CD? -- the links in it have \ instead of / as path separators and kchmviewer won't open the .chm files.

2) Any idea what the button between the space bar and the touchpad does?

---

### Post by earlycj5 on 2008-07-18
> **jtappin said:**
> A couple of questions:


2) Any idea what the button between the space bar and the touchpad does?

Disables the touchpad.

---

### Post by jtappin on 2008-07-18
> **earlycj5 said:**
> Disables the touchpad.

Now that's a really good idea! Why don't other laptops have a similar thing?

---

### Post by earlycj5 on 2008-07-18
It will occasionally light itself up but not disable the touchpad on mine and I've seen others report the same.

Though it seems to work whenever I press it, touchpad disables.

---

### Post by andif62 on 2008-07-19
One of my biggest complaints on Ubuntu on the Mini-Note is the long boot-up time it needs. Is there anything I can do to speed things up to get boot under 1 min?

---

### Post by WillyLinux on 2008-07-19
> **andif62 said:**
> One of my biggest complaints on Ubuntu on the Mini-Note is the long boot-up time it needs. Is there anything I can do to speed things up to get boot under 1 min?

Hi,
A bit of search will diminish your complaints; thanks to the work of a lot of people we can solve almost everything. 

You can try bootchart [http://www.bootchart.org]("http://www.bootchart.org")
"Bootchart is a tool for performance analysis and visualization of the GNU/Linux boot process. Resource utilization and process information are collected during the boot process and are later rendered in a PNG, SVG or EPS encoded chart."

It's very useful, you can see graphically which processes are slowing the boot time and decide where to modify the boot process.

---

### Post by andif62 on 2008-07-19
> **WillyLinux said:**
> Hi,
A bit of search will diminish your complaints; thanks to the work of a lot of people we can solve almost everything

Just want to see "facts and figures"! Before I try and hassle around with bootchart - and it is a hassle because for me installation did not work - I'd like to know whether it is worth or not.
So, again my question: what are your boot times, guys?
With and without tweaking?

---

### Post by foobard on 2008-07-19
I do not have an external CD/DVD drive, but I want to purchase a 2133 and install ubuntu.

Is there any way to use the CD/DVD on a different laptop to use the install CD on the 2133?

---

### Post by earlycj5 on 2008-07-19
> **foobard said:**
> I do not have an external CD/DVD drive, but I want to purchase a 2133 and install ubuntu.

Is there any way to use the CD/DVD on a different laptop to use the install CD on the 2133?

Install from a USB drive or SD card is the easiest method I've found for my 2133.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

This writeup is for the Acer One, but it does include at least one item related to the lack of a CD drive and editing the FSTAB for a UMPC like ours so it should prove useful as well.
[http://cafelinux.org/OzOs/content/prepare-bootable-ozos-usb-stick-installation](http://cafelinux.org/OzOs/content/prepare-bootable-ozos-usb-stick-installation)

---

### Post by jtappin on 2008-07-20
One gotcha to look out for in the VIA driver install:

The installer sets up the GL library /usr/lib/libGL.so.1.2.via_chrome9 with 0700 permissions (or at least it did for me) so you will probably need to do 
```

sudo chmod a+rx /usr/lib/libGL.so.1.2.via_chrome9

```
To be able to use GL applications.

---

### Post by andif62 on 2008-07-21
@jtappin: Which kernel are you using?

---

### Post by allinurl on 2008-07-21
Could somebody that got their Built-in mic explain how did they get this to work, I just can made the external mic to work, perhaps some screenshots of their alsamixer will be appreciate it. BTW, I already watch the screenshot of couple weeks ago, but dint work for me. Thanks

---

### Post by andif62 on 2008-07-22
> **andif62 said:**
> So, again my question: what are your boot times, guys? With and without tweaking?

Still no replies? O.k., I´ll start with this:

KX868AT, 2 GB RAM, 32 GB Sandisk SATA5000 SSD,
Ubuntu 8.04 with 2.6.24-16 kernel, automatic log-in
From power-on to desktop in 1 min 45 sec

---

### Post by earlycj5 on 2008-07-22
> **andif62 said:**
> Still no replies? O.k., I´ll start with this:

KX868AT, 2 GB RAM, 32 GB Sandisk SATA5000 SSD,
Ubuntu 8.04 with 2.6.24-16 kernel, automatic log-in
From power-on to desktop in 1 min 45 sec

2GB RAM, 120GB 7200RPM HD, 1.6GHz processer.
OzOS
~1 minute according to Bootchart.

---

### Post by andif62 on 2008-07-22
> **earlycj5 said:**
> ~1 minute according to Bootchart.

Hm..sounds very promising!
Did you do some optimization to get this short boot time?

---

### Post by jtappin on 2008-07-22
> **andif62 said:**
> @jtappin: Which kernel are you using?

The stock one from Hardy:
2.6.24-19-generic

And yes I did get the Ubuntu VIA drivers.

---

### Post by earlycj5 on 2008-07-22
> **andif62 said:**
> Hm..sounds very promising!
Did you do some optimization to get this short boot time?

Installed preload.

Turned off Chron, left Anachron on.

Ran the "profile" option from the GRUB menu.

---

### Post by earlycj5 on 2008-07-22
> **jtappin said:**
> The stock one from Hardy:
2.6.24-19-generic

And yes I did get the Ubuntu VIA drivers.

And the 3D acceleration works?  I thought the drivers were version numbered and would only work with the -16 release for Hardy?

---

### Post by catdriver97 on 2008-07-23
> **andif62 said:**
> So, again my question: what are your boot times, guys?
With and without tweaking?


KX869AT, 1GB RAM, Stock 120GB HDD,
Ubuntu 8.04 with 2.6.24-19 kernel,
Automatic log-in, no further optimization

~1 min 40 sec

---

### Post by Monstroxus on 2008-07-24
Installed it on my wife's new HP2133 (1.2 GHz) ... (xubuntu 8.04) it takes around 1:40 to boot up. Runs nicely, but can't enable 3d acceleration (yet), that VIA driver needs to be updated.

---

### Post by jtappin on 2008-07-24
> **earlycj5 said:**
> And the 3D acceleration works?  I thought the drivers were version numbered and would only work with the -16 release for Hardy?

On test - no the kernel modules will not load, I've now removed the VIA proprietory drivers and switched to openchrome (the version in Hardy, maybe I'll try the current one sometime).

Both openchrome and the VIA supplied drivers give glxgears at about 145 fps (the original SuSE only did 87)

---

